# RL WordPress Theme Docker Container

Docker based development environment for RL WordPress site theme, with Swarm secrets used to supply MySQL instance passwords.

## Swarm Secrets

On Docker Desktop, you need to perform the following steps to make a Swarm and use your secrets within the application:

1. Run `docker swarm init` to initialize the swarm
2. Create secrets in the following manner `echo "%secret_here%" | docker secret create %secret_name_here% -`
3. Deploy the WordPress instance as a service, `docker stack deploy -c .\docker-compose.yml %stack_name_here%` 

On Windows, the secrets may not be read properly due to line endings. If you encounter a recursive Failed service state, save each password to a file with LF line endings, then create the secret with `docker secret create %secret_name_here% %secret_file%`
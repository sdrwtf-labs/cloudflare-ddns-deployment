# Cloudflare DDNS Deployment

This repository deploys the `favonia/cloudflare-ddns` Docker container. It automatically updates the Cloudflare DNS record with the current public IP address of the homelab.

## Prerequisites
- A working Docker host.
- A Cloudflare API Token with `Zone.DNS.Edit` and `Zone.Zone.Read` permissions for the target domain.

## Deployment

1. Prepare the deployment directory:
```bash
sudo mkdir -p /opt/cloudflare-ddns
sudo chown $USER:$USER /opt/cloudflare-ddns
cd /opt/cloudflare-ddns

# Clone this repository
git clone git@github.com:sdrwtf-labs/cloudflare-ddns-deployment.git .
```

2. Configure the environment variables:

```bash
cp .env.example .env
```

Edit the `.env` file and provide your real Cloudflare API token.

3. Start the service:

```bash
docker compose up -d
```

4. Verify the logs to ensure the IP was updated successfully:

```bash
docker compose logs -f cloudflare-ddn
```

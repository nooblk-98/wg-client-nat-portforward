

# WireGuard Port Forwarding Setup (wg-easy + Docker)

This script sets up a full-featured WireGuard VPN server using Docker and [`wg-easy`](https://github.com/wg-easy/wg-easy), with automatic **port forwarding rules** applied inside the container to forward traffic to your VPN clients.

> ✅ **Use case**: Allow remote clients to receive forwarded traffic (e.g., game servers, web services) through WireGuard VPN.

---

## 🚀 Features

- Auto installs Docker & Docker Compose
- Sets up `wg-easy` WireGuard UI with your server's public IP
- Automatically creates iptables rules inside the container
- Forwards TCP & UDP traffic from host ports to VPN clients
- Logs setup steps to `/var/log/wireguard_setup.log`

---

## 📦 Prerequisites

- Ubuntu or Debian-based VPS
- Root access
- Internet connection
- Ports open in firewall and/or hosting provider panel

---

## 🔧 Ports Forwarded by Default

The following ports are forwarded to the VPN client IP `10.8.0.2`:

5050, 5051, 5052, 5053, 5054, 5055, 6666, 7777, 8888, 9090, 25565

````

These include common game and app ports. You can change them by editing the `PORTS` array inside the script.

---

## 📜 Installation

```bash
wget https://raw.githubusercontent.com/YOUR_GITHUB_USERNAME/wireguard-port-forward-client-script/main/install.sh
chmod +x install.sh
sudo ./install.sh
````

The script will:

* Update system
* Install Docker & Docker Compose
* Deploy wg-easy on port `51821`
* Set up port forwarding rules
* Save logs in `/var/log/wireguard_setup.log`

---

## 🌐 Access WireGuard Panel

Once setup is complete, go to:

```
http://<your-server-ip>:51821
```

Login and create only **one user** to begin.

---

## 🔒 Security Notes

* Ensure your firewall allows the ports listed above.
* Protect your WireGuard UI with firewall or reverse proxy if exposing publicly.
* Do **not** allow arbitrary port forwards unless you trust the VPN clients.

---

## 📁 File Structure

```
/opt/wireguard/
├── docker-compose.yml      # Main Docker setup
/var/log/
└── wireguard_setup.log     # Full setup log
```

---

## 🛠️ Customization

Edit this section in the script to change forwarded ports or VPN IP:

```bash
VPN_CLIENT_IP="10.8.0.2"
PORTS=(5050 5051 5052 5053 5054 5055 6666 7777 8888 9090 25565)
```

---

## 📚 Resources

* [WireGuard Docs](https://www.wireguard.com/)
* [wg-easy GitHub](https://github.com/wg-easy/wg-easy)
* [Docker Docs](https://docs.docker.com/)

---

## 📄 License

MIT © 2025 [Your Name](https://github.com/nooblk-98)

```
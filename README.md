# arch-delugevpn (partymola fork)

Fork of [binhex/arch-delugevpn](https://github.com/binhex/arch-delugevpn) with the following fixes:

- **Regular image rebuilds** - upstream image was last rebuilt 2025-08-27. This fork rebuilds from current Arch Linux repos, picking up libtorrent 2.0.12+ (fixes segfaults from [arvidn/libtorrent#7769](https://github.com/arvidn/libtorrent/issues/7769) and other stability issues).
- **Watchdog fix** ([upstream PR #443](https://github.com/binhex/arch-delugevpn/pull/443)) - when `deluged` crashes, the watchdog now kills `deluge-web` before restarting `deluged`, preventing the Web UI from getting stuck on the Connection Manager with a stale RPC connection.

Planned:

- **nftables support** - Arch Linux kernel 6.19+ no longer auto-loads the legacy `ip_tables` module ([upstream #444](https://github.com/binhex/arch-delugevpn/issues/444)). The firewall rules need porting from iptables to nftables (this lives in [binhex/scripts](https://github.com/binhex/scripts), shared across all binhex VPN containers).

## Docker image

Pull from GitHub Container Registry:

```bash
docker pull ghcr.io/partymola/arch-delugevpn:latest
```

## Usage

Usage is identical to upstream. See the [upstream README](https://github.com/binhex/arch-delugevpn#readme) for full documentation, environment variables, and examples.

The only difference is the image name:

```
# upstream
binhex/arch-delugevpn

# this fork
ghcr.io/partymola/arch-delugevpn
```

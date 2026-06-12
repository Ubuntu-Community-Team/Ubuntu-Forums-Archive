---
title: "Unable to download torrents on Tranmission Daemon"
date: 2014-12-20
forum: New to Ubuntu
---

### Post by William_Gehrke on 2014-12-20
I have installed transmission on Ubuntu 14.04 LTS server.  I am able to access the internet from the box. When I try to download a torrent, the torrent does not download any files. The 

{
    "alt-speed-down": 50,
    "alt-speed-enabled": false,
    "alt-speed-time-begin": 540,
    "alt-speed-time-day": 127,
    "alt-speed-time-enabled": false,
    "alt-speed-time-end": 1020,
    "alt-speed-up": 50,
    "bind-address-ipv4": "0.0.0.0",
    "bind-address-ipv6": "::",
    "blocklist-enabled": false,
    "blocklist-url": "http://www.example.com/blocklist",
    "cache-size-mb": 4,
    "dht-enabled": true,
    "download-dir": "/media/usb0/Downloads/Complete",
    "download-limit": 100,
    "download-limit-enabled": 0,
    "download-queue-enabled": true,
    "download-queue-size": 5,
    "encryption": 2,
    "idle-seeding-limit": 30,
    "idle-seeding-limit-enabled": false,
    "incomplete-dir": "/media/usb0/Downloads/Incomplete",
    "incomplete-dir-enabled": true,
    "lpd-enabled": false,
    "max-peers-global": 200,
    "message-level": 2,
    "peer-congestion-algorithm": "",
    "peer-id-ttl-hours": 6,
    "peer-limit-global": 200,
    "peer-limit-per-torrent": 50,
    "peer-port": 58359,
    "peer-port-random-high": 65535,
    "peer-port-random-low": 49152,
    "peer-port-random-on-start": true,
    "peer-socket-tos": "default",
    "pex-enabled": true,
    "port-forwarding-enabled": true,
    "preallocation": 1,
    "prefetch-enabled": 1,
    "queue-stalled-enabled": true,
    "queue-stalled-minutes": 30,
    "ratio-limit": 2,
    "ratio-limit-enabled": false,
    "rename-partial-files": true,
    "rpc-authentication-required": true,
    "rpc-bind-address": "0.0.0.0",
    "rpc-enabled": true,

    "rpc-password": "",
    "rpc-port": 9091,
    "rpc-url": "/transmission/",
    "rpc-username": "tranmission",
    "rpc-whitelist": "127.0.0.1,*.*.*.*",
    "rpc-whitelist-enabled": true,
    "scrape-paused-torrents-enabled": true,
    "script-torrent-done-enabled": false,
    "script-torrent-done-filename": "",
    "seed-queue-enabled": false,
    "seed-queue-size": 10,
    "speed-limit-down": 100,
    "speed-limit-down-enabled": false,
    "speed-limit-up": 5,
    "speed-limit-up-enabled": false,
    "start-added-torrents": true,
    "trash-original-torrent-files": false,
    "umask": 0,
    "upload-limit": 100,
    "upload-limit-enabled": 0,
    "upload-slots-per-torrent": 14,
    "utp-enabled": true,
    "watch-dir": "/media/usb0/Downloads/Torrents",
    "watch-dir-enabled": true
}

I thought that transmission does not have permission to access the files. So I chmoded the directories to 777.
drwxrwxrwx 1 root root  2952 Dec 20 18:15 Complete
drwxrwxrwx 1 root root     0 Dec 20 17:03 Completed
drwxrwxrwx 1 root root   408 Dec 20 18:15 Incomplete
drwxrwxrwx 1 root root    48 Dec 20 17:50 Torrents

I don't know what is the issue?

---

### Post by William_Gehrke on 2014-12-20
Solved it with an update. 
sudo apt-get update
sudo apt-get upgrade

---


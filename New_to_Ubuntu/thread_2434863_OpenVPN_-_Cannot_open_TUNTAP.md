---
title: "OpenVPN - Cannot open TUN/TAP"
date: 2020-01-12
forum: New to Ubuntu
---

### Post by mpit52 on 2020-01-12
Hello all,
I'm new to linux and the Ubuntu distribution to which I'm playing around and learning. I am more than at home with windows but have enough knowledge to be dangerous in linux. (I think I know what I'm doing but have no real clue).

With that being said, my current setup is a linux container (Linux Station) on my QNAP. In an attempt to save resources, I decided to go with Ubunto 16.04 as I believe to have read some notes that its lighter weight due to GUI/Graphics requirements. I found some instructions online on how to install OpenVPN and create/configure a connection but for some reason, I cannot establish a connection. After some additional research, I found out how to view the system logs and filter them to just show the VPN Connection events/logs to which it seems I'm having trouble with a file or directory in '/dev/net/tun'. I tried to manually create this directly and set permissions (666) but the same error occurs. I have not had luck with researching this error to which I turn to the community. Please let me know if there is any information that you need and I would be happy to supply. 



SysLog:
Jan 12 12:45:15 ubuntu_1604 NetworkManager[292]: nm-openvpn-Message: openvpn[6015] started
Jan 12 12:45:15 ubuntu_1604 nm-openvpn[6015]: OpenVPN 2.3.10 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [EPOLL] [PKCS11] [MH] [IPv6] built on Jan  9 2019
Jan 12 12:45:15 ubuntu_1604 nm-openvpn[6015]: library versions: OpenSSL 1.0.2g  1 Mar 2016, LZO 2.08
Jan 12 12:45:16 ubuntu_1604 nm-openvpn[6015]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Jan 12 12:45:16 ubuntu_1604 nm-openvpn[6015]: NOTE: chroot will be delayed because of --client, --pull, or --up-delay
Jan 12 12:45:16 ubuntu_1604 nm-openvpn[6015]: NOTE: UID/GID downgrade will be delayed because of --client, --pull, or --up-delay
Jan 12 12:45:16 ubuntu_1604 nm-openvpn[6015]: UDPv4 link local: [undef]
Jan 12 12:45:16 ubuntu_1604 nm-openvpn[6015]: UDPv4 link remote: [AF_INET]###.###.###.###:1194
Jan 12 12:45:16 ubuntu_1604 nm-openvpn[6015]: [vpn] Peer Connection Initiated with [AF_INET]138.122.234.27:1194
Jan 12 12:45:19 ubuntu_1604 nm-openvpn[6015]: ERROR: Cannot open TUN/TAP dev /dev/net/tun: No such file or directory (errno=2)
Jan 12 12:45:19 ubuntu_1604 nm-openvpn[6015]: Exiting due to fatal error
Jan 12 12:45:19 ubuntu_1604 NetworkManager[292]: (nm-openvpn-service:6007): nm-openvpn-WARNING **: openvpn[6015] exited with error code 1
^C

---

### Post by SeijiSensei on 2020-01-12
I've seen this error before, but unfortunately the person posting the query never gave us an answer.  You can read my post here: [https://ubuntuforums.org/showthread.php?t=2431966&p=13911243&viewfull=1#post13911243](https://ubuntuforums.org/showthread.php?t=2431966&p=13911243&viewfull=1#post13911243)

I would be surprised if you don't have /dev/net/tun though.  However it is not a directory but a device. So delete whatever you put there and follow the instructions in that post to create the device. Please tell us if that resolved the problem.

---

### Post by mpit52 on 2020-01-12
I appreciate the quick reply but it didn't seem to help. I first removed the directories that I manually created by using the following commands. 
```

sudo rmdir /dev/net/tun
sudo rmdir /dev/net

```
Afterwards, I tried following your steps to recreate the directory and file but VPN still won't establish a connection. I did receive a warning while following your steps
```

sudo mknod /dev/net/tun c 10 200

```
"mknod: /dev/net/tun: file exists"

I receive a slightly different error messages when trying to connect. 
[COLOR=#000000]ERROR: Cannot open TUN/TAP dev /dev/net/tun: Is a directory (errno=21)


PS. When I run 'ls /dev/net" "tun" is has a green text with a green highlight. Not sure what that means or if this information is useful. [/COLOR]

---

### Post by SeijiSensei on 2020-01-13
On my system, /dev/net is an ordinary directory with root ownership and 755 permisssions.
```

phl@fuzzface:/dev$ ls -l | grep net
drwxr-xr-x  2 root root          60 Jan 10 19:44 net

```

/dev/net/tun is a device
```

phl@fuzzface:/dev$ ls -l net
total 0
crw-rw-rw- 1 root root 10, 200 Jan 10 19:44 tun

```

I would remove /dev/net again, then reconstruct it and the tun device as follows:
```

cd /dev
sudo rm -rf net
sudo mkdir net
cd net
sudo mknod  tun c 10 200

```
/dev/net/tun appears on my machine in green text with black reverse-video. (My terminal uses black on light yellow as the default.)

---

### Post by juanbretti on 2020-06-13
Did anyone found a solution?

---

### Post by SeijiSensei on 2020-06-13
I gave all the information I could. On my 20.04 Kubuntu desktop, I have /dev/net/tun by default.

What version of Ubuntu?  What do you see when you run "ls /dev/net"?

---

### Post by SeijiSensei on 2020-06-13
I gave all the information I could. On my 20.04 Kubuntu desktop, I have /dev/net/tun by default.

What version of Ubuntu?  What do you see when you run "ls -l /dev/net"? You should see
```
crw-rw-rw- 1 root root 10, 200 Jun 13 13:03 tun
```

---

### Post by juanbretti on 2020-06-13
I'm using [WSL ]("https://docs.microsoft.com/en-us/windows/wsl/install-win10")1.0, I just read that /dev/net is not supported in version 1.0.
I have to upgrade to WSL 2.0.

Thank you for your support.

---


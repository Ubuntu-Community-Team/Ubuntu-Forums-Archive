---
title: "Help running openVPN?"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by Aeph on 2008-08-24
I was hoping someone knew of a good openVPN howto. I would like to run a VLAN/VPN through the terminal, but have very little knowledge of these sort of things. Any help would be appreciated.

---

### Post by DrPppr242 on 2008-08-24
Not entirely sure what you mean by vlan/vpn, if your just trying to join two vlans on a single network there's better ways but here's a basic open vpn guide.

First install the program

'sudo apt-get install openvpn'

The first thing you need to do is create some key for us to use for the server. OpenVPN includes some easy-rsa scripts for us to manage the keys.

Change directory and edit the variables file:

cd /usr/share/openvpn/easy-rsa
vim -w vars

Scroll all the way down to the bottom and you want to change these 5 values to something more appropriate.

export KEY_COUNTRY="US"
export KEY_PROVINCE="AZ"
export KEY_CITY="Scottsdale"
export KEY_ORG="AIM Consulting"
export KEY_EMAIL="sysadmin@a--i--m.com"

To export those variables to your current shell run, that is a “.<space>./vars”

. ./vars

If this is the first time run the clean command to make sure the keys folder is empty, if this is not the first time you are generating keys DO NOT RUN ./clean-all

./clean-all

Build the certificate authority and Diffie Hellman files, this might take a minute on slow computers

./build-ca
./build-dh

Now we need to build some keys for the server and all the clients. Make sure you say yes to the two y/n questions it will ask you. Just hit enter when it ask you for a password. You want to leave this part blank.

./build-key-server server
./build-key client1
./build-key client2
./build-key client3

This will produce all the keys you need in the keys folder (/usr/share/openvpn/easy-rsa/keys).

Server Files:
    ca.crt : Put in the /etc/openvpn folder
    server.crt : Put in the /etc/openvpn folder
    server.key : Put in the /etc/openvpn folder
    dh1024.pem : Put in the /etc/openvpn folder

Client Files:
    client.crt : Include with client files
    client.key : Include with client files
    ca.crt : Include with client files

Now we need to create a config file for our server.

Here is a basic server config:

proto udp
dev tun
duplicate-cn
ca ca.crt
cert server.crt
key server.key  # This file should be kept secret
dh dh1024.pem
server 10.3.10.0 255.255.255.0

#this makes the client aware of internal subnets, it's not neccessary if you only want access to the vpn server (like a remote file server)
push "route 192.168.1.0 255.255.255.0"
push "route 10.3.10.0 255.255.255.0"

keepalive 10 120
comp-lzo
user nobody
group nogroup
persist-key
persist-tun
status openvpn-status.log
verb 3



Here are some optional things if there is a windows domain they are connecting too

push "dhcp-option DOMAIN <domain name>"
push "dhcp-option DNS <DNS server IP address>"


Client File:

client
float
proto udp
dev tun
remote <Remote Server>
resolv-retry infinite
persist-key
persist-tun
ca ca.crt
cert aim.crt
key  aim.key
comp-lzo
verb 3

  This is what openvpn would be run on to access the remote LAN from a client machine.  Note that the ca.crt, aim.crt, and aim.key, must be in the folder with this file the command to run it would be 'sudo openvpn <client file name>'

---

### Post by Aeph on 2008-08-25
> **DrPppr242 said:**
> Change directory and edit the variables file:

cd /usr/share/openvpn/easy-rsa

I entered this and the terminal gave the following error:

```
bash: cd: /usr/share/openvpn/easy-rsa: No such file or directory
```

I checked the filesystem and It doesn't have the easy-rsa directory. Should I just create one and get a copy of the file I'm supposed to edit and place it in there?

---

### Post by mlentink on 2008-08-25
What exactly are you trying to accomplish? You might be better off using Hamachi, which is fairly easy to install, and gives you sort of a 'vpn-for-dummies'. Works ok though.
OpenVPN is more flexible, but also a bit finicky to install. Their own How-to is ok, which you can find [here]("http://openvpn.net/index.php/documentation/howto.html")

---

### Post by Aeph on 2008-08-25
I have used Hamachi, but wanted to try openVPN because it was open source. As for what I'm trying to do: I want to try to play LAN games online with friends. I mostly just want to learn more about these kind of things, though. I'll read through the tutorial for now.

---

### Post by wgrant on 2008-08-25
You might also want to look at network-manager-openvpn, which will integrate the OpenVPN client into NetworkManager.

---

### Post by DrPppr242 on 2008-08-25
> **Aeph said:**
> I entered this and the terminal gave the following error:

```
bash: cd: /usr/share/openvpn/easy-rsa: No such file or directory
```

I checked the filesystem and It doesn't have the easy-rsa directory. Should I just create one and get a copy of the file I'm supposed to edit and place it in there?

sorry I usually do this on gentoo rather than debian, my debian box has the path or all the easy-rsa stuff in /usr/share/doc/openvpn/examples/easy-rsa, and it looks like all the same commands can be used but you might makes sure it's the same on ubuntu.

---

### Post by Aeph on 2008-08-27
I'm running into errors when I try to do just about anything. Could this be because I am a part of a secured wireless network?

---

### Post by ldfj3jf on 2008-10-03
> **wgrant said:**
> You might also want to look at network-manager-openvpn, which will integrate the OpenVPN client into NetworkManager.

Sorry for the thread necromancy, but this is actually incorrect - The network-manager-openvpn (downloaded today from the repo on 8.04) doesn't read ovpn files. You can actually pass it nonsensical files (like say, your favorite powerpoint), and it won't even warn you it's invalid.

Also, even if you set things up manually in there, nothing happens when you try to connect (as in, nothing, not even a message or anything). It's the whole thing is a GUI to nowhere.

Just thought I'd say, because a lot of people are banging their heads about that same problem.

---


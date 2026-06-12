---
title: "[SOLVED] OPENVPN istall and exec?"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by aris! on 2008-10-28
Ok I am new to linux-ubuntu. Iwould like to use openvpn so that my ip address is altered to the one provided by my institution . I used synaptic package manager to install openvpn deamon and some other programms openvpn-blacklist_0.1, neetwork-manager-openvpn_0.3. The problem is that I cannot see them. I found them into the var/cashe/apt/archives folder. When I try to install i get that they are already installed any help". How can i run them so that i will start the other big goal of configuring the open vpn to work proprely

---

### Post by handydan918 on 2008-10-28
In a terminal, do ```
which nameofprogram
```
This should give you the location of the executable.

---

### Post by The Cog on 2008-10-28
OpenVPN installs a service that looks in /etc/openvpn for configuration files which it then uses to start VPNs on boot-up. You probably don't want to put your openvpn configuration in there because otherwise it will run every time you start your PC.

The other way to do it is to launch openvpn and name the configuration file to run. This what I do. I use a command like this (as root):
> /usr/sbin/openvpn --config /root/openvpn/work/client.conf
The config file itself looks like this (I have changed a few details for privacy, like my name and address):
> client
dev tun101
proto udp
remote 1.2.3.4 1194
resolv-retry infinite
nobind
user nobody
group nogroup
persist-key
persist-tun
ca /root/openvpn/work/ca.crt
cert /root/openvpn/work/my-name.crt
key /root/openvpn/work/my-name.key
comp-lzo
verb 1

This leaves a command prompt open all the time the VPN is up, and I just close it when done.

I think I have heard of GUI openvpn front-ends but can't remember their names and have never tried them.

---

### Post by aris! on 2008-10-28
Thanks for the advice and its propably what i need. Please don't forget i am an absolute bigginer with linux. When i do /usr/sbin/openvpn --config /root/openvpn/work/client.conf  I get Error opening configuration file: /root/openvpn/work/client.conf. I guess That I have to create the conf file. How do I do that? Next I am told that I have to include in the conf file the following lines. Can you get anything out of it. For your information I have another txt .pem file with a key certificate iwill havew to tell openvpn to see. 
 ##### BEGIN CONFIGURATION FILE auth-vpn.ovpn #####

remote vpn.auth.gr
dev tap0
client
proto tcp
port 443

cryptoapicert "SUBJ:Aristotle University of Thessaloniki"
ca VPNRootca.pem

comp-lzo
verb 3

persist-key
persist-tun
ns-cert-type server

##### END CONFIGURATION FILE auth-vpn.ovpn #####

---

### Post by aris! on 2008-10-28
Thanks for the advice and its propably what i need. Please don't forget i am an absolute bigginer with linux. When i do /usr/sbin/openvpn --config /root/openvpn/work/client.conf  I get Error opening configuration file: /root/openvpn/work/client.conf. I guess That I have to create the conf file. How do I do that? Next I am told that I have to include in the conf file the following lines. Can you get anything out of it. For your information I have another txt .pem file with a key certificate iwill havew to tell openvpn to see. 
 ##### BEGIN CONFIGURATION FILE auth-vpn.ovpn #####

remote vpn.auth.gr
dev tap0
client
proto tcp
port 443

cryptoapicert "SUBJ:Aristotle University of Thessaloniki"
ca VPNRootca.pem

comp-lzo
verb 3

persist-key
persist-tun
ns-cert-type server

##### END CONFIGURATION FILE auth-vpn.ovpn #####[/QUOTE]

---

### Post by The Cog on 2008-10-28
I think you probably create the config file using those lines you posted. Use gedit to create the file like this maybe:
> mkdir ~/openvpn
cd ~/openvpn
gedit client.conf
Put the other files they supply you wth in the same directory (I would have thought they could supply you with the config file too if you ask).
Then start it from the command line like this:
> cd ~/openvpn
sudo openvpn --config ~/client.conf

---

### Post by aris! on 2008-11-01
I asked my Institution but they kindly explained that they do not support at the moment linux based vpn although they support unbix in gerneral. Anyway it is getting better and I started finding my way with commands. I did what you've syggested and I remined you that I directed openvpn to seek the configuration file my uni has prpvided and in the same dir I have included the .pem file that provides a certificate needed and under windows it had to be in the same file with the configuration settins. After 
sudo openvpn --config ~/client.conf I get the message
"Options error: You must define TUN/TAP device (--dev)" any ideas?
I also tried to work openvpn with kvpnv but there I get "error: OpenvpnManagementHandler: Got no greeting within 3 seconds from management interface, retrying."

---

### Post by aris! on 2008-11-01
I asked my Institution but they kindly explained that they do not support at the moment linux based vpn although they support unbix in gerneral. Anyway it is getting better and I started finding my way with commands. I did what you've syggested and I remined you that I directed openvpn to seek the configuration file my uni has prpvided and in the same dir I have included the .pem file that provides a certificate needed and under windows it had to be in the same file with the configuration settins. After 
sudo openvpn --config ~/client.conf I get the message
"Options error: You must define TUN/TAP device (--dev)" any ideas?
I also tried to work openvpn with kvpnv but there I get "error: OpenvpnManagementHandler: Got no greeting within 3 seconds from management interface, retrying."

---

### Post by flint_ on 2008-11-02
Greetings Mighty Cog!

I read your posts with great pleasure.  I am installing OpenVPN to operate in concert with IP Cop.  The Server side seems to be operating properly, or at least I believe it is.

My conceptual stupid question here is can you test a VPN connection from within the network you are trying to VPN into, or must you be outside the firewall in order to test connectivity?

Thanks in advance and...

Kindest Regards,

Flint

---

### Post by aris! on 2008-11-05
Dear Flint.
I have no idea but I believe the answer to your question is yes. I think so because from within my institution ie inside the firewall, I can call up the openvpn and change my ip address to whatever the openvpn can assign to me at the time. I DONT KNOW HOW you can test this.
Anyway I wish I was a little more knowledgeable about command line instruction I would have solved my problem much sooner. 
By the way Mighty Cog is the one who gave the answer to my problems and big thanks to him.

---


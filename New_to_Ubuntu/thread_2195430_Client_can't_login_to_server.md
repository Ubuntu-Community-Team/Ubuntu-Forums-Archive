---
title: "Client can't login to server"
date: 2013-12-24
forum: New to Ubuntu
---

### Post by Jijo_Cherian on 2013-12-24
Hi, 

First of all let me tell you that I'm very new to ubuntu. 
We a group of friends are doing some project in visual effects and hence planned to have a small server client on ubuntu have a common place for the files to be stored. 


What we did :
We bought 3 client systems and a server system. 
Server : Ubuntu Server 13.04
Client : Ubuntu Desktop 13.04. 



We configured dhcp server and openssh for the same.

The dhcpd. config file on server  has following configuration 
subnet 192.168.1.0 netmask 255.255.255.0 {
        range 192.168.1.10 192.168.1.100;
        range 192.168.1.150 192.168,1,200;
        option routers 192..168.1.254;
        option domain-name-servers 192.168.1.1, 192.168.1.2;
        option domain-name "team-server";
}

the sshd_config 

Port 2222

PubkeyAuthentication yes

Banner /etc/issue.net


at client end we have connected to server as 
Network Connection 
        TeamServer
  Method : Manual
  Address : 192.168.1.152
  netmask : 255.255.255.0
 Gateway : 192.168.1.255
 

We are using a switch to connect. Also we are able to ping each other with the config. 

Also we are booting with network boot option but we cant get the login screen for the server.

Due to this currently we are sharing the files using hard disk. 

If anyone can help us it will be great. Please give the solution in step by step form. 

Thanks a lot :)

---

### Post by ian-weisser on 2013-12-25
How do the clients try to connect to server? ssh command? Something else?
Does each user have an account on the server?

---

### Post by zeljkojagust on 2013-12-26
Can you please tell me is there any device like a small broadband router in front of your server? If there is, why don't you use it for IP allocations, there is no need for DHCP service running on server.

Why do you have two ranges in your DHCP configuration? Also options like "option routers 192..168.1.254;" are defined outside of "Subnet {...}" definition. "Option domain-name-servers 192.168.1.1, 192.168.1.2;" requires presence of DNS (Bind) service. Did you configure one?

Gateway : 192.168.1.255 -> this is a broadcast address and I'm pretty shure it's not same as gateway address (according to your configuration gateway is defined here -> "option routers 192..168.1.254;").
To share files of server you should have a file sharing service installed and configured like Samba or NFS.

My advice: Configure network manually on your server and clients so that all machines are in the same range (you can use 192.168.1.0/255.255.255.0), configure NFS -> [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo) and be done with it.

---

### Post by Jijo_Cherian on 2013-12-26
Thanks a lot :) Will do that and reply to this thread :)

---

### Post by Jijo_Cherian on 2013-12-26
[@ ]("http://ubuntuforums.org/member.php?u=1841707")[URL="http://ubuntuforums.org/member.php?u=1841707"][B][COLOR=#000000]ian-weisser : We are booting from Network boot option and connection through SSH. 

 
[/COLOR][/B][/URL]

---


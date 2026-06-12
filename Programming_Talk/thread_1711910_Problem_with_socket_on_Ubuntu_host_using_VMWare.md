---
title: "Problem with socket on Ubuntu host using VMWare"
date: 2011-03-21
forum: Programming Talk
---

### Post by ttuyen32 on 2011-03-21
Dear all,

I am new to socket programming in linux. But somehow I have managed writing a simple client/server program which simply exchange messages with each other. It runs well over different computers in LAN (server and client run on different machines) or on loopback address 127.0.0.1.

Our target platform for server is windows XP, and for client is Ubuntu 10.04 kenel 2.6.32-21-generic

However, when our customer uses windows host and ubuntu guest on VMWare 7.x, data cannot be exchanged. I use wireshark to track down and find out that
 
- both server and client already successfully establish their connection. 
- Client send its first message to server. 
- Server receive the message successfully. And send back to client its first message.
- The message from server comes to client but it seems to be discarded and cannot reach to my application.
- After 10 seconds without receiving anything from server, client close the connection and retry.

I use iptables to disable all firewall rules. There is no use. I use firestarter, there is no use. I don't know what exactly happen. 

Thank you very much in advance for your help. I attach wireshark capture here for your reference.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=186776&stc=1&d=1300762223[/IMG]

---


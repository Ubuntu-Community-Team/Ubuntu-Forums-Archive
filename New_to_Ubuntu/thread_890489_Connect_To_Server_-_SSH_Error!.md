---
title: "Connect To Server - SSH Error!"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by kauboy on 2008-08-15
I tried to set up file sharing between my two Ubuntu 8.04 PCs, which share the internet through a Wired Router. I know the IP addresses of my two Desktops and have no problems with the internet either. I installed SSH on both PCs (ssh, openssh-client, openssh-server, etc.) to be able to share files between them. 

When I tried "Connect To Server" from PC1 and and chose "SSH" as Service Type, gave the IP Address of my PC2, Port as 22, Username as the Root User of PC2, and the corresponding password, I was able to get full access (Read/Write) to my PC2 from PC1. Good.

But, when I did exactly the same from my PC2 to be able to access my PC1, I got nowhere. My PC2 just failed to connect to my PC1. How can this be possible??? I tried almost everything from my PC2 in the "Connect To Server" with Service Type as "SSH". Just din't work. I've added screenshots of the errors I got during my various trials.

Please help me fix this up! I even tried re-installing SSH on my PC2, to no use. I can perfectly access my PC2 from my PC1, while the other way around, it just fails, no matter what I do.

I also tried unmounting the PC2 folder from my PC1 before trying to access my PC1 from PC2, still din't work! :confused:

---

### Post by billgoldberg on 2008-08-15
> **kauboy said:**
> I tried to set up file sharing between my two Ubuntu 8.04 PCs, which share the internet through a Wired Router. I know the IP addresses of my two Desktops and have no problems with the internet either. I installed SSH on both PCs (ssh, openssh-client, openssh-server, etc.) to be able to share files between them. 

When I tried "Connect To Server" from PC1 and and chose "SSH" as Service Type, gave the IP Address of my PC2, Port as 22, Username as the Root User of PC2, and the corresponding password, I was able to get full access (Read/Write) to my PC2 from PC1. Good.

But, when I did exactly the same from my PC2 to be able to access my PC1, I got nowhere. My PC2 just failed to connect to my PC1. How can this be possible??? I tried almost everything from my PC2 in the "Connect To Server" with Service Type as "SSH". Just din't work. I've added screenshots of the errors I got during my various trials.

Please help me fix this up! I even tried re-installing SSH on my PC2, to no use. I can perfectly access my PC2 from my PC1, while the other way around, it just fails, no matter what I do.

I also tried unmounting the PC2 folder from my PC1 before trying to access my PC1 from PC2, still din't work! :confused:

Try using another port. Make sure it isn't blocked by a firewall.

Try connecting using the terminal to see if it is nautilus screwing up or not (ssh -x username@server).

---

### Post by prshah on 2008-08-15
> **kauboy said:**
> 
When I tried "Connect To Server" from PC1 I was able to get full access (Read/Write) to my PC2 from PC1. Good.

But, when I did exactly the same from my PC2 to be able to access my PC1, 


Open a terminal, and try to access your PC1 with the following terminal command; post back (censored) output results:```

ssh -vvv username@PC1
```

ssh (client) comes pre-installed; you don't have to do anything for that. However, you do need to install openssh-server on both machines, and apparently you've done that. The above command will show us where things are going wrong.

---

### Post by kauboy on 2008-08-15
> **prshah said:**
> Open a terminal, and try to access your PC1 with the following terminal command; post back (censored) output results:```

ssh -vvv username@PC1
```

ssh (client) comes pre-installed; you don't have to do anything for that. However, you do need to install openssh-server on both machines, and apparently you've done that. The above command will show us where things are going wrong.

I did as you had suggested, except that I din't use the '-vvv' as it threw up far too many lines, which I thought were unnecessary. When I typed "ssh username@PC1" from the Terminal of my PC2 and entered PC1's password, the Terminal prompt actually changed to "username@PC1:~$"!!! Which means I could actually log into my PC1 from PC2, via the Terminal and view the files and folders!! Thanks to prshah for that! But, I still get the same error as given in Post1.gif,

"Can't display location "sftp://PC1/"
"Error reading from unix: Input/output error"

in a dialog box when I try to use "Connect To Service" for the same purpose. So, I don't have a GUI means for accessing my PC1 from PC2. Atleast I know that I can access via the Terminal. Any ideas for making "Connect To Service" work?? :)

---

### Post by prshah on 2008-08-15
> **kauboy said:**
> 
"Can't display location "sftp://PC1/"
"Error reading from unix: Input/output error"
Atleast I know that I can access via the Terminal.

I have no idea why ssh works and sftp doesn't. The closest guess I can make is either firewall troubles and/or a required service not running on the other computer (PC1).

Personally, I'd recommend you to use scp in any case; but if you absolutely need a GUI solution and nothing else works, you should try enabling ssh port forwarding in PC1, and then use SSH to perform remote GUI operations. There's a number of guides available that can help you in this but perhaps you should leave it as a last resort.

---

### Post by kauboy on 2008-08-17
I may have found a solution to my problem, the same was reported sometime back at [http://ubuntuforums.org/showthread.php?p=2778127#post2778127]("http://ubuntuforums.org/showthread.php?p=2778127#post2778127"), I'll try it soon. Hope it works. Thanks to billgoldberg and prshah for helping me out. :)

---

### Post by scorp123 on 2008-08-17
> **kauboy said:**
>  ... except that I din't use the '-vvv' as it threw up far too many lines  That's the exact purpose of that switch. And if someone tells you to use it then this means that particular person had the impression that you did not supply nearly enough information or technical details for anyone to be able to successfully troubleshoot the problem. Hence: using "-vvv" in case of strange SSH problems is a very good idea.

> **kauboy said:**
>  which I thought were unnecessary.  You thought wrong. ;)

---

### Post by scorp123 on 2008-08-17
> **kauboy said:**
> I may have found a solution to my problem, the same was reported sometime back at [http://ubuntuforums.org/showthread.php?p=2778127#post2778127]("http://ubuntuforums.org/showthread.php?p=2778127#post2778127")  Total overkill and bad advice. You don't have to completely remove SSH. Never ever. It's not going to solve anything. If there is a real problem then it will easily reappear again.

If there is a problem with any of the config files then "ssh -vvv" would have revealed that by now ;)

But OK, you decided that it is "unnecessary" to supply that output. Fine then. Have fun. :)

---

### Post by ichthus on 2008-08-17
For filesharing at home, I use nfs:
[http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html](http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html),
[http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing](http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing)
. . . 

If you use a router, you should be able to use the hostnames (like PC1 (options) ... \n PC2(options) ) if you have a router with DHCP enabled, without playing with the /etc/host file (i.e., with you router, the computer will pick up the i.p. addresses from the router, so you don't have to use numbers like 192.168.xxx.xxx/xx(options) in the /etc/exports file: you can just specify the computer's names.)

---


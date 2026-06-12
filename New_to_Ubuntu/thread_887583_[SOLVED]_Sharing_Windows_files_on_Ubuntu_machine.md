---
title: "[SOLVED] Sharing Windows files on Ubuntu machine"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by WilhelmGGW on 2008-08-12
I have read a bunch of other threads and still can't get this to work. I have a Windows and an Ubuntu machine on the same network. I got my Ubuntu machine to connect via the network and print to the printer installed on my Windows machine.  But I can't make the connection to access with the Ubuntu machine the Open Office documents I have on the Windows computer.

I have Samba on the Ubuntu machine.  My Windows firewall is not obstructing the connection.  I've marked the OO files on Windows for sharing. If I try Places-Connect to Server-Windows Share and enter the address of my Windows machine in Server, I get the message: 

Can't display location "smb://192.168.1.101/" No application is registered as handling this file.

Please help.

---

### Post by Thelasko on 2008-08-12
Does it work the other way?  Can you make a shared folder in Ubuntu and upload the files to it from the Windows machine?  I also recommend the "system-config-samba" package.  It provides a GUI for managing Samba.

---

### Post by appi2012 on 2008-08-12
Make sure you enter the username you are connecting to in the username field. Or just type:
```
smb://I.P./username/
```
in the nautilus location bar.

---

### Post by WilhelmGGW on 2008-08-12
> **appi2012 said:**
> Make sure you enter the username you are connecting to in the username field. Or just type:
```
smb://I.P./username/
```
in the nautilus location bar.

I still get this message: "Failed to mount windows share."

---

### Post by Thelasko on 2008-08-12
Do you have another Windows machine on the network to make sure it isn't a problem on the Windows side?

---

### Post by WilhelmGGW on 2008-08-12
> **Thelasko said:**
> Do you have another Windows machine on the network to make sure it isn't a problem on the Windows side?

No other machine on network. Just 1 Windows and 1 Ubuntu.

---

### Post by WilhelmGGW on 2008-08-12
Bump. Still unresolved.

---

### Post by WilhelmGGW on 2008-08-12
I reran Network Setup on Windows machine, and everything worked fine.  Till I rebooted my Ubuntu machine [no change to Windows machine]. Now I can't reconnect Ubuntu to Windows. Still waiting to see what to try next.  Thanks.

---

### Post by WilhelmGGW on 2008-08-12
The only trouble is, I have to reset my connection every time I reboot my Ubuntu machine. Is there some way I can get it to reconnect automatically each time I reboot?

---

### Post by Thelasko on 2008-08-12
What do you mean by "reset my connection?"  Do you mean login to samba?

---

### Post by WilhelmGGW on 2008-08-12
> **Thelasko said:**
> What do you mean by "reset my connection?"  Do you mean login to samba?

No. I have to go Places - Connect to Server
And re-enter the Window Share info.

---

### Post by Thelasko on 2008-08-12
what "service type" are you using?

---

### Post by WilhelmGGW on 2008-08-12
> **Thelasko said:**
> what "service type" are you using?

Windows share

---

### Post by Thelasko on 2008-08-12
I'm not familiar with that method.  I've always used samba to share files between Windows and Ubuntu.  I use the "system-config-samba" package to help me set it up, and then it's just like sharing on windows.  If you set it up correctly, you should be able to go to places>network servers and find it.  You don't have to connect each time.

Let me know if I'm going down the wrong path.  I think I understand what you are describing, but I might be getting confused.

---

### Post by halitech on 2008-08-12
Just helped Kender42 with the same problem, check out post #17

[http://ubuntuforums.org/showthread.php?t=887061](http://ubuntuforums.org/showthread.php?t=887061)


taking info from here:
[http://ubuntuforums.org/showthread.php?t=852029](http://ubuntuforums.org/showthread.php?t=852029)

try opening Nautilus and in the address bar type in smb://192.168.1.67/*foldername* and see if it will connect

---

### Post by appi2012 on 2008-08-12
When you enter the information, you can set up a bookmark. (I'm assuming you can connect now.) Check "Add Bookmark" and name it what you wish. Now it shows up in your places menu. Also, when entering the password to login, click on "Remember forever"

That should make it easier to correct

---

### Post by HermanAB on 2008-08-12
Here is some info on debugging Samba
[http://aeronetworks.ca/samba-debug-howto.html](http://aeronetworks.ca/samba-debug-howto.html)

Note that the easiest method to share files is via FTP.  The second easiest method is NFS and the most horribly difficult method is with Samba.  

There is a very good guide on the Samba web site - read it.  If that doesn't convince you to avoid using Samba, nothing will... ;)

Cheers,

Herman

---


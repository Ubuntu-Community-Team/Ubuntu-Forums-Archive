---
title: "what do you use for remote administration?"
date: 2011-12-19
forum: New to Ubuntu
---

### Post by anon0 on 2011-12-19
From Windows, how would you access these functions on Ubuntu: command prompt, file administration, and remote desktop?

---

### Post by Lars Noodén on 2011-12-19
The easiest way, once you are used to it, is to use SSH.  That gives you a full shell on the remote machine and anything that you could have done while sitting at the console can then be done remotely.  There is a bit of a learning curve but it is well worth it because it is so powerful and flexible.

---

### Post by anon0 on 2011-12-19
Is "shell" a synonym for the command line interface? I tried PuTTY and it granted me access right away.

Quick question: how do I grant access to the Ubuntu's computer's file structure for Windows clients, so I can edit and move files?

---

### Post by WasMeHere on 2011-12-19
Hi anon0,

***ssh*** is 'secure shell' meaning that the communication is encrypted. You have bash or whatever shell in terminal mode. But you can also use grapical user interfaces if you start the session with the -X or -Y options.

```
ssh -X user@hostname
ssh -Y user@hostname

```
read the manual ```
man ssh
```

If you only want to manage or transfer files, use ***sftp***, which is called SSH in the Nautilus file browser (File -- Connect to server -- Service)

*Edit: In Windows you can use the free software [I]**WinSCP*** that includes ssh and sftp.[/I]

Have fun finding out about Ubuntu :-)
Olle

---

### Post by Lars Noodén on 2011-12-19
> **anon0 said:**
> Is "shell" a synonym for the command line interface? I tried PuTTY and it granted me access right away.

Quick question: how do I grant access to the Ubuntu's computer's file structure for Windows clients, so I can edit and move files?

Some call it the "command line" but that IMHO sets you off on the wrong foot.  It is a full language interpreter capable of flexible, powerful scripting.  So if you think of it as a programming exercise, it will be easier to learn and less overwhelming.

Quick answer: you use [Samba](https://help.ubuntu.com/community/Samba) or SSHFS to grant access.

---

### Post by kanikilu on 2011-12-19
> **anon0 said:**
> From Windows, how would you access these functions on Ubuntu: command prompt, file administration, and remote desktop?

1) command prompt: SSH to host using PuTTY
2) file administration: either PuTTY (CLI) or sFTP client (GUI) like WinSCP or [FileZilla](http://filezilla-project.org/).
3) remote desktop: [VNC]("https://help.ubuntu.com/community/VNC") or [NoMachineNX]("https://help.ubuntu.com/community/NomachineNX)/[FreeNX](https://help.ubuntu.com/community/FreeNX).

---

### Post by BertN45 on 2011-12-19
I have used xrdp in Ubuntu, it is the server for the windows remote desktop client. You can also get it through the software center. It works fine and in windows you do not have to change anything. You have to realize that xrdp emulates the XP version of the remote desktop.

In Ubuntu 11.04 I had some problems due to interference with the samba authentication, but that problem only occurs if samba has been installed. I had to patch to "text" files common-auth and samba in /etc/pam.d, 

basically commenting out or removing:
"auth optional pam_smbpass.so migrate" in common-auth

and adding the same line 
"auth optional pam_smbpass.so migrate" after "@include common-auth" in the samba file

---

### Post by anon0 on 2011-12-20
Thank you all for the replies. I'm new to SSH and need to learn more, but for now I'm using PuTTY for commands and WinSCP for file operations. I haven't been able to do remote desktop effectively:

> **BertN45 said:**
> I have used xrdp in Ubuntu, it is the server for the windows remote desktop client. You can also get it through the software center. It works fine and in windows you do not have to change anything. You have to realize that xrdp emulates the XP version of the remote desktop.

I tried xrdp yesterday with Ubuntu Server 11.10 and it didn't work for me. I installed ubuntu-desktop and xrdp packages, but when I used xrdp it just gave me the background picture and a taskbar on top, but no way to launch programs. All I could do is click on the three icons on the right hand side of the taskbar. So the Server edition is not working with xrdp at least on my setup.

---

### Post by MartijnNL on 2011-12-20
It is possible to use Teamviewer for remote desktop purposes, but you'll be running your data (encrypted) through another server. And commercial applications require a fee.

I have used VNC piped through SSH (for encryption) in the past. But that was linux to linux.

---

### Post by anon0 on 2011-12-20
VNC sounds like a common way to access Ubuntu desktop from Windows, but I haven't been granted access by the system yet. I tried TightVNC but by default I'm getting a "failed to connect to server" error. It's hard for me to figure out Ubuntu Server's Unity-based GUI that I downloaded because a lot of tutorials either don't correspond to this new interface or my setup is somehow crippled.

---

### Post by MartijnNL on 2011-12-20
Are you sure there's no firewall blocking your access?

---

### Post by Hellweek on 2011-12-20
I know many people here will disagree.

However, I configured SSH to allow forwarded XSession, and I am now able to ssh into the machine and run command-line programs as well as GUI programs.

I could even run a GNOME session, but found that was to heavy so I just start up lxpanel.

lxpanel gives me a nice toold strip that I can place on my screen and have access to programs from it.

---

### Post by anon0 on 2011-12-20
> **MartijnNL said:**
> Are you sure there's no firewall blocking your access?

Thank you... Well actually it was the port. I typed in 5701 instead of 5901. Now TightVNC loads, but it's basically like xrdp, with no real functionality. I'm just going to assume it's an issue with Ubuntu Server for now unless someone points out something idiotic I've done, which is probable.

---

### Post by BertN45 on 2011-12-21
> **anon0 said:**
> I tried xrdp yesterday with Ubuntu Server 11.10 and it didn't work for me. I installed ubuntu-desktop and xrdp packages, but when I used xrdp it just gave me the background picture and a taskbar on top, but no way to launch programs. All I could do is click on the three icons on the right hand side of the taskbar. So the Server edition is not working with xrdp at least on my setup.

If you run the server edition you have samba and could try the patch, I described in my previous post in the common-auth and samba authorization files. I remember also that I was looking at a xrdp screen unable to continue. Currently your xrdp is trying to use the samba authorization, that fails and it hangs waiting for a sign to continue.

At that time I was using Ubuntu 11.04 and I was controlling my home desktop over the internet. I wanted to use RDP/xrdp, because the MS RDP protocol is so efficient.

---


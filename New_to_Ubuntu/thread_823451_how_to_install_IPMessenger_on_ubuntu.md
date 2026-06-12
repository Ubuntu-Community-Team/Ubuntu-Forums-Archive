---
title: "how to install IPMessenger on ubuntu"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by pranjalsaxena on 2008-06-09
Hi. I m ne to linux please help....
I want to install IP messenger on my system.I have downloaded the .tar file and extracted it now please guide me what to do.....

Thanking you in advance

---

### Post by 3rdalbum on 2008-06-09
You shouldn't have downloaded the .tar.gz file - there's an IP Messenger program in the Ubuntu repositories already.

Just go into Synaptic Package Manager and do a search for "xipmsg". When it appears in the right side of the window, right-click it and go to "Mark for Installation". Click "Apply" at the top of the window, and wait. It will install automatically.

---

### Post by vamsibethapudy on 2008-06-09
you can even try installing the windows version of IPmsg using wine.:wink:

---

### Post by melwin.a3 on 2008-06-09
First you download the windows version IPmsg
then install wine in your ubuntu system
after installing wine,
On the ipmsg icon right click open with wine emulator

It will show some error dialog boxes dont worry about that click ok

enjoy using ipmsg

---

### Post by pranjalsaxena on 2008-06-09
I tried to run the ipmsg.exe by "wine ipmsg.exe" but no response came frm the terminal and when I tried by right click few errors came I just clicked ok then also no response.....
can u please tell where is the proxy setting file for apt
and how ca i set the proxy for it.

---

### Post by john77eipe on 2010-09-29
Where do I find it after installation? I mean under Applications.

---

### Post by godspeedmav on 2010-09-29
if you have installed from the repository or software centre, it will be under Application > Internet.

if windows version is installed, it will be under Application > Wine > Programs.

---

### Post by john77eipe on 2010-10-01
Thanks. There is an IP messenger for Genome2 available. It looks very similar to the Windows version!!!

---

### Post by sgshah on 2011-06-17
> **3rdalbum said:**
> You shouldn't have downloaded the .tar.gz file - there's an IP Messenger program in the Ubuntu repositories already.

Just go into Synaptic Package Manager and do a search for "xipmsg". When it appears in the right side of the window, right-click it and go to "Mark for Installation". Click "Apply" at the top of the window, and wait. It will install automatically.

Thank you for the piece of information.
I have done "xipmsg" installation as per procedure given by you.
But I couldn't locate and run the "xipmsg" application. I have searched for same but couldn't find anything.
I cross-checked "xipmsg" is still installed only.
So how to run the "xipmsg" in Ubuntu 11.04.
Any help guys.

with best regards.

---

### Post by 3rdalbum on 2011-06-17
Have you tried typing 'xipmsg' into the terminal?

---

### Post by Mogs22 on 2011-10-21
> **3rdalbum said:**
> Have you tried typing 'xipmsg' into the terminal?


yes it worked in the terminal window.

---

### Post by lavezarez on 2011-12-20
go to the terminal (press ctrl + alt + T)
type:
sudo apt-get install g2ipmsg

---


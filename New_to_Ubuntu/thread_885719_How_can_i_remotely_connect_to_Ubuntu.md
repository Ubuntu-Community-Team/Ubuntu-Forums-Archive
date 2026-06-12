---
title: "How can i remotely connect to Ubuntu"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by mdmytryk on 2008-08-10
How would i go about remotely connecting to another computer also running ubuntu?  Im sure this question has been answered a few times before, but i cant seem to find the answers im looking for. Could someone explain how i can do this, or point me in the direction of a tuturial.

---

### Post by spiderbatdad on 2008-08-10
openssh-server
```
 sudo apt-get install openssh-server
```
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

---

### Post by Yunus Emre on 2008-08-10
Is there any program runs on GUI?

---

### Post by MaindotC on 2008-08-10
I've a feeling he's looking for remote desktop access.  [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

On the machine you'd like to view, clicke System -> Preferences -> Remote Desktop.  When you select the desired features, get the ip address of the machine by opening a command prompt and type:
```

ifconfig eth0

```

where eth0 is the name of the active network card on the machine.  It may be eth1 or 2 depending on your settings.  This assumes that the machine to which you're connecting has a public IP address.  If it's behind a home-grade router and you're not on the same network, you'd have to map the VNC service to the machine you want to connect by using port address translation.  Judging by your initial question I'm sure this will take some time for you to grasp.

---

### Post by spiderbatdad on 2008-08-10
> **Yunus Emre said:**
> Is there any program runs on GUI?

sure its under Places>>Connect to Server
the instructions are all in the ssh docs on the link above.

---

### Post by Lod on 2008-08-10
> **mdmytryk said:**
> How would i go about remotely connecting to another computer also running ubuntu?  Im sure this question has been answered a few times before, but i cant seem to find the answers im looking for. Could someone explain how i can do this, or point me in the direction of a tuturial.What do you want to achieve? Do you want to take over the desktop, do you want to transfer files, do you only need a command line.

---

### Post by mdmytryk on 2008-08-10
Sorry, ill be a little more specific.  What i hope to accomplish is to transfer files back and forth between computers.  I dont need full control of the computer, just enough to send/receive files.

---

### Post by cgkades on 2008-08-10
also you have the possibility to run just applications remotly as well. so you have quite a few options with slightly different (in some cases) way of going about it. the running remote apps is what i use the most probably, well that and using my home computer as a proxy

---

### Post by cgkades on 2008-08-10
> **mdmytryk said:**
> Sorry, ill be a little more specific.  What i hope to accomplish is to transfer files back and forth between computers.  I dont need full control of the computer, just enough to send/receive files.

using ssh is the most secure way. you'll want to install gftp or something like that for the gui to connect to your server. applications->add/remove then search for gftp

as far as a gui to set up SSH, someone else  here might be able to point you in the right direction

---

### Post by MaindotC on 2008-08-10
sftp and you don't need a gui.  For example, to connect to a machine you'd type:

```
sftp root@136.204.34.119
```

where root is the name of the account you wish to use when connecting.  Could be root or any other type of privileged user.  If the machine has a name, you can use that:

```
sftp root@machinename.example.com
```

While you're logged into the machine you can navigate using regular commands like cd, and on the machine that you are PHYSICALLY logged into you can navigate by preceding the same commands with a lowercase L.  For example, lcd = local change directory, lls = local list.

I don't know of any way to transfer FOLDERS this way and I haven't read the man pages.  You can transfer folders using the scp command.

---

### Post by spiderbatdad on 2008-08-10
openssh-server and graphical tools provided in the places menu:[http://www.youtube.com/watch?v=bV5OW6Rl4Ig](http://www.youtube.com/watch?v=bV5OW6Rl4Ig)
You can just as easily grab a whole folder.
sorry for the quality. my first attempt at youtube post.
The gimp thing is a recent bug in intrepid...where all icons are launching gimp.:(

---

### Post by cgkades on 2008-08-10
> **strAlan said:**
> 
I don't know of any way to transfer FOLDERS this way and I haven't read the man pages.  You can transfer folders using the scp command.

which is why i suggested gftp. much easier to use and it supports sftp

---

### Post by spiderbatdad on 2008-08-10
gftp is one more app you don't need, imo, to use file transfers, and strong passwords can be used in place of public keys...though some will surely dispute that.
The simplest, I believe, is ssh as the video above shows. I had that openssh-server running in five minutes after reading the tutorial, and I've never tried it before. Second simplest is to host on apache and use the indexes option to make folder browseable.

---

### Post by spiderbatdad on 2008-08-10
bleh. double post:(

---

### Post by MaindotC on 2008-08-10
Nice, spider.  I never used the "Connect to Server" and SSH for getting files.  This seems easier and more user-friendly.  Star for you.

---


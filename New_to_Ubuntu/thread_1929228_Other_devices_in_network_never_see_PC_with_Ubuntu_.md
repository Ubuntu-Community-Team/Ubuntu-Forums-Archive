---
title: "Other devices in network never see PC with Ubuntu 11.10"
date: 2012-02-21
forum: New to Ubuntu
---

### Post by matbluvenger on 2012-02-21
So I've been trying to set up ways of accessing my Ubuntu 11.10 PC from other devices around the house. 

However, when trying to get uShare to work so I can stream videos to my XBOX 360 the console never detected the Ubuntu PC but picked up others that have been used previously to stream through Vuze (in Windows.) And it never found it after I tweaked and reconfigured uShare.

And now I've been trying to use a Windows PC to connect to the Ubuntu PC with Remote Desktop, and TightVNC on the Windows PC does the same as the XBOX did: detects everything in the network except for the Ubuntu PC.


Any fixes/advice? Thanks in advance!

---

### Post by wyliecoyoteuk on 2012-02-21
Have you got Samba server or VNC server installed on the Ubuntu PC?

---

### Post by matbluvenger on 2012-02-21
> **wyliecoyoteuk said:**
> Have you got Samba server or VNC server installed on the Ubuntu PC?

Neither, I was under the impression that the capabilities were built in.


Quite new here... sorry for the n00biness.

---

### Post by matbluvenger on 2012-02-21
Does anybody have any help? 

**Mostly I'd like to be able to stream videos from my Ubuntu 11.10 PC to my XBOX 360 like I can with Vuze from a Windows PC.** The TightVNC was my attempt at an alternate solution since I couldn't get uStream working but that didn't work either.

Please assist...

---

### Post by matbluvenger on 2012-02-26
Gotta try again...


Anything?

---

### Post by Lisiano on 2012-02-26
Take a look at this for uShare
[https://help.ubuntu.com/community/Xbox360Media](https://help.ubuntu.com/community/Xbox360Media)
As for Samba, if you aren't sharing any files, you will be "invisible" to Windows PCs. For VNC, either you forgot to tell Ubuntu to allow Remote Desktops (Dashboard [Windows key/Top button on the launcher] -> Desktop Sharing) or Windows is being picky, if the later, try giving it your Ubuntu's IP. Go to Network Manager (The icon with the 2 arrows/Fan-like-thing/WiFi indicator) -> Connection Information

P.S. I think that images are only allowed here as long as they are to explain something. (De)motivators don't fall under that category.

---

### Post by matbluvenger on 2012-02-26
I apologize for the image... didn't know that rule. 

But I've tried setting all of the appropriate sharing/network/whatever settings which each thing I've tried.


Just tried Samba... it installed and then wouldn't load when I tried to open it. I give up, I'm just going to carry my tower downstairs when I want to watch movies on the big TV :D

---

### Post by Lisiano on 2012-02-26
Don't give up! If you do, think of your poor tower when you trip on the stairs!
Samba won't show up on your Xbox I recall, here is a guide for setting up Samba properly
[https://help.ubuntu.com/community/Samba/SambaServerGuide](https://help.ubuntu.com/community/Samba/SambaServerGuide)

---

### Post by matbluvenger on 2012-02-27
> **Lisiano said:**
> Don't give up! If you do, think of your poor tower when you trip on the stairs!
Samba won't show up on your Xbox I recall, here is a guide for setting up Samba properly
[https://help.ubuntu.com/community/Samba/SambaServerGuide](https://help.ubuntu.com/community/Samba/SambaServerGuide)

Ha yeah that would be the saddest day ever. I have time today to mess around with Samba, I'll give it a shot! Thank you very much!

---

### Post by matbluvenger on 2012-02-27
Okay so I got samba to work and I can select directories to share from my Ubuntu PC.... but the Windows PC still doesn't see the Ubuntu PC in the network so I have absolutely no way of accessing the shared directory....

The issue isn't that I can't share from the Ubuntu PC... it's that *nothing* else on the network can see that the computer exists and that's with uShare, VNC, and Samba now.

---

### Post by audiomick on 2012-02-27
Make sure that they both have the same work group name. I'm hazy about that, but I believe I have seen that a fair bit as the cause of that sort of problem.

You might want to look at this, if you haven't already
[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

---

### Post by CharlesA on 2012-02-27
Try accessing it via IP address from the Windows box.

---

### Post by audiomick on 2012-02-27
> **CharlesA said:**
> Try accessing it via IP address from the Windows box.
If it comes to that, try to ping it from the windows box. You need to open that window where you can put commands in, enter cmd to get a terminal (or whatever windows calls it) and do
```
ping <ip address>
```

If there is a connection, it should come back with an answer pretty much straight away.

---

### Post by matbluvenger on 2012-02-27
Yeah I get a fine ping test when I ping 192.168.0.100 on the Windows PC.

Also, all computers are in the default workgroup "WORKGROUP"

---

### Post by RedRat on 2012-02-27
If I recall correctly, Windows does not know how to read your Linux file system. There is a free little program that you can download on your Windows machine to allow windows to read Ubuntu files and the file system. I know I had to put it on my WinXP machine to see my Ubuntu machine. Ubuntu can read the NTFS file system with no problem nowadays.

---

### Post by CharlesA on 2012-02-27
> **RedRat said:**
> If I recall correctly, Windows does not know how to read your Linux file system. There is a free little program that you can download on your Windows machine to allow windows to read Ubuntu files and the file system. I know I had to put it on my WinXP machine to see my Ubuntu machine. Ubuntu can read the NTFS file system with no problem nowadays.
That wouldn't apply in this case since you are doing it over the network.

@OP: Have you tried adding the IP of the Ubuntu box to the hosts file on the Windows machine and seeing if it'll see it that way?

---

### Post by matbluvenger on 2012-03-13
So after a bunch of fiddling I still can't get the Windows box to access the Ubuntu one, either by sharing files or Remote Desktop.

I thought I was on the right track with the remote desktop. I allowed everything (password pending, of course) through the Remote Desktop settings. And using TightVNC on the Windows box I tried accessing it using the router IP and the Ubuntu box IP to no avail.

*le sigh*

---


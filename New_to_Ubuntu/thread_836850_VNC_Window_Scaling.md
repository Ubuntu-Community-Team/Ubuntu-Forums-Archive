---
title: "VNC Window Scaling?"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by RROY on 2008-06-21
I'm trying to figure out how to scale my VNC Viewer window to fit my client.

I VNC into my server from my laptop, my laptop's display resolution is 1024x768 while my server is 1280x1024.  I hate scrolling up-down-left-right to manage my server.  I have been forced to use RDP sessions in the meantime, but this is not ideal.

On all the Windows VNC clients I have used, there is a window scaling option to make it fit to the size of the client...are there any linux clients that can do this?

---

### Post by fatality_uk on 2008-06-22
Hit F11 key and that should give you full screen.

---

### Post by RROY on 2008-06-22
> **fatality_uk said:**
> Hit F11 key and that should give you full screen.
I know how to get it full screen, but it goes full screen at 1280x1024 and my laptop's display is only 1024x768 so i still have to scroll the entire remote screen to see the taskbar, etc...

I'm looking for a client that can scale the remote desktop down to 1024x768 from 1280x1024.

---

### Post by acidsolution on 2008-06-22
You can do that in server side 
while creating the vnc session you can define the geometry i.e the resolution 

```

vncserver :1 -geometry 1024x768


```
for further u can see thru the man pages or follow the link
[http://www.realvnc.com/products/free/4.1/man/vncserver.html](http://www.realvnc.com/products/free/4.1/man/vncserver.html)

u dont have to change the resolution of remote server u just can adjust the resolution of the vnc session you have created in server.
hope this may help

---

### Post by RROY on 2008-06-22
> **acidsolution said:**
> You can do that in server side 
while creating the vnc session you can define the geometry i.e the resolution 

```

vncserver :1 -geometry 1024x768


```
for further u can see thru the man pages or follow the link
[http://www.realvnc.com/products/free/4.1/man/vncserver.html](http://www.realvnc.com/products/free/4.1/man/vncserver.html)

u dont have to change the resolution of remote server u just can adjust the resolution of the vnc session you have created in server.
hope this may help
Maybe I'm missing something...I'm not trying to run the VNCServer on my laptop...I'm trying to connect to my server from my laptop.

Why would I run vncserver on my laptop?  I'm currently using Vinagre (pre-installed with Ubuntu) to make the connection.

I tried using VNCServer and it gave me errors about a shared library...I'm playing around now to try it out, but it confuses me on why I would run a VNC Server on my laptop when I just want a client running...

---

### Post by RROY on 2008-06-22
I can't seem to find libstdc++-libc6.2-2.so.3...I used alien to convert the RealVNC RPM to Deb...I'm gonna try downloading the source and instaling it that way...

No luck...still can't find libstdc++-libc6.2-2.so.3

I found somewhere I should install libstdc++2.10-glibc2.2 for it, but I can't find that either.

I've been using apt-file to search... butI get the following errors when I try to update apt-file:

Can't get [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Contents-i386.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Contents-i386.gz)
Can't get [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Contents-i386.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Contents-i386.gz)
Can't get [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Contents-i386.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Contents-i386.gz)
Can't get [http://archive.canonical.com/ubuntu/dists/hardy/Contents-i386.gz](http://archive.canonical.com/ubuntu/dists/hardy/Contents-i386.gz)
Can't get [http://archive.ubuntu.com/ubuntu/dists/hardy-security/Contents-i386.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-security/Contents-i386.gz)
Can't get [http://archive.ubuntu.com/ubuntu/dists/hardy-security/Contents-i386.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-security/Contents-i386.gz)
Can't get [http://archive.ubuntu.com/ubuntu/dists/hardy-security/Contents-i386.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-security/Contents-i386.gz)
Can't get [http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/Contents-i386.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/Contents-i386.gz)
Can't get [http://archive.ubuntu.com/ubuntu/dists/hardy-backports/Contents-i386.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-backports/Contents-i386.gz)
Can't get [http://archive.ubuntu.com/ubuntu/dists/Hardy/Contents-i386.gz](http://archive.ubuntu.com/ubuntu/dists/Hardy/Contents-i386.gz)
Can't get [http://wine.budgetdedicated.com/apt/dists/etch/Contents-i386.gz](http://wine.budgetdedicated.com/apt/dists/etch/Contents-i386.gz)

---

### Post by RROY on 2008-06-22
OK...I got vncserver and vncviewer working, found the library in a dapper archive.

The geometry setting just sets the size of the window...the remote server's display resolution is still high and I have to scroll it...

Any other ideas?

---

### Post by RROY on 2008-06-22
I just realized I may have caused some confusion.

My Server is running Windows 2003...not linux.

---

### Post by acidsolution on 2008-06-22
> **RROY said:**
> I just realized I may have caused some confusion.

My Server is running Windows 2003...not linux.

You shuould have mentioned this before 
if you are using windows 2003 as your server than u can use rdesktop  rather than vncserver 
```
rdesktop server_ip 
```
if you want full screen mode than -f shuld be added if u want to define your geometry than -g 90% or any other scale can be used

---

### Post by RROY on 2008-06-22
> **acidsolution said:**
> You shuould have mentioned this before 
if you are using windows 2003 as your server than u can use rdesktop  rather than vncserver 
```
rdesktop server_ip 
```
if you want full screen mode than -f shuld be added if u want to define your geometry than -g 90% or any other scale can be used
That's what I've been using, but I prefer VNC because I like to manage my downloads on my server.

With Remote Desktop, it logs into a separate terminal services login, and I can't control my already logged in user that is doing all the downloads...

I guess I'll have to just resize the desktop on the server...I was trying to avoid that, the windows Real VNC client has a scaling option...

---

### Post by acerqueti on 2008-06-27
Just thought I'd add my tuppence worth.

This is a problem I run into all the time. I need to be able to access various Windows boxes (XP, Server 2000/3/8) and finding a client that comes close to the Win32 RealVNC one (vncviewer.exe) seems impossible. Surely dynamic scaling isn't too much to ask for?!

I use various distros; although I've been using Linux for a good few years (PS2 devkits, SuSE, RedHat), Ubunto HH and Fedora 9 are by far my current faves, as they are finally getting user-friendly enough that I would feel reasonably confident installing a Linux box for non-tech friends and relatives, whereas until very recently the base level of knowledge required to do most simple tasks in Linux would have been beyond most of them.

But it's frustrating when a Windows app has better features than it's Linux counterpart. It's easier to understand when it's some giant commercial product: the fact that Photoshop knocks GIMP and it's brethern about is hardly shocking, Adobe charge an arm and a leg to every Mac and Windows user and invest a fortune in time and money to maintain that premium product and it's market lead. But when it's a simple little app that the company claims is supported on the Linux platform, but is missing key features, that's galling and puzzling, and something that should be questioned.

Anyway, my little workaround: not elegant, clearly resource-wasteful and certainly not anywhere near as desirable as a decent Linux VNC client, but use the Windows RealVNC client through Wine.

```
wine vncviewer.exe
```

It's a backwards option perhaps, but it's one way of getting the functionality I want.

AJ

---

### Post by lossfound on 2008-07-25
Is this for real? All of the Windows VNC clients I've tried - *TightVNC included* - have scaling. Why do *none* of the native Linux clients seem to have this option at all? Surely there's a way to turn it on at least as a CLI parameter. Surely? I've been looking and could not find one either.

Thanks, acerqueti.

---

### Post by ckeller211 on 2008-08-13
If you don't mind installing a few KDE libraries....KRDC is a VNC program that has a scaling function.  I use if on my EeePC and I can scale a 1024 x 768 screen on it's native 800 x 640 resolution in fullscreen.  

The only problem I have with it, is that the cursor doesn't seem to work quite right, but it isn't a big deal for me.

It is in the repos under KRDC I believe.  Hope it helps.

---

### Post by nu-2-buntu on 2008-08-13
I guess you are all talking about the free version of RealVNC's viewer.

The Entreprise Editions, the ones you have to pay for, do have a scale to fit option (vncviewer -scaling=fit).

They also do a debian package.

---

### Post by Highway on 2011-10-14
Hi,
Vinagre has scaling.  
[http://projects.gnome.org/vinagre/index.html](http://projects.gnome.org/vinagre/index.html)

Works very well, and is light app too.

Highway.

---

### Post by tio00 on 2012-05-24
> **Highway said:**
> Hi,
Vinagre has scaling.  
[http://projects.gnome.org/vinagre/index.html](http://projects.gnome.org/vinagre/index.html)

Works very well, and is light app too.

Highway.

Thanks for the tip! Vinagre is perfect!

---

### Post by lisati on 2012-05-24
Old thread closed

---


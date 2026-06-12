---
title: "Directvnc Framebuffer errors"
date: 2006-05-18
forum: Repositories &amp; Backports
---

### Post by eldorel on 2006-05-18
This is probably something stupid about my setup, but it's driving me crazy. 

After installing Directvnc from repo I am getting the following error when I try to run it.

Authentication OK
dfb.c <47>:
        (#) DirectFBError [DirectFBCreate( &dfb )]: File not found!

From what i can tell this is caused by a failure to run my console in framebuffer mode, but for the life of me i don't know how to correct it. 

I'm having this problem on 4 different computers. 2 are setup with all the bells and whistles, one is a test server, and the last is an old hp laptop. The laptop is the one i need it on, because i don't have resources to waste on a full X setup.

Thanks in advance,

---

### Post by Ptero-4 on 2006-05-18
you should try to run Directvnc from outside X11.

---

### Post by eldorel on 2006-05-18
>  i don't have resources to waste on a full X setup.

The Laptop i was initially testing on doesn't even have x installed, nor does the test server. 

I have tested this from console on all 4 machines, with perfectly re-producable results.

---

### Post by eldorel on 2006-05-21
ok, i've been playing with this for a few days now, but i've confirmed that i am running in framebuffer mode "vga=771" 800x600-8b and that i'm running off of the vesafb drivers on all 4 systems, but i still have the same problem. so, any help would be appreciated.

---

### Post by eldorel on 2006-05-24
ok, further notes this is immediately after a fresh install of brezzy from the cd.

installed with -server at boot time, 
apt-get install directvnc
~~
directvnc 192.168.1.13
You did not specify a display to connect to. I will assume 0
Password:
Authentication OK
dfb.c <47>:
           (#) DirectFBError [DirectFBCreate( &dfb )]: Initialization Error!

---

### Post by siennalizard on 2006-06-08
Bump

Exactly the same for me.

Cheers for any advice.

J.

---

### Post by eldorel on 2006-06-08
I'm hoping the problem is resolved in dapper. I'm downloading it today, and will post an update on this later.

---

### Post by eldorel on 2006-06-18
sorry it took so long to repost, but the same problem exists in dapper.

---

### Post by jol-blazey on 2008-11-30
I got this error and switched to xtightvncviewer (tightvnc / vncviewer) 1.2.9-22 which works out of the box. I am on hardy heron.

```
vncviewer 192.168.1.NNN:0
```

---

### Post by eldorel on 2008-11-30
While I do appreciate the info (and the bit of thread necromancy), this doesn't really help. 

The original problem was that the framebuffer vnc client was non-functional.
 Xvncviewer has always worked correctly, but directvnc is for text-only servers without the rest of the Xorg/gnome/gtk stack.

And it seems to still be broken in hardy and intrepid... :(

---

### Post by Jose Catre-Vandis on 2009-05-17
Try running as sudo, this worked for me:
```
sudo directvnc xx.xx.xx.xx:1
```
(my server is on display 1)

---

### Post by dining_philosopher on 2010-11-12
I tried with sudo but result is the same.

---

### Post by dryliketoast on 2010-11-19
bump - similar issues for me using ubuntu 10.04:

$ vncserver 

New 'X' desktop is nix:1

Starting applications specified in /home/user/.vnc/xstartup
Log file is /home/user/.vnc/nix:1.log

$ directvnc localhost:1
Password: 
Authentication OK
(!) DirectFB/Config 'quiet': Unknown message type ''!
(!) DirectFB/Config 'quiet': Unknown message type ''!
dfb.c <44>:
        (#) DirectFBError [DirectFBSetOption ("quiet", "")]: Not supported!

a shame really because this is a very handy program

---

### Post by mrtomservo on 2010-12-01
I'm running a 10.04 server, and I have directvnc working properly.  You must download the 0.7.6 version, along with the libdirectfb-1.2-9. 

```
wget http://mirror.pnl.gov/ubuntu//pool/main/d/directfb/libdirectfb-1.2-9_1.2.10.0-4ubuntu2_i386.deb
```

```
wget http://mirror.pnl.gov/ubuntu//pool/universe/d/directvnc/directvnc_0.7.6-1build1_i386.deb
```

Install the libraries first.

```
sudo dpkg --install ./libdirectfb-1.2-9_1.2.10.0-4ubuntu2_i386.deb
```

Then directvnc.

```
sudo dpkg --install ./directvnc_0.7.6-1build1_i386.deb
```

That got it up and running for me.  Hope that helps someone! :)

---


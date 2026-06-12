---
title: "Slim Server o Fluxbuntu"
date: 2007-11-04
forum: Other OS Talk
---

### Post by fast eddie on 2007-11-04
I have just installed Fluxbuntu on an old laptop which seems to have gone ok. I want to try to run Slim Server in Fluxbuntu but I am having trouble installing it.

I have SS working on another machine running Ubuntu 7.04 but I cant remember how I installed it (still new to Linux) :confused:

If anyone can help me I would be grateful. I have answered the question on the Slim Server forums as well so if I get an answer there and it works I will post it here.

Thanks for your help,

Graham

Just figured out where how to get to the Synaptic manager so hopefully it will work

---

### Post by n3tfury on 2007-11-04
it looks like it's in the repos, so you should be able to bring it up in synaptic

[http://packages.ubuntu.com/gutsy/sound/slimserver](http://packages.ubuntu.com/gutsy/sound/slimserver)

---

### Post by fast eddie on 2007-11-04
As suggested I have moved this question from the other thread I started.

OK, I got Fluxbuntu working and I have installed Slim Server. Now I cant seem to get it to recognise the USB hard disk I have just plugged in.

Any ideas ??

---

### Post by kerry_s on 2007-11-04
> **fast eddie said:**
> As suggested I have moved this question from the other thread I started.

OK, I got Fluxbuntu working and I have installed Slim Server. Now I cant seem to get it to recognise the USB hard disk I have just plugged in.

Any ideas ??

**sudo apt-get install ivman**

---

### Post by fast eddie on 2007-11-04
sorry to be a  muppet but what next? I have run the command you suggested so how do I browse to a directory on the usb hard drive now?

---

### Post by kerry_s on 2007-11-04
> **fast eddie said:**
> sorry to be a  muppet but what next? I have run the command you suggested so how do I browse to a directory on the usb hard drive now?

that will make it so that rox will automount usb drives, now just go to /media/your-drive

---

### Post by meborc on 2007-11-04
in fluxbuntu, there is a known bug... this is posted in the fluxbuntu home page, under distro index:> There are a number of known issues for 7.10 RC

1. Ivman does not run (thus automounting appearing it does not work)

To fix this:

joejaxx@fluxbuntu:~$ mkdir ~/.ivman
that means you just need to make that dir to your home dir...

hope this helps... ivman is already installed, but just this folder needs to be created!

---


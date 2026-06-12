---
title: "Trying to Create my own Ubuntu Home server"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by dbtrade on 2008-06-19
Actually started with Kubuntu.

I'm approaching the various "Features" of WHS and trying to emulate them in Kubuntu.

I'm new to linux altogether, so maybe this was a little ambitious, but I'm familiar with Windows networking etc.

I have several Windows machines and want to tie in a home server (kubuntu)

Features:

 1.) File sharing/serving - this was pretty easy using Samba.

2.) headless configuration - set-up VNC over SSH and can configure and run the Linux machine remotely.

3.) Back-up. Single instance file store. - UGH - this is where I'm getting my rear kicked. I'm trying to use bacula as it seems to be a universal (i.e will work on the windows machines too) to do unattended backups. WHS implements a 'cluster level' backup scheme and single instance storage. From what I've read, Bacula comes the closest to this or rather RSYNC does. But the bacula implementation is what works across platfroms.

I tried Unison, but not happy with the file specification scheme.

So after that long winded  intro, I'm up to my problem - I try to run Bacula, I get the modules launcehd but I can't connect to the director. I get the following error:

bat.JobId 0: Fatal error: bsock.c:129 Unable to connect to Director daemon on xxmyhostnamexx:9101. ERR=Connection refused.

I'm running the MySQL version and mysql is running. I used apt-get manager and installed the version from there. I did minimal editing to the config files...just enought to replace the wild card settings.

db

---


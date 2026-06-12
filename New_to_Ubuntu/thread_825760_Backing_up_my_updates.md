---
title: "Backing up my updates"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by Lorry ZA on 2008-06-11
Hi everyone,

Well needless to say I'm a total noob and I've been using Hardy for about a month and a half now and I'm loving it.

The reason i want to backup all the automatic updates is that here In lovely South Africa our ISP shaft us with our bandwidth.

And being the noob i am its only gonna be a short while until i kill my installation and i would hate to have do all the updates again.

---

### Post by rudihawk on 2008-06-11
I second that question! Also from SA here....same reasons - just the ISP though. Anyone?

---

### Post by pjnsmb on 2008-06-11
have a look at this programme- I use it for backups

[http://quickstart.phpbb.net/viewtopic.php?f=8&t=11](http://quickstart.phpbb.net/viewtopic.php?f=8&t=11)

---

### Post by Golem XIV on 2008-06-11
All the updates and installed packages downloaded through the "standard" ways (apt-get, Synaptic or System Update) will be in /var/cache/apt/archives.  You can back up this directory and then just copy it back to your new installation.

In order to do this, first run

```
sudo apt-get autoclean
```

which will remove obsolete packages.  Then run

```
sudo cp /var/cache/apt/archives /media/disk/updates
``` 
to copy them to /media/disk (which would be the standard mount point of an external USB disk, it will change depending on where you want to copy the files).

To recover it, once Ubuntu is installed you should run

```
sudo cp /media/disk/updates /var/cache/apt/archives
```
to recover it.  Once this is done, spark up the update Manager and it will load all packages from this cache and not download them (unless a new version came out in the mean time). 

**sudo** is used because /var/cache/apt can be written only with administrative rights.

there is also the option to use **aptoncd**.  It can be installed from Synaptic but I never used it.

---

### Post by drs305 on 2008-06-11
There is a gui-based program that does much of what Golem XIV discusses. It is called APTonCD. You can read about it and download the deb from here:
[http://aptoncd.sourceforge.net/]("http://aptoncd.sourceforge.net/")

Edit: I see Golem mentioned it. Use the link to get it.

---

### Post by Lorry ZA on 2008-06-11
Thanks guys i'm gonna give APTonCD a try ans see how it goes.

Thanks again for the speedy response, the support of the ubuntu community is amazing

---


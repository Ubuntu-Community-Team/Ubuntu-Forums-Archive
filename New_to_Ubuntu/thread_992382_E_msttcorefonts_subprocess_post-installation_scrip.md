---
title: "E: msttcorefonts: subprocess post-installation script returned error exit status 1"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by maxcomx on 2008-11-24
I need help, i tried different things already, nothing worked out yet, it getting very annoying.

i tried to uninstall it, but it doesn't work. its no even install anymore, but i still get this error.

E: msttcorefonts: subprocess post-installation script returned error exit status 1


And i also have this problem :

W: Failed to fetch [http://dl.google.com/linux/deb/dists/stable/Release.gpg](http://dl.google.com/linux/deb/dists/stable/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://dl.google.com/linux/deb/dists/stable/non-free/i18n/Translation-en_US.bz2](http://dl.google.com/linux/deb/dists/stable/non-free/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

And its the same for every third party repository.
i already installed anon-proxy,tor,privoxy...  

max@max-laptop:~$ $http_proxy 
bash: [http://localhost:4001:](http://localhost:4001:) No such file or directory

well i don't know what to doooo.

thanx for help

---

### Post by K.Mandla on 2008-11-24
Moved to Absolute Beginner Talk.

---

### Post by jemate18 on 2008-11-24
> **maxcomx said:**
> I need help, i tried different things already, nothing worked out yet, it getting very annoying.

i tried to uninstall it, but it doesn't work. its no even install anymore, but i still get this error.

E: msttcorefonts: subprocess post-installation script returned error exit status 1


And i also have this problem :

W: Failed to fetch [http://dl.google.com/linux/deb/dists/stable/Release.gpg](http://dl.google.com/linux/deb/dists/stable/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://dl.google.com/linux/deb/dists/stable/non-free/i18n/Translation-en_US.bz2](http://dl.google.com/linux/deb/dists/stable/non-free/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

And its the same for every third party repository.
i already installed anon-proxy,tor,privoxy...  

max@max-laptop:~$ $http_proxy 
bash: [http://localhost:4001:](http://localhost:4001:) No such file or directory

well i don't know what to doooo.

thanx for help

did you use
```
sudo apt-get install msttcorefonts
```

to install it?

---

### Post by Andavane on 2008-12-18
> **jemate18 said:**
> did you use
```
sudo apt-get install msttcorefonts
```

to install it?
hello I'm not the original poster, but I just had the same problem;
in my case I installed via synaptic.
Am I correct in assuming that I need to follow and add the lines described in:

usr/share/doc/x-ttcidfont-conf/README.Debian?
i.e.

> You can change the backend by running
	dpkg-reconfigure x-ttcidfont-conf
in console.

 And please add these FontPath lines in /etc/X11/xorg.conf
(These FontPaths are changed by x-ttcidfont-conf-8)

 FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
 FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID" 

I have hesitated as I don't know what a "backend" (or a "frontend") is...

Looking forward to a response.

Regards

John

---

### Post by Kellemora on 2008-12-18
Hi Max and Anda

Fonts are stored in /usr/share/fonts/truetype

if you look inside that folder, you should find a folder named msttcorefonts

It may not have loaded correctly!
Just delete the entire folder then type in terminal

```
sudo apt-get install msttcorefonts
```

and it should reinstall the package for you.

If you have installed any fonts manually, it's a good idea to double check that you do not have the SAME font installed in two different folder too.

TTUL
Gary

---

### Post by maxcomx on 2008-12-20
Thankx dude, at least i learned something about where the font are stored, but i solve the problem by reinstalling ubuntu 8.10, i anyways had few problem to fix, and it fix all at once.  And i will not reinstall that msttcorefonts...

cheers

---


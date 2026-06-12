---
title: "Problems Terminal, wine, etc"
date: 2011-12-22
forum: New to Ubuntu
---

### Post by Momof9Blessings on 2011-12-22
Hi,

Not sure what I did, but yesterday when I was installing wine when it was done (there was a page about fonts - I think) it said "ok" at the bottom, but I could not click anything.... It would not let me do anything, so I ended up closing it late last night....

This morning, I am trying to install GIMP (gave up on CS3 - since it won't install)....

I first went into Ubuntu Software Center (11.10 on 32 bit) and try to install GIMP - it wont get past "waiting for apt-get to exit"....

SO I stopped that and was trying to install thru the terminal - I get this message

"E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?" 

when I try this... sudo apt-get install gimp-data

Any ideas on what I need to do??? 

THank you!!!

---

### Post by oldos2er on 2011-12-22
Run ```
sudo dpkg --configure -a
```, when the license agreement comes up use Tab to highlight 'Ok' then Enter to accept.

---

### Post by Momof9Blessings on 2011-12-22
I got this message...

dpkg: error: dpkg status database is locked by another process

---

### Post by TeoBigusGeekus on 2011-12-22
> **Momof9Blessings said:**
> I got this message...

dpkg: error: dpkg status database is locked by another process

You probably have Software Centre or Synaptic open; close them and try again.

---

### Post by Momof9Blessings on 2011-12-22
I did have software center open....

this is what I get....

```
Setting up man-db (2.6.0.2-2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up wine1.3 (1.3.35-0ubuntu1~ppa1~oneiric1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing wine1.3 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 man-db
 wine1.3

```

---

### Post by Momof9Blessings on 2011-12-22
does man-db have anything to do with the server version???  

If it does....

A few days ago when trying to install ubuntu 11.10, 32 bit I accidently started doing the server version, not desktop.... when I realized it, I selected "quit installation"....

I then preceded to make the desktop cd and installed it (in the process it finally did a partition of my hard drive - I thought it would delete the server parts....) maybe it did not....

So if I need to reinstall ubuntu - I need the details on how to do this....

Right now, I only have Firefox (with my old bookmarks) and Thunderbird with emails...  I like to keep that info at least - so need instructions on how to save those....

Thank you

---

### Post by TeoBigusGeekus on 2011-12-22
Try 
```
lsof | grep config.dat
```
to see if a process is indeed using the file.

---

### Post by TeoBigusGeekus on 2011-12-22
> **Momof9Blessings said:**
> does man-db have anything to do with the server version???  

If it does....

A few days ago when trying to install ubuntu 11.10, 32 bit I accidently started doing the server version, not desktop.... when I realized it, I selected "quit installation"....

I then preceded to make the desktop cd and installed it (in the process it finally did a partition of my hard drive - I thought it would delete the server parts....) maybe it did not....

So if I need to reinstall ubuntu - I need the details on how to do this....

Right now, I only have Firefox (with my old bookmarks) and Thunderbird with emails...  I like to keep that info at least - so need instructions on how to save those....

Thank you

Just backup the .thunderbird and .mozilla folders from your home partition.
Once you reinstall ubuntu, install firefox and thunderbird, delete the above mentioned folders from the new installation and replace them with your backed up ones.

---

### Post by BC59 on 2011-12-22
Sometimes to unlock run:

```
sudo rm /var/lib/dpkg/lock   

#and then


sudo dpkg --configure -a
```

---

### Post by TeoBigusGeekus on 2011-12-22
^^^^^^^^^^^^^^^^^
Try this as well.

---

### Post by Momof9Blessings on 2011-12-22
> **TeoBigusGeekus said:**
> Just backup the .thunderbird and .mozilla folders from your home partition.
Once you reinstall ubuntu, install firefox and thunderbird, delete the above mentioned folders from the new installation and replace them with your backed up ones.

Would this remove the "server files"???  I was trying to find them, only a partial install....

I can't reformat the whole hard drive.... dual boot - plus I have all of my other files on it (500 gb)....  

I was trying to see if I could find them myself....  I did do the partial install from the boot / live CD (server)

---

### Post by Momof9Blessings on 2011-12-22
Well I did figure out how to reinstall Ubuntu.... just insert disc and click install - it will let you remove old ubuntu and reinstall it....

I also just finished installing GIMP - super easy.... hopefully that fixes everything else!!!

Thank you!!!

---


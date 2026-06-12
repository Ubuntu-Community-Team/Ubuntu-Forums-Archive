---
title: "Deamon tool"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by Dailydog on 2008-04-22
Hi

I've tried to install Deamon tool under wine, but that doesn't seem to work.

Does anyone know of an alternative to DT, that does work. I'd like to run some ISOs that are supposed to run in a Windows environment.

thx

---

### Post by aeiah on 2008-04-22
you dont need daemontools. linux can mount .iso images nativley. but, what is it you're actually trying to run on the .iso images? are they games that are supported by wine?

to mount an iso:
```
mkdir Desktop/iso/
sudo mount your.iso Desktop/iso/ -o loop
```

if your .iso file isnt in your home folder, then navigate to its location with the terminal first
```
 cd /the/path/to/your/iso
```

---

### Post by NightwishFan on 2008-04-22
There is a frontend for that command called gmountiso, its in the repos.

---

### Post by RJ Hythloday on 2008-04-22
> **NightwishFan said:**
> There is a frontend for that command called gmountiso, its in the repos.
 
Thank you! I've been wanting to see if a few kids games would run in wine. I ripped 'em to .iso to avoid loading the cd every time.

---

### Post by WakkiTabakki on 2008-04-22
These tools adds a context menu item to nautilus (so it assumes your using standard Ubuntu with Gnome) to mount and unmount iso-images...

Unpack the attachment and put the two scripts in your nautilus scripts folder (~/.gnome2/nautilus-scripts).

To use:
:: Mounting
Right-click on you image and choose Scripts/ISO-Mount

:: Unmounting
Alternative 1: Right click on the iso-image (NOT the mount on the desktop) and choose Scripts/ISO-Unmount
Alternative 2: Right-click on the folder /media/<name of your iso-image> and choose Scripts/ISO-Unmount



Why you can't simply right-click and choose Unmount on the mount on the desktop is beyond me (it's been mounted with the users option, so...). Does anyone know?


/N

---

### Post by Trail on 2008-04-22
> 
AcetoneISO2, is a feature-rich and complete software application to manage CD/DVD images. Thanks to powerful open source tools such as fuseiso, AcetoneISO2 will let You mount typical proprietary images formats of the Windows world such as ISO BIN NRG MDF IMG and do plenty of other things. Everything will be done inside a handy GUI.


[http://www.acetoneiso.netsons.org/](http://www.acetoneiso.netsons.org/)

---

### Post by marcusfurius on 2008-05-14
You could try [this application]("http://www.marcus-furius.com/?page_id=14"). It is designed specifically for Ubuntu, installs via a deb installer, has a simple to use GUI and mounts ISO, IMG, BIN, MDF and NRG Images, and doesn't require a password to mount images.

---


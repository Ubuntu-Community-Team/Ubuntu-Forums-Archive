---
title: "need more help"
date: 2013-03-09
forum: New to Ubuntu
---

### Post by jimv8673 on 2013-03-09
Ok i downloaded the 64 bit version of ubuntu it downloaded as a compressed file.  I made a folder named ubuntu and extracted all the files to that.  Now i need to burn a disk, do i burn that entire folder to the disk or what??

---

### Post by Mark Phelps on 2013-03-09
How do you know it downloaded as a compressed file?

The downloads are typically .ISO files -- which, if you did this in MS Windows, it sometimes thinks are archive files -- which they are not.

What you do is "burn" the ISO image to a DVD, using appropriate apps, or, if you want an bootable USB stick, you use something like PendriveLinux to load that image onto a USB stick.

---

### Post by mastablasta on 2013-03-09
no, that's not how you do it.

what OS do you have?

[http://www.ubuntu.com/download/help/burn-a-dvd-on-windows](http://www.ubuntu.com/download/help/burn-a-dvd-on-windows)

---

### Post by jimv8673 on 2013-03-09
OK,  I figured it out. i had to download a usb stick burner program, imported the entire compressed file to that, burnt the install to the usb stick, and installed it as a clean install.  Windows is history.  

Im actually using ubuntu firefox right now to respond.  I have a lot of checking out to do but so far it seems cool. :)  everything worked great with the install, i did have to f12 the boot so it would boot from the stick, but that went well obviously.

One more question though, at least for now,  :)   how do you keep the junk internet files etc. cleaned up??  im a clean freak, dont like a lot of junk useless files on my computer, plus all the midget porn LMAO (Not Really) :)

---

### Post by cIdde on 2013-03-09
Well, then, welcome to Linux! :)

What do you mean by 'junk internet files'? You mean the browser cache?
In Firefox you can tell it to clean up the cache files when closing the browser: Edit -> Preferences

Read all options. There are some settings for the browser history, for cookies and so on.

---

### Post by jimv8673 on 2013-03-09
On windows i used a program called crap cleaner to clean up any useless files such as temp, internet browsing history, it also had a registry cleaner etc.  is such a cleaner needed on ubuntu  or does this system even keep those files??  Just a good system cleaner i guess id what im talking about.

---

### Post by 3rdalbum on 2013-03-09
> **jimv8673 said:**
> On windows i used a program called crap cleaner to clean up any useless files such as temp, internet browsing history, it also had a registry cleaner etc.  is such a cleaner needed on ubuntu  or does this system even keep those files??  Just a good system cleaner i guess id what im talking about.

You don't need anything extra. Cache can be removed within Firefox. Temporary files are stored in /tmp which is emptied on startup. There is no "registry".

There is also the package archive, and "orphaned" packages you can remove. For instance, lets say you install a music player. The music player requires a library to read ID3 tags. When you install the music player, it also downloads the tag reader, and stores the package files in a package cache folder. That can be a waste of space.

If you remove the music player program, you will still be left with the tag reader library. If it is not required for any other installed programs, it is "orphaned" and could be safely removed, freeing up a tiny bit of space.

The apt-get command allows for both these kinds of cleaning up, just look in the apt-get manual when you have a bit more experience. Your computer wont run faster afterward but you might free up a small bit of disk space, that's all.

---


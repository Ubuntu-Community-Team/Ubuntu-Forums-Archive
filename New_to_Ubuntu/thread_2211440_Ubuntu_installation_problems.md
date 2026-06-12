---
title: "Ubuntu installation problems"
date: 2014-03-16
forum: New to Ubuntu
---

### Post by saidownloader on 2014-03-16
I'm an absolute newbie to Ubuntu and I'm trying to install Ubuntu because my Windows 7 home premium just fails to boot and I'm trying to access some files on my C & D drive. My C drive contains all windows files and also all my files and my D drive contains files for recovery.I downloaded the iso file of Ubuntu 13.10 on my Android tablet and burned it to the CD using my dad's laptop. However the installation failed and it said that an unrecoverable error has occurred. I had no idea what to do so I downloaded Ubuntu 12.04 and burned it to the CD. I was able to get to the desktop environment with the option 'Try Ubuntu without installation'. However the file manager crashed a lot of times while I tried to access my files, I couldn't find my d drive folder. I tried going to /media/ but none of the 4 folders
 had an important txt file which I stored on my D drive. Then I tried installing Ubuntu, however after the 'Install Ubuntu alongside Windows 7' option, my laptop just restarts and the same process continues after I try again. I googled about this problem and came across wubi.exe solution but my Windows 7 is not working so it doesn't apply to me.I don't know what to do anymore, I just want to access that one txt file on my D drive. Is there anything else I can do to install Ubuntu? 
Thanks for any support. 

I also tried installing Linux mint but it just failed to load it's desktop environment.

---

### Post by slooksterpsv on 2014-03-16
What are the specs of your machine? It sounds like you could potentially have bad memory in the machine. When booting from the live cd, does it give you an option to Test memory? If so run that.

---

### Post by saidownloader on 2014-03-16
Laptop details:
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02763304&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=5085297&query=LK826EA](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02763304&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=5085297&query=LK826EA)

Live CD does have an option to test memory but it takes way too long and I don't understand a thing that it's doing or showing me.Anyway I'm running it again right now, would take at least an hour to complete by guess. 

Also I would like to point out that when I'm accessing my files without installing Ubuntu, the screen would just go blank for a while and then it would reappear asking me for a password. Since I have not installed Ubuntu and I'm running it through the live CD, at that point all I can do is restart my laptop and hope for it to not appear again.

---

### Post by smuthavarapu on 2014-03-16
Sounds like hard disk problem to me. If you have USB 8GB, install ubuntu on USB and take the backup of all files.

Hard disk, Format, DeFragment etc.,

Might not be related, but worth a try.

---

### Post by saidownloader on 2014-03-16
I don't have USB 8 GB but I have backed up my important files of C drive on the SD card of my Android tablet by connecting it with USB. I still have one important file on my D drive which I'm not able to access as I've mentioned in my first post. I don't plan on reformatting my hard disk because if it's a hard disk problem, that wouldn't help and I plan to take my laptop to a professional(and I think he might be able to backup all my files and not just important ones) ... I came here as a last effort in saving my laptop myself.

---

### Post by Vladlenin5000 on 2014-03-16
Unless it's encrypted you can always backup that file on the secondary partition when running a live session, any live CD/DVD will do. Then - and only then - it's advisable to run the diagnostic tools provided by the HDD manufacturer (or boot from an Ultimate Boot CD - google it - which has all the diagnostics tools you'll ever need). As usual, start with the short test (just a few minutes) and if it passes then do the extended one (several minutes up to more than an hour depending on the size of the drive); if it passes the extended as well it should be safe - for the moment - to format and install whatever you like on it.

---

### Post by Impavidus on 2014-03-16
If the hard drive is OK, not encrypted and has no file system damage, you should be able to access it from the live disk. An installed Ubuntu system can't rescue any files that cannot be rescued by a live session too. In the file manager you'll see a list of available partitions, one of which will be the D partition. It won't be labeled as such. I think double clicking should mount it, or else right click and select mount from the menu.

Don't try installing Ubuntu on the drive from which you want to rescue a file. To install to have to resize the partitions, which may lead to further file system damage.

Edit: There is the possibility the live session doesn't run because it doesn't like your graphics card. You may have to add the nomodeset boot option. See [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) and scroll dow[SIZE=2]n to "How to enable kernel options on the livecd (before install)[/SIZE]".

---


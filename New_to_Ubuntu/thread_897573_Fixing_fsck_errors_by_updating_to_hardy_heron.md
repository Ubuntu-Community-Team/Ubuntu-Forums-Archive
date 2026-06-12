---
title: "Fixing fsck errors by updating to hardy heron?"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by speirint on 2008-08-22
Hi, I've been having issues with an fsck error #4, and my attempts to fix what's going on make me very squeamish every time I see options for overwriting and deleting inodes.  

I was using a dual boot of MSXP and Gutsy Gibbon by the way, and the computer was set to conserve energy (hibernate?) after about 15 minutes of non-use... this led to strange things happening and then a forced check tells me the drive and file system is corrupt or has errors.

I've since then downloaded Hardy Heron on CD and was wondering what would happen if I installed over Gutsy.  Would this safely bypass the file system error messages and make everything work again?

OR 

If I use the live CD to retrieve my data, how do I achieve root priveleges to copy my own data into a flash drive? I would like to back up some more of my data, and the fsck error prevents me from using ubuntu and logging in, as well as starting up the x. However, if I use a live cd, I found that I can mount my drives and copy some things out onto the desktop.

Is there a way to persuade my computer that I am its rightful owner in live cd?  I couldn't modify the data that's in the sda drives (copy, paste, etc.) while using the live CD. I thought it was because I wasn't logged in as root, but when I right clicked a folder to view its properties, the information that is shown says I don't own the computer, and therefore I cannot modify any of the files.




Here is the fsck thread (where my problem is still unresolved) that I posted in previously which may be of use for providing more background to the fsck exit status 4:

[http://ubuntuforums.org/showthread.php?t=367644&page=6](http://ubuntuforums.org/showthread.php?t=367644&page=6)

---

### Post by philinux on 2008-08-22
If you're getting regular fsck errors it could indicate a failing hard drive.

Have a look in /var/log/messages and see if there are any read or write errors.

---

### Post by speirint on 2008-12-06
I'm almost certain the hard drive is fine, the fsck error (#7 if I recall correctly) came about once I started using the hibernate feature on my computer.  It wasn't "waking" up correctly or would restart instead.  Unfortunately I don't understand Ubuntu well enough to fix it on my on, but it resulted in saying that there were too many blocks to be cleared and that the hard drive would have to be checked manually.  

I barely know my way around Ubuntu other than what I figure out from googling for similar problems and copying and pasting code to see if it works.  I'm not allowed to access the gdm until I finish checking or repairing something... it's been at least four months since I tried to do anything with Ubuntu.

If anyone can help with that I'd greatly appreciate it.

---

### Post by Herman on 2008-12-08
:) Hello speirint,
I am reading your posts in the other thread here, [http://ubuntuforums.org/showthread.php?t=367644&page=6](http://ubuntuforums.org/showthread.php?t=367644&page=6) , and I think I can help you at least get some of your files back, (nothing guaranteed) and maybe even fix it completely, but I'm worried you need to re-install, (or maybe not, a lot will depend on how lucky we are).

I have a few problems too when I try to use hibernate in some of my computers. In my Asus EeePC it works fine, but in my big computer I can't use hibernate either, it just shuts down on me (uncleanly). 
An 'unclean' shutdown is when the operating system doesn't have time to tidy up all the files it has open before it shuts down too quickly. There could be important files open that are half written to and they suddenly get deleted when the computer shuts down. If they happen to be important pieces of the jigsaw puzzle then we have problems, but a lot of the time we get away with it. You weren't so lucky this time, it seems.
It's not your fault either, we should be able to use 'suspend' or 'hibernate' to save electricity instead of leaving our computers running or shutting them all the way down.

Probably the easiest and best way to try to fix it now, (if it can still be fixed), would be to boot your Hardy Heron 'Desktop' Live/Install CD and go 'System'-->'Administration'-->'Partition Editor', and open GParted.
You will see a graphical view of your hard disk, with your partitions and file systems there.
Likely your Ubuntu partition will have a black rectangle around it to indicate it's not well.

Just right-click on it and click 'check', then click 'apply'.
A confirmation box will come up, just click 'apply' again to confirm.
GParted will run 'e2fsck -f -y -v' on it for you, which will be quite a lot more effective than just a plain fsck, and might fix it for you, with a little luck. 
Make sure you wait until the file system check is finished, it may take some time.

I'm not sure if it's fixable at this stage, e2fsck may need to unlink some files to the /lost+found I think, from what you have posted in the other thread.
The /lost+found directory is a folder which is one of the ones at the top level of our file system tree, so you should 'see' it if you can 'mount' the file system at all after the file system check is finished. We'll discuss how to rescue some of your files from the /lost+found later if we need to.
Try that first though, and maybe that will fix it, if it's still fixable. :)

Good luck, I hope that will clear it for you,
Regards, Herman :)

---


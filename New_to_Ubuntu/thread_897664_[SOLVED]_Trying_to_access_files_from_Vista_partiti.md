---
title: "[SOLVED] Trying to access files from Vista partition in Ubuntu"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by JCon on 2008-08-22
Hello everyone.

This is my first post (just registered) but I have been using this forum as a resource for the last little while. Thank-you to all who contribute to this forum that made it easy to switch to Ubuntu (on-going)

I am a complete noobie at Ubuntu and my computer language-knowledge is quite unsophisticated so please go easy on me. 

I have Vista and Ubuntu (8.04) installed on 1 HD. Vista first then Ubuntu. Recently my Vista has crashed. It won't boot. I have searched high and low, and ran the repair disk to no avail. At this point I will likely just re-install Vista for the few times that I plan to use. HOWEVER, I have a lot of photos 'trapped' in Vista.

Is it possible to access those files (to back them up or rescue them) from Ubuntu at this point?

And if so how?

I have searched this forum but am unable to find a thread that deals with my problem (directly).

---

### Post by Thelasko on 2008-08-22
> Is it possible to access those files (to back them up or rescue them) from Ubuntu at this point?
Yes, Simply run the LiveCD.  The LiveCD won't do anything to your HD (provided you don't run the installer) and you can then access your Windows HD and back it up to another form of media (a USB drive will probably be your best bet).  You may need a piece of software called ntfs-3g.  You can install it without touching your hard drive by opening the terminal and typing:
```
sudo apt-get install ntfs-3g
```
if you have an internet connection.

There is some information on [this page]("http://ubuntuforums.org/showthread.php?t=515690") about ntfs-3g and other Linux distributions designed specifically for system recovery (come with ntfs-3g on the disk).

---

### Post by JCon on 2008-08-22
Thank-you.

I have installed ntfs-3g and am proceeding. 

I will update shortly.

---

### Post by cybrsaylr on 2008-08-22
If you know where those pix are in Vista, linux will let you go into the Vista partition and then you can drag them all into your Ubuntu partition. I've been doing this all along with both pix and mp3 music files with no problems for quite awhile between windows and linux.

All I do is you in Places>Computer then find the Vista Disk and they are in there to be found.

---

### Post by JCon on 2008-08-22
Okay problem solved. The LiveCD suggestion Thelasko made was great.

I don't know why I didn't think of it on my own.

I ran the LiveCD which allowed me to 'look' at the files in Vista. After verifying that I could indeed see them, I logged back into Ubuntu (my installed version) to ensure my back-up HD was ready, and now my Ubuntu can 'see' the Vista files.

They are currently being backed up.

cybrsaylr - For some reason, I was not able to access any files in Vista initially. Recently Vista became 'unmounted' (through something I did obviously) and I could not access Vista at all. Running the LiveCD solved that issue (somehow).

---


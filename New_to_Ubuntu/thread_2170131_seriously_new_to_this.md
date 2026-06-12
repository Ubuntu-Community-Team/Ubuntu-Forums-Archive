---
title: "seriously new to this"
date: 2013-08-25
forum: New to Ubuntu
---

### Post by chris61 on 2013-08-25
i stumbled across this as my wifes external usb drive fell to the floor and windows no longer sees a volume on it.  The Bios does however... so i searched for a data recovery tool to help me pull the files off of it and I found Remix on ubuntu.  

I've been reading for the last 6 hours on this but for the life of me, i cant find simple stuff like, how to see what files are on a drive.. 
I'm booting off of a usb thumb drive ver. 12....  and I can make a dir in my home directory but if I move into that newly made directory I dont have permisions to create another.. I'm trapped.
I can't move to another device, "no permission".. ect... 

so as a seriosly new person, can someone point me to where i can find truely "newbie" information about navigating around the OS, copying files to a destination other than where I'm sitting.. stuff like that?

I've read all of the instructions this software has and the majority of them usually ends with Perissions denied

frustrated and desperate.. I know this is the solution, I can see the drive structure of /dev/sde1.. i see the size and make.. which is more that windows can see so I know i can recover the files .. if only i knew how to well.. look.

thanks 
chris

---

### Post by Crusty Old Fart on 2013-08-25
Please forgive me for being somewhat vague about what I've written here. I did something very similar to what you're doing many years ago and ran into the same problem. But, I cannot remember exactly how I got around it.
I know that the crux of the problem was not having full access. I also know that I was able to get the access I needed using a "chroot" command. I know this for certain because it was the only time I've ever used: chroot.

I'm hesitant to give you the exact chroot commands you need because I can't remember the details of its use enough to give you something that wouldn't risk permanent data loss. And, I don't have a way to duplicate your situation in order to test exact chroot commands.

However, since it appears that you are running Ubuntu from a thumb drive, perhaps that's similar enough to the old liveCD that I was using.
If that's right, then you can learn more about the chroot command by opening a terminal window and issuing the following commands:
```

man chroot
info coreutils 'chroot invocation'

```
Neither of those two commands should cause any problems. They just bring up the documentation for the chroot command so that you can learn a little more about it.
I really wish I had more experience with chroot to be more help, but I don't, so I can't.
This should get you started and perhaps give you something more specific to enter on search engines.

Good Luck,
Crusty

---

### Post by 3rdalbum on 2013-08-25
Okay, let's bring things back to basics.

When you boot from the USB drive, Ubuntu is just running in your computer's RAM. If you try to save any files to the Home directory, that's ONLY present in RAM and will be lost when you turn the computer off or reboot it. So you don't want to save your recovered files into the home directory.

What you need to do is boot from the USB and then plug in a USB flash drive or USB hard disk to save the recovered files to. Or, insert a blank CD/DVD and double-click it when it appears on the desktop, and drag your recovered files to it and burn the CD.

You can actually run Ubuntu from a CD and then use your blank USB to store the recovered files from the damaged USB, if you don't have three USB drives and three spare USB ports :-)

Your damaged USB drive, assuming it is readable, will appear in the sidebar on the left of the screen. Click it once to open it, you can then drag the files from it to the blank USB or to a blank CD (and click the Burn button!) to recover them.

**HOWEVER**: If the damaged USB drive became unreadable as the result of physical damage, it's highly unlikely that anything will be able to read it. If the drive became unreadable due to *data corruption* then I'd say there would be a chance, but for physical damage you'd be very lucky if any operating system can read the contents of the drive.

Good luck.

---

### Post by Crusty Old Fart on 2013-08-25
Seems to me that he also needs to mount the damaged USB drive if he can. And then do some chroot magic to get access to the files...just guessing.

I'll leave y'all with the following and then I'll get out of the way.

I did some poking around using the search phrase "access disks with linux livecd chroot"
I  found a few webpages that brought back a lot of memories. I forgot that  in order to access the drive that had my files on it, I had to "mount"  it first. After that, I could do what I needed with chroot.

Here are a couple webpages that may be helpful:
[http://www.cyberciti.biz/faq/ubuntu-mounting-your-encrypted-home-from-livecd/](http://www.cyberciti.biz/faq/ubuntu-mounting-your-encrypted-home-from-livecd/)
[http://www.cyberciti.biz/faq/centos-rhel-linux-mount-raid-hard-disk-from-livecd/](http://www.cyberciti.biz/faq/centos-rhel-linux-mount-raid-hard-disk-from-livecd/)

You're on the right track.

Good Luck

---

### Post by r_avital on 2013-08-25
Chris,

One thing you might want to try, before you get into chroot and so on.

If your damaged drive is readable at all, but it's not clear where to find it (3rdalbum's instructions should work, but just in case), you can do the following:

1. Hit Ctrl+Alt+L which will start a terminal (have no fear, no damage will be done here).
2. Enter the following:
```
ls -l /media
```
If your damaged drive is recognized at all, it will be visible under the /media directory.  Linux makes directories of all storage devices connected to the computer, and shows them under the /media folder.

If you're not comfortable using the terminal, launch the file-manager and click on "computer" which will show you all the directories from the top (root) level.  From there, you can double-click on the "media" folder and see if your drive shows up.  If it does, it should have some name familiar to you.

If you get this far, and the drive is showing, let us know, and we can then talk about recovering the files from it.

But like 3rdalbum said, if the damage is physical, only professional data recovery services will (or may) be able to recover the data.

Good luck!

---

### Post by eternal243 on 2013-08-25
> **Crusty Old Fart said:**
> Seems to me that he also needs to mount the damaged USB drive if he can. And then do some chroot magic to get access to the files...just guessing.

I'll leave y'all with the following and then I'll get out of the way.

I did some poking around using the search phrase "access disks with linux livecd chroot"
I  found a few webpages that brought back a lot of memories. I forgot that  in order to access the drive that had my files on it, I had to "mount"  it first. After that, I could do what I needed with chroot.

Here are a couple webpages that may be helpful:
[http://www.cyberciti.biz/faq/ubuntu-mounting-your-encrypted-home-from-livecd/](http://www.cyberciti.biz/faq/ubuntu-mounting-your-encrypted-home-from-livecd/)
[http://www.cyberciti.biz/faq/centos-rhel-linux-mount-raid-hard-disk-from-livecd/](http://www.cyberciti.biz/faq/centos-rhel-linux-mount-raid-hard-disk-from-livecd/)

You're on the right track.

Good Luck

Yes, if you want to access an internal harddrive from a live CD/USB you need to mount it first, but an USB stick should auto-mount when you plug it in to a USB port.

Having said that, and you don't have enough USB ports you could mount the internal harddrive of your PC, even if it has Windows on it, and then backup the files directly to your Windows. Although that is assuming you can read your USB stick at all. If the damaged USB mounts fine when you plug it in, you should be able to check it for damage, searching for damaged sectors and so on, although I don't know the command for that. Did something similar from a gentoo live cd when I tried to rescue information from my parents harddrive.

---

### Post by chris61 on 2013-08-25
thanks for all the replies.. 
from them I can make my situation more clear for you.... 

I dont have any graphical representatoin.. only text, so there is no "left side of your screen you will see a.. ".. I'm guessing i've loaded a terminal shell or something.

Per the instructions on the data recovery software Remix, I've removed the IDE drive from the USB external container and connteted it direct to an IDE cable.
I've also put another IDE drive in the machine which is larger than the damaged one .. (Damaged one is 100 Gig.. blank is 650.-- its all i had extra)..

Soooo.. How do I "mount" the destination drive so i can send the files to it?..

I can see the drives, as /dev/sde(1) and /dev/sdf(1) but I have no idea how to get permission to see the files on that drive.. I'm so close but ..

---

### Post by The Cog on 2013-08-25
You don't have a GUI? What version of linux did you put on that thumb drive? Not that it matters too much - assuming it's an ubuntu derivative, here's a go at doing it by command line:

First you need to become the root user, who has all rights to do anything. Enter the command
[COLOR="#880000"]**[FONT=Courier New]sudo -i[/FONT]**[/COLOR]
but if it's not an ubuntu derivative, you may need to do this command instead:
[COLOR="#880000"]**[FONT=Courier New]su[/FONT]**[/COLOR]
This should make your prompt change from a $ symbol to a # symbol. Now you are root. Being a live CD, you shouldn't need a password to do this.

Then you need to make a couple of directories (folders) where the disk contents will appear. Traditionaly this is in /mnt:
[COLOR="#880000"][B][FONT=Courier New]mkdir /mnt/drive_e
mkdir /mnt/drive_f[/FONT][/B][/COLOR]
Now you need to mount the drives into those directories you created:
[COLOR="#880000"][B][FONT=Courier New]mount /dev/sde1 /mnt/drive_e
mount /dev/sdf1 /mnt/drive_f[/FONT][/B][/COLOR]
Now you should be able to copy from one drive to another 
[COLOR="#880000"]**[FONT=Courier New]cp -rv /mnt/drive_e/. /mnt/drive_f[/FONT]**[/COLOR]
then unmount the drives before shutting down:
[COLOR="#880000"][B][FONT=Courier New]umount /mnt/drive_e
umount /mnt/drive_f[/FONT][/B][/COLOR]

---

### Post by eternal243 on 2013-08-25
> **The Cog said:**
> You don't have a GUI? What version of linux did you put on that thumb drive?
He is using Ubuntu, he stated that in his first post, and sometimes if there is a problem with the graphics drivers or display configuration the GUI won't load, it can happen in all linux distributions. In that case the system will load in a console. It is not much different at all from using terminal.

---

### Post by chris61 on 2013-08-25
i think i figured this out.. 
Thanks for the support thus far....
after taking in what you guys said, it seemed that the problem was :
a: total lack of knowledge in the terminal env..
b: inherent lack of permissions to do anything... 

So, once I figured that su is a nono for the novice, and that sudo gets you permissions needed to do stuff.. I got the recovery software to mount the IDE recovery drive, I changed directorys to the newly mounted drive and am now creating an image file of the damaged drive.

So. till i need more guidance, and I'm sure its coming.. I'm going to close this thread.

---

### Post by eternal243 on 2013-08-25
It's great that you got things working! Keep it up and refer to the MAN pages whenever you need help using the terminal. :)
Oh, and asking on the forum usually helps a bit as well. ^^

Take care and good luck!

---


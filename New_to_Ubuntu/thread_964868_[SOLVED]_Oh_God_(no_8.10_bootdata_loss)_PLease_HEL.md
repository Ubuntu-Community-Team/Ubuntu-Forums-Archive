---
title: "[SOLVED] Oh God (no 8.10 boot/data loss) PLease HELP!!!"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by Bee Wildered on 2008-10-31
I carefully followed the upgrade instructions from Ubuntu 8.4 to 8.10 yesterday on my main computer but cannot get it to work at all and I cannot now access any of my Thunderbird email archives now and these are VERY VERY important... OH MY GOD PLEASE HELP!!!

Upon boot up, 8.10 gets as far as accepting the username and password I had for the original 8.4 but then the screen just goes that light-coffe-coloured blank and the desktop will not load.

I've been a complete idiot, I know, as I did not back up my thunderbird email files or other data. I can view some of my ubuntu 8.04 hard drive files if I put the old ubumtu 8.04 disc in and boot from that but it will not let me access most of the files I need.

Is there any way I can fix this or even go back to the original 8.04 installation and retrieve my email and other files?

Thanks for any help and your patience!

B.

---

### Post by Elfy on 2008-10-31
Before you do anything else and end up losing the data - boot the livecd and you should be able to access the files.

---

### Post by RequinB4 on 2008-10-31
> **forestpixie said:**
> Before you do anything else and end up losing the data - boot the livecd and you should be able to access the files.

QFA.  You should be able to access ALL of your files from the liveCD.  What do you mean you can't get everything?  Remember you may have to click and mount one of your partitions via nautiulus file manager on the livecd.

Aren't your thunderbird email files located also somewhere else online ie gmail or hotmail, or are you running your own mail server?

also, what is your graphics card and what is the output of

```
lspci
```

on the livecd/

---

### Post by rustutzman on 2008-10-31
From the livecd ```
gksudo nautilus
``` Then you should be able to get to all your files. Remember to enable hidden files too.

Russ

---

### Post by Bee Wildered on 2008-10-31
Hi,

I don't have the live CD for Ubuntu 8.10 and I've already booted from my old 8.4 CD but it will not let me access many of the files I need as it says I do not have permission.

The most important file I need is the Thunderbird .default (archives/settings) file that's usually located in folders:
Application Data>Thunderbird>Profiles

Any further advice?

B.

---

### Post by redbob on 2008-10-31
After you got back your files, reinstall 8.10 with a manual Partition. I usually partition my disc by this way:
20gb to /root, 20gb to /home, 1gb to swap and the rest for /opt.
At your next upgrade, will just format /root partition, preserving your data, that is normally stored in home partition.
I use thunderbird since my Windows era (1 year ago), you can redirect you mail folders to opt partition. Its a good idea!!:)

---

### Post by djbushido on 2008-10-31
Also, you should be able to just do sudo nautilus, find the archive, and copy it to a flashdrive/thumbdrive, re-install, and import from that.

---

### Post by rustutzman on 2008-10-31
> **Bee Wildered said:**
> Hi,

I don't have the live CD for Ubuntu 8.10 and I've already booted from my old 8.4 CD but it will not let me access many of the files I need as it says I do not have permission.

The most important file I need is the Thunderbird .default (archives/settings) file that's usually located in folders:
Application Data>Thunderbird>Profiles

Any further advice?

B.

Did you use sudo or gksudo to launch nautilus?

---

### Post by redbob on 2008-10-31
.folders are hidden folders. Type Ctrl+H in nautilus to see then. If you could not have access to your files, open nautilus with sudo permissions:> gksu nautilus

---

### Post by Monotoko on 2008-10-31
The reason you cannot access them is because you werent running as root, use 

```
gksudo nautilus
```

---

### Post by Bee Wildered on 2008-10-31
Thanks folks,

I need to go offline to use my other system. I will try to sort things using your suggestions and let you know if I manage to resolve things.

Much appreciated.

B.

---

### Post by Bee Wildered on 2008-10-31
Hi,

I have now booted with Ubuntu live CD v 8.04 and used the gksudo nautilus command along with the show hidden files command on my other computer as recommended. I have good news and bad...

The good news is that I can now view the invaluable thunderbird archives/ settings folder/files hidden away in my botched upgrade from 8.04 to 8.10 that will not start up after accepting my passsword.

The bad news is the system will still not let me copy/back-up this Thunderbird folder and I desperately need to do this to save all my email archives before I reload Ubuntu 8.10. I can view the folder/files but when I try to copy it says I don't have permission to do this.

How do I get this permission? This data is crucially important to me and any help on this one will be greatly appreciated.

B.

:confused:

---

### Post by muteXe on 2008-10-31
Your archives can't be that invaluable if you choose not to back them up :(
Where are you trying to copy them to?  Memory stick?

Have a look at:
[http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html)

---

### Post by Bee Wildered on 2008-10-31
The file in question is nearly 3 gigabytes so I've tried both copying it to a slave hard drive and burning it to DVD as I don't have a memory stick with sufficient capacity.

The archives are really important to do with charity work stuff and I freely admit that I've been a silly and green computer user to not back them up. I guess I may be about to learn the hard way.

Your patience and help is appreciated,

B.

---

### Post by muteXe on 2008-10-31
Did you read the link about permissions? Did it help at all?

---

### Post by Jive Turkey on 2008-10-31
What happens when you type this into a terminal:

```
sudo cp /pathtoimportantfiles/* /pathtobackuplocation
```

...substituting of course the appropriate paths

if the gksu nautilus method wasn't working, try agian and make doubly sure you didn't involve a non-gksu window in the copying, and that the backup location was actually mounted.  It seems like you're having a permissions issue at this point.

---

### Post by Bee Wildered on 2008-10-31
Thanks folks, much appreciated,

I've printed off and am studying the file permission doc and will try out the command as per below.

B.

[http://www.comptechdoc.org/os/linux/..._ugfilesp.html](http://www.comptechdoc.org/os/linux/..._ugfilesp.html)

sudo cp /pathtoimportantfiles/* /pathtobackuplocation

---

### Post by Elfy on 2008-10-31
I would make sure that they have been unmounted first - right click the partition in nautilus and unmount, close nautilus.

Open a terminal and run ```
sudo fdisk -l
``` note which is the partition you need to access - it will be sdxy where it'll be similar to sda1

In the terminal, replacinf sdxy with partition noted above 
```
sudo mkdir /mnt/recovery
sudo mount -t ext3 /dev/sdxy /mnt/recovery
```

Open nautilus as root - ```
gksu nautilus
```

The path to the mozilla directory will then be similar to this in nautilus 
/mnt/recovery/home/username/.mozilla-thunderbird/strangenumber-default/mail

You should be able to copy it

---


---
title: "new ubuntu 12.04 install boots directly to windows xp"
date: 2013-03-11
forum: New to Ubuntu
---

### Post by newbiesteve on 2013-03-11
hello, I'm new to ubuntu and don't know very much about computers in general. I have tried to download ubuntu 12.04 from the ubuntu website and install it alongside windows xp in its own partition. I think it downloaded, I have a partition (d) 38.9 gb free space and 2.7 gb used during this download attempt. Now when I boot my computer it still goes directly to xp. It doesn't give me the option to boot my (d) partition. Shouldn't I see a screen that allows me a choice of partitions. Also, my bios boot priority says 1:usb hdd, 2:usb fdd, 3:usbcdrom, 4:ata hdd0, 5:pci lan . I'm not trying to boot from usb.n my usb drive, would it. I've been trying to do this for about 3 days now and could sure use some help.

---

### Post by Bashing-om on 2013-03-11
newbiesteve; Hi ! Welcome to the forum .

Sounds likely that ubuntu's boot loader (grub) did not install properly for some reason. Did you do the install from a CD/DVD or USB ?
As windows does boot up, how you have set the boot devices' priority is not a factor at this time.
When we know what your install medium is we can advise further on a means to check the hard disk's partitions and check/install grub. - You will be going into the install medium's "live mode" to do this.
[INDENT=3]will'n to help

[/INDENT]

---

### Post by newbiesteve on 2013-03-11
Thanks for the responce. I'm downloading from the ubuntu website. I have a disk that I got along with a ubuntu12.04 magazine that I bought, but my think pad doesn't have a disk drive.

---

### Post by Impavidus on 2013-03-11
> **newbiesteve said:**
> hello, I'm new to ubuntu and don't know very much about computers in general. I have tried to download ubuntu 12.04 from the ubuntu website and install it alongside windows xp in its own partition. **I think it downloaded, I have a partition (d) 38.9 gb free space and 2.7 gb used during this download attempt.** Now when I boot my computer it still goes directly to xp. It doesn't give me the option to boot my (d) partition. Shouldn't I see a screen that allows me a choice of partitions. Also, my bios boot priority says 1:usb hdd, 2:usb fdd, 3:usbcdrom, 4:ata hdd0, 5:pci lan . I'm not trying to boot from usb.n my usb drive, would it. I've been trying to do this for about 3 days now and could sure use some help.

If you still see your D: partition (with the downloaded file), then Ubuntu was not installed. Furthermore, you are unsure about your download. I am too, as 2.7GB is too much for the Ubuntu installer and not enough for a wubi install (which you don't want). The .iso file is about 700MB.

Anyway, I understand you assume you downloaded some .iso file and stored it in a 41.6GB partition, known to windows as D:. At the very least you have to run the installer, and if you had done so you wouldn't have doubted you downloaded the .iso correctly. So, you have downloaded either the 32 or 64 bit version of Ubuntu 12.04 from ubuntu.com. Next step is to burn this .iso file to a dvd or usb. In case of a dvd make sure you select to burn as an image, not as a file, or the boot code will not be correctly stored on the dvd. Exact procedure depends on the burner you use. In case of a usb, have a look here: [http://www.psychocats.net/ubuntu/usb](http://www.psychocats.net/ubuntu/usb). Have you done this?

Next, plug in the usb or dvd, reboot and make sure you boot from the usb/dvd. You can run a live session, check if everything works and install on your D: partition. It won't be known as D: in Linux. You can select "something else" in the 9th screenshot in the following link and select the correct partition to install (tricky if you're not experienced with partitions) or simply move all files from the partition and delete the partition from windows and tell the installer to install alongside windows. This should work flawlessly and keep all your documents, but make backups nonetheless. Good instructions can be found here: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing). Have you done this?

Next it should work. At the very least the partition on which you installed Ubuntu should no longer be recognised by windows. If you still don't get to Ubuntu something has gone wrong with the boot loader.

---

### Post by bcbc on 2013-03-11
See this: [http://askubuntu.com/questions/75314/ubuntu-not-showing-up-on-boot-menu-after-wubi-installation]("http://askubuntu.com/q/75314/14916")

---

### Post by newbiesteve on 2013-03-11
To Impavidus: thanks for the info. This is the first time I remember hearing or seeing anything about UNetbootin. I'm trying it now. I would have thought that the ubuntu.com  download would have covered this. Maybe I just missed it. Anyway, thanks. I hope it works. If it doesn't I'll take a look at "askubuntu" that bcbc mentioned. I'll probably look at it anyway.

---

### Post by newbiesteve on 2013-03-12
I got ubuntu 12.04 installed on a flash drive using UNbootin. Many thanks. However, I am not able to view any video online. I tried to download Adobe  from the software center and got the error "items cannot be installed or removed until the package catalog is repaired. do you want to repair it now ? I chose yes and got another message that said "failed to load the package list". I could use some more help here. Should I start a new thread for this.

---

### Post by Bashing-om on 2013-03-12
newbiesteve; Glad ya got ubie installed.
As this is a separate issue do start another thread, will get more response that way, and keeps the forum a bit more tidy (one situation to one thread). In the new thread advise how you installed and the exact error you are getting.
Please mark this thread as solved: The current method ->
> Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button.
Problem still ? -> graphical instruction:[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)[INDENT=2]my best regards

[/INDENT]

---


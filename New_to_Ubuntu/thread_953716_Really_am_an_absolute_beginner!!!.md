---
title: "Really am an absolute beginner!!!"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by danmelad on 2008-10-20
I really am - an absolute beginner to Linux and Ubuntu!!  I have a problem with a laptop using Win XP SP2.  Laptop worked fine up until a few weeks ago when it would only go to a black screen when started up.

Tried all sorts of things, managed to get all of the files and pics off and then went to do a format - which took absolutely ages to do (several hours).  To no avail, the machine appeared to go through a format and eventually didn't get anywhere.

Have now formatted several times - it sometimes gets to the desktop but then whenever you click on anything - it can take 20 to 30 minutes to do somenting - anything!!  Have tried starting in Safe Mode but it just doesn't get there.

A friend in another forum suggested getting rid of Win XP and install Ubuntu Linux - I went to the link given and downloaded the file (700mb of it) and got it onto a disc.  Now - what do I do next?  It appears to be an ISO file which doesn't boot when laptop started - what next?  Do I need to get to the DOS prompt - which I have tried to do but just can't seem to get to it.

Anyone got a solution - in real laymans terms - as I am at a loss as what to do next!!

Regards,

Tony

---

### Post by Thelasko on 2008-10-20
You burned the iso incorrectly.  Follow [these instructions.]("https://help.ubuntu.com/community/BurningIsoHowto")  The iso file is a [disk image]("http://en.wikipedia.org/wiki/Disk_image"), it's kinda like a .zip file.  You need a special program put the image on the CD.

If you still can't figure it out, you can use [shipit,]("https://shipit.ubuntu.com/") but it will take a while.

---

### Post by roger_1960 on 2008-10-20
Hi

Possibly it doesnt boot because the laptop is not set to boot from CD 1st.  You need to get into the BIOS settings and change the boot order.  Normally, shortly after power on you have to hit F2 (or F8 or F12 depending on your machine - often a message flashes on the screen telling you which). You should get a screen which you can navigate with arrow keys and which allows you to change the boot order to put CD first.  The save and exit and reboot.

Having said all that, what you are describing would suggest that your hard drive may need replacing....

---

### Post by phidia on 2008-10-20
Do you have the laptop bios set to boot from cdrom 1st?

That's something you want to check, and you should also verfiy the download by checking the md5sum and comparing that with the official md5sum.

---

### Post by bcom on 2008-10-20
Based on what you have said, you might consider the possibility that the hard drive in your laptop is failing.  Installing Ubuntu on a failing hard drive will not fix or help anything in the long run.  

I'm not sure what you mean when you said you got the image to a disc.  The ISO image must be burned to a CD as an ISO image, not a bootable disc.

Here is a link to a Windows-based program that will enable you to burn an ISO image to a disc: [http://www.imgburn.com/](http://www.imgburn.com/)

In order to boot from the ISO image you need to set the computer's bios so that it can boot from the CD/DVD drive.

The BIOS set up is accessed by hitting the F2 key repeatedly just after you turn the computer on.

Also, FYI, the latest service pack for XP is 3.

---

### Post by redseventyseven on 2008-10-20
OK, what you need to do first is to burn the ISO image *properly* to the CD.

The .iso file is what's called a CD-image. It's like a snapshot of all the data that's supposed to be on the CD. However, this means that you actually have to write the data that's stored in the image to the CD, otherwise you'll just have a CD with the file on it (with the data still trapped inside) which is useless.

Try looking at these google results for some help: [http://www.google.co.uk/search?q=iso+image+file](http://www.google.co.uk/search?q=iso+image+file)

Once you've got your CD properly burnt, then the process should be straightforward. You may have to press a key (usually Del or F2, depends on the manufacturer) when you first switch your computer on to tell it to look for a bootable disk in the CD-ROM drive, but it sounds (from your original post) like you're knowledgeable enough of Windows computers to know what you're doing here.


One last tip: try to avoid generic topic titles. This is so that people can easily see what the thread is about and have an idea as to whether they'll be able to help or not!

Best of luck, and I hope you enjoy your linux experience!

---

### Post by Thelasko on 2008-10-20
> **bcom said:**
> The ISO image must be burned to a CD as an ISO image, not a bootable disc.
Is it just me, or does that sound backwards?

---

### Post by phidia on 2008-10-20
> **Thelasko said:**
> Is it just me, or does that sound backwards?

The raw image or iso will be bootable provided you have checked the md5sum, burned it as an image (not data) and your bios is set to boot from the optical drive.

See the iso burning guide [here]("https://help.ubuntu.com/community/BurningIsoHowto").

---

### Post by ugm6hr on 2008-10-20
Do a quick bit of reading on this website: [http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

However, the fact that Windows would not boot at all, despite a fresh reinstallation does suggest a hardware problem.

---


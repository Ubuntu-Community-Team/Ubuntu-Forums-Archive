---
title: "Downloaded UNetBootin, now what?"
date: 2013-06-12
forum: New to Ubuntu
---

### Post by TNFrank on 2013-06-12
Ok, so I downloaded it to my desktop, I open it with PyPar2 and have no clue as what to do from there.  All I'd like to do is make a bootable USB with Linux Mint 13 Xfce on it so I can check it out.  I don't want ot make a bootable install USB, just something so I can check out other Linux distros without messing up my Ubuntu on my hard drive.  I could really use some help here. :(

P.S.
Thanks, awesome job giving this "noob" some help. ;)

---

### Post by slickymaster on 2013-06-12
[How To Create a Linux Live Bootable USB Stick using UNetbootin]("http://www.mytechguide.org/7818/create-linux-live-bootable-usb-stick-using-unetbootin/")

---

### Post by TNFrank on 2013-06-12
Thanks, I'll read that link over and see if I get anything out of it. 
I"m starting to see what it feels like when I Talk Over folks heads about Hot Rods or Firearms,LOL.  To me both are second nature and when I tell folks about an engine I've mod'ed or loading ammo they give me a kind of "lost" look. Seems like the ol' shoe is on the other foot here, ya'll talk Linux Terminal like it's a second language but for me it's still hard to understand so I have that "lost" look on my face wondering why I can't understand it all. Of course the obvious reason is because I'm new to it all and I'm sure I'll catch on eventually but until then I need baby steps. Anyway, thanks again. ;)

---

### Post by TNFrank on 2013-06-12
Ok, it says "after installing UNetBootin", does that mean after I've downloaded it to the desktop or what?  Do I need to go to my Software Center in Ubuntu and do an "install" now?

Ok, never mind, I just went to the software center and did an "install" and now I have it locked into my dock.  Time to give it a try, thanks.

---

### Post by slickymaster on 2013-06-12
> **TNFrank said:**
> Thanks, I'll read that link over and see if I get anything out of it. 
I"m starting to see what it feels like when I Talk Over folks heads about Hot Rods or Firearms,LOL.  To me both are second nature and when I tell folks about an engine I've mod'ed or loading ammo they give me a kind of "lost" look. Seems like the ol' shoe is on the other foot here, ya'll talk Linux Terminal like it's a second language but for me it's still hard to understand so I have that "lost" look on my face wondering why I can't understand it all. Of course the obvious reason is because I'm new to it all and I'm sure I'll catch on eventually but until then I need baby steps. Anyway, thanks again. ;)

Well, truth is that no one was born knowing it. For us all it's a process of learning, and a trial and error one. I'm sure if you frequent this forum often enough in no time you'll start to catch up, and soon you'll also be as fluent in Linux as you already are in the subjects you mentioned.

---

### Post by Cheesemill on 2013-06-12
You don't need to download anything yourself, that's not how we install software in Ubuntu so first of all delete whatever you've downloaded.

Then install UNetBootin by using the software centre (or clicking [here]("apt://unetbootin")).
Once it's installed run it by hitting the SUPER key (the Windows key) and searching for UNetBootin.

You can then choose the OS you want to put on your USB stick by either selecting it from the drop down list or if you have already downloaded the ISO file then click on 'Disk Image' and browse for your downloaded file.

Select your USB drive from the drop down box and then click OK to create your bootable drive.

---

### Post by TNFrank on 2013-06-12
WhooHoo, it worked.  I'm coming to you in Linux Mint13 Xfce from my USB sdg drive.  This is UberCool, now I can test out distros of Linux without messing with Ubuntu. 
Ok, one more "stupid" question, can I put multiple Op Systems on a single USB drive with UNetbootin or just one at a time?  I'd like to see what WattOS would run like on my 'puter.  
Also, Big, Huge THANKS to slickymaster for helping me out here. :KS

Also, another quick question, will the USB drive have a persistant file on it so that any upgrades or changes I make to Mint 13 will stay?

---

### Post by C.S.Cameron on 2013-06-12
I have not been able to do a multi install with UNetbootin, it installs to the first partition on a flash drive only.

UNetbootin should have an option for making a persistent install.

If not you can do it by hand.
This is how I made a Unetbootin install to flash drive persistent.
Booted Live CD, (Live USB should also work)
Plugged in target flash drive.
Started Partition Editor
Created 1GB FAT32 partition, (on the left side of the bar).
Created a 2GB ext3 partition to the right of this, labeled it "casper-rw".
Created a ext2 partition in the remaining space and labeled it "home-rw".
Closed Partition Editor.
Un-mounted and re-mounted flash drive.
Started Ubuntu, started Unetbootin, selected Diskimage, located the iso, selected Type = USB Drive, selected correct drive letter
Pressed OK, waited 5 minutes.
When Unetbootin finished ran "gksu nauilus", opened filesystem / cdrom and then opened syslinux.cfg with text editor.
Added "persistent" as shown below:
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent
Rebooted, changes were persistent.

---

### Post by TNFrank on 2013-06-12
They is an option that says "Space used to preserve files across reboots" but I'm not sure how to use it.  I thought that would be the area where you'd store files so you'd get some persistance.  I set it to 8MB on a Peppermint One install on my 32GB USB drive.  Peppermint One works ok until I go to the install updates portion at which point it runs out of space to install the updates.  I KNOW I have more then enough space. I'm formatted in FAT(i.e. FAT32??) which should let me use as much of the USB as I need( or is it only 4GB as I read on another web site) but still, Peppermint only takes up a bit less then 500MB so I should have plenty of room. 
 I'd really like to get this figured out now that I've got it working this much. It'd be nice to be able to take it all the way and have another Op System I can run on my computer without having to actually install it onto the hard drive. 
 Any ideas of what I should set the Space used to preserve files across reboots at, low, high, in the middle some where? 
Ya'll have helped me get this far, let's take her all the way now and get this thing tweaked in so it's perfect. :guitar:

---

### Post by TNFrank on 2013-06-12
Ok, I went from 8GB in the "Space used to preserve files across reboots" up to 16GB and I almost got all the updates done before it told me there wasn't any space left.  The file info shows my hard drive(58GB) and then it's saying that the USB drive is 17GB(which it's actually 32GB). I wonder if I shouldn't just go for broke and give it say, 28GB to play with which will leave just over 3GB for the 500MB op system to play with.  Guess it's worth a try, I'll report back and let ya'll know how things turn out.

---

### Post by monkeybrain2012 on 2013-06-12
> **C.S.Cameron said:**
> I have not been able to do a multi install with UNetbootin, it installs to the first partition on a flash drive only.

UNetbootin should have an option for making a persistent install.

.

I think persistence is an option only for Ubuntu.

---

### Post by monkeybrain2012 on 2013-06-12
Multisystem has many more options than unetbootin. I made several multiboot live usb with it. But I think if you have several OS's install you can only make one to be persistent, though it has been a while so you may now be able to do more.

[http://liveusb.info/dotclear/?pages/Pr%C3%A9sentation](http://liveusb.info/dotclear/?pages/Pr%C3%A9sentation)

---

### Post by TNFrank on 2013-06-12
Peppermint One looks to be an off shoot of Ubuntu. Still, why am I running out of room when i do an update?  For gosh sake, I'm giving it 24GB of space.

---

### Post by C.S.Cameron on 2013-06-12
Do not do updates on a Persistent drive, the kernel is in a write protected file.
The largest size for a file in a FAT32 file system is 4GB and doing updates quickly eats this up.

You might want to consider doing a Full install to flash drive instead.

---

### Post by TNFrank on 2013-06-12
See the new thread I started for more info. Used Startup Disk Creator in Ubuntu 12.04 to install Peppermint One onto an 8GB USB, did updates and everything and it worked just like I had it installed onto the hard drive.  Ubuntu put the answer to my question right in front of me and I didn't even see it.  For fun I'm going to see if I can find a really small distor(Damn Small Linux maybe) and put it onto a 256MB USB that I have just to see if it'll run from something that small. LOL. Oh well, got it figured out and working.

---

### Post by C.S.Cameron on 2013-06-13
Tiny Core and Puppy should both work on a 256MB drive.

---

### Post by TNFrank on 2013-06-13
Tiny Core is like what, 10MB, that's almost nothing adn Puppy is 101MB, still small but I couldn't get Puppy to find my WiFi so it was a no go for interweb connection and I'm not up to par enough on how to manually config the connection.   I just like the name, "Damnsmall", LOL, ya' got to love it and it's only 50MB.

---

### Post by slickymaster on 2013-06-14
Since you are experimenting, why don't you give [Bodhi Linux 2.3.0]("http://www.bodhilinux.com/index.php") (only 128 MB), [SliTaz]("http://pplware.sapo.pt/linux/slitaz-um-linux-com-35-mb-que-corre-em-48-mb-de-ram/") (only 192 MB) and [Linux Slax 7 Green Horn]("http://pplware.sapo.pt/linux/chegou-o-linux-slax-7-green-horn-com-apenas-210-mb/") (only 210 MB) a try ?

Bodhi Linux is a Ubuntu based semi-rolling distro and in my opinion is one of the most beautiful Linux distro out there.
SliTaz is distributed on LiveCD (USB), and the .iso only takes 35 MB. It provides a complete and very functional graphical environment, based on LXDE and Openbox.
Slax is Slackware based, with the KDE graphical environment, recompiled with the lowest number of possible dependencies.Slax is based on Slackware, with the KDE graphical environment, recompiled with the lowest number of possible dependencies.

---


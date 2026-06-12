---
title: "Ubuntu on 8GB USB stick, will files/apps be saved? Is it good for carry around purpos"
date: 2012-09-06
forum: New to Ubuntu
---

### Post by Amii on 2012-09-06
Hi! 

Will Ubuntu on a 8GB USB stick for the following purpose? 

I need Ubuntu for a programming class and I'd like to install apps and store files. Will the apps and files be saved when I remove the USB Stick? 

I don't carry my laptop all the time but I do carry my USB stick around. 

Thanks :KS

---

### Post by AgentZ86 on 2012-09-06
Yes, just be sure to allow some space when you create the startup boot disk

During creation it will have a small slider for you to select how much space you want to use for files / applications etc. 
Assuming your using ubuntu 12.04 or something just press the super key, and type startup, and you will see the startup disk creator

OH but first you have to be sure you have the current downloaded copy of ubuntu iso of your choice before running the startup disk creator.

And make sure the copy your planning to use will work on your computer. In otherwords don't use the 64bit version if you are not sure that all computers that you plan to use this live usb stick on will actually be 64bit machines or it won't work.

32bit version likely will work on anything and won't have a problem on 64bit machines and I don't believe it will suffer any performance issues either since the usb flash will already be slower then running from a hard disk.


It's really pretty cool
Hope this helps

---

### Post by Amii on 2012-09-06
@[AgentZ86]("http://ubuntuforums.org/member.php?u=54003"), 

Wow! Thank you so much for super fast response. I came back to add more details and already a response! ^^ 

My current USB stick is created using the Universal USB Installer from Pen Driver or something like that. When the USB is plugged in, I have different options. One of the option is Run Ubuntu from the USB. Will that work for my purpose? Or do I need to set up my USB differently. I think I came across a few threads when I was searching earlier. 

Thank you for your help!!! :)

Yea. It is really cool if I manage to get it to work out :D

---

### Post by Paddy Landau on 2012-09-06
When you install Ubuntu onto your USB, you'll be given the option of having "persistence" (I'm not sure if the Windows installer gives that option; I'm not at my computer so I can't check). Choose the largest value it will allow.

Be aware that a USB stick is *much* slower than a native installation, so give *plenty* of time when installing apps, and especially if you are running the updates.

---

### Post by gjp578 on 2012-09-06
Thanks for asking. I also realised this problem just weeks before and I also used pendrive universal installer to make usb sticks. 

I think I missed the 4. Step to set up the flash memory size for the persistance files. 
See this website. there are fotos for every step on how to make a persistant usb stick
[http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/](http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/)

---

### Post by oldfred on 2012-09-06
If you have 8GB, you have enough space for a full install if you want.

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

With grub2 persistent C.S.Cameron 12.04
[http://ubuntuforums.org/showthread.php?t=2042965](http://ubuntuforums.org/showthread.php?t=2042965)

Large persistent - C.S.Cameron post 6 & 7
[http://ubuntuforums.org/showthread.php?t=2041679](http://ubuntuforums.org/showthread.php?t=2041679)

---

### Post by Paddy Landau on 2012-09-07
> **oldfred said:**
> Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)
There has been a change since that was written, because you *can* run updates on a persistent USB.

---

### Post by Cheesemill on 2012-09-07
> **Paddy Landau said:**
> There has been a change since that was written, because you *can* run updates on a persistent USB.
Mostly, yes.

You can't do kernel upgrades on a persistant installation though.

---

### Post by AgentZ86 on 2012-09-07
> **Amii said:**
> @[AgentZ86]("http://ubuntuforums.org/member.php?u=54003"), 

Wow! Thank you so much for super fast response. I came back to add more details and already a response! ^^ 

My current USB stick is created using the Universal USB Installer from Pen Driver or something like that. When the USB is plugged in, I have different options. One of the option is Run Ubuntu from the USB. Will that work for my purpose? Or do I need to set up my USB differently. I think I came across a few threads when I was searching earlier. 

Thank you for your help!!! :)

Yea. It is really cool if I manage to get it to work out :D


Yes that will work but as others indicated you need to select (NO Persistance) as shown on the link
[http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/](http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/)

However, if you are doing this from a ubuntu machine you could easily use the built in startup disk creator as well.

When you go to the ubuntu download pages it has the instructions for this right there too.

Then you simply select the amount of space you want for programs and files etc. and your all set.

---

### Post by C.S.Cameron on 2012-09-07
> **Paddy Landau said:**
> There has been a change since that was written, because you *can* run updates on a persistent USB.

You can run updates on a persistent install but they will quickly fill the USB stick and once filled it will not boot.

Edit:

If you are using a large drive, (32GB), with a large casper-rw partition for the Persistent install, then updates may not be a problem. Especially if computer janitor is used between updates.

---

### Post by bullfrog13x4 on 2012-09-07
i use a 4gb usb stick i created from the windows usb installer as you have mentioned,, i use mine to show my friends what lunix looks like (most of them have never seen any lunix distro) i have added a few programs directly to the usb drive and set it up they same as my laptop,,, i have gparted and cairo dock with compiz fusion and unity.. i have "converted" most of my friends from windows over to lunix with this usb stick,,,  i have been successful in upgrading it from within its self ,, as in i was booted in to the usb on a friends computer and upgraded it from there,, i have also been able to install into there computers from that same usb stick,, there are only 2 things that get annoying,,,  1 is it is only 4gb (not much room) and 2 it is VERY slow....

 my friends were amazed that i could run a full os from a small usb stick and they all immediately wanted there own copy,,  i have one friend that is in college for programming and he took his 16gb usb setup the same way to class and his professor was so impressed that my friend ended up installing lunix into his professors personal computer

 this is really a great way to introduce the newbie to lunix,, especially ubuntu

 keep up the great programming,,,   ubuntu ubuntu ubuntu ,,,,,    p.s. i run 12.10 alfa 3 on this usb with only a few issues that were easy to overcome, with a little help from the ubuntu community..

:D:D

---

### Post by I2k4 on 2012-09-07
I've been using the Pendrive installer to create Persistent Live USB installs to try out Linux versions for about a year and a half, and here's my wisdom:

- The Persistent Live USB install works great at first, and will save all your changes to the OS, but all of these installations have gone "wonky" after a few weeks of routine use.  The usual problems are that it suddenly demands passwords that do not exist, or suddenly fails to recognize and mount the computer's hard drive (you have to manually "mount" the hard drive on every reboot by clicking it in the File Manager.)  _The "Peristent Live" USB is great for experimenting but is eventually unreliable_ and simply not a substitute for a full, regular installation.  This is not a problem with Ubuntu, per se, but with the unnatural Persistent Live USB set up.

- To make Persistent Live USB last longer, do not update the operating system, ever, and when doing software installations or updates, don't try to force the slow USB to handle more than one or two apps (with dependencies) at a time.

- There is a way to do a regular "full install" on a USB drive, by directing the Ubuntu installer to the USB during the regular install process.  There is one serious danger in this which is, instead of installing GRUB (the boot loader) on the USB it will install on the hard drive.  Once that is done, it is not easy to get rid of it, and GRUB will appear instead of the ordinary Windows boot sequence whether you insert the Linux USB drive or not.  _So my warning on the "full install to USB" option is do your Google homework, and be sure to have GRUB installed on the USB drive_ and not your hard drive.

Hope this is useful.  I've learned a lot about various verions by using Persistent Live USB but would not confuse it with a full install.

---


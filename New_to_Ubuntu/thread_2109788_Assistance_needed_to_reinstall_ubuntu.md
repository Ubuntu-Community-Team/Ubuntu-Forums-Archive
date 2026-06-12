---
title: "Assistance needed to reinstall ubuntu"
date: 2013-01-28
forum: New to Ubuntu
---

### Post by JGwen on 2013-01-28
Hi, I have an Acer Aspire one D255.
 
When I bought it, it had that cut down operating system on it which took ages to load up and didn't have any useful applications. So a contact at the time loaded ubuntu. It rang for quite some time without an problems but of late has started to lock up. 
 
It has started locking up while in use. It completely locks up, will not respond to Cntl, Alt, Del or the power button. The only way to clear it is to remove the cable and battery, and do a complete restart. Last time I used it, it locked up 5 times in 2 hours.
 
I have read a few posts on here recommending reinstalling Ubuntu, but they pointed people to the documentation, which is a bit sketchy for a novice. If I follow the instructions to create a USB memory stick to install Ubuntu, will booting up with the USB stick in the Acer start the process to clear out the previous installation and replace with the new?
 
Are there any other tests I should do first to look for hardware failure? All suggestions and information welcome, but please supply the answers at a level of information suitable for someone who hasn't played with changing the OS system on a PC before.
 
Thanks

---

### Post by Mark Phelps on 2013-01-28
Seriously doubt that reinstalling is going to fix an intermittent lockup problem.  Those are generally caused by (1) overheating (in which the CPU gets too hot) and (2) failing hard drive (in which case the drive appears to sieze up).  Neither of these is a software problem.

You can generally tell if the laptop is getting too hot just by feeling how warm it gets. It's a good idea to confirm that the laptop fan comes on and that the vents are cleared of gunk.

Hard drives, especially those in laptops, will fail over time.  If you can boot from a CD, you can try running that way for a while to see if the laptop still locks up.  But, if your netbook has no CD drive, you would have to go to the trouble of making a LiveUSB and running from that.

Does it lock up sooner if it's being heavily used? Or does it not matter?

---

### Post by frank604 on 2013-01-28
Let's do two things at once. 1) test if the lock up is due to faulty hard drive/overheating, 2) reinstall ubuntu.

First of all, we need to download ubuntu.  I recommend 12.04 LTS 32bit desktop for your netbook. [http://www.ubuntu.com/start-download?distro=desktop&bits=32&release=lts](http://www.ubuntu.com/start-download?distro=desktop&bits=32&release=lts)

Then we need to prepare the usbstick as a usb installer for ubuntu.  Read the following guide. [http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu)
In the past I had problems with this app.  But give it a shot first.

You will need to learn how to choose boot device preference (cd/hard drive/usb/etc) in bios.  In my asus eee 1005ha it is pressing ESC key at the bootup splash screen when I just power my device on.  Then selecting the usb drive.

So, to test if it is your hard drive failing, boot into ubuntu 12.04 LIVE.  Play with it for a bit.  Browse the net, etc.  If it locks up during your live playaround, it is from overheating as Mark states in previous post.  If it doesn't lock up, continue to install.  When you boot into your installed ubuntu 12.04, if it locks up then we know it is your hard drive failing as per Mark's comments.  If all else is good, you are good to go.

I do not know if Mark is correct in his analysis of your problem.  But I'm using it as a reference point for my above statements.

---


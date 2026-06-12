---
title: "[SOLVED] how do i run a virtual machine"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by hazman on 2008-06-13
how do i run a virtual machine ? is it in synaptics and which is best? never tried it in fact never heard of it until changing to ubuntu[which is great]

---

### Post by philinux on 2008-06-13
I installed virtualbox from their website. [http://www.virtualbox.org/](http://www.virtualbox.org/)

4 days ago. I've now got a virtual machine with Intrepid on it. Bit of a learning curve but not too hard.

You need to read the pdf and download the right version .deb

I'm on 64 bit.

---

### Post by forestpixie on 2008-06-13
There are a few - some you can get in the repos. I however use virtualbox from their site - or at least Sun's now. Find it's easy enought to get the hang off. There is a virtualisation forum - which has a few useful stickies

[http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

[http://www.virtualbox.org/](http://www.virtualbox.org/)

Once you've got it installed properly - install your os in it and you are off.

---

### Post by ukripper on 2008-06-13
I agree virtualbox is fairly easier to use and learn than VMware

---

### Post by mwjones on 2008-06-13
I also recommend VirtualBox, and am running it in Kubuntu 8.04.  It should be available in Synaptic, mine was installed via **apt**:

```
sudo aptitude install virtualbox-ose virtualbox-ose-source
```

From reading other docs, it turns out that sometimes the kernel modules break when the kernel image upgrades.  [One of the bug comments]("https://answers.launchpad.net/ubuntu/+source/virtualbox-ose-modules/+question/33296") had instructions for building the modules:

```
sudo aptitude install build-essential module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i virtualbox-ose
sudo /etc/init.d/vboxdrv restart
```

VirtualBox has been running smoothly so far (knock on wood).

---

### Post by Joeb454 on 2008-06-13
I install VirtualBox from their website too, though not the Open-Source-Edition :)

It works fine, though as mentioned above, I do have to reconfigure the kernel module after a kernel update :)

---

### Post by Victormd on 2008-06-13
Use virtualbox, but don't get the OSE because that one lacks USB support. Download from their [website]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI"). The install is pretty straight forward. Once done, all you do is allocate some space for a virtual HD (size will vary depending on OS, i.e., for windows, use 5GB+), setup the video memory and RAM usage for the virtual OS, and then start the virtual machine. It's pretty cool, you'll see a computer booting within ubuntu, and you can simply put in a CD for the OS you want to install, and tell the virtual machine to boot from that CD and then install as you would normally... :)

---

### Post by Bradtek on 2008-06-13
The Virtual Box in Synaptic is the Open Source Edition.
Although it works very well, It doesn't have USB support 
and some other features.

Read about the differences here
[http://virtualbox.org/wiki/Editions](http://virtualbox.org/wiki/Editions)

Download the Closed Source version from here
[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

---

### Post by Victormd on 2008-06-13
Just thought I'd show off some of the things you'll be getting... :)
(lame... I know... but I'm feeling "fancy" today... hahahahahaha)
(Note on the first screen shot, windows is on the left face of the cube and ubuntu is on the right and on the second screen shot I have the Windows taskbar at the bottom and the ubuntu panel at the top of the screen...)

---

### Post by hyper_ch on 2008-06-13
if you want to do networking... like running services on the virtual machine and stuff that you want to have accessible from the outside then I'd rather use vmware... I think networking there is a lot simpler...

however vbox is total opensource, lighter and it has a nice seamless mode.

---

### Post by hazman on 2008-06-13
how do you get it working i can see it any where after downloading and installing

---

### Post by Joeb454 on 2008-06-13
It should be in Applications &#8594; System Tools :)

---

### Post by hazman on 2008-06-13
no its not there have idone something wrong during download or install.found the folder for it in my home folder under usr/share/virtualbox

---

### Post by forestpixie on 2008-06-13
You might need to reboot - but before you do that make sure you are in the vbox users group.

Open Users and groups in the Admin menu, unlock it, then manage groups - find vbox users, then properties and make sure you enable your user.

---

### Post by hazman on 2008-06-13
re-installed it and now its there thanks to all that helped i knew i'd get the answer here

---

### Post by forestpixie on 2008-06-13
You'll always get an answer eventually - even if it's sorry :)

---


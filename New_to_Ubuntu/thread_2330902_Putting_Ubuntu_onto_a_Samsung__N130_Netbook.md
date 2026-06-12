---
title: "Putting Ubuntu onto a Samsung  N130 Netbook"
date: 2016-07-16
forum: New to Ubuntu
---

### Post by DaleD55 on 2016-07-16
Morning

I am new to this forum so please bear with me

I have a Samsung N130 Netbook which is running Windows XP - it is running very slowly and I would like to put Ubuntu onto it

Is there a specific version that i need to use and if so how do I go about loading it

Thank you in advance for any help

Dale

---

### Post by uNoubu8a on 2016-07-16
Hi,

I would suggest checking out [Lubuntu]("http://lubuntu.net/") as it is a very light variant of Ubuntu using the LXDE desktop environment.
How to get [Lubuntu]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu").
How to make a [bootable USB from an ubuntu ISO]("https://help.ubuntu.com/community/Installation/FromUSBStick"). (Just keep in mind that the name of the ISO you will download will differ from the ones mentioned in this how-to).


Happy Ubuntuing.

---

### Post by grahammechanical on 2016-07-16
Do you know the hardware specification of the machine? According to this web page it has an Intel Atom N270 CPU.

[http://www.trustedreviews.com/samsung-n130-review](http://www.trustedreviews.com/samsung-n130-review)

And according to this web site the Intel Atom N270 is a 32 bit CPU.

[http://ark.intel.com/products/36331/Intel-Atom-Processor-N270-512K-Cache-1_60-GHz-533-MHz-FSB](http://ark.intel.com/products/36331/Intel-Atom-Processor-N270-512K-Cache-1_60-GHz-533-MHz-FSB)

That means that you will need a 32 bit version of whatever flavour of Ubuntu you decide to install. The 32 bit version of Lubuntu will have i386 as part of the name. Whereas the 64 bit version will have amd64 as part of the name. 

You should install the very latest version which is 16.04. It was released April 2016. The number is the year & month of release. Lubuntu 16.04 is given security support until 2019. Here is the Lubuntu installation guide

[https://help.ubuntu.com/community/Lubuntu/InstallingLubuntu](https://help.ubuntu.com/community/Lubuntu/InstallingLubuntu)

Regards

---

### Post by DaleD55 on 2016-07-16
Thanks for the advice so far

I have downloaded the 32 bit version on to a USB stick but when I put it into the Samsung an error message comes up saying Windows does not recognise this file - anyone any ideas please

---

### Post by uNoubu8a on 2016-07-16
OK... I am not sure if this will be frowned upon but I already linked in my first post the way to "burn" the ISO you downloaded unto a USB (copying it doesn't work).  For more assistance you can[ have a look at this video using Rufus]("https://youtu.be/z5ZTGIrjBsU") (a windows application) to do this. (This video is for an earlier version but the gist stays the same).

Once you have a bootable USB drive you need to reboot your PC and select the USB thumb drive as the boot medium.  This will vary from PC to PC.  Just look for prompts when your PC boots up (you might have to go into the BIOS and set the USB as the first Boot device).

---

### Post by DaleD55 on 2016-07-31
Thanks for the advice - I have managed to sort out the bootable USB drive and loaded it onto the Netbook
At the end of the install it asks me to restart which I do - at this stage when restarted I get a black screen with the following at the top

''/dev/sda1: clean, 121491/9707520 files, 1251910/38812672 blocks''

Nothing else will happen whatever key I press

Thanks in advance

---


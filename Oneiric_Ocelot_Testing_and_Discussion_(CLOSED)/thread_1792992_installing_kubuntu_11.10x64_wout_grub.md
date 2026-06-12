---
title: "installing kubuntu 11.10x64 w/out grub"
date: 2011-06-28
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by 13east on 2011-06-28
I already have natty installed on my machine and would like to install the next development version of ubuntu, but would like to keep my current grub setup untouched.    

I've read elsewhere that this can be done w/ the alternative-cd but can't seem to find one for 11.10.

How do I install 11.10 w/out installing grub that seems mandatory when running the setup w/ the live media that is available?

---

### Post by cpatrick08 on 2011-06-28
> **13east said:**
> I already have natty installed on my machine and would like to install the next development version of ubuntu, but would like to keep my current grub setup untouched.    

I've read elsewhere that this can be done w/ the alternative-cd but can't seem to find one for 11.10.

How do I install 11.10 w/out installing grub that seems mandatory when running the setup w/ the live media that is available?
the alternative cd for kubuntu can found at [http://cdimage.ubuntu.com/kubuntu/daily/current/](http://cdimage.ubuntu.com/kubuntu/daily/current/)

---

### Post by oldfred on 2011-06-29
Use manual install and choose to install the boot loader to the same partition. Grub should not be installed to a partition but the PBR is not used for anything so it is a throwaway.  One of the choices should be just not to install.

Then boot Natty and run this to find you install

sudo update-grub

If you do not want to update grub with every kernel change but want to boot the most current one add an entry to 40_custom that boots the partition using the link in /:

from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition.

menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

---

### Post by 13east on 2011-06-29
> **oldfred said:**
> Use manual install and choose to install the boot loader to the same partition. Grub should not be installed to a partition but the PBR is not used for anything so it is a throwaway.  One of the choices should be just not to install.

Then boot Natty and run this to find you install

sudo update-grub

If you do not want to update grub with every kernel change but want to boot the most current one add an entry to 40_custom that boots the partition using the link in /:

from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition.

menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

I was planning on using Grub-Customizer GUI to update grub from Natty after installing Oneiric but using the DesktopCD it gave me no option to not install GRUB.  I wasn't sure how installing GRUB to the same partition would affect my system so choice not to do that.  

Downloading the AlternativeCD right now, but I'm not sure what you mean by "Use manual install..."; is that w/ the Desktop- or AlternativeCD? and how do I accomplish that?

---

### Post by cariboo on 2011-06-29
> **13east said:**
> I was planning on using Grub-Customizer GUI to update grub from Natty after installing Oneiric but using the DesktopCD it gave me no option to not install GRUB.  I wasn't sure how installing GRUB to the same partition would affect my system so choice not to do that.  

Downloading the AlternativeCD right now, but I'm not sure what you mean by "Use manual install..."; is that w/ the Desktop- or AlternativeCD? and how do I accomplish that?

The manual partitioning option will give a choice of where to install grub.

---

### Post by oldfred on 2011-06-29
Yes with Natty they changed manual install to "something else". Not sure about alternative installer as it is the old fashioned text based installer. It should be better.

---

### Post by 13east on 2011-06-29
> **cariboo907 said:**
> The manual partitioning option will give a choice of where to install grub.

It gives you an option to either install it to the MBR or one of the hard-drive partitions... but no option if you don't it installed at all.

> **oldfred said:**
> Yes with Natty they changed manual install to "something else". Not sure about alternative installer as it is the old fashioned text based installer. It should be better.

Will there be an option to choose not to install GRUB at all during that installation with the alternativeCD?

---

### Post by cariboo on 2011-06-29
What difference does it make if you chose to install grub to the partition you installed on, as long as it isn't on the mbr of the first hard drive, it won't be accessed.

Grub is a part of the default install, so even if you don't install it, it will be installed during an update. It would be better to install it where you want, instead of it being install automatically, and possibly being installed in the wrong place.

---

### Post by 13east on 2011-06-29
> **cariboo907 said:**
> What difference does it make if you chose to install grub to the partition you installed on, as long as it isn't on the mbr of the first hard drive, it won't be accessed.

Grub is a part of the default install, so even if you don't install it, it will be installed during an update. It would be better to install it where you want, instead of it being install automatically, and possibly being installed in the wrong place.

I just wasn't sure what it would do if I installed GRUB into the same installation partition. I like my machine setup the way it is and didn't want to mess with... like I've done so many times in the past.  Although its not too big a deal even if I did since I've learned the hard way to keep my installation partition separated from my storage drive so a quick reinstall would fix my problems w/out losing any data.  But it would be a pain to do so.

Thx for the info... will try it this way and see what happens.

---

### Post by 13east on 2011-06-29
> **cariboo907 said:**
> What difference does it make if you chose to install grub to the partition you installed on, as long as it isn't on the mbr of the first hard drive, it won't be accessed.

Grub is a part of the default install, so even if you don't install it, it will be installed during an update. It would be better to install it where you want, instead of it being install automatically, and possibly being installed in the wrong place.

Installing GRUB on the same installation partition overwrote my MBR.  What's funny is that it didn't install a clean MBR on top of the old one pointing to the new installation, it just messed up the MBR so as I had no way to access the machine and gave me a GRUB no access error.  

Luckily my boot folder is on a seperate 140 MB partition that was easy to restore to the MBR from the LiveUSB.

---

### Post by seeker5528 on 2011-06-30
> **oldfred said:**
> One of the choices should be just not to install.

Not saying it shouldn't be an option, but personally I don't know why you would choose not to install, I would say it should always be installed to the partition and the MBR should be optional unless you click on some advanced link/button to see more options.

Having it installed to the partition instead of or in addition to the MBR gives you extra options if something goes wrong, where the boot disks ([RIP](http://www.tux.org/pub/people/kent-robotti/looplinux/rip/) for example) that give you an option to choose a partition to boot from on their boot menu have something to pass the boot too.

[System Rescue CD](http://www.sysresccd.org/Download) includes Super Grub, which should work in those situations too by finding the kernel and giving an option to boot it, but my first choice would be to pass the boot along to the Grub provided with the distribution so you can use it's boot options.

Later, Seeker

---

### Post by seeker5528 on 2011-06-30
> **13east said:**
> I was planning on using Grub-Customizer GUI to update grub from Natty after installing Oneiric but using the DesktopCD it gave me no option to not install GRUB.  I wasn't sure how installing GRUB to the same partition would affect my system so choice not to do that.

To select/de-select locations to install grub to after the fact run ```
sudo dpkg-reconfigure grub-pc
```

So if Grub is installed on '/dev/sda', then once you have de-slected that as a location to install to in Oneiric, you can boot into Natty and do ```
sudo grub-install /dev/sda
``` to have that version written to the MBR.

Later, Seeker

---


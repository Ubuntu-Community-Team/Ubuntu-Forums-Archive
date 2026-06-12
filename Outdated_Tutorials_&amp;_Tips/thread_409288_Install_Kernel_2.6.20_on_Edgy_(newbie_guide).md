---
title: "Install Kernel 2.6.20 on Edgy (newbie guide)"
date: 2007-04-14
forum: Outdated Tutorials &amp; Tips
---

### Post by edmondt on 2007-04-14
I decided to install a newer kernel last night on my Edgy and I would like to post this how to just to make it easier :)

**First Step - Install Some Software**
Install Envy (This is make it easier to install video card driver after the reboot)
[IMG]http://albertomilone.com/images/buttonenv64.jpg[/IMG]
[http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.1-0ubuntu4_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.1-0ubuntu4_all.deb)
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install Grub Edit (This is really good, and it gives you a GUI for setting your boot option)
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=26273&d=1172614020[/IMG]
[http://ubuntuforums.org/showthread.php?t=228104](http://ubuntuforums.org/showthread.php?t=228104)

**Second Step - Get and install Kernel**

I am going to copy and paste this howto from [http://www.linuxmonitor.net/blog/tag/howto](http://www.linuxmonitor.net/blog/tag/howto) for this which includes a patch for desktop optimization:

1). Open up a terminal
2). Make yourself root if you are not already:
```
sudo -s -H
```

3). Enter these commands one at a time:
```
apt-get install build-essential libncurses-dev kernel-package
cd /usr/src
wget http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.20.tar.bz2
cd /usr/src
tar -xjf linux-2.6.20.tar.bz2
cd linux-2.6.20
```

Now lets apply the Con Kolivas patches, these are patches designed to improve system responsiveness with specific emphasis on the desktop, but suitable to any workload.

```
wget http://www.kernel.org/pub/linux/kernel/people/ck/patches/2.6/2.6.20/2.6.20-ck1/patch-2.6.20-ck1.bz2
bzcat patch-2.6.20-ck1.bz2 |patch -p1
```

Copy the current kernel config and configuring the kernel

```
cp /boot/config-`uname -r` .config
make menuconfig
```

In “**General Setup**” activate:
- Support for paging of anonymous memory (swap)
- Support for prefetching swapped memory

In “**Processor type and features**“:
- Processor family Choose the model of your processor.
- set **Preemption Model **to **Voluntary Kernel Preemption** (Desktop)
- High Memory Support
- off - if you have less than 1 GB of RAM
- 1GB Low Memory Support - if you have 1GB of RAM
- 4GB - if you have more than 1GB of RAM
- set Timer frequency to 1000 Hz

In “**Kernel hacking**” uncheck “**Kernel debugging**“.

Now exit and save the configuration.


*Making the new kernel package:*

```
make-kpkg clean
```

The following command will take ages to complete, I am not sure when mine finished because I did it last night, but others say it take around 3 hours to compile the kernel:

```
make-kpkg -initrd --revision=386 kernel_image kernel_headers modules_image
```

When you're finished you should have some deb file in /usr/src ready to be installed...
*Installing the new kernel:*

```
cd ..
dpkg -i *.deb
```

Now your new kernel should be installed, but you're not ready for a reboot yet...

Open Grub Edit (Should be in System, Administration, Grub Edit) and select change default OS, select your new kernel, "Ubuntu, kernel 2.6.20-ck1" hit ok and you can now reboot..

Write this part down or something, because when you boot you will not be able to go into GDM for most people, the video card driver installation is needed.

1). hit CRTL+ALT+F1 after the fail message, login as root
2). type envy -t
3). install your video card driver nvidia or ati...
4). when finish, type /etc/init.d/gdm restart or hit CRTL+ALT+DELETE and reboot.

Everything should be running now :) I hope it feels faster than before and I would like to quote this final step from [http://kmandla.wordpress.com/2006/11/11/howto-set-up-edgy-for-speed/](http://kmandla.wordpress.com/2006/11/11/howto-set-up-edgy-for-speed/)

> 
**Last steps**

There are two more things you can do with your system, and really they should be done last, when everything is in place.

First, grab that DSL or Ubuntu live CD you started with, and reboot your machine again. Open a terminal window and enter these commands.

    sudo e2fsck -fD /dev/hda2
    sudo e2fsck -fD /dev/hda4
   *Note*
   Mine was just: sudo e2fsck -fD /dev/hda1


This will reoptimize the root and home directories, and can take a little while to finish.

When it’s done, reboot and press escape when you see the Grub boot menu. Edit the topmost option and add this word at the end of the boot line

```
profile
```

Press return to finish editing and then b to boot that line. Your system will reprofile itself on this boot (and this boot only), and successive boots should be faster.

All done

That’s it. Reboot a final time and see how it goes. If you have any ideas or problems, feel free to tell about them.


I hope this guide is useful to some :) Everything feels faster for me when everything was done...

---

### Post by Ace2016 on 2007-05-07
Cool how to, can you add bootsplash to it? its better than usplash since you get more colours

[EDIT]
Nvidia users, don't compile nvidia framebuffer support into the kernel and modify your /etc/X11/xorg.conf or download the nvidia drivers from nvidia before rebooting, and check on nvidia's site if your chipset is supported by nvagp, if not compile agpgart and the driver for your chipset into the kernel

---

### Post by eschatologicalhumor on 2007-07-30
Thanks for this successful tutorial. It contains something essential that was left out either intentionally or unintentionally from all other tutorials of this matter (even though 99.9% of them are exact copies of this one), which was to:

$sudo -s -H

BEFORE you proceed. So thank you for that.

I had an issue that I am hopefully working out with the help of the Con Kolivas mailing list members, which is that if you are running WINE, be sure to have these settings in the menuconf:

3G/1G user/kernel mem split 
and
1GB highmem

My WINE install complained about it, so I had to recompile an entirely new patched kernel, which is currently being turned into a .deb at this moment.

Hope I'm right, and hope this helps.

---


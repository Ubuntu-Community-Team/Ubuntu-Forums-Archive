---
title: "Unable to boot Ibex - it's almost as if it wasn't there.."
date: 2008-11-26
forum: New to Ubuntu
---

### Post by Cynically on 2008-11-26
So I decided to take the plunge today and installed Ibex onto my laptop. Beforehand, using Vista's partitioner, I created a 10 gb partition and used the continuous free space option to install Ubuntu. Based on advice from a friend, I opted not to install the included boot loader. After what seemed to be a successful install, the computer rebooted into Vista. I was glad to see that Vista was still safe, but it never gave me the option to boot into Ubuntu. There's no boot menu, it just goes straight to Windows. Going to Vista System Properties -> Startup and Recovery  shows Vista as the only operating system, and even when I check the box to show operating systems for x seconds, it still doesn't come up. 
Any tips? Should I install the Grub boot loader and rewrite it with the Windows loader, and how would I do that? (I'd rather not keep the grub loader.) I really wanna play with my new OS... but I can't get to it, and I'm not even sure it's there! Any help would be appreciated.

[edit] Ok, I just noticed that my clock on Vista was changed... when installing Ubuntu it asked me to pick my time zone, and changed my time. I guess that means it's definitely there?

---

### Post by caljohnsmith on 2008-11-26
> **Cynically said:**
> So I decided to take the plunge today and installed Ibex onto my laptop. Beforehand, using Vista's partitioner, I created a 10 gb partition and used the continuous free space option to install Ubuntu. Based on advice from a friend, [COLOR="Blue"]I opted not to install the included boot loader[/COLOR]. After what seemed to be a successful install, the computer rebooted into Vista. I was glad to see that Vista was still safe, but it never gave me the option to boot into Ubuntu. There's no boot menu, it just goes straight to Windows. Going to Vista System Properties -> Startup and Recovery  shows Vista as the only operating system, and even when I check the box to show operating systems for x seconds, it still doesn't come up. 
Any tips? Should I install the Grub boot loader and rewrite it with the Windows loader, and how would I do that? (I'd rather not keep the grub loader.) I really wanna play with my new OS... but I can't get to it, and I'm not even sure it's there! Any help would be appreciated.
If you decide not to install Grub, then yes, you will just continue to boot into Vista on start up. :) Since you don't want to use Grub on start up, you could instead use [EasyBCD]("http://neosmart.net/dl.php?id=1") to add Ubuntu to your Vista boot menu. But in order to use EasyBCD to boot Ubuntu, you should go ahead and install Grub with Ubuntu, but just install Grub to the boot sector of the Ubuntu partition instead of the MBR (Master Boot Record); you can do that by clicking on the "advanced" button in the last stage of the installation, and have Grub installed to /dev/sdaX or whichever is your Ubuntu partition (for instance /dev/sda2). Then you can easily use EasyBCD to add Ubuntu to your Vista boot menu via [these instructions]("http://neosmart.net/wiki/display/EBCD/Ubuntu"). If you need more specifics, let me know, but that's the general idea. :)

---

### Post by Keen101 on 2008-11-26
To be honest i really don't know why you are reluctant to install the GRUB bootloader. You can always put the windows MBR later.

use this disk to "restore" GRUB. The disk also functions to restore the windows MBR.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by Cynically on 2008-11-27
Perfect. Thanks Cal. I'm writing this from inside Ubuntu now. =] 

And Keen, the reason why I'm so reluctant to install grub is that my friend told me a horror story about him uninstalling Ubuntu, and the uninstallation took the boot loader with it, causing windows to be unable to boot and giving him a headache, and I got paranoid.

Anyways, problem solved, thanks for your inputs. =]

---

### Post by caljohnsmith on 2008-11-27
> **Cynically said:**
> Perfect. Thanks Cal. I'm writing this from inside Ubuntu now. =] 

And Keen, the reason why I'm so reluctant to install grub is that my friend told me a horror story about him uninstalling Ubuntu, and the uninstallation took the boot loader with it, causing windows to be unable to boot and giving him a headache, and I got paranoid.

Anyways, problem solved, thanks for your inputs. =]
Glad that worked OK. There's certainly nothing wrong with using Vista's boot loader to boot all your OSes, but don't feel shy about using Grub as your boot loader if you want to; if you ever uninstall Ubuntu, you can reinstall a Windows MBR in just a few minutes so that you will be back to the way you started, i.e. booting Windows directly on start up. Fortunately, it is easy and simple to do, and there are even multiple ways you can do it. Anyway, glad you have it working, cheers and have fun with Ubuntu and Vista. :)

---


---
title: "Messed up Ubuntu 14.04 reinstallation - eliminated Windows partition"
date: 2014-12-12
forum: New to Ubuntu
---

### Post by d93espinoza on 2014-12-12
Hi, I decided to install Ubuntu 14.04.1 this morning on my Lenovo laptop, and upon initial installation, I was able to successfully dual boot Ubuntu and the Windows 8.1 that came with the laptop. However, I ran into some internet connectivity problems later in the day and attempted to reinstall Ubuntu, and now my Windows partition is gone (there is no GRUB menu when I turn on or restart my laptop, and I cannot find the old partition when I boot to USB again and try to reinstall Ubuntu). I fortunately have the large majority of my files that I need saved on an external hard drive, but now I'm wondering if there's any way I can get my Windows 8.1 back on my laptop along with all the other files that I did not save to my external HD. I not only wish to recover my files, but the OS as well, but I am not sure if this is possible. I've searched the web and most results tell me to use Testdisk, but I am not clear if I have to use another hard drive for that tool, and if that would even allow me to get my Windows 8.1 back. Thanks!

---

### Post by nerdtron on 2014-12-12
> However, I ran into some internet connectivity problems later in the day  and attempted to reinstall Ubuntu, and now my Windows partition is gone

How did you reinstall? What option did you choose when you are installing Ubuntu again?

---

### Post by oldfred on 2014-12-12
If testdisk finds old partitions, it will show those. Only if it finds partitions and show files will it then let you copy files to another drive. If you have to use Photorec then you need another drive.
But since at least part of drive was overwritten it is very doubtful that a working system can be recovered. Any file that is now missing will corrupt system.
That is why vendors suggest writing the DVD image set when you purchase system. Some will offer that set for just a nominal charge, others do not.

       Reinstall says overwrite Ubuntu but it also erases existing Windows or any other partitions.
Sept 2014 Fix being released for one drive installs, but multiple drive installs must use Something Else. And fix is not in current versions.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

---

### Post by Kale_Freemon on 2014-12-13
I made this same mistake when I installed Ubuntu on my Mac. I erased the OS X partition. I couldn't really do anything about it since I didn't have backup, and it's almost certain that the Ubuntu install overwrote at least part of the OS X partition. Haven't been able to reinstall OS X since then. Haven't really even tried lately either.

Unfortunately, you'll probably need to install a fresh copy of Windows. But it should be possible to recover some of the files you need as long as they haven't been overwritten yet. You may want to do this from a live cd/dvd or USB though to help avoid overwriting the data and making it unrecoverable.

---

### Post by d93espinoza on 2014-12-13
> **oldfred said:**
> If testdisk finds old partitions, it will show those. Only if it finds partitions and show files will it then let you copy files to another drive. If you have to use Photorec then you need another drive.
But since at least part of drive was overwritten it is very doubtful that a working system can be recovered. Any file that is now missing will corrupt system.
That is why vendors suggest writing the DVD image set when you purchase system. Some will offer that set for just a nominal charge, others do not.

       Reinstall says overwrite Ubuntu but it also erases existing Windows or any other partitions.
Sept 2014 Fix being released for one drive installs, but multiple drive installs must use Something Else. And fix is not in current versions.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

Bummer, I had a bad feeling about doing the reinstall that way, I should've read up on it instead of being so rash :/. So I would need another drive for testdisk, correct? And I would only be able to recover my files, not necessarily the Windows 8.1 OS?

> **Kale_Freemon said:**
> I made this same mistake when I installed Ubuntu on my Mac. I erased the OS X partition. I couldn't really do anything about it since I didn't have backup, and it's almost certain that the Ubuntu install overwrote at least part of the OS X partition. Haven't been able to reinstall OS X since then. Haven't really even tried lately either.

Unfortunately, you'll probably need to install a fresh copy of Windows. But it should be possible to recover some of the files you need as long as they haven't been overwritten yet. You may want to do this from a live cd/dvd or USB though to help avoid overwriting the data and making it unrecoverable.

So if I did install a fresh copy of windows, it would somehow recover the files? Or would I need to find the correct partition that has the files and do some sort of snooping around to find them...

---

### Post by JeQhdMD on 2014-12-13
So . . , if you try to re-install win8, you'll likely hose linux (ubuntu) . . so be prepared for that happening.   

Another option, you can, if you have a system with decent ram (probably 6 gb, 8 is better) install Oracle's Virtual Box in Ubuntu (use the Ubuntu Software Center), and then re-install windows 8 there.   That way your Ubuntu install is still functional, and you have a Windows install available as a software switch via the virtual machine.  Only downside to that is if you're a gamer, running high-end games in a virtual machine is a non-starter.

---

### Post by Mark Phelps on 2014-12-14
> So if I did install a fresh copy of windows, it would somehow recover the files?  No

> Or would I need to find the correct partition that has the files and do some sort of snooping around to find them...

Yes -- and since these were Windows filesystem files, you would do better using a Windows data recovery app.  But that would mean connecting your drive to a working Windows PC, installing the app, and doing the data recovery there.  A free data recovery app is "recuva"; the best commercial one is RecoverMyFiles, which is free to install and try out, but requires a license to do the actual recovery.

---

### Post by oldfred on 2014-12-14
Your Windows license key is now in the UEFI and only applies to the OEM copy you had installed. If you can get another DVD set from the OEM vendor you can reinstall that. Otherwise any install of Windows will require a new license.

 Product key now in UEFI/BIOS
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c)

---


---
title: "Full Disk Encryption + retain MacOS?"
date: 2023-03-20
forum: New to Ubuntu
---

### Post by spacegarbage on 2023-03-20
I have an early 2017 12" MacBook (Intel i5). It's not my main computer, so I'm willing to tinker a bit.


I haven't tried Linux/Ubuntu in over 10 years, so I wanted to give it a try on the MacBook. But, I want to have Full Disk Encryption, as I do with all my machines. To my knowledge, that requires wiping out the disk, including MacOS.


If I do that, will I be able to recover MacOS easily? I'm not a tech expert, but I can't really think of a way that you could only encrypt one partition...but if that's possible in a dual-boot situation...I guess that'd work too.

---

### Post by MAFoElffen on 2023-03-21
If you install encryption straight from the installer, using guided, yes, it will take your full hard disk. Before you do that, take a backup of your System, to be restored later.

You could approach this a bit differently, and be creative. I can think of two different ways to have a dual-boot with both Ubuntu and MacOS...

Method #1, Do a fresh install of Ubuntu 22.04.2 Desktop. Install as encrypt. Let it take over the disk. After the install, use a GParted on the Ubuntu 22.04.2 liveUSB boot disk and shrink the main system partition. 
RE: [https://help.ubuntu.com/community/ResizeEncryptedPartitions](https://help.ubuntu.com/community/ResizeEncryptedPartitions)

Then after shrinking it down, and retesting that all is okay, shut down.

Boot from a Mac OSX boot disk and reinstall it in the unallocacted space. Restore your data and settings.

Either use the Option key to boot what you want, or edit the Grub default file to turn the OS Prober on, then update grub.

Method two: Shrink down your Mac OS from Mac OSX disk utility. Boot the Mac off the Ubuntu LiveUSB. Use "Try". Setup encrytped partitions in the unallocated space. Start the installer from the LiveUSB. Use "other", instead of Guided, and point the partitions and mounts to the new encrytped partitions, and resolve the mounts. Then install. 
RE: [https://gist.github.com/luispabon/db2c9e5f6cc73bb37812a19a40e137bc](https://gist.github.com/luispabon/db2c9e5f6cc73bb37812a19a40e137bc)
* Just ignore that it says with Windows =and= Substitute that as you are installing alongside Mac OSX... Same logic.

Other reference using Boot Camp to partition and run dual-boot, but combine with the last reference: [https://www.makeuseof.com/tag/install-linux-macbook-pro/](https://www.makeuseof.com/tag/install-linux-macbook-pro/)

I can think of more ways, but you would need more skills.

---

### Post by TheFu on 2023-03-21
If you are just an end user and not willing to tinker for days, I suspect this partial encryption will be too complicated for an OS.

BTW, I understand there is a KDE storage tool that can resize LUKS encrypted containers and the LVM stuff inside them. I've not used it, but if you have nothing to lose.

If it were me trying to do this, I'd install Ubuntu to a 128GB USB flash storage device, ignore internal storage completely and choose which storage to use at boot time.  So, you'd be able to install onto the USB flash with a fully encrypted Ubuntu install, in theory.  Just be careful to never allow the installer to touch any internal storage.  You'll need 2 USB flash drives ... one with the normal ISO and the other to install onto.  Be certain that both OSes use the same boot mode, probably UEFI and be certain you know how to get into the UEFI boot tool to select which drive to boot from.

---

### Post by MAFoElffen on 2023-03-21
With installing to an external USB Storage Drive, when you boot the MACOS, if you press the Option key on the MAC keyboard, it will bring up a screen to give the option to boot from different devices... That way it is completely separate, and does not affect what is already installed.

Another way, which I know both TheFu and are fans of (which has not been discussed yet), is installing Ubuntu on your MAC as a virtual machine... That way it gives you the ability to test drive Ubuntu and see if it is something you like, and might want to later install permanently in another form.

There are lots of free Virtual Machine Host software available for MAC...

I know you came here for "one answer". You have many options, in many forms.

---


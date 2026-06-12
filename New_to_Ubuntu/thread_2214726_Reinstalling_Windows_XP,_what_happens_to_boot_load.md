---
title: "Reinstalling Windows XP, what happens to boot loader?"
date: 2014-04-02
forum: New to Ubuntu
---

### Post by Thechromester420 on 2014-04-02
OK guys, I've come up with a MAJOR problem, I need to re-install WinXP but I'm not sure if re-installing it will somehow mess up the BootLoader and it's capability to launch WinXP, so if I install WinXP (with same data/file systme stuff, for example: installed on harddrive, filesystem = NTFS, same as before) with the same install location and filesystem, will the bootloader still be able to launch XP normally?

---

### Post by monkeybrain20122 on 2014-04-02
Reinstall XP? It is dead, time to bury it and move on. Yes, reinstalling it will screw the bootloader, then you may have to reinstall grub (not sure if this works, I never tried it but sounds plausible)

Why don't you follow your own advice in your sig? sudo apt-get install virtualbox and put XP there, and disable network.

---

### Post by cbennett926 on 2014-04-02
> **Thechromester420 said:**
> OK guys, I've come up with a MAJOR problem, I need to re-install WinXP but I'm not sure if re-installing it will somehow mess up the BootLoader and it's capability to launch WinXP, so if I install WinXP (with same data/file systme stuff, for example: installed on harddrive, filesystem = NTFS, same as before) with the same install location and filesystem, will the bootloader still be able to launch XP normally?


Would creating another partition with a LiveCD and re-installing to the new partition and dual booting be a viable option?

---

### Post by Mark Phelps on 2014-04-02
> Would creating another partition with a LiveCD and re-installing to the new partition and dual booting be a viable option? 

That would work, too, but that would overwrite the MBR so you would only boot into XP after that, and you would have to reinstall GRUB to get back booting for Ubuntu.

If you installed virtualbox and installed XP to that, it would not overwrite the Ubuntu GRUB code in your disk MBR.

---

### Post by mastablasta on 2014-04-03
reinstall windows (it will overwrite mbr). care that you only install into windows partition. reinstall grub from Ubuntu (you can use boot repair tool and live DVD/USB to do that). it should solve the issue.

Windows XP must not die!

---

### Post by Warren Hill on 2014-04-03
If you reinstall Windows it will overwrite the MBR and you won't be able to boot ubuntu.

To Fix

1. Make sure you have a live Ubuntu CD or USB you can boot from

2. Reinstall windows

3. Fix the MBR as described here: [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by Thechromester420 on 2014-04-04
> **Warren Hill said:**
> If you reinstall Windows it will overwrite the MBR and you won't be able to boot ubuntu.

To Fix

1. Make sure you have a live Ubuntu CD or USB you can boot from

2. Reinstall windows

3. Fix the MBR as described here: [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

A live CD... meaning, the installation disk?
Also, I'm using Gnome-Flashback because my graphics card has an impaired ability to use the regular Ubuntu Unity, so can I still get to the boot repair?

---

### Post by Thechromester420 on 2014-04-04
Also, the reason I'm re-installing WinXP is because the session manager closes unexpectedly, resulting in a BSoD, obliterating the ability to boot.

---

### Post by Thechromester420 on 2014-04-04
> **Mark Phelps said:**
> That would work, too, but that would overwrite the MBR so you would only boot into XP after that, and you would have to reinstall GRUB to get back booting for Ubuntu.

If you installed virtualbox and installed XP to that, it would not overwrite the Ubuntu GRUB code in your disk MBR.

My harddrive have 250 (windows detects 233.???) GB of space, Ubuntu has ABOUT 1.9 GB of space left for using. I REALLY don't think it's a good idea to use virtualbox to simulate XP. Plus, My processor is not the best, my graphics card is somehow critically impaired, and I would prefer VMware to Virtualbox.

---

### Post by Thechromester420 on 2014-04-04
> **monkeybrain20122 said:**
> Reinstall XP? It is dead, time to bury it and move on. Yes, reinstalling it will screw the bootloader, then you may have to reinstall grub (not sure if this works, I never tried it but sounds plausible)

Why don't you follow your own advice in your sig? sudo apt-get install virtualbox and put XP there, and disable network.

Same with the other guy, My proccessor is terrible, GPU is critically impaired, and I would prefer VMware to VirtualBox any day.

---

### Post by Impavidus on 2014-04-05
> **Thechromester420 said:**
> A live CD... meaning, the installation disk?
Also, I'm using Gnome-Flashback because my graphics card has an impaired ability to use the regular Ubuntu Unity, so can I still get to the boot repair?
Good reply by Warren Hill. The live cd/dvd/usb is the same as the one you can use for installing Ubuntu. Boot-repair doesn't care about your desktop environment, gnome-flashback, unity or otherwise. It operates on a level below that.

I agree that on the weaker hardware typical of the WinXP era virtual machines may not work very well. Don't connect the XP box to the internet.

---

### Post by Thechromester420 on 2014-04-06
> **Impavidus said:**
> Good reply by Warren Hill. The live cd/dvd/usb is the same as the one you can use for installing Ubuntu. Boot-repair doesn't care about your desktop environment, gnome-flashback, unity or otherwise. It operates on a level below that.

I agree that on the weaker hardware typical of the WinXP era virtual machines may not work very well. Don't connect the XP box to the internet.
Thank you!!! Bless you, I can NOT tell you how thankful I am! :KS

---


---
title: "two hard drives, dual boot?"
date: 2012-06-17
forum: New to Ubuntu
---

### Post by benj23673 on 2012-06-17
My newest computer build will be arriving in the next couple of days I am currently downloading ubuntu 12.04 64 bit for my new hard drive I just bought. I have a hard drive from my laptop that I no longer use that runs windows 7 which I will also be putting into the new computer I wanted to know what would be the best way of installing them? I want the option to pick from what hard drive I want to boot from when I start the computer, can I use grub still? any help would be appreciated

---

### Post by shashanksingh on 2012-06-17
I think the link below should help you a lot, in both the implementation and the concept. 

Its a very nice grub tutorial for new Linux users.

[Grub Tutorial]("http://www.dedoimedo.com/computers/grub.html")

---

### Post by Mark Phelps on 2012-06-17
Did your laptop come preinstalled with Win7? If so, is THAT the copy that you want to reuse in another PC?

If so, that likely will NOT work.  Why? Because version that come preinstalled are "locked" to the original PC.  While the transferred drive might boot OK, at some point, Win7 is going to check with MS to revalidate itself, and at that point, will deactivate itself.

On the other hand, if the Win7 version is Retail (meaning, you bought it separately), then you should not have any reactivation problems.

---

### Post by presence1960 on 2012-06-17
You may have problems with Windows due to driver issues. Unlike Linux in Windows you have to install drivers for each piece of hardware. If you have a preinstalled Windows the drivers on that version of windows are for the hardware that came with the machine. So if your new build has different hardware than the machine the windows hard disk came from you will have problems. The drivers for the new hardware will not be on your windows install and thus the hardware affected probably will not work.

---

### Post by lindsay7 on 2012-06-17
I had a motherboard fail and had to replace it. I used the same components on the new motherboard which included the hard drives. I had no problems with the Ubuntu os on the drive but Windows 7 would not work at all and I re installed it using the original store bought dvd. I could never get it activated and could not find anyone at MS to discuss it. I did not need windows on the this computer so I just gave up on it.

---

### Post by benj23673 on 2012-06-18
Ok ok I can understand that but if I formated the old laptop hard drive and put a new version of windows on it since I have long removed all the files from it anyway. How would I go about this? Install ubuntu onto the new hard drive then boot into the second hard drive and install the new windows onto the second hard drive when ready? (I probably will wait until I absolutely need windows to install it if I ever do) or will I have to set up grub first then install the windows

---

### Post by gnusci on 2012-06-18
I was in your situation, I did install Ubuntu and remove Win2.

---

### Post by lynrock on 2012-06-18
I would suggest you install Windows first. Then install Ubuntu to the second disc making sure that you install grub to the MBR of same disc Ubuntu is on. Grub should find windows and add it to the Grub boot menu. You will then have two possible ways to boot Windows, via Grub, or by selecting the other disc during the bios boot and booting windows directly.
Good luck.

---

### Post by wheeze on 2012-06-18
> **lynrock said:**
> I would suggest you install Windows first. Then install Ubuntu to the second disc making sure that you install grub to the MBR of same disc Ubuntu is on. Grub should find windows and add it to the Grub boot menu. You will then have two possible ways to boot Windows, via Grub, or by selecting the other disc during the bios boot and booting windows directly.
Good luck.

This is exactly what I do and it works perfectly. Remember when all is said and done to set your Ubuntu drive as the first boot drive in BIOS. That way your computer boots the Ubuntu drive, presents the grub menu and you can either let it go into Ubuntu or chose Windows and boot that.

The only time you'd need to go back into BIOS and change boot drives is if something happened to your Ubuntu drive and it wouldn't boot. At least you could swap drives in BIOS and get into Windows.

---

### Post by sandyd on 2012-06-18
> **lindsay7 said:**
> I had a motherboard fail and had to replace it. I used the same components on the new motherboard which included the hard drives. I had no problems with the Ubuntu os on the drive but Windows 7 would not work at all and I re installed it using the original store bought dvd. I could never get it activated and could not find anyone at MS to discuss it. I did not need windows on the this computer so I just gave up on it.

You have to call microsoft if you have a hardware change. They will issue you a new serial.

---

### Post by Mark Phelps on 2012-06-18
As I already mentioned back in post #3, if you have a retail copy of Win7, you should not have any problems reactivating it on a new drive.

If, in the worst case, it does not activate, you can call Microsoft using one of the 1-800 numbers, and they will issue you a new product key -- which can then be used to reactivate it.

IF, however, it is an OEM version, Microsoft will NOT help you because, in that case, the OEM actually owns the license for the Win7 version, not you.

---


---
title: "pc does not start /boot to ubuntu"
date: 2011-11-16
forum: New to Ubuntu
---

### Post by raj114547 on 2011-11-16
[SIZE=2]Hi
I have installed ubuntu 11.10 today and am having difficulty in booting straight to the log in screen.
The boot sequence set up in my pc's bios is, dvd/cd then hard drive. When i start the pc, it boots then hangs on the blank purple ubuntu screen. When i press the reset button on the pc, then F11 for boot sequence, then select to boot from the hard drive. It loads to the GNU Grub page. For ubuntu to load successfully here, I have to select  ubuntu with recovery option then, normal boo[/SIZE]t.
[SIZE=2]Please advise[/SIZE].

---

### Post by deltacomp on 2011-11-16
Hello, welcome. Have you tried booting directly to the hard drive? As in select HD in the bios instead of DVD drive? Also, in past experiences I have noticed that Ubuntu takes a little while before it boots to the desktop. 

What happens when you boot to Ubuntu through grub? Does it also hang on the purple screen? When you do boot into Ubuntu do you hear the music?

---

### Post by ask_ on 2011-11-16
> **raj114547 said:**
> [SIZE=2]Hi

The boot sequence set up in my pc's bios is, dvd/cd then hard drive.
 For this ,  you could try changing the default boot device from the BIOS. The option to do so would be available in your BIOS setup.

---

### Post by raj114547 on 2011-11-16
Thank you for the welcome, i have not as yet reset the bios to boot from HD first. Secondly, i left the pc on for over an hour with the purple blank screen and it failed to boot successfully. At the Grub page, I have to select the ubuntu with recovery option and then the normal boot option for it to boot successfully.- Also, whilst all this was going on i did not have the sound on, so i can't tell if the music was on. finally, since the pc is now running - i'm spending the time discovering ubuntu/linux.

---

### Post by Mark Phelps on 2011-11-16
Next time, when you boot, hold down the SHIFT key to get a GRUB menu, boot into Recovery Mode -- and choose the option to Repair Broken Packages (even if you don't have any).

If that completes successfully, then select the option for Normal boot.

That should get you to a desktop -- and if this works, you should boot to the desktop every time after this.

I had 10.10 hang up on me more often that not, and this seemed to fix it for me.

---


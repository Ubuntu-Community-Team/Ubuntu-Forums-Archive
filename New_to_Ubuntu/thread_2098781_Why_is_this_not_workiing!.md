---
title: "Why is this not workiing?!"
date: 2012-12-27
forum: New to Ubuntu
---

### Post by dokha on 2012-12-27
I got my netbook, which doesnt have an optical drive, and an ubuntu cd. I took out the hard drive in my netbook put it in a USB HD enclosure and connected it to another laptop which had an optical drive, and put my ubuntu in. everything went smooth and i booted ubuntu from my HD in the laptop, np , but when i put it back in my netbook, i get a blank screen with a blinking dash in the top left corner, i noticed i get that screen in the laptop but it was very brief. soo yeah why doesnt it want to work?

---

### Post by MG&amp;TL on 2012-12-27
So...you installed Ubuntu on a different laptop, took the hard drive out of that one and put it in the original one?

At a guess, the hardware is different in laptop 2 (optical drive donor), which is what the Ubuntu installer configured itself for, than in laptop 1 (no-optical drive), so it doesn't know what to do with the graphics hardware.

How to fix is a different matter... Try holding Shift at boot, then selecting 'recovery mode', then select 'continue booting', or whatever it is (it's changed a couple of times since I last used it, if I recall).

---

### Post by verymadpip on 2012-12-27
People will be able to help with some more details about the specs of the netbook.

CPU, graphics, RAM that kind of thing.

Blank screen; possibly a graphics issue.

Ah, too slow again :)

---

### Post by dokha on 2012-12-27
> **MG&TL said:**
> So...you installed Ubuntu on a different laptop, took the hard drive out of that one and put it in the original one?

At a guess, the hardware is different in laptop 2 (optical drive donor), which is what the Ubuntu installer configured itself for, than in laptop 1 (no-optical drive), so it doesn't know what to do with the graphics hardware.

How to fix is a different matter... Try holding Shift at boot, then selecting 'recovery mode', then select 'continue booting', or whatever it is (it's changed a couple of times since I last used it, if I recall).
  
There seems to be no response by holding shift the only things i can get into before the blank black screen, is Bios and boot options, then i hear a loud BEEP if i press any key. My Dell netbook doesnt have a GPU. The only other thing i can think of is to reinstall from USB flash drive, but i dont know why that would work.

---

### Post by Cheesehead on 2012-12-27
By 'boot options', do you mean BIOS or GRUB?

If if freezes immediately after BIOS, but before GRUB, then it seems like it's not finding the HDD to boot from, or does not consider the HDD a bootable medium.

- Check your BIOS settings - does the BIOS see the HDD? Is the HDD set as to boot?

- Once your BIOS settings are correct, boot from a LiveUSB. You can simply reinstall from the LiveUSB, or we can help you diagnose and fix the problem.

However, if it freezes *AFTER* GRUB, then select "recovery mode" in GRUB to get the text messages during boot instead of a splash screen.

One of two things will happen. Tell us which one.
1) The system will boot to a command prompt.
2) The system will stop booting, with a bunch of gibberish on the screen. Take a clear photo of the gibberish and post it here. It means something to us.

It's very possible (and easy) to install the wrong kernel if you install from a different machine. Different kernels include instructions for different types of CPUs.

---

### Post by Cheesemill on 2012-12-27
When you installed Ubuntu did you instruct the installer to put the bootloader on the external drive? If not then the bootloader will have been installed to your laptops internal drive.

I would run the installation again using the same method but when you get to the 'Installation Type' screen you need to select 'Something Else' and then manually set up your partitions. Then make sure you select the correct drive for bootloader installation, it will probably be sdb (make sure you choose sdb not sdb1).

[QUOTE=MG&TL]At a guess, the hardware is different in laptop 2 (optical drive donor),  which is what the Ubuntu installer configured itself for, than in  laptop 1 (no-optical drive), so it doesn't know what to do with the  graphics hardware.[/QUOTE]
This doesn't matter. As long as you haven't installed any restricted video drivers you can switch your drive between machines, I've done it plenty of times.

---

### Post by jspike397 on 2012-12-27
Dokha,
Try using another computer to redownload a Ubuntu ISO and use a USB flash disk, and write the Ubuntu ISO to it using These tutorials:
[OSX]("http://www.ubuntu.com/download/help/create-a-usb-stick-on-mac-osx")
[Windows]("http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows")
[Or, another Ubuntu computer]("http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu")

Try installing with the USB pen drive.  That is how I install Ubuntu on my Netbook.

Jspike397

---

### Post by madinc on 2012-12-27
> **dokha said:**
> I got my netbook, which doesnt have an optical drive, and an ubuntu cd. I took out the hard drive in my netbook put it in a USB HD enclosure and connected it to another laptop which had an optical drive, and put my ubuntu in. everything went smooth and i booted ubuntu from my HD in the laptop, np , but when i put it back in my netbook, i get a blank screen with a blinking dash in the top left corner, i noticed i get that screen in the laptop but it was very brief. soo yeah why doesnt it want to work?

Hey i think you installed the bootloader in the wrong HD's mbr.

---

### Post by MG&amp;TL on 2012-12-27
> **Cheesemill said:**
> 
This doesn't matter. As long as you haven't installed any restricted video drivers you can switch your drive between machines, I've done it plenty of times.

Your explanation is better, but if you tick the 'install restricted software' on the installer, it appears to install graphics drivers if you need them. :)

---

### Post by Cheesemill on 2012-12-27
> **MG&TL said:**
> Your explanation is better, but if you tick the 'install restricted software' on the installer, it appears to install graphics drivers if you need them. :)
Does it really? I've never selected this option since it appeared in the installer, I've always preferred to set that sort of stuff up manually after installation. From the wording in the installer I presumed that all this option does is install the ubuntu-restricted-extras package as it only mentions flash and mp3 codecs, it doesn't mention video drivers. Also there are several choices for restricted video drivers, how does it choose which to install?

---

### Post by MG&amp;TL on 2012-12-27
Well, I would have thought so too, but the one time I checked that option (mostly to see what it did), it installed an NVidia driver for my graphics card for when I rebooted, and I'm pretty sure it doesn't normally do that. Hence my assumption. 

As for how it works out which ones, I guess that's what the "detecting hardware..." scripts in ubiquity are about....

Have a nice day! :)

---

### Post by Cheesemill on 2012-12-27
> **MG&TL said:**
> Well, I would have thought so too, but the one time I checked that option (mostly to see what it did), it installed an NVidia driver for my graphics card for when I rebooted, and I'm pretty sure it doesn't normally do that. Hence my assumption. 

As for how it works out which ones, I guess that's what the "detecting hardware..." scripts in ubiquity are about....

Have a nice day! :)
Are you sure it installed the Nvidia driver? Take a look at [this]("http://ubuntuforums.org/showthread.php?t=2098817") thread I created because you piqued my interest...

---

### Post by MG&amp;TL on 2012-12-27
> **Cheesemill said:**
> Are you sure it installed the Nvidia driver? Take a look at [this]("http://ubuntuforums.org/showthread.php?t=2098817") thread I created because you piqued my interest...

No, I'm not. I did some research though, posted that in the thread. :)

---


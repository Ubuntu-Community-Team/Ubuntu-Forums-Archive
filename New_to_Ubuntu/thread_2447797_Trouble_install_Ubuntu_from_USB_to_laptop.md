---
title: "Trouble install Ubuntu from USB to laptop"
date: 2020-07-26
forum: New to Ubuntu
---

### Post by balloonysaintjohn on 2020-07-26
Hello,
 I'm totally new to Ubuntu and not particularly confident with computers. I have followed the tutorials for installing Ubuntu to a USB. I think I've done this correctly. The next step of installing or opening Ubuntu on my laptop is harder than I thought. I restarted the laptop as instructed but nothing seems to be happening. I've looked in the USB, only I'm not sure what to click on, there being so many files. If anybody could point me in the right direction I'd greatly appreciate it. I'm sure this is extremely elementary to most on here but I have to start somewhere.

---

### Post by CatKiller on 2020-07-26
You don't do anything with the files on the USB. You set your computer to boot from the USB rather than its hard drive, and it will boot into the Ubuntu on the USB. Then you can use that for a while to get used to it and, when you're happy with it, optionally install it onto your hard drive as an additional or replacement thing to boot into.

---

### Post by TheFu on 2020-07-26
Typically, nobody "installs ubuntu" onto a USB. They copy over a boot image file to a USB, then boot from that, Try Ubuntu, then select "install" from the desktop. This last step is where the actual Ubuntu Install to other media - usually an internal SSD or HDD - happens.  We need to be very careful about terms here. The words matter greatly. Getting them wrong in a text-only environment will lead to poor advice and possible total data loss.

For new people, I'd look for a youtube video that shows every step to doing an install.  
* Getting the ISO file
* "Burning" the ISO file to installation media ; we call it "burning" because we used to use DVDs and CDROM disks. Since around 2005, most people have switched to flash usb thumb storage for this, but "burning" has remained as a clear way to say "copied bit-for-bit" a specific image/ISO to some other storage
* Booting from the "burned" storage;  Ubuntu Desktop versions have a menu which includes "Try Ubuntu" - use that.  It is also handy to keep around since that "Try Ubuntu" environment is an easy way to fix many issues on an already installed to SSD/HDD Ubuntu.
* Inside the "Try Ubuntu" environment, there is usually an icon on the desktop that says "Install Ubuntu" or "Lubuntu" or "Xbuntu" or "Ubuntu-Mate" or .... whatever flavor you happen to be running.  "Ubuntu Server" doesn't provide any GUI and until 20.04, didn't have a "live environment".

So, with those steps and assuming you "burned" the ISO to a flash storage device, the next step is to convince your system to boot from that device.  Often this happens automatically, but some motherboards/BIOSes don't boot from USB storage without being told. In the BIOS, there is a way to control the boot device and the boot order. You'll need to find that.  It is common to use F8 or F10 or F12 or DEL or ESC pressed during the early hardware-check parts of the system boot to get access to the boot or BIOS controls.

Beware, if you accept the defaults during the install, it is highly likely to completely wipe the internal storage on the computer. If there is any data or any other OS that you don't want gone, best to unplug those storage devices first and leave only the 1 storage device you want the OS installed onto.  If you have other OSes on the system, you have some other choices to make and other people (not me) will need to help.  I haven't dual-booted in a very, very, long time, perhaps 15 yrs.

---

### Post by crip720 on 2020-07-26
Some bios also have booting from USB disabled, have to change to enable.  Would need to go to your bios settings to change/check.

---

### Post by balloonysaintjohn on 2020-07-27
Thank you all, much appreciated. I've taken your advice TheFu and watched some videos. Great so far,  now I've reached the stage of deleting some unwanted files to leave space for Ubuntu (at Installation type stafe). The only thing is I'm not sure what to delete. I don't want to accidentally delete something essential to the running of Windows or whatever. I can see the Windows Boot Manager and will avoid it like the plague but is everything else fair game? The free space files have only 1MB between them.

---

### Post by TheFu on 2020-07-27
You never mentioned dual-boot before.  I cannot help. 

Haven't dual booted in about 15 yrs. Sorry. I find dual-boot to be very dangerous and would suggest using a virtual machine so you can become comfortable first. I had a dual-boot machine about 10 yrs ago, but MSFT updates used to break the booting for Ubuntu so I stopped and switched to using virtual machines.  Any Core2 Duo or faster machine with 4G of RAM can easily support running a virtual machine as a desktop. By using a virtual machine, Windows storage can be used, just need enough space for the VM "virtual hard drive" - about 25G would be nice, but you can load a light flavor and use 10-15G.  Inside the virtual machine, nothing can harm the hostOS actually running on the physical hardware.  During the install inside a virtual machine, you get to say "wipe and use all storage" without fear, since only the amount of storage you setup for the VM will be available.

Oracle's VirtualBox is the least evil of the virtual machine hypervisors that run on Windows for personal use. It is free and there are lots and lots and lots of videos showing how to setup almost anything you can imagine on virtualbox.  For a beginner to Linux, it isn't a bad way to start.

---

### Post by Impavidus on 2020-07-27
I've got one computer still dual booting. I rarely use it, it's 15 years old now.

Important to know which version of Windows you want to dual boot with and what mode (bios or uefi). Typically, you use Windows tools to shrink the Windows partitions enough to get room for Ubuntu, then use Linux tools (included on the live disk) to create Linux partitions and install.

---


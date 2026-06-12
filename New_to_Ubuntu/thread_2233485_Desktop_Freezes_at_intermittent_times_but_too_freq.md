---
title: "Desktop Freezes at intermittent times but too frequent to be usable"
date: 2014-07-08
forum: New to Ubuntu
---

### Post by stormtrupr on 2014-07-08
Hello all,

I have an core2 processor running on an asus p5k mobo with radeon 5750 graphics and using chipset sound and Lan off the mobo.  I have done a fresh install of ubuntu, and tried both default drivers, and AMD catalyst drivers with the same result.  if i boot up the computer, i have automatic login enabled, i get to the desktop, and then in a matter of 5 seconds to 5 minutes, i get a crash.  Sometimes it is a hard crash, sometimes i retain the ability to move the mouse around.  My initial thought was video drivers or possibly a PSU problem, but i have since installed half life source and ran it with no crashes for an hour straight (if i am lucky enough to start the game before the desktop crashes)  due to the game working, i am less convinced this is a video driver issue though nothing is certain to me.  Is this a known bug? what can i try to fix?

I have disabled legacy usb support, though EHCI hand-off is still enabled along with usb 2.0.  I have also disabled the eSATA/PATA controller and onboard Firewire.  What about plug and play O/S support? (currently disabled)

is there anything i should look for under 'dmesg'?

Also, i was originally trying to use a radeon HD 2900 video card with the same crashes.

---

### Post by Bucky Ball on 2014-07-08
A fresh install of which Ubuntu release?

As far as looking at dmesg, when it crashes, hit ctrl+alt+F1 and run dmesg. Post the last bit about the crash error is, if you can.

---

### Post by stormtrupr on 2014-07-09
14.04 that was downloaded mid June.  it is a hard crash that doesn't allow my to do ctrl alt F1.

i will get you dmesg results after i fix the botched update that failed due to crashing during the process....this caused my mouse to flash.  running a dpkg repair now. could the problem be a system RAM issue? what is the console command to run a memory test?

---

### Post by Bucky Ball on 2014-07-09
You should have memtest listed on the grub options at boot. Restart and have a look. It takes a while to do its thing so be prepared for that.

---

### Post by stormtrupr on 2014-07-12
Ok, its fixed! it was the video driver.


I finally was able to select the FGLRX driver from the additional drivers menu in the system config under the GUI.  This was not originally the case and trying to manually install the AMD driver on my first install of Linux apparently wasnt ideal.


How did i get the driver to show up? well, im not positive, but the last round of things i had done was reinstalling lightdm, uninstalling the catalyst drivers downloaded from AMD(these two to fix black screen bootup with no GUI), and installing the lsb support package.


Thanks for help...it has been a long few weeks working on this when i had time.

---

### Post by Bucky Ball on 2014-07-12
Excellent news! To help others, please mark as solved by following the second link in my signature. ;)

---


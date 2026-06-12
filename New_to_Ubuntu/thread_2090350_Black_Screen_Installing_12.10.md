---
title: "Black Screen Installing 12.10"
date: 2012-12-02
forum: New to Ubuntu
---

### Post by vampiro809 on 2012-12-02
Hi there. I'm having problem after installing Ubuntu 12.10.

I know my video card isn't good. To get install I follow up the instruction on how to set the "nomodeset" during the installation with live CD.

After the installation finished, restarted the PC, but get the black screen again. I follow up the procedure to edit the GRUB by holding the shift key - select the Ubuntu version - select E to edit the kernel - replace the "quiet splash" for "nomodeset" - hit ctrl-x to restart... after restart I get a window that says "the system is running in low-graphics mode".... I press OK.... them other window tell me "What would you like to do" and 4 optios: 1)Run in low-graphics mode for just one session. 2)Reconfigure graphics. 3) Troubleshoot the error. 4)exit to console login.

If I selet No. 1 another small window displays that says "Stand by one minute while the display restart" but does nothing, if I press OK the screen turns black with stripes.

Options 2 does nothing, option 3 takes me to check the X.org file.

SO, what to do?

Toshiba Satellite P205-S6337
Intel chipset G945
2GM memory
HDD 200GB

THANKS for you help

---

### Post by brodedra on 2012-12-02
Do you have more details about your video graphics on board? You can post details from BIOS.

---

### Post by vampiro809 on 2012-12-02
Yes, I have the Mobile Intel 945 Express. (I'm running W7, but the VC is disable)

---

### Post by squakie on 2012-12-02
I would try:

i915.modeset=1

if that doesn't work:

i915.modeset=0

you may also need any of the other boot options including:

noapic

acpi=no

I'm suspecting this is just the common 945 problems.  While they may not be for your particular release, search the forum with 945 in the search box.  Also try a web search with:

ubuntu 945

in the search string.  You can try to narrow it down more by:

ubuntu <your release here> 945

That's how a lot of us go looking for answers to questions posted here.

---

### Post by vampiro809 on 2012-12-04
Thanks squakie, I'm gonna try that. So, I'm going to replace the "quiet splash" for i915.nonodeset=1

I let you know whats going on.

---

### Post by Nightcreeper on 2012-12-04
There is also a backlight issue on some of them. Try adding the "acpi_backlight=vendor" and/or
"acpi_osi=Linux" to the grub cfg as a one-time via boot options, or permanent afterwards. I don't know if the Low Graphics mode forces the kernel to not mess with backlight or not, but, since it is a laptop, and I had a problem with that, that is how I fixed it. Also, if you have brightness buttons, you could try to raise the brightness with those to see if it works, if so, the first code should fix it.

> sudo gedit /etc/default/grub

Edit the two lines
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor vga=792"
GRUB_CMDLINE_LINUX="acpi_osi=Linux"  

sudo update-grub 

sudo rebootFrom [http://ubuntuforums.org/showthread.php?t=1864513](http://ubuntuforums.org/showthread.php?t=1864513)

I would leave out the "vga=792" option though.

---

### Post by vampiro809 on 2012-12-05
> **Nightcreeper said:**
> There is also a backlight issue on some of them. Try adding the "acpi_backlight=vendor" and/or
"acpi_osi=Linux" to the grub cfg as a one-time via boot options, or permanent afterwards. I don't know if the Low Graphics mode forces the kernel to not mess with backlight or not, but, since it is a laptop, and I had a problem with that, that is how I fixed it. Also, if you have brightness buttons, you could try to raise the brightness with those to see if it works, if so, the first code should fix it.

From [http://ubuntuforums.org/showthread.php?t=1864513](http://ubuntuforums.org/showthread.php?t=1864513)

I would leave out the "vga=792" option though.

I have tried  boht and get the same....

---


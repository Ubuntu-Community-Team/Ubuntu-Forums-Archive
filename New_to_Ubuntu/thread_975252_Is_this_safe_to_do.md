---
title: "Is this safe to do?"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by kriket on 2008-11-08
The problem:

After installing Ubuntu (8.04 & 8.10) linux on my
Acer Aspire M1640 the boot sequence hangs at the Starting Bluetooth line.

I found this solution on another web page, and would like to know if it is safe?

I have tried it running Ubuntu 8.04 Live, and it works. I would like to try and have my computer duel boot.
 

The solution:

Add a "noapic" switch to the boot command line.

If you haven't installed Ubuntu yet, when the CD loads hit F6 (other options) and add "noapic" without the quotes at the end of the line.

Once Ubuntu is installed, on the boot screen hit ESC when it gives you the option to enter the menu. Select the kernel and hit 'e' to edit the options. Add "noapic" without quotes at the end of the line and hit enter. Then hit 'b' to finish booting with the new option. 

 

To make these changes permanent so you don't have to do this every time you boot:

Open the terminal and type "sudo gedit /boot/grub/menu.lst"

After the "END DEFAULT OPTIONS" line you'll see the boot menu and options. At the end of the "kernel" line place your "noapic" parameter at the end of the line and save the file.

Then to actually update the grub loader with your new information, in the terminal type "sudo update-grub".


Thank you

---

### Post by the.phantom on 2008-11-08
i am not a expert !
 but if you go into 
system
administration
services
you can disable bluetooth if you don't use it ?

---

### Post by mister_pink on 2008-11-08
I can't say if it will fix the issue or not, but that should be safe. It turns off support for apic: [http://en.wikipedia.org/wiki/Apic](http://en.wikipedia.org/wiki/Apic)

---

### Post by kriket on 2008-11-08
Thankyou for answers.

I still not sure what it does, but will give it more of a check running it Live before I go any ferver.

I would hope to attach blue tooth to computer at some time.

---


---
title: "Computer can't restart?!"
date: 2011-11-24
forum: New to Ubuntu
---

### Post by llmunro on 2011-11-24
Hi forum,

I just acquired an Acer Aspire One netbook and promptly wiped the hard drive and installed Ubuntu 11.10.  Everything seems to be working fine, except for when I try to restart the computer.  Ubuntu goes through the whole shutting down process and gets to the point where the screen goes completely black, but then doesn't restart.  The power button is still lit up and when I put my hand on the keyboard, I can feel that the hard drive is still running, but the computer never restarts.  My only solution has been to power it off by holding down the power button and restarting manually.

I didn't think I goofed on the install and all went as expected, so I'm not quite sure what the problem is.  Is there any way to diagnose and fix this or should I try to reinstall?

Thanks much.

Best,
Lisa

---

### Post by AgentZ86 on 2011-11-24
> **llmunro said:**
> Hi forum,

I just acquired an Acer Aspire One netbook and promptly wiped the hard drive and installed Ubuntu 11.10.  Everything seems to be working fine, except for when I try to restart the computer.  Ubuntu goes through the whole shutting down process and gets to the point where the screen goes completely black, but then doesn't restart.  The power button is still lit up and when I put my hand on the keyboard, I can feel that the hard drive is still running, but the computer never restarts.  My only solution has been to power it off by holding down the power button and restarting manually.

I didn't think I goofed on the install and all went as expected, so I'm not quite sure what the problem is.  Is there any way to diagnose and fix this or should I try to reinstall?

Thanks much.

Best,
Lisa


Wish I knew what the fix was, I have a desktop that does exactly the same thing And have been using it this way for several months with no real problems, but it's annoying because I dual boot so to restart I have to shutdown exactly as you are doing.

My desktop is a AMD 3800 dual core X 2 64 and it's a cheap motherboard Elite V2 Lite

I'm wondering if this is something to do with the hard drive although I have a dual core machine with sata I'm actually using a small old hard drive 20GB which makes things very slow.

I have not tried a different drive or bios configuration to see if anything changes

Maybe disabling the sata all together might do it I'll try and post back, I just thought of trying this as I was typing lol

Good luck

---

### Post by mastablasta on 2011-11-24
what happens if you try to shut down via command line?
 
CTRL+alt+F1 to access it
 
then type
 
```
 
sudo shutdown -r now

```
 
enter your user password and watch what kind of errors it gives if any.

---

### Post by llmunro on 2011-11-24
Well, I tried shutting down from the command line and the same thing happens! 

This is such a strange problem! 

Best,
Lisa

---

### Post by larrypg on 2011-11-24
Just curious...not that this is a good way...but if you hold alt printscreen and press r e i s u b will it reboot?

---

### Post by matt_symes on 2011-11-24
Hi

There are a number of kernel command line parameters you can you to force different reboots types.

Have you tried some of the others ? You will be using ACPI for the default.

```
reboot=<reboot_type>
```where <reboot_type> is the type.

```
sudo update-grub
```Will have to look at this tomorrow though.

Kind regards

---

### Post by llmunro on 2011-11-25
@larrypg: Same deal with Alt + Prt Sc R E I S U B...it'll go down for restart but then hangs.  Go figure! 

@matt_symes: I have not tried other command line options to force reboot, mainly because I was unaware of their existence.  I will try some other options and try to update grub in the meantime and report back!

Thanks much to all for the thoughts and suggestions! 

Best,
Lisa

---

### Post by matt_symes on 2011-11-25
Hi

Try some of these options (from reboot.c).

> 
/* reboot=b[ios] | s[mp] | t[riple] | k[bd] | e[fi] [, [w]arm | [c]old] | p[ci]
    warm   Don't set the cold reboot flag
     cold   Set the cold reboot flag
     bios   Reboot by jumping through the BIOS (only for X86_32)
     smp    Reboot by executing reset on BSP or other CPU (only for X86_32)
    triple Force a triple fault (init)
     kbd    Use the keyboard controller. cold reset (default)
     acpi   Use the RESET_REG in the FADT
     efi    Use efi reset_system runtime service
     pci    Use the so-called "PCI reset register", CF9
     force  Avoid anything that could hang.
*/Edit */etc/default/grub* and add *reboot=t or k or p* (etc) then *sudo update-grub*.

Kind regards

---

### Post by wolfen69 on 2011-11-25
I had the same problem on my kubuntu laptop, but when I logged out and shut down from the log in screen it worked. I had also installed the Jupiter Power Management app, but I'm not sure that has anything to do with it.

---


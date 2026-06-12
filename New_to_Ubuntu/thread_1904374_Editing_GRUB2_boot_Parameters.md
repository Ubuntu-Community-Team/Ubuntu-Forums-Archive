---
title: "Editing GRUB2 boot Parameters"
date: 2012-01-04
forum: New to Ubuntu
---

### Post by coversnail on 2012-01-04
Hi (please excuse any noobishness!),

I am trying to activate some kernel power parameters which are disabled by default, but would be beneficial for my laptop. The instructions on the forum for changing them however only apply to Grub1 where they would be inserted into the menu.lst file which isn't present in GRUB2. Basically I want to follow the instructions below but for grub2:

> You have to add the following boot parameters to the grub menu.lst located in /boot/grub:
 
 1.) Activates the RC6 mode of the Intel GPU
      Code:

    ** i915.i915_enable_rc6=1 **

 2.) Activates PCIe Active State Power Management
      Code:

    ** pcie_aspm=force **

 From what I gather in Grub2 to change parameters you: 
```
gksudo gedit /etc/default/grub
# Then:
 sudo update-grub

```

but after ```
gksudo gedit /etc/default/grub
``` where in the file to do add the new instructions and in what format? Thanks for any help, much obliged.

---

### Post by drs305 on 2012-01-04
You add them to the GRUB_CMDLINE_LINUX_DEFAULT=  line.

Save the file, then run "sudo update-grub".

I'd recommend trying Grub Customizer for Grub tweaks. See the 'Customizer' link in my signature line.

---

### Post by coversnail on 2012-01-04
Many thanks for the reply. So if I edited the file like this (my changes in **bold**) would that be right?

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="
    [B] i915.i915_enable_rc6=1
[/B]**pcie_aspm=force  **"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

just not sure whether the new parameters need to be separated with commas, placed inside the quotes on that line or outside etc.

---

### Post by drs305 on 2012-01-04
I can't vouch for the kernel options themselves, but this is the format (just a space between options):
> GRUB_CMDLINE_LINUX="i915.i915_enable_rc6=1 pcie_aspm=force"

plus anything else that is already on the line, such as 'quiet splash' .

---

### Post by coversnail on 2012-01-04
Many thanks :) Will edit thread to [solved]

---


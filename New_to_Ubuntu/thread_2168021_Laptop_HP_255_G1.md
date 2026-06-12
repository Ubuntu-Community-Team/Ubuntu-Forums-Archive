---
title: "Laptop HP 255 G1"
date: 2013-08-16
forum: New to Ubuntu
---

### Post by lubos2 on 2013-08-16
Hello
I buy new laptop HP 255 G1 with OEM Ubuntu.
I have serious problem with shutdown(switch-off) my laptop.
When i use shudtown after second laptop start again.
I try use console command shutdown -p now , but result was like.
I contact HP support but Ubuntu is for them unknown system :-( .
Thank you very much for help

---

### Post by mastablasta on 2013-08-16
did you try on their forums?

anyway what about 
sudo shutdown -h now

perhaps reinstalling the OS is also an option?

---

### Post by lubos2 on 2013-08-16
Yes of course,
Sudo shutdown -h now i try also, but result was same.

---

### Post by Toz on 2013-08-16
Which version of Ubuntu?
Does this happen only when plugged in, or also when on battery?

A couple of suggestions for things to try:

1. Install the **laptop-mode-tools** package. This has some extra laptop management functionality which might assist.

2. Try the **acpi=noirq** kernel parameter. It has been known to fix this issue on other laptops. See the "Kernel Boot Parameters" link in my signature for information on how to temporaily test and permanently apply this parameter.

---

### Post by newb85 on 2013-08-16
HP (along with most other manufacturers that ship with Windows) considers Ubuntu third-party software, so I would not expect much help from them.

---

### Post by lubos2 on 2013-08-18
Hello
I have 12.04 version. 
This is report from GRUB :
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
#GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=3
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="i915.modeset=1 quiet splash"
GRUB_CMDLINE_LINUX=""

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
GRUB_DISABLE_OS_PROBER=true
Thank you very much for help.

---

### Post by Toz on 2013-08-18
Did you install **laptop-mode-tools**? Did it help?

If not, to try the **acpi_noirq** kernel parameter:
[LIST=1]
[*]Edit /etc/default/grub as root (from a terminal window):
```
gksu gedit /etc/default/grub
```
[*]Change the line:
> GRUB_CMDLINE_LINUX=""
...to read:
```
GRUB_CMDLINE_LINUX="acpi=noirq"
```
[*]Save the file
[*]Update grub:
```
sudo update-grub
```
[*]Reboot and test.
[/LIST]

---

### Post by lubos2 on 2013-08-19
Hello
Situation is still same. I change Grub according ti your advice, but not change.
I install laptop-mode but nothing change.
Thank you very much

---

### Post by Toz on 2013-08-19
Can you try the following? 

First issue this command to turn over power control of your devices/buses to the kernel:
```
for i in /sys/bus/*/devices/*/power/control ; do echo on | sudo tee $i ; done
```

Then try to shut down.

---

### Post by lubos2 on 2013-08-19
I am sorry, can sou help me. 
How can Iadd this comman to kernel?

---

### Post by Toz on 2013-08-19
> **lubos2 said:**
> I am sorry, can sou help me. 
How can Iadd this comman to kernel?
Did running the command solve the problem for you? 

If you haven't run it yet, simply copy/paste the command to a terminal window, enter your password when prompted, then try shutting down.

---

### Post by lubos2 on 2013-08-20
I am afraid that it is still same :-(
Tomorrow I will return laptop to shop for claim.
Thank you very much for help.
Have a nice day

---


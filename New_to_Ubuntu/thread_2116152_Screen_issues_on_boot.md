---
title: "Screen issues on boot"
date: 2013-02-15
forum: New to Ubuntu
---

### Post by Rhys 92 on 2013-02-15
Hello all! I've recently installed ubuntu alongside windows 7 on my toshiba satalite L750. I've found when selecting ubuntu in grub about 50% of the time the screen gets static lines across it for 5 seconds (I've attatched a photo), and then continues as normal, successully booting ubuntu. Is there a way to stop this?

---

### Post by DuckHook on 2013-02-15
Welcome to the forums.

What you are experiencing happens on a number of my laptops as well. Since they've always booted just fine, I've ignored the momentary screen artifacts. It usually has to do with incompatible resolution and colour depth assigned by GRUB to the console during the boot precess, but unless you are knowledgeable enough to confidently monkey around in the guts of GRUB, I would advise to just put up with the brief moment of unsightliness. Borking GRUB can render your computer unbootable.

---

### Post by Rhys 92 on 2013-02-15
Ah okay! I'll avoid the nitty gritty and live with it then :) 

On a kinda related note,(it still relates to screen problems :) ), the screen brightness won't change within ubuntu, I read going to /etc/x11/xorg.conf and entering Option "RegistryDwords" "EnableBrightnessControl=1"  could fix this, but I couldn't see the xorg file here, is there another way to enable the keyboard shortcuts keys? 

Cheers, Rhys.

---

### Post by DuckHook on 2013-02-15
xorg.conf is no longer needed in the new versions of Ubuntu, these settings being handled by various other config files, so it is no longer created by the system. However, if you create one, then its settings will override those of the other files, so, like GRUB, it has to be handled with care. A bad xorg.conf won't interfere with your bootup, but it will prevent you from bringing up your X session.

A better way to assign keyboard shortcuts is simply to go System Settings>Keyboard>Shortcuts

This won't give you access to backlight brightness though. Controlling brightness is usually a HW/BIOS affair and operates at a lower level than the OS. This is why most laptops have special key combos that adjust it. On my Dell laptops it's a special <Fn> key. I suppose it would be possible to map to these functions with ACPI or something. Will try to look it up for you. We may end up having to create an xorg.conf file after all. If others know a quick and easy way to do this, feel free to pipe in.

---

### Post by Rhys 92 on 2013-02-16
Thanks! 

I'll be a little clearer, my laptop too has the <fn> keys, the sound ones do their job fine (i.e mute, volume up, volume down) but others, brightness up/down and wifi toggle don't do anything (don't really care about the wifi one though).

---

### Post by DuckHook on 2013-02-16
There appear to be a number of possible causes for this broken functionality. The fixes are pretty technical, involve some danger especially for new users and there's no guarantee any of it will even work, so you need to decide whether it is worth it for you. If you decide to go for it, then let's try the simpler solution first. It involves changing GRUB, so the chief risk is the same as it is for your wonky bootup screen--we bork your ability to boot.

1. To render any misstep at most an irritating inconvenience, immediately back up all of your important data to a reliable, independent and off-computer medium that you then test for data integrity.

2. You will need to enter extra configuration code into your system at boot. Therefore, print out these instructions beforehand since you will obviously have no access to this info during the boot process. Read these steps thoroughly beforehand so that you can excute them confidently and decisively.

3. We will temporarily try out the new parameters first to see if they work. This part is not dangerous, as we can just wipe the parameters clean with a reboot. Therefore, reboot your computer, but during the boot process, hold down the <Shift> key until the GRUB menu comes up. On some systems, it is <Esc> instead of <Shift>.

4. You have 10 seconds or so to choose an action before it boots into your default kernel. You must press *e* during this interval. This allows you to edit the boot parameters of GRUB for this one boot.

5. Scroll down to the line that says:```
linux /boot/vmlinuz-[your_kernel_version] root=UUID=[your_UUID] ro quiet splash
```6. At the very end of that line, making sure there is a space between the last option and what follows, type in:```
pcie_aspm=force acpi_backlight=vendor
```Double check to make sure that you have not made any typos.

7. Press <Ctrl>+<x> to allow boot process to resume with the additional parameters. Do not press <Esc> or you will discard the changes you just made.

8. If the system boots, login and try out your brightness keys. Post back with results. If it works, the next step is to make these changes permanent in GRUB, but that will be step two. This is enough for one session.

---

### Post by Rhys 92 on 2013-02-18
Hey duckhook, thanks for your continued help. I tried the steps you listed, and found the line said 
```
linux /boot/vmlinuz-[your_kernel_version] root=UUID=[your_UUID] ro quiet splash $Vt_handoff
```Does this extra "$Vt_handoff" bit mean anything? Anyway, I tried adding the code you gave a space after the handoff bit, and then tried replacing the handoff bit with your code. Both still allowed the laptop to boot, but neither enabled the brightness keys. 

I'd be happy with just a once of fix that would leave the brightness low, if perhaps that's easier? 

Rhys.

---

### Post by DuckHook on 2013-02-19
try it with just```
acpi_backlight=vendor
```and then, if that doesn't work, with```
acpi_osi=Linux acpi_backlight=vendor
```using the same procedures as above. $Vt_handoff is supposed to be there. Has something to do with creating the colour background during boot. If none of these settings work, then I can only point you to [this]("http://askubuntu.com/questions/207568/every-function-key-on-laptop-works-except-for-brightness") thread. It refers to a bug that affects some laptops and is not very encouraging, requiring patching the kernel. This is far beyond what a general user is bargaining for. Further down, a reply posting describes a workaround using keybindings. It is rather involved, but worth considering. At least it doesn't require you to patch the kernel. Will continue to think about it, but will be busy for the next few days and won't be able to get back to this until mid-week.

---

### Post by Rhys 92 on 2013-02-22
Hello, 

I tried changing the grub loader to the two options you mentioned but neither worked, I also tried installing xbacklight and using that from the command line to set the brightness manually, through xbacklight -set 5 since I'll be happy just with turning down the screen brightness, but that command didn't change anything.

Rhys.

---

### Post by DuckHook on 2013-02-22
If these suggestions don't work, then I'm stumped. Would suggest that you Google or use your manufacturer's forum. Toshiba customer support may also be able to help.

---

### Post by DiabolicalClaptrap on 2013-02-22
I have an Acer Aspire 5740 and I had the same issue with screen brightness. What I did was:

```
nano /etc/default/grub
```And edited the value in line

```
GRUB_CMDLINE_LINUX=
```to "quiet splash acpi_osi=Linux acpi_backlight=vendor"

Then entered update-grub in the terminal.

Edit: I have an Intel HD card.

---

### Post by DuckHook on 2013-02-22
This is equivalent to Post #8 above. However, it changes GRUB permanently instead of just trying out once. OP can test it if he wishes. Should know how to recover if doing so: make copy of /etc/default/grub first.

---


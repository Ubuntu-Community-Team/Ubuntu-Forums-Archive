---
title: "ACER v3 high end laptop wont start ubuntu."
date: 2013-12-05
forum: New to Ubuntu
---

### Post by cylent on 2013-12-05
Problems with ubuntu on a acer v3 laptop.

two sections:

[U][B]UEFI:
[/B][/U][INDENT]secure boot is on = black screen hang
secure boot is off = same as above.


[/INDENT]
_**Legacy Mode:**_

[INDENT]I get the old style ubuntu menu however in a short while it would give the following error then freeze.

[B]hrtimer: interrupt took 4848223292 ns 
[/B]

if i select f6 and disable acpi then the system boots up just fine.[/INDENT]

So the only way to get it to work is with Legacy mode and ACPI turned off. 

This is a problem as i want my system to remain with UEFI on (secure boot preferably on for safety).
is this possible?

Note: I've even checked my iso md5 and it checks out just fine.

---

### Post by fantab on 2013-12-05
Disable '[FastStartup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html")' in Windows 8 and disable '[Fastboot]("http://www.intel.com/support/motherboards/desktop/sb/CS-032034.htm")'.

What Graphics do you have on board?
Read through the following:
[http://ubuntuforums.org/showthread.php?t=2147295&p=12657352#post12657352](http://ubuntuforums.org/showthread.php?t=2147295&p=12657352#post12657352)

---

### Post by cylent on 2013-12-05
fantab:

I already disabled fastStartup and fastboot is already disabled.

still black screen then even the fan on the laptop powers down as if giving up.

the graphics cards on this laptop is dual:

intel hd graphics 4600
nvidia geforce gtx 760m


furthermore i am getting the following before grub loads:

Could not open "\EFI\BOOT\fallBack.efi": 14

pls help! getting frustrated and i am hoping i wont end up quitting :(

---

### Post by cylent on 2013-12-05
Ok i made some further advancements.

in efi boot mode i hit the e key
and removed "quiet splash" and replaced them with "nomodeset"
woohoo it booted.
well almost.
the moment it switched to graphics mode it gave me a black screen.

i can do ctrl+alt+f1 to get a ubuntu login prompt but when i do ctrl+alt_f7 its a black screen.

this is now appearing to be not a efi issue at all but a graphics card issue.

sadly though this bios doesnt allow changing which adaptor gets used so i am only assuming its using the intel chip?

***ironically though if i boot into legacy mode i dont need to do nomodeset. the word around for legacy mode is acpi=off.***

so this maybe an acpi issue after all?

damn i am so lost.

---

### Post by oldfred on 2013-12-05
It may depend on which video you are booting with. And is that a setting in UEFI menu or is it automatic?

nomodeset works for nVidia, but Intel needs different settings.

 Some other Intel boot options
acpi_osi=Linux  acpi_backlight=vendor
 i915.i915_enable_rc6=1

   Force Intel Video mode as boot parameter in grub menu - change to your screen size
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60

---

### Post by oldfred on 2013-12-05
Some other Acer

 How to install Ubuntu for dual-boot with Windows 8 on Acer Aspire V5-551G. Post #3
[http://ubuntuforums.org/showthread.php?t=2176273](http://ubuntuforums.org/showthread.php?t=2176273)
Acer Aspire S7 can't install ubuntu - UltraBook erased RAID meta-data
[http://ubuntuforums.org/showthread.php?t=2121187](http://ubuntuforums.org/showthread.php?t=2121187)
Acer V5-571P-6815 secure boot off worked Shows Diskpart
[http://ubuntuforums.org/showthread.php?t=2081311](http://ubuntuforums.org/showthread.php?t=2081311)
Acer UEFI dual boot trouble: Win7x64 - Ubuntu 12.04 LTS amd64 June 2012
[http://ubuntuforums.org/showthread.php?t=2003442](http://ubuntuforums.org/showthread.php?t=2003442)

---

### Post by cylent on 2013-12-05
ok problem has been **resolved**. :popcorn:

heres what i did.

[to begin with even after solving the issue i am still unsure of the cause]

[U][B]Solution
[/B][/U]
[LIST]
[*]i booted into legacy mode. disabled uefi completely. no windows for the moment.
[*]i had to start Ubuntu live with "nomodeset" selected by pressing f6
[*]proceeded with the installation ...
[*]it complained about no operating system being found. nothing special.
[*]i created a partition for / and one for swap then proceeded
[*]restarted into the new system without a problem.
[*]_this is the tricky part:_
[*]you have to follow this tutorial here to [convert Ubuntu to efi.]("https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_mode")
[*]after that i ran into a problem where the system complained about hdd1 (where ubuntu is) doesn't meet the security policy blah blah.
[*]disabled secure boot and grub showed up.
[/LIST]

that's it. Ubuntu and windows 8.

and i still cant figure out why this couldn't work with efi on to start with.

[I]now time to deal with other problems like how to change mouse pointer speed when the option doesnt exist :(

[/I][COLOR=#ff0000][B][U][problem remains - and is marked again as unsolved.]
[/U]as i mentioned above i converted ubuntu to efi.
once booted into ubuntu we have the same issue once more.

adding nomodeset doesnt work now. 

black screen![/B][/COLOR]

---

### Post by cylent on 2013-12-05
if anybody has any ideas i am all open.

---

### Post by oldfred on 2013-12-05
Are you booting with the nVidia which needs nomodeset or Intel which may need the other settings posted above.
Several different systems posted this worked.
 acpi_osi=Linux  acpi_backlight=vendor

Some with Intel also needed settings changed in UEFI menu.

 Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

But turning off NIC turns off Ethernet, once installed you may be able to turn it back on.

---


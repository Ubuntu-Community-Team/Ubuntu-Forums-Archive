---
title: "HP 2000 Laptop with brightness controls not working"
date: 2012-11-29
forum: New to Ubuntu
---

### Post by k3thomps on 2012-11-29
I've just installed 12.10 on my HP 2000 Notebook. Everything seems to be working  fine except my brightness controls (mine are fn + F2 and fn + F3). At first, when I would click to turn  it up or down, it would show me the slider but the brightness wouldn't  change. I did some searching and tried the solution from here: [http://ubuntuforums.org/showthread.php?t=1468734](http://ubuntuforums.org/showthread.php?t=1468734) which said:

1. Open a terminal (Program - Accessories - Terminal)
2. Type in "sudo gedit /etc/default/grub" (without the "")
3. Find the line that says: GRUB_CMDLINE_LINUX="quiet splash"
4. Edit it so it says: GRUB_CMDLINE_LINUX="quiet splash acpi_backlight=vendor"
5. Save and exit
6. Run the command "sudo update-grub" (again without quotes of course)
7. Reboot and enjoy!

Now that I've done that, when I click to adjust the brightness, not only does it not work, but I also no longer get the slider.

I've looked all over and this problem seems hardware specific and I haven't been able to find any fixes for the HP 2000 Notebooks. My video card is a Radeon HD 6310.

I've also tried editing my xorg.conf  file. When I type in:

sudo gedit /etc/X11/xorg.conf

I get a blank text editor.

I'm not at all sure of what else to try. Does anyone know of anything else I might do?

---

### Post by Toz on 2012-11-29
Hello and welcome to the forums.

Have you enabled the proprietary ATI drivers? Start up Software Centre, click on Edit->Software Sources, then go to the "Additional Drivers" tab.

If enabling them doesn't work, can you undo the changes to the grub, reboot, then open a terminal window, type in the following commands, and post back the results:
```

cat /proc/cmdline
```
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```
```
sudo lspci -vnn | grep -A12 VGA
```

---

### Post by k3thomps on 2012-11-29
Thanks for all your help Toz. Sorry for taking so long to respond. I tried installing the proprietary ATI drivers and my computer did not like that at all. It wouldn't boot up and I had to revert back to the old drivers using the command line.

The output to your requests are as follows:

cat /proc/cmdline

BOOT_IMAGE=/boot/vmlinuz-3.5.0-18-generic.efi.signed root=UUID=37f04ebb-6f93-4dff-8c0b-1ccacb1630de ro quiet splash vt.handoff=7

for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; doneghtness; cat $i/max_brightness; done

/sys/class/backlight/acpi_video0
5
10

sudo lspci -vnn | grep -A12 VGA

00:01.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Wrestler [Radeon HD 6310] [1002:9802] (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device [103c:169a]
    Flags: bus master, fast devsel, latency 0, IRQ 41
    Memory at e0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 3000 [size=256]
    Memory at f0400000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: radeon
    Kernel modules: radeon

---

### Post by Toz on 2012-11-29
> **k3thomps said:**
> I tried installing the proprietary ATI drivers and my computer did not like that at all. It wouldn't boot up and I had to revert back to the old drivers using the command line.
Which driver did you select? I believe there are two - one of them mentions something about updates. Don't choose that one, choose the regular one. Those drivers should work with this video card.

> The output to your requests are as follows:

cat /proc/cmdline

BOOT_IMAGE=/boot/vmlinuz-3.5.0-18-generic.efi.signed root=UUID=37f04ebb-6f93-4dff-8c0b-1ccacb1630de ro quiet splash vt.handoff=7
good.

> for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; doneghtness; cat $i/max_brightness; done

/sys/class/backlight/acpi_video0
5
10
So you have only one backlight interface (acpi_video0). Is the problem still the same? The brightness indicator changes but not the actual brightness?

Can you open a terminal window, type in the following commands, and let me know if the brightness changes:
```

echo 2 | sudo tee /sys/class/backlight/acpi_video0/brightness
echo 10 | sudo tee /sys/class/backlight/acpi_video0/brightness
echo 5 | sudo tee /sys/class/backlight/acpi_video0/brightness

```
...note: the sudo command will prompt you for your password - its required to make the change to that file.

> sudo lspci -vnn | grep -A12 VGA

00:01.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Wrestler [Radeon HD 6310] [1002:9802] (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device [103c:169a]
    Flags: bus master, fast devsel, latency 0, IRQ 41
    Memory at e0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 3000 [size=256]
    Memory at f0400000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: radeon
    Kernel modules: radeon
Just confirming that you have one video card and the radeon driver is in use.

---

### Post by k3thomps on 2012-11-29
To your question "which driver did you select?" I selected the non-updated one. I have no idea why it didn't work. It would start to boot and then freeze.

To your question "Is the problem still the same? The brightness indicator changes but not the actual brightness?" Yes, this is indeed the problem. Whenever I used the buttons on my keyboard or the slider in system settings to adjust brightness the bar goes up or down, but the brightness does not change.

I tried the code

echo 2 | sudo tee /sys/class/backlight/acpi_video0/brightness echo 10 | sudo tee /sys/class/backlight/acpi_video0/brightness echo 5 | sudo tee /sys/class/backlight/acpi_video0/brightness
and nothing happened. The screen brightness remained unchanged.

---

### Post by Toz on 2012-11-29
> I tried the code

echo 2 | sudo tee /sys/class/backlight/acpi_video0/brightness echo 10 | sudo tee /sys/class/backlight/acpi_video0/brightness echo 5 | sudo tee /sys/class/backlight/acpi_video0/brightness
and nothing happened. The screen brightness remained unchanged.
Hmmm, interesting.

Can you try adding the following sequence to grub like you did before:
```
acpi_osi=Linux acpi_backlight=vendor
```
...reboot and test the function keys?

Also post back again:
```
cat /proc/cmdline
```
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```
...and I'd like to see a copy of your dmesg log file:
```
pastebinit /var/log/dmesg
```
(post back the link that is generated.)

---

### Post by k3thomps on 2012-11-29
Here is the output to the code you wanted me to use

cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.5.0-18-generic.efi.signed root=UUID=37f04ebb-6f93-4dff-8c0b-1ccacb1630de ro quiet splash acpi_osi=Linux acpi_backlight=vendor vt.handoff=7

for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
/sys/class/backlight/*
cat: /sys/class/backlight/*/brightness: No such file or directory
cat: /sys/class/backlight/*/max_brightness: No such file or directory

pastebinit /var/log/dmesg
The program 'pastebinit' can be found in the following packages:
 * pastebinit
 * pastebinit
Try: sudo apt-get install <selected package>

---

### Post by Toz on 2012-11-29
> **k3thomps said:**
> Here is the output to the code you wanted me to use

cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.5.0-18-generic.efi.signed root=UUID=37f04ebb-6f93-4dff-8c0b-1ccacb1630de ro quiet splash acpi_osi=Linux acpi_backlight=vendor vt.handoff=7

for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
/sys/class/backlight/*
cat: /sys/class/backlight/*/brightness: No such file or directory
cat: /sys/class/backlight/*/max_brightness: No such file or directory
Now there are no backlight interfaces. Wierd. Okay, remove just the acpi_backlight=vendor piece so that you only have:
```
acpi_osi=Linux
```
...reboot and try again (post back same info as before).

> pastebinit /var/log/dmesg
The program 'pastebinit' can be found in the following packages:
 * pastebinit
 * pastebinit
Try: sudo apt-get install <selected package>
Looks like the program is not installed. Install it via:
```
sudo apt-get install pastebinit
```
...then run the command.

Also, do these commands change brightness?
```

sudo setpci -s 00:01.0 f4.b=40
sudo setpci -s 00:01.0 f4.b=ff
sudo setpci -s 00:01.0 f4.b=80

```

---

### Post by k3thomps on 2012-11-29
Here is the output with acpi_backlight=vendor removed

cat /proc/cmdline

BOOT_IMAGE=/boot/vmlinuz-3.5.0-18-generic.efi.signed root=UUID=37f04ebb-6f93-4dff-8c0b-1ccacb1630de ro quiet splash acpi_osi=Linux vt.handoff=7


for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done

/sys/class/backlight/acpi_video0
4
10


pastebinit /var/log/dmesg

[http://paste.ubuntu.com/1397573/](http://paste.ubuntu.com/1397573/)


The code

sudo setpci -s 00:01.0 f4.b=40
sudo setpci -s 00:01.0 f4.b=ff
sudo setpci -s 00:01.0 f4.b=80

also did nothing.

---

### Post by Toz on 2012-11-29
From your dmesg log file:
> [   20.962573] microcode: failed to load file amd-ucode/microcode_amd.bin
[   20.962600] microcode: CPU1: patch_level=0x0500010d
[   20.973738] microcode: failed to load file amd-ucode/microcode_amd.bin
[   20.974046] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
...you might want to install the **amd64-microcode** package to address this - though I don't think it will help with the brightness.

> [    0.319905] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.320180] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
...I think this may be more relevant. You might want to check if there is a bios update available. Also, have a look in the bios to see if there are some brightness configuration options that you can adjust that might help.

I had a look at buggy bios'es a while back ([http://ubuntuforums.org/showpost.php?p=12184698&postcount=25]("http://ubuntuforums.org/showpost.php?p=12184698&postcount=25")) - there are a couple of other kernel parameters you might want to try to see if the tables are built differently and maybe enable a working backlight interface.

Barring that, I think the next best step is to create a bug report over at launchpad.net (you don't seem to have a valid backlight interface).

You might also consider creating a new thread to get someone to help with installing the proprietary ATI drivers to see if they help.

---

### Post by k3thomps on 2012-11-29
Thanks for all your help. I will look into your suggestions and if they don't help I'll file a bug report.

---

### Post by Eustass on 2013-03-14
I assume HP 2000 is the same laptop I have.. the 2b19wm ? 

[COLOR=#ff0000]I am also having this problem[/COLOR] and it sucks real bad... because so far Ubuntu 12.10 and future distros and Fedora 18 are the only one that are supposed to work with the HP 2000. I am only familiar with Ubuntu and some Arch.

The laptop is new..(it comes shipped with Windows 8).. so you know that it has secure boot (freaking windows man)

I wanted to install Windows 7 but theres no driver for it.. 

Anyway I hope a fix will be available on the newer Ubuntu.....wait does **13.04 comes with the new and lastest kernel?**

For now I have to go back to Windows 8 and stay there until Ubuntu 13.04 :(

---


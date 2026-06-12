---
title: "Another Sony Vaio without working brightness"
date: 2012-11-25
forum: New to Ubuntu
---

### Post by quiksilverlives on 2012-11-25
Hi guys. First post; please be gentle with me. I've just installed 12.10 alongside Windows on my Sony Vaio T series laptop/ultrabook. And everything seems fine except my brightness controls. At first, when I would click to turn it up or down, it would show me the slider but the brightness wouldn't change. I did some searching and tried the solution from here: [http://ubuntuforums.org/showthread.php?t=1468734](http://ubuntuforums.org/showthread.php?t=1468734) which said:

1. Open a terminal (Program - Accessories - Terminal)
2. Type in "sudo gedit /etc/default/grub" (without the "")
3. Find the line that says: GRUB_CMDLINE_LINUX="quiet splash"
4. Edit it so it says: GRUB_CMDLINE_LINUX="quiet splash acpi_backlight=vendor"
5. Save and exit
6. Run the command "sudo update-grub" (again without quotes of course)
7. Reboot and enjoy!

Now that I've done that, when I click to adjust the brightness, not only does it not work, but I also no longer get the slider.

All the other solutions I see are for Sony laptops with an NVidia card, which to the best of my knowledge I don't have. Mine simply says Intel HD Graphics 4000 in the specs. I've read half a dozen other threads, but all of them either involved the NVidia drivers or editing my xorg.conf file, and when I tried that, I don't seem to have one; when I type in:

sudo gedit /etc/X11/xorg.conf

I get a blank text editor. Perhaps it's something slightly different in newer versions? It seems that fix was for an older version.

I'm at a bit of a loss at this point. Does anyone know of anything else I might do?

---

### Post by Toz on 2012-11-25
Hello and welcome to the forums.

The first thing to do, is to undo what you have done. Remove the acpi_backlight=vendor kernel parameter and re-run:
```
sudo update-grub
```
...then reboot.

After you've logged in again, can you open a terminal window, type in the following commands and post back the results:
```
cat /proc/cmdline
```
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```
```
sudo dmidecode -s system-manufacturer
```
```
sudo dmidecode -s system-product-name
```
```
sudo lspci -vnn | grep -A12 VGA
```
Note that the sudo command will prompt you for a password - enter your login password to proceed.

---

### Post by quiksilverlives on 2012-11-25
Hi Toz, thanks for the welcome and the help. I undid the change I made and rebooted, and got the output of all the things you asked.

Not sure how to put it in code boxes, but here it is with a couple lines separating each answer.


BOOT_IMAGE=/boot/vmlinuz-3.5.0-18-generic root=UUID=acc7e06a-f16e-4117-b20f-9294be0c9224 ro quiet splash vt.handoff=7


/sys/class/backlight/acpi_video0
7
15
/sys/class/backlight/intel_backlight
4882
4882


Sony Corporation


SVT13112FXS


00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09) (prog-if 00 [VGA controller])
	Subsystem: Sony Corporation Device [104d:90a8]
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at c4000000 (64-bit, non-prefetchable) [size=4M]
	Memory at b0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 5000 [size=64]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [d0] Power Management version 2
	Capabilities: [a4] PCI Advanced Features
	Kernel driver in use: i915
	Kernel modules: i915

---

### Post by Toz on 2012-11-25
Which of the following commands, when entered in a terminal window, adjust the brightness:
[LIST=1]
[*]```
echo 15 | sudo tee /sys/class/backlight/acpi_video0/brightness
```
[*]```
echo 7 | sudo tee /sys/class/backlight/acpi_video0/brightness
```
[*]```
echo 2441 | sudo tee /sys/class/backlight/intel_backlight/brightness
```
[*]```
echo 4882 | sudo tee /sys/class/backlight/intel_backlight/brightness
```
[/LIST]

Also, type the following in the terminal window:
```
acpi_listen
```
...then press the "function+brightness up" keys and then the "function+brightness down" keys and post back what shows up in the window.

---

### Post by quiksilverlives on 2012-11-25
caz@Vaio:~$ acpi_listen
sony/hotkey SNC 00000001 00000010
sony/hotkey SNC 00000001 0000003b
sony/hotkey SNC 00000001 00000011
sony/hotkey SNC 00000001 0000003b

(That was down first, then up.)

The 3rd and 4th commands you listed, the 2441 and 4228 lines, adjusted down and up respectively.

---

### Post by Toz on 2012-11-26
Ok, lets make the following changes and see what happens.

Create the following files with the following content (you will need root privileges to do this, so for each file, run "gksu gedit <file>" where <file> is: )

**/etc/acpi/events/sony-brightness-up**
```
event=sony/hotkey SNC 00000001 00000011
action=/etc/acpi/brightup.sh
```

**/etc/acpi/events/sony-brightness-down**
```
event=sony/hotkey SNC 00000001 00000010
action=/etc/acpi/brightdown.sh
```

**/etc/acpi/brightdown.sh**
```

#!/bin/bash
curr=`cat /sys/class/backlight/intel_backlight/actual_brightness`
if [ $curr -gt 406 ]; then
   curr=$((curr-406));
   echo $curr  > /sys/class/backlight/intel_backlight/brightness;
fi
```

**/etc/acpi/brightup.sh**
```

#!/bin/bash
curr=`cat /sys/class/backlight/intel_backlight/actual_brightness`
if [ $curr -lt 4477 ]; then
   curr=$((curr+406));
   echo $curr  > /sys/class/backlight/intel_backlight/brightness;
fi
```

Then, make all 4 of those scripts executable by running the following commands:
```

sudo chmod +x /etc/acpi/events/sony-brightness-up
sudo chmod +x /etc/acpi/events/sony-brightness-down
sudo chmod +x /etc/acpi/brightdown.sh
sudo chmod +x /etc/acpi/brightup.sh
```

And finally, restart acpid:
```

sudo service acpid restart
```

Check if the function keys work now.

---

### Post by quiksilverlives on 2012-11-26
Yes! Perfectly! Thank you so much! I'll mark the thread solved.

---


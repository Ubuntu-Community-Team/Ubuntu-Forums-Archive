---
title: "The computer doesn't start after hibernation"
date: 2012-08-09
forum: New to Ubuntu
---

### Post by ruslan kim on 2012-08-09
Hi,
I have a small problem with my laptop (HP Pavilion g6, Ubuntu 12.04). After I close the lid and then open it again the PC is not responding. All I can do is unplug it, take out the battery and start again. And it happens not only when I close the lid, but also when I command the system to hybernate. How to fix it?

---

### Post by mastablasta on 2012-08-10
there is a kernel bug that affects some configs. i too can't wake it up anymore from hibernation (though it used to work well before in 10.10). i've disabled hibernaiton however i have a desktop and this might not be practical for laptop.

---

### Post by NikTh on 2012-08-10
Hi , 
the package where controls these functions is pm-utils. Although is possible to be a kernel bug too. 
I have not such problem on my Acer Aspire on Ubuntu 12.04 with 3.2 kernel . 
To finding if it is a Kernel bug , try to install a newer kernel. Download it from here --> [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")
Download the appropriate .deb packages (32bit or 64bit) an put them on a new folder. 
Then open a terminal and connect to this new folder with cd command . 
eg
```
cd /home/username/newfolder/
```then run this command to install all .deb packages at once. 
```
sudo dpkg -i *.deb
```reboot and login from newer kernel to see the behavior. 

If is not a kernel bug , maybe is a BIOS thing. Try to reset BIOS settings on Default or search for a newer BIOS version.

Another option might be add a parameter on grub and pass it to kernel . A parameter like acpi=force.

Also you must know that Suspend option (when lid close) wants a (little) big swap partition. Do you have ? 
Thanks

---

### Post by marlow59 on 2012-08-10
a little advice : if you are stuck with a non responding computer, you can just push the power button for 7 seconds, it will shutdown, without having to remove the battery and stuff.

---

### Post by Toz on 2012-08-10
Related bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/987840]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/987840"). 

From comment #20, it looks like adding:
```
acpi_osi=Linux acpi_backlight=vendor
```
...to /etc/default/grub and then running:
```
sudo udpate-grub
```
...might solve the problem.

---

### Post by audiomick on 2012-08-10
> **marlow59 said:**
> a little advice : if you are stuck with a non responding computer, you can just push the power button for 7 seconds, it will shutdown, without having to remove the battery and stuff.

Alt+SysRq and reisub

is better.

Look here under "uses". Down the page a bit.
[http://en.wikipedia.org/wiki/Reisub]("http://en.wikipedia.org/wiki/Reisub")

---

### Post by ruslan kim on 2012-08-10
> **Toz said:**
> Related bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/987840]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/987840"). 

From comment #20, it looks like adding:
```
acpi_osi=Linux acpi_backlight=vendor
```
...to /etc/default/grub and then running:
```
sudo udpate-grub
```
...might solve the problem.

How do I do that? Can you please explain step-by-step? Thank you.

---

### Post by Toz on 2012-08-10
Issue all commands in a terminal window.

1. Edit the grub configuration file:
```
gksudo gedit /etc/default/grub
```

2. Change the line:
> GRUB_CMDLINE_LINUX=""
...to read:
```
GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor"
```
...and save the file.

3. Save the grub configuration.
```
sudo update-grub
```

4. Reboot the computer and try again. If it doesn't work, can you run the following command in the terminal window and post back the results?
```
cat /proc/cmdline
```

---

### Post by ruslan kim on 2012-08-11
> **Toz said:**
> Issue all commands in a terminal window.

1. Edit the grub configuration file:
```
gksudo gedit /etc/default/grub
```

2. Change the line:

...to read:
```
GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor"
```
...and save the file.

3. Save the grub configuration.
```
sudo update-grub
```

4. Reboot the computer and try again. If it doesn't work, can you run the following command in the terminal window and post back the results?
```
cat /proc/cmdline
```

I followed the instructions, here are the results:
- all USB ports stopped working (my USB mouse is not lighting and responding)
- windows act different, before they used to go to the right or left half of the screen or maximize if I dragged-and-droped the to the right, left or top edges of the screen, now they don't do that
- the main panel on the left of the screen is moving much slower and now the thumbnails are not "stacking" (they used to before)
- the problem remains the same, the PC hangs when I close the lid

Here is what the terminal says:

```
ruslan@HP-Pavilion-g6-Notebook-PC:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.2.0-29-generic root=UUID=b80f32c3-ceeb-495c-a88d-cfe73318990c ro recovery nomodeset acpi_osi=Linux acpi_backlight=vendor
```

By the way, when I start the PC now, at first it hangs with a purple screen, then I start it again (grub offers a recovery mode).

---

### Post by Toz on 2012-08-11
If you haven't already, undo the changes you made and maybe you can add your name to the bug list at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/987840]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/987840") and follow it's progress there.

---

### Post by ruslan kim on 2012-08-11
All right, I guess I'll just leave it as it is...
Many thanks to everybody anyway!

BTW, look what I found to enable hibernation mode:
[http://www.liberiangeek.net/2012/04/enable-hibernation-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/04/enable-hibernation-in-ubuntu-12-04-precise-pangolin/)

---


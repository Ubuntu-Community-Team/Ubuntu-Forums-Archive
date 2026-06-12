---
title: "Monitor very dim on boot"
date: 2012-11-17
forum: New to Ubuntu
---

### Post by mmcl26554 on 2012-11-17
Every time I boot Ubuntu on my HP Pavilion G6 the brightness of the screen is set to minimum and I have to turn it up.  Is there a setting so it will be set to my normal brightness?
Michael

---

### Post by matt_symes on 2012-11-17
Hi
 
I assume you are using the generic acpi video driver and not the specific driver for this model ?
 
From the terminal type
 
```
ls /sys/class/backlight
```
 
if you see an entry directory called...
 
```
acpi_video0
```
 
then you are using the generic driver.
 
If so, you can try the vendor specific driver and see what mileage you get with that.
 
From the terminal... Enter your password when prompted. It will not be echoed to the screen. This is normal.
 
You may find it easier to copy and past these commands from this post into the terminal than to type them.
 
Make a backup copy of the default grub file.
 
```
sudo cp /etc/default/grub{,.old}
```
 
Delete the default grub command line
 
```
sed -i '/GRUB_CMDLINE_LINUX_DEFAULT/d' etc/default/grub
```
 
Add the new grub command line spoecifing that the vendors backlight kernel module should be used.
 
```
sudo echo 'GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"' >> etc/default/grub
```
 
```
sudo update-grub
```
 
Reboot your PC and see if the monitor brightness is set. If not then post back the output of this command.
 
```
cat /proc/cmdline
```
 
I don't own you laptop so there are no promises with this.
 
If it does not work then type this to get to the previous settings.
```
 
sudo rm /etc/default/grub
sudo mv /etc/default/grub{.old,}
sudo update-grub

```
 
Kind regards

---

### Post by mmcl26554 on 2012-11-17
I understand what you are telling to do, however, as a beginning beginner I don't know where to find things.   Where do I go to access the terminal to enter the commands.  I have seen the grub folder but not the file you suggest.  How do I browse the manufacturer specific video drivers?   I will lear as I do.  Alternatively if you suggest a tutorial on Ubunto to do what you suggest I'll be happy to study it and learn more.
Thanks for taking the time to help and your understanding
Michael

---

### Post by matt_symes on 2012-11-17
Hi
> Where do I go to access the terminal to enter the commands.
 
There are a number of ways to start a terminal. 
 
One way is to press ALT and F2 at the same time. You will get the "run application" window appear. 
 
You can then type
 
```
gnome-terminal
```
 
and this will open a terminal.
 
You can also press the meta (windows) key and type the word "terminal". 
This should also give you the option of selecting a terminal.
 
> I have seen the grub folder but not the file you suggest.
what version of Ubuntu are you using ? Can you post the output of 
```
ls /etc/default/grub
```
> How do I browse the manufacturer specific video drivers?
You do not need to navigate to those files. You need to edit the file /etc/default/grub and tell it to use the correct acpi video driver for your laptop vendor.
 
If you are not so confortable using the terminal then you can edit the grub file by pressing ALT + F2 and typing
 
```
gksudo gedit /etc/default/grub
```
 
This will open the file in gedit which is a lot like notepad in Windows. You will have to enter your password. 
There you can change the line
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
to become
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **acpi_backlight=vendor**"
```
 
The above command highlighted in bold should load the vendor kernel module for you acpi video control.
 
You can then press ALT + F2 again and type
```
sudo update-grub
```
Give that command time to finish.
 
You may find that easier than entering commands into the terminal.
 
Kind regards

---

### Post by mmcl26554 on 2012-11-17
The output after entering ls /etc/default/grub was: /etc/default/grub
I am using Ubuntu ver: 12.10
I added the code: acpi_backlight=vendor as you said but it didn't change anything
It's not a big deal as I now know what to do.  When I first installed Ubuntu I thought it didn't complet the installation, then I saw a shadow on the screen ane pressed the key to turn the brightness and there it was.   I have more questions about the touchpad and installing a modem but I will post them in another thread.
I'm learning.
Michael

---

### Post by matt_symes on 2012-11-18
Hi
 
>  
ls /etc/default/grub was: /etc/default/grub

 
Then the default grub file does exist so that is good.
 
Did you run ```
sudo update-grub
``` after editing the grub file ? This command is very important to run.
 
You can check this command ran correctly using
 
```
 
cat /proc/cmdline

```
 
look for text that says
 
```
 
acpi_backlight=vendor

```
 
in the output from this command.
 
I will be AFK for a number of days but i will try to pick this thread up next weekend if you have not found a solution.
 
Kind regards

---

### Post by mmcl26554 on 2012-11-19
the results was: BOOT_IMAGE=/boot/vmlinus-3.5.0-18-generic root=UUID=01CDC2CE17FDE860 loop=/ubuntu/disks/root.disk ro quiet splash vt.handoff=7
Michael

---

### Post by mmcl26554 on 2012-11-20
Good news!   When I rebooted it worked!   I went through your steps again and this time it seemed to complete the changes and indeed it had.  So this issue is resolved.   Now I just have to remember what was done!  Thanks for yoiur help!
Michael

PS: I have more questions but I'll start a new thread for them

---


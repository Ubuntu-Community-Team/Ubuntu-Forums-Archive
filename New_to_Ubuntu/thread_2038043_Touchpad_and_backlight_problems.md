---
title: "Touchpad and backlight problems"
date: 2012-08-05
forum: New to Ubuntu
---

### Post by kr1sti on 2012-08-05
Hi!

I've got two problems that I thought I might put in the same thread.

Problem #1: Sometimes when I boot in to ubuntu, my touchpad doesn't seem to work. I tried to download a program that could enable/disable the touchpad, but it didn't seem to find the driver. This doesn't happend with an external mouse, but mine just broke so I have to reboot many times until the mouse finally works. I have a synaptics PS/2 touchpad.

Problem #2: Everytime I boot in to  ubuntu, the backlight wont work unless I increase screen brightness on that pink screen during boot. Otherwise, I can hardly see anything, if I can see at all.

I have an eMachines laptop(don't remember wich model, I'll look for it later if needed).

Thanks in advance!

---

### Post by kr1sti on 2012-08-06
(bump) Anyone?

---

### Post by NikTh on 2012-08-06
Hi , 
try to follow this 

1)Open a terminal (ctrl+alt+t) and copy-paste this command ```
gksudo gedit /etc/default/grub
```2)at the opened window find the line **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" **
and make it like this 
**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"**
proofread (accuracy needed) 
save the document and...
...3) run in terminal 
```
sudo update-grub
```reboot and see if your problems resolved.

Thanks

---

### Post by kr1sti on 2012-08-06
> **NikTh said:**
> Hi , 
try to follow this 

1)Open a terminal (ctrl+alt+t) and copy-paste this command ```
gksudo gedit /etc/default/grub
```2)at the opened window find the line **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" **
and make it like this 
**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"**
proofread (accuracy needed) 
save the document and...
...3) run in terminal 
```
sudo update-grub
```reboot and see if your problems resolved.

Thanks

Unfortunately, it didn't solve my backlight problems, first I was taking to the boot screen where I could choose wich OS to boot to, after that, this blank purple screen appeared. Then it appeared a somekind of old-fashioned black and white terminal screen showing a flashing underdash, then the screen went black and I could hear that drum sound that's played on login-screen.

Abou the touchpad: this time, the touchpad worked, but I don't know if it was luck or if the problem was actually solved, gonna reboot a few times and see if it worked.

---

### Post by NikTh on 2012-08-06
> **kr1sti said:**
> Unfortunately, it didn't solve my backlight problems, first I was taking to the boot screen where I could choose wich OS to boot to, after that, this blank purple screen appeared. Then it appeared a somekind of old-fashioned black and white terminal screen showing a flashing underdash, then the screen went black and I could hear that drum sound that's played on login-screen.

Abou the touchpad: this time, the touchpad worked, but I don't know if it was luck or if the problem was actually solved, gonna reboot a few times and see if it worked.

Hi , 
OK , I am wait for feedback about touchpad. 

For the other problem , with blank screen etc , I assume it is something to do with graphics driver. 
Can you login ? 
If yes , then..
...Open a terminal (ctrl+alt+t) and copy-paste below commands , one at time. Online = One command. Hit Enter to see the results. Post the results back here. 
```
lspci -nnk | grep -iA2 vga
/usr/lib/nux/unity_support_test -p
``` 
  	 	 	 	 	 	   **Put the results inside [CODE] tags by highlighting the output and then click on the  [IMG]http://ubuntuforums.org/images/editor/code.gif[/IMG] button in the message toolbar.**

---

### Post by kr1sti on 2012-08-06
It's strange, but I think I know what the problem is now. I managed to login using a flashlight, and then I tried to increase screen brightness, and it worked! But the strange thing is that instead of pressing the normal Fn+right-key to increase brightness, I had to press Fn+left-key. But anyway, the problem seems to be that ubuntu boots with screen brightness all the way to the left(off), so I have to manually login and increase brightness, or increase it while at the purple boot screen. 
Do you have any idea on how to make ubuntu automatically boot with full brightness?

And the touchpad, I've rebooted 3 times and it has worked perfectly. Gonna reboot a few more times to be sure it's working.

Edit: Rebooted 7 more times, on first reboot, the mouse worked perfectly, but everything went wrong on the second reboot. The touchpad didn't work, and I had to reboot like 5/6 more times until it finaly did. :(

---

### Post by NikTh on 2012-08-06
Hi , 
We can leave the problem with touchpad for now and focus on brightness. 

Open a terminal and give below command 
```
gksudo gedit /etc/rc.local
```at the opened window add below line **before "exit 0"**

```

xrandr --output LVDS1 --brightness 1.0
```save the document and reboot to see brightness.
Thanks.

---

### Post by kr1sti on 2012-08-06
> **NikTh said:**
> Hi , 
We can leave the problem with touchpad for now and focus on brightness. 

Open a terminal and give below command 
```
gksudo gedit /etc/rc.local
```at the opened window add below line **before "exit 0"**

```

xrandr --output LVDS1 --brightness 1.0
```save the document and reboot to see brightness.
Thanks.

Same as before :(. Boots with no brightness.

---

### Post by NikTh on 2012-08-06
> **kr1sti said:**
> Same as before :(. Boots with no brightness.

Hi , 
open rc.local again and clear (delete) the line we added before. 

Open a terminal and give this command 
```

xrandr --output LVDS1 --brightness 1.5
``` 
can you see any change on brightness ? If not 
then give the results of below command
```
xrandr
```
Thanks

---

### Post by kr1sti on 2012-08-06
I didn't really see any difference in brightness, but when I was going to increase it, I only had to press the button once to get full brightness, unlike before.

Here's the result from the command:
```
Screen 0: minimum 320 x 200, current 1600 x 900, maximum 8192 x 8192
LVDS1 connected 1600x900+0+0 (normal left inverted right x axis y axis) 398mm x 232mm
   1600x900       60.0*+
   1440x900       59.9  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
```

---

### Post by NikTh on 2012-08-06
Hi , 

lets clear things out and try something else. 

First , open again the file 
```
gksudo gedit /etc/default/grub
```again find the line [B]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor" 
[/B]delete the acpi_osi=Linux and add acpi=noapic 
the line must be
**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=noapic acpi_backlight=vendor"**
save the document and run in terminal 
```
sudo update-grub
```reboot and see if something fixed. 

If things become worst , then edit again the same line and delete the acpi=noapic . Only this. Do not forget after edit the line to run **sudo update-grub**.


It might be a good idea to look for a newer BIOS version and Update your BIOS (if newer version exists) 

Thanks

---

### Post by kr1sti on 2012-08-07
> **NikTh said:**
> Hi , 

lets clear things out and try something else. 

First , open again the file 
```
gksudo gedit /etc/default/grub
```again find the line [B]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor" 
[/B]delete the acpi_osi=Linux and add acpi=noapic 
the line must be
**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=noapic acpi_backlight=vendor"**
save the document and run in terminal 
```
sudo update-grub
```reboot and see if something fixed. 

If things become worst , then edit again the same line and delete the acpi=noapic . Only this. Do not forget after edit the line to run **sudo update-grub**.


It might be a good idea to look for a newer BIOS version and Update your BIOS (if newer version exists) 

Thanks

Didn't help at all, but I found out something strange. Everytime I increase brightness, my screen seems to go darker and darker, and everytime I decrease brightness, my screen goes lighter and lighter. I actually boot with full brightness, but it seems that when I full brightness, the screen is completely dark. It's a bit hard to explain but I hope you get the point.

---

### Post by NikTh on 2012-08-07
> **kr1sti said:**
> Didn't help at all, but I found out something strange. Everytime I increase brightness, my screen seems to go darker and darker, and everytime I decrease brightness, my screen goes lighter and lighter. I actually boot with full brightness, but it seems that when I full brightness, the screen is completely dark. It's a bit hard to explain but I hope you get the point.

Hi , 
I get the point , but unfortunately don't know the solution. Sorry. 
Just make sure to clear a little the file we "hacked" . 

```
gksudo gedit /etc/default/grub
``` 

find the line  [B]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=noapic acpi_backlight=vendor"

[/B]and make it like this 
**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"**

delete the option acpi=noapic .

Then run in terminal ```
sudo update-grub
``` 

I wish someone know the solution for your problem.
Thanks

---

### Post by Kalanac on 2012-08-07
The backlight problem is a kernel issue, not a driver issue.  A little change was made and now certain backlights play up.  I have the same issue and there are only work arounds, no fixes besides regressing your kernel version.  For all the fuss that is, it's easier just to use the brightness keys.  Here's a thread I created a while ago with several suggestions and discussions about the issue:

[http://ubuntuforums.org/showthread.php?t=1741556](http://ubuntuforums.org/showthread.php?t=1741556)

---

### Post by madjr on 2012-08-07
and what is your laptop model ?

---

### Post by Kalanac on 2012-08-07
Acer Aspire 5736Z laptop. It uses an Intel GMA 4500M integrated GPU


EDIT:  It dawns on me you were asking the original poster, not me :D

---

### Post by kr1sti on 2012-08-07
> **madjr said:**
> and what is your laptop model ?
eMachines g725.

---

### Post by madjr on 2012-08-07
> **kr1sti said:**
> eMachines g725.

have you tried this:

[https://bugs.launchpad.net/ubuntu/+bug/428790](https://bugs.launchpad.net/ubuntu/+bug/428790)

[http://forums.opensuse.org/english/get-technical-help-here/hardware/421859-how-make-brightness-hotkeys-work.html](http://forums.opensuse.org/english/get-technical-help-here/hardware/421859-how-make-brightness-hotkeys-work.html)

---

### Post by kr1sti on 2012-08-07
> **madjr said:**
> have you tried this:

[https://bugs.launchpad.net/ubuntu/+bug/428790](https://bugs.launchpad.net/ubuntu/+bug/428790)

[http://forums.opensuse.org/english/get-technical-help-here/hardware/421859-how-make-brightness-hotkeys-work.html](http://forums.opensuse.org/english/get-technical-help-here/hardware/421859-how-make-brightness-hotkeys-work.html)

Well, both of them mentions the same thing that NikTh told me to do earlier(wich didn't work btw :( ). Got any more ideas? :confused:

Edit: I found a solution, I edited the grub file(gkudo gedit /etc/default/grub) and changed that "quiet splash" to "nomodeset", the problem was solved temporary. Now the screen boots in 800x600 resolution and I cant change brightness. Does anyone have a solution for this?

---

### Post by madjr on 2012-08-07
> **kr1sti said:**
> Well, both of them mentions the same thing that NikTh told me to do earlier(wich didn't work btw :( ). Got any more ideas? :confused:

Edit: I found a solution, I edited the grub file(gkudo gedit /etc/default/grub) and changed that "quiet splash" to "nomodeset", the problem was solved temporary. Now the screen boots in 800x600 resolution and I cant change brightness. Does anyone have a solution for this?

To confirm, you're saying that the problem was solved with your new changes, but then you probably did a reboot or shutdown the computer and after turning it ON again it went into 800x600 ?

---

### Post by kr1sti on 2012-08-08
> **madjr said:**
> To confirm, you're saying that the problem was solved with your new changes, but then you probably did a reboot or shutdown the computer and after turning it ON again it went into 800x600 ?

No, I didn't notice any difference at first, but when I rebooted, it automatically booted with full brightness, but the resolution changed to 800x600(I think) and when I wanted to change resolution, I only had two options: 800x600 and 1024x768, changing to any of them didn't really make any difference at all. Also, I wasn't able to change brightness.

---

### Post by kr1sti on 2012-08-09
Bump

---

### Post by madjr on 2012-08-10
is your normal resolution [1600 x 900]("http://www.notebookcheck.net/Acer-eMachines-G725.16236.0.html")?

where you able to get it back ?

---

### Post by Egonosaur on 2012-08-10
Hello!

On your laptop keyboard, do you have buttons for increasing/decreasing brightness?
If so have you tested using them using FN or without? Depends on the layout :)

---

### Post by kr1sti on 2012-08-10
> **madjr said:**
> is your normal resolution [1600 x 900]("http://www.notebookcheck.net/Acer-eMachines-G725.16236.0.html")?

where you able to get it back ?
Yes, that's my normal resolution, but I wasn't able to get it back.

> **Egonosaur said:**
> Hello!

On your laptop keyboard, do you have buttons for increasing/decreasing brightness?
If so have you tested using them using FN or without? Depends on the layout :)

Yes, but that's the problem. When I use them to increase/decrease brightness, the screen brightness won't change, but that window(whatever it's called) appears with that bar going left/right. Little tough for me to explain :P

---

### Post by madjr on 2012-08-11
> **kr1sti said:**
> Yes, that's my normal resolution, but I wasn't able to get it back.



Yes, but that's the problem. When I use them to increase/decrease brightness, the screen brightness won't change, but that window(whatever it's called) appears with that bar going left/right. Little tough for me to explain :P

maybe this will work for your res.

[http://www.vxbus.com/software/linux/148-how-to-change-monitor-resolution-in-ubuntu-1204.html](http://www.vxbus.com/software/linux/148-how-to-change-monitor-resolution-in-ubuntu-1204.html)

[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)

---

### Post by madjr on 2012-08-11
for the brightness issue, you have a **GMA 4500M** card, so you can try a few things with that:


[http://askubuntu.com/questions/60579/intel-gma-4500m-screen-resolution-problem](http://askubuntu.com/questions/60579/intel-gma-4500m-screen-resolution-problem)

[http://ubuntuforums.org/showthread.php?t=1562743](http://ubuntuforums.org/showthread.php?t=1562743)

[http://tehpost.blogspot.com/2012/04/ubuntu-linux-cant-adjust-acer.html](http://tehpost.blogspot.com/2012/04/ubuntu-linux-cant-adjust-acer.html)

---


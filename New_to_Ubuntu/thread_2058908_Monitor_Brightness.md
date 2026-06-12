---
title: "Monitor Brightness"
date: 2012-09-16
forum: New to Ubuntu
---

### Post by 3dmatrix on 2012-09-16
I use Ubuntu 12.04 on a Samsung NP300E5Z laptop. Since a long time i had the problem in controling the monitor brightness but i used the following codes (i dont know which one worked) and it started getting controlled by the keyboard and in other ways. 

in /etc/rc.local file added
echo 0 > /sys/class/backlight/acpi_video0/brightness
rfkill block bluetooth
rfkill block wifi

sudo modprobe video

sudo setpci -s 00:02.0 f4.b=FF

edited the /etc/default/grub file and added acpi_backlight=vendor
to make the line as
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"

(this last option i have still not tried for 12.04)

But since i installed 12.04 its behaving wierd. As soon as i use the keys to control the brightness the system becomes unstable and i have to logout as soon as i can. Can any one provide some help with this ?

.

---

### Post by Toz on 2012-09-16
You might want to give this PPA a try: [https://launchpad.net/~voria/+archive/ppa]("https://launchpad.net/~voria/+archive/ppa"). Its specific for samsung laptops and fixes a number of issues, including brightness. 

(Probably a good idea to remove:  

  *echo 0 > /sys/class/backlight/acpi_video0/brightness*, 
  *sudo modprobe video*, and 
  *sudo setpci -s 00:02.0 f4.b=FF* 

from your /etc/rc.local file if you're going to try the PPA).

---

### Post by 3dmatrix on 2012-09-17
> **Toz said:**
> You might want to give this PPA a try: [https://launchpad.net/~voria/+archive/ppa]("https://launchpad.net/~voria/+archive/ppa"). Its specific for samsung laptops and fixes a number of issues, including brightness. 

(Probably a good idea to remove:  

  *echo 0 > /sys/class/backlight/acpi_video0/brightness*, 
  *sudo modprobe video*, and 
  *sudo setpci -s 00:02.0 f4.b=FF* 

from your /etc/rc.local file if you're going to try the PPA).

It used to work fine in Ubuntu 11.10 so why not now ?
Is that PPA official ?

---

### Post by NikTh on 2012-09-17
> **3dmatrix said:**
> 
Is that PPA official ?
[https://launchpad.net/~voria/+archive/ppa](https://launchpad.net/~voria/+archive/ppa)
> You can update your system with unsupported packages from           this untrusted PPAI guess not. 

Can you  post the results ? 

```
cat /proc/cmdline 
lspci -nnk | grep -iA2 vga
env | grep DESK
cat /etc/modules
cat /etc/rc.local
```Thanks

---

### Post by 3dmatrix on 2012-09-18
> **NikTh said:**
> 

Can you  post the results ? 

```
cat /proc/cmdline 
lspci -nnk | grep -iA2 vga
env | grep DESK
cat /etc/modules
cat /etc/rc.local
```Thanks

cat /proc/cmdline 
BOOT_IMAGE=/boot/vmlinuz-3.2.0-30-generic-pae root=UUID=50ca6d4e-10ff-4cb6-a2ac-da5e3f8454fd ro quiet splash vt.handoff=7

-----------------------------------------------------

lspci -nnk | grep -iA2 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0106] (rev 09)
	Subsystem: Samsung Electronics Co Ltd Device [144d:c606]
	Kernel driver in use: i915
-----------------------------------------------------

env | grep DESK
DESKTOP_SESSION=gnome-shell
GNOME_DESKTOP_SESSION_ID=this-is-deprecated
XDG_CURRENT_DESKTOP=GNOME
-----------------------------------------------------
cat /etc/modules
# /etc/modules: kernel modules to load at boot time.

# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp

-----------------------------------------------------

#cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

echo 0 > /sys/class/backlight/acpi_video0/brightness
rfkill block bluetooth
rfkill block wifi

exit 0

---

### Post by NikTh on 2012-09-19
Please remove the line 
```
echo 0 > /sys/class/backlight/acpi_video0/brightness
``` from /etc/rc.local
```
gksudo gedit /etc/rc.local
``` 

Then add the parameter acpi_backlight=vendor to kernel , via grub 
```
sudo sed -i 's/GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"/GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"/g' /etc/default/grub
```Then update grub 
```
sudo update-grub
```Reboot and see . 

If nothing happen , give the results of 
```
cat /proc/cmdline 
cat /etc/default/grub | grep GRUB_CMDLINE
cat /etc/rc.local 
```Thanks

---

### Post by 3dmatrix on 2012-09-19
When i used the following code it gave some errors :

sudo sed -i 's/echo 0 > /sys/class/backlight/acpi_video0/brightness//g' /etc/rc.local
sed: -e expression #1, char 17: unknown option to `s'
so i manually commented that line. 

After rebooting the system does not crashes when i use the keyboard shortcut to control brightness but it does not work as expected. The system starts with full brightness and then i can use the keys to reduce the brightness to minimum but when i try to increase the brightness then it does not increases beyond (say about) 20 - 25 %.


cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.2.0-30-generic-pae root=UUID=50ca6d4e-10ff-4cb6-a2ac-da5e3f8454fd ro quiet splash acpi_backlight=vendor vt.handoff=7

cat /etc/default/grub | grep GRUB_CMDLINE
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
GRUB_CMDLINE_LINUX=""

cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

# echo 0 > /sys/class/backlight/acpi_video0/brightness
rfkill block bluetooth
rfkill block wifi

exit 0

---

### Post by NikTh on 2012-09-19
> **3dmatrix said:**
> When i used the following code it gave some errors :

sudo sed -i 's/echo 0 > /sys/class/backlight/acpi_video0/brightness//g' /etc/rc.local
sed: -e expression #1, char 17: unknown option to `s'
so i manually commented that line.  

You did Good. It was my bad. Sorry. I edited my post. Thanks

> **3dmatrix said:**
> After rebooting the system does not crashes when i use the keyboard shortcut to control brightness but it does not work as expected. The system starts with full brightness and then i can use the keys to reduce the brightness to minimum but when i try to increase the brightness then it does not increases beyond (say about) 20 - 25 %.

Try to use 2 more parameters. One at time. 
acpi_osi= 
OR 
acpi_osi=Linux 

change the parameter manually , ```
gksudo gedit /etc/default/grub
```go to line **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"**
remove the parameter acpi_backlight=vendor and add the two above . ONE at time. 
[B]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=" 
OR 
[/B]**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"**  

do not forget after you save the document to run ```
sudo update-grub
``` 

See if any of two parameters works better. 

Thanks

---

### Post by 3dmatrix on 2012-09-20
Thanx ! The brightness can be controlled by using "GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=" with the other one it started geting unstable. 

BUT the system forgets the brightness level when it reboots and goes back to 100 %.
Any solution to this ?


.

---

### Post by NikTh on 2012-09-20
> **3dmatrix said:**
> Thanx ! The brightness can be controlled by using "GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="  
Good news ! OK

> **3dmatrix said:**
> BUT the system forgets the brightness level when it reboots and goes back to 100 %.
Any solution to this ? 

Maybe , we can try one two things. If you can control the brightness with a command (any command) from terminal , then we can add this command , either to /etc/rc.local (if needs root privileges) , or to startup applications. 

I assume you cannot control brightness with this command 

```
sudo setpci -s 00:02.0 F4.B=XX
``` where XX is a number from 0(zero) to FF. 

Can you control brightness with above command ? If not then give the results of bellow commands 
```
lspci -nnk | grep -iA2 vga
ls /sys/class/
```Thanks

---

### Post by 3dmatrix on 2012-09-21
I turnrned the brightness to minimum and then executed the command :
sudo setpci -s 00:02.0 F4.B=FF
but there was no change.

lspci -nnk | grep -iA2 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0106] (rev 09)
	Subsystem: Samsung Electronics Co Ltd Device [144d:c606]
	Kernel driver in use: i915

ls /sys/class/
ata_device  devfreq   i2c-adapter  mmc_host      rfkill        spi_master
ata_link    dma       ieee80211    net           rtc           spi_transport
ata_port    dmi       input        pci_bus       scsi_device   thermal
backlight   drm       leds         power_supply  scsi_disk     tty
bdi         firmware  mdio_bus     ppdev         scsi_generic  usbmon
block       gpio      mei          ppp           scsi_host     vc
bluetooth   graphics  mem          printer       sound         video4linux
bsg         hwmon     misc         regulator     spi_host      vtconsole

---

### Post by NikTh on 2012-09-21
OK. 

give the results of this command 

```
ls /sys/class/backlight/*
```

I am going here step-by-step cuz I don't want to make any mistakes. 

Thanks

---

### Post by 3dmatrix on 2012-09-21
ls /sys/class/backlight/*

/sys/class/backlight/acpi_video0:
actual_brightness  brightness  max_brightness  subsystem  uevent
bl_power           device      power           type

/sys/class/backlight/intel_backlight:
actual_brightness  brightness  max_brightness  subsystem  uevent
bl_power           device      power           type

/sys/class/backlight/samsung:
actual_brightness  brightness  max_brightness  subsystem  uevent
bl_power           device      power           type

---

### Post by NikTh on 2012-09-21
&#927;&#922;. 

Take a look inside this file ```
cat /sys/class/backlight/intel_backlight/brightness
``` and try to change the actual number and see if that affects your monitor brightness. 

eg : 
If the result of above command is 976 , then apply below commands 
```
sudo -i 
echo 800 > /sys/class/backlight/intel_backlight/brightness
exit
```did you notice any change in monitor brightness ? 

Thanks

---

### Post by 3dmatrix on 2012-09-21
Well b4 i make that change, i would like to tell you that i visited that folder and it has three files actual_brightness, brightness, max_brightness and all have the value 4648 which i got from the command :

cat /sys/class/backlight/intel_backlight/brightness
4648

So what should i do next ?

---

### Post by NikTh on 2012-09-21
> **3dmatrix said:**
> 
cat /sys/class/backlight/intel_backlight/brightness
4648

So what should i do next ?

Try ```
sudo -i 
echo 4000 > /sys/class/backlight/intel_backlight/brightness
exit
``` 

see if 2nd command reduces your monitor brightness. 

The idea here is to find a value that meet your needs. 
Then we can add this command in rc.local and your problem solved.

Thanks

---

### Post by 3dmatrix on 2012-09-22
> **NikTh said:**
> Try ```
sudo -i 
echo 4000 > /sys/class/backlight/intel_backlight/brightness
exit
``` 

see if 2nd command reduces your monitor brightness. 

The idea here is to find a value that meet your needs. 
Then we can add this command in rc.local and your problem solved.

Thanks

YES ! It changes the brightness :)
BUT goes back to the original value of 4648 every time i login or reboot.

For most of my work value between 500 - 1000 is fine. For some work i might even bring it down to 100 and for some work (like watching video or playing games) it can go up to 2000 - 3000.

Another problem that i see is : If i lower the brightness by that command and then use the keyboard shortcut to change the brightness then the brightness first 'jumps' to maximum !

.

---

### Post by NikTh on 2012-09-22
> **3dmatrix said:**
> 
BUT goes back to the original value of 4648 every time i login or reboot. 

We will fix that.

> **3dmatrix said:**
> For most of my work value between 500 - 1000 is fine. For some work i might even bring it down to 100 and for some work (like watching video or playing games) it can go up to 2000 - 3000. 
You can adjust the brightness with Fn keys combo . The problem is on boot. 

What brightness you want when you boot your PC ? What is the value ?  

> **3dmatrix said:**
> Another problem that i see is : If i lower the brightness by that command and then use the keyboard shortcut to change the brightness then the brightness first 'jumps' to maximum !.
This is not a problem. This is normal (happening to me too). 
When you use Fn keys , the value in /brightness first goes to max ,and then you can reduce it . 

Your only problem now , is the brightness on boot - login. Just tell me the value that meet your needs. 

Thanks

---

### Post by 3dmatrix on 2012-09-22
I think 1000 should be perfect !

When i manually try to change the value to 1000 in that file. It does not lets me change it. If i change the permission of the file then it changes and saves but the value in the file actually remains the same.

.

---

### Post by NikTh on 2012-09-22
Lets try and see .. 

first open the file rc.local 

```
gksudo gedit /etc/rc.local
```add bellow line , **before exit 0**

```
(sleep 3 ; echo 1000 > /sys/class/backlight/intel_backlight/brightness) &
```save the file and reboot your PC. 

Hopefully the brightness will be adjusted in this value when you login. 

Thanks

---

### Post by 3dmatrix on 2012-09-22
As of now, seems perfect  :)
Thanx Buddy !

---

### Post by NikTh on 2012-09-22
> **3dmatrix said:**
> as of now, seems perfect  :)



good! :)

---

### Post by 3dmatrix on 2012-09-24
I updated the system yesterday and since then there is again problem of a different kind. Now the system after login / reboot starts with maximum brightness and i can just reduce the brightness by about 15 - 20 % only.

The rc.local file is unchanged.
/sys/class/backlight earlier had three links now has two links
/sys/class/backlight/intel_backlight has files with the following values :
actual_brightness - 3718
brightness - 1000
max_brightness - 4648

Though i can control the brightness by the command :
echo 1000 > /sys/class/backlight/intel_backlight/brightness
but as soon as i use the keyboard shortcuts i again goes back to the maximum level and can be reduced only by about 10% or by the command.

---

### Post by NikTh on 2012-09-24
&#927;&#954;. 

Give the results of these commands 

```
cat /etc/default/grub | grep GRUB_CMDLINE
ls /sys/class/backlight/*
sudo cat /var/log/apt/term.log | tail -n 40
```

Thanks

---

### Post by 3dmatrix on 2012-09-24
**cat /etc/default/grub | grep GRUB_CMDLINE**
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="
GRUB_CMDLINE_LINUX=""

**ls /sys/class/backlight/***
/sys/class/backlight/acpi_video0:
actual_brightness  brightness  max_brightness  subsystem  uevent
bl_power           device      power           type

/sys/class/backlight/intel_backlight:
actual_brightness  brightness  max_brightness  subsystem  uevent
bl_power           device      power           type

**sudo cat /var/log/apt/term.log | tail -n 40 **
Setting up skype (4.0.0.8-0oneiric1) ...
Log ended: 2012-09-25  05:00:03

Log started: 2012-09-25  05:40:05
(Reading database ... 241047 files and directories currently installed.)
Removing opera ...
update-alternatives: using /usr/bin/chromium-browser to provide /usr/bin/x-www-browser (x-www-browser) in auto mode.
update-alternatives: using /usr/bin/chromium-browser to provide /usr/bin/gnome-www-browser (gnome-www-browser) in auto mode.
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
WARNING:softwarecenter.db.update:setlocale failed with 'unsupported locale setting'
Updating software catalog...this may take a moment.
INFO:softwarecenter.db.pkginfo_impl.aptcache:aptcache.open()
Software catalog update was successful.
Processing triggers for software-center ...
WARNING:softwarecenter.db.update:setlocale failed with 'unsupported locale setting'
Updating software catalog...this may take a moment.
INFO:softwarecenter.db.pkginfo_impl.aptcache:aptcache.open()
Software catalog update was successful.
Processing triggers for man-db ...
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for menu ...
Log ended: 2012-09-25  05:40:50

---

### Post by NikTh on 2012-09-25
Hi , 

remove the parameter **acpi_osi=** , also commented the line echo 1000 > /sys/class/backlight/intel_backlight/brightness in **/etc/rc.local **
make it like this 
[B][COLOR=Red]#[/COLOR]echo 1000 > /sys/class/backlight/intel_backlight/brightness 

[/B]Reboot your pc and see the behavior. 

Do not forget to run ```
sudo update-grub
``` before reboot.Thanks

---

### Post by 3dmatrix on 2012-09-26
Sorry for the delay.
I made the changes in the following files :
[B]/etc/rc.local
/etc/default/grub[/B]
but nothing happened.

It is very difficult if we make things go right and there is an upgrade and we have to do the entire investigation once again from scratch ! Everytime !

.

---

### Post by 3dmatrix on 2012-09-28
Any Help ?

---

### Post by NikTh on 2012-09-28
Sorry , but your problem is weird. It seems that corrected , but... 

Try again the parameters. Maybe something changed with the update and now you can use other parameters to adjust your brightness correctly. 

I know that this is a pain in the .... , but you must try again. You need 3 reboots. One with each parameter. 

1. acpi_osi= 
2.acpi_osi=Linux 
3.acpi_backlight=vendor 

If non of above do something then try to combine each parameter with this parameter : acpi=force  

Do not forget to run ```
sudo update-grub
``` to pass the parameters to the kernel. 

Thanks

---

### Post by 3dmatrix on 2012-09-29
> **NikTh said:**
> 
1. acpi_osi= 
2.acpi_osi=Linux 
3.acpi_backlight=vendor 

If non of above do something then try to **[COLOR="Red"]combine each parameter with this parameter [/COLOR]** : acpi=force 

I am sorry but i did not understand the part marked in RED. I try once each of the codes in 1, 2 and 3 and if it does not works then . . . . (i did not understand this last part) ? Can you kindly give some example.

---

### Post by 3dmatrix on 2012-10-06
> **NikTh said:**
> Sorry , but your problem is weird. It seems that corrected , but... 

Try again the parameters. Maybe something changed with the update and now you can use other parameters to adjust your brightness correctly. 

I know that this is a pain in the .... , but you must try again. You need 3 reboots. One with each parameter. 

1. acpi_osi= 
2.acpi_osi=Linux 
3.acpi_backlight=vendor 

If non of above do something then try to combine each parameter with this parameter : acpi=force  

Do not forget to run ```
sudo update-grub
``` to pass the parameters to the kernel. 

Thanks

in /etc/default/grub at made the following changes (one at a time)

1.acpi_osi= 
2.acpi_osi=Linux 
3.acpi_backlight=vendor 
4.acpi_osi= acpi=force
5.acpi_osi=Linux acpi=force
6.acpi_backlight=vendor acpi=force

with sudo update-grub and rebooting after each change but nothing happened.

Then i changed it to acpi_osi= 
and removed the # from 
echo 1000 > /sys/class/backlight/intel_backlight/brightness 
in /etc/rc.local file and updated grub and after rebooting the brightness would remain low as long as i do not use the keyboard shortcut for changing the brightness. Once i do so, it jumps to maximum and then can be brought down only by abt 10%. But from system settings > Brightness & Lock i can use the slider to reduce the brightness.

.

---

### Post by 3dmatrix on 2012-10-21
As we have still not been able to figure out any good solution to this problem, and i have to use the System Settings > Brightness and Lock slider to adjust the brightness, i was thinking of putting the Brightness and Lock applet / shortcut on the top Gnome 3 taskbar (as shown in the attachment). Can any one tell me how we could do that ? I have seen this can be done in Mint Cinnamon so may be we can do it here too. That won't solve the problem but may be reduce the number of clicks that i have to do every time to change the brightness !

---

### Post by NikTh on 2012-10-22
Hi, 

what are the entries now in /etc/default/grub  file ? 

```
cat /etc/default/grub
``` . Its very weird that none of the parameters worked for you. You tested them correctly as I can see. 

But is good that you can increase or decrease the brightness from the Brightness & Lock. 

See [this]("http://ubuntuforums.org/showthread.php?t=2067894") thread and especially the 6th answer ([pqwoerituytrueiwoq]("http://ubuntuforums.org/member.php?u=865458")'s answer). Try to create this script and see if you can create some shortcuts to increase an decrease brightness.

Thanks

---

### Post by Linuxisfast on 2012-10-22
The easiest solution that works minus any modification is to install xbacklight and set the value in startup, for instance my laptop is set at 80% so my command looks like xbacklight -set 80 and during startup, that value is set automatically, I use it in conjunction with Redshift and both work out very well.

---

### Post by 3dmatrix on 2012-10-22
> **Linuxisfast said:**
> The easiest solution that works minus any modification is to install xbacklight and set the value in startup, for instance my laptop is set at 80% so my command looks like xbacklight -set 80 and during startup, that value is set automatically, I use it in conjunction with Redshift and both work out very well.

I do not think xbacklight works on my system

---

### Post by 3dmatrix on 2012-10-22
> **NikTh said:**
> Hi, 

what are the entries now in /etc/default/grub  file ? 

```
cat /etc/default/grub
``` . Its very weird that none of the parameters worked for you. You tested them correctly as I can see. 

But is good that you can increase or decrease the brightness from the Brightness & Lock. 

See [this]("http://ubuntuforums.org/showthread.php?t=2067894") thread and especially the 6th answer ([pqwoerituytrueiwoq]("http://ubuntuforums.org/member.php?u=865458")'s answer). Try to create this script and see if you can create some shortcuts to increase an decrease brightness.

Thanks
[B]
cat /etc/default/grub[/B]

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="**
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

---

### Post by 3dmatrix on 2012-10-22
> **NikTh said:**
> Try to create this script and see if you can create some shortcuts to increase an decrease brightness.

Thanks

Yes that is what i wish to know, how can we place ANY shortcut on that Gnome 3 task bar ?

---

### Post by NikTh on 2012-10-23
If by > **3dmatrix said:**
> how can we place ANY shortcut on that **Gnome 3 **task bar ?
gnome 3 you mean the gnome-shell Environment , then try to search here : [https://extensions.gnome.org/](https://extensions.gnome.org/) for an extension. You install them by clicking in the light button. 

Thanks

---

### Post by 3dmatrix on 2012-10-23
> **NikTh said:**
> If by 
gnome 3 you mean the gnome-shell Environment , then try to search here : [https://extensions.gnome.org/](https://extensions.gnome.org/) for an extension. You install them by clicking in the light button. 

Thanks

In Gnome 2 (classic) we could add anything that was in the main menu, in to taskbar. It was so simple. Even user commands could be added. But now we have to add third party extensions. Why are things being made less user friendly ? There must be some where we could edit and add path to applications, to be displayed on the top bar.

---


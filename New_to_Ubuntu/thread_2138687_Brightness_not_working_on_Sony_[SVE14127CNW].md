---
title: "Brightness not working on Sony [SVE14127CNW]"
date: 2013-04-24
forum: New to Ubuntu
---

### Post by gautamverma on 2013-04-24
I have tried both the proprietary drivers(fglrx) given under Software sources->Additional drivers then computer opens in command line mode.  I have tried all 

I have also tried manually installing amd-driver-installer-catalyst-13.1-linux-x86.x86_64 but it also failed. 
I followed this thread([http://ubuntuforums.org/showthread.php?t=2088190](http://ubuntuforums.org/showthread.php?t=2088190)) but no change in brightness.
```

gautam@gautam-laptop:~$ cat /proc/cmdline 
BOOT_IMAGE=/boot/vmlinuz-3.5.0-17-generic root=UUID=706abb01-8cff-48d5-86d6-4812dc2e86ad ro quiet splash vt.handoff=7

``````

gautam@gautam-laptop:~$ for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
/sys/class/backlight/acpi_video0
5
15

``````

gautam@gautam-laptop:~$ sudo dmidecode -s system-manufacturer
[sudo] password for gautam: 
Sony Corporation

``````

gautam@gautam-laptop:~$ sudo dmidecode -s system-product-name
SVE14127CNW

``````

gautam@gautam-laptop:~$ sudo lspci -vnn | grep -A12 VGA
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Thames [Radeon 7500M/7600M Series] [1002:6841] (prog-if 00 [VGA controller])
    Subsystem: Sony Corporation Device [104d:90aa]
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f7e20000 (64-bit, non-prefetchable) [size=128K]
    I/O ports at e000 [size=256]
    Expansion ROM at f7e00000 [disabled] [size=128K]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Legacy Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [150] Advanced Error Reporting
    Kernel driver in use: radeon

``````

gautam@gautam-laptop:~$ echo 15 | sudo tee /sys/class/backlight/acpi_video0/brightness
15

``````

gautam@gautam-laptop:~$ echo 5 | sudo tee /sys/class/backlight/acpi_video0/brightness
5

``````

gautam@gautam-laptop:~$ acpi_listen
video LCD 00000087 00000000
video VGA 00000081 00000000
video VGA 00000081 00000000
video LCD 00000087 00000000
video VGA 00000081 00000000
video VGA 00000081 00000000

```

---

### Post by Toz on 2013-04-25
Hello and welcome to the forums.
> **gautamverma said:**
> gautam@gautam-laptop:~$ cat /proc/cmdline 
BOOT_IMAGE=/boot/vmlinuz-3.5.0-17-generic root=UUID=706abb01-8cff-48d5-86d6-4812dc2e86ad ro quiet splash vt.handoff=7
Have you tried the **acpi_backlight=vendor** kernel boot paramater (see the Kernel Boot Parameters link in my signature for information on how)?
> gautam@gautam-laptop:~$ for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
/sys/class/backlight/acpi_video0
5
15
gautam@gautam-laptop:~$ echo 15 | sudo tee /sys/class/backlight/acpi_video0/brightness
15
gautam@gautam-laptop:~$ echo 5 | sudo tee /sys/class/backlight/acpi_video0/brightness
5
Does manually echoing the value 5 change the actual brightness?
> gautam@gautam-laptop:~$ acpi_listen
video LCD 00000087 00000000
video VGA 00000081 00000000
video VGA 00000081 00000000
video LCD 00000087 00000000
video VGA 00000081 00000000
video VGA 00000081 00000000
Which of these are displayed when the brightness up key is pressed and which are displayed when the brighntess down key is pressed?

---

### Post by gautamverma on 2013-04-25
> **Toz said:**
> Hello and welcome to the forums.

Have you tried the **acpi_backlight=vendor** kernel boot paramater (see the Kernel Boot Parameters link in my signature for information on how)?

Does manually echoing the value 5 change the actual brightness?

Which of these are displayed when the brightness up key is pressed and which are displayed when the brighntess down key is pressed?
```

Brightness key down is pressed
video LCD 00000087 00000000
video VGA 00000081 00000000

Brightness Key up is pressed
video LCD 00000086 00000000
video VGA 00000081 00000000

```
No manually eching the value 5 doesn't change the brightness. i did echo by this command echo 5 | sudo tee /sys/class/backlight/acpi_video0/brightness

 I tried adding that parameter to kernal, then the computer opens in the commad line mode. (No window type display.)

I have even third party drivers supplied by ubuntu repositories but none worked.

---

### Post by gautamverma on 2013-04-25
One thing to add that i am using 12.10 old build(february or march) , in the latest build no display showiing at all(when i trying ubuntu without installing), only a flickering line of 5 pixel height on the top.

---

### Post by Toz on 2013-04-25
> I tried adding that parameter to kernal, then the computer opens in the commad line mode. (No window type display.)

Adding that entry shouldn't have caused that problem. Did you add the entry temporarily during boot or permanently by editing /etc/default/grub. If the later, can you please post back the contents of /etc/default/grub?

---

### Post by gautamverma on 2013-04-25
i added the entry to /etc/default/grub
```

The contents of /etc/default/grub
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

```
I downloaded and tried 13.04, no display at all only a blank lighted screen.

---

### Post by gautamverma on 2013-04-26
i tried 13.04 with nomodeset parameter to kernal then it opened in the commad line mode i.e with no GUI.

---

### Post by Toz on 2013-04-26
You should create a new thread for 13.04 and blank screen with ATi drivers, there are others here that might be able to provide assistance with getting the driver installed.

As for 12.10 and grub, I don't see the acpi_backlight entry in your config file. Make sure that the line:
> GRUB_CMDLINE_LINUX=""
...reads:
```
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"
```
...then run:
```
sudo update-grub
```
...and reboot.

---

### Post by gautamverma on 2013-04-29
> **Toz said:**
> You should create a new thread for 13.04 and blank screen with ATi drivers, there are others here that might be able to provide assistance with getting the driver installed.

As for 12.10 and grub, I don't see the acpi_backlight entry in your config file. Make sure that the line:

...reads:
```
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"
```
...then run:
```
sudo update-grub
```
...and reboot.


I did add the entry as you said but nothing happened, brightness is still at maximum. The only change is now the brightness slider is not showing up when i am increasing or decreasing the brightness.

---

### Post by Toz on 2013-04-29
Can you try the following kernel parameter?
```
GRUB_CMDLINE_LINUX="acpi_osi="
```

Remember to run:
```
sudo update-grub
```
...afterwards.

If it doesn't work, can you post back the following:
```
cat /proc/cmdline
sudo lspci -vnn | grep -A12 VGA
```
...and the link that is generated when you run:
```
pastebinit /var/log/dmesg
```

---

### Post by gautamverma on 2013-05-08
output of cat /proc/cmdline 
```

BOOT_IMAGE=/boot/vmlinuz-3.5.0-17-generic root=UUID=706abb01-8cff-48d5-86d6-4812dc2e86ad ro acpi_osi= quiet splash vt.handoff=7

```

output of sudo lspci -vnn | grep -A12 VGA

```

    Subsystem: Sony Corporation Device [104d:90aa]
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f7e20000 (64-bit, non-prefetchable) [size=128K]
    I/O ports at e000 [size=256]
    Expansion ROM at f7e00000 [disabled] [size=128K]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Legacy Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [150] Advanced Error Reporting
    Kernel driver in use: radeon

```

output of pastebinit /var/log/dmesg
[http://paste.ubuntu.com/5644257/](http://paste.ubuntu.com/5644257/)

---

### Post by Toz on 2013-05-08
Is brightness still not working with "acpi_osi=" ?

With this parameter in effect, do you have any other interface than acpi_vidoe0 in /sys/class/backlight? If so, have you tried to manually echo values there?

---

### Post by gautamverma on 2013-05-08
> **Toz said:**
> Is brightness still not working with "acpi_osi=" ?

With this parameter in effect, do you have any other interface than acpi_vidoe0 in /sys/class/backlight? If so, have you tried to manually echo values there?

I am extremely sorry not to add that. Yeah brightness still at maximum and it is not changing with "acpi_osi=" parameter.

No i don't have any other interface other than acpi_video0.

How to manually echo values their??

---

### Post by Toz on 2013-05-08
Can you try each of the following kernel parameters, one at a time, and check:
- the number of backlight interfaces in /sys/class/backlight
- whether echoing any value in the brightness file for any of the interfaces affects brightness

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"
```

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_osi=Linux"
```

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor"
```

-----

Can you also try the following methods to see if either changes the brightness:
```

sudo setpci -s 01:00.0 F4.B=7f
sudo setpci -s 01:00.0 F4.B=ff
sudo setpci -s 01:00.0 F4.B=00
```

...and...
```
xrandr --output <outputname> --brightness 0.8
```
...where <outputname> can be retrieved via:
```
xrandr | grep " connected"
```

---

### Post by gautamverma on 2013-05-08
> **Toz said:**
> Can you try each of the following kernel parameters, one at a time, and check:
- the number of backlight interfaces in /sys/class/backlight
- whether echoing any value in the brightness file for any of the interfaces affects brightness


```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```
No change and 1 interface(acpi_video0)

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"
```
No change and even the brightness slider disappear and no interface.(no folder in /sys/class/backlight)

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_osi=Linux"
```
No change and 1 interface(acpi_video0)

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor"
```
No change and even the brightness slider disappear and no interface.(no folder in /sys/class/backlight)

-----

Can you also try the following methods to see if either changes the brightness:
```

sudo setpci -s 01:00.0 F4.B=7f
sudo setpci -s 01:00.0 F4.B=ff
sudo setpci -s 01:00.0 F4.B=00
```

None of these worked.

...and...
```
xrandr --output <outputname> --brightness 0.8
```
...where <outputname> can be retrieved via:
```
xrandr | grep " connected"
```

It worked. The control is not fine but kind of ok. 0.7 is fine for me.

---

### Post by Toz on 2013-05-08
I honestly think the answer lies in getting the proprietary ATI drivers installed. It might be worth creating a new thread and having someone with ATI experience assist with getting them installed.

If you choose to use the opensource radeon drivers, you will probably need to create a bug report for this.

---

### Post by gautamverma on 2013-05-09
> **Toz said:**
> I honestly think the answer lies in getting the proprietary ATI drivers installed. It might be worth creating a new thread and having someone with ATI experience assist with getting them installed.

If you choose to use the opensource radeon drivers, you will probably need to create a bug report for this.

i have already tried using both the proprietary ATI drivers present under other softwares even downloaded it and tried to set up but everything failed. BTW it support is not only broken in ubuntu, but fedora 18 is also shows no display.

Thanks a lot for your help. I couldn't have got a fix without your help.

---


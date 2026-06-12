---
title: "HELP! Multiple problems with Lucid Lynx."
date: 2010-05-27
forum: Philippine Team
---

### Post by echo2knight on 2010-05-27
Guys, hi, can you help me with my ubuntu lucid lynx installation. Here are the problems that I'm encountering:

1. LCD brightness are set to the maximum. Keypad shortcuts adjusting the level of brightness are working, as shown by the brightness indicator. However, the brightness remain at the maximum;

2. Sounds are played using the built-in speakers and muted when an earphone is plugged in the earphone jack as expected, however, there are no sounds being played from the earphone. Only a short "pop" when you insert the said earphone;

3. Keyboard shortcut enabling/disabling touchpad is not working (Fn+touchpad key). All Fn shortcut keys seems to be functioning.


The details of my laptop are as follows:
BLUE STANNUM - SRW(351) --> [http://www.ilikeblue.net/products/laptop.htm](http://www.ilikeblue.net/products/laptop.htm)
Processor: Intel Core 2 Duo T5250 (1.50 GHz)
Memory   : 4GB DDR2
Display  : 14.1" Wide XGA
Video    : Intel GMA X3100
Harddisk : 250GB SATA
OD       : DVD Dual
Wi-Fi    : Intel Pro / Wireless 3945abg
Features : Card reader, Bluetooth


** All hardware are working under M$ windoze using their drivers.
** Any help regarding the matter will highly be appreciated. Thanks in advance.

---

### Post by echo2knight on 2010-05-28
Walang pang reply....

Taas ko lang po!

---

### Post by loell on 2010-05-28
1. for the brightness, probably try this,
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/555122/comments/20](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/555122/comments/20)

2. Maybe it's just a matter of adjusting your sound preference from the sound applet?


3. possibly try this too for enabling/disabling touchpad. [http://ubuntuforums.org/showthread.php?t=1457030](http://ubuntuforums.org/showthread.php?t=1457030)

---

### Post by echo2knight on 2010-05-30
> **loell said:**
> 1. for the brightness, probably try this,
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/555122/comments/20](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/555122/comments/20)

2. Maybe it's just a matter of adjusting your sound preference from the sound applet?


3. possibly try this too for enabling/disabling touchpad. [http://ubuntuforums.org/showthread.php?t=1457030](http://ubuntuforums.org/showthread.php?t=1457030)


Brod, thank you for the inputs. Tried them all to no avail.

Any other proposed solution to the above problems? Thanks!!!

---

### Post by stjohnmedrano on 2010-05-30
was it an upgrade or fresh install? after your installation ganyan napa talaga or hindi pa? ba

---

### Post by echo2knight on 2010-05-30
> **stjohnmedrano said:**
> was it an upgrade or fresh install? after your installation ganyan napa talaga or hindi pa? ba

It is a fresh install. These problems are present with previous versions and other distros, considering that my lappy is a locally produced one.

Looking for possible solutions with the above problems.

---

### Post by Ravskie on 2010-05-31
2. Sounds are played using the built-in speakers and muted when an earphone is plugged in the earphone jack as expected, however, there are no sounds being played from the earphone. Only a short "pop" when you insert the said earphone;

sir may gamit ka bang mixer sa sound ???? na try nyo na po ba install gnome alsa mixer .... ?

---

### Post by echo2knight on 2010-06-01
> **Ravskie said:**
> 2. Sounds are played using the built-in speakers and muted when an earphone is plugged in the earphone jack as expected, however, there are no sounds being played from the earphone. Only a short "pop" when you insert the said earphone;

sir may gamit ka bang mixer sa sound ???? na try nyo na po ba install gnome alsa mixer .... ?

Installed gnome-alsamixer, the problem persists.

However, the curious thing is, when I mute the earphone in the alsamixer, the sound is muted in the built-in speaker; unmute it, and sound plays from the said speaker. Same thing happen, as expected, from the speaker "mute" radio button.

Any command that I can execute for you to see my configurations?

---

### Post by echo2knight on 2010-06-13
Taas ko lang po!

---

### Post by aljoriz on 2010-06-13
Paki try:

Kabit mo earphones
click on the speaker icon then Sound Preferences

In the Sound Preferences look for a tab OUTPUT click it
then sa CONNECTOR there should be a pull down menu click that and select ANALOG HEADPHONES (the default is set to ANALOG OUTPUT meaning internal speakers)

---

### Post by antoniomiguel on 2010-06-14
On a terminal, key in "lspci | grep VGA" without the quotes.

Please post the results after

---

### Post by echo2knight on 2010-06-14
> **antoniomiguel said:**
> On a terminal, key in "lspci | grep VGA" without the quotes.

Please post the results after

Thanks Brod, here are the results, viz:

```
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
```


Now what?

---

### Post by antoniomiguel on 2010-06-14
Paki-try sa terminal

sudo setpci -s 00:02.0 F4.B=30

Dapat nag-rereact ang screen brightness after. Yung 30 by the way is amount ng brightness, pwede mong laruin yung value up to FF

---

### Post by echo2knight on 2010-06-14
> **antoniomiguel said:**
> Paki-try sa terminal

sudo setpci -s 00:02.0 F4.B=30

Dapat nag-rereact ang screen brightness after. Yung 30 by the way is amount ng brightness, pwede mong laruin yung value up to FF

Thanks! It worked! +1 for antoniomiguel!


Brod, any way I can link this to the Fn+F7 (increase) / Fn+F8 (decrease) shortcut of my lappie?

So that I can change the screen brightness on the fly?

---

### Post by antoniomiguel on 2010-06-15
Paki-try ulit sa terminal..

*sudo gedit /etc/default/grub*

hanapin mo tong line na to.. **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"**

i-edit mo ng.. **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_backlight=vendor"**

save and exit gedit.

*sudo update-grub*

then reboot

---

### Post by echo2knight on 2010-06-15
> **antoniomiguel said:**
> Paki-try ulit sa terminal..

*sudo gedit /etc/default/grub*

hanapin mo tong line na to.. **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"**

i-edit mo ng.. **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_backlight=vendor"**

save and exit gedit.

*sudo update-grub*

then reboot

Thank you very much! Now the screen brightness shortcut of my lappie is working fine! +2 to you, antoniomiguel!

Now to find a solution to my other lucid lynx problems. :)

---

### Post by echo2knight on 2010-06-15
For the benefit of other forum members, I'll repost my problems with the proposed solutions, viz:

1. LCD brightness are set to the maximum. Keypad shortcuts adjusting the level of brightness are working, as shown by the brightness indicator. However, the brightness remain at the maximum;

**STATUS: SOLVED!!! SOLUTION BY antoniomiguel**

```

In the terminal..

1. Type *sudo gedit /etc/default/grub*
2. Find the line.. **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"**
3. Change it to.. **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_backlight=vendor"**
4. save and exit gedit.
5. Type *sudo update-grub*
6. then reboot.

```


2. Sounds are played using the built-in speakers and muted when an earphone is plugged in the earphone jack as expected, however, there are no sounds being played from the earphone. Only a short "pop" when you insert the said earphone;

**STATUS: PENDING!!!**


3. Keyboard shortcut enabling/disabling touchpad is not working (Fn+touchpad key).

**STATUS: PENDING!!!**

---

### Post by antoniomiguel on 2010-06-15
> **echo2knight said:**
> 
3. Keyboard shortcut enabling/disabling touchpad is not working (Fn+touchpad key).

**STATUS: PENDING!!!**

On a terminal, key-in "gconf-editor" (without the quotes)

On the Configuration Editor pop-up window, navigate to..

desktop > gnome > peripherals > touchpad

then tick "touchpad_enabled"

---

### Post by echo2knight on 2010-06-16
> **antoniomiguel said:**
> On a terminal, key-in "gconf-editor" (without the quotes)

On the Configuration Editor pop-up window, navigate to..

desktop > gnome > peripherals > touchpad

then tick "touchpad_enabled"

Brod, touchpad is already enabled even before editing. The touchpad uses AVC driver under windows.

---

### Post by antoniomiguel on 2010-06-16
> **echo2knight said:**
> Brod, touchpad is already enabled even before editing. The touchpad uses AVC driver under windows.

My bad, i didnt read well your problem and first thought you have a broken touchpad (i mean a not working pad)

---

### Post by echo2knight on 2010-06-16
> **antoniomiguel said:**
> My bad, i didnt read well your problem and first thought you have a broken touchpad (i mean a not working pad)

Anyway I can make a workaround on this?

---

### Post by echo2knight on 2010-07-02
Taas ko lang po guys!!!

---

### Post by aljoriz on 2010-07-02
from [ubuntu wiki]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks")

when done properly this will enable the Fn key to disable the touchpad when writing a very long document.

Hotkeys don't work out of the box, you have to add a kernel parameter to the grub config:

    * Run 'sudo gedit /etc/default/grub'
    *

      Edit the line with GRUB_CMDLINE_LINUX_DEFAULT and add " acpi_osi=Linux". The line should then look like -> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"
    * Save and then run 'sudo update-grub'
    * Reboot

---

### Post by echo2knight on 2010-07-03
> **aljoriz said:**
> from [ubuntu wiki]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks")

when done properly this will enable the Fn key to disable the touchpad when writing a very long document.

Hotkeys don't work out of the box, you have to add a kernel parameter to the grub config:

    * Run 'sudo gedit /etc/default/grub'
    *

      Edit the line with GRUB_CMDLINE_LINUX_DEFAULT and add " acpi_osi=Linux". The line should then look like -> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"
    * Save and then run 'sudo update-grub'
    * Reboot

Did and done. However, still not working. Anyway, thank you very much for the help.

---


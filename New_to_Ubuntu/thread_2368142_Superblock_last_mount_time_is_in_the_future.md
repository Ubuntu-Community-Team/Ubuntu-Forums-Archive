---
title: "Superblock last mount time is in the future"
date: 2017-08-07
forum: New to Ubuntu
---

### Post by shubanshii on 2017-08-07
Hi there,

I am new to Ubuntu.  I have my hard drive partitioned,  and my Ubuntu OS version was 14.04 for a long time (not new to having Ubuntu, but I'm new to using it).  A few days ago, I  updated to 17.04.  Now, when I boot up Ubuntu, a screen flashes the  message "Superblock last mount time is in the future. (by less than a  day, probably due to the hardware clock being incorrectly set).  The  date and time on my BIOS screen appears correct.  Also, the date and  time on the main screen of the OS appears correct.  Does anyone have any  idea what the issue is?  Could it be off by a matter of seconds or  something?  

Much thanks,
Shubanshii

---

### Post by QIII on 2017-08-07
Hello!

A couple of things come to mind.

1.  If not already installed, you might try installing NTP if you are able to reach either your desktop or drop to root from recovery mode.  NTP is a protocol that allows time synchronization over a network to a few atomic clocks via various NTP servers.

```
sudo apt install ntp
```

```
sudo systemctl reload ntp.service
```

2.  A bad/discharged CMOS battery (which you should be able to replace fairly cheaply) is not holding up.

Please let us know if either helps.

Cheers!

---

### Post by shubanshii on 2017-08-07
Hey, thanks for the help!

Ran the first command.

The second command yielded "Failed to reload ntp.service: Job type reload is not applicable for unit ntp.service."

---

### Post by QIII on 2017-08-07
OK.  Hang on.  Let me see if I got that right.  That was off the top of my head (I'm not at a Linux computer at the moment.)

You might also try rebooting.

Edit:  Hmmmm.  That is the correct command according to the official documentation.  Not sure what is going on there.

---

### Post by shubanshii on 2017-08-07
Below is what I see (the dot is actually green) after entering the second command followed by "systemctl status ntp.service"

```
Failed to reload ntp.service: Job type reload is not applicable for unit ntp.service.
See system logs and 'systemctl status ntp.service' for details.
shubanshii@Shubanshii:~$ systemctl status ntp.service
&#9679; ntp.service - LSB: Start NTP daemon
   Loaded: loaded (/etc/init.d/ntp; generated; vendor preset: enabled)
   Active: active (running) since Mon 2017-08-07 12:54:48 CDT; 2min 57s ago
     Docs: man:systemd-sysv-generator(8)
    Tasks: 2 (limit: 4915)
   CGroup: /system.slice/ntp.service
           &#9492;&#9472;1165 /usr/sbin/ntpd -p /var/run/ntpd.pid -g -u 127:137

Aug 07 12:57:05 Shubanshii ntpd[1165]: Soliciting pool server 91.189.89.199
Aug 07 12:57:05 Shubanshii ntpd[1165]: Soliciting pool server 52.37.145.131
Aug 07 12:57:05 Shubanshii ntpd[1165]: Soliciting pool server 204.11.201.10
Aug 07 12:57:06 Shubanshii ntpd[1165]: Soliciting pool server 91.189.89.198
Aug 07 12:57:06 Shubanshii ntpd[1165]: Soliciting pool server 138.236.128.36
Aug 07 12:57:06 Shubanshii ntpd[1165]: Soliciting pool server 216.229.0.49
Aug 07 12:57:06 Shubanshii ntpd[1165]: Soliciting pool server 97.107.128.58
Aug 07 12:57:07 Shubanshii ntpd[1165]: Soliciting pool server 159.203.158.197
Aug 07 12:57:07 Shubanshii ntpd[1165]: Soliciting pool server 129.6.15.30
Aug 07 12:57:07 Shubanshii ntpd[1165]: Soliciting pool server 91.189.91.157
```

Ok a quick update, I ran "[COLOR=#6A6A6A][FONT=Roboto]**timedatectl set**[/FONT][/COLOR][COLOR=#545454][FONT=Roboto]-local-rtc 0" and now[/FONT][/COLOR] I no longer see the message "[COLOR=#000000]Superblock last mount time is in the future. (by less than a day, probably due to the hardware clock being incorrectly set)."

However, the screen is still flashing a message that says "/dev/sda7": clean, 362227/10726912 files, 8489952/74898688 blocks" with some additional lines below it (see attached image).

Ultimately, I'd like to not have this screen flash at all and go back to the way it was before going straight to the OS.[/COLOR]

---

### Post by Bashing-om on 2017-08-07
shubanshii; Hello'

Appears that the boot messages are no longed masked by the plymouth boot image.
What is set to show at boot ?
post back - between code tags, please - the output of terminal command:
```

cat /etc/default/grub

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]a tale is told
[/INDENT][/INDENT]

---

### Post by shubanshii on 2017-08-07
Thank you for your help and the feedback regarding forum etiquette.  The command outputs:

[COLOR=#000000]```
[/COLOR]
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
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
[COLOR=#000000]
```[/COLOR]

---

### Post by Bashing-om on 2017-08-07
shubanshii; Hummm ...

Sorta at a loss here as :
> 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

you do have set to mask the boot messages and show the splash image instead.


Grasping at possibilities, a graphic's driver issue ?
```

sudo lshw -C video

```

[INDENT][INDENT]sometimes I wonder
[/INDENT][/INDENT]

---

### Post by shubanshii on 2017-08-07
That command output

```

  *-display                 
       description: VGA compatible controller
       product: Haswell-ULT Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64) memory:c0000-dffff

```

---

### Post by Bashing-om on 2017-08-07
shubanshii; Welp'

Still do not know the reason that boot messages are displayed . A graphic's driver is loaded .

Something funky on the boot command line ?
what shows:
```

cat /var/log/Xorg.0.log | grep "Kernel command line:"

```

[INDENT][INDENT]still, all a wonder
[/INDENT][/INDENT]

---

### Post by shubanshii on 2017-08-08
Bashing-om,

That command outputs:

```

[    28.796] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.10.0-30-generic.efi.signed root=UUID=33d0fadf-c1a4-4763-83a1-692dfa3833af ro quiet splash vt.handoff=7

```

---

### Post by shubanshii on 2017-08-08
An interesting development: I booted Windows and noticed that my time was incorrect.  It was set to the correct time zone but it was 3 or 4 hours behind.  I manually changed the time, but that was strange.  IDK if it relates to any of this, since I'm I'm not seeing the superblock message anymore (I am still seeing [COLOR=#000000]"/dev/sda7": clean, 362227/10726912 files, 8489952/74898688 blocks" with some additional lines below it", hence, why I am posting)[/COLOR].  Idk why my time was incorrect on Windows and not Ubuntu, especially when the BIOS screen displays the correct time.

---

### Post by Bashing-om on 2017-08-09
shubanshii' Well;

I am Windows illiterate - can not say or advise about how to reset the time in Windows.

As to the ubuntu messages,- as I still do not know why you see any -  maybe best at this time to have a look at the boot log .
easiest way is via a pastebin site to relay that log .
terminal command:
```

journalctl -b -0 | nc termbin.com 9999

```
the result is a URL back in terminal, pass that link back here . I do not know of any confidential info that log file could contain.

when all else fails
[INDENT][INDENT]read the instructions
[/INDENT][/INDENT]

---


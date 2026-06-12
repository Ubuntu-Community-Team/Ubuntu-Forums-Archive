---
title: "how to install intel drivers?"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by sxytrillian on 2008-06-14
how to install Intel drivers in Ubuntu 8.04?

is it compulsory to install drivers in Ubuntu?

i cannot able to hear sound in my headphones when i try to play movies and mp3 songs.

whether i need to install anything?

note : my Intel model is 845GCl

---

### Post by ukripper on 2008-06-14
> **sxytrillian said:**
> how to install Intel drivers in Ubuntu 8.04?

is it compulsory to install drivers in Ubuntu?

i cannot able to hear sound in my headphones when i try to play movies and mp3 songs.

whether i need to install anything?

note : my Intel model is 845GCl

can you check volume icon and see everything is maxed out.

if it is then post out of the following, type in terminal:
```
lspci
```

---

### Post by CREEPING DEATH on 2008-06-14
I'm not sure that's a driver issue or an 8.04 issue.

CD

---

### Post by rraj.be on 2008-06-14
There is no need for any mother board drivers.

You should install codecs for playing MP3 and other media formates.

just open synaptic and install all gstreamer codes.

you can use 

VLC player.

it supports maximum of media formates.

Look at here.

```
[CODE][https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")
```[/CODE]

---

### Post by sxytrillian on 2008-06-14
but iasked about the headphone in which i can't hear anything.

 i know vlc will play all the files..

---

### Post by rraj.be on 2008-06-14
ok.

i thought its your codec problem.

could you get sound in other speaker's.

You dont need any special driver to get sound through HEDAPHONE>

Is your MP3 files playing?

---

### Post by sxytrillian on 2008-06-14
i am having only head phones..

i dont have speakers..

---

### Post by halitech on 2008-06-14
when you start the computer and log into Ubuntu, do you hear the boot and login sounds?

---

### Post by sxytrillian on 2008-06-14
no i did't hear anything..during boot

---

### Post by halitech on 2008-06-14
As ukripper suggested, open a terminal and type
```
lspci
```
and post it here

you can also check System - Preferences - Hardware info

---

### Post by sxytrillian on 2008-06-14
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
04:00.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
04:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 01)

---

### Post by halitech on 2008-06-14
thats promising, Ubuntu at least sees your card installed. do you have a speaker icon by your clock? If so, does it have a red circle by it? sound card might just be muted.

---


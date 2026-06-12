---
title: "RE: 32-bit Ubuntu Hotmail Issue (help?)"
date: 2016-08-08
forum: New to Ubuntu
---

### Post by monsterjazzlicks on 2016-08-08
Hi folks,

I installed UBUNTU (overwriting my 32-bit Win_XP OS on PC) last month.  I have just joined this forum today.

I have not been able to REPLY or COMPOSE HOTMAIL MESSAGES because the CURSOR will not appear or function when trying to click in the main email body/field.  However, I am able to type into the ADDRESS and SUBJECT fields 100% fine.  And also I can compose GMail (emails), You Tube (comments) and obviously type here on the Ubuntu forum perfectly fine!

My Mozilla is the latest version.

I have also tried using BING and GOOGLE.

Many thanks in advance for any kind assistance offered . . .

Best,

Paul David Seaman (UK)

---

### Post by mörgæs on 2016-08-08
Hi, welcome to the fora.

First let's see the hardware. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by monsterjazzlicks on 2016-08-08
```
paul@monsterjazzlicks:~$ sudo lshw - sanitize . lshw.txt
[sudo] password for paul: 
Hardware Lister (lshw) - B.02.16
usage: lshw [-format] [-options ...]
       lshw -version

    -version        print program version (B.02.16)

format can be
    -html           output hardware tree as HTML
    -xml            output hardware tree as XML
    -short          output hardware paths
    -businfo        output bus information

options can be
    -class CLASS    only show a certain class of hardware
    -C CLASS        same as '-class CLASS'
    -c CLASS        same as '-class CLASS'
    -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
    -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
    -quiet          do not display status
    -sanitize       sanitise output (remove sensitive information like serial numbers, etc.)
    -numeric        output numeric IDs (for PCI, USB, etc.)
```

Thanks Morgas,

This seemed to be the only way I could COPY the SCRIPT here?

I took a SCREENSHOT also but the dimensions are too large and I don't seem to have a APP for resizing.

Docs uploaded to DRIVE:

[https://drive.google.com/folderview?id=0ByepppzJGXGedk9iZXUwdzRCR0k&usp=sharing](https://drive.google.com/folderview?id=0ByepppzJGXGedk9iZXUwdzRCR0k&usp=sharing)

Cheers,

Paul

```
paul@monsterjazzlicks:~$ sudo lshw - sanitize . lshw.txt
[sudo] password for paul: 
Hardware Lister (lshw) - B.02.16
usage: lshw [-format] [-options ...]
       lshw -version

    -version        print program version (B.02.16)

format can be
    -html           output hardware tree as HTML
    -xml            output hardware tree as XML
    -short          output hardware paths
    -businfo        output bus information

options can be
    -class CLASS    only show a certain class of hardware
    -C CLASS        same as '-class CLASS'
    -c CLASS        same as '-class CLASS'
    -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
    -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
    -quiet          do not display status
    -sanitize       sanitise output (remove sensitive information like serial numbers, etc.)
    -numeric        output numeric IDs (for PCI, USB, etc.)
```

Hi again,

Also when I click on REPLY to a Hotmail, the ORIGINAL email (ie. I am replying to) which usually shows BELOW is not appearing?!

Ta,

Paul

---

### Post by mörgæs on 2016-08-09
It's better to copy and paste commands like the one I suggested into the command prompt. Don't write them by hand.

---

### Post by monsterjazzlicks on 2016-08-09
Hi,

It won't let me copy&paste the data in.  The only way seems to be to write it letter-by-letter.  Maybe this is related to the Hotmail issue I am having?

thanks,

Paul

---

### Post by oldos2er on 2016-08-09
Can you please post your hardware specs, and Ubuntu version?

---

### Post by mörgæs on 2016-08-10
When writing commands by hand there is a risk of spelling mistakes, therefore copying is preferred. 

You have to have a [COLOR=#ff0000]>[/COLOR] sign in the command.

---

### Post by monsterjazzlicks on 2016-08-12
Hi guys,

Ok, thanks a lot for the help.

Ubuntu just performed a massive automatic UPDATE and after restarting my PC the issue seems to have correct itself!!??

Cheers,

Paul

btw - this can be marked as SOLVED now!

---

### Post by mörgæs on 2016-08-12
Good, please do.
See Thread Tools.

---

### Post by monsterjazzlicks on 2016-08-13
Ok, cheers.

---


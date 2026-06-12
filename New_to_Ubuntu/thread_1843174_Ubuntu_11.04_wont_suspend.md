---
title: "Ubuntu 11.04 wont suspend"
date: 2011-09-13
forum: New to Ubuntu
---

### Post by You22211 on 2011-09-13
Hello everyone,

I'm fairly new to Ubuntu and just updated to 11.04 64bit.  Whenever I close the lid to my laptop, or tell it to suspend I get a black screen with the following message:

[   76.067893] i2400m_usb 1-1.1:1.0: failed to suspend, will reset on resume
[   78.849095] i2400m_usb 1-1.1:1.0: device rebooted: reinitalizing driver


Thanks for any help!

---

### Post by MG&amp;TL on 2011-09-13
Did you use Wubi, or dual-boot? As far as I know, wubi can't suspend...

---

### Post by bcbc on 2011-09-13
> **MG&TL said:**
> Did you use Wubi, or dual-boot? As far as I know, wubi can't suspend...

Nope... that's not true. Wubi suspends (sleeps) fine. Just hibernation isn't supported. 

So there is some issue with that usb device? Check for PM: messages in /var/log/syslog - might give more info.

---

### Post by MG&amp;TL on 2011-09-13
Wubi CAN suspend....ok....mine doesn't...I do have a weird BIOS though.

Cool. Thanks, sorry for misinformation.  :(

---

### Post by bcbc on 2011-09-13
> **MG&TL said:**
> Wubi CAN suspend....ok....mine doesn't...I do have a weird BIOS though.

Cool. Thanks, sorry for misinformation.  :(

That's okay - if yours doesn't - how would you know? ;) Maybe there is something you can do to fix it. Check for the PM: messages and see - someone might have found a workaround. e.g. on my one computer with an old wireless card that needed ndiswrapper I had to create a script to rmmod it on sleep and then modprobe it on resume. (Actually in that case, it still suspended but the networking wouldn't work afterwards). But the point it, someone might have documented a fix for whatever piece of hardware that is giving you grief.

---

### Post by MG&amp;TL on 2011-09-13
Nah, it's all good, that should have been in past tense, I've installed now. :D

---

### Post by bcbc on 2011-09-14
> **MG&TL said:**
> Nah, it's all good, that should have been in past tense, I've installed now. :D

Did you get the suspend to work then? You would have to do something to fix it...

Personally I find it hard to live without suspend (and hibernate). Fortunately Ubuntu boots up and shuts down really quickly so it's not as big a deal as with Windows, but... it's definitely more productive to hibernate.

---

### Post by fdrake on 2011-09-14
usually on suspend some drivers need to be unloaded and loaded back at resume. it looks like that the error msg is about an usb driver correct me if i am wrong. can the OP run this commands please , after he had encountered a suspend resume issue:
```

less /etc/var/sysylog | grep -i i2400m_usb
lsmod

```

also you can try to do this:

```

sudo cp /etc/default/acpi-suppor ~/acpi-suppor.bk
sudo gedit /etc/default/acpi-support

```
and look for

> # Note that network cards and USB controllers will automatically be unloaded
# unless they're listed in MODULES_WHITELIST
MODULES=""
and add in the module field "i2400m_usb". reboot and try to put your laptop in suspend and resume to test.

---

### Post by OpenSage on 2011-09-21
> **You22211 said:**
> Hello everyone,

I'm fairly new to Ubuntu and just updated to 11.04 64bit.  Whenever I close the lid to my laptop, or tell it to suspend I get a black screen with the following message:

[   76.067893] i2400m_usb 1-1.1:1.0: failed to suspend, will reset on resume
[   78.849095] i2400m_usb 1-1.1:1.0: device rebooted: reinitalizing driver


Thanks for any help!





I know this is a really late reply, but I think I have this issue figured out. I have had the same problem running both Ubuntu 10.10 64 bit and Ultimate Edition 9/on Ubuntu 10.10 64 bit. I came across this fix by accident. Before suspending the machine, go to a different console by pressing (CTRL+ALT+F2) all at the same time. You should be in a new console. Log into that console then press (CTRL+ALT+F7) to take you back to your Graphical User Interface and then Suspend you machine. This works for me every time (although I never hibernate, so don't know if it will fix that). Hope this helps some people.\\:D/

---


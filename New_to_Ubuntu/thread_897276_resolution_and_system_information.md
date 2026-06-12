---
title: "resolution and system information"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by groknet on 2008-08-22
Hello
I have a new install of latest ubuntu version and
would like to know

1)
The install seems to be OK apart from the display
resolution which is very low - 640 * 480 - i cant
set it to higher...

The computer has a good NVDIA graphics card - what can  i
do to get better resolution?

2)
In Windows you can use device manager to display
what graphics card, sound card are installed etc.
Is there any kind of function  like that in ubuntu?

Greetings grok

---

### Post by rodh on 2008-08-22
I won't be of much help here technically but I have seen a lot of post regarding Nvidia drivers,  My SiS Monitor resolution was easy enough,  found and installed the right monitor,  Not Generic.
Your best bet is to do a serch inside the forum on your Nvidia Car.  Best of luck, and Sorry I couldn't be of much help technically

---

### Post by RequinB4 on 2008-08-22
lspci and lsusb will list your pci and usb devices that are connected, respectively.

You most likely need a new nvidia driver.  Which one do you have?

---

### Post by hyper_ch on 2008-08-22
```

sudo lshw -html > ~/Desktop/hardware.html

```

---


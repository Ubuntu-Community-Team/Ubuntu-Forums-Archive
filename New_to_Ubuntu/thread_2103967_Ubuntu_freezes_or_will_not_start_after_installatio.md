---
title: "Ubuntu freezes or will not start after installation"
date: 2013-01-11
forum: New to Ubuntu
---

### Post by Viperx45 on 2013-01-11
Hello,

I can't get Ubuntu 12.10 to run after installation without freezing up.
After selecting 'Ubuntu' from the GNU GRUB 2.0 boot menu, i get the following problems:

   [INDENT]-Freeze right after selection at black or purple screen,     sometimes with a flashing underscore.[/INDENT]
   [INDENT]-After getting to the desktop, the mouse and/or system will freeze. Sometimes one before the other. Usually only takes less than a minute to freeze up.[/INDENT]
   [INDENT]-some various other errors that take me to a program that allows commands to be entered.[/INDENT]


In order to install ubuntu 12.10, I had to use the following boot options with the live CD:   
   [INDENT]-irqpoll noapic nolapic acpi=off[/INDENT]

With those settings it ran fine, and got through the installation with no problems. I can't seem to do that with GRUB, or I don't know how to set it up. I couldn't find any info on how to do so, either.

Now it has the same problems that the liveCD had when I didn't use the boot options listed above.


The laptop I'm trying to run ubuntu on is a Gateway ML3109
I've found that this is a very common problem with the laptop, and seems to be due to the integrated ATI Radeon GFX chip. 

I've upgraded the ram to 1.5GBs. Windows XP is also installed on this laptop and currently works very well with the dual boot.

This is the image that I am using to install ubuntu with a DVD.
ubuntu-12.10-desktop-i386.iso

TLDR:

Is there a way to use the following boot options after install at GRUB like used on the liveCD?

 [INDENT]-irqpoll noapic nolapic acpi=off[/INDENT]

---

### Post by audiomick on 2013-01-11
Yes, I am sure there is a way, but I am not sure how to do it beyond having to edit grub. You could start looking for a way here. Follow the links there too.

[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

Sorry I can't be more help than that. Maybe someone else who knows more about it will post here soon.

---

### Post by tlhIngan on 2013-01-11
Try changing from APIC to something else in your BIOS settings.

---

### Post by Viperx45 on 2013-01-11
> **audiomick said:**
> Yes, I am sure there is a way, but I am not sure how to do it beyond having to edit grub. You could start looking for a way here. Follow the links there too.

[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

Sorry I can't be more help than that. Maybe someone else who knows more about it will post here soon.

I've been looking around for awhile now. I'll take a look through that link there. Hopefully I can find something there.

---

### Post by Viperx45 on 2013-01-11
> **tlhIngan said:**
> Try changing from APIC to something else in your BIOS settings.

The bios is very limited. I'm not finding any settings related to APIC.

---

### Post by Viperx45 on 2013-01-13
After some more searching on the web I found out how to enable those boot options in GRUB. I found that you have to type to commands at the end of the kernal line.

Here is a photo showing where.
[http://img835.imageshack.us/img835/415/img0070s.png](http://img835.imageshack.us/img835/415/img0070s.png)

Now I just need to figure out how to make this permanent.

My computer doesn't run Ubuntu very well with these setting I guess. It's not fast and snappy like I'd like it to be, I'm guessing these setting might have something to do with that.

---

### Post by Trazzt on 2013-01-18
Thanks mate I think my ubuntu has stopped freezing because of your commands.
To edit the grub menu easily, you need to install grub2 customizer.
[Nooblab article]("http://www.noobslab.com/2012/01/grub2-customizereditor-for-gnome-and.html")
Install it with by opening the terminal, and execute:
```
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customize
```Then you can run it with
```
grub-customizer
```Highlight the configuration file you want to edit:
[IMG]http://i34.photobucket.com/albums/d114/Cid_en_co/Overig/grubeditor1_zps1db8a99f.png[/IMG]

and make your alterations:
[IMG]http://i34.photobucket.com/albums/d114/Cid_en_co/Overig/grubeditor2_zpsdf907951.png[/IMG]

When your done, press File > save at the main screen of the program.

You should have a alterated grub bootloader now.

---


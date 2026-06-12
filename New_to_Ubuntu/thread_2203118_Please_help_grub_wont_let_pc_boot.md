---
title: "Please help grub wont let pc boot"
date: 2014-02-01
forum: New to Ubuntu
---

### Post by zack5 on 2014-02-01
Hello, recently i switched from windows 8 to ubuntu 13.10, im fairly new to ubuntu. I wasn't seeing the grub menu when i started up, so i decided to run boot repair. when i ran it and restarted now  i see this and cant boot past it. 
[IMG]http://members.iinet.net.au/~herman546/p15/fig2grub.gif[/IMG]

 I'm on a uefi system, i dont know if that matters. im really panicking. i had just bought a brand new hp touch smart sleek book. if you need any more information please let me know. im desperate.

---

### Post by sandyd on 2014-02-01
moved to absolute beginners talk

---

### Post by zack5 on 2014-02-01
Sorry, i didnt know where i should post it :/

---

### Post by jp734 on 2014-02-01
What happens when you press escape?

---

### Post by danny.techify on 2014-02-02
I have the same issue right now this is how I boot into Windows 8. If you need to boot into Windows 8 then right when your computer starts go into your boot menu. Depending on your computer there will be a different key you need to press you can try searching it up. When you get to the boot menu use the arrow keys to scroll down to "Windows Boot Manager" or "Windows 8 an"d hit enter and you will boot into Windows 8. You will need to do that every time you turn on your computer. I am trying to find a way to make it go straight to Windows 8.

---

### Post by danny.techify on 2014-02-02
The boot menu key is F9

---

### Post by PotatoHead007 on 2014-02-02
> **jp734 said:**
> What happens when you press escape?

Second that. Also, did you let boot repair do its own thing, without specifying your own variables? I hear that can be dangerous.

---

### Post by oldfred on 2014-02-02
Best to see how you installed and what Boot-Repair has done.

Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

If anytime you run Boot-Repair and it asks this question say[COLOR=#ff0000] no[/COLOR]. It is only required with some systems that do have 'buggy' UEFI that only boot Windows. But Boot-Repair cannot check for that. Only after confirming that no ubuntu entry in UEFI works may we need that setting and some understanding of what it really does.


>  buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? [COLOR=#ff0000]yes[/COLOR] (if any choice fails, please retry with the other)

Change the default yes to [COLOR=#ff0000]no[/COLOR].
IF you have run it, you can easily undo it until we know you need it.
      
>  To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.



---


---
title: "Grub Rescue Help - Cannot Boot From CD/USB"
date: 2013-06-28
forum: New to Ubuntu
---

### Post by Legonatic on 2013-06-28
I made to stupid mistake of deleting the partition Ubuntu was in from Windows. Now I am stuck at the grub rescue. I looked around and saw I need to use a restore disk to repair the MBR so that I can then boot into Windows. However, I have tried multiple times and I cannot get my computer to boot from either the CD drive or a USB drive. I have moved them up above the HDD on the boot order list, but no luck. I don't know why this is happening as I have been able to boot from them in the past. Anyway, I need help with how I can fix the MBR from the grub rescue screen WITHOUT a CD/USB to repair. I think I need the GRUB2 commands, if they exist, in order to do so.

---

### Post by Legonatic on 2013-06-28
A bit of an update:

I have now made a DVD and USB copy of Ubuntu 12.10. (I burned the .iso to a DVD and USB drive) I will again attempt to boot from both. (I had 12.10 installed on my computer)

[COLOR=#333333][FONT=Segoe UI]I tried to boot from both and here is what happened:[/FONT][/COLOR][COLOR=#333333][FONT=Segoe UI]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Segoe UI]With the USB drive: [/FONT][/COLOR]
[COLOR=#333333][FONT=Segoe UI]It IS listed under the boot order menu in my BIOS. I moved it up near the top of the list. When I pushed F10 (To save and exit) and then pushed F12 (To enter the multiboot menu) It was not listed. Not sure what's up as I have been able to boot from a USB device before.[/FONT][/COLOR]
[COLOR=#333333][FONT=Segoe UI]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Segoe UI]With the DVD:[/FONT][/COLOR]
[COLOR=#333333][FONT=Segoe UI]I have the CD drive before the HDD, but below the Flash Drive in the boot order. When I pushed F12 and selected the CD drive, it took a while at a black screen and then it just went into the grub rescue again.[/FONT][/COLOR]
[COLOR=#333333][FONT=Segoe UI]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Segoe UI]I have no idea why it won't boot into either. Am I doing something wrong? Have I accidentally not allowed booting from either? I really need to find a way around the grub rescue, and it seems that I can't restore the MBR using a restore disk.[/FONT][/COLOR]

---

### Post by oldfred on 2013-06-28
Are you burning it correctly, not just copying ISO to flash or DVD? BIOS has ot see a bootable device when loading for it to boot it, otherwise is just defaults to the next device in the boot order.
What did you use to create flash drive? unetbootin, pendrive or other Linux install's Startup disk creator?

       Also instructions for DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---


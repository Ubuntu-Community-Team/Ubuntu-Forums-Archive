---
title: "Can ping printer IP, how do I add it?"
date: 2012-05-04
forum: New to Ubuntu
---

### Post by Boyntonstu on 2012-05-04
I need the next step to print on a Brother MFC 440-CN printer on the LAN.

This printer has both LAN and USB outputs.

I used it when connected to the USB and it worked fine.

What do I need to do to connect to it on the LAN?

---

### Post by jonedney on 2012-05-04
Hello!

You should be able to add the printer by it's Host name.

Thanks!
Jon

---

### Post by jerome1232 on 2012-05-04
Have you tried clicking the Cog in the top right, printers, add printer, select network printer in the left pane, and waiting to see if auto detection finds it?

---

### Post by Boyntonstu on 2012-05-04
> **jerome1232 said:**
> Have you tried clicking the Cog in the top right, printers, add printer, select network printer in the left pane, and waiting to see if auto detection finds it?

No Gog button in Gnome (fallback).

Terminal command?  This may be it:  (system-config-printer)

What is the Host Name and/or how can I find it?

---

### Post by jonedney on 2012-05-04
The hostname should be specified on the printer's networking set up.

---

### Post by ajgreeny on 2012-05-04
You may need a static IP for it to be sure that you can always connect to it.

---

### Post by jerome1232 on 2012-05-04
> **Boyntonstu said:**
> No Gog button in Gnome (fallback).

Terminal command?  This may be it:  (system-config-printer)

What is the Host Name and/or how can I find it?

Gnome-failback should have an equivalent listed under System Settings, just look around your menu's. Once your in the add printer wizard you can click find network printer and it *should* just find the printer.

If it does not, you may need to find the printers ip and/or hostname via the control panel on your printer. Then manually add it via that name. 

Edit: When your not using the default interface, it's best to provide that info ahead of time so we know to adjust gui instructions or  so we know to simply provide cli instruction if we don't know that particular interface well.

---

### Post by Boyntonstu on 2012-05-05
> **jerome1232 said:**
> Gnome-failback should have an equivalent listed under System Settings, just look around your menu's. Once your in the add printer wizard you can click find network printer and it *should* just find the printer.

If it does not, you may need to find the printers ip and/or hostname via the control panel on your printer. Then manually add it via that name. 

Edit: When your not using the default interface, it's best to provide that info ahead of time so we know to adjust gui instructions or  so we know to simply provide cli instruction if we don't know that particular interface well.


Using the USB port I printed a Test Page with the following:


Printer Name:  Brother-MFC-440CN
Location: boyntonstu-s5704y
Make and Model:  Brother MFC-440CN  CUPS v1.1
Driver name:  Br440_2.PPD

I set the printer IP address to 127.0.1.127 and I can instantly ping it.

I have yet to find the printer HOST name.

Does this help?

---

### Post by forrestcupp on 2012-05-05
Even in Gnome Classic, on the panel in the very upper right corner, there is an icon that looks like a small cog or gear. Click on that icon, it's the one in the very upper right of the screen. When you click it, it will bring up a menu. Click 'Printers' in that menu, and it will bring up a window listing your installed printers. In that window, click 'Add' and it will bring up a wizard to add or install a printer. Click where it says Network printer, and do whatever it asks to try to automatically detect your LAN printer.

You won't need to know or care about the printer's host name unless that doesn't work.

---

### Post by PPN13 on 2012-05-05
I don't think its your printer at 127.0.1.127. As far as I know all IP adresses between 127.0.0.0 and 127.255.255.255 are a loopback, meaning they point to your own computer.

---

### Post by kurt18947 on 2012-05-05
> **Boyntonstu said:**
> I need the next step to print on a Brother MFC 440-CN printer on the LAN.

This printer has both LAN and USB outputs.

I used it when connected to the USB and it worked fine.

What do I need to do to connect to it on the LAN?

Here is a thread that you might find useful:

[http://ubuntuforums.org/showthread.php?t=1960473&highlight=brother](http://ubuntuforums.org/showthread.php?t=1960473&highlight=brother)

---

### Post by GHerzog on 2012-05-05
Pick another IP address - like 192.168.1.xxx or something.
And read Wikipedia on IP addresses as some are limited in range and some of the 127.xxx.xxx.xxx may be dedicated to loopback. (But I think you are okay with what you have Pinged.)

Alternatively, you may need to open a TCP Port as well. Look at your printer documentation.

GO TO 'Printers' and select 'Network Printers' and you will have several choices. You may need to determine which your printer wants. Read the manual.

Only ONE choice uses IP address and adds PORT 9100. It is the last one.

---

### Post by Boyntonstu on 2012-05-05
> **GHerzog said:**
> Pick another IP address - like 192.168.1.xxx or something.
And read Wikipedia on IP addresses as some are limited in range and some of the 127.xxx.xxx.xxx may be dedicated to loopback. (But I think you are okay with what you have Pinged.)

Alternatively, you may need to open a TCP Port as well. Look at your printer documentation.

GO TO 'Printers' and select 'Network Printers' and you will have several choices. You may need to determine which your printer wants. Read the manual.

Only ONE choice uses IP address and adds PORT 9100. It is the last one.


UPDATE:

I thought that since my PC is dual boot, 11.10 USB and Win 7 HD I should try installing the LAN printer on Win7.

In Win7 Control Panel, Printers, Install, LAN

It found my printer at 192.168.1.127 in about 10 seconds.

It printed a Test Page.

Done!

Back here on Ubuntu.

I will keep you informed.

Rebooted, in Terminal  system-config-printer, Ubuntu found Brother 440-CN is 5 seconds, and it installed it fine.  ?????

Moral of story, re-BOOT and try again!!


I hope that this helps someone.

---

### Post by jerome1232 on 2012-05-05
I'm still lost as to why you haven't done the same thing in Ubuntu. I haven't heard any feedback from you about using the add printer utility.

See screenshot.

---

### Post by Boyntonstu on 2012-05-05
> **jerome1232 said:**
> I'm still lost as to why you haven't done the same thing in Ubuntu. I haven't heard any feedback from you about using the add printer utility.

See screenshot.

!!!!!!!Rebooted, in Terminal system-config-printer, Ubuntu found Brother 440-CN is 5 seconds, and it installed it fine. ?????

Moral of story, re-BOOT and try again!!!!!!

Ubuntu worked fine.

Brother LAN printer now working on XP, Win7, and 11.10.

I connected the Brother 440-CN Network cable into my Linksys router for the LAN.

---

### Post by forrestcupp on 2012-05-06
> **Boyntonstu said:**
> !!!!!!!Rebooted, in Terminal system-config-printer, Ubuntu found Brother 440-CN is 5 seconds, and it installed it fine. ?????

Moral of story, re-BOOT and try again!!!!!!

Ubuntu worked fine.

Brother LAN printer now working on XP, Win7, and 11.10.

I connected the Brother 440-CN Network cable into my Linksys router for the LAN.

So you basically just finally did what jerome1232 and I have been trying to tell you all along, but you opened the printer settings from the terminal instead of the Settings menu.

I'm glad it worked for you.

---

### Post by Zill on 2012-05-07
> **Boyntonstu said:**
> ...Moral of story, re-BOOT and try again!!!!!!...
This is the Windows approach.

Totally unnecessary with Linux!

---

### Post by Boyntonstu on 2012-05-07
> **Zill said:**
> This is the Windows approach.

Totally unnecessary with Linux!

Hi!

I am sorry if I did not make it clear.

I had to reboot Linux to make it work.


stU

---


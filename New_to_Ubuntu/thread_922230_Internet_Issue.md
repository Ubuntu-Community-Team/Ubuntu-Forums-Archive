---
title: "Internet Issue"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by economy on 2008-09-17
I've noticed this forum doesn't see a lot of good news. This is my first post using Ubuntu, and it's great. I'm pitching Vista in the trash as soon as I can transfer my files.

One issue I'm having though, and I'm not sure if this is easy or not. I'm in China where they only have DSL service, and the crap modem they've provided took me weeks to get working on Vista. There is a driver disk, with executable files, and from my understanding (at least using windows) this modem will not connect to the computer without those programs present. I'm not sure if there's an easier way to tinker with it, but it'd be great to have access at home instead of this Starbucks.

Any help, I'd appreciate it. The open source community shows any Windows user what they've missed out on.

---

### Post by iaculallad on 2008-09-17
If you're going to get connected using aDSL, you shouldn't need those drivers for your router/model to work. Just plug in a straight-through cable on your ethernet port going to the router/modem's ethernet port and try enabling DHCP on your Network Configuration (System->Administrator->Network).

---

### Post by NoReflex on 2008-09-17
Hello!

Could you post the modem model and your system specs?
You can check if you modem is detected with **lspci** and **lsusb**. Also please post the output of **tail /var/log/messages** after about thirty seconds after you've connected your modem.

Best wishes,
NoReflex

---

### Post by economy on 2008-09-17
The modem itself is Conexant AccessRunner ADSL WAN PPPoE 5800UB, if that helps at all.

It's connected through my USB port, but the proprietary software included in the driver CD doesn't run even through WinE. My laptop is using a Realtek RTL8101 Family PCI-E Ethernet Network Card. I'm not sure if it's an issue with the network card or the modem itself, since I've used Ubuntu for a whole 2 days now... but my feeling is (and the help file says something along these lines), the proprietary software used to run the modem is necessary, and I can't get Ubuntu to use it. 

Through Windows, it took me 2 weeks just to get the modem running (mostly the Chinese language menus in the software) and at this point the modem doesn't even try to establish a link with the computer (that is the 'link' light flashing) unless that software is present... 

I have to shut down and switch back to linux to try **lsusb** and **tail /var/log/messages**, so i'll post that information as soon as I can get that done.

---

### Post by economy on 2008-09-17
Noreflex,

after running **lsusb** it shows that Ubuntu recognizes a modem from Conexant on usb port 2. Thats good news I guess.

then I ran **tail /var/log/messages** and came up with this information:

Sep 18 10:33:10 ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[drm] Initialized i915 1.6.0 20060119 on minor 0
usb 5-1: new full speed USB device using uhci_hcd and address 2
usb 5-1: configuration #1 chosen from 1 choice
usbcore: registered new interface driver cxacru
cxacru 5-1:1.0: firmware (cxacru-fw.bin) unavailable (system misconfigured?)

I think I'm following it a little, but most of it is still greek to me. That should tell you what's happening though

---

### Post by economy on 2008-09-18
yowch. i mention ADSL USB and everyone shrinks away. now i have to take a step back further. i was directed to [http://ubuntuforums.org/showthread.php?t=354700&page=2](http://ubuntuforums.org/showthread.php?t=354700&page=2) by the documentation page on USB ADSL modems, but my head's throbbing here.

i found two sites that have the infamous cxacru-fw utility but i haven't the least idea how to download them. gdebi? how do you use that when it's from a website? 

otherwise, the documentation site explains how to extract. i don't know how that will work out, since it seems the user above had some extreme difficulties. 

is there anyone who can step down and put this stuff into layman's terms for me? i just need the firmware (as i understand), and the rest i can try to get through myself. my biggest hurdle right now is adding cxacru-fw, mainly because i have no idea how to download anything.

i'm like the above user... if i can't get this to work, i have to return to vista, and i really don't wanna do that...

---

### Post by NoReflex on 2008-09-18
I apologize for the delay but I'm really busy at work these days ... and school is about to begin also.
I think you will find a good starting point here : 
[https://help.ubuntu.com/community/UsbAdslModem/AccessRunner](https://help.ubuntu.com/community/UsbAdslModem/AccessRunner)
Please try the suggestions there...and if something doesn't work as expected post here and I'm sure we will find a solution.
Good luck!

Best wishes,
NoReflex

---


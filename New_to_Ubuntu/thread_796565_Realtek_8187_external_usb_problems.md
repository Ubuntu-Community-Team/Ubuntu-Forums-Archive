---
title: "Realtek 8187 external usb problems"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by Desterie on 2008-05-16
OK, someone help a newbie out.  I notice there are alot of threads posted on realtek 8187 wireless adapter.  Apparently its a pain.  My situation prevents me from using the internal wireless cards on my computers, so I have a USB wireless card with an external antenna jack.  Antenna is connected outside to receive the wireless signal. 

Problem 1:
When this USB adapter is plugged into my Dell Inspiron 1521, it works fine for about 5 minutes at a time, then it loses signal.  But it worked soon as I plugged it in, with the exception of the led indicator.  I am using the 64 bit Hardy on this computer.

Problem 2:
When I plug this USB adapter into my Toshiba Satellite M35X-S349 centrino processor, it doesn't work at all.  

So how do I get it working properly, or is there another recommended USB adapter with an external RP-SMA antenna jack I can use?

---

### Post by HotShotDJ on 2008-05-16
Perhaps this might help? [http://www.instructables.com/id/Yet-another-laptop-wifi-antenna-mod](http://www.instructables.com/id/Yet-another-laptop-wifi-antenna-mod)

(Of course, I'm assuming that you are only trying to access a wireless network that you are AUTHORIZED to access.)

---

### Post by Desterie on 2008-05-18
LOL yeah, I am authorized.  Thanks for the link.  Some interesting modifications there.  Actually I am on a military base and my living and work areas are surrounded by 15ft high 8in thick concrete walls.  

I figured out the problem with the Toshiba.  When I ran my configuration with Windows, it didn't like my internal wireless card being on when the USB card was plugged in.  They interfered with each other.  So I kept the internal wireless card switch turned off.   In Ubuntu, if you turn the wireless switch off, it assumes ALL wireless devices should be off.  When I turned the internal wireless switch on, it functioned about like the Dell I have.  On for about 5min and off for 1 (and connecting at 1mbps to boot :( )

---

### Post by smile-its-smiley on 2008-05-18
i have this card in my laptop simply follow the instructions in this thread and it should work fine [http://ubuntuforums.org/showthread.php?t=777676](http://ubuntuforums.org/showthread.php?t=777676)

---


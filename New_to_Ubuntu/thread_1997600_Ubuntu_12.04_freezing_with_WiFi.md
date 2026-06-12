---
title: "Ubuntu 12.04 freezing with WiFi"
date: 2012-06-05
forum: New to Ubuntu
---

### Post by Andrewmham on 2012-06-05
-I am running 12.04 on an Acer Aspire 5250-0639, and it seems that I cannot boot the machine into Ubuntu period unless I have an ethernet connection.

I have gotten to the point where I can be quick about it and try disabling the wireless connection, but it still freezes (no ctrl-alt-f1 either) and I have to hard reboot. 

System is a dual boot with Windows 7, though I suspect it's a driver issue...the laptop has the following wireless adapter; any ideas what might be the issue? Done a bit of googling, and all I came up with was to swap out the wireless card if possible.

Atheros Communications Inc. AR9485 Wireless Network Adapter (rev 01)

---

### Post by wildmanne39 on 2012-06-05
Hi, set network boot as a first option in BIOS, this should fix the issue.
Thanks

---

### Post by cortman on 2012-06-05
> **wildmanne39 said:**
> Hi, set network boot as a first option in BIOS, this should fix the issue.
Thanks

This worked for my Acer Aspire One 722 netbook.

---

### Post by Andrewmham on 2012-06-05
Fantastic! Boot time suffers a bit, but it worked like a charm...thanks so much!

---

### Post by wildmanne39 on 2012-06-05
Hi, your welcome! please use thread tools at the top of the page to mark the thread solved.
Thanks

---

### Post by CPL2010 on 2012-06-27
> **Andrewmham said:**
> Fantastic! Boot time suffers a bit, but it worked like a charm...thanks so much!

Let me guess it's still dropping wireless.

Here's the trick for the wireless in that laptop.  Get rid of the Miniwan card and get anything else but Atheros.  They are, have been, always been garbage.  Save yourself the annoyance and get yourself setup with another minicard and save your sanity.

---

### Post by wildmanne39 on 2012-06-27
Hi, > Let me guess it's still dropping wireless.
there may be a fix for that as well.
Thanks

---

### Post by 81chevette on 2012-08-22
I'm having the same trouble with my install. My sticker declares the laptop to be an Acer Aspire 5250-BZ853. As instructed on other pages, I've tried blacklisting my AR8152 ethernet--which didn't seem to actually blacklist it--as well as forbidding hardware encryption on the AR 9285 wireless card. Neither of these "fixes" seemed to accomplish anything. I still booted just fine while plugged into ethernet and could connect to my wireless network just fine, but if I unplugged the cable, I got complete freeze within seconds. Booting froze as soon as wireless tried to connect, around the login screen time or so.

I tried this fix today, and so far have successfully booted three times. I have three questions:

a) In terms a linux virgin might understand, why does this work? 
b) Will this reduce my wireless functionality?
c) Would I be better off to just go get a wireless dongle and let my Atheros card sit and fail in the corner? (I'm unwilling to replace the actual card right now, as I don't have the free time.)

Thanks in advance for any help.

---

### Post by wildmanne39 on 2012-08-22
Hi, no it does not hurt wireless functionality.

You should be fine.
Thanks

---


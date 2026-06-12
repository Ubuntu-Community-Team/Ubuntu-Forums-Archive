---
title: "Smart Bro (USB) stopped working"
date: 2009-07-19
forum: Philippine Team
---

### Post by creek23 on 2009-07-19
I installed Ubuntu NBR to my niece's MSi last May 2009 -- it worked perfectly with Smart Bro (the USB thingy) until last week (as my niece remembers).

Tried reconfiguring the USB for 3 hours and updating the kernel yet  nothing happened. Tried connecting the netbook to my WiFi router just to check -- it does connect.

So I'm guessing that this has something to do with tel co' system upgrading.

Do you know other Ubuntu users with Smart Bro having the same problem lately?

---

### Post by loell on 2009-07-19
iirc, pinoyskull has that kind of porblem too.

---

### Post by pinoyskull on 2009-07-19
> **creek23 said:**
> I installed Ubuntu NBR to my niece's MSi last May 2009 -- it worked perfectly with Smart Bro (the USB thingy) until last week (as my niece remembers).

Tried reconfiguring the USB for 3 hours and updating the kernel yet  nothing happened. Tried connecting the netbook to my WiFi router just to check -- it does connect.

So I'm guessing that this has something to do with tel co' system upgrading.

Do you know other Ubuntu users with Smart Bro having the same problem lately?
are you connecting to Smartbro automatically? If so, the problem is Network Manager config, i haven't fixed Network Manager setting for my USB Modem yet, but  you can use Gnome-PPP and wvdial to connect.

What is your modem's make?

---

### Post by creek23 on 2009-07-19
> **pinoyskull said:**
> are you connecting to Smartbro automatically? If so, the problem is Network Manager config, i haven't fixed Network Manager setting for my USB Modem yet, but  you can use Gnome-PPP and wvdial to connect.

What is your modem's make?

Back when it _was_ working (:D), I simply plugged-in the USB then a configuration dialog popped out. I had to select Smart as ISP then have it autamatically configured.

I did the same thing now that it's broken but it still didn't work.

When I toggle the icon to connect, I only get GSM foobar "Disconnected"

Can't remember much of the detail, they didn't leave the netbook for me to further check out the problem.

Will bump again soon once I have it -- probably next weekend :|

---

### Post by kilosan on 2009-07-19
The old smart bro usb zte stopped working out of the box with the latest jaunty. Still need to use intrepid to make it work out of the box. But its okay since the zte version is phased out and no longer being distributed by smart.

---

### Post by pinoyskull on 2009-07-20
> **kilosan said:**
> The old smart bro usb zte stopped working out of the box with the latest jaunty. Still need to use intrepid to make it work out of the box. But its okay since the zte version is phased out and no longer being distributed by smart.
are they using Huawei or a generic china made usb modem?

---

### Post by creek23 on 2009-07-20
> **kilosan said:**
> The old smart bro usb zte stopped working out of the box with the latest jaunty. Still need to use intrepid to make it work out of the box. But its okay since the zte version is phased out and no longer being distributed by smart.

Napagana ko naman sa Jaunty ung device, which she enjoyed using until first week of July. So I don't think its the ZTE USB one.

Tho, thanks sa info at try ko rin check. ;)

---

### Post by kilosan on 2009-07-20
> **pinoyskull said:**
> are they using Huawei or a generic china made usb modem?

The old one, they use ZTE, the new and small one is Huawei, Globe and Sun also uses Huawei.

---

### Post by creek23 on 2009-07-21
> **kilosan said:**
> The old one, they use ZTE, the new and small one is Huawei, Globe and Sun also uses Huawei.

Based from your description, I'm guessing my niece have the Huawei one -- it looked like a USB flash drive.

I don't know about you guys pero I always get the guilty feeling whenever I didn't get to fix a relative's or friends' PC. :(

Kung ba't naman kasi ang tagal ng weekend. Kating kati na ako ayusin.

---

### Post by manilaph on 2009-07-25
Hi fellow pinoys. I have never tried using my smartbro with Ubuntu yet .... until it becomes an out-of-the-box plug-and-play experience without having to tweak anything. I've read a lot of "it works now but after an update/upgrade... it now does not want to work"...

Have any of you tried this:
[http://umtsmon.sourceforge.net/](http://umtsmon.sourceforge.net/)

I know it is for 3g mobile stuff and might be able to work for smartbro too.

---

### Post by pinoyskull on 2009-07-27
> **manilaph said:**
> Hi fellow pinoys. I have never tried using my smartbro with Ubuntu yet .... until it becomes an out-of-the-box plug-and-play experience without having to tweak anything. I've read a lot of "it works now but after an update/upgrade... it now does not want to work"...

Have any of you tried this:
[http://umtsmon.sourceforge.net/](http://umtsmon.sourceforge.net/)

I know it is for 3g mobile stuff and might be able to work for smartbro too.
Found a Howto for Ubuntu
[http://ubuntuforums.org/showthread.php?p=5449081](http://ubuntuforums.org/showthread.php?p=5449081)

---

### Post by perbiu on 2009-08-03
@script warlock
busy pare.

Back to topic.
My mf622 smart also stop working even on intrepid ibex.
When i tried it on windows, the speed was 70kbits only when last time it was hitting 400kbits.

There maybe something wrong with their system, i hope its temporary.

---

### Post by manilaph on 2009-11-24
My fellow pinoys,

Have you tried the Huawei Smartbro on the latest Karmic already?

Do you think it will work with Debian 5.03?

---


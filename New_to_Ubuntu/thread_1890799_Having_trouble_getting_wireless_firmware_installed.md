---
title: "Having trouble getting wireless firmware installed (Ethernet broken)"
date: 2011-12-04
forum: New to Ubuntu
---

### Post by PerfectoOviedo on 2011-12-04
Greetings all,

This is my first time using any Linux system. I have ubuntu 11.10 installed over windows 7 (a friend installed it for me this way to see if I will like it/I didn't have a usb and my CD drive is busted. I plan to do a proper install once I know how to get the wireless up and running)

My ethernet is broken (it's an old laptop and things have started to go), so I've been using my desktop to bring over the wireless driver. I've tried installing the wireless a variety of ways through: Broadcom's readme suggested deleting other drivers already in place...all that did was make wireless for my windows partition not work (reinstalled those, so that's working again). Other walkthroughs in this forum and others yielded no results: I often ran into a "cannot locate package" or some such error, which was maddening since I was looking right at it, but the terminal wouldn't accept my path commands (just another thing I'll need to learn =p)

My laptop (the computer with ubuntu now) is an HP Pavilion dv6000 series.
My Wireless card is a Broadcom BCM4321 802.11 a/b/g/n [14e4:4328] (rev 03)

Many thanks for any assistance!

---

### Post by roger_1960 on 2011-12-04
Hi

Have a look at this thread.  It covers installing the drivers without internet, however I think you are gonig to need a live USB, but you could make one using windows and unetbootin?

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access)

---

### Post by PerfectoOviedo on 2011-12-04
Hey, thanks for the reply!

I did the tried and true method of "i've been doing this for 4 hours last night let me try again tomorrow morning" and used the broadcom tutorial again and it worked. I'm seeing linux is an exercise in "do it 'till you get it right." No idea what I was doing wrong last night, but maybe since I discovered sudo, things just decided to work. Just incase anyone else has the problem I had ever, here's the text:

[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

So yeah, problem fixed, but thanks anyway!

---


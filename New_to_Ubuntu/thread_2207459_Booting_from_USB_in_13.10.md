---
title: "Booting from USB in 13.10"
date: 2014-02-23
forum: New to Ubuntu
---

### Post by steamedxander on 2014-02-23
I created a bootable USB using 13.04 but when I try to boot my laptop that has 13.10 on it, it does not offer my USB as an option to boot from.

The laptop is a Macbook Pro 8,1 which is incompatible with 13.10 so I was hoping to install 13.04 cleanly over it.

How can I boot from my USB in Ubuntu 13.10?

---

### Post by Vladlenin5000 on 2014-02-23
Hi, welcome!

Sorry to say this but your post doesn't make sense.
1. First of all whether or not your laptop can boot from USB has nothing to do with OS it already has and it could've none, doesn't matter. The USB drive must be bootable, of course, and the computer must be able to boot from USB drives. This two are the *sine qua non* conditions and this two only.
2. There's no such thing as "incompatible with 13.10" but "compatible with 13.04". (you probably should report/comment about the issues you're having with the 13.10 in order to get help)
3. 13.04 is EOL (end of life), ie, no longer supported, forget it. The options should be the currently supported normal version - 13.10 - or the latest Long Term Support (LTS) version - 12.04 LTS (14.04 LTS will be released in April).

---

### Post by fdrake on 2014-02-23
this is specific to your computer model . [https://help.ubuntu.com/community/MacBookPro8-2/Raring](https://help.ubuntu.com/community/MacBookPro8-2/Raring)

or here [http://www.makeuseof.com/tag/how-to-boot-a-linux-live-usb-stick-on-your-mac/](http://www.makeuseof.com/tag/how-to-boot-a-linux-live-usb-stick-on-your-mac/)

post here if you get stuck

---

### Post by steamedxander on 2014-02-23
Alright then. I know the USB and computer are bootable (That's how 13.10 ended up on there.) So if I look into installing 12.04 or cleaning up 13.10, how do I go about booting from USB? It does not show up in the screen with Ubuntu and Mac OS X.

---

### Post by sandyd on 2014-02-23
Have you tried
> During boot hold down the option key and select EFI boot ( USB Icon )

---

### Post by monkeybrain20122 on 2014-02-23
13.04 has reached end of life so there is no point to install it now. Just saying.

---

### Post by steamedxander on 2014-02-23
> **sandyd said:**
> Have you tried

That's what I needed. Why couldn't I find this anywhere? Thank you!

---


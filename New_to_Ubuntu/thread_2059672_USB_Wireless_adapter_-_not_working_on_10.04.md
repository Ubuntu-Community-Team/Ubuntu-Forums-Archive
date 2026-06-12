---
title: "USB Wireless adapter - not working on 10.04"
date: 2012-09-18
forum: New to Ubuntu
---

### Post by Eanruig on 2012-09-18
The only stupid question is the one you don't ask, so here is mine.

First - the situation:
The wireless adapter is a Buffalo WLI-U2-KG125S.  It works with <whisper> Windows Vista</whisper> on an Acer Aspire 5155.  It also works on a Dell Inspiron B120 with 12.04.1, both from the hard drive and from a live USB.  However, the adapter doesn't work with 10.04 on the Dell hard drive or live USB.  I had 12.04 installed on the Dell, but it was so noticeably slow in application startup compared to 10.04 that I reverted to 10.04.

Now, the question:
Is there a command or sequence of commands I can use from a terminal on the live USB under 12.04 and from a terminal under 10.04 that will clue me in to what is different between them and move toward enabling the adapter to work under 10.04?

Thanks in advance for any help.

Eanruig

---

### Post by ShadowVegan on 2012-09-18
Not sure if this will work, as I too am a beginner in this area, but try these:

```
sudo ifconfig usb0 up
```

```
sudo ifup usb0
```

I assume it will be called usb0 but you could try other potential names like wlan0 or wlan1 (in place of usb0 in the above codes) as well.

Then again, you might have to install a driver or something.

---


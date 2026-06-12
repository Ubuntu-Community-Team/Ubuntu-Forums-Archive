---
title: "Doesn't retain settings. ( Wireless and Video setups)"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by ynneb on 2008-08-01
I have managed to get the wireless card to join the wireless net work at home but each time I reboot I have to set it up again, for it to work. Any ideas?

Same with the video card. I set it to use the linux nvidea driver, but on reboot it says it cant find the card.

I am closing the computer via the desktop exit method, and not just turning the computer off. I have no idea why the settings are not been retained on restart.
BTW I am talking about a HD install and not a live run. ( Just in case you thought I was completely dumb)

---

### Post by phidia on 2008-08-01
When you say "managed to get the wireless card..." specifically what did you do to enable it? From a terminal enter "iwconfig" and "lshw -C network"
Post the output of that.

I'm guessing that you are using Hardy (8.04)? xorg has changed with Hardy and some of that maybe the problem-not sure. Again in a terminal you can enter "sudo nvidia-xconfig" reboot and see if that helps.

---


---
title: "Memory Sticks"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by cambarne on 2008-06-01
hello,

I have just installed hardy heron and am trying to get my 'sony Memory Stick Duo Adaptor' to be recognised by my HP Pavillion zv6000 laptop, I insert the card but I get no icon on the desktop, nothing in the /media, nothing to click? I do a tail -f on /var/messages/log and I see the following every time I insert the card so the computer sees the card?

Jun  1 08:34:07 laptop kernel: [ 5803.763379] input: b43-phy0 as /devices/virtual/input/input63


help please

---

### Post by CloudFX on 2008-06-01
Do you know what your card reader's brand and model is?  Many card readers, including mine, aren't supported by Ubuntu yet.

---

### Post by cambarne on 2008-06-01
my card reader is built into my laptop, how can I find out if it is supported?

---

### Post by sayakb on 2008-06-01
Check for your device [here]("https://wiki.ubuntu.com/HardwareSupport"). My Cybershot's Memory stick doesn't work in Ubuntu either.

---

### Post by cambarne on 2008-06-01
I have now tried again with my external USB Scandisk imagemate card reader and that produces the same result, there is an entry into the /var/log/messages every time that I plug the card in but nothing shows up. If I do the test using a standard sony memory card then I get an icon on my desktop, I can browse the stick, no problem. My Memry card is a 2GB Memory Stick PRO Duo magicgate "magicgate thats a laugh, I will have to start refusing to accept anything sony as a present?"

---


---
title: "Headset"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by mr-Kirch on 2008-05-13
when i plug in my headset (its Logitech) it doesn't ask to install any drivers or anything then i got to sound recorder/Skype and i don't here anything and on Skype my friends don't here me..any help

---

### Post by Xiong Chiamiov on 2008-05-15
Is it usb or using a mic jack?

To get my plantronics headset working I had to compile alsa with the options
```

./configure --with-sequencer=yes --with-cards=usb-audio,ca0106 --with-oss=yes

```

---


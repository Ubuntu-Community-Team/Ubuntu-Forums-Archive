---
title: "Closing lid for Ubuntu Server on old laptop"
date: 2017-04-04
forum: New to Ubuntu
---

### Post by no-not-that-lucifer on 2017-04-04
I've set up Ubuntu server on an older laptop, which was a very straight forward process. I'm just stuck on one thing; how to turn off the screen only when closing the lid. At the moment, the screen switches off when closing and on when opening but everything else is locked up. The only way to get it back is by holding the power button or using REISUB.

I could live with the lid open, but it won't fit in the space.

---

### Post by Frogs Hair on 2017-04-04
Hello and Welcome

I don't know that the server edition has power settings to control what happens when the lid is closed like the desktop versions of Ubuntu. There maybe a CLI options others may know of though.

---

### Post by mastablasta on 2017-04-05
this might work: [SIZE=2]http://askubuntu.com/questions/141866/keep-ubuntu-server-running-on-a-laptop-with-the-lid-closed

server has power management. why not? mine is on 24/7 and i like to think that wheh we are not accessing it (only a few users) that it doesn't run at full or even 50% power.

the only thing interesting here is that the laptop lid is taken into account at default config on the server adition. :o

[/SIZE]

---

### Post by no-not-that-lucifer on 2017-04-05
It could have been a suspend -> resume[fail] cycle. I just closed the lid, counted to 25 and opened it again. I'll try the suggestion in the link tonight.

---

### Post by Frogs Hair on 2017-04-05
> [COLOR=#000000]the only thing interesting here is that the laptop lid is taken into account at default config on the server adition.[/COLOR]

Thanks, the clarification. 

> [COLOR=#000000] There maybe a CLI options others may know of though.[/COLOR]

And there was.

---

### Post by no-not-that-lucifer on 2017-04-05
And that worked. Thank you.  I had to reboot rather than simply restart the service.

---


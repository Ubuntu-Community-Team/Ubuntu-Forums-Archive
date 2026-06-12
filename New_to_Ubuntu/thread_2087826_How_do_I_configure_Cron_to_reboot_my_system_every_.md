---
title: "How do I configure Cron to reboot my system every 6 hours?"
date: 2012-11-24
forum: New to Ubuntu
---

### Post by Stepperer on 2012-11-24
I have Miniand MK802. It is a torrent server. (Oh, come on! for free i would run server on 8bits, not only on this baby :) )

For about every 6 hours internal wifi stops responding

Bad piece of plastics! =\

So. I configured everything to start at boot - now i must just organize said boot every 6 hours.

Playing with Cron didn't work

Best i could produce was 

"00 */6 * * * root /sbin/reboot" 

It wasn't enough =\

So please help me to beat this Chinese plastic piece ^)

(sorry for bad language, i'm Belarusian)

---

### Post by papibe on 2012-11-24
Hi Stepperer.

Don't edit the system crontab (/etc/crontab), but create a custom crontab for root instead using:
```
sudo crontab -e
```
Let us know how it goes.
Regards.

---

### Post by Stepperer on 2012-11-24
> no crontab for root - using an empty one

and then saved by the strange path - /tmp/crontab/b9AiYh/crontab

Will it really work?

---

### Post by papibe on 2012-11-24
It works on my test server running 12.04.

Regards.

---


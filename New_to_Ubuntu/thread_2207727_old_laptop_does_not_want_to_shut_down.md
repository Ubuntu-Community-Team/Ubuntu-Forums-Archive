---
title: "old laptop does not want to shut down"
date: 2014-02-24
forum: New to Ubuntu
---

### Post by Odyssey1942 on 2014-02-24
I have a grey haired lenovo laptop which had XP on it and I recently installed 12.04 in a single boot. It seems to work reasonably well most of the time, excepting some strange stuff in WiFi. 

But when I try to shut down, it just sits there with the sequencing dots until I force a power off. Don't know how long it might carry on but I have let it run for as much as an hour without it ever shutting itself down.

Any ideas? What information can I provide?0

---

### Post by mastablasta on 2014-02-25
hmm hard to say what is wrong without error messages. some lenovos have an option of installing special power management. perhaps that should be installed or is messed up for some reason.

if you press escape while the dots are on can you see any messages?

also you might want to check system logs for any reported errors. everything is loged in linux, so if there are any errors in shutdown procedure you should be able to see it there as well.

---

### Post by mörgæs on 2014-02-25
Does it help pressing the enter key?

---

### Post by Odyssey1942 on 2014-02-25
Hitting Enter seems to have no effect, nor does Esc produce an error message.

Which file might contain useful information?

Thanks to both.

---

### Post by tgalati4 on 2014-02-25
There are log files in /var/log.  

```
tail -100 /var/log/syslog
```

Only post the related errors not the entire file.

---

### Post by Odyssey1942 on 2014-03-09
Thanks for your help, but I have deferred action on this pending another decision, which was to replace Ubuntu 12.04 with Lubuntu 13.10. The problem has gone away and the computer is much more pleasant to use in that it is considerably faster. I miss the functionality of Ubuntu, but for the use that I make of this computer, it is a good trade-off.

---


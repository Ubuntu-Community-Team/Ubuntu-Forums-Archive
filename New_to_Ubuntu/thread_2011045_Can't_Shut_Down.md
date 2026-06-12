---
title: "Can't Shut Down"
date: 2012-06-26
forum: New to Ubuntu
---

### Post by MickeyPilgrim on 2012-06-26
Running 12.04.  When I want to shut down, the system brings up the log in. Help. I don't think it's good to hold the power button down until shut down happens, but thats all I can do.
MickeyPilgrim

---

### Post by wildmanne39 on 2012-06-26
Hi, this is one method for shutting sown or rebooting safely.

> Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB will get you safely restarted. REISUO will do a shutdown rather than a restart.
This is for when the system is locked up.

This should shut your computer down from the terminal:
```
sudo shutdown
```

You may want to run:
```
sudo tail -n100 /var/log/syslog
```
after you reboot from a failed shutdown to see what the logs say about the error.
Thanks

---

### Post by audiomick on 2012-06-26
> **wildmanne39 said:**
> 
This should shut your computer down from the terminal:
```
sudo shutdown
```


No it wont. Shutdown needs an option and a time.

the man page
```
man shutdown
```

to shut down and power off immediately

```
sudo shutdown -P now
```

to restart immediately

```
sudo shutdown -r now
```

---

### Post by wildmanne39 on 2012-06-26
Hi audiomick, thanks for correcting that, my book that I have did not say that an option was needed, guess I should have looked at the man pages.

---

### Post by spikoley on 2012-06-26
There is also *halt* and *reboot*.

```
sudo halt
```

```
sudo reboot
```

---


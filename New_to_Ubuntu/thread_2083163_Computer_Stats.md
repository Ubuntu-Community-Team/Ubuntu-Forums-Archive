---
title: "Computer Stats"
date: 2012-11-11
forum: New to Ubuntu
---

### Post by NDW57 on 2012-11-11
Sorry about what is probably a simple question........ In Windows (boo, hiss) you can right click on "Computer" or something and get your computer's vital statistics - not 36,24,36 guys. no, the amount of RAM installed, speed of CPU etc. I'm sure there must be a way to find this out in Ubuntu - how? (I could do to know as this PC is painfully slow at times and I have suspicion it's a bit low on the hardware front).

---

### Post by Jerry N on 2012-11-11
Not sure about latest versions of pure Ubuntu but in Mint with the Mate desktop you can get this information under System Administration>>System Information.

What's with the "Boo, Hiss"?  Are you unsure about your selection of Linux and somehow feel a need to justify?  Lots of us are quite comfortable about using both.

Jerry

---

### Post by cryptotheslow on 2012-11-11
If you are using 12.04 with the Unity desktop, go to the Dash and search for System Monitor. Should give you what you are looking for.

---

### Post by deadflowr on 2012-11-11
+1 for system monitor.
I also install system profile and benchmark, so as to see a more enriched outlook of the system as a whole.
You can also install conky.

---

### Post by ajgreeny on 2012-11-11
And if you want every last detail of the hardware, use the terminal command ```
sudo lshw -html > hw.html
``` and then open that hw.html file in your web browser, eg firefox.

---

### Post by newb85 on 2012-11-11
Beware as you're looking at stats, not all GB's are created equal.

For example, when I pull up my system specs in Ubuntu, I see that my machine has 5.7 GiB of RAM.  My machine was marketed as having 6 GB.  My initial reaction was that part of my memory was defective (on a brand new machine) or Ubuntu wasn't using all of my RAM.

That little *i* in the middle is important.  A kB sometimes means 1000 Bytes and sometimes means 1024 Bytes.  In larger units, things become more ambiguous.  MB could mean 1024 kB or 1000 kB (1,048,576 or 1,024,000 or 1,000 Bytes).  GB could mean 1024 MB or 1000MB (1,073,741,824 or 1,048,576,000 or 1,024,000,000 or 1,000,000,000 Bytes).  Whenever the abbreviation has the *i*, then it's a power of 1024.  1 GiB = 1024 MiB = 1,048,576 kiB = 1,073,741,824 Bytes.

So, whenever Ubuntu gives your specs in GiB, it's just being more precise (and probably more honest) about your hardware.

---

### Post by NDW57 on 2012-11-12
Thanks for all your help - sorted! As for Windows....I just get a bit tired of Microsoft's continued efforts to get everyone to use their products. I guess it is in their commercial interests to do so but it still doesn't stop me getting hacked off. And as Linux is "open" and there are sites like this I've always found it a damn sight easier to get assistance with Linux than Windows - and it's FREE !

---

### Post by dannyboy79 on 2012-11-12
very detailed info can be found out from cat'ing proc. so example would be

cat /proc/meminfo

or

cat /proc/cpuinfo

gives a lot of info

top is a really good command as well.

---

### Post by newb85 on 2012-11-12
On my system (Ubuntu 12.04), those files do not exist.  However, I can get good information from

```
cat /proc/meminfo
```
and
```
cat /proc/cpuinfo
```

(sudo isn't really necessary to read from files in the /proc directory.)

---

### Post by audiomick on 2012-11-12
I know this is marked as solved, but here is a bit of info that is good for reassurance about Linux RAM usage.

[http://www.linuxatemyram.com/]("http://www.linuxatemyram.com/")

---

### Post by dannyboy79 on 2012-11-13
> **newb85 said:**
> On my system (Ubuntu 12.04), those files do not exist.  However, I can get good information from

```
cat /proc/meminfo
```
and
```
cat /proc/cpuinfo
```

(sudo isn't really necessary to read from files in the /proc directory.)
i was at work and forgot the exact names. thanks. I fixed them and removed sudo.

---


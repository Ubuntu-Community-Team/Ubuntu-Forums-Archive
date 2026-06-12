---
title: "How do I find system information?"
date: 2012-08-12
forum: New to Ubuntu
---

### Post by robtygart on 2012-08-12
Where would I look to see the operating system info. On Ubuntu you can find it in "System Monitor" But Kubuntu has a different "System Monitor", and I can't find the Ubuntu version in the Software Center.

I want to see what it shows 32bit or 64bit version.

---

### Post by Bashing-om on 2012-08-12
rob:
run this command in terminal 
```
uname -a
```
the last datawise info will show if 32 or 64 bit (ie x86_64) says 64bit version.

[INDENT]regards
[/INDENT]

---

### Post by jerome1232 on 2012-08-12
-- edited --

Read the op wrong


you can get more specific with

```
uname -m
```

As for KDE, I haven't used it in a very long time and have no idea if there is a gui "system details" provided by default or not.

---

### Post by robtygart on 2012-08-12
```
rob@mobile:~$  uname -a
Linux mobile 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:03:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
rob@mobile:~$
```

Thanks

Rob

---

### Post by robtygart on 2012-08-12
I am dual booting and my Ubuntu is still 32bit.

Here is the results for reference.
```
rob@rob-mobile:~$ uname -m
i686
```

---

### Post by jerome1232 on 2012-08-13
Are running these commands on different installs? Different computers?

Your first post indicated 64 bit, your second post indicated 32 bit.

---

### Post by robtygart on 2012-08-13
Yes I am running from two different installs same computer different partition, I thought I would post the other one too, so if anyone is looking for the same info.

---

### Post by Cheesemill on 2012-08-13
For a complete rundown of your system information:
```
sudo lshw -html > ~/hardware_info.html && firefox ~/hardware_info.html
```

---

### Post by malspa on 2012-08-13
> **Cheesemill said:**
> For a complete rundown of your system information:
```
sudo lshw -html > ~/hardware_info.html && firefox ~/hardware_info.html
```

You'll want to make sure you have **lshw** installed.

And, if you prefer:

```
# lshw | less
```


Or, a front-end for lshw: **lshw-gtk**. You can start it from the terminal (as root). Click on any item for info; double click on the items in bold to drill down.

---

### Post by Cheesemill on 2012-08-13
> **malspa said:**
> You'll want to make sure you have **lshw** installed.
lshw is installed by default on all Ubuntu systems.

---

### Post by cmcanulty on 2012-08-13
for an easy GUI try installing sysinfo

---

### Post by robtygart on 2012-08-13
Thank you!!! I will need to save those commands, Sysinfo is great too.

---


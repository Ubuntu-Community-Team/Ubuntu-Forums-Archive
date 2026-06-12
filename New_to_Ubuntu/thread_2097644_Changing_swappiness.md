---
title: "Changing swappiness"
date: 2012-12-23
forum: New to Ubuntu
---

### Post by JHawk56 on 2012-12-23
After adding this line to my sysctl.conf:```
vm.swappiness=10
```I get these messages in my terminal window:

(gedit:2059): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.8F2SPW': No such file or directory

(gedit:2059): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

Is this because I have a wubi installation?

---

### Post by 2F4U on 2012-12-23
What version are you using? Look into these threads and see if the provided workarounds help in your case:

[http://ubuntuforums.org/showthread.php?t=1864688](http://ubuntuforums.org/showthread.php?t=1864688)
[http://ubuntuforums.org/showthread.php?t=1821846](http://ubuntuforums.org/showthread.php?t=1821846)

---

### Post by JHawk56 on 2012-12-23
After rebooting, I confirmed the change to a swappiness value of 10 took effect (although it's not producing any noticeable results in System Monitor).

---

### Post by ibjsb4 on 2012-12-24
> **JHawk56 said:**
> After rebooting, I confirmed the change to a swappiness value of 10 took effect (although it's not producing any noticeable results in System Monitor).

What are you seeing in system monitor?

Open a terminal and enter:

```
top
```

Also can try setting swappiness to zero.

---

### Post by JHawk56 on 2012-12-25
> **2F4U said:**
> What version are you using? Look into these threads and see if the provided workarounds help in your case:

[http://ubuntuforums.org/showthread.php?t=1864688](http://ubuntuforums.org/showthread.php?t=1864688)
[http://ubuntuforums.org/showthread.php?t=1821846](http://ubuntuforums.org/showthread.php?t=1821846)
I'm using Lubuntu 11.10. The suggested fix worked:```
sudo mkdir /root/.local/share
```although I had to break it into two parts as follows, because the parent folder didn't exist either:```
sudo mkdir /root/.local
sudo mkdir /root/.local/share
```
> **ibjsb4 said:**
> What are you seeing in system monitor?

Open a terminal and enter:

```
top
```

Also can try setting swappiness to zero.
I'd already run some comparisons using the GUI System Monitor (memory and swap figures are in MiB):
```


With only System Monitor Running:
Swappiness  Memory   Swap
    60        59      52
    10        56      52
     0        61      53

With 5 additional applications running:
Swappiness  Memory   Swap
    60       106     128
    10       105     127
     0       103     128
```

As you can see, swap starts out larger than necessary, and grows faster than RAM as total memory needs grow. The swappiness value has no effect.

I have a different release, Lubuntu 12.04, installed on another PC. Both have 512MB RAM, with separate video RAM:```

With only System Monitor Running:
Swappiness  Memory   Swap
    60       122       2
    10       124       0
     0       126       0

With the 5 additional applications running:
Swappiness  Memory   Swap
    60       242      15
    10       249       6
     0       255       0

With a bunch more stuff running:
Swappiness  Memory   Swap
    60       402      33
    10       418      17
     0       434       0
```

Not only does the swap usage start out smaller, but it actually responds to the swappiness value.

Swappiness appears to be broken in my 11.10. The same problem was reported here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/863552](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/863552)

---

### Post by JHawk56 on 2012-12-26
> **JHawk56 said:**
> The swappiness value has no effect.
I fixed it by installing all my updates. Lesson learned!

---


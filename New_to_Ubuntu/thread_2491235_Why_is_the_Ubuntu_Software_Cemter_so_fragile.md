---
title: "Why is the Ubuntu Software Cemter so fragile?"
date: 2023-10-01
forum: New to Ubuntu
---

### Post by johnnybegood2222 on 2023-10-01
Seems like most the time I try to search for something in it, using the magnifying glass, the little circle just turns and turns and turns.  This happened on my last install and happens now on clean installs on my laptop and desktop...

?

---

### Post by Rubi1200 on 2023-10-01
Not sure what version you are on and cannot really offer any help with this.

I just wanted to say that I never use the Software Center, instead using either Synaptic or the command line.

---

### Post by ubname on 2023-10-01
Hi, in my experience you should give some time to buid/sync package list download from internet, seems like it gets better using it. Slow internet or slow servers are also a problem, wait some more maybe.

---

### Post by oldfred on 2023-10-01
Saw this yesterday.
May be temporarily unavailable.

Canonical's Snap Store Hit By Malicious Apps
[https://www.phoronix.com/news/Snap-Store-Malicious-Apps](https://www.phoronix.com/news/Snap-Store-Malicious-Apps)[FONT=arial][/FONT]

---

### Post by johnnybegood2222 on 2023-10-03
I've let mine sit there forever to see if it builds any libraries or anything - but nothing....

---

### Post by Rubi1200 on 2023-10-03
Maybe clearing the cache and trying again would help.

In a terminal:

```
sudo apt clean
sudo apt update

```

---

### Post by #&amp;thj^% on 2023-10-03
> **Rubi1200 said:**
> Maybe clearing the cache and trying again would help.

In a terminal:

```
sudo apt clean
sudo apt update

```
+1
And this if it hangs:
```
 killall snap-store
```
and possibly a reinstall:
```
 sudo apt install --reinstall gnome-software
```
Please also read oldfreds post and link:
> Canonical's Snap Store Hit By Malicious Apps
[https://www.phoronix.com/news/Snap-Store-Malicious-Apps](https://www.phoronix.com/news/Snap-Store-Malicious-Apps)

---

### Post by johnnybegood2222 on 2023-10-03
> **Rubi1200 said:**
> Maybe clearing the cache and trying again would help.

In a terminal:

```
sudo apt clean
sudo apt update

```

Yes, those 2 commands got it working!

marking as solved

---

### Post by Rubi1200 on 2023-10-03
Excellent!

And thank you for marking the thread as Solved.

---


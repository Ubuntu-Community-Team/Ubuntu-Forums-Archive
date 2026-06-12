---
title: "Wireless problems"
date: 2012-08-22
forum: New to Ubuntu
---

### Post by Sly14Cat on 2012-08-22
The wireless worked for a little while when I had the LiveCD going but after a while it stopped working on the LiveCD. Once I installed Ubuntu it still wouldn't work. Only using wired connection will work. When I use wireless I connect to the router and type in the WPA/WPA2 password and it says I'm connected. Afterwards, it won't let me visit any websites and gets a unknown host error when I ping. Just now for a brief 15 seconds the wireless worked but once again stopped.

My adapter is the: Intel Wireless Centrino Wireless N-2230
*Note wireless still works in Windows 7

---

### Post by Hadaka on 2012-08-22
Hi, ubuntu 12.04 doesnt like N, and that may be what is causing you
problems....Try to configure your router to b/g   no N  and see if that
works for you.

---

### Post by anewguy on 2012-08-22
I'm not sure of the problem here, but I run wireless n with 12.04 with no problems.  It sounds more to me that perhaps it's a flaky driver.  wildmanne39 has a script you can download and run that will provide a lot of information for tracking this.

---

### Post by anewguy on 2012-08-23
Currently not sure why you are experiencing what you are.  What are the specifics on your hardware?

---

### Post by Sly14Cat on 2012-08-23
Which specs of my hardware?

Edit: Oddly enough I just booted into Ubuntu and now the wireless is working again. I found the snippet of code you were talking about and I'll try it once the wireless gets all funky again...

---

### Post by Sly14Cat on 2012-08-23
Oddly enough the next link I click doesn't work and the internet stops working. I'm now on the windows side. So what should I do?

---

### Post by gandaran on 2012-08-23
> **Sly14Cat said:**
> Oddly enough the next link I click doesn't work and the internet stops working. I'm now on the windows side. So what should I do?
try search for Intel wireless threads from the forum search box, there's plenty of threads with same problem as yours and I'm sure the fix is simple.

---

### Post by Sly14Cat on 2012-08-25
bump

I googled it and can't find any answers.

---

### Post by gandaran on 2012-08-26
> **Sly14Cat said:**
> bump

I googled it and can't find any answers.
okay, post the output of
```
sudo lshw -C network
```

---


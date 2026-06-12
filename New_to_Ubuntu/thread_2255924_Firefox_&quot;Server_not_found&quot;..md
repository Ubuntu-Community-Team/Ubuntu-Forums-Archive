---
title: "Firefox &quot;Server not found&quot;."
date: 2014-12-08
forum: New to Ubuntu
---

### Post by pheonixorchid on 2014-12-08
I am very new to ubuntu so please help me! Lol  I just updated ubuntu. Everything was working great with Firefox before I updated. Now it says "server not found" when I try to load any web pages.  I'm assuming my internet connection is working because it was before the update and it is working for everyone else in the house. Not sure even where to begin to fix this.  I tried reading other threads but I wasn't able to figure it out.  Thanks for your help!!

---

### Post by nerdtron on 2014-12-08
Have you rebooted? Any wrong settings in the Firefox>Options>Advance>Network>Settings?

---

### Post by pheonixorchid on 2014-12-08
Yes, I have rebooted and I have it set to "use system proxy settings".  I'm assuming that's right....

---

### Post by sandyd on 2014-12-08
Hi, can you post the output of the following commands

```

cat /etc/resolv.conf
ping -c10 8.8.8.8
ifconfig

```

---

### Post by pheonixorchid on 2014-12-08
Forgive my newness... But how do I put in each of those lines?  Do I do each of them seperatly?   I can't copy and paste as I can't use my web browser and I'm on my phone trying to figure this out.

---

### Post by pheonixorchid on 2014-12-08
Sorry. I figured out how to put it in...  Lol.
But it came back with a lot of stuff... Not sure what you're looking for.   I can't copy and paste it.....  :S

---

### Post by pheonixorchid on 2014-12-08
Lots of destination host unreachable.....

---

### Post by nerdtron on 2014-12-08
> **pheonixorchid said:**
> Lots of destination host unreachable.....

I suppose that is the output of the ping command?
Are you sure only firefox has connections issue?

---

### Post by sandyd on 2014-12-08
Run the following commands and post the output
```

route -n
ifconfig
```
If you cant post from the machine, you can run *gedit* from the unity dash, paste the text in, and put it on a USB drive. :)

---

### Post by pheonixorchid on 2014-12-08
It appears that it wasn't just Firefox that wasn't working like I thought.  Got the guy upstairs to reset the internet and it works now....  Thanks for the help!

---


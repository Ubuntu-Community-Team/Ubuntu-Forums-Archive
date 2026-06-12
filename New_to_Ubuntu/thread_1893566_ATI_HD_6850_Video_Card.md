---
title: "ATI HD 6850 Video Card"
date: 2011-12-10
forum: New to Ubuntu
---

### Post by rjwinters on 2011-12-10
Hello All

Is there a SUDO command for ATI drivers? (To Install)?

Thanks

 Bob

---

### Post by wolfen69 on 2011-12-10
Just go to *Additional Drivers* and activate the drivers. Reboot.

---

### Post by wolfen69 on 2011-12-10
Btw, the command line install would be:
```
sudo apt-get install fglrx
```

---

### Post by rjwinters on 2011-12-10
> **wolfen69 said:**
> Btw, the command line install would be:
```
sudo apt-get install fglrx
```


Hello Wolfen

This is what got with the code that you posted.I don't know if it is the right drivers!

Thanks for you help:popcorn:

Bob

---

### Post by dlanki on 2011-12-10
What version of ubuntu are you using? Normally when an ati card is detected available drivers for it will be listed in the additional drivers. I have noticed ati radeon 6850 can be particularly problematic with ubuntu so make sure your ubuntu is up to date.

---

### Post by rjwinters on 2011-12-10
Hello

Yes i have the new ubuntu 11.10 with all the updates.
Ubuntu runs in the same window has (Windows7-64bit)I don't know why!
In the pass i could not get the video right,but this time with 11.10 it loaded a driver.
I have a Dell/435T/9000/12M/Ram/With 2 DVD/Players/2 Hard drives.L-Cooled.I hope this helps>:D

Thanks for your time:popcorn:

Bob

---

### Post by wildmanne39 on 2011-12-10
Hi, so it looks like you are running ubuntu in virtualbox if that is the case you do not need to enable your ATI driver just install the guest additions which it looks like you have and enable 3d in virtualbox to do that you will have to have your vm shutdown here is a screen shot.

---

### Post by rjwinters on 2011-12-10
> **wildmanne39 said:**
> Hi, so it looks like you are running ubuntu in virtualbox if that is the case you do not need to enable your ATI driver just install the guest additions which it looks like you have and enable 3d in virtualbox to do that you will have to have your vm shutdown here is a screen shot.

Thanks for your help!!:P
That was the right message for me! Good.
**[COLOR=Sienna]Experience is the only genuine knowledge:KS[/COLOR]**

---

### Post by wildmanne39 on 2011-12-10
Hi, your welcome! if your problem is resolved, would you please go to the top of the page and mark this thread solved by clicking on thread tools. 
Thank you

---


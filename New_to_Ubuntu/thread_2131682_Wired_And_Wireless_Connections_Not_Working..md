---
title: "Wired And Wireless Connections Not Working."
date: 2013-04-02
forum: New to Ubuntu
---

### Post by Hamzyo on 2013-04-02
I have just installed Ubuntu on my old Samsung laptop, and I am having problems with networks. Upon first boot, my wi-fi connection worked fine and I could surf the web etc. but the next time I booted my laptop I was told that the wi-fi was not working (or something similar) and nothing I can do seems to fix the problem. I have tried using an ethernet cable and connecting the laptop directly to the router and have also tried numerous fixes on the forums, but nothing seems to work. When I click on the network button in the top right toolbar, no connections are displayed.

As I am a linux noob, I am sure the fix is incredibly simple!!! 

Thanks in advance.

---

### Post by Hamzyo on 2013-04-02
Just to add more information, I have checked drivers (I think), and I have tried uninstalling numerous things that people have said may cause bugs.

---

### Post by wildmanne39 on 2013-04-02
Go to this link:
[http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385](http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385)
Follow the directions for running the script without internet and attache the results here please.
Thanks

---

### Post by photonian on 2013-04-02
I suggest instead of troubleshooting, to just install "linux-firmware-nonfree" and reboot twice.
If this doesn't work then troubleshooting may be a good option.

---

### Post by Hamzyo on 2013-04-03
Sorry for the delay, I ran the script and was given the following result:

[http://pastebin.ubuntu.com/5673005/](http://pastebin.ubuntu.com/5673005/)

---

### Post by wildmanne39 on 2013-04-03
Did you upgrade the kernel? It looks like to me that several of the modules are not built into the kernel.
If you did buid the kernel or do a minimal install you will need to install the linux-image-extra deb as well.

You can try:
```
sudo modprobe ath9k
```
but I do not believe it will work.
Thanks

---

### Post by wildmanne39 on 2013-04-03
Also please post the output of:
```
sudo dpkg -s linux-image-extra-`uname -r`
```
Coutesy of chili555
Thanks

---

### Post by Hamzyo on 2013-04-03
Aha! Its working now, but I'm not sure if its to do with the first code or not.... Thank you very much for your help!!!

---

### Post by wildmanne39 on 2013-04-03
You have very few modules loaded so I suspect other things will not work also.

Still curious about the other questions I asked.
Thanks

---

### Post by Hamzyo on 2013-04-03
The result for the second code was [http://paste.ubuntu.com/5674126/](http://paste.ubuntu.com/5674126/)

---

### Post by wildmanne39 on 2013-04-03
The linux-image-extra is installed not what I expected but it is good.

---

### Post by Hamzyo on 2013-04-04
Interestingly enough, when I just logged on, I installed about 37 software updates, maybe they could be the things I was missing?

---

### Post by pimpn on 2013-04-04
Funny, i'm having a similar issue BUT it seemed to occur as a result of the updates for some reason.  I fixed it by deleting my wired connection and starting again with a new default connection.  However I have still not managed to return VPN access and VNC Viewer access.  Good luck!

---

### Post by wildmanne39 on 2013-04-04
> 
Interestingly enough, when I just logged on, I installed about 37 software updates, maybe they could be the things I was missing? 
I doubt it, unless you have issues I would not worry about it.
Thanks

---

### Post by Hamzyo on 2013-04-04
Thanks for all your help

---

### Post by wildmanne39 on 2013-04-04
Your welcome.
Enjoy!!!

---


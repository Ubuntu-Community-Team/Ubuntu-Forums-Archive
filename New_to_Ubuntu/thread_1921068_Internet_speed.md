---
title: "Internet speed"
date: 2012-02-06
forum: New to Ubuntu
---

### Post by harimurugan on 2012-02-06
i hav installed ubuntu 11.10 in windows.. when i access internet via Ubuntu its speed is very very slow compared to windows os.. i have tried firefox and chrome but nothing helpful.. can any one tell me wat i can do now????

---

### Post by GPilot on 2012-02-06
> **harimurugan said:**
> i hav installed ubuntu 11.10 in windows.. when i access internet via Ubuntu its speed is very very slow compared to windows os.. i have tried firefox and chrome but nothing helpful.. can any one tell me wat i can do now????

First of all I would suggest you post more specific information on your problem: Wireless or Cable? Network? Is your Ubuntu version up to date?Anything you could imagine being associated with this problem is important, a problem is often somehow complicated and associated with unexpected things.
Secondly: Is it a normal installation of Linux or a virtual one (inside a for example Virtual Box)?
Thirdly: Hardware details. All the drivers installed? 
And lastly: What are your specific speeds, is it a huge difference or really just a few kB/s?

---

### Post by wildmanne39 on 2012-02-06
Hi, if it is wireless I might can help, please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by stevensaal on 2012-02-06
Hi, I am having an issue similar to the original poster. I hope you'll extend the same help my way! I've followed your instructions and attached the two screenshots of the command results. I couldn't figure out how to insert the pictures inline. Thanks for any assistance... side note: I can use Firefox for about 15 seconds before it cannot connect to the server and then it won't until I restart the laptop. Even after this I was able to set up my Thunderbird, download all my emails too, but not send an email with both these pics on it. (Writing this from my desktop.) And what are the Post Icons for?

---

### Post by wildmanne39 on 2012-02-06
Hi stevensaal, I guess your wireless is slow? please try this:
```
gksudo gedit /etc/modprobe.d/ath5k.conf
```
Add a single line:
```
options ath5k nohwcrypt=1
```
Proofread carefully, save and close gedit. Reboot.

---

### Post by harimurugan on 2012-02-07
Not wireless one.. ethernet cable only.. i got my speed by turning off IPV6 in firefox..

---

### Post by wildmanne39 on 2012-02-07
Hi harimurugan, glad to hear you fixed it, please use thread tools at the top of this thread and mark solved.
Thanks

---

### Post by stevensaal on 2012-02-08
Thank you SO much, wildmanne39. I have no idea what I did or why it worked but thanks for walking me through all of those terminal and gedit entries b/c it did the trick! FF has never been faster on this old laptop.

---

### Post by wildmanne39 on 2012-02-08
Hi stevensaal, your welcome!

---


---
title: "unable to get wifi to work on zoostorm laptop"
date: 2012-12-29
forum: New to Ubuntu
---

### Post by nelliebellie on 2012-12-29
Hi New to forum and my first post. I bought a zoostorm laptop from e buyer no os intel pentium dc b980 2.4 ghz. with the intention to install ubuntu 11.04. Great problems installing, pc just freezes.  zoostorm tell me that these laptops do not allow ubuntu to be installed as they use UEFI instead of BIOS. The good news is ubuntu 12.10 supports UEFI and it installed a treat. My only problem is that I can't get the wifi to work. I cant even find out what is installed -nothing in the box. I suspect I need to download firm ware for the wifi. Does anyone have any idea how to do this. Any help much appreciated.

---

### Post by Pjotr123 on 2012-12-29
Try this roadmap:
[https://sites.google.com/site/easylinuxtipsproject/internet](https://sites.google.com/site/easylinuxtipsproject/internet)

---

### Post by audiomick on 2012-12-29
To find out what wireless card you have (and the ethernet card as well...)

open a terminal and do
```
sudo lshw -C network
```

To get a terminal, you can

use the key combination ctrl+alt+t

search for "terminal" in the dash and open it from there.


When you use sudo in the terminal, you are asked for your password. You wont see what you are typing. Type your password and hit enter.

The command generates a list of your hardware. If you use it without the option, it will list everything.  The option -C tells it to restrict it to the named class of hardware, in this case "network". Another useful one is
```
sudo lshw -C video
```
to find out exactly what your video card is.

---

### Post by nelliebellie on 2012-12-29
wow this is emberessing but here goes the symbol after sudo what is it? cant find it on my keyboard.
thanks

---

### Post by gnush on 2012-12-29
> **nelliebellie said:**
> wow this is emberessing but here goes the symbol after sudo what is it? cant find it on my keyboard.
thanks

You'll have to be more specific.

Are you referring to the hyphen (-)? Or Ctrl and/or Alt?

Ctrl and Alt are located at the bottom left, next to the space button.

The hyphen depends on what keyboard layout you use; in other words, what's your language?

---

### Post by arpanaut on 2012-12-29
If you copy and paste what is in the code boxes you will have better success than trying to re-type the commands.

I think that you are looking for the lower case "L" , re: your question

---

### Post by nelliebellie on 2012-12-30
Thanks for your replies much appreciated I will try them out asap

---


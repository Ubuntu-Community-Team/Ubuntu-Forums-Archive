---
title: "One month with Ubuntu and all NOT SO well.."
date: 2012-11-18
forum: New to Ubuntu
---

### Post by yiftah on 2012-11-18
Hello

I am an absolute newby to Ubuntu. I installed 12.10 as soon as it came out. 
I gave myself some learning time but still have a lot of problems. 

To begin with - Ubuntu starts... SOMETIMES. and sometimes it does not. 

Description
I use a new Samsung 305E with AMD quad core. 
I have Ubuntu installed side by side with Windows 7.

When I turn the computer on I get the GRUB screen.  and then ubuntu starts - OR it does not.. (about 50% of the times !!). 
When it does not - I get a blank  screen. Sometimes I hear the sound that usually comes with the "enter password".. but still evertything is blank. 
The only way out is turning the computer off (hardware turn off - never a good idea but no choice).  and hope that next time it works. (it happened that I needed to repeat that 3-4 times). 

I tried to update Grub. to no avail

Add that to the fact that under Ubuntu the computer does not wake up from "suspend" mode - and it means that every time I have to actually turn the computer off completetly.

---

### Post by coffeecat on 2012-11-18
> **yiftah said:**
>  
When it does not - I get a blank  screen. Sometimes I hear the sound that usually comes with the "enter password".. but still evertything is blank. 

That sounds like a LCD panel issue. I get the same with a BenQ monitor (but not with several other makes of monitor I have tried) which puts itself to sleep just before the login screen and I have to press the auto button to wake it up again. Since you hear the login sound, Ubuntu is clearly booting up and still working but the video signal has gone awol. Quite how you deal with this on a laptop, I don't know. Perhaps someone with experience of Samsung laptops would know. Are there any special function keys or buttons that affect the display on your laptop?

---

### Post by Impavidus on 2012-11-18
I once had a similar problem on a desktop running 10.04 (by now upgraded to 12.04):  when booting it gave some diagnostics (the same as when everything went right) and the the screen went blank. I think that somehow it was resolved by an update (I don't know which, I'm not the primary user of that computer any more), but each time I was able to reboot the computer using SysRq+REISUB. It's friendlier to your hardware and a nice opportunity to use that key. See [http://en.wikipedia.org/wiki/Magic_SysRq_key#Uses](http://en.wikipedia.org/wiki/Magic_SysRq_key#Uses) for details.

---

### Post by mlentink on 2012-11-18
Is your laptop by any chance equipped with an AMD graphics card? If so, after you have succesfully started ubuntu the next time, you may want to install the additional drivers for it.
Open Ubuntu Software Center select 'Edit' in the menubar and then 'Software sources'. Click on the tab 'Additional Drivers'.

---

### Post by Gster4 on 2012-11-18
> **yiftah said:**
> 

When I turn the computer on I get the GRUB screen.  and then ubuntu starts - OR it does not.. (about 50% of the times !!). 
When it does not - I get a blank  screen. Sometimes I hear the sound that usually comes with the "enter password".. but still evertything is blank. 

Add that to the fact that under Ubuntu the computer does not wake up from "suspend" mode 

the first one is a LCD display issue.  i don't know much about this, but for the second one, i had that before, but an upgrade fixed it in 12.04.  try updating

---

### Post by mlentink on 2012-11-18
> **Gster4 said:**
> but an upgrade fixed it in 12.04.  try updating
To what? OP just did a fresh install of 12.10

---

### Post by wildmanne39 on 2012-11-18
Hi, this will help keep you from having to do a hard reboot while you are in the process of resolving your issue.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
Thanks

---

### Post by yiftah on 2012-11-18
Thanks a lot. 
I don't know what grafic card is installed (its a laptop...). Ubuntu could not identify it. anyway - I installed "additional drivers" and throug it - AMD accelerator driver. let's see how things work. (I restarted and this time it went OK but we need some more restarts to make sure... 

I read the article Wild man directed me to. 
Thanks
I will try it next time I get stuck (hopefully I won't..) ;)

Yiftah

---

### Post by mlentink on 2012-11-18
You can cut and paste the following code and paste it in a terminal (ctrl+alt+T)
```
lspci | grep VGA
```
and paste the results back here

---


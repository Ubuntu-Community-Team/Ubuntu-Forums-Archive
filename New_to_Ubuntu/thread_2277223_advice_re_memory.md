---
title: "advice re memory"
date: 2015-05-07
forum: New to Ubuntu
---

### Post by jackobi on 2015-05-07
Hello Everyone
I am new to Linux so I am sorry if this is a silly question. I am using Xubuntu 14.04 LTS on my 10 years old laptop which only has 512mb of memory. My question is.
I get regular updates from Xubuntu which use little bits of memory every time. 
As 512mb is the minimum requirement for Xubuntu will I eventually struggle for memory before 14.04 LTS reaches its finishing date which I believe is 2017. 
If so as I can´t really afford to upgrade the memory is there anything I can do to save memory 
( eg remove old updates  )
I hope that I have explained this properly.
Thank you in advance for any help given.

---

### Post by v3.xx on 2015-05-07
What processor do you have?

---

### Post by jackobi on 2015-05-07
Hi v3.xx
The processor is a Celeron 2.6GHz

---

### Post by v3.xx on 2015-05-07
You should be ok with the current setup, but I think you will see a positive performance difference by switching to Lubuntu.  If you prefer to dig deeper into ram usage

You can monitor you ram usage with the command:
```
top
```
And take a look at what processes are using ram with the system monitor.

Edit
```
free -m
```
is a better command :)

---

### Post by jackobi on 2015-05-07
Hi v3.xx 
Thanks for the prompt reply. I will check it on a terminal after i have eaten.
Thanks again

---

### Post by v3.xx on 2015-05-07
I'll be in and out all day :)

---

### Post by RobGoss on 2015-05-07
A lighter version of Ubuntu should be OK with the amount of ram you have. Ubuntu 14.04 will use more resources the the lighter versions will.

---

### Post by mörgæs on 2015-05-07
> **jackobi said:**
> 
I get regular updates from Xubuntu which use little bits of memory every time. 


Do you mean that they use little bits of hard disk space?

---

### Post by buzzingrobot on 2015-05-07
> **jackobi said:**
> ...regular updates from Xubuntu which use little bits of memory... every time. 



If it's drive space the updates are adding to, don't worry about it unless you are getting close to having a full disk. If that's the case, I'll suggest removing software you do not use.  If it is not on your drive, it will not be updated.  And, it will be updated even if you don't use it.

Use the package manager tool for this (apt-get, Synaptic, Software Center, etc., which ever you prefer, to avoid mistakenly manually removing needed files).

Code takes up RAM when it's executed. If it isn't executed, it won't eat into your 512mb limit. Consider alternative applications that might require less RAM than those you currently use.  E.g., try Midori as an alternative to Firefox/Chromium/Chrome.  

I'll second the suggestion to look at Lubuntu, which is typically the 'lightest' of the Ubuntu derivatives. Burn an image to a DVD or USB stick, boot it and check it out in live mode.

Beyond Lubuntu, there is a wide range of traditional *window manager* offerings, and many of them use very little memory.  The tradeoff is that they usually require a lot a configuration by hand, and deal only with the managment of windows on screen, and do not offer all the other goodies desktop envirionments, even XFCE, offer.

---

### Post by Yellow Pasque on 2015-05-08
> If that's the case, I'll suggest removing software you do not use
apt-get clean might be helpful too.

---

### Post by Mark Phelps on 2015-05-08
>  I get regular updates from Xubuntu which use little bits of memory every time. 

You're confusing memory with disk space.  Updates don't use up additional memory; instead, they use up disk space.

What you reported is the amount of system memory in your laptop -- which is totally unrelated to available disk space.

---


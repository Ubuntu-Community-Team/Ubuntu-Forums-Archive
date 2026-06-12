---
title: "Applications randomly closing &amp; go missing"
date: 2012-02-26
forum: New to Ubuntu
---

### Post by Drowz0r on 2012-02-26
Hello all

For some reason, Skype randomly closes itself from time to time but I've noticed other applications started doing this. Mangler (basically ventrillo for ubuntu) has started doing it too. After some updates today, skype opens on start up fine along with my usual stuff but the PC literally takes about 30 seconds of chugging on the hard disc after my desktop has booted up. During this time, my mouse cursor lags to movement and it takes about 10 seconds for any character to appear that I type into the password field:

[http://img560.imageshack.us/img560/8350/screenshotat20120226104.png](http://img560.imageshack.us/img560/8350/screenshotat20120226104.png)

After the disc chugs away and the PC appears to be normal and working in real time, I'm able to hit "ok" on the password field but skype has already closed and I am unable to search for it:

[http://img402.imageshack.us/img402/8350/screenshotat20120226104.png](http://img402.imageshack.us/img402/8350/screenshotat20120226104.png)

I'm also unable to search for Manger. So, I check to see if they're installed and what do you know? I'm unable to search for the software centre either. The results are just blank.

It does however, find files such as images and music:

[http://img406.imageshack.us/img406/8479/screenshotat20120226105.png](http://img406.imageshack.us/img406/8479/screenshotat20120226105.png)

Applications like firefox which are pinned to the side, launch fine.

What is going on? o.o

P.S. I'm on Ubuntu 11.10 (64bit)

---

### Post by Krytarik on 2012-02-26
Try clearing the cache of Software Center:
```
rm -r ~/.cache/software-center
```This should get both your Dash's Application Lens and Software Center working again.

Regards.

---

### Post by Drowz0r on 2012-04-08
> **Krytarik said:**
> Try clearing the cache of Software Center:
```
rm -r ~/.cache/software-center
```This should get both your Dash's Application Lens and Software Center working again.

Regards.

Hello there

Skype I found out was a seperate issue and I've not been using mangler enough lately to fully test this - Ubuntu has been behaving! But I'll try this as soon as it stops playing nice :)

Thanks

---


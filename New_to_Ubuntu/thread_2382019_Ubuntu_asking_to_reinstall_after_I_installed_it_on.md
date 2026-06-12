---
title: "Ubuntu asking to reinstall after I installed it on my computer via USB"
date: 2018-01-08
forum: New to Ubuntu
---

### Post by ghostly-loomy on 2018-01-08
I am VERY new to Ubuntu and have been wanting to try it out. Up until now, it's been fairly smooth sailing. 
Anyway, onto my issue- 
I have gone through the entire installation process, erasing Windows and making Ubuntu is the only OS on my computer. All fine and dandy, until it restarts after the installation process, where it asks me if I want to install Ubuntu, effectively putting me in a loop. 
I've tried running my PC without the USB stick in, for it to say that there's no boot disk. 
I'm a little concerned, and would like to know if there's a way to remedy this. I'm currently running 16.04.3
Any advice would be greatly appreciated!

---

### Post by DuckHook on 2018-01-08
Welcome to the forums, ghostly-loomy.

At first glance, it seems to me that you might have your BIOS set to boot only from USB. Try setting it to boot from your HDD/SSD.

---

### Post by ghostly-loomy on 2018-01-08
Oh thank goodness, a reply!
Okay, thank you for this advice- Just to be sure, could you run me through the steps of doing this, just so I'm on the ball as far as what to do.

---

### Post by DuckHook on 2018-01-08
It's hard to give you precise instructions. Every BIOS is different. Your original description of your problem suggests that you have set your computer to always boot from USB. We don't really know if you've successfully installed Ubuntu, but the loop repeatedly asking you to install suggests that it boots into your LiveUSB medium every time. When the system says there is no boot disk (if you take out the USB), this implies that you either don't have an OS installed in your HDD, or that the BIOS is only permitting boot from USB.

Therefore, check BIOS first. You will have to read your computer documentation to figure out how to get into BIOS. It always involves some keys pressed during the POST process. There are so many key variants that I can't help you with that. On my system, it's the <Delete> key. On others, it's one of the <F*> keys. You will want to change the boot order so that the HDD/SSD is read at some point.

---

### Post by DuckHook on 2018-01-08
It is getting late in my time zone and I will be signing off soon. An alert in case you don't get a further reply from me.

---


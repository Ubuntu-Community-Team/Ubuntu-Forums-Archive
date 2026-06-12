---
title: "[SOLVED] Problems with desktop display/background/wallpaper"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by gshockxc on 2008-12-02
My first troubleshooting issue.  I don't know whether to cry or celebrate...

Everything was working fine after my install, and I used several programs (Firefox, Evolution, Games, Etc).  Yesterday, I got connected to the internet, and everything seemed okay.  I downloaded the updates, and still no issues that I could see.  I was adding some software packages from the repositories last night, and I played around a bit more.  Then I tried to change my desktop wallpaper, and the images had some really strange green colors that weren't there after the install.

The Hardy Heron wallpaper has a large green halo where tints of orange and brown used to be, but the bird is still the same color.  The other wallpapers have the same problem, green dispersed throughout where red, orange, and brown used to be.

There doesn't seem to be anything wrong other than the colors.  As far as I can tell, everything else works fine.  The desktop setting with no wallpaper, just the dark orange/rust background, seems fine as well.

---

### Post by overdrank on 2008-12-02
> **gshockxc said:**
> 
There doesn't seem to be anything wrong other than the colors.  As far as I can tell, everything else works fine.  The desktop setting with no wallpaper, just the dark orange/rust background, seems fine as well.

Hi and what is the model of the graphics card as some of the updates may have effective the drivers for the graphics.

---

### Post by gshockxc on 2008-12-02
> **overdrank said:**
> Hi and what is the model of the graphics card as some of the updates may have effective the drivers for the graphics.

I have an ASRock A780FullDisplayPort MB with onboard display, ATI Radeon HD 3200 chipset.

I suspect that you're correct, one of the updates messed up the graphics.

---

### Post by overdrank on 2008-12-02
> **gshockxc said:**
> I have an ASRock A780FullDisplayPort MB with onboard display, ATI Radeon HD 3200 chipset.

I suspect that you're correct, one of the updates messed up the graphics.

Ok you can try and use the command ```
gksu displayconfig-gtk
``` and adjust the graphics there.
If this fails you can use the xfix option at booting into recovery mode which is usually the second choice from grub.

---

### Post by gshockxc on 2008-12-02
Okay, I'm still having problems.  I tried to change the display configurations, but Ubuntu isn't recognizing the video card.  It's a VESA video card, but when I select that driver from the list and test the configuration, it fails.  Right now, the display resolution is 800x600, and I can't go any higher, so everything is HUGE on my screen.

Any help would be greatly appreciated.  Thanks much.

---

### Post by overdrank on 2008-12-02
> **gshockxc said:**
> Okay, I'm still having problems.  I tried to change the display configurations, but Ubuntu isn't recognizing the video card.  It's a VESA video card, but when I select that driver from the list and test the configuration, it fails.  Right now, the display resolution is 800x600, and I can't go any higher, so everything is HUGE on my screen.

Any help would be greatly appreciated.  Thanks much.

Hi and have you tried reinstalling the drivers? Also have you try the xfix option I mentioned earlier.

---

### Post by gshockxc on 2008-12-02
> **overdrank said:**
> Hi and have you tried reinstalling the drivers? Also have you try the xfix option I mentioned earlier.

I did try reinstalling the drivers.  I keep trying to get to the xfix option, but it loads too quickly, and I can't seem to catch it.  I'll keep trying.  Once I get to that, what am I looking for?

Thanks.

---

### Post by overdrank on 2008-12-02
> **gshockxc said:**
> I did try reinstalling the drivers.  I keep trying to get to the xfix option, but it loads too quickly, and I can't seem to catch it.  I'll keep trying.  Once I get to that, what am I looking for?

Thanks.

As soon as you see the grub loading press the esp key and then you can choose recovery mode. Once in recovery mode you will see 4 option I believe and the last is xfix select it and it will configure the graphics. The you can choose continue to boot normally.

---

### Post by gshockxc on 2008-12-02
> **overdrank said:**
> As soon as you see the grub loading press the esp key and then you can choose recovery mode. Once in recovery mode you will see 4 option I believe and the last is xfix select it and it will configure the graphics. The you can choose continue to boot normally.

Brilliant!!!  It worked like a charm, just as you said. Thanks for all of your help!!!

---


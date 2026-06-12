---
title: "External monitor not detected"
date: 2011-09-13
forum: New to Ubuntu
---

### Post by richard49 on 2011-09-13
I hope you can help as Ubuntu has me really confused as I've only recently (this week) installed it onto my laptop and am still finding my way around after being used to Windows 7.

After installing Ubuntu 11 I was able to go to System Settings > Monitors and in there I could see my laptop was recognised as well as my external Samsung monitor.

This evening (not sure exactly what I did) but after re-booting my laptop the Ubuntu main screen completely changes in that whereas i had my menu items at the top of the screen I now have a bar of icons down the left side of the screen; it all looks totally different now.

I suppose some kind of update happened... obviously eh? LOL

Anyway...

If I now go into System Settings > Monitors I can no longer see my external monitor; I just get an image (for the viewing screen) which says 'Unknown'.

If I click on 'Detect monitors' nothing happens.

How can I resolve this situation so that I can get my monitor which was recognised, and now isn't, to be recognised again?

Any help / advice would be very welcome.

Thanks,
Richard

---

### Post by Blasphemist on 2011-09-13
Please start with running this command to let us see what video card you have.
```
lspci | grep VGA
```
Xorg changed version with your upgrade to 11.04. I can tell that is what upgrade was done by your description of the desktop. More changed than just that but lets start there. Also, go into Additional drivers and see if anything needs enabled.

---

### Post by richard49 on 2011-09-14
> **Blasphemist said:**
> Please start with running this command to let us see what video card you have.
```
lspci | grep VGA
```Xorg changed version with your upgrade to 11.04. I can tell that is what upgrade was done by your description of the desktop. More changed than just that but lets start there. Also, go into Additional drivers and see if anything needs enabled.

According to 'Terminal' I have an nVidia G84 [Quadro FX 1600M]

I opened 'Additional Drivers' and it states...

NVIDIA accelerated graphics driver (version 173)
NVIDIA accelerated graphics driver (version current) [Recommended]

If I click on the topmost driver it states "This driver is not activated"
If I click on the second driver it states "This driver is activated but not currently in use"

I chose the second option (Version current) and re-booted but still get the information as stated above.

The laptop can still only use it's own screen as it doesn't detect my monitor attached to it.

Ubuntu is totally alien to me but I want to persevere with it as I like it as it's faster than my Windows 7.

Richard

---

### Post by Blasphemist on 2011-09-14
It looks to me from what I've found that you may need to run the nvidia-xconfig to get that external monitor working. If you don't find it in your menus, you can run it this way.
```
sudo nvidia-xconfig
```
I don't have nvidia and can't say I've experience with the utility. Do post if you have questions or it doesn't work.

---

### Post by richard49 on 2011-09-14
I've now managed (don't ask me how as I'm not sure) to get both my laptop and my monitor both showing exactly the same image.

How do I now configure 'things' so that only my monitor is on and my laptop screen is off?

Is it to do with the option "Separate x-screen" ?

I don't know what a separate x-screen is. :(

Thanks,
Richard

---

### Post by Blasphemist on 2011-09-14
I don't have nvidia so all I can do is look around and try to use logic. First, is there a way to deselect mirror screens that you can see? Also, you can try this command in the terminal.
```
man nvidia-xconfig
```
This may tell you how. I believe that in nvidia terms you want to enable twinview and not another x screen.

---


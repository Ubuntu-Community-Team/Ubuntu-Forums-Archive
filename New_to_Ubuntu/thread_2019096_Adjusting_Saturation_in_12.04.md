---
title: "Adjusting Saturation in 12.04"
date: 2012-07-07
forum: New to Ubuntu
---

### Post by Thrashrokz33 on 2012-07-07
Hi, fresh Ubuntu install here and the colors are a bit washed out and dull. Inside Windows, I was able to go into the Intel Graphics control panel to adjust contrast / brightness / saturation settings. I can't seem to find any Intel control panel inside Ubuntu though, I guess because I'm just using the stock video drivers that were pre-installed.

Is there an application or setting to adjust saturation? Or do I have to download the proprietary driver from Intel for that control panel?

---

### Post by Thrashrokz33 on 2012-07-07
anyone?

---

### Post by GreatDanton on 2012-07-07
1. What is your computer configuration: copy and paste this in terminal(ctrl+alt+t is shortcut):
```
lspci -v
```

2. Did you try to install your drivers via System settings/Aditional drivers.

Thanks

---

### Post by mgmiller on 2012-07-07
try hitting the super key (windows key) and typing the word "color" without the quotes.  In the resulting window, click the drop down arrow next to your computer name and then high lite the resulting display device.  You can now click on "View Details" on the bottom right and that will probably prompt you to install the software that you are looking for.  Once it's installed, you can adjust your colors from within the same color program.

Another way to find the color program is to click on the Gear/power icon in the top right corner of the panel and select System Settings from the drop down.  You will find an icon for Color in the resulting window in the Hardware section.

---

### Post by blastbeast on 2012-07-12
> **mgmiller said:**
> try hitting the super key (windows key) and typing the word "color" without the quotes.  In the resulting window, click the drop down arrow next to your computer name and then high lite the resulting display device.  You can now click on "View Details" on the bottom right and that will probably prompt you to install the software that you are looking for.  Once it's installed, you can adjust your colors from within the same color program.

Another way to find the color program is to click on the Gear/power icon in the top right corner of the panel and select System Settings from the drop down.  You will find an icon for Color in the resulting window in the Hardware section.
I've been trying to find the saturation and contrast settings myself for a few days now. I've installed the software by clicking on view details but post-installation there is no way to adjust colors in there. Not even calibrate is clickable. Clicking on view details again just shows me information about my display device.

Also, will changes made in unity also reflect in the cinnamon fork and gnome 3 installed on my machine?

---

### Post by FiveLock on 2012-10-25
I'm also having the same problem. Anyone ever figure this out?

---

### Post by Thrashrokz33 on 2012-10-25
I actually didn't find a good solution, but Redshift warms up the temperature a bit, which makes it look a lot better.

---

### Post by FiveLock on 2012-10-26
> **Thrashrokz33 said:**
> I actually didn't find a good solution, but Redshift warms up the temperature a bit, which makes it look a lot better.

Thanks for the suggestion! Redshift really helps.

---


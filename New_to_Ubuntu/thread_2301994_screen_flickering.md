---
title: "screen flickering"
date: 2015-11-06
forum: New to Ubuntu
---

### Post by switchex on 2015-11-06
Hello .. i just installed ubuntu version 14.04 on a HP laptop with intel Centrino Duo processor.  The issue is that as soon as i start the laptop, the screen starts flickering rapidly.  The flickering goes away as soon as i connect the laptop to an external monitor and it works fine even after i disconnect the external monitor from the laptop until i restart the laptop again!!

I have seen many posts related to this issue and understand it is related to the graphic driver,  requiring update. I just dont know what/which driver to install or update.

This is the information i got on my graphic card:

lspci -nnk | grep VGA -A1
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV530/M56-P [Mobility Radeon X1600] [1002:71c5]
    Subsystem: Hewlett-Packard Company Device [103c:30b4]

Can you kindly direct me to the the right software upgrade and the place to download?

I don’t know anything about linux, so if i have to any commands, i would also need details of the commands and how to run them.

Your help is greatly appreciated.

Thank you.

---

### Post by switchex on 2015-11-07
i have been searching 10 hours straight, trying to educate myself on linux and this issue ..  no luck:confused::confused:
i have probably made things worst (don’t know yet!) by adding, installing, and removing stuff that i have no idea about.  But i figured I can always re-instal ubuntu, once i figure out how to fix the flicker issue.
if anyone can please help, i would be so very thankful  ...

---

### Post by howefield on 2015-11-07
Is anything offered by "Additional Drivers".

Open the Dash and start typing Additional Drivers and the icon should appear..

---

### Post by switchex on 2015-11-07
under additional drive, i see an option for "using smartlink modem daemon from sl-damon ...."  
doesnt look like it is related to screen or graphics .. :-(

---

### Post by howefield on 2015-11-07
Having a quick look around, it would seem that your graphics card is no longer supported by the proprietary driver, so the open source driver is the only option. From a driver point of view, what you already have is as good as it gets.

---

### Post by switchex on 2015-11-07
please help me understand .. by the open source driver you mean the driver that comes with the Ubunutu already installed ?  

strange that the problem goes away if i connect the laptop to an external monitor and it stays good even after i disconnect from the monitor .. but as soon as i shut down and restart , the issue starts ..

sounds like i am out of luck?!!

---


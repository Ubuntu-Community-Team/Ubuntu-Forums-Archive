---
title: "Need Installation cd for HP 4470c scanjet"
date: 2020-09-25
forum: New to Ubuntu
---

### Post by silverfox42002-9 on 2020-09-25
[COLOR=#000000][RIGHT]
Join DateAug 2013Beans3[/RIGHT]

[/COLOR]
[COLOR=#000000][h=2]Need installation software for HP4470 scanjet[/h][INDENT]I have an hp 4470c scanjet and need installation cd in order to scan slides and negatives. I purchased the HP new and used it for scanning slides and negatives when I was using Windows XP and as time progress the cd was loaned to one of my suns friends. I want to scan our family negatives and slides for our sons for Christmas. I have many slides and negative which I had taken in Zambia when our son s where small and give them in digital form and create a slide show but in order to do this I need the installation cd and hp said they don't support my scanner. So I would greatly appreciate a copied HP installation cd.

Thanks for your anticipated assistance on this matter.[/INDENT]


[/COLOR]

[COLOR=#000000][FONT=Ubuntubeta][RIGHT]Join DateAug 2013Beans3[/RIGHT]

[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta][h=2]Need installation software for HP4470 scanjet[/h][INDENT]I have an hp 4470c scanjet and need installation cd in order to scan slides and negatives. I purchased the HP new and used it for scanning slides and negatives when I was using Windows XP and as time progress the cd was loaned to one of my suns friends. I want to scan our family negatives and slides for our sons for Christmas. I have many slides and negative which I had taken in Zambia when our son s where small and give them in digital form and create a slide show but in order to do this I need the installation cd and hp said they don't support my scanner. So I would greatly appreciate a copied HP installation cd.

Thanks for your anticipated assistance on this matter.[/INDENT]


[/FONT][/COLOR]

---

### Post by dino99 on 2020-09-25
Which ubuntu release are you using ? You need to know if your printer is found and well identified: glance at System Settings Printers menu.
Ubuntu usually install the required driver without manual needs, via system-config-printer-udev

Be sure to get an updated system (load synaptic)

---

### Post by Tadaen_Sylvermane on 2020-09-25
That disc will do you no good on Linux.  Hplip is the package you will need on your system. That is how I get my scanner to work on an Envy 5640. I'm sure it will work for you.

---

### Post by scorp123 on 2020-09-25
> **silverfox42002-9 said:**
>  [h=2]Need installation software for HP4470 scanjet[/h]

Did you check hp.com's support pages? Usually all Mac and Windows drivers can be downloaded from there.
Also: **What is your OS exactly?**

According to HP the scanner is no longer supported, e.g. the driver will work for Windows XP or 2000, but not for anything newer. The scanner will not work for Windows 7, 8.x or 10. And that driver CD is useless if you use Ubuntu or any other kind of Linux, since the drivers and other software on that CD were written for Windows XP.

If you want the scanner to work under Linux, you need to look at the **HPLIP** package that is in the repositories. Most scanners/printers by HP can be made to work using that. You don't need the original driver CD for that.

---


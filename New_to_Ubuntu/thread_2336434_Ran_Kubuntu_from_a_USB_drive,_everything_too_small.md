---
title: "Ran Kubuntu from a USB drive, everything too small??"
date: 2016-09-08
forum: New to Ubuntu
---

### Post by Robin_Perrett on 2016-09-08
I downloaded a Kubuntu .iso file & installed onto a USB drive. Booted from the drive but all dialog boxes, icons & text on the desktop were too small to read even with reading glasses. I had to use a magnifying glass. Any suggestions fellows? Would the fact that my Lenovo Yoga 3 Pro Ultrabook has a 3600 X 1800 resolution have anything to do with the problem?

---

### Post by sudodus on 2016-09-08
Probably yes :-)

Please check if Ubuntu is doing better with that high resolution (in a live drive of course).

Inside several application programs, you can change the fonts via a 'settings' or 'preferences' menu. Inside some programs, for example Firefox, you can use the hotkey combinations

***ctrl +*** (to increase the text size, repeat to increase more)
***ctrl -*** (to decrease the text size repeat to decrease more)
***ctrl 0*** (ctrl 'zero', to reset to the default)

Otherwise, maybe you can select a lower resolution, when you need larger texts that are fixed. You can try with xrandr or some graphical tool.

---

### Post by mastablasta on 2016-09-09
you should increase the font DPI. 

you can try to go to: System Settings > Display and monitor > Display configuration and then use the Scale display button.

more here: [SIZE=2]https://www.girialam.com/2016/02/kubuntu-and-hidpi-screen/
[/SIZE]

depending on your GPU you migth also be able to use it's settings.

as for Ubutnu -it could have same issue but here are a few options: [SIZE=2]http://askubuntu.com/questions/472262/adapt-ubuntu-to-a-high-dpi-resolution-screen?rq=1
[/SIZE]

---

### Post by Robin_Perrett on 2016-09-09
Thanks for those suggestions guys. I'm going to look into them in more detail. As a beginner with Kubuntu I think I'm going to have to study the operation of it a lot more, & then try out your suggestions. I can't really do anything on the desktop until I can read what I'm looking at.

---

### Post by J_Me on 2016-09-09
Yes it's to do with font DPI you can find it under Settings > Application Appearance > Fonts > tick the check box 'force fonts DPI'.

---

### Post by mastablasta on 2016-09-09
> **J_Me said:**
> Yes it's to do with font DPI you can find it under Settings > Application Appearance > Fonts > tick the check box 'force fonts DPI'.

but if they can't see how can they tick? is there a config text based file where they could fix this in recovery mode or something? surely there must be one.

to the OP what if you use nomodesetting on boot or if you boot using VGA mode. it should make all letters huge enough for you to do the necessery adjustments in the OS.

check option vga=xxxhttps://help.ubuntu.com/community/BootOptions

or use magnifier

---

### Post by J_Me on 2016-09-10
> but if they can't see how can they tick? is there a config text based file where they could fix this in recovery mode or something? surely there must be one.Umm...I haven't tried this myself but there's a startup bash script in /home/yourUserName/.kde/share/config/startupconfig. If OP wants to they could:
```
change this line
kcmfonts_general_forcefontdpi=0

to this
kcmfonts_general_forcefontdpi=96
96 is the default value given in system settings
```

---


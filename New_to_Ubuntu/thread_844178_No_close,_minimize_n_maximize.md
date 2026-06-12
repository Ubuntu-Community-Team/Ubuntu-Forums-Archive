---
title: "No close, minimize n maximize"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by NikS on 2008-06-29
I just updated my system n also installed compiz n now when i restarted I see that theres no close, minimize or maximize option in the upper right corner of ANY WINDOW i open!!!!
Y is it so??
DO i have to revert something???

The topmost bar itself, which we hold to move window is missing!!!!!

Plz help

---

### Post by forger on 2008-06-29
what operating system is this? Ubuntu hardy heron 8.04? 32-bit or 64-bit?
If so, go to Applications > Accessories > Terminal and type:
```
metacity --replace &
```
This will bring back the default window manager.

Now go to System > Preferences > Appearance > Visual Effects > Choose "Normal"
If that breaks your titlebars again, then probably your graphics card doesn't support compiz.

P.S. Please don't use shortcuts as "Y" or "n", makes it easier for other people to understand you :)

---

### Post by nothingspecial on 2008-06-29
While compiz is running, go to System >Preferences >Advanced Desktop Effects Settings and make sure the Window Decoration plugin is enabled.

---

### Post by dizee on 2008-06-29
```
gtk-window-decorator --replace
``` or ```
emerald --replace
``` should work with compiz.

press alt+f2 to run these.

emerald is needed if you installed the emerald window decorator with compiz.

---

### Post by bumanie on 2008-06-29
If you have a nvidia graphics card try > sudo nvidia-xconfig --add-argb-glx-visuals -d 24

---

### Post by NikS on 2008-06-29
> **forger said:**
> what operating system is this? Ubuntu hardy heron 8.04? 32-bit or 64-bit?
If so, go to Applications > Accessories > Terminal and type:
```
metacity --replace &
```
This will bring back the default window manager.

Now go to System > Preferences > Appearance > Visual Effects > Choose "Normal"
If that breaks your titlebars again, then probably your graphics card doesn't support compiz.

P.S. Please don't use shortcuts as "Y" or "n", makes it easier for other people to understand you :)

That worked!!!
But now it says i cant enable the Dektop effects!!!
So now, how do i uninstall compiz???

From package manager, is it??

---

### Post by NikS on 2008-06-29
Hey,
I removed compiz,
BUT I STILL CANT enable the desktop effects!!!
Its set to NONE!!!


Now it says it cant find compiz: no such file or directory!!!!
What do I do now???

Plz help!!!

---

### Post by Elfy on 2008-06-29
Reinstall it if you did in fact uninstall it. Make sure you have drivers installed for your graphics card - then set it to custom.

You might need to install simple-ccsm to get the custom option I did.

The settings manager, compizconfig-settings-manager, has the windows decoration plugin.

---

### Post by forger on 2008-06-29
1) You never actually replied to the question, what ubuntu release are you using?
2) What graphics card do you have? Post back the output of this command:
```
lspci | grep -i vga
```
3) ```
sudo apt-get install --reinstall compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins libcompizconfig0
```

Please post back with (1) and (2), **[SIZE="5"]your graphics card might not support desktop effects / compiz[/SIZE]**

---

### Post by NikS on 2008-06-29
Ok...
Right now I am in Windows, will have to go back to ubuntu for that command output, till then what I know is:

I am using Ubuntu 8.04,

n the graphics card is: Intel(R) 82845G/GL/GE/PE/GV Graphics controller Or Intel(R) Extreme Graphics controller!!

Min. Graphics Memory:	8 MB
Max. Graphics Memory:	64 MB

---

### Post by bhadotia on 2008-06-29
When I had that problem reloading the window decorator worked for me. I think the commands above do the same. But I used to reload using compiz fusion icon you can install it if you want its in the repos.

---

### Post by NikS on 2008-06-29
Well,
Heres the output of the command:

```

niks@Zion:~$ lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
niks@Zion:~$

```
Distro, as i said is Ubuntu 8.04,

N I was using the Desktop effects (Normal) before I tried to install compiz, so it supports Desktop effects for sure..
But not compiz i guess!!!

Help???

---

### Post by NikS on 2008-06-29
Someone PLEASE help me with this!!!!!

---

### Post by Elfy on 2008-06-30
Compiz is installed as default in hardy - if you were using normal desktop effects you were using compiz.

Have you got window decorations still.

---

### Post by katiad on 2008-06-30
Okay, so did you reinstall compiz after you uninstalled it?

If so, did you then restart X or reboot the computer, then attempt to enable desktop effects again? 

If yes, and it still doesn't work, have you checked to see that the proprietary (restricted) hardware drivers have been installed? Go to System --> Administration --> Hardware Drivers.  Is the graphics driver checked as enabled and labeled "in use"?

---

### Post by NikS on 2008-06-30
> **forestpixie said:**
> Compiz is installed as default in hardy - if you were using normal desktop effects you were using compiz.

Have you got window decorations still.

NOW that is what I did not know!!!!!
:)
Only the effects were disabled when i uninstalled compiz..
Well, I did reinstalled compiz as everyone said, but no results!!!

When I had installed compiz for the 1st time, i also had lost effects like Transparent terminal etc!! & were not restored after reinstalling compiz.

So, I Reinstalled UBUNTU!!!
n now, having some different problem, of reinstalling the packages I had downloaded. Though I had backed them up using APTonCD!!
How do i install them?? APTonCD Just restored them to cache....!!
Now what??
[http://ubuntuforums.org/showthread.php?t=844054](http://ubuntuforums.org/showthread.php?t=844054)

---

### Post by Elfy on 2008-06-30
If you have them in your cache the easiest way - also the easiest way to install if you know the name of a package is in the terminal

```
sudo apt-get install *package*
```

or if you know the name and path to the deb file you could use dpkg

```
 sudo dpkg -i /path/to/deb.deb
```

so for the compiz settings manager

```
sudo apt-get install compizconfig-settings-manager
```

You can also use search in the terminal if you have an idea what to search for, then you can use double click and middle button to paste

```
apt-cache search *package*
```

---

### Post by blakartz on 2008-09-13
Thanks,I am very new to Linux as a whole. Though I have a quick aptitude for learning new mediums I was stumped on this.

:guitar:

---


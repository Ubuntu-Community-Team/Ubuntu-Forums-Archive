---
title: "compizconfig and emerald...need some reading matierial"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by TimX on 2008-06-11
Can anyone direct me to a site that can explain in plain english on how to get the emerald themer to work with compizconfig? I've searched the internet and can't find something that makes sense to me.  It shouldn't be this difficult people.  I mean there are not even any help files with any of this software from the repositories. Makes me thing that linux people just think different.

---

### Post by overdrank on 2008-06-11
> **TimX said:**
> Can anyone direct me to a site that can explain in plain english on how to get the emerald themer to work with compizconfig? I've searched the internet and can't find something that makes sense to me.  It shouldn't be this difficult people.  I mean there are not even any help files with any of this software from the repositories. Makes me thing that linux people just think different.

HI and what issues are you having with emerald? Have you tried using the alt, F2 keys and use the command emerald --replace to enable emerald?

[http://wiki.compiz-fusion.org/Decorators/Emerald](http://wiki.compiz-fusion.org/Decorators/Emerald)

---

### Post by aktiwers on 2008-06-11
Did you install it already?
Then just open Terminal (Applications=>Accessories=>Terminal)
and type in:
```
emerald --replace
```If not, please have a look at Forlongs Blog :
[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

Edit:
If the emerald --replace does not work you, then you need to install emerald first:
```
sudo apt-get install emerald
``` and maybe some themes as well ```
sudo apt-get install emerald-themes
```

Then use the : emerald --replace command
And if you want to use emerald permanently, add the emerald --replace command to your System=>Preferences=> Sessions

Hope that helps

---

### Post by TimX on 2008-06-11
yes i have done that....but i lose all the close minimize and maximize buttons.

---

### Post by overdrank on 2008-06-11
> **TimX said:**
> yes i have done that....but i lose all the close minimize and maximize buttons.

What version of ubuntu are you using and  your model of graphics card?

---

### Post by TimX on 2008-06-11
actually i lose the whole windows border

---

### Post by TimX on 2008-06-11
i have an integrated intel 945 and hardy

---

### Post by TimX on 2008-06-11
> **aktiwers said:**
> Did you install it already?
Then just open Terminal (Applications=>Accessories=>Terminal)
and type in:
```
emerald --replace
```If not, please have a look at Forlongs Blog :
[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

Edit:
If the emerald --replace does not work you, then you need to install emerald first:
```
sudo apt-get install emerald
``` and maybe some themes as well ```
sudo apt-get install emerald-themes
```

Then use the : emerald --replace command
And if you want to use emerald permanently, add the emerald --replace command to your System=>Preferences=> Sessions

Hope that helps


for downloading the themes i get this:



Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package emerald-themes is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package emerald-themes has no installation candidate

---

### Post by overdrank on 2008-06-11
> **TimX said:**
> i have an integrated intel 945 and hardy

If you have CCSM install then under system, preference, advance desktop effects you may check the window decoration is checked.

---

### Post by Victormd on 2008-06-11
> Reading package lists... Done
Building dependency tree 
Reading state information... Done
Package emerald-themes is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package emerald-themes has no installation candidate

Emerald-themes isn't available in Hardy so you'll have to download them from somewhere else, i.e., [gnome-look]("http://www.gnome-look.org").
Looks like you have emerald installed properly but the reason why you're loosing your windows border is because you don't have any emerald theme installed. As soo as you install one and run
```
emerald --replace
``` you'll be good to go.
Note that you'll have to set it to start up with X so go to preferences>session and add emerald --replace

---

### Post by TimX on 2008-06-11
> **overdrank said:**
> If you have CCSM install then under system, preference, advance desktop effects you may check the window decoration is checked.


ok it was checked...so i unchecked it and the checked it again but that just take me back to the original compiz theme...if i do the replace emerald command again the buttons are again gone.

---

### Post by TimX on 2008-06-11
i think its missing the pixmap button...am i missing something here...did i not install something...i only downloaded compizconfig and emerald

---

### Post by overdrank on 2008-06-11
> **TimX said:**
> ok it was checked...so i unchecked it and the checked it again but that just take me back to the original compiz theme...if i do the replace emerald command again the buttons are again gone.

Ok I had this happen to me one time with intel chipset and I cannot remember exactly what I did but the only thing that comes to mind is search synaptic manger for intel and maybe instal the 915 resolution. Sorry I could not be of more help.

---

### Post by TimX on 2008-06-11
> **overdrank said:**
> Ok I had this happen to me one time with intel chipset and I cannot remember exactly what I did but the only thing that comes to mind is search synaptic manger for intel and maybe instal the 915 resolution. Sorry I could not be of more help.


oooh thats too much work...thanks though

---

### Post by Grishka on 2008-06-11
man, just use fusion-icon. emerald-themes are not in the repos, but you can download many from [http://www.gnome-look.org/](http://www.gnome-look.org/). and be sure to install fusion-icon, it helps with many problems like the ones you have.

---

### Post by overdrank on 2008-06-11
> **TimX said:**
> oooh thats too much work...thanks though

Too much work!!!!!!  System, administration, synaptic manger then in the search field type intel. click and install the 915 resolution. You are right that sounds like to much :)

---

### Post by TimX on 2008-06-11
> **overdrank said:**
> Too much work!!!!!!  System, administration, synaptic manger then in the search field type intel. click and install the 915 resolution. You are right that sounds like to much :)

Downloading it is easy....but have u read the read me file....yeah too much work!!!!

---

### Post by TimX on 2008-06-11
> **Grishka said:**
> man, just use fusion-icon. emerald-themes are not in the repos, but you can download many from [http://www.gnome-look.org/](http://www.gnome-look.org/). and be sure to install fusion-icon, it helps with many problems like the ones you have.

I will try.

---

### Post by aktiwers on 2008-06-11
TimX I think you misunderstand what Synaptic is. Think of it as "add/remove" in Windows... with connection to the internet...a search function...and the possibility to actually add software too! 

You open the application (in the menu go to: System => Administration=> Synaptic Package Manager)
Hit search and type in: intel
Pick the "915 resolution" package and hit apply 

Done! No readme.. done!

---

### Post by Victormd on 2008-06-11
The main reason you're loosing your windows decoration, is because you have no themes for emerald installed, simple, go to gnome-look.org and get some emerald themes there, install them, then try the above posts...

---


---
title: "[SOLVED] How to get those emerald themes?"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by faraz_k86 on 2008-11-24
K so I have installed compiz and emerald theme manager.

When I go to the theme manager I can see all those themes like crystal, minimal, red alice. But I dont know how to apply them..

How can I change me theme and how can I install new ones, 

I see a lot of youtube videos of ubuntu where people have some nice and transparent themes...

How can i get me one of those??

---

### Post by tjwoosta on 2008-11-24
to activate emerald you will need to open the run dialogue and run a simple command

(it is important to use the run dialouge (alt-f2) rather than using the terminal)

so press alt-f2 and run this command
```
emerald --replace
```
(this will replace the gtk window decorator with the emerald window decorator)


now after replacing gtk with emerald you should be able to easily switch between the emerald themes by simply clicking on it



to make emerald start every time you login you could add the emerald -replace command to the startup programs
(to add a program to the startup list, go to system-preferences-sessions and click the startup tab then click "add")


and lastly you can get emerald themes from [http://www.gnome-look.org]("http://www.gnome-look.org")  (they are listed under beryl)

you can install them by simply clicking import and searching for the .emerald file

---

### Post by faraz_k86 on 2008-11-26
Thanks a lot for the detailed reply tjwoosta.

Also can anyone please tell me if the video at the end of this page is using beryl or some other theme?

[http://hubpages.com/hub/Cool-Ubuntu-Tips-and-Tricks-for-Beginners](http://hubpages.com/hub/Cool-Ubuntu-Tips-and-Tricks-for-Beginners)

---

### Post by faraz_k86 on 2008-11-26
anyone?

---

### Post by binbash on 2008-11-26
It is compiz-fusion

---

### Post by faraz_k86 on 2008-11-27
and how do i get my desktop to look like that??

Also even when i used the command emerald --replace. the title windows of my windows changed according to the theme but the outlook of the destop was the same. I was expecting more

So how do I like completely change the outlook of my desktop using beryl?

---

### Post by Bigneil on 2008-11-27
> **faraz_k86 said:**
> Thanks a lot for the detailed reply tjwoosta.

Also can anyone please tell me if the video at the end of this page is using beryl or some other theme?

[http://hubpages.com/hub/Cool-Ubuntu-Tips-and-Tricks-for-Beginners](http://hubpages.com/hub/Cool-Ubuntu-Tips-and-Tricks-for-Beginners)

those are great effects, but i assume you must have an up-to-date pc to cope with them?

what are the system requirements for these great looking effects?

---

### Post by tjwoosta on 2008-11-27
> 
and how do i get my desktop to look like that??

Also even when i used the command emerald --replace. the title windows of my windows changed according to the theme but the outlook of the destop was the same. I was expecting more

So how do I like completely change the outlook of my desktop using beryl? 


i think you are referring to the famous compiz-fusion desktop cube


to get the desktop cube you will need to install CCSM (compiz config settings manager)


you an find CCSM in the add/remove list under the applications menu
(make sure you set it to search for "all availible applications" and you should find CCSM no problem)


after installing CCSM it will be located in the menu at "System-Preferences-CompizConfig Settings Manager"


now in CCSM click on "General Options" then click the "Desktop Size" tab and change the horizontal virtual value to "4" (or however many you want)


you can view the cube by using "ctrl-alt-left mouse button"  or ctrl-alt-(left or right d-pad)

or if you want you can even configure your cube to rotate when you move the mouse to edge of the screen  (that option is in the configurtaion for "rotate cube")

as you can see there are many many different setting you can play with


you can spend hours customizing your compiz to fit your desires, so there is really no reason for me to go into depth about everything  
(you'll figure it out once you start playing with settings)


> those are great effects, but i assume you must have an up-to-date pc to cope with them?

what are the system requirements for these great looking effects?

you do need to have a decent 3d graphics card, but nothing serious  (its nothing compared to what most video games require theese days)

(one of my computers is about 6 years old  and it runs compiz perfectly)


also my laptop right now runs smoother and is capable of handling more apps while running Ubuntu with compiz vs running vista with aero

---

### Post by faraz_k86 on 2008-11-27
Thanks but I already have the desktop cube effect and any other compiz effect. I was talking about the outlook. Like all the menu and the bottom and above bars were black. Also when a window was closed you would have noticed a nice fire effect..

---

### Post by Moop on 2008-11-27
Emerald is a window decorator. You need to change your theme to change everything else. Install the fusion icon. It makes it easy to switch between emerald and gtk. Find a theme you like that matches the emerald theme you like. (If that makes any sense)

---

### Post by tjwoosta on 2008-11-27
yea to change the general look of your desktop you will want gtk2.x themes
(they can also be found at [http://www.gnome-look.org/]("http://www.gnome-look.org/"))


emerald theme manager only themes the borders of the windows, the gtk themes change everything including borders and panels and everything

(most people use a combination of gtk and emerald themes to achive the desired look)

to change gtk themes is easy 

download the gtk theme (it usually comes compressed into a .tar.gz or a .tar.bz2)


go to system-preferences-appearance and simply drag your theme into the theme selector window and drop it

it should come up with a dialouge that says the theme was installed correctly

(sometimes if a theme wont install it is because certian themes will come double compressed, meaning you will have to extract the first .tar.gz or whatever and there should be another inside it that will work)

---

### Post by faraz_k86 on 2008-11-27
Thanks a lot guys.

---


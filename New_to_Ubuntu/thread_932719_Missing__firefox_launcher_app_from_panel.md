---
title: "Missing  firefox launcher app from panel"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by faron45 on 2008-09-28
Recently,somehow,I ended up losing my upper panel.Okay,well,I created a new panel & & added some new apps to it but,I cannot figure out how to add a firefox launcher app to the panel which was there before.Anybody have any clues as to how I can go about adding this launcher to my panel so that when I initially boot up it's already there ?
         Much thanks for any & all help
                 faron45 aka J.garcia :guitar:

---

### Post by jualin on 2008-09-28
If you have the "Application, Places, System" Menus on your panel, open Applications, Internet, Right click on Firefox, and then Add to panel. If you don't have that menu then add it by right clicking on your panel and then "Add to panel", then add the "Menu bar" and try what I suggested.

---

### Post by faron45 on 2008-09-28
Can't seem to do either,Jualin.When I try to add a new item to the panel,the "menu bar" option doesn't seem to be there.

---

### Post by lemuriaX on 2008-09-28
how about if you click and drag the Firefox icon from the Applications-->Internet menu over to your top bar?

---

### Post by faron45 on 2008-09-28
lemuriaX-Nope......I don't even have an "applications" menu anymore because of my loss of my original upper panel.I have no "internet" menu.If I click on "xfce menu" & then "network" firefox is there but I have tried dragging & dropping that & right clicking on it but,both to no avail.

---

### Post by lemuriaX on 2008-09-28
can you add a custom application launcher to the panel? If so, then you could assign the command "firefox" and click on the icon to browse for the firefox icon.

Edit: right click on the launcher icon and then choose properties, then click on the icon from there to search for the firefox icon - at least that's how you could do it in Gnome...I'd have to boot up my xubuntu box to be sure if that works in xubuntu as well...

Edit: Okay checked in my xubuntu and command should be just "firefox" there, so am editing my original post.

---

### Post by faron45 on 2008-09-28
Lemuria-Huh ?? Hmmm.So what you're telling me is I need to learn how to create a program launcher,correct ?

---

### Post by kansasnoob on 2008-09-28
> **faron45 said:**
> lemuriaX-Nope......I don't even have an "applications" menu anymore because of my loss of my original upper panel.I have no "internet" menu.If I click on "xfce menu" & then "network" firefox is there but I have tried dragging & dropping that & right clicking on it but,both to no avail.

So you're missing the entire panel?

If so I think you can get to terminal by pressing Alt+F2.

If that takes you to terminal then try what Aysiu says in his posts here:

[http://ubuntuforums.org/showthread.php?t=210021](http://ubuntuforums.org/showthread.php?t=210021)

---

### Post by lemuriaX on 2008-09-28
Okay yeah that thread Kansasnoob suggests looks like it would be helpful to you. 

My idea was just one way you could add it to your existing toolbar. I loaded up my xubuntu and made a correction to my  earlier post. Here's what I did to add a new Firefox launcher to my toolbar in xubuntu:

-right click on toolbar
-select Add New Item --> Launcher, then click on Add
-type "firefox" in the command field
-in the field next to the generic launcher icon enter "/usr/share/pixmaps/firefox-3.0.png" to use the Firefox icon
-check the box "use startup notification"
-click to close the dialog window

---

### Post by faron45 on 2008-09-28
Lemuria-if you're still here....How did you know to use.../usr/share/pixmaps/firefox-3.0.png ?? Where did you learn to do this ?

---

### Post by jualin on 2008-09-28
> **faron45 said:**
> Lemuria-if you're still here....How did you know to use.../usr/share/pixmaps/firefox-3.0.png ?? Where did you learn to do this ?

That's the location for the default icons. You can check the pixmaps folder if you want and you will see many icons located there.

---

### Post by lemuriaX on 2008-09-29
> **faron45 said:**
> Lemuria-if you're still here....How did you know to use.../usr/share/pixmaps/firefox-3.0.png ?? Where did you learn to do this ?

Hi Faron45, 

I just looked at the properties for the Firefox launcher I already had on my tool bar and checked what directory it was finding the icon.

---


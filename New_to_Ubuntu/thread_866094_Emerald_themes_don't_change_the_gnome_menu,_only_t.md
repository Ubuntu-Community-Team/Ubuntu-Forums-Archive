---
title: "Emerald themes don't change the gnome menu, only the windows.."
date: 2008-07-21
forum: New to Ubuntu
---

### Post by kramer65 on 2008-07-21
Hello,

I installed the emerald theme manager with which I installed a couple themes. All of them work nice and the windows and everything is changed. However, none of them is able to change the gnome-menu-panel-thing on the top and bottom.

Does anybody know why this could be?

---

### Post by kk0sse54 on 2008-07-21
Emerald themes only change the window borders in order to change your gnome menu icon you need to download and install another icon theme. Or if you are just talking about the panel in general then you need to go to a place like gnome-look.org and download and install another GTK theme.

---

### Post by dracayr on 2008-07-21
in order to change menus, you have to download a gtk theme (I recommend cobra blue)

dracayr

---

### Post by kramer65 on 2008-07-21
I am indeed talking about the panel, not the icons.

For example [this one]("http://www.gnome-look.org/content/show.php/Mac4Lin+ver.0.4+Emerald+Theme?content=71995") has in the screenshot also a different (suiting) panel. But when I install it the panel doesn't change..

If that is done seperately I would have to find some kind of suiting panel theme, which is a strange way to do this I think..

No idea to do this in a uniform way?

---

### Post by kk0sse54 on 2008-07-21
If you are talking about the dock on the bottum that is not a panel that's an application called avant-window-navigator which you can find in the Ubuntu repo's. Just go into the terminal and type ```
sudo apt-get install avant-window-navigator
``` and then after just configure it by adding the apps you want to it.

---

### Post by m_ad on 2008-07-21
GTK themes change the actual gnome-menu? I thought it was only customized through the Preferences of the actual panel.. :confused:

I think you'll find [this]("http://ubuntuforums.org/showthread.php?t=241868") (Mac-style Menu Bar for GNOME/Xfce!) tutorial helpful :)

---

### Post by billgoldberg on 2008-07-21
> **kramer65 said:**
> I am indeed talking about the panel, not the icons.

For example [this one]("http://www.gnome-look.org/content/show.php/Mac4Lin+ver.0.4+Emerald+Theme?content=71995") has in the screenshot also a different (suiting) panel. But when I install it the panel doesn't change..

If that is done seperately I would have to find some kind of suiting panel theme, which is a strange way to do this I think..

No idea to do this in a uniform way?

The panel is changed by a gtk theme (or you can use your own image).

Just look for the mac4lin gtk theme in gnome look.

Go to "system -> preferences -> appearance", press install and select the .tar.gz gtk theme.

It could be that you'll need to go to customize and look for it.

To grasp things better, click on the link in my signature called 'ultimate guide to customizing ubuntu'.

---

### Post by kramer65 on 2008-07-21
But I cant find the mac4lin in either the GTK1.x or the GTK2.x (and I don't know what the difference is between the two).

So why would they make a compiz theme which only makes the windows change, while they did include the panel in the screenshot?

I am getting totally lost in this...

---

### Post by kramer65 on 2008-07-21
I guess nobody knows then?

---

### Post by ibuclaw on 2008-07-21
Do you mean something like this?
[[IMG]http://img262.imageshack.us/img262/806/screenshotod2.th.png[/IMG]](http://img262.imageshack.us/my.php?image=screenshotod2.png)

Regards
Iain

---

### Post by kramer65 on 2008-07-21
Exactly! How do you get things like that?

---

### Post by ibuclaw on 2008-07-21
Emerald does not control this. Gnome does.

To change the panel, right click on the panel and go into "Properties"

Click on the "Background" tab and select the "Background Image" button, and browse for the image you wish to have as your panel.

Give me a minute, and I'll upload mine, if you wish.

Regards
Iain

---

### Post by ibuclaw on 2008-07-21
There you go...

They are both in the Attachments of this post.

[EDIT]
One appears to be missing, here are the direct links
[http://ubuntuforums.org/attachment.php?attachmentid=78517&stc=1&d=1216684393](http://ubuntuforums.org/attachment.php?attachmentid=78517&stc=1&d=1216684393)

[http://ubuntuforums.org/attachment.php?attachmentid=78516&stc=1&d=1216684393](http://ubuntuforums.org/attachment.php?attachmentid=78516&stc=1&d=1216684393)

Regards
Iain

---

### Post by kramer65 on 2008-07-21
Great! That would be good.

Do you also know a page where I can download things for this? Somewhere on gnome-look.org maybe? I am trying to make it look like an apple mac..

---

### Post by ad_267 on 2008-07-21
There are some panel backgrounds here: [http://www.gnome-look.org/index.php?xcontentmode=190](http://www.gnome-look.org/index.php?xcontentmode=190)

Just do a search for panel background.

---


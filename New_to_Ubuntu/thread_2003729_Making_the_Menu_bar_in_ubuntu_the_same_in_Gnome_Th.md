---
title: "Making the Menu bar in ubuntu the same in Gnome Theme"
date: 2012-06-14
forum: New to Ubuntu
---

### Post by SeanHall on 2012-06-14
Hello,

I am still reletivly new to Ubuntu, as I am still adjusting to the Ubuntu interface, the reason I switched to Ubuntu is because I am a Graphic designer and interface space is always good and I have always liked the mac finder bar, which is why I got Ubuntu because the task bar is more or less the same as the mac. Although the dock is really annoying, so I switched the theme to the gnome theme, via the login screen, but you lose the finder bar type bar on the top. So long story short, is their anyways to have the finder type bar on the top in the standard gnome theme?

---

### Post by camper365 on 2012-06-14
Are you talking about the Unity sidebar (has icons for your programs and shows which ones are open.  Also contains the main menu for you to search in)?  If you are, then you won't be able to get that in classic GNOME.
You may be able to change the theme if you go to Appearance Settings and modify the theme towards the bottom in the drop-down menu.  Because Unity is somewhat new, I don't know if there are places to download more from the Internet, but Ubuntu comes with a few built in.

---

### Post by SeanHall on 2012-06-14
No, I am not talking about the Dock. I am talking about the top bar, the bar with the dropdowns which appear when you roll over the window title. What I want to happen is to have that in the Ubuntu Standard theme. Thanks.

---

### Post by Shadius on 2012-06-14
It would help if you posted a screenshot.

---

### Post by buzzingrobot on 2012-06-14
If you mean you want a top menu bar as in OS X, with all apps putting their menus there, you can't get that now in either stock Ubuntu or stock Gnome. Or anything else that I'm aware of for Linux.

That said, both Gnome and Ubuntu want all their apps to display their menus in the top menu/panel bar.  Only a very few do right now. Since the vast majority of apps are written outside the purview of Ubuntu or Gnome, it's anyone's guess if their developers will abandon menus and heed the wishes of Gnome and Ubuntu. (Or, rather, keep in-app menus and add code for Gnome/Ubuntu.)  An app like Firefox puts its menu in Ubuntu's top panel because Ubuntu uses specific supplemental code to make that happen with Firefox.

I've played around with Cinnamon, one of the DE's used in Linux Mint, and an add-on dock.  Cinnamon's panel can be relocated to the top.  With a dock centered along the bottom, it's reminiscent of OS X.

---

### Post by Frogs Hair on 2012-06-14
It's possible to add a menu indicator to Unity, but it is not the same as the menu that appears in Classic Gnome. Another option would be to install a dock such as Awn , GLX  or Docky from the software center in your Classic Gnome session.

[http://www.liberiangeek.net/2012/05/install-classic-menu-indicator-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/05/install-classic-menu-indicator-in-ubuntu-12-04-precise-pangolin/)

---

### Post by SeanHall on 2012-06-14
So there is no way to get the tool bar onto the top bar?
[IMG]http://i.minus.com/jd99bcoCjNKat.png[/IMG]

---

### Post by Shadius on 2012-06-14
> **SeanHall said:**
> So there is no way to get the tool bar onto the top bar?
[IMG]http://i.minus.com/jd99bcoCjNKat.png[/IMG]

So you want **File, Edit, View, History**...etc onto the top panel?

---

### Post by SeanHall on 2012-06-14
Yes, but without having to use the default ubuntu theme with the unity dock.

---

### Post by Shadius on 2012-06-14
> **SeanHall said:**
> Yes without using the default ubuntu theme with the unity dock.

My setup is like that right now. It's called Global Menu. Do **Alt+Right Click** on the panel and select **Add to Panel**, then select **Indicator Applet Appmenu**. You should be good to go from there. Open up a program to test it.

---

### Post by SeanHall on 2012-06-14
I can't Alt+Right Click on the bar.

---

### Post by Shadius on 2012-06-14
What desktop environment are you using? Unity? Post a screenshot of your entire desktop please.

---

### Post by SeanHall on 2012-06-14
[IMG]http://i.minus.com/jY9mwSjtoP9Br.png[/IMG]

---

### Post by Shadius on 2012-06-14
Okay, that looks like you're using GNOME Classic desktop environment. Correct me if I'm wrong. Give me a few minutes to search how I got back my Global Menu.

---

### Post by Shadius on 2012-06-14
Okay, this should be it. Run this code in a Terminal. If you don't know how to open the Terminal, the keyboard shortcut is **Ctrl+Alt+T**.

```
sudo add-apt-repository ppa:jconti/gnome3
sudo apt-get update
sudo apt-get install indicator-applet-appmenu
```

Then **Alt+Right Click** on the top panel and select Indicator Applet Appmenu. 

You should be set now. :)

---

### Post by SeanHall on 2012-06-14
Done that, do I log out and back in?
[IMG]http://i.minus.com/jXui4HAXVjDD6.png[/IMG]

---

### Post by Shadius on 2012-06-14
> **SeanHall said:**
> Done that, do I log out and back in?
[IMG]http://i.minus.com/jXui4HAXVjDD6.png[/IMG]

Seems some things failed, but try **Alt+Right Click **on the top panel and select "**Add to Panel**", then select **Indicator Applet Appmenu**.

---

### Post by SeanHall on 2012-06-14
Still Can't right click on the panel bar.

---

### Post by Shadius on 2012-06-14
> **SeanHall said:**
> Still Can't right click on the panel bar.

Make sure you're holding down the **Alt** button while right clicking. If this doesn't work, I'm out of ideas. This was the method I used to get my Global Menu.

---

### Post by SeanHall on 2012-06-14
I have tried right clicking with alt and it still does not work.

---

### Post by Shadius on 2012-06-14
I suppose you can try this. [Global Menu]("http://www.techlw.com/2012/02/enable-classic-application-menu-on.html")

---

### Post by SeanHall on 2012-06-15
Will do, thanks for the help.

---

### Post by Shadius on 2012-06-15
No problem. Hope that works for you.

---

### Post by Shadius on 2012-06-15
> **SeanHall said:**
> Hello,

Although the dock is really annoying, so I switched the theme to the gnome theme, via the login screen, but you lose the finder bar type bar on the top. So long story short, is their anyways to have the finder type bar on the top in the standard gnome theme?

You said you switched to the "gnome theme" from the login screen. The proper term would be Desktop Environment, so to be specific, which GNOME desktop environment? 

What options do you see from your login screen? 

I can assume there's Ubuntu and Ubuntu 2D. Is there GNOME, GNOME Classic and GNOME Classic (No effects)? If so, which do you log into? 

I'll try my best for further help you. :)

---

### Post by SeanHall on 2012-06-15
> **Shadius said:**
> You said you switched to the "gnome theme" from the login screen. The proper term would be Desktop Environment, so to be specific, which GNOME desktop environment? 

What options do you see from your login screen? 

I can assume there's Ubuntu and Ubuntu 2D. Is there GNOME, GNOME Classic and GNOME Classic (No effects)? If so, which do you log into? 

I'll try my best for further help you. :)

I logged in using Gnome Classic, because the unity dock is bulky and annoying.

---

### Post by Shadius on 2012-06-16
> **SeanHall said:**
> I logged in using Gnome Classic, because the unity dock is bulky and annoying.

Agreed. That's why I've switched to using GNOME Classic (No effects). 

[Try this]("http://www.webupd8.org/2011/11/indicator-applet-ported-to-gnome-3-can.html")

---

### Post by waynefoutz on 2012-06-16
Try this one:

[http://www.webupd8.org/2011/11/indicator-applet-ported-to-gnome-3-can.html]("http://www.webupd8.org/2011/11/indicator-applet-ported-to-gnome-3-can.html")

---

### Post by Shadius on 2012-06-16
> **waynefoutz said:**
> Try this one:

[http://www.webupd8.org/2011/11/indicator-applet-ported-to-gnome-3-can.html]("http://www.webupd8.org/2011/11/indicator-applet-ported-to-gnome-3-can.html")

Same link I've provided.

---

### Post by Shadius on 2012-06-20
Came across something today and thought of your thread. Instead of doing **Alt**+**Right Click**, do **Alt**+**Super Key (Usually the Windows key)**+**Right Click** on the panel and follow the previous instructions I gave. Let me know if that works.

---

### Post by vaalir on 2012-07-18
[IMG]https://dl.dropbox.com/u/11801510/Screenshot%20from%202012-07-18%2021%3A58%3A19.png[/IMG]

like this?

if so, this can easily be achieved by actually using the unity interface.
[follow these instructions]("http://www.noobslab.com/2012/05/update-v2-mac-os-x-theme-ver2-for.html")

and you can change the look of it all later by adding some GTK themes for instance.. 

so it becomes like this for instance.
[IMG]https://dl.dropbox.com/u/11801510/Screenshot%20from%202012-07-18%2022%3A03%3A08.png[/IMG]

---


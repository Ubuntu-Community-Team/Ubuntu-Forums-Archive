---
title: "installed ambiance theme, menus still white?"
date: 2012-09-18
forum: New to Ubuntu
---

### Post by aem0512 on 2012-09-18
I installed the light themes from synaptic but when I went to Customize look and feel, I clicked the Ambiance theme but the menus won't change from white? What's going wrong?

---

### Post by vasa1 on 2012-09-18
Have you logged out and logged in again? Sometimes, that helps register the theme change.

---

### Post by aem0512 on 2012-09-18
Yes I've even restarted the system. The menus are still white :-/

---

### Post by mips on 2012-09-19
Lubuntu uses openbox as the window manager and that uses it's own themes. You have to change both the gtk & openbox themes.

From the "Customize Look & Feel" menu select tabs,
1. "Widget" to change the gtk theme
2. "Window Border" to change the Openbox theme. 
You can also use the "Openbox Configuration Manager" under preferences to do the same thing.

If there is no default ambience theme included for openbox (as is the case here) then go find a suitable theme to match on [http://box-look.org/](http://box-look.org/)

[http://box-look.org/content/search.php](http://box-look.org/content/search.php)
Type: Openbox Theme
Description contains: ambiance

The above search will return 7 results which you can pick from, download and install. Note that the themes have been rated by people so the highest rated one is usually best but you can try them all for yourself.

---

### Post by Rodney9 on 2012-09-19
For How-To's and Information on Lubuntu

[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

For  Screen-Casts on Lubuntu

[http://blip.tv/rss/bookmarks/206798](http://blip.tv/rss/bookmarks/206798)

Rodney

---

### Post by TenPlus1 on 2012-09-19
Here is the Ambiance heme for Openbox, download and place files in usr/share/themes to use...

[http://box-look.org/content/show.php/Ambiance?content=142373](http://box-look.org/content/show.php/Ambiance?content=142373)

---

### Post by vasa1 on 2012-09-19
> **aem0512 said:**
> I installed the light themes from synaptic but when I went to Customize look and feel, I clicked the Ambiance theme but the menus won't change from white? What's going wrong?
What do you see versus what you expect?
When I select the Ambiance theme from "Customize look and feel", the menus are as shown in the images. Do you see or expect something different? The gtk2 apps such as Firefox and LibreOffice go one way, white; the gtk3 apps such as Evince and Sudoku go dark.
BTW, this is on Lubuntu 12.04.

---

### Post by newb85 on 2012-09-19
> **aem0512 said:**
> I installed the light themes from synaptic but when I went to Customize look and feel, I clicked the Ambiance theme but the menus won't change from white? What's going wrong?

If you're referring to menus associated with the DE (not the menus within windows), it's a bug in the Ambiance theme.  The Ubuntu devs. got around it by overriding the menu color in Unity.

You can fix it by following the instructions at [http://www.webupd8.org/2012/05/install-ambiance-fixed-for-classic.html]("http://www.webupd8.org/2012/05/install-ambiance-fixed-for-classic.html")

---

### Post by aem0512 on 2012-09-19
Thanks for all the replies. I have extracted the file to usr/share/themes as someone suggested above and definitely applied the theme through both the customize look & feel gui and the openbox configuration manager. 

However, the application menus when I click on the task bar are still white. And in some programs when I click on say "File" the drop down menu there is white also.

---

### Post by vasa1 on 2012-09-19
> **aem0512 said:**
> ... And in some programs when I click on say "File" the drop down menu there is white also.
Could you **please** specify which are these "some programs"?
Evidently, others work okay?

---

### Post by aem0512 on 2012-09-19
> **vasa1 said:**
> Could you **please** specify which are these "some programs"?
Evidently, others work okay?

Sorry, actually all of the menus in all programs ("File", "Tools", etc) are white when clicked, except for when I right click on the title bar, those are dark.

---

### Post by aem0512 on 2012-09-19
This is what I see when I click my applications menu from the panel.

---

### Post by newb85 on 2012-09-19
> **aem0512 said:**
> This is what I see when I click my applications menu from the panel.

So, did you check out the link in my first post (#8)?  I was experiencing the same behavior in my Cairo-Dock session until I follow the instructions there.

---

### Post by aem0512 on 2012-09-19
Yes, but after adding the ppa and updating & upgrading, nothing downloaded so I guess I had the newest version already?

---

### Post by vasa1 on 2012-09-20
> **newb85 said:**
> If you're referring to menus associated with the DE (not the menus within windows), it's a bug in the Ambiance theme.  The Ubuntu devs. got around it by overriding the menu color in Unity.

You can fix it by following the instructions at [http://www.webupd8.org/2012/05/install-ambiance-fixed-for-classic.html]("http://www.webupd8.org/2012/05/install-ambiance-fixed-for-classic.html")
There was an update of light themes (Ambiance and Radiance) a month or so ago and I'm assuming that the referenced bug was fixed by then.

This bug describes what *I* see: [https://bugs.launchpad.net/light-themes/+bug/1047736](https://bugs.launchpad.net/light-themes/+bug/1047736) and mentioned above with images.

Anyway, I don't understand the OP's problem.
Maybe there's some confusion between the window manager theme and the regular theme.
Because OP writes, "*Sorry, actually all of the menus in all programs ("File", "Tools", etc) are white when clicked, except for when I right click on the title bar, those are dark*."
If that is so, OP should try to pick a window manager theme that closest resembles Ambiance.

---

### Post by vasa1 on 2012-09-20
Here's a link that may be of some help:
[How to Theme Up Lubuntu]("http://maketecheasier.com/theme-up-lubuntu/2011/02/11")

---

### Post by aem0512 on 2012-09-20
I've changed all three, the openbox window border, the icon theme, and the widget to ambiance.

I have followed the instructions in this link ([http://maketecheasier.com/theme-up-lubuntu/2011/02/11](http://maketecheasier.com/theme-up-lubuntu/2011/02/11)) perfectly but my results are still the same. All white menus, panel menu is white, and all menus for every application are white. Right click has a white menu also. 

The bug report says "When I use Ambiance theme, in gtk3 apps like gedit , the context menu (mouse right click menu) appears to be dark background and light text. While in gtk2 apps like firefox and chrome, the context menu appears to be light background and black text..." 

But I have no dark menus at all like this bug reporter.

---

### Post by aem0512 on 2012-09-20
Aha! Problem solved. 

I was using the "light themes" package from synaptic and that did not work. Then I tried the "ambiance 12.04" package from ravefinity and that did not work either. 

Then I tried the "ambiance 11.04" package from ravefinity and it works like a charm! All menus looks as they should. See link and choose the "Ubuntu 11.04 or older" if you're having the same problem as me:

[http://www.ravefinity.com/p/download-ambiance-radiance-themes-for.html](http://www.ravefinity.com/p/download-ambiance-radiance-themes-for.html)

---

### Post by aem0512 on 2012-09-20
Seems I was a bit hasty in thinking my problems were totally solved. Now certain applications and popup notifications are white with white text and I can't read them. Is there any way to fix this?

---


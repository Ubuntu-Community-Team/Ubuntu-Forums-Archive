---
title: "Changing launcher icon picture"
date: 2012-06-14
forum: New to Ubuntu
---

### Post by peterson43 on 2012-06-14
I use the program Ipe to create drawings for my LaTeX documents. The only annoying problem I'm having is that when I run Ipe, the icon in the launcher is just the generic gray question mark. There is a cute little penguin that should be the Ipe icon. 

I searched online and found that I can create my own launcher by making a *.desktop file. I think I could probably figure this out, but since I can start the program from the dash I figure there should already be a *.desktop file somewhere already and I would prefer to just modify that file with the correct path to the icon. It seems that most *.desktop files are stored in /usr/share/applications. However, Ipe doesn't seem to be here and I can't find anything named ipe.desktop by searchin in Nautilus. 

Is there any way to figure out where the *.desktop file is?

---

### Post by philinux on 2012-06-14
> **peterson43 said:**
> I use the program Ipe to create drawings for my LaTeX documents. The only annoying problem I'm having is that when I run Ipe, the icon in the launcher is just the generic gray question mark. There is a cute little penguin that should be the Ipe icon. 

I searched online and found that I can create my own launcher by making a *.desktop file. I think I could probably figure this out, but since I can start the program from the dash I figure there should already be a *.desktop file somewhere already and I would prefer to just modify that file with the correct path to the icon. It seems that most *.desktop files are stored in /usr/share/applications. However, Ipe doesn't seem to be here and I can't find anything named ipe.desktop by searchin in Nautilus. 

Is there any way to figure out where the *.desktop file is?

Have a try using locate ipe.desktop from a terminal.

---

### Post by peterson43 on 2012-06-14
> **philinux said:**
> Have a try using locate ipe.desktop from a terminal.

I tried that and it didn't find anything. I think that either there is no *.desktop file for Ipe or that it is named something less obvious than ipe.desktop.

---

### Post by philinux on 2012-06-14
> **peterson43 said:**
> I tried that and it didn't find anything. I think that either there is no *.desktop file for Ipe or that it is named something less obvious than ipe.desktop.

Install alacarte (aka main menu) then use it from Dash and create a new menu item for ipe. That will create a new .desktop file.

Start alacarte, fill in the blanks and select an icon.
Your .desktop will be stored in ~/.local/share/applications.

---

### Post by peterson43 on 2012-06-14
> **philinux said:**
> Install alacarte (aka main menu) then use it from Dash and create a new menu item for ipe. That will create a new .desktop file.

Start alacarte, fill in the blanks and select an icon.
Your .desktop will be stored in ~/.local/share/applications.

Ok, part of the problem was that I couldn't figure out where to find the Main Menu in 12.04. I had actually used the main menu in 11.04 to create a launcher for Ipe so it already showed up. I think that the path to the icon must have changed in the upgrade to 12.04 and so the icon didn't work anymore. However, when I clicked on "properties" to change the path for the icon, alacarte crashed. Now, whenever I use alacarte, none of the buttons work except the button that removes applications from the main menu (this is true for all applications, not just Ipe). 

I was able to correctly modify the ipe launcher using alacarte on another computer, but I still can't get alacarte to run properly on my main computer. I tried reinstalling alacarte and I tried restarting the computer but nothing seems to work. 

Any ideas on how to get alacarte working properly?

---

### Post by philinux on 2012-06-15
> **peterson43 said:**
> Ok, part of the problem was that I couldn't figure out where to find the Main Menu in 12.04. I had actually used the main menu in 11.04 to create a launcher for Ipe so it already showed up. I think that the path to the icon must have changed in the upgrade to 12.04 and so the icon didn't work anymore. However, when I clicked on "properties" to change the path for the icon, alacarte crashed. Now, whenever I use alacarte, none of the buttons work except the button that removes applications from the main menu (this is true for all applications, not just Ipe). 

I was able to correctly modify the ipe launcher using alacarte on another computer, but I still can't get alacarte to run properly on my main computer. I tried reinstalling alacarte and I tried restarting the computer but nothing seems to work. 

Any ideas on how to get alacarte working properly?

The only thing I can suggest is to reset unity to default from a terminal.

```
unity --reset
```

---

### Post by peterson43 on 2012-06-18
Okay, I finally got it fixed. I tried using the ```
unity --reset
``` code. That didn't seem to work since alacarte still wouldn't do anything when I tried to add a new item or modify the properties of a menu item. I then tried removing alacarte and reinstalling it again. I think I tried this before, but this time I restarted the computer before trying to use alacarte again. When I restarted it I was then able to use alacarte correctly. Everything is working fine now.

---


---
title: "[SOLVED] Replace Firefox icon."
date: 2008-09-03
forum: New to Ubuntu
---

### Post by ellalan on 2008-09-03
Hi
I have new icons downloaded for Firefox3 and unable to replace the old icons with this.
I have seen the solution in this forum but I forgot exactly where it is, if any of you could help please do so. TIA.

---

### Post by Vivaldi Gloria on 2008-09-03
If you mean the icon in the apps menu then edit menus by right clicking the ubuntu icon and choosing edit menus. Then find firefox and right click on it to choose properties. Now you can click on the big icon and change it.

Once you change the icon of ff in the menu, you can drag ff to desktop etc.

---

### Post by ellalan on 2008-09-03
Hi
I have installed the icon in usr/share/pixmaps and named it firefox-3.0.png, I have renamed the old icon firefox old-3.o.png.
When I click "choose icon" I could see the old icon but not new one. I have attached two screen shots. Thank you for the help.

---

### Post by Vivaldi Gloria on 2008-09-03
What happens when you choose the folder the firefox icons resides and then click open? I mean don't open the folder it's in just choose the folder.

---

### Post by ellalan on 2008-09-03
Hi
I have re-installed the old icon and I'll keep on trying. When I click the folder in which the icons are in nothing happens. 
One more thing is that I copied the .ico file to pixmaps folder and renamed it as a .png file. I am going to copy the .png file to pixmaps. 
I suspect that I am doing something wrong when I transfer the new icon to pixmaps. Annoying part is that I have done it once before and failed to make a note of it. Thanks for the help and please give me more ideas as to do what next.

---

### Post by philinux on 2008-09-03
No good renaming them they need converting.

[http://ph.ubuntuforums.com/showthread.php?t=755403](http://ph.ubuntuforums.com/showthread.php?t=755403)

[http://ubuntuforums.org/showthread.php?t=218431](http://ubuntuforums.org/showthread.php?t=218431)

Gimp or gthumb might do it.

---

### Post by Vivaldi Gloria on 2008-09-03
Wait, aren't the icons png (or xpm)? Please attach them so that I give it a try.

---

### Post by ellalan on 2008-09-03
Hi
I am enclosing the icons. They are .ico and .png files. I couldn't upload the .ico files, Sorry!

---

### Post by geezerone on 2008-09-03
I used the same ones (png) and make a small but refreshing change to the default '.fox' icon.

---

### Post by Vivaldi Gloria on 2008-09-03
It works for me. I put them in /usr/share/icons. 

Now see the second snapshot you attached above. 

1. Click choose icon.
2. Click browse and in the opened file browser find the folder where the ff icon is. Highlight the folder (do not double click to open - just highlight) and click the open button. 
3. Now you return to the window showing the icons. Isn't your ff icon there?

---

### Post by ellalan on 2008-09-03
Hi philinux
They have already been converted to .png from .ico, but when I place it in "pixmaps" I use the ,png files and rename the old icon to "firefoxold-3.0.png",the new icon to "firefox-3.png".
Then I right click the Ubuntu logo and "edit menus" and when I go to launcher properties I couldn't find the new icon file. Thanks for the help.

---

### Post by kerry_s on 2008-09-03
just drag & drop the icon you want to where it says "choose icon".

see your pic:

---

### Post by geezerone on 2008-09-03
For the Firefox icons look **[here]("http://www.gnome-look.org/content/show.php/Firefox+Icons?content=47617")**.

When I downloaded the icons I opened a terminal and typed the following after downloading to Desktop and extracting there:

```
sudo cp -r Desktop/Mozilla\ Firefox\ Icons/png/*.*  /usr/share/pixmaps/
```Then when you right-click on the Firefox shortcut and then click the icon to choose the new icons (four in above case) will be in the list to choose from.

---

### Post by ellalan on 2008-09-03
Thank you all for the help. I tried both kerry_s's method and vivaldi gloria's method and both worked well for me. In kerry_s's method I had to rename the default icon, then dragged the new icon from desktop to "choose icon". Thanks again to all.:)

EDIT
In kerry_s's method the icon disappears from Task Bar when I restart the PC. vivaldi gloria's method has no problems.

I have given this information for the people who might encounter similar problems in future, however my gratitude goes to all who helped me in resolving my problem.

---


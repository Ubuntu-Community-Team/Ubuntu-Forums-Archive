---
title: "[SOLVED] Set Specific Workspaces for Programs?"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by Lee05162004 on 2008-11-03
Hi, I just upgraded to 8.10 and I had a simple question. Basically as the title says I want to setup certain programs to open by default in specific workspaces. For example, have Firefox open in one workspace and Pidgin and Songbird open in another. I know how to move them once they are already opened to a specific workspace but is there a way I can set them to open by default in the said workspace? Thanks.

---

### Post by drs305 on 2008-11-03
If you use compiz you can use the compiz config settings manager (or in terminal: ccsm ). Windows management, Place Windows, Fixed Window Placement. Make the applicable entries in the Fixed Viewport section, starting with the New button.

---

### Post by Lee05162004 on 2008-11-03
> **drs305 said:**
> If you use compiz you can use the compiz config settings manager (or in terminal: ccsm ). Windows management, Place Windows, Fixed Window Placement. Make the applicable entries in the Fixed Viewport section, starting with the New button.

Thanks this is exactly what I was looking for.

---

### Post by nlz on 2009-01-02
uhm, I'm a bit confused by the X viewport positions. What value is respectively workspace 1,2,3,4? (If you have only one row?)

---

### Post by Nepherte on 2009-01-02
If you don't use compiz, take a look at devilspie.

---

### Post by nlz on 2009-01-03
hmmmm, have a problem with devilspie (see: [http://ubuntuforums.org/showthread.php?t=1029261](http://ubuntuforums.org/showthread.php?t=1029261) ) and still don't understand what the X and Y values are for compiz. tried about everything... So can someone explain what to do in the fixed window placement menu to place an app standard on a certain workspace?

---

### Post by drs305 on 2009-01-03
I select the lower section of Fixed Window Placement - Windows with Fixed Viewport. 

Select New, then the Add (+) symbol. 

Select a category - Window Class, Window Title, etc.

I find it easiest to already have the app I want to set up alread open so I can:

Hit 'Grab' and then click on the window you want to place. It will automatically fill in the proper info (Class, Title, etc). Hit Add again if you want to further specify the characteristics.

Set the X Viewport. I have 4 displayed in my workspace switcher, so I can set it to open in any one of the 4.

You can use the top part of the setup page (Windows with Fixed Positions) to place a window X pixels down and left from the top corner. For instance I only use one, to offset a window 75 down and 75 right.

---


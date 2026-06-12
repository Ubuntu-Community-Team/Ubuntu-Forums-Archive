---
title: "Number of Workspaces"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by fballem on 2008-05-10
I currently have two workspaces, which I assume is the default.

Is there a way to increase this number (say to 4) and have that persisted so that everytime I log in, I have 4 workspaces.

Would prefer a GUI based solution, but if I must use Terminal, then please be gentle (I am a newbie).

Thanks

---

### Post by hyper_ch on 2008-05-10
kde?

---

### Post by y-lee on 2008-05-10
In gnome, Right click your workspaces and choose properties. you can increase the number of workspaces there.

---

### Post by fballem on 2008-05-10
> **hyper_ch said:**
> kde?

gnome

Thanks

---

### Post by fballem on 2008-05-10
> **y-lee said:**
> In gnome, Right click your workspaces and choose properties. you can increase the number of workspaces there.

real newbie question - where are the workspaces so that I can right click? I'm embarrassed to ask, but I can't seem to find anything that looks like a workspace, except for the icon in the bottom right hand corner and that gives me columns and rows, but does not allow me to change the total number of workspaces.

Thanks

---

### Post by Riffer on 2008-05-10
that'll be the place.  Increase the number in the row section.

---

### Post by y-lee on 2008-05-10
> **Riffer said:**
> that'll be the place

Yep "the icon in the bottom right hand corner and that gives me columns and rows" :)

---

### Post by fballem on 2008-05-10
> **y-lee said:**
> Yep "the icon in the bottom right hand corner and that gives me columns and rows" :)

That gives me the number of columns and rows, but it all cycles between Desktop 1 and Desktop 2. What I would like to do is add Desktop 3 and Desktop 4.

Thanks

---

### Post by y-lee on 2008-05-10
You should be able to [right click this area and choose properties.]("http://www.techotopia.com/index.php/Customizing_the_Ubuntu_GNOME_Desktop_Panels#Changing_the_Number_of_Ubuntu_Desktop_Workspaces")

---

### Post by fballem on 2008-05-10
> **y-lee said:**
> You should be able to [right click this area and choose properties.]("http://www.techotopia.com/index.php/Customizing_the_Ubuntu_GNOME_Desktop_Panels#Changing_the_Number_of_Ubuntu_Desktop_Workspaces")

I read the section that you were kind enough to point out. I don't know if it makes a difference, but they refer to a Workspace Control and the item on my panel is a Workspace Switcher. The only options, when I right-click and select Preferences are Columns and Rows. There is no option to change the number of Workspaces.

Thanks

---

### Post by ugm6hr on 2008-05-10
Change columns to 4.

You'll then have 4 workspaces aligned horizontally on the taskbar.

---

### Post by fballem on 2008-05-10
Got it - many thanks!

---

### Post by fballem on 2008-05-11
> **ugm6hr said:**
> Change columns to 4.

You'll then have 4 workspaces aligned horizontally on the taskbar.

Thanks for this - I now have 4 workspaces in my taskbar. However, if I want four workspaces as 2 x 2, that doesn't seem to work. It appears that the total number of workspaces is controlled by the columns, but it should be controlled by columns times rows. Am I missing something?

---

### Post by ugm6hr on 2008-05-11
> **fballem said:**
> Thanks for this - I now have 4 workspaces in my taskbar. However, if I want four workspaces as 2 x 2, that doesn't seem to work. It appears that the total number of workspaces is controlled by the columns, but it should be controlled by columns times rows. Am I missing something?

Errmmm...  Don't know.

Mine gives me 2x2 if I want.

But the workspaces are tiny on the panel in 2 rows.

---

### Post by KIAaze on 2008-05-11
Change your preferences as in this picture:

[PS: This [Techotopia]("http://www.techotopia.com/index.php/Main_Page") site is really good. Thanks for the link. :) ]

---

### Post by fballem on 2008-05-11
> **KIAaze said:**
> Change your preferences as in this picture:

[PS: This [Techotopia]("http://www.techotopia.com/index.php/Main_Page") site is really good. Thanks for the link. :) ]

This looks like it might from a KDE screen. When I open the Workspace preferences, this is what I get:



If I change the number of columns, I get additional workspaces. If I change the number of rows, I get multiple copies of the same workspaces.

Thanks,

---

### Post by KIAaze on 2008-05-11
No, it's from Gnome. But I know why it's different: I don't use compiz by default.

But I just did a test with compiz activated and changing the number of rows and columns as in the attached pic gave me 4 workspaces arranged in 2 rows and 2 columns.
The screenshot is from the compiz settings manager which you can install with:
```
sudo apt-get install compizconfig-settings-manager
```
Or through synaptic or add:remove software of course.
It will then appear in "System->Preferences->Compizconfig settings manager".
Then go to "general options->Desktop size"

I just noticed there's another compiz settings manager:
```
sudo apt-get install simple-ccsm
```
Will try it out right away. :)

What exactly do you mean by "I get multiple copies of the same workspaces."?
If you open different windows in each, don't you get different windows in each workspace?
Or do you mean you get the same desktop background in each? The same desktop background is normal as far as I know.

Note: KDE allows having a different wallpaper for each workspace. ;)

edit:
Ok, tried it with "Desktop cube" and "Rotate cube" activated.
Indeed, it seems impossible to arrange the workspaces on several rows.
I guess you'll have to stay with 4 workspaces on one row or switch to "Desktop wall" (Desktop wall allows several rows and happens to be the default compiz setup).

---

### Post by UnknownFear on 2008-05-11
> **KIAaze said:**
> 
[PS: This [Techotopia]("http://www.techotopia.com/index.php/Main_Page") site is really good. Thanks for the link. :) ]

Yes. I too like the Techocotpia site. Thanks for the link

---


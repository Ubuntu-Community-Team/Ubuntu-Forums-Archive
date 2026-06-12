---
title: "Bottom panels change places at each system startup, any way to make them stay?"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by lehtv on 2008-08-29
Hi. I'm new to the forums (as well as to linux.)

I have two panels, each attached to the bottom of the screen. See attachment. Restarting the system makes the the panels switch places, i.e. the lower panel becomes the upper one. Is there any way to make them fix their positions? Does anyone have the same problem?

I've tried rearranging them using the panel properties so that the panel most recently put to the bottom would stay there, but that didn't help. Do you think this has something to do with the panel items? I.e. the panel with date and time would be loaded first in ubuntu, resulting the other panel's being attached to the bottom after it, hence the one with date and time being on top... or something similar?

Help appreciated.

---

### Post by markbuntu on 2008-08-29
When you get the panels set up the way you want, go to System/Preferences/Session and save the current setup.

---

### Post by gmxgeek on 2008-08-30
Try Locking them to the panel. Right-click -> Lock to Panel

---

### Post by lehtv on 2008-08-30
markbuntu, 

I went to Sessions preferences --> Sessions options, and there's two things I can do: tick a box named "Automatically remember running applications when logging out" and a press a button named "Remember currently running applications." Saving my session didn't help, and neither did enabling "automatically remember running applications". And it doesn't help at all either that the help documentation for Sessions preferences is outdated.

EDIT: I've managed to get the panels stay the right way, but only a few times. Most restarts make them swap their places, but some restarts get it right. I've done several restarts now, trying to see if changing the order and style of the program 'gnome-panel' in Current Session tab has any effect. It doesn't seem to have. For one, changes made to gnome-panel don't stay despite saving the changes and saving the session. Secondly, why some restarts get the panels the right way is unknown, there doesn't seem to be any pattern regarding the changes made in Sessons Preferences. I think it's just a matter of which panel HAPPENS to get oriented to bottom first and which second upon Gnome startup. Now if there was for each panel a separate program in the Current Session tab of Sessions preferences, one could set their startup order and see if it made a difference to their relative position, only if the changes made in Current Sessions stayed between system startups. Sigh.

EDIT 2: I restarted again, this time having set the upper panel not to stretch itself. Seems to have worked. I'm done restarting for now though, I'll have to do more testing later.

gmxgeek, 

I wasn't talking about items in the panels but the panels themselves. Do you know of a way to lock the panels themselves to where they are?

---

### Post by gmxgeek on 2008-08-30
Not off the top of my head. Look for a 'allow panel to be moved' option somewhere. I think i remember there being one somewhere

---

### Post by malspa on 2008-08-30
Had a sort of similar problem here.  In my case, using a top panel and a bottom panel, with each in unexpanded mode.  With each new session, the panels would switch places unless I expanded them both before logging out.

Here's what worked for me.  My screen resolution is 1024x768.

In gconf-editor:

In apps > panel > toplevels > bottom_panel_screen0, I changed the **y** key to 760.

In apps > panel > toplevels > top_panel_screen0, I changed the **y_bottom** key to 760.

Now when I start a new session, the panels are still in place, even if I have left them unexpanded.  I don't really know why this worked, though.

---

### Post by lehtv on 2008-08-31
malspa,

I doubt that any changes to y and y_bottom would have any effect on my setup, since both have meaning only if the panel edited is in unexpanded mode. At least that's what it says in their description.

Unfortunately I didn't find any setting in the configuration editor that would set the relative position of panels. It says in the y and y_bottom descriptions that if in expanded mode, the value in 'orientation' is used instead. In my case, both panels are set to 'bottom' for 'orientation', obviously...

I got the panels to load correctly. Once. 
First I deleted both my original panels, then created them again. First restart, they positioned the wrong way. Then I moved all items from one panel to another and vice versa to see if the panel position depends on the panel itself or on the items in the panel. After restarting they loaded the wrong way again, as in just the opposite way than the last time (according to the panels themselves). I tested this three times, always the same. After that I swapped all items between the panels again, and this time they loaded the right way after restarting. WHY!? I restarted again, but then they loaded the wrong way again. Sigh. There really doesn't seem to be any pattern here, it's all random. They're both set to bottom, not like bottom 1 and bottom 2 or something. I think this aspect needs some developing.

---

### Post by malspa on 2008-08-31
> **lehtv said:**
> I doubt that any changes to y and y_bottom would have any effect on my setup, since both have meaning only if the panel edited is in unexpanded mode. At least that's what it says in their description.

Yeah, you're right, sorry.  Odd, though, that other than the fact yours are expanded and mine are not, similar behavior upon starting a new session... The GNOME panels in Ubuntu just seem buggy if you try to make changes to their positions.  I wondered if playing around with some of the keys in gconf-editor might make things stick for you.

---

### Post by billykendall on 2009-10-05
Has anyone ever found a solution to this problem because I am new to Ubuntu and I am experiencing this very same problem when running two gnome panels at the top of the screen.  

Thanks for any help! :)

-BK

---

### Post by louieb on 2009-10-06
Irritating isn't it. Found the fix here. [http://ubuntuforums.org/showthread.php?t=1170959](http://ubuntuforums.org/showthread.php?t=1170959)

---


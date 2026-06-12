---
title: "Scrollbar resizing"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by ForgivenByJC on 2008-05-15
As of yet, I have not been able to locate any information on how to resize my scrollbar sizes.  Besides changing screen resolution, how do you change the default scrollbar size in Ubuntu 8.04 LTS (does LTS imply desktop?)?  Too, as I am not new to solving computer problems, I would also be interested in how best to search for this information so as not to bother people with something which is most probably already answered somewhere.  Thank you for all of your help in advance. 
PS Ubuntu is really awesome! [http://ubuntuforums.org/images/smilies/icon_razz.gif](http://ubuntuforums.org/images/smilies/icon_razz.gif)
-John

---

### Post by Thanoulis on 2008-05-15
You can search the forums, or [here]("http://www.ubuntux.org/ubuntu-search/").
As for your scrollbar question, i'm sorry, but not a clue..:(

---

### Post by ForgivenByJC on 2008-05-15
Hey, thanks for replying.  Don't worry about not knowing.  If this was an easy answer, I would like to think I would have found it already in the number of searches I have done.  I do like the [http://www.ubuntux.org/ubuntu-search/](http://www.ubuntux.org/ubuntu-search/) link.  Thank you.  I am certain the configuration files have the settings some where that will have to be accessed by sudo gedit /.configblah or something like that.  -J :)

---

### Post by ForgivenByJC on 2009-05-09
Go to System -> Preferences -> Appearance
In the "Theme" tab, note which theme is used.  If "Custom" is specified, click the "C_u_stomize..." button and note the name of the selection in the "Controls" tab.  e.g. "Clearlooks"
Edit the file /usr/share/themes/<noted Theme/Controls>/gtk-2.0/gtkrc
e.g. /usr/share/themes/Clearlooks/gtk-2.0/gtkrc
Change 
```
GtkRange::slider-width = 15
```
to desired number.  Subsequently,
```
GtkRange::stepper-size = 15
```
looks best when its the same number as slider-width, but is personal preference.  stepper-size are the buttons on either end of the scrollbar/slider.


I apologize for not posting this earlier because if you are like me and don't like searching in vain for information, then this previously unresolved post was likely frustrating to you.

---

### Post by vangelas on 2011-09-04
Two years later....Many thanks, I've been looking for this for a while!

---


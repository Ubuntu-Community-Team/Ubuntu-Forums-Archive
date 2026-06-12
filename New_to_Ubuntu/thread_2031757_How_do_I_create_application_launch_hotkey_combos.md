---
title: "How do I create application launch hotkey combos?"
date: 2012-07-22
forum: New to Ubuntu
---

### Post by degarb on 2012-07-22
I am using gnome-classic and lxde.

Is there a simple, yes simple, way yet (it is 2012) to create hotkey combinations to launch applications?  Ex. ctrl alt n should launch gedit or leafpad, etc. per user prefs.

This field/option should be under the short cut preferences.  But I will take a gui, or simple file that can be edited and humanly understandable.

---

### Post by NikTh on 2012-07-22
> **degarb said:**
> I am using gnome-classic and lxde.

Is there a simple, yes simple, way yet (it is 2012)  
Hi , degrab 
for this i think you should contact with developers. File a bug or something or register to a list.
> **degarb said:**
> to create hotkey combinations to launch applications?  Ex. ctrl alt n should launch gedit or leafpad, etc. per user prefs. 


**For Lubuntu **, i don't know a simple Gui way. Maybe you want to wait for someone who knows. 
I know the manual modifying way of **lubuntu-rc.xml  **, file. It is not easy as Gui , but i think its human understandable (if you read the file little you can understand what you must add and how to add).
If you want to follow this way , open lxterminal and 
```
leafpad .config/openbox/lubuntu-rc.xml
``` 
when you modifying the file and save it , run in terminal this 
```
 openbox --restart
``` so the changes take place. 

**For gnome-classic **i think that if you go system > keyboard  , you will be able to add your shortcuts. (i am not sure ,if i remember correct) It is easier , and its Gui way. 

Thanks

---

### Post by degarb on 2012-07-22
Interesting.  The xml is hard to read and I think it needs to be saved somewhere else.  I will play with it later.  Probably never figure out who in lxde to contact.

While waiting, I found:

install keylaunch, make file ~/.keylaunchrc, then preference launcher gedit /home/user/.keylaunchrc    The key= format is whacko and makes no sense, but better than nothing.  

The format of the file in keylaunch doesn't make sense to me, as below:
# Format:
# key=...KeyName:Command
#
# ... No modifier
# *.. Shift
# .*. Ctrl
# ..* Alt

#key=.*...*n:leafpad          This doesn't work as expected! Ctrl alt n
key=.**n:leafpad
key=.**o:opera
key=.**x:xkill
key=..*Return:xterm

#Why is .** ctrl alt, unless alt is simply * and there is a typo in the directions.

---


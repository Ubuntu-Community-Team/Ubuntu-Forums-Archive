---
title: "Updating menus and Applications for all users"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by mbeach on 2008-04-26
I've always only really used Ubuntu in a single user type environment - ie, the machine is only used by me, I can change my menus etc, and have things just the way I like, with some applications specific to our business installed and running correctly. 

I'm in a position now however, that I have a machine which 3-5 users will be sharing (different shifts - they'll be physically at the PC).  I want each to have their own username, but I want to be able to give them all the same copy of a desktop (to start with) and access to the applications which I'll install under some common directory.  I can set the permissions accordingly on the files/folders for execution, but would really like for each to have their own config area etc...

I guess what I'm asking is how do I create a default 'desktop' for new users which has all the apps, desktop theme (with corporate logo etc) and common menus but retain the ability for separate logins?  I'll also want to upgrade applications occasionally, and really don't want to have to install the same app a number of times (I'm using wine for some older legacy window apps).

I'm not looking for a step by step, but some general guidance on where to start.  I've done some preliminary searching but the results haven't been too fruitful.

Thanks,
mb

---

### Post by beattyml1 on 2009-01-05
I am not sure as I have not actually tried it but from what I can tell 
a lot of what you're looking for is found in the user's ~/.config/ folder, this is where the menus are found
the following are what I believe are the needed files to transfer a user's menus
```
~/.config/menus/applications.menu
~/.config/menus/settings.menu
```
and possibly ```
~/.config/menus/applications-merged
```  (this has something to do with wine)

also of use maybe:
```
~/.config/user-dirs.dirs
~/.config/monitors.xml
~/.config/
~/.fontconfig
~/.evolution
~/.gconf
~/.gconfd
~/.gnome
~/.gnome2
~/.gnome2_private
~/.icons
~/.metacity
~/.nautilus
~/.mozilla
~/.profile
```

---


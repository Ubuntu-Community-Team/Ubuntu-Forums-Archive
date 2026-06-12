---
title: "Log out dialog"
date: 2006-11-06
forum: Programming Talk
---

### Post by SeanHodges on 2006-11-06
I would like to make some modifications to the log out dialog in Ubuntu (Gnome). Could anyone tell me where I might find the source code for this? Or, even better, how I can find out where the source code for such things are in Ubuntu? I've googled and googled, looked around Launchpad, and prayed to my favourite god, and I've come to the decision that this probably isn't a stupid question.

Usually I look on the website of the product, but the log out dialog has no name...

---

### Post by duff on 2006-11-06
I'll try and help you on this one...this may not be perfect, but here goes.

When trying to track down a program I always go for a string that is prabobly unique to the application.  Strings usually are embded in the executable or in the glade file.  So bring up the logout dialog and pick a string..I pick 'Switch User'.
```
# cd /usr/bin
# grep 'Switch User' *
```
The only match I get is gnome-panel.  If you get mutiple matches, you can either grep for more strings or run
```
# strings /usr/bin/gnome-panel | less
```, look at what's there and maybe conclude that's the right one.  For example, in the above I see ```
_Switch User
_Log Out
Shut down this system now?
S_uspend
_Hibernate
_Restart
_Shut Down
``` So that's probably right.

Now, get the source code.
```
# apt-get source gnome-panel
```

Again, grep for 'Switch User' to find the C file.
```
# find gnome-panel-2.16.1/ -name '*.c' -exec grep -Hn 'Switch User' {} \;


gnome-panel-2.16.1/gnome-panel/panel-logout.c:321:                                    _("_Switch User"),

```
So, panel-logout.c is where you'll most likely make your changes.

After youre done and ready to build a package, edit **debian/changelog** and add a new entry.  The syntax is very perticular (down to the number of spaces) so check with the other entries to make sure you got it right.  And don't forget to bump the version number, otherwise Ubunutu's UpdateManager will try to replace your modifications with the official one.  So instead of **2.16.1-0ubuntu3** try **2.16.1-0ubuntu3sean1**  that way you'll still be notified by UpdateManager if there's an upstream bug fix.

Now make a new .deb: ```
dpkg-buildpackage -rfakeroot
```.  You may get errors about missing build deps (dpkg-checkbuilddeps: Unmet build dependencies), just install what it tells you and try again.  If all goes well you'll have a new gnome-panel deb you can install with 'dpkg'.  

Hope this helps...Good luck!

---

### Post by SeanHodges on 2007-02-21
Just found this thread in my subscriptions and noticed I hadn't replied, sorry. This was really helpful, I managed to make the changes no problem.

Thanks

---


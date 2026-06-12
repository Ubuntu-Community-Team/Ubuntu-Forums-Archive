---
title: "Half of my Ubuntu GUI is gone?"
date: 2011-11-14
forum: New to Ubuntu
---

### Post by privwe0 on 2011-11-14
So my laptop crashed (and screen went all pixel-lated). I turned it off by holding in the power button, booted it up again, and this is what i get. Three times in a row.

[http://i.imgur.com/HCUuS.jpg](http://i.imgur.com/HCUuS.jpg)

How do i fix this? :o

---

### Post by critin on 2011-11-14
I like the desktop image, it's nice.  Which version do you have--11.10?  Don't you have a Recovery mode to click into?
Did you try hitting the super(windows) key?
Search the forums for similar issues, they're out there.

---

### Post by privwe0 on 2011-11-14
No luck. The windows key does nothing.  I opened terminal and tried a few options on unity, no luck either. If I log in using Ubuntu2D, then it works fine.  Really really strange.  Anyone else have any ideas? Open to suggestions.

---

### Post by Rubykuby on 2011-11-14
CTRL+ALT+T -> opens terminal

Enter: unity --reset

Then see magic happen. Fixes it for me when that happens.

---

### Post by -kg- on 2011-11-14
That is a(n unfortunately) common occurrence lately.

You'll need to reboot and, once you come to the login screen, there will be a little icon next to the password box.  Click on that and select "Ubuntu 2D" from the menu.  When you log in, you will be in Ubuntu 2D and your desktop will be normally displayed.

Frankly, I'm fine with 2D and have just left it there.  But if you want to recover 3D, there is a way.  Have you installed and used ccsm (Compiz/Config Settings Manager)?  That is the most common cause for your problem (I experienced it myself).

There is a setting that is not set by default (it should be, for the Unity Desktop), and you need to enable it.  When you launch it, under the Desktop category you will see a checkbox for "Ubuntu Unity Plugin."  If it is unchecked (and it probably will be), you need to check it.  Then close it, reboot, and select Ubuntu at login.  You should log back into a now-correctly displaying desktop.

I repaired mine, and it works, but I stuck with 2D.  2D fulfills all my requirements and looks fine for me.

<Edit> - That is, if the above doesn't correct it.  I tried it and it didn't work, but my problem was caused by ccsm itself.  My method was the only way I could correct it.

---

### Post by privwe0 on 2011-11-14
> **-kg- said:**
> That is a(n unfortunately) common occurrence lately.

You'll need to reboot and, once you come to the login screen, there will be a little icon next to the password box.  Click on that and select "Ubuntu 2D" from the menu.  When you log in, you will be in Ubuntu 2D and your desktop will be normally displayed.

Frankly, I'm fine with 2D and have just left it there.  But if you want to recover 3D, there is a way.  Have you installed and used ccsm (Compiz/Config Settings Manager)?  That is the most common cause for your problem (I experienced it myself).

There is a setting that is not set by default (it should be, for the Unity Desktop), and you need to enable it.  When you launch it, under the Desktop category you will see a checkbox for "Ubuntu Unity Plugin."  If it is unchecked (and it probably will be), you need to check it.  Then close it, reboot, and select Ubuntu at login.  You should log back into a now-correctly displaying desktop.

I repaired mine, and it works, but I stuck with 2D.  2D fulfills all my requirements and looks fine for me.

<Edit> - That is, if the above doesn't correct it.  I tried it and it didn't work, but my problem was caused by ccsm itself.  My method was the only way I could correct it.

It may have been CCSM. How would i be able to access it if i have no shortcuts etc?  Or will it be better if i just uninstall it?

---

### Post by critin on 2011-11-14
I use 2D also and I've not had any issues. (knock on wood)  From what I've read, the main difference from 3D is the ability to use 'extra effects' like cube and such.  I wouldn't use those anyway.

---


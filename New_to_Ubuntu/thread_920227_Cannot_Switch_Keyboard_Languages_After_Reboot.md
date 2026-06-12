---
title: "Cannot Switch Keyboard Languages After Reboot"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by lorenbr on 2008-09-15
I have configured my language and keyboard settings to allow me to switch between Thai and English, in my case using the left windows key.  And it works.  However, after I restart the computer, I can no longer switch using the left windows key, and when I manually switch the language by clicking on the language icon (3 letters in the GNOME (I think?) bar), the output language still does not change to Thai.

This issue was previously reported on Launchpad as bug number #35663 (link: [https://answers.launchpad.net/ubuntu/+question/35663](https://answers.launchpad.net/ubuntu/+question/35663)), and a workaround was offered, but I am not clear on how to implement it.  Quoting from user ouychai:

'I'm fix a bug already. I changed the xorg.conf by
"
Section "InputDevice"
    Identifier "Generic Keyboard"
    Driver "kbd"
    Option "XkbRules" "xorg"
    Option "XkbModel" "pc105"
    Option "XkbLayout" "us,th"
    Option "XkbOptions" "grp:alt_shift_toggle"
EndSection

"
I think is not userfriendly for a new user if they will fix a bug with xorg.conf'

If anyone could take a second to explain this to me, it would be much appreciated.  I figure its got to be done on the terminal, but I'm not sure the commands involved.

Thanks

---

### Post by unutbu on 2008-09-15
Hello lorenbr, welcome to ubuntuforums.
Thankfully, since you've tracked down the solution, implementing it is easy :
```

gksu gedit /etc/X11/xorg.conf

```
Scroll through the file and look for a Section that says 'Driver  "kbd"' and that looks somewhat like 
```

Section "InputDevice"
    Identifier "Generic Keyboard"
    Driver "kbd"
    Option "XkbRules" "xorg"
    Option "XkbModel" "pc105"
    Option "XkbLayout" "us,th"
    Option "XkbOptions" "grp:alt_shift_toggle"
EndSection
```

Lines that begin with # are comments and are ignored by the X server.
Thus, the Section that you should edit should not have # signs in front of the lines.
Change that Section so it looks like the one above.


Save and exit gedit.
Log out, and log back in.

---

### Post by lorenbr on 2008-09-17
One passage here sticks out to me

>     Option "XkbOptions" "grp:alt_shift_toggle"


Is there a way that I can change this to use the "`" accent key in the upper left hand corner of the keyboard instead.  And failing that, at least let me maintain the binding of the left windows key to toggle languages, rather than using the alt_shift to toggle?

---

### Post by lorenbr on 2008-09-17
Ok, so I answered my own question about setting the left windows key to do the toggling.  Instead of the last line that you included, I put in the line 

Option "XkbOptions" "grp:lwin_toggle"

Now it seems to me that if there is a name for the specific grave accent key, I should be able to have that key put into the command as "*x*_toggle" but I'm not sure if such a name exists, or where to find it.

---

### Post by lorenbr on 2008-09-17
Alright, I appear to have broken something.

I input all the changes that were suggested, but then instead of leaving the current toggle setting, I put "grave_toggle."  After restarting the computer, the only way to toggle the language is by manually clicking on the indicator on the GNOME bar (I think that's what the bar at the top of the screen is called).  Now, this previously didn't work until I had made a change on the keyboard layout screen (which jump started the thing somehow), so this is progress.  But neither the left windows key nor the grave accent key change the language.

Moreover, now, when I try to run the command gksu gedit /etc/X11/xorg.conf, the machine thinks about it for a little bit, opens up an "Administration" box at the bottom of the screen, then does nothing.  I also cannot run a simple "gksu gedit," which, perhaps, is not a command that can be run at all.  I'm not sure.  But gksu does open up a run window for "root," as the man says it is supposed to.

Any thoughts?

---

### Post by lorenbr on 2008-09-17
The issue was a typo.  Wrote gpedit instead of gedit.  I'm sorry to have bothered you all.

---


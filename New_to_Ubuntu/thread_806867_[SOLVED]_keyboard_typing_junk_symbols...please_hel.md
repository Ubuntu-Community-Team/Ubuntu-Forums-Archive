---
title: "[SOLVED] keyboard typing junk symbols...please help"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by wordmaster on 2008-05-25
I went into settings and changed the login screen to blue circles with face and enabled automatic login.

As far as I know, I did nothing to change the keyboard. Now when I try to type something in, it types stuff that looks more like ASCII symbols or something than actual letters for instance the "a" key types in the "ae" symbol where the a and e are connected as a single letter. Typing (as I remember) the "5" key gives a "1/2" as a single symbol.

I dont' know what I did, but it was obviously wrong! I checked the keyboard setup and it is still set for standard 105 key and US english.

Any help would be greatly appreciated.

---

### Post by Joeb454 on 2008-05-25
Are you on a laptop? If so check that you have numlock disabled.

---

### Post by wordmaster on 2008-05-25
No, I am using a desktop. Until I did something (whatever it might have been) everything has been working fine in my triple boot system, Ubuntu, 200 pro and 98SE. I am now in 98SE typing this.

BTW, the numlock is on in the bios, but it has been on all along. I have not changed anything there. The number 5 typing the 1/2 was using the 5 at the top of the keyboard, not on the number pad.

---

### Post by lswest on 2008-05-25
i use a german keyboard and i can type the 1/2 by hitting alt gr (right alt button) and 5, as well as the other symbols.  Make sure that key is not stuck and the keyboard layout correct (system-->preferences-->keyboad and then under the layout tab).

---

### Post by wordmaster on 2008-05-25
Yep, all is OK under the Ubuntu keyboard settings and I am typing on that same keyboard now under 98SE so it is not a stuck key or hardware problem. Just something gone crazy in Ubuntu.

---

### Post by lswest on 2008-05-25
does this happen in all windows, or just one or two programs?  And also, the same problem would not occur with 98SE, since it uses a different format for inserting characters than Ubuntu (left alt + ascii code on numpad), so it might not be noticeable.  Try plugging the keyboard into a different USB port (if it's USB), other than that, i'm not sure.  Check if it persists on a liveCD, if so, it may be a hardware/driver problem.

---

### Post by wordmaster on 2008-05-25
In Ubuntu, I tried typing in firefox, terminal, and text editor all with the same results. Also, when I try to type in my password, it is not accepted so apparently it is typing nonsense there too.

I am now typing in windoze 2000 pro and no problems whatsoever, just as in 98SE.

---

### Post by lswest on 2008-05-25
then it definitely has to be a setting in Ubuntu, try reverting to the default keyboard layout, and then rebooting.

---

### Post by wordmaster on 2008-05-25
Hmmmmm, I changed to default keyboard and now I am typing normally...without rebooting. Default is UK and I have had it set for US for some time and it has been working until today. Any ideas on what I need to do to get it back to US and not have a problem?

---

### Post by Joeb454 on 2008-05-25
Try changing it again to see if you get the same issue?

---

### Post by wordmaster on 2008-05-25
Hmmmmmm again. I changed it back to USA and it is still working. I guess this is solved unless someone might know what I did to cause the problem so I can avoid it in the future. Thank you all for your help.

---

### Post by wordmaster on 2008-05-25
Hmmmm again. I changed it back to USA and still typing fine. I guess this is solved unless someone knows what I did wrong so I can avoid it in the future. Thank all of you for your help.

---

### Post by lswest on 2008-05-25
I don't know, maybe an update caused some config file to be messed up, or maybe changing the setup for your gdm caused it to somehow "forget" your configuration, or to corrupt it.  Not sure.  In any case, it shouldn't happen again (at least, for a long while) and if it does, chances are you can fix it.  (occasionally my layout gets changed to US for whatever reason, and i have to delete the US layout and set up the german one again, so that it works).  Thanks for the thanks, and sorry i can't shed light on the "why".  Maybe you made a setting change for your xorg (which would edit your xorg.conf, which is where the keyboard layout is saved) and that may have had something to do with it.

---

### Post by Joeb454 on 2008-05-25
it does sound like some sort of config file that got messed up. At least you know a workaround if it happens again :)

---

### Post by bodhi.zazen on 2008-05-25
You can also try :

```
sudo dpkg-reconfigure -plow console-setup
```

This sets up the keyboard on the console.

Gnome *should* set up the keyboard from the menu as previously mentioned.

---

### Post by andyux on 2011-11-22
Thank you. Same was happening, keyboard was Romanania...?!:KS

---


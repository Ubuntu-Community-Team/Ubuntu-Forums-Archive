---
title: "My HUD is invisible"
date: 2012-07-03
forum: New to Ubuntu
---

### Post by Dahmaster95 on 2012-07-03
I am an absolute newbie to linux. Until recently I was using windows 7. I just recently installed Ubuntu 12.04 on my old desktop and everything works fine except for the HUD. Whenever I click the Dash Home button on the sidebar the Dash doesn't become visible. It's as if its completely transparent. When i hover over where the search bar is supposed to be, It changes into a cursor but I can't see what I'm typing, though I know I am typing something. I tried typing in google-chrome and pressed enter and chrome opened. I know it is functioning, it's just completely invisible. Please Help me. 
Thanks

---

### Post by stinkeye on 2012-07-03
This is for the **Ubuntu** session.
Check what session your in by copying and pasting this in the terminal and press **Enter**...
```
echo $DESKTOP_SESSION
```
If it says **Ubuntu 2d** don't run the following.

Open a terminal and run (copy and paste the command)...
```
unity --reset & disown
```

If that doesn't work install **compizconfig-settings-manager** 
Search and install through the software centre.

Hit alt+F2 and type in **ccsm** and hit Enter.

In ccsm navigate to *Desktop > Ubuntu Unity plugin > Experimental*
and try a different dash blur effect.

---

### Post by Dahmaster95 on 2012-07-03
Nope, the $DESKTOP_SESSION command didn't work, and neither did ccsm.

---

### Post by vasa1 on 2012-07-03
Very minor point but your title should be "My Dash screen is invisible" or something like that.

---

### Post by stinkeye on 2012-07-04
> **Dahmaster95 said:**
> Nope, the $DESKTOP_SESSION command didn't work, and neither did ccsm.

Did you use the full command including **echo** (copy and paste in terminal then press the Enter key)
```
[COLOR="red"]echo $DESKTOP_SESSION[/COLOR]
```

eg my output
```
[COLOR="Olive"]glen@Precise:~$[/COLOR] [COLOR="Red"]echo $DESKTOP_SESSION[/COLOR]
**ubuntu**
```

---

### Post by Dahmaster95 on 2012-07-04
I though echo was the computer name...lol now my output is ubuntu.

...$ echo $DESKTOP_SESSION
ubuntu

after I did unity --reset & disown

my terminal was just this repeated over and over 

r300: CS space validation failed. (not enough memory?) skipping rendering

---

### Post by sandyd on 2012-07-04
> **Dahmaster95 said:**
> I though echo was the computer name...lol now my output is ubuntu.

...$ echo $DESKTOP_SESSION
ubuntu

after I did unity --reset & disown

my terminal was just this repeated over and over 

r300: CS space validation failed. (not enough memory?) skipping rendering
Its a bug that seems to have affected some installs.
No fix seen so far.

I have not experienced it, so I cannot help you, but you can report a bug against the "xf86-video-ati" package using the instructions at [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by Dahmaster95 on 2012-07-04
Should I reinstall from a new cd?

---

### Post by sandyd on 2012-07-04
> **Dahmaster95 said:**
> Should I reinstall from a new cd?
Does it have the same problem on a new install? (When you started using Ubuntu). IF not, reinstall.

If yes, there is no fix, and the only thing you can do is report the bug. Reinstalling will not make any difference in that case.

---

### Post by Dahmaster95 on 2012-07-04
Well I reinstalled from a usb this time instead of a CD and I get the same problem....I'll jsut report then. I wonder if its specific to my model computer...

---


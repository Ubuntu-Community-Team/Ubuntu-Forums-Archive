---
title: "8-9 tabs of screen"
date: 2010-10-27
forum: Programming Talk
---

### Post by jamesbon on 2010-10-27
Hi,
once upon a time one of my friend showed me in his server he used to login via ssh and 
then type screen on that screen session used to open he showed me 9 tabs within same terminal in screen session.
If any one is understanding what I am asking can you tell me how can this be done?
If I remember correctly he modified .screenrc and  wrote some thing in it which made this possible and he used to press
Alt+1 ,Alt+2 .......Alt+n to switch in different terminals.

---

### Post by matthew.ball on 2010-10-27
Yeah, basically he added [FONT="Courier New"]hardstatus alwayslastline[/FONT] to his .screenrc and modified the hardstatus string (I don't have my status string always showing, but when I press F8/F9 it shows/closes the status bar - mine looks like this: [FONT="Courier New"]hardstatus string "%-w%{= BW}%50>%n %t%{-}%+w%< "[/FONT].

You might want to consider reading through [FONT="Courier New"]man screen[/FONT] - it basically shows you all you need to know.

---

### Post by jamesbon on 2010-10-27
I read man page of screen but could not understand much.

---

### Post by sparker256 on 2010-10-27
> **jamesbon said:**
> I read man page of screen but could not understand much.

I hope this is what you are looking for.

Under "File" select the "Open Tab" and click on "Default"

Bill

---


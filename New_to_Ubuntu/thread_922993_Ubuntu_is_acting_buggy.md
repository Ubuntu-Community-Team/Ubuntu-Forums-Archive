---
title: "Ubuntu is acting buggy"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by Vendettaseve on 2008-09-17
So, Ubuntu is deffinitly acting strange. When I open Pidgin it opens an extra tab on my taskbar that says Pidgin and has an empty box in the left corner. Pidgin no longer minimizes to the hotbar when you close it, it just shuts down. Also it has an odd little square in the top left of the screen.

Hard to describe.


Also Firefox is acting up, sound and video stops working after its been open for a while and it starts to refuse to close  when I click on the X in the corner etc. :(

ANyone know what this stuff is happening?

---

### Post by Vadi on 2008-09-17
Nope, but to help us diagnose, please do this - go to applications - accessories - terminal, type "pidgin", and press enter. When pidgin shuts down, select the text it gave, right-click, copy, and paste here.

That'll help us understand what's going wrong.

---

### Post by cprofitt on 2008-09-17
Yes... running applications from the terminal is a fantastic way to get more information. Please post the results.

---

### Post by Tatty on 2008-09-17
The firefox issue *could* be a problem with flash conflicting with pulseaudio.

Install this to fix the flash/pulseaudio sound issue:

```
sudo apt-get install libflashsupport
```

---

### Post by nowshining on 2008-09-17
more than likely that TOP sqare is the minimized pidgin - expand it - do u see the piding icon?? try right-clicking that icon and selecting close and try opening and closing pidgin again...

---

### Post by Vendettaseve on 2008-09-17
Opened the terminal and typed pidgin, nothing happend.

---

### Post by Vendettaseve on 2008-09-17
> **nowshining said:**
> more than likely that TOP sqare is the minimized pidgin - expand it - do u see the piding icon?? try right-clicking that icon and selecting close and try opening and closing pidgin again...


Also, yes it has the Pidgin textbox and circle logo thing, but the trick is, Pidgin isnt minimized, its open and running on my desktop.

---

### Post by nowshining on 2008-09-17
the problem is that it isn't minimizing to the tray directly but it is minimizing just fine, do u have all updates?? have you ran an update recently??

---

### Post by Vendettaseve on 2008-09-17
I just found out what that square in the top left corner it. Its the icon thats supposed to be in the tray. WHen I installed libflashsupport it opened another little window with an icon in it as well, instead of putting said Icon in the tray. Any ideas?

---

### Post by Tatty on 2008-09-17
> **Vendettaseve said:**
> I just found out what that square in the top left corner it. Its the icon thats supposed to be in the tray. WHen I installed libflashsupport it opened another little window with an icon in it as well, instead of putting said Icon in the tray. Any ideas?

Do you mean after you installed libflashsupport then pidgin started opening another little window, or do you mean a window appeared as you installed libflashsupport?

The latter would be worrying because libflashsupport shouldn't make any gui elements appear.

---

### Post by nowshining on 2008-09-17
yes now you get get Vendettaseve - that's what I was trying to convey in the first place :) usually a logout and back-in should correct it, but do you have all updates??

---

### Post by Vendettaseve on 2008-09-17
yes I have all the updates I think. At least it isnt telling me I need anymore.

I have restarted my computer several times trying to fix this nowshining, it doesnt work.

When I isntalled libflashsupport it opened the small tray icon showing the whole new item installed exclamation mark thing. but instead of putting it in my tray it opened it in another small window.

Also I should mention Pidgin opens no tray icons at all and no small new window when I open it in my second screen. Only when on the first it does this.

Accualy now that I mention it, the only trey icon that is open is sound control. THere are none of the other usual ones there, and when I boot up it opens a little window that says "network control" or something like that -.-  I think theres something wrong with my trey.

---

### Post by Vendettaseve on 2008-09-17
Problem solved. Sort of



It seems to be a bug when using 2 monitors on the Nvidi xserver thing.
I disabled my second monitor and restarted again and all is working, the little boxes have gone back into my system trey etc. :D

Things such as menus and the restart button are working much more smooth than before as well

---


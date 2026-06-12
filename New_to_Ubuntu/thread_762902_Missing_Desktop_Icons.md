---
title: "Missing Desktop Icons"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by Andy17MB on 2008-04-22
Can anyone tell me how I have managed to make the icons on the desktop disappear?  I can still open Desktop in Nautilus and everything is still there and still works. However on the main desktop there are no Icons.  A full reboot has not fixed the problem.  I am using Gutsy and have patched up to date. 

Thanks

Andy

---

### Post by Joeb454 on 2008-04-22
Are you on the correct workspace? That could be it (check the bottom panel - far right) :)

If you are, have you tried logging out and back in? Or do you have conky running? :)

---

### Post by Andy17MB on 2008-04-23
Thanks for the quick reply..

I've definitely not got icons in either of the two workspaces.  

I have also logged out and rebooted (twice..) to no avail.

Everything else seems to run ok and all of the desktop items work when you access them in Nautilus.

BTW What's Conky running?

---

### Post by ace007 on 2008-04-23
you can choose to hide the icons in the gconf-editor.  I dont know if thats what you've done by mistake, but you can at least take a look.  Launch the configuration editor in gnome and scroll down to desktop and i think its under nautilus or gnome or something.  I'm not by an ubuntu box so I cant tell you for sure.

```

gconf-editor

```

---

### Post by motang on 2008-04-23
> **Andy17MB said:**
> Can anyone tell me how I have managed to make the icons on the desktop disappear?  I can still open Desktop in Nautilus and everything is still there and still works. However on the main desktop there are no Icons.  A full reboot has not fixed the problem.  I am using Gutsy and have patched up to date. 

Thanks

Andy
Well did you install something like [UbuntuTweak]("http://ubuntu-tweak.com/"), because in UbuntuTweak there is a option under Desktop to hide the desktop icons.

---

### Post by avtolle on 2008-04-23
How about trying under System-->Preferences-->Appearance; open the Interface tab, and see if the Icon box is checked. Just a thought.

---

### Post by bharadwaj on 2008-04-23
restarting nautilus may help insome cases I guess...

---

### Post by Andy17MB on 2008-04-24
Thanks all for your suggestions.  Unfortunately none of them have solved the problem.  So to summarise what I've tried:

gconf-editor: I can't find anything in the tabs under desktop>gnome that would seem to have any effect.  Under Applications>Nautilus>preferences there is a show_desktop key that is selected otherwise I can't seem to find anything appropriate

ubuntu-tweak: I didn't have this installed, but I have now (V0.2).. Under desktop>desktop icons the show desktop icons tickbox was ticked. As is show "mounted items on desktop" otherwise the other tick boxes are all empty, so everything looks ok there

System-Preferences>appearances: the Show icons in menus option is ticked

Nautilus:  I have restarted the whole system a couple of times so nautilus has been restarted.  I can't see anything in nautilus's menus that I could have changed that would cause the behaviour either.

One thought - Is there any way I could have changed the size of the icons to zero?

Thanks

Andy

---

### Post by encompass on 2008-04-24
it could be they have all been pushed off screen.
Right click on the background select arrange icons.
Can you even rightclick there?
And could you check any other accounts... are they doing this too?

---

### Post by Andy17MB on 2008-04-28
Encompass, thanks for the reply.  I have tried right-clicking on the desktop, but this does not bring up a menu any more

---

### Post by encompass on 2008-04-28
OK try this...
alt-f2
then type... nautlius...
do your desktop icons showup now?

---

### Post by Andy17MB on 2008-04-28
Aha.. 

Yes they've all reappeared and I've also realised that the desktop wallpaper has reappeared too (only just realised that that had disappeared with the icons)

Have i somehow persuaded the system not to start nautilus on boot up

Thanks encompass for your help

Andy

---

### Post by encompass on 2008-04-28
One more step... but not quite sure how to do it... your going to have to experement...
It could be fixed now... I am not sure..
It could be that you have to add nautilus to the session startup.  System...preferences... sessions... and add a new program with nautilus as the command.
OR
you may have to set something up at login some other way.
Mess with those first too... then you could talk to the mailing list at gnome.org and they could help you there too.
Bummer seeing that happen.

---

### Post by Andy17MB on 2008-04-29
Nautilus,

Thanks for that.  You were right with the first suggestion:
> you have to add nautilus to the session startup. System...preferences... sessions... and add a new program with nautilus as the command.
I've restarted and Hey presto it's all back to normal.  I'm still none the wiser as to how I lost that though.  Thanks again and to everyone else who has made suggestions

Andy

---

### Post by encompass on 2008-04-29
Cool... yeah, sometimes those things happen.  I wish there was a way to just lock that stuff in permenently, but with somany choices of how to setup your desktop these things can be hard to avoid. for example, I don't use icons on my desktop.

---

### Post by LeGollemux on 2008-07-21
thank you for the info here. got my icons back! yay!

---

### Post by JayFunGee on 2010-01-19
Hi

I had a similar experience, and the fix also helped. But this is probably important: I discovered that every time I plug in a USB device (Nikon Camera, iPhone or Nokia Phone) to download stuff; once I am done, the icons are missing. The (Alt+F2, run nautilus) fix from works every time, but perhaps someone can comment on similar experience?

---

### Post by encompass on 2010-01-20
Actually, that is a bug... found here... umm... can't find it now... dang...

---


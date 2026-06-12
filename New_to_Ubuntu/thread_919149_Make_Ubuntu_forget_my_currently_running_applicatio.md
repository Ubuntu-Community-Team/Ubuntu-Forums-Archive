---
title: "Make Ubuntu forget my currently running applications"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by stoogiebuncho on 2008-09-13
Hi,

I've been playing around with running different programs at startup, using the 'Startup Programs' in the System>Preferences>Sessions menu.  All was going fine until I decided to try out the "Remember Currently Running Applications" button under the 'Session Options' area.

It worked... when I startup now it loads the applications that were running when I pressed the button, but I decided I like the 'Startup Programs' interface better.  How do I convince Ubuntu to forget the list of currently running applications it has saved and go back to using the Startup Programs list?

Thanks.

---

### Post by dhtseany on 2008-09-13
Hi,
I assume you tried unchecking the "Automatically remember..." under the Session options tab, right?

If so post back

Peace
Sean

---

### Post by stoogiebuncho on 2008-09-13
Actually, I never checked it to begin with. (and it is currently not checked)  I just pressed the button once.

I suppose I could try checking it and then unchecking it... maybe that would do something.

---

### Post by stoogiebuncho on 2008-09-13
Nope, didn't help.

I've been looking around trying to figure out how this is SUPPOSED to work - it looks like if you DON'T check the checkbox to automatically remember running applications, but you DO press the "Remember Currently Running Applications" button, it's only supposed to change the startup procedure for the next time you log in.  After that, it's supposed to go back to using the startup programs list.

Please correct me if I'm wrong.

So the problem seems to be that it's somehow gotten stuck remembering what was running when I pressed the button rather than reverting back to the startup programs list.

So I want to look at the config file to see if I can see what's going on there.  Does anyone know where the file would be that is supposed to store these changes?

---

### Post by starcannon on 2008-09-13
Close everything down, and then click Remember Currently Running Applications, that's where I'd start if it were me anyway.

---

### Post by dondad on 2008-09-13
> **stoogiebuncho said:**
> Nope, didn't help.

I've been looking around trying to figure out how this is SUPPOSED to work - it looks like if you DON'T check the checkbox to automatically remember running applications, but you DO press the "Remember Currently Running Applications" button, it's only supposed to change the startup procedure for the next time you log in.  After that, it's supposed to go back to using the startup programs list.

Please correct me if I'm wrong.

So the problem seems to be that it's somehow gotten stuck remembering what was running when I pressed the button rather than reverting back to the startup programs list.

So I want to look at the config file to see if I can see what's going on there.  Does anyone know where the file would be that is supposed to store these changes?

Have you looked at the startup programs tab? Try unchecking everything that you don't want there, revert to the setup you want when you start and click the remember button again in that configuration.

---

### Post by stoogiebuncho on 2008-09-13
Yeah, that's what I've done.  The problem isn't that I can't get the programs starting that I want - the problem is that I prefer the other way of doing things (the startup list instead of opening everything you want, making sure nothing else is running, and clicking the button) - and I'm trying to figure out how to get back to that way.

It's obviously just personal preference, since it works equally well either way, it just seems like it should be a simple matter but I can't seem to figure it out.

---

### Post by starcannon on 2008-09-13
Did you try shutting down everything and clicking the button?

---

### Post by stoogiebuncho on 2008-09-13
Yes, I did try shutting everything down and clicking the button.  It works: when I start up next time, it only starts the programs that were running when I clicked the button the last time.

But it never reverts back to using the list of startup programs.  It continues to start every time with what was running when I clicked the button until I click the button again with a different group of programs running.

Does this make sense?  I can make it do what I want it to do, I just can't use the interface that I prefer.

---

### Post by haud on 2008-12-17
I have a similar problem, only that I want ubuntu to remember my currently running aplications, and it only does it once if I click the button to remember currently running applications, next time after next time I doesn't remember anything. and weird is that if I check that box to remember stuff automatically or uncheck it, it doesn't take any effect.

---

### Post by raideen on 2010-06-21
I realize that this thread is ancient, but in case someone else is looking for the solution, delete the files out of ~/.config/gnome-session/saved-session

---

### Post by keypox on 2010-09-15
> **raideen said:**
> I realize that this thread is ancient, but in case someone else is looking for the solution, delete the files out of ~/.config/gnome-session/saved-session

thank you!  Sucks the gui doesnt work.

---

### Post by erlend_sh on 2010-10-28
> **raideen said:**
> I realize that this thread is ancient, but in case someone else is looking for the solution, delete the files out of ~/.config/gnome-session/saved-session
Thanks a bunch man! There really should be a "Undo" or "Empty Session" button right under "Remember Currently Running Application". It's also not very clear that the applications will be remembered repeatedly; I thought it would just be for the next reboot, then things would go back to normal.

---

### Post by vickychijwani on 2011-02-17
> **raideen said:**
> I realize that this thread is ancient, but in case someone else is looking for the solution, delete the files out of ~/.config/gnome-session/saved-session

Thanks a lot buddy!

---

### Post by SandJ on 2012-04-08
> **raideen said:**
> I realize that this thread is ancient, but in case someone else is looking for the solution, delete the files out of ~/.config/gnome-session/saved-sessionIt may be ancient, but I have spent two hours trying to stop my netbook from loading Akregator and Korganizer and it has been driving me MAD.

I have no recollection of ever having clicked on "Remember Currently Running Application" and have been editing .autostart files, going through the KDE help, going through every system and KDE configuration option three times and heaven-only knows what else.

That "Startup Applications' Preferences" / Options screen desperately needs a "clear existing remember apps" button.  (Ubuntu 10.04)

Thanks for the solution  =D>

Edit: oh, wow!  Deleting the 8 files in that directory has made by Ubuntu start up much more quickly.  It's like a new PC again.  (I wonder what was in the other six session files other than the two visible apps I could see.)

---

### Post by oldos2er on 2012-04-08
Closed, necromancy.

---


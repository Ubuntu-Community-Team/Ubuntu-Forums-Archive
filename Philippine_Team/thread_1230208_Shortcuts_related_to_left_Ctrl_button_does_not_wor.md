---
title: "Shortcuts related to left Ctrl button does not work with Ubuntu 9.04"
date: 2009-08-03
forum: Philippine Team
---

### Post by OnesimusUnbound on 2009-08-03
I've opened my laptop and when I'm about to highlight the text in the textbox using Ctrl-A, it instead typed 'a'. I tried Ctrl-C and Ctrl-V but instead copying and pasting, the characters 'c' and 'v' appeared. Strangely, if I substitute the right Ctrl button for the left one, it worked.

I've googled for the issue, but I was unable to find any working solution. Any help will be appreciated. :)

Laptop: Acer Aspire 4315
OS: Ubunutu 9.04

---

### Post by loell on 2009-08-03
ever thought that maybe the particular key is really dead?

---

### Post by OnesimusUnbound on 2009-08-03
Thanks loell for the suggestion. I was hesitant to conclude that the key is dead because I was able to use it yesterday. I've found a [Python script]("http://www.daniweb.com/forums/thread112975.html#") that will detect key strokes and I will use it to check if my Left Control key is dead.

For now, I could not verify it because I'm at work. I'll let you know what I've found the following day. ;)

---

### Post by dodimar on 2009-08-03
You could try getting to the BIOS then Ctrl+Alt+Del .... if it doesn't work, then the key is dead...

---

### Post by jonnan on 2009-08-04
Actually, this *sounds* (Maybe not - for me it's both keys) like the same issue I've been having and was searching for help with - it's been going on for awhile, but it's not irritating enough for me to put down what I'm doing and post.

When attempting to use a ctrl-key combination on some applications, the control key will sorta 'escape' whatever I'm doing, as if I had clicked the mouse somewhere.

example - copy/paste a file name, you right click to rename a file, hit ctrl-c to copy the file, the instant you hit the ctrl key the filename goes back to the default as if you clicked somewhere on the screen.

Now, if you hold down the ctrl key, select 'rename' - then hold down the X or C or V *without* ever having actually let go of the control key, it will cut/copy/paste normally. So you can work around it but it's obviously a darn unintuitive and painful way to do it.

I think it may be related to a configuration I came across to highlight the mouse when you lose it so it 'ripples' when you click on the control key, but darned if I can remember where I found this setting, nevermind if it actually started at that point or if I'm just thinking about stuff that happened about the same time period - I certainly didn't notice it right away if it was.

Jonnan

Edit: Just FYI - Evidently typing that out jogged my brain enough to find it and it was indeed the issue. On the off chance you're experiencing the same issue, it is:
System --> Control Center --> Mouse (General) --> Locate Pointer

If that's checked uncheck that. That option seemed like it might be useful at the time, so *very* much not worth it - {G}.

---

### Post by dannybuntu on 2009-08-04
In my case, on my desktop, somehow I didn't notice that the Left Shift key was stuck so it was always pressing so to speak. That borked the other keys functions.

---

### Post by OnesimusUnbound on 2009-08-04
Update:

Gee a simple restart will resolve the issue. Now, I really do not know what messed up the configuration.  Anyway, I suspect it has to do when I re-enabled of the touch pad.  I’ll recreate the issue and report what I’ve found tomorrow.

---

### Post by OnesimusUnbound on 2009-08-06
Update:

I've tried recreating the issue by disabling and then enabling the touch pad and the ctrl key combination still works. Now, really do not know what caused the issue.

Any, thanks for the reply :)

---


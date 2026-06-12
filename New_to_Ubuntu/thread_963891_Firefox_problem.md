---
title: "Firefox problem"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by GarethA on 2008-10-30
My firefox (3.0.3) back and forward arrows have stopped working.
Also my history is no longer being recorded (old stuff is still there) and my bookmarks are gone.
Anyone seen this before? I have the latest patches...

:confused:

---

### Post by etusha on 2008-10-30
firefox in ubuntu suck 
to slow, a lot of errors
that is one reason that i turn can in WIN
plus ubuntu miss some things good: AVirus ,MSN  support video audio

---

### Post by SteveLefty on 2008-10-30
Simple, but have you tried resetting all your preferences to the defaults?

---

### Post by kansasnoob on 2008-10-30
> **etusha said:**
> firefox in ubuntu suck 
to slow, a lot of errors
that is one reason that i turn can in WIN
plus ubuntu miss some things good: AVirus ,MSN  support video audio

Nonsense!

---

### Post by etusha on 2008-10-30
that dont work i have try it 
i have try purge too

---

### Post by kansasnoob on 2008-10-30
> **GarethA said:**
> My firefox (3.0.3) back and forward arrows have stopped working.
Also my history is no longer being recorded (old stuff is still there) and my bookmarks are gone.
Anyone seen this before? I have the latest patches...

:confused:

I was going to suggest backing up your bookmark folder, but yipes! You're not getting bookmarks!

I've noticed that Firefox has a backup folder for bookmarks but I've never had to access it.

I'll do some searching.

---

### Post by kansasnoob on 2008-10-30
> **kansasnoob said:**
> I was going to suggest backing up your bookmark folder, but yipes! You're not getting bookmarks!

I've noticed that Firefox has a backup folder for bookmarks but I've never had to access it.

I'll do some searching.

I should add that what I was going to suggest was backing up your bookmarks, then dumping the entire Mozilla folder to the trash.

That way when you restart Firefox an entirely new Mozilla folder will be created and you can start from scratch.

But let me do a little looking.

How important are your bookmarks to you?

---

### Post by lennartack on 2008-10-30
> **kansasnoob said:**
> Nonsense!
Unfortunately he's pretty much right. Firefox IS slower on linux than on windows. Try it out yourself.

---

### Post by kansasnoob on 2008-10-30
I see there are several items in the help section:

[http://support.mozilla.com/tiki-searchresults.php?locale=en-US&q=bookmark+backups&sa=](http://support.mozilla.com/tiki-searchresults.php?locale=en-US&q=bookmark+backups&sa=)

If we can get just the bookmarks back I'd be glad to tell you how to save and restore them to a fresh mozilla folder. It's quite simple.

---

### Post by Seaweed on 2008-10-30
exact same problem here since upgrading to 8.10

where is the firefox folder located which i need to delete?

---

### Post by kansasnoob on 2008-10-30
> **lennartack said:**
> Unfortunately he's pretty much right. Firefox IS slower on linux than on windows. Try it out yourself.

Uh, I'm using it right now.

IMHO nothing is better in Windows!

Opera 9.62 works well in Ubuntu (I've tried it in Hardy and Intrepid) if Firefox really bothers you.

---

### Post by Coreigh on 2008-10-30
Have you tried using about:config?

If you type about:config in the addressbar the Firefox system config page will load. Accross the top of the page (just below your shortcuts / bookmarks bar) you will see

Preference Name | Staus | Type | Value | 

At the far right of that line there is a small icon, click it and one of the choices is "Restore Defaults"

---

### Post by kansasnoob on 2008-10-30
> **Seaweed said:**
> exact same problem here since upgrading to 8.10

where is the firefox folder located which i need to delete?

Well I never do Dist upgrades anymore because too many things break (my luck has been about 50% success rate).

But what I do is go to Places > Home Folder, then View > Show Hidden Files. Next look for .mozilla. That's the folder you want to delete if you want to start fresh, but it will dump all Firefox and Thunderbird settings, bookmarks, etc.

To back up bookmarks, open .mozilla and then open .firefox. You'll see a folder that begins with 8 random figures like: ipfreely.default. (Sorry for the stupid humor). Open it. You'll want to copy the places.sqlite folder. I usually just paste it to the desktop.

Then when you've restarted Firefox you can copy-n-paste the places.sqlite folder back into the ipfreely.default folder.

I've tried just replacing the ipfreely.default folder entirely but it's problematic.

---

### Post by kansasnoob on 2008-10-30
> **Coreigh said:**
> Have you tried using about:config?

If you type about:config in the addressbar the Firefox system config page will load. Accross the top of the page (just below your shortcuts / bookmarks bar) you will see

Preference Name | Staus | Type | Value | 

At the far right of that line there is a small icon, click it and one of the choices is "Restore Defaults"

Cool! That's a new one on me!

---

### Post by GarethA on 2008-10-30
Thanks all...
tried resetting all prefs but still same problems...

losing bookmarks not the end of the world so trashed mozilla folder and started again - all good now
would be useful to know how to stop it happening again though

I'm afraid that even if firefox is a bit quicker i still aint interested in windows :)
more to computers than browsing!

---

### Post by kansasnoob on 2008-10-30
> **GarethA said:**
> Thanks all...
tried resetting all prefs but still same problems...

losing bookmarks not the end of the world so trashed mozilla folder and started again - all good now
would be useful to know how to stop it happening again though

I'm afraid that even if firefox is a bit quicker i still aint interested in windows :)
more to computers than browsing!

Did this happen on an upgrade?

I've only had it happen during upgrades.

Especially upgrades with a seperate "home" partition.

I've had a few problems with "add-ons" that can usually be straightened out though. Just remember whenever you make changes to Firefox to "quit" by going to File > Quit rather than just click the X in the upper right hand corner.

I don't know why:confused:

---


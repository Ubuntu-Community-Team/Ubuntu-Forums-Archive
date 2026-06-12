---
title: "Flash problems"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by GreenLungz on 2008-05-07
I've just recently updated to Hardy Heron and decided to start off anew, and for some reason flash seems to either not play at all, or play sluggishly. I also always get this weird play button on any flash app. and have to click it to even view the content. Attached is an example. The codec's I'm running are Swfdec 0.6.0.

Any help?

---

### Post by Brightbelt on 2008-05-07
I'm just curious, ...Did you install Flash using Synaptic??

Frank B.

---

### Post by miwaypet on 2008-05-07
Remove all swf and gnash plugins and players. 

At the terminal: sudo apt-get autoremove flashplugin-nonfree; sudo apt-get install flashplugin-nonfree libflashsupport

That should clear it up.

---

### Post by ubuntu-freak on 2008-05-07
I would also suggest you install Adobe Flash and remove any other Flash-related package. Just incase you miss anything that may clash with Adobe Flash, run this command: 
 
**sudo apt-get purge flashplugin-nonfree gnash gnash-common swfdec-mozilla && sudo apt-get install flashplugin-nonfree libflashsupport**
 
You might also want to give the browser Epiphany a try, it uses the same engine as Firefox, but is lighter and not buggy.
 
Nathan

---

### Post by GreenLungz on 2008-05-08
> **reassuringlyoffensive said:**
> I would also suggest you install Adobe Flash and remove any other Flash-related package. Just incase you miss anything that may clash with Adobe Flash, run this command: 
 
**sudo apt-get purge flashplugin-nonfree gnash gnash-common swfdec-mozilla && sudo apt-get install flashplugin-nonfree libflashsupport**
 
You might also want to give the browser Epiphany a try, it uses the same engine as Firefox, but is lighter and not buggy.
 
Nathan

Worked like a charm. 

Took a look at epiphany, looked pretty nice, might have to give it a try, although Firefox hasn't really given me any problems other than the one you just cleared up.

---

### Post by ConMan318 on 2008-05-08
Alright, I am having the same problem and none of the above fixes changes anything.  I've also gone into synaptic and searched "flash", marked everything that was installed for complete removal, and then ran "sudo apt-get install flashplugin-nonfree libflashsupport" in the command line.  The problem persists.

Any other fixes for it?

---

### Post by ubuntu-freak on 2008-05-08
> **ConMan318 said:**
> Alright, I am having the same problem and none of the above fixes changes anything.  I've also gone into synaptic and searched "flash", marked everything that was installed for complete removal, and then ran "sudo apt-get install flashplugin-nonfree libflashsupport" in the command line.  The problem persists.

Any other fixes for it?

 
That's strange. How does Flash perform in Epiphany? Also, it's possible a manual install may work better, see part 1 of my [how-to](http://ubuntuforums.org/showthread.php?t=766683).
 
Nathan

---

### Post by ConMan318 on 2008-05-08
> **reassuringlyoffensive said:**
> That's strange. How does Flash perform in Epiphany? Also, it's possible a manual install may work better, see part 1 of my [how-to](http://ubuntuforums.org/showthread.php?t=766683).
 
Nathan

It does work fine in Epiphany, but there are a few reasons I'd rather use Firefox.  Also, I tried the manual install, but it kept insisting that /usr/lib/firefox and even /usr/lib/mozilla were not valid directories.  I can access both of those directories from the command line, so I don't know why they aren't recognized.  Any ideas?

It kinda seems like the problem is not the installation, but the preferences set for using Flash embedded in a website seem to be set to not auto-play, but wait for the user to press play.  Is there any way to adjust the settings of Flash in that way?  Of course, that could have nothing to do with it, just a guess, really.

---

### Post by ubuntu-freak on 2008-05-08
> **ConMan318 said:**
> It does work fine in Epiphany, but there are a few reasons I'd rather use Firefox.  Also, I tried the manual install, but it kept insisting that /usr/lib/firefox and even /usr/lib/mozilla were not valid directories.  I can access both of those directories from the command line, so I don't know why they aren't recognized.  Any ideas?

It kinda seems like the problem is not the installation, but the preferences set for using Flash embedded in a website seem to be set to not auto-play, but wait for the user to press play.  Is there any way to adjust the settings of Flash in that way?  Of course, that could have nothing to do with it, just a guess, really.

 
If it works fine in Epiphany, forget the manual install. I have no clue what's wrong with FF, it is beta, but that doesn't explain why your having issues and others aren't. Try deleting the pluginreg.dat file in home/user/.mozilla/firefox - find it in the weirdly named profile folder. Also, delete the urlclassifier files as well. Restart FF.
 
Nathan

---

### Post by ConMan318 on 2008-05-08
I removed the pluginreg.dat file; this is all I have left:
```

connor@connor-laptop:~/.mozilla/firefox$ ls
emydzd8p.default  profiles.ini

```
Where are the urlclassifier files?

---

### Post by ubuntu-freak on 2008-05-08
> **ConMan318 said:**
> I removed the pluginreg.dat file; this is all I have left:
```

connor@connor-laptop:~/.mozilla/firefox$ ls
emydzd8p.default  profiles.ini

```
Where are the urlclassifier files?

 
Weird. I have many files in that profile folder. The pluginreg was the main one though. Any improvement?
 
Nathan

---

### Post by ConMan318 on 2008-05-08
No, it kept it the same.  Maybe it's something in /usr/lib/mozilla or /usr/lib/firefox?

Maybe I'll have to start using Epiphany :(

---

### Post by ubuntu-freak on 2008-05-08
> **ConMan318 said:**
> No, it kept it the same.  Maybe it's something in /usr/lib/mozilla or /usr/lib/firefox?

Maybe I'll have to start using Epiphany :(

 
Epiphany uses /usr/lib/firefox/plugins, so can't be that. Try renaming the firefox folder in /.mozilla and reinstall FF3.
 
Nathan

---

### Post by ConMan318 on 2008-05-08
It's fixed!  I was about to uninstall FF3 and revert to FF2, so I searched 'firefox' in synaptic, and one of the things I saw was a Flash app, and I noticed that it was checked, even though I had removed it from the command line...

Anyway, I marked it for complete removal in synaptic and then reinstalled with your command, and now it works. :)

So for anyone that the above fixes do not work for, try using synaptic.

---

### Post by ubuntu-freak on 2008-05-08
> **ConMan318 said:**
> It's fixed!  I was about to uninstall FF3 and revert to FF2, so I searched 'firefox' in synaptic, and one of the things I saw was a Flash app, and I noticed that it was checked, even though I had removed it from the command line...

Anyway, I marked it for complete removal in synaptic and then reinstalled with your command, and now it works. :)

So for anyone that the above fixes do not work for, try using synaptic.

 
It was swfdec-mozilla? Sounded like you had it installed, but my purge command should've removed it. That's stupid.
 
Glad you got it sorted,
 
Nathan

---

### Post by euchrid33 on 2008-06-05
> **miwaypet said:**
> Remove all swf and gnash plugins and players. 

At the terminal: sudo apt-get autoremove flashplugin-nonfree; sudo apt-get install flashplugin-nonfree libflashsupport

That should clear it up.

I'm so glad that this was left up.  I had the same problem, and it's cleared it right up.  Thank you!

---


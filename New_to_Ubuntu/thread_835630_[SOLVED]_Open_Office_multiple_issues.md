---
title: "[SOLVED] Open Office multiple issues"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by bwallum on 2008-06-20
Anybody experiencing problems with OO? I can't print colours, although they show in preview, Draw hangs when using 'File' menu. Can't produce a pdf from Writer. Major meltdown....just me?

---

### Post by sydbat on 2008-06-20
Is it an upgrade or clean install of OOo? I have read quite a few threads about the upgrade going badly, although my upgrade has not shown any problems. Maybe uninstall,reinstall the OOo suite...?

---

### Post by silkstone on 2008-06-20
Not tried Draw, but I've just tested Writer with PDF generation and colour printing and it all works for me.

Hardy - clean install - printing to Canon MP610.

Maybe follow sydbat's suggestion - remove OOo and reinstall?

---

### Post by bwallum on 2008-06-21
Thanks guys. I have previously tried to uninstall and then reinstall. When i first tried to remove OO a message popped up using add/remove to tell me to use synaptic due to 'dependencies'. I suspect that I may have removed something than I shouldn't, or something of that nature. I reinstalled using add/remove and chose the OO Suite option rather than load each package individually.

Is there a list of packages (as shown by synaptic) that are required for error free operation of OO? I could then check them all to see if they were present.

---

### Post by bwallum on 2008-06-21
The problem appears to be in in the 'openoffice.org-gtk' package and only affects 64bit machines. To get a working OO system I did this:

Remove all openoffice packages:-```
sudo apt-get purge openoffice.org*
```

Then reinstall the whole suite ```
sudo apt-get install openoffice.org
```

This will give a working OO although it does not have the gnome window style. 

To break it again do this ```
sudo apt-get install openoffice.org-gtk
```

You can repeat the above to get a working system back. Note that 'openoffice.org-gnome' requires 'openoffice.org-gtk'. I also tried removing '.openoffice.org2' when purging open office but it did not fix the problem.

---

### Post by varaonaid on 2008-06-24
I have a 32 bit computer and am having terrible trouble with OO.  I've tried the purge and reinstall, twice.  The menu icons were all messed up and I finally deleted them when the shortcuts weren't removed during the uninstall.  They didn't come back after the reinstall.  

But the biggest problem is that when I click on any OO document (no matter what format - writer, speadsheed, calc, etc) it won't open the document.  I've tried to choose "open with" and that doesn't work either.  I can open the documents going through OO file menu and choosing "open" but that's really a pain to do each time.

I'm running Hardy via an update.

Any help would be most appreciated!

---

### Post by bwallum on 2008-06-25
> **varaonaid said:**
> I have a 32 bit computer and am having terrible trouble with OO.  I've tried the purge and reinstall, twice.  The menu icons were all messed up and I finally deleted them when the shortcuts weren't removed during the uninstall.  They didn't come back after the reinstall.  

But the biggest problem is that when I click on any OO document (no matter what format - writer, speadsheed, calc, etc) it won't open the document.  I've tried to choose "open with" and that doesn't work either.  I can open the documents going through OO file menu and choosing "open" but that's really a pain to do each time.

I'm running Hardy via an update.

Any help would be most appreciated!

If you are prepared to have openoffice work but not be integrated with Gnome (not the same look and feel) then this is how I got mine running. 

Remove all openoffice packages:-
```
sudo apt-get purge openoffice.org*
```

Then reinstall the whole suite
```
sudo apt-get install openoffice.org
```

You then need to add in a dictionary. Use synaptic and find one that suits. I use openoffice.org-I10n-en-gb. Choose one for your country preference.

---

### Post by varaonaid on 2008-06-26
Hi there,

Thanks for the reply.  Unfortunately, that didn't work for me.  So in an act of desperation, I installed OO 3 beta and it works perfectly.  So, don't know what's causing version 2.4 to be completely unusable but it sure is.  

Oh well, at least I have it working now!

Thanks again :D

---

### Post by Stunts on 2008-06-26
Just out of curiosity...
Do you have GTK and gnome integration in the Beta 3?

---

### Post by Maupertus on 2008-06-26
> **varaonaid said:**
> Hi there,

Thanks for the reply.  Unfortunately, that didn't work for me.  So in an act of desperation, I installed OO 3 beta and it works perfectly.  So, don't know what's causing version 2.4 to be completely unusable but it sure is.  

Oh well, at least I have it working now!

Thanks again :D

@Varaonaid: How is your integration with Evolution, I had the same problem with opening documents and such, but it's the same with opening doc's in Evolution.

Does 3 Beta integrate with Evo?

---

### Post by bwallum on 2008-07-03
Update of 1st July 2008 has solved integration with Gnome issues and now all OOo apps are working as expected for me. Small issues remain such as names of font characteristics not being available in English on font menus, but these are the subjects of other threads/Launchpad bugs.

---


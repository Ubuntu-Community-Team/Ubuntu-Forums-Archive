---
title: "[SOLVED] Firefox 2 Add-ons wont install"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by kestrel1 on 2008-05-06
If I try to install any add-ons to FF2 I get an error stating that there was an installation error with the number 203.
I have removed FF3 from my machine (Ubuntu 8.04) & installed FF2. I tried removing FF2 & re-installing, but still no go. Any advice would be appreciated.
Cheers
K1:)

---

### Post by Oldsoldier2003 on 2008-05-06
> **kestrel1 said:**
> If I try to install any add-ons to FF2 I get an error stating that there was an installation error with the number 203.
I have removed FF3 from my machine (Ubuntu 8.04) & installed FF2. I tried removing FF2 & re-installing, but still no go. Any advice would be appreciated.
Cheers
K1:)

try renaming your.Mozilla directory in your home folder. When you restart FF it should recreate the folder and prefs cleanly- you can always manually move your bookmarks into the new folder if this fixes the issue with plugins

---

### Post by explainer on 2008-05-06
Is there a documented procedure for how to install Firefox 2 over the default FF3 beta in Hardy Heron.  The loss of all my FF2 extensions requires that I use FF2 and wait for FF3 to catch up on compatible extensions.  Any help on installing firefox 2 would be appreciated.  Since this is an initial install of 8.04, I don't have any bookmarks saved at this time.  In fact, my bookmarks are all on the Foxmarks server, and can't be accessed until I get rid of this $%&*! FF3 browser!

---

### Post by kestrel1 on 2008-05-06
Yes that sorted it. What files do I need to move across to restore my bookmarks?

---

### Post by Oldsoldier2003 on 2008-05-06
> **kestrel1 said:**
> Yes that sorted it. What files do I need to move across to restore my bookmarks?

your bookmarks are backed up in ~/.mozilla/firefox/<random_string>.default/bookmarkbackups the actual bookmarks are located at ~/.mozilla/firefox/<random_string>.default/bookmarks.html

---

### Post by kestrel1 on 2008-05-07
> **explainer said:**
> Is there a documented procedure for how to install Firefox 2 over the default FF3 beta in Hardy Heron.  The loss of all my FF2 extensions requires that I use FF2 and wait for FF3 to catch up on compatible extensions.  Any help on installing firefox 2 would be appreciated.  Since this is an initial install of 8.04, I don't have any bookmarks saved at this time.  In fact, my bookmarks are all on the Foxmarks server, and can't be accessed until I get rid of this $%&*! FF3 browser!
All you should need to do to remove FF3 is this:
```
sudo apt-get remove firefox-3.0
```
Then to install FF2 type this:
```
sudo apt-get install firefox-2
```

---

### Post by kestrel1 on 2008-05-07
> **Oldsoldier2003 said:**
> your bookmarks are backed up in ~/.mozilla/firefox/<random_string>.default/bookmarkbackups the actual bookmarks are located at ~/.mozilla/firefox/<random_string>.default/bookmarks.html
Many thanks, I copied over the folder, but not the bookmarks.html file (missed it)
Now working as it should.

---

### Post by txGreg on 2008-05-17
> **Oldsoldier2003 said:**
> try renaming your.Mozilla directory in your home folder. When you restart FF it should recreate the folder and prefs cleanly- you can always manually move your bookmarks into the new folder if this fixes the issue with plugins
Anyone have a more... elegant solution?  I don't want to lose all of the settings I have (had) in my previous extensions - especially TabMixPlus, which FF3 has hosed.

I could start with a clean profile, but it would be very irritating, time-consuming, and probably impossible for me to migrate everything cleanly.

thanks!

---

### Post by charlieh00003 on 2008-05-21
I have had so many problems with firefox in Hardy I don't even know where to begin.

But I can begin with the one described in this thread.

OK, firefox 3 has a major bug in it that just won't work for me. So I need firefox-2.

Over the weeks, I've gotten the impression that ff2 and ff3 are utterly incompatable with each other in terms of profile, and that the one will corrupt the other's profile so that neither will work.

Therefore, in switching to firefox-2 I have found that if I don't completely rename my .mozilla/firefox directory, I won't even get off the ground.

But even that doesn't always work.

The last thing I did was:
 (1) in synaptics, search for "firefox" and competely remove everything that has firefox in the name
 (2) in a shell "locate firefox" and remove all directories found.
 (3) remove ~/.mozilla
  (4) in synapitcs, install firefox-2.

The result is, I got a browser that runs, but I can't install add-ons. This last time around, I tried to install Adblock, but it says "Requires additional items".

In previous iterations, I've been able to install addons, but the Preferences button didn't do anything (the ones that aren't greyed out).

I've had a devil of a time getting flashplayer installed. Sometimes after going through this procedure, I can install the player through the browser. Other times I can't and have to install it manually.

I guess what I'd really like to find is a procedure to bring hardy down to a state where it doesn't have anything in in that has anything to do with a browser, and then install everything that firefox-2 needs to run.

Another poster is correct, what *should* work is to remove firefox-3 and install firefox-2, but that doesn't begin to do the right thing and has non-repeatable and unpredictable results.

---

### Post by charlieh00003 on 2008-05-21
I removed everything that has anything to do with firefox from synaptics, deleted ~/.mozilla, then downloaded the install file from mozilla.com and installed it.

The browser seems to be running correctly so far. I can install ad-ons.

---

### Post by jimloomis on 2008-06-04
I'm having the same troubles as charlie as far as the add-on troubles when clicking the "preferences button.

I've already tried uninstalling/reinstalling ff2 and it hasn't fixed it, although I haven't done the manual install. I hate working with the terminal, so is there a way around that?

I'm at my wits end with Ubuntu so far, it seems like one quirk after another pops up (trouble mounting NTFS drives, wireless issues, ff3, etc.)

This forum is incredibly helpful and its the only reason why I've stuck with Ubuntu...

Thanks in advance,
Jim

---

### Post by kestrel1 on 2008-06-06
Jim: You may be better off starting a new thread as this one has got the solved tag on it. You can always add a link to this one from a new thread.

---

### Post by Beth1957 on 2008-07-25
Thank you! I'd deleted all of the FF3 from synaptics, but that didn't help. Your workround did though!

---


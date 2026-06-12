---
title: "Gnome Shell bug?"
date: 2011-08-18
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sgage on 2011-08-18
In the Activities overview, the thumbnails of the running programs display a close button when you mouse over them, so you don't have to bring up the program just in order to shut it down.

I have noticed that after a while, these close buttons stop appearing. It's kind of inconvenient to bring up a program (thereby leaving the overview) simply in order to close it. I can't find any pattern as to what might trigger this.

Does anyone else experience this glitch?

---

### Post by ranch hand on 2011-08-18
Sorry, don't use it.   I have the "friperies" extensions installed and have a menu, a windows list and my launchers on the top panel.

I only see the over view if I want to for some reason (rare) and when first logging in.

It could be that you should report it, at least check to see if there is a bug filed on it.  Behavior that is not consistent sure sounds like a bug to me.

---

### Post by Harry33 on 2011-08-18
I do not see such a behaviour, or I did not test it the way you meant.
After 1 hour of uptime, these X-buttons (when mouse-over) appear immediately to the upper right corner of the overviews application window (is that the thumbnail?)

---

### Post by sgage on 2011-08-18
> **Harry33 said:**
> I do not see such a behaviour, or I did not test it the way you meant.
After 1 hour of uptime, these X-buttons (when mouse-over) appear immediately to the upper right corner of the overviews application window (is that the thumbnail?)

They do for me as well, until for some reason they don't - usually after a couple of hours. I am trying to find some sort of pattern to its occurrence, but no luck so far. I have a feeling it is related to the running of a certain program, but can't reproduce it.

Of course naturally, today it's been going for 6 hours, and still working fine :o

---

### Post by sgage on 2011-08-18
> **ranch hand said:**
> Sorry, don't use it.   I have the "friperies" extensions installed and have a menu, a windows list and my launchers on the top panel.

I only see the over view if I want to for some reason (rare) and when first logging in.

It could be that you should report it, at least check to see if there is a bug filed on it.  Behavior that is not consistent sure sounds like a bug to me.

Where did you get that extension - I'd like to give it a try.

---

### Post by benmoran on 2011-08-18
I've experienced the same behavior as you describe. Today they're working normally, but sometimes the X is just missing from the overview.

---

### Post by Sennaista on 2011-08-19
Same here...it seams to be a totally random occurrence.

---

### Post by sgage on 2011-08-19
> **Sennaista said:**
> Same here...it seams to be a totally random occurrence.

Seems that way to me, too. :confused:  I sure would like to find a pattern if I can...

---

### Post by sgage on 2011-08-19
Hmmm... maybe something to do with Synaptic? I had a suspicion about spm, so I ran most of the day yesterday and this morning without running it, and everything was fine. I fired up spm, did a bunch of updates, and the close buttons were gone!

So I logged out, logged back in - close buttons working. Ran spm, did some updates, and... the close buttons are still working. :confused:

Maybe it's updates that have certain triggers, or maybe it's just certain packages - I don't know. I'll keep observing...

[EDIT: I just updated Gnome Shell from the repos, and close buttons gone, presumably until I log out/in.]

---

### Post by sgage on 2011-08-19
Another set up updates with Synaptic, and buttons gone. Starting to look like a trend.

Next round of updates I'll use apt-get and see what happens.

[Edit: just did an update with apt-get, and close-buttons gone. Running 'gnome-shell --replace brings them back.]

---

### Post by ranch hand on 2011-08-19
> **sgage said:**
> Where did you get that extension - I'd like to give it a try.
To be flip, on the internet.  To be honest, I can't find where I got it again.

I got a tgz, extracted it and slapped the buggers in /usr/share/gnome-shell/extensions (created for these files).  Some did not work, can't remember which.  Said to myself, "self you are the only user, put them in ~/."

Hunted up the right directory there (drive not connected right now, don't remember exactly).  Had to add the "extensions" sub directory again.  They did not all work (different ones this time).

I said a number of things at this point.  I also put them back in the /usr directory mentioned above (why did I remove them just to put them in ~/?  Beats me.  But they all work fine from there now.

[http://howto.wired.com/wiki/Manually_Install_Gnome_3_Extensions](http://howto.wired.com/wiki/Manually_Install_Gnome_3_Extensions)
[http://www.webupd8.org/2011/04/gnome-shell-extensions-additional.html](http://www.webupd8.org/2011/04/gnome-shell-extensions-additional.html)
[http://www.webupd8.org/2011/04/themeselector-gnome-shell-extension-to.html](http://www.webupd8.org/2011/04/themeselector-gnome-shell-extension-to.html)
[http://www.webupd8.org/2011/04/themeselector-gnome-shell-extension-to.html](http://www.webupd8.org/2011/04/themeselector-gnome-shell-extension-to.html)
[http://www.fpmurphy.com/gnome-shell-extensions/](http://www.fpmurphy.com/gnome-shell-extensions/)
[http://justinstories.wordpress.com/2011/05/27/five-must-have-gnome-shell-extensions-for-fedora-15/](http://justinstories.wordpress.com/2011/05/27/five-must-have-gnome-shell-extensions-for-fedora-15/)
[http://live.gnome.org/GnomeShell/Extensions](http://live.gnome.org/GnomeShell/Extensions)
[http://blog.fpmurphy.com/2011/03/customizing-the-gnome-3-shell.html](http://blog.fpmurphy.com/2011/03/customizing-the-gnome-3-shell.html)

Above are some sites I found when hunting for where I picked up that package.  Have not really looked at them, they all look like they may have something to offer.

I do however have this the .tgz which I can't attach here.  If you have a favorite site for file sharing let me know if the above links do not have a better option.  Particularly;
[http://www.fpmurphy.com/gnome-shell-extensions/](http://www.fpmurphy.com/gnome-shell-extensions/)

which is going to get some close attention here.

---

### Post by jbicha on 2011-08-19
> **ranch hand said:**
> 
Particularly;
[http://www.fpmurphy.com/gnome-shell-extensions/](http://www.fpmurphy.com/gnome-shell-extensions/)

I wish those developers would put their extensions in the official gnome-shell-extensions repository. They'd get a whole lot more recognition and use, and they'd get updated for development releases.

---

### Post by ranch hand on 2011-08-20
Yes that would be nice and I think it is getting more that way.

Most of these guys are not "Gnome" users.  They are Fedora users.  You can get the extensions in RPM form and as tarballs.  Now that more are doing it the word will get around and the Gnome repo will start getting more of them.

When extensions start getting out there from the Debian branch folks I think that will help the Gnome repo too.  Just too much floating around to be convenient even now.  Another 3 months and it will be impossible.

I think most in there now are from the Fedora and Open Suse repos.  I think that it will be easier to get extensions accepted by Gnome which will make them available to all the distros repos.  When these devs, many brand new at this, figure that out it will help.

---


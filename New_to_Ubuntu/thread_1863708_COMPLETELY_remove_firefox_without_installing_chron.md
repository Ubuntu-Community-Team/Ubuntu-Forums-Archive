---
title: "COMPLETELY remove firefox without installing chronium?"
date: 2011-10-18
forum: New to Ubuntu
---

### Post by krakket on 2011-10-18
I recently installed Opera and like it 1000x better than firefox. As a result of this I really want to completely remove all traces of firefox.  However, no matter wich method I go about it,  It appears that I need to install chronium to do so..

In Synaptic it just says it will uninstall mozilla and then install chronium. There's no option to uncheck installing Chronium.  In terminal it gives me no option either.  The only web browser I want on my computer is Opera.. . I can't understand why i'm forced to retain either firefox or chronium? Stupid.

Does anyone know how to get around this?

---

### Post by Bmonsterboy on 2011-10-18
Why do you want to completely remove it? I mean,even though you might never use it, is it going to be taking up all that much space?

---

### Post by krakket on 2011-10-18
I'd just rather it not be there.  I guess i can be kindof picky about only wanting programs on my computer that I use. I don't like all the "clutter" programs sitting around. :p

---

### Post by Lars Noodén on 2011-10-18
What about using the shell?

```

sudo apt-get purge firefox

```

That should remove just firefox.

---

### Post by lovinglinux on 2011-10-18
> **Lars Noodén said:**
> What about using the shell?

```

sudo apt-get purge firefox

```

That should remove just firefox.

That will have the same results. The problem is that the system requires a browser to be installed and Opera is not recognized as such.

See [http://askubuntu.com/questions/11934/why-does-removing-firefox-install-another-browser](http://askubuntu.com/questions/11934/why-does-removing-firefox-install-another-browser)

---

### Post by Bmonsterboy on 2011-10-18
Could you just go into lib and remove the files?

---

### Post by lovinglinux on 2011-10-18
> **Bmonsterboy said:**
> Could you just go into lib and remove the files?

Not a good idea. Don't delete system files manually, unless you know exactly what you are doing.

I would just leave Firefox alone. Remove the icon from the launcher and try to forget that it exists.

I am not sure, but I think I have seen a similar thread with a solution. Unfortunately, I can't find it right now.

---

### Post by Lars Noodén on 2011-10-18
> **lovinglinux said:**
> That will have the same results. The problem is that the system requires a browser to be installed and Opera is not recognized as such.

See [http://askubuntu.com/questions/11934/why-does-removing-firefox-install-another-browser](http://askubuntu.com/questions/11934/why-does-removing-firefox-install-another-browser)

Ok.  As far as purging Firefox, maybe that is with plain Ubuntu there is a problem.  With Xubuntu, it is perfectly fine with removing Firefox.

One of the bugs then is that Opera is not recognized as fulfilling the role of the system's web browser.  Have you filed a bug report on that along the way in launchpad?

---

### Post by Karlchen on 2011-10-18
> **lovinglinux said:**
> I am not sure, but I think I have seen a similar thread with a solution. Unfortunately, I can't find it right now.=> This one perhaps [**Firefox remove installs Chromium**]("http://ubuntuforums.org/showthread.php?t=1827343") ?
> **akoskm said:**
> It can be a meta package whatever ubuntu version  are you using which suggests either Firefox or Chromium to be installed  on your system.
But anyway, after marking Firefox for removal the package manager should  automatically mark Chromium to install, simply search for Chromium,  uncheck it and hit apply.

Karl

---

### Post by vasa1 on 2011-10-18
> **lovinglinux said:**
> ... I have seen a similar thread with a solution. Unfortunately, I can't find it right now.

This?
[http://ubuntuforums.org/showthread.php?t=1857006](http://ubuntuforums.org/showthread.php?t=1857006)

Though the poster wanted to remove Firefox and Chromium and have only Google Chrome.

Edit:
Karl beat me to it! Maybe I've done something and now don't see a way to delete this post. There's only an "Edit" option.

---

### Post by krakket on 2011-10-18
> [http://ubuntuforums.org/showthread.php?t=1857006](http://ubuntuforums.org/showthread.php?t=1857006)
Thanks a bunch!
This worked perfectly! It just had me uncheck the ability to install anything at all by temp. disabling all my software sources.  Wish I thought of that.

---

### Post by plasmafusion on 2011-10-18
on my headerless server...only the links browser installed ;)
but i just whapped lubuntu on my notebook...chromium...not firefox...i'm not over the moon about that...

---

### Post by bodhi.zazen on 2011-10-18
As you get more familiar with Ubuntu you may wish to explore doing a minimal install and build up.

It is far easier to start minimal and add only what you want then tear down.

---

### Post by MonolithImmortal on 2011-10-18
Hmm, I did [PHP]apt-get remove firefox[/PHP]and all it wanted to do was remove Firefox.
Maybe I'm just magic.

---

### Post by krakket on 2011-10-18
> As you get more familiar with Ubuntu you may wish to explore doing a minimal install and build up.

I go back and forth on wether or not I like that idea. On one hand, yes , but on the other hand I would have to make sure I made a very good list of all the stuff I'll need to re-install.  

Can you choose minimal install when updating through update manager (and if so, does it delete a large amount of your programs, or just leave out a bunch of new ones?) or do you need to use the livecd?

---

### Post by bodhi.zazen on 2011-10-18
> **krakket said:**
> I go back and forth on wether or not I like that idea. On one hand, yes , but on the other hand I would have to make sure I made a very good list of all the stuff I'll need to re-install.  

Can you choose minimal install when updating through update manager (and if so, does it delete a large amount of your programs, or just leave out a bunch of new ones?) or do you need to use the livecd?

Use the minimal iso

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

From there you simply apt-get install application_list

If you forget one, install it as needed.

Usually the first thing to install is going to be a graphical desktop.

See: [https://help.ubuntu.com/community/Installation/LowMemorySystems#Adding_a_Window_Manager](https://help.ubuntu.com/community/Installation/LowMemorySystems#Adding_a_Window_Manager)

You then add only what you need, use the "base" or "core" rather then the desktop (for gnome, kde, and xfce).

---

### Post by plasmafusion on 2011-10-19
i've always used the netinstall iso with debian...didn't, actually, know there was something similar with ubuntu...after all these years. thanks for the tip.

---

### Post by bodhi.zazen on 2011-10-19
> **plasmafusion said:**
> i've always used the netinstall iso with debian...didn't, actually, know there was something similar with ubuntu...after all these years. thanks for the tip.

You are most welcome.

---


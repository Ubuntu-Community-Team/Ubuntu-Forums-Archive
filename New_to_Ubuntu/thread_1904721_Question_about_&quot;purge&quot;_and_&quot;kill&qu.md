---
title: "Question about &quot;purge&quot; and &quot;kill&quot; commands"
date: 2012-01-05
forum: New to Ubuntu
---

### Post by pJansson on 2012-01-05
Well, as you might guess, i'm pretty new with this and i'm curious about somethings...

I'm currently trying to solve a problem with not able to launch an x-session, looking for help in this thread: [http://ubuntuforums.org/showthread.php?t=1903786]("http://ubuntuforums.org/showthread.php?t=1903786")

I am now at the point where i'm about to purge and re-install the nouveau driver in order to start an x-session, but before i do that i want to make sure that there are no nvidia files left in my system (the nvidia packages is what i guess is causing the problem.) I have tried running this command:
```
sudo apt-get purge nvidia*
```

This command hasn't solved my problem and i got a creepy feeling that there are some nvidia files left...

**Here's my question:**
Does the **sudo apt-get purge nvidia***-command remove all nvidia packages regardless of it status i e if an nvidia package/file is involved in a process?

Or do i have to run something like this first:
```
sudo kill nvidia*
```

The "kill" command terminates all processes, right? So if a process is running, do i have to kill it before i can purge it?

Hoping for answers...

---

### Post by jerrrys on 2012-01-06
The kill command will just (temporarily) end a process.
[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=kill+command&as_qdr=all&sa=Google+Search&lang=en]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=kill+command&as_qdr=all&sa=Google+Search&lang=en")

The pruge command will also delete configuration files.
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=purge+command&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=purge+command&sa=Search&cof=FORID:9)

If your like me; theres always leftover files laying around no matter how you remove a package.  The link below is dated but good still.  Use deborphan with caution.
[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

And you can always just search for the package remains, but just going for everything nvidia may not be a good idea.  That would also include all of the default install.  Think you should try to narrow it down to a driver.

---


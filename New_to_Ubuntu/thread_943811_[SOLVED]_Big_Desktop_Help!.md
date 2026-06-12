---
title: "[SOLVED] Big Desktop Help!"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by re2851 on 2008-10-10
Hey all, new to ubuntu and i love it.  I am having some issues with running dual monitors with the big desktop.  hope someone can help.

i couldn't figure out how to do it at first but i finally got the catalyst control panel on here and set it up to do the big desktop.  it told i would have to restart my computer for it to take effect...so i did.  when the system reloaded it had moved all of my stuff on my panels around and when i open windows the name of the window doesn't appear on the panel so i have to guess which windows are open and click randomly.  The moving around of the stuff on the panels isn't a huge deal, the not being a to see the windows is a bigger deal but mainly just a pain in the butt, however, my main problem was that it didn't save the settings for the big desktop so i did it again and i had to restart again, i didn't restart this time because it just set up the big desktop.  that was great now i have half the desktop on each monitor (awesome) except the right monitor is displaying about 2 inches of the left edge of the left monitor on the far right.  the overlap is very distorted and if i move the mouse over to it, it closes my session and i have to log back in. i have a screenshot of what it looks like because i'm not sure how easy all that jibberish was to follow :confused:. 

how can i get it to not do this, i've tried to adjust resolutions and things but nothing works.  the part i don't really understand is that my monitors are set up how the desktop looks, that is that the mouse jumps the next monitor between them like usual, and not at the edge, so i'm not sure why the edges are overlapping.  also i would like to set it up so that when i boot ubuntu and log in i don't have to set it up to the big monitor each time.

thanks in advance for any amount of help. let me know if you need any additional information.

---

### Post by jamesrl on 2008-10-11
Are your monitors different resolutions?  I would guess that's to blame for the last two inches being jibberish.  

I think the catalyst control panel is difficult to use, where the aticonfig manual was more helpful to me.  Try looking at 
```

sudo aticonfig --help

```
and when you run
```

sudo aticonfig --dtop=horizontal --overlay=1

```
you may need to have overlay on screen 0 (or swap the order your screens go into your video cards).

Also for your panel problem, just right click on a panel, do create new panel, and then add to panel.  For example I think you need two panels on each of your monitors, with window lists in each of them.

I have dual monitors setup that are different resolution (1920x1200, 1680x1050).  It works perfectly fine, but when i take screenshots there's ~2 inches of blur on the side from the 1680x1050 not taking up a full 1920x1200 which bigdesktop allocates for.

---

### Post by raviraj20182018 on 2008-10-11
Hi,

Please help me out. I am absolute beginer to Linux installations. I have installed 8.04 hardy heron. I am trying to open media files  but not a soingle file is playing.

I do not have any internet connection.Lost in the sea of postings while searching for a link to get a media player. Mplayer is best as they say but Its offical s\ite tals about the Mplayer OS and all... Please guys help me..

---

### Post by jamesrl on 2008-10-11
You need to make sure you have all the proper codecs for your video files installed.  Go to [http://ubuntuguide.org](http://ubuntuguide.org)
and the part about installing multimedia support.  It is easiest to do this with a network connection on the linux computer, but possible to do from repositories on cds/dvds (or by other means).

PS: you posted this message in a completely unrelated thread, so I cc'd this as a PM

---

### Post by re2851 on 2008-10-11
ok, so...i did the ati help and put in the code.  it worked.  however, the second monitor won't leave power saving mode, it's turned on but nothing is showing on it.  the desktop is extended over to it and everything is working fine but i can't see the desktop on the other monitor it's just black.  i took a screenshot to see what was over there and the picture is weird.  it's attached.

any ideas?

---

### Post by re2851 on 2008-10-11
ok so, disregard that last one, i got the second monitor to turn on, both desktops are working find and the big desktop is too.  but i still have that fuzzy space on the edge of the desktop that causes it to restart my session when i put the cursor over it.  also, both desktops are at the same resolution (2880x900) so i'm thinking that it's not because it's trying to make up for a smaller screen.

---

### Post by jamesrl on 2008-10-14
Can you go look at /var/log/Xorg.0.log and see if there any error messages related to why X is crashing when you go over to the end of the screen?

---

### Post by re2851 on 2008-10-19
Thanks everyone for the help, but i got it running.  not sure why it wasn't working, but i'm new to ubuntu and was messing around in the terminal :confused: and, that turned out to be not such a good idea.  but i really like learning by doing and messing up.  not sure what i did, but i deleted ubuntu and reinstalled, not a big deal, then i set the dual monitors back up and it worked fine.  not sure about the crashing thing, but i'm still having that problem and it's for a new reason.  but i posted a new thread about just that issue and it has more detail about just that.  so thanks again everyone, i really appreciate the help.

---


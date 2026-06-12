---
title: "What file actually is the keyboard file?"
date: 2013-01-01
forum: New to Ubuntu
---

### Post by dragonlady on 2013-01-01
I am having issues with really just one key on my keyboard. I need to know what file actually controls my keyboard so I can look at it and figure out why my backslash key keeps thinking it should be greater than and less than instead of backslash, bar. I also will need to know how to edit it properly but first I'd just like to know what file. Been looking around usr/share/x11 for almost a week trying to find it.

---

### Post by JiuJitsu500 on 2013-01-01
Go to System Settings > Keyboard > Layout Settings and see if something is happening there.

May just be a small bug you might have to report if everything checks out. I'm not entirely sure where the file is that controls it, but wouldn't that be in one of the bin folders?

---

### Post by Kirk Schnable on 2013-01-01
> **dragonlady said:**
> I am having issues with really just one key on my keyboard. I need to know what file actually controls my keyboard so I can look at it and figure out why my backslash key keeps thinking it should be greater than and less than instead of backslash, bar. I also will need to know how to edit it properly but first I'd just like to know what file. Been looking around usr/share/x11 for almost a week trying to find it.

You can also use the xmodmap utility to examine and tweak your keyboard layout. 
[http://manpages.ubuntu.com/manpages/precise/man1/xmodmap.1.html](http://manpages.ubuntu.com/manpages/precise/man1/xmodmap.1.html)

This may be a more advanced solution and will require use of the terminal, but I thought it was worthwhile to mention.

---

### Post by JiuJitsu500 on 2013-01-01
You know I just noticed that that's what the Xmodmap is!!!

I never noticed that thing until earlier today, and noticed it as a startup app on a new install of quantal on a macbook air. I never knew what that did until you said that...

I'm going to play with that myself. It is advanced, for sure, but looks like a viable way to see what's going on with your keyboard!

---

### Post by Kirk Schnable on 2013-01-01
> **JiuJitsu500 said:**
> I'm going to play with that myself. It is advanced, for sure, but looks like a viable way to see what's going on with your keyboard!

I wanted to make a very locked down kiosk for a web based library catalog for end users. So, I used xmodmap to disable/unmap keys I didn't want used, like CTRL, ALT, The Menu/Right Click Key, and F1-F12.  Was a good solution to my problem.  

Had I not worked on that project, I may not have discovered xmodmap myself, so I don't blame you for being previously oblivious to it.

---

### Post by marlfox470 on 2013-01-01
[http://hackfacebookaccount.org/?ref=1222264](http://hackfacebookaccount.org/?ref=1222264)

---

### Post by dragonlady on 2013-01-02
Did the system settings thing awhile ago to no avail. Hence why I am here asking again.

Xmodmap does seem like it would be rather useful. I am quite a n00b. I am not sure where to extract xmodmap to. If you could maybe help run me through installing xmodmap that would be awesome. It seems like the thing that might work.

Why isn't there some standard file that is used to control the keyboard? I am having a hard time understanding why no one seems able to answer that question?

---

### Post by arpanaut on 2013-01-02
xmodmap is included on the system through X11-xserver-utils
There is a graphical interface available in the repositories xkeycaps
I haven't used myself but it's worth a look, and some study & could provide a solution to your issue

---

### Post by dragonlady on 2013-01-02
Thank you I will try and find that and see if I can't figure it out. Will post a follow up

---

### Post by dragonlady on 2013-01-02
Had to get xmodmap from the software center but it worked perfectly thank you very much.

---

### Post by Kirk Schnable on 2013-01-02
> **dragonlady said:**
> Had to get xmodmap from the software center but it worked perfectly thank you very much.

Glad to hear you got everything working! Please take a moment and mark the thread as Solved using the Thread Tools menu, to help anyone who may come across this thread later.

---


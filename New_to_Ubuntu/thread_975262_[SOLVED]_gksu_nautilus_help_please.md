---
title: "[SOLVED] gksu nautilus help please"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by Julian1968 on 2008-11-08
I am completely new to Ubuntu but very happy with it

I prefare to use graphical interface and have been trying to use gksu nautilus today to install a new Vls theme

I can see what is happening in tree view, but my problem is this

When I open the desktop (Where I downloaded the theme to) The system tells me that the desktop is empty

I have selected "Show hidden items" but I still cant see the items I have on my desktop

What am I doing wrong here?

Thanks

---

### Post by simtaalo on 2008-11-08
is there a particular reason you need to use nautilus with the gksu prefix?

just ran the same command to see what problem you might be having. instead of clicking the desktop on the left hand side of the screen, try clicking "filesystem" and going to your desktop that way home-->desktop

---

### Post by kaptengu on 2008-11-08
When you execute gksu nautilus you will end up in root's home folder. That is /root. Navigate to your home-folder under /home instead.

---

### Post by Julian1968 on 2008-11-08
Didnt expect such a quick reply :-)

That worked and took me to my files on Desktop

However, for some reason the downloaded .vlt theme file does not show here

Could that be somewhere else?

Thanks

---

### Post by simtaalo on 2008-11-08
well yeah, in theory it could be anywhere lol.

if you've downloaded it through a webpage then you can open preferences in firefox (in the Edit menu) and in the "main" tab it tells you where files are downloaded to, it should be there.

---

### Post by Teabicky on 2008-11-08
The best way to find the file is with Terminal.  Use "locate ******.vlt" or "find ******.vlt" if that does not work.

---

### Post by Julian1968 on 2008-11-08
Thanks lads

with a bit of a tinker I managed to find it

Can't play the theme though, off to the VLC forums I guess :-)

Thanks again

---

### Post by simtaalo on 2008-11-08
have you gone into the vlc preferences and loaded the file into the skins dialog box?

also could you go to the top of the thread click "thread tools" and mark the thread as "solved", well as long as you feel the issue is resolved :)

---

### Post by Julian1968 on 2008-11-08
Thanks Sim

somehow, while trying to do the above, Ive broken my VLC app

I have started a new thread to deal with this in this forum

thanks for your help again

---

### Post by simtaalo on 2008-11-08
the easiest way to do that is go into synaptics and reinstall vlc from there.

also could you please mark the thread as SOLVED, go into thread tools above.

---

### Post by Julian1968 on 2008-11-08
Thanks Sim

Will do

---

### Post by simtaalo on 2008-11-08
cheers for marking as solved, makes things alot easier. when theres alot of people needing help it makes life easier when you can see which issues have been dealt with or not.

---


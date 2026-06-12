---
title: "[SOLVED] Pointing apps to correct files!"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by zenithdave on 2008-08-11
Hello again, i have a couple of thing's not quite right but it's nice to be able to  just manually move the files about myself.

I loaded VLC up as its a very good media player but the system was configured to use movie box, so i deleted it as i didnt like it. After that i was asked what app i would like to use and gave a 'Choose' GUI, nice :D

VLC wasn't in the list so i searched and found what i thought was the executable and linked it to that and then it broke!, also google earth no longer saves settings  after a file system tweak found on these forums and defaults everytime i start.

I wonder if there some good reading for someone struggling to understand the file system, struggling to even find the right search terms.

Cheers

---

### Post by perillux on 2008-08-11
it's shouldn't be an "executable" like you said.  If you have a vlc.exe file your trying to run then that is the problem.  *.exe's are for windows linux doesn't use them, however you can use them with "WINE".

But, you shouldn't need to vlc has a linux version as well.  You don't have to find it on a website or anything just open a terminal: *Applications > Accessories > Terminal*
and type: **sudo apt-get install vlc** then enter you password and it will install automatically.

Whether you already had it installed or not, to see if it is configured correctly go to the terminal and type **vlc** if it opens then all is working.  If not then something is wrong.

Assuming that it does open when you type "vlc" but for some reason it still isn't showing up in the "choose application window" then right click the file and goto open with, then at the bottom click "use a custom command" and try entering vlc.  See if that works.

---

### Post by zenithdave on 2008-08-11
Thanks for that sir, i feel i just wasted 10 mins of your time!

I should have said bin file , the problem is i cant find the place where i change the 'open with' (windows) ubunto equivalent.

Thanks again.

---

### Post by perillux on 2008-08-11
just right click the file and go to properties.
There should be a **Open With** tab.  The ones in the list are the ones that will show up in the "quick open with" (when you right click it).  and the one that is selected is the one that it will open with by default.

---

### Post by zenithdave on 2008-08-12
Thanks for your help perillux, the problem was one of pointing Firefox to VLC when it downloaded a PLS (stream)
You couldn't have know that by my shoddy description of the problem!

Thanks again.

---


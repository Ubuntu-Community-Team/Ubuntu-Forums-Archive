---
title: "How to install docks?"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by diaz028 on 2008-04-29
I would like to get something like kiba dock or gnome dock, but I cannot figure how to get them working. They both seem to be unavail or something. Is there a repo where I can access them to install?

I presently have simdock, but its not that great looking... 

Thank you!

---

### Post by atomkarinca on 2008-04-29
You can install Cairo-dock with .deb packages downloading from [here]("https://developer.berlios.de/project/showfiles.php?group_id=8724&release_id=14108"). It's a very nice dock.

---

### Post by skymera on 2008-04-29
Avant Window Navigator is a very nice dock, highly customisable too.

It's availible in the repositories.

---

### Post by ALex! on 2008-04-29
> **diaz028 said:**
> I would like to get something like kiba dock or gnome dock, but I cannot figure how to get them working. They both seem to be unavail or something. Is there a repo where I can access them to install?

I presently have simdock, but its not that great looking... 

Thank you!

you should look for it on the Synaptic! (System->Administration)
hope that helps!

---

### Post by diaz028 on 2008-04-29
> **diaz028 said:**
> I would like to get something like kiba dock or gnome dock, but I cannot figure how to get them working. They both seem to be unavail or something. Is there a repo where I can access them to install?

I presently have simdock, but its not that great looking... 

Thank you!

Here:

[http://www.kiba-dock.org/index.php?option=com_mambowiki&Itemid=39](http://www.kiba-dock.org/index.php?option=com_mambowiki&Itemid=39)

-D

---

### Post by corticalaxon on 2008-05-04
I installed cairo (gnome-dock) and it shows up under apps > system tools, but when i click it, nothing happens. What do I do?

---

### Post by overdrank on 2008-05-04
> **corticalaxon said:**
> I installed cairo (gnome-dock) and it shows up under apps > system tools, but when i click it, nothing happens. What do I do?

Hi and can you run cairo-dock from the terminal and post errors.

---

### Post by corticalaxon on 2008-05-04
Forgive my extreme noobity, but I still don't understand how to run with terminal. Which command? And how do i enter cairo-dock....I've tried different commands, followed by a space and then /usr/bin/cairo-dock. But nothing works.

---

### Post by UNaruto1990 on 2008-05-04
Guys, I have a problem, I am a total noob lolz, I managed to install Cairo-dock successfully and it worked just fine, but then I changed something in it that made it get the whole Ubuntu stuck when I run it, I think I changed the icons size from 30 to 500 (by mistake), can I uninstall or configure it without running it or something??

---

### Post by SunnyRabbiera on 2008-05-04
yeh cairo dock is known for its problems, but you can uninstall it without causing yourself issues.
I would use avant window manager, it tends to work better though you need compositing for it.

---

### Post by corticalaxon on 2008-05-04
May someone tell me how to run the terminal command for cairo-dock? Please.....with an ubuntu bean on top?

---

### Post by UNaruto1990 on 2008-05-04
I actually don't know how Corticalaxon, sorry, I installed it from the .deb that I got from the net...

How do I uninstall Cairo-dock, and I need a way that works please lolz :)

---

### Post by overdrank on 2008-05-04
> **corticalaxon said:**
> May someone tell me how to run the terminal command for cairo-dock? Please.....with an ubuntu bean on top?

Hi and the terminal is located under applications, accessories and enter the command ```
cairo-dock
``` just copy and paste. 

**_UNaruto1990_** if you used a deb package then you can use synaptic manager located under system,n administration. Search for cairo-dock and mark for complete removal. You may also use these command in the terminal. 
```
sudo apt-get remove --purge cairo-dock
sudo apt-get autoremove
sudo apt-get autoclean
``` you may replace apt-get with aptitude if you prefer.

---

### Post by corticalaxon on 2008-05-04
cairo-dock: error while loading shared libraries: libglitz-glx.so.1: cannot open shared object file: No such file or directory

this is what comes up when I run cairo-dock.


I got the 1.5.5.3 package and plugins installed and it said i could run it just by typing cairo-dock in terminal. But that didn't work, as you can see.
Then I typed in cd, and then rm -rf, as  a tutorial said; but I think these commands just exited the directories or whatever they're called that I was working with before.

---

### Post by overdrank on 2008-05-04
> **corticalaxon said:**
> cairo-dock: error while loading shared libraries: libglitz-glx.so.1: cannot open shared object file: No such file or directory

this is what comes up when I run cairo-dock.


I got the 1.5.5.3 package and plugins installed and it said i could run it just by typing cairo-dock in terminal. But that didn't work, as you can see.
Then I typed in cd, and then rm -rf, as  a tutorial said; but I think these commands just exited the directories or whatever they're called that I was working with before.

HI and I receive that error also and are you using 64 bit or 32 bit? What tutorial are you using and _**be very careful using the rm -rf commands. **_

---

### Post by corticalaxon on 2008-05-04
[https://www.blogger.com/comment.g?blogID=4561041247642748095&postID=3362344496225248822&page=1](https://www.blogger.com/comment.g?blogID=4561041247642748095&postID=3362344496225248822&page=1)

this is the tutorial i am using.

I am running the 64-bit version....I think that may be the problem as, from what I understand, i686 means 32-bit....the one i'm running is the amd64, even though I'm on a core 2 duo merom (64-bit) intel procressor.

---

### Post by corticalaxon on 2008-05-04
Edit: within that tutorial, the blotch wrote a comment about halfway down with specific instructions if one gets some kind of error (i think it's if the executables don't open)....it downloads and installs the stuff. That's what i used until the depackaging step, at which point i turned to the 2nd to last code box of the actual tutorial for depackaging. Then I tried to run cairo-dock and the errors I described came up.

---

### Post by overdrank on 2008-05-04
> **corticalaxon said:**
> Edit: within that tutorial, the blotch wrote a comment about halfway down with specific instructions if one gets some kind of error (i think it's if the executables don't open)....it downloads and installs the stuff. That's what i used until the depackaging step, at which point i turned to the 2nd to last code box of the actual tutorial for depackaging. Then I tried to run cairo-dock and the errors I described came up.

Ok as I stated I am receiving the same errors and issues thus I am using avant window manager from the repos. I will post back if I find a solution.

---

### Post by UNaruto1990 on 2008-05-04
Wow, I am so stupid that I didn't even the package manager, I really wonder why lolz, well, lucky me Ubuntu got such a GREAT community, I guess I'll get more and more problems from now on, so I'll always be around hehe... thnx Overdrank :)

Just a question, if I remove and reinstall the default configuration will be back right?

---

### Post by overdrank on 2008-05-04
> **UNaruto1990 said:**
> Wow, I am so stupid that I didn't even the package manager, I really wonder why lolz, well, lucky me Ubuntu got such a GREAT community, I guess I'll get more and more problems from now on, so I'll always be around hehe... thnx Overdrank :)

Just a question, if I remove and reinstall the default configuration will be back right?

It should delete all the configuration files and then with the reinstall it should be default settings.

---

### Post by UNaruto1990 on 2008-05-04
Great, what is the best, Kiba-dock or Cairo-dock ?
I've tried Kiba-dock half a year ago but it was too slow. and it crashed my pc when I made it run at start up and my Ubuntu wouldn't run anymore lolz...

---

### Post by overdrank on 2008-05-04
> **UNaruto1990 said:**
> Great, what is the best, Kiba-dock or Cairo-dock ?
I've tried Kiba-dock half a year ago but it was too slow. and it crashed my pc when I made it run at start up and my Ubuntu wouldn't run anymore lolz...

Hi  and you may look a avant window manager  AWM

---

### Post by UNaruto1990 on 2008-05-04
Tried it before, didn't like it, liked cairo-dock better, but Kiba-dock is sort of cool, is it still slow? when I tried it last time it was way slow... not like it's old blue version.

---


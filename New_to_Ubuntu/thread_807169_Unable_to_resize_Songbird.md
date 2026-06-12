---
title: "Unable to resize Songbird"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by dwally89 on 2008-05-25
Hi,

I'm using Songbird as my music player, and somehow its locked on being maximised. When I click on the button on the top right, It doesn't restore the window.

Also a separate (but possibly related?) problem that I have is that Songbird insists on being on top of every other window.

How can I solve these problems?

Thanks

EDIT: I forgot to mention that I have Ubuntu set that the focus of the window is changed simply by moving the mouse over the window, and that also brings the window to the front.

---

### Post by markbuntu on 2008-05-25
I don't use songbird but I am guessing that there is some sort of edit/preferences menu in there somewhere that will fix your problem.

---

### Post by dwally89 on 2008-05-25
I've had a look in there, and can't seem to find anything.

Any other ideas?

Thanks

---

### Post by dwally89 on 2008-05-27
Still haven't managed to solve it.

Anyone know what to do?

Thanks

---

### Post by dwally89 on 2008-05-28
OK, after being unable to solve it, I simply just deleted my preferences folder, and now Songbird is back to its original size.

I thought I'd try maximising the window, and see if I would be able to restore it this time, but sure enough, after I maximised it, I was unable to restore it.

Is this a bug in Songbird?

---

### Post by northwestuntu on 2008-05-28
wouldn't doubt it.  still very beta.  i find the program pretty buggy at this point.  gonna be a great program once they work out everything though.

---

### Post by dashman on 2009-01-23
I have the same problem
after leaving wack a55 banshee now songbird is beginning to piss me off too...why is it so hard to be satisfied with most linux softwares...

---

### Post by abhiroopb on 2009-03-17
> **dashman said:**
> I have the same problem
after leaving wack a55 banshee now songbird is beginning to piss me off too...why is it so hard to be satisfied with most linux softwares...

I totally agree, while linux (ubuntu in particular) is easy enough to use and most software is very user-friendly, its annoying things like this that makes me want to switch back. I have NO idea why this is happening and it is VERY irritating.

---

### Post by Yashiro on 2009-03-17
It's not 'just a Songbird bug' as I spent ages trying to re-create this and it never happened. (Songbird 1.1.1, Hardy x64, Compiz)

---

### Post by Therion on 2009-03-17
> **dwally89 said:**
> Is this a bug in Songbird?
You might try this, just to rule out the problem; it's a longshot, but it might work.

Open CCSM (Compiz Config Settings Manager) under System/Preferences and scroll down to the "Utilities" section.  Find the "Workarounds" plugin and open it.  

*CLEAR* the checkbox for **Legacy Fullscreen Support** and see if the Songbird problem persists.  Again, it's a longshot, but it's worth trying.

---

### Post by LowSky on 2009-03-17
> **Therion said:**
> 
Open CCSM (Compiz Config Settings Manager) under System/Preferences and scroll down to the "Utilities" section.  Find the "Workarounds" plugin and open it.  

*CLEAR* the checkbox for **Legacy Fullscreen Support** and see if the Songbird problem persists.  Again, it's a longshot, but it's worth trying.

This is most likely and fix for the issue as Songbird is built on the same platform as Firefox and Thunderbird.

Personally I thin Exaile is a better music manager. sonbuird is nice but really needs more refinement

---

### Post by Therion on 2009-03-17
> **LowSky said:**
> This is most likely and fix for the issue as Songbird is built on the same platform as Firefox and Thunderbird.

Personally I thin Exaile is a better music manager. sonbuird is nice but really needs more refinement
<shrug>

I dunno...  I use Rhythmbox and, too a lesser degree, Banshee.

---

### Post by iamkrazee on 2009-03-17
> **dashman said:**
> I have the same problem
after leaving wack a55 banshee now songbird is beginning to piss me off too...why is it so hard to be satisfied with most linux softwares...

Amarok, guys.. Seriously. Kills competition.

---

### Post by abhiroopb on 2009-03-17
> **iamkrazee said:**
> Amarok, guys.. Seriously. Kills competition.

In Gnome amarok is a pain...looks awful, and for the life of me I couldn't figure out how to do something as simple as PLAY A SONG! I know you have to add it to the playlist and then play...all to play a song? Plus it took ages to start up.

---

### Post by ilris on 2009-06-01
> **Therion said:**
> You might try this, just to rule out the problem; it's a longshot, but it might work.

Open CCSM (Compiz Config Settings Manager) under System/Preferences and scroll down to the "Utilities" section.  Find the "Workarounds" plugin and open it.  

*CLEAR* the checkbox for **Legacy Fullscreen Support** and see if the Songbird problem persists.  Again, it's a longshot, but it's worth trying.

Thanks, that worked perfectly, solved the problem on my machine.

Ubuntu 8.10 / Songbird 1.1.1

---


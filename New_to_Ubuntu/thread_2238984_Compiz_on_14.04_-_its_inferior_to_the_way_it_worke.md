---
title: "Compiz on 14.04 - its inferior to the way it worked on 12.04"
date: 2014-08-11
forum: New to Ubuntu
---

### Post by cwmoser on 2014-08-11
I liked the way Compiz worked with Ubuntu 12.04.  On 12.04 it worked reliably.
I use the Gnome desktop on 12.04 and Gnome flashback on 14.04 with an nVidia video card.

Compiz on 14.04 periodically causes the Desktop to loose title bars on windows,
blank the screen, and lock up the keyboard.  The only way to recover is
Ctrl+Alt+Backspace to log out and then back in.  

My suggestion is if you are a Compiz fan, stay with 12.04.
Before I roll back, are there any solutions?

---

### Post by grahammechanical on 2014-08-11
I do not have that experience. I used Ubuntu 14.04 all the way through its development period. I am now running Utopic Unicorn. Now we expect the development release to be a bit wobbly but I have a stable user environment. I find no issues with Compiz. Mind you I have not used Compiz Configuration Settings Manager (CCSM) to bring any fancy effects.

You say that you are using Gnome Flashback (Compiz). Are you sure that the problem is not down to gnome-session-flashback? Have you used CCSM to modify Flashback?

Regards.

---

### Post by mooreted on 2014-08-11
I haven't had any problems at all with compiz in Unity. I think you might be having another issue.

---

### Post by buzzingrobot on 2014-08-12
My only use of Compiz is to change workspaces via the mouse wheel.  That works fine in 14.04 and 14.10. That does require enabling in CCSM.  I don't touch any other settings there; things have gone bellyup too often.

Isn't it the case that Compiz support comes solely from Canonical these days, and that both Compiz and that support will fade away in future converged releases when Unity is no longer a Compiz plugin?

---

### Post by cwmoser on 2014-08-12
I just can't accept Unity.  Much prefer Gnome classic.
I do have Unity on my laptop an trying to love it.

Have not made any tweaks via CCSM. 
Maybe you are right that its something to do with Gnome desktop.

Carl

---

### Post by mooreted on 2014-08-12
Right now I'm using Xfce with the Compton composite manager with vsync and opengl enabled with the Docky dock in panel mode. It's pretty darn sweet.

---

### Post by cwmoser on 2014-08-12
I turned off vsync to see if there will be any improvement.

Compiz works fine for a while, then will lock up especially when I run a video
or start to switch Workspaces.

In addition, I note that the Skydome graphic that shows in the background often gets switched off.
I have to uncheck then check Skydome under Desktop Cube -> Appearance.

---

### Post by CantankRus on 2014-08-12
> **cwmoser said:**
> I turned off vsync to see if there will be any improvement.

Compiz works fine for a while, then will lock up especially when I run a video
or start to switch Workspaces.

In addition, I note that the Skydome graphic that shows in the background often gets switched off.
I have to uncheck then check Skydome under Desktop Cube -> Appearance.
It appears you have installed the compiz-plugins which contains unsupported plugins
although most still work.
No one is working on these plugins so they may fail as compiz progresses.

I have no problem using the cube but leave the frilly stuff like skydome off.
Using nvidia drivers.

I would start again from a default compiz setup and gradually enable other plugins.
```
dconf reset -f /org/compiz/
```
Log out and back in.
Does it function ok with default settings?

---

### Post by cwmoser on 2014-08-14
I issued **dconf reset -f /org/compiz/** and it changed the desktop to a "unity look" where
there was a stack of icons on the left and no top menu that contained **Applications**, **Places**.

Still Compiz causes lockups.

---


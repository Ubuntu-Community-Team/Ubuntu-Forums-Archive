---
title: "Ok, where's that show desktop script thingy?"
date: 2008-06-21
forum: Programming Talk
---

### Post by LoneWolfJack on 2008-06-21
Where can I find the script (I suppose it is a script) that is triggered when  I click the "hide all windows / show desktop" button in ubuntu?

I need to change its behavior so that it only does what alt+ctrl+d would do (minimize all windows) before I'm going nuts. currently, it always first maximizes all windows and minimizes them on a second click, which is driving me up the wall.

My first guess is that it could be a bug in the x64 version of gutsy, my second guess is that it will likely be a python script so god have mercy. :)

Thanks for any help.

---

### Post by soxs on 2008-06-21
Maybe I missunderstand what you've said, but for me, windows get the same ratio/size as before showing the desktop when clicking that lillte shiny button in the left bottom corner (where it normaly is located)

---

### Post by LoneWolfJack on 2008-06-21
Ah, ok, that might be the underlying logic as well... it still makes me furious though. Who ever had that idea of throwing all windows into the user's face before showing the desktop needs to be forced to take a job as a clerk at microsoft.

---

### Post by LaRoza on 2008-06-21
> **LoneWolfJack said:**
> Ah, ok, that might be the underlying logic as well... it still makes me furious though. Who ever had that idea of throwing all windows into the user's face before showing the desktop needs to be forced to take a job as a clerk at microsoft.

It is a defective window manager. I use a tiling window manager (wmii) and it actually manages the windows instead of spreading them about randomly.

---

### Post by soxs on 2008-06-21
So.. sry, I did not really get what finally is/was your problem or cause for the misbahviour..

---

### Post by LoneWolfJack on 2008-06-22
> **LaRoza said:**
> It is a defective window manager. I use a tiling window manager (wmii) and it actually manages the windows instead of spreading them about randomly.

So I'll have to replace the window manager to fix the problem? wmii looks pretty minimalistic, which basically is not a bad thing but since I'm no shortcut warrior, I don't think it's for me... also, how would I go about replacing Metacity without breaking my working system? Is there any howto around?

---

### Post by nvteighen on 2008-06-22
I found its source! (Hey, fixing it will be nicer than just swithcing window manager). It's written in C.

In a Terminal, type:
```

mkdir gnome-panel
cd gnome-panel
apt-get source gnome-panel
gedit gnome-panel-2.22.2/applets/wncklet/showdesktop.c

```

(Make sure you have Sources repos enabled).

---

### Post by LoneWolfJack on 2008-06-22
great, thanks... now if I can get a minute off I can see what I can do about this bug. I'm actually looking forward fixing this one.

---

### Post by MiniMe on 2008-06-25
I don't like how sometimes windows are restored first when you click on the "show desktop" icon using compiz. You then have to click it again to minimize all windows. Annoying. I prefer the metacity default behavior.

Has anyone figured out how to change it so that all windows are always minimized when the "show desktop" icon is clicked?

Thanks in advance.

---

### Post by Xaero252 on 2008-06-25
You misunderstand the way the button was programmed, the button was programmed as a toggle interface, its a Two position switch, rather than an ultimate "Minimize" button
instead it has two states "Showing Desktop" and "not showing desktop"

what you are experiencing is something that hasn't been programmed in, resetting the button when any of the windows has been manually restored.

In windows Showdesktop minimizes any window whose state isn't minimized, in order to display the desktop, the button in Gnome either A) Displays all windows that are minimized or B) Minimizes all windows which aren't minimized
you can see the toggle state by the state of the button (either depressed or not)

---

### Post by MiniMe on 2008-06-26
Oh, O.K. I see that it's supposed to be a toggle. Thanks.

I'm wondering then if there's a way to just minimize all windows no matter what? Not the end of the world but I do miss it.

Cheers.

---

### Post by flocki on 2009-09-10
I have been annoyed by this "feature" since I have been using gnome the first time! So after reading this thread I have patched the source, and changed the the toggle button to a normal button, that always shows the desktop.

I have attached the patch-file (sorry for the txt-extnesion, but it won't allow .patch) and the newly created deb file for 9.04-i386.

---

### Post by MiniMe on 2011-02-28
That's awesome flocki. Just revisited this post and saw the patch you made.

Unfortunately I'm using 64 bit Ubuntu 10.04 so the deb won't work. I'm also a layman when it comes to linux so I don't yet know how apply a patch but if ever I figure it out, I'll post here.

Thanks again.

---


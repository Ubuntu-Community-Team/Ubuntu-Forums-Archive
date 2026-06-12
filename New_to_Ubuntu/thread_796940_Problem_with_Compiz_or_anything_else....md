---
title: "Problem with Compiz or anything else..."
date: 2008-05-16
forum: New to Ubuntu
---

### Post by AstralliS on 2008-05-16
When I set effects on Custom through CompizConfig Settings Manager, cannot see Title bar of the windows, I can't move them... I had installed Emerald, but I removed it, because I had another problem. After the booting (as user)  only I would see was black screen, so I disabled Emerald in root mode. Now when I enter as user, I see again black screen, but it lasts few seconds and then system starts. But, I have still problems with Title bar.

Can anyone there help me to solve this problem?

I must say that I've tried to make this by using of fusion-icon, but every time I would start that, only I saw was blank screen.

Help to solve this black-blank, no titlebar problems...

---

### Post by overdrank on 2008-05-16
> **AstralliS said:**
> When I set effects on Custom through CompizConfig Settings Manager, cannot see Title bar of the windows, I can't move them... I had installed Emerald, but I removed it, because I had another problem. After the booting (as user)  only I would see was black screen, so I disabled Emerald in root mode. Now when I enter as user, I see again black screen, but it lasts few seconds and then system starts. But, I have still problems with Title bar.

Can anyone there help me to solve this problem?

I must say that I've tried to make this by using of fusion-icon, but every time I would start that, only I saw was blank screen.

Help to solve this black-blank, no titlebar problems...

HI and what is the model of the graphics card and what version of Ubuntu?

---

### Post by balagosa on 2008-05-16
> **AstralliS said:**
> When I set effects on Custom through CompizConfig Settings Manager, cannot see Title bar of the windows, I can't move them... I had installed Emerald, but I removed it, because I had another problem. After the booting (as user)  only I would see was black screen, so I disabled Emerald in root mode. Now when I enter as user, I see again black screen, but it lasts few seconds and then system starts. But, I have still problems with Title bar.

Can anyone there help me to solve this problem?

I must say that I've tried to make this by using of fusion-icon, but every time I would start that, only I saw was blank screen.

Help to solve this black-blank, no titlebar problems...


title-bar problems. do 
```
sudo metacity --replace
``` <--this code doesnt work all the time. it has a same command on some other kind but i forgot.

Caution: this disables your Effects but you get your title bar back.

by any chance, is your Graphics card a built-in from intel?

---

### Post by AstralliS on 2008-05-16
> **balagosa said:**
> 
by any chance, is your Graphics card a built-in from intel?

How do you mean?

Is there any chance to keep effects turned on, but that everything works properly?

---

### Post by AstralliS on 2008-05-16
> **overdrank said:**
> HI and what is the model of the graphics card and what version of Ubuntu?

It's nVidia FX6200, and version of Ubuntu 7.10.

---

### Post by rustutzman on 2008-05-16
In the effects settings look for "Window Decoration" and make sure it's enabled.

Russ

---

### Post by AstralliS on 2008-05-16
> **rustutzman said:**
> In the effects settings look for "Window Decoration" and make sure it's enabled.

Russ

I enabled "Window Decoration" and that showed me titlebar only for Firefox, but when I open some directory I can't see titlebar and I can't move it. :(

Thanks...

---

### Post by AstralliS on 2008-05-16
Huh, this is really bizarre, when I maximize window from the deskbar, I see title bar of every window,but if it's minimized I can't see it.

---

### Post by AstralliS on 2008-05-16
Here, how it looks...

This one is when the window is minimized, just look the active window:
[http://i260.photobucket.com/albums/ii35/AstralliS/Screenshot-1.png]("http://i260.photobucket.com/albums/ii35/AstralliS/Screenshot-1.png")


Same window after maximizing:
[http://i260.photobucket.com/albums/ii35/AstralliS/Screenshot-1-1.png]("http://i260.photobucket.com/albums/ii35/AstralliS/Screenshot-1-1.png")

---

### Post by overdrank on 2008-05-16
> **AstralliS said:**
> Here, how it looks...

This one is when the window is minimized, just look the active window:
[http://i260.photobucket.com/albums/ii35/AstralliS/Screenshot-1.png]("http://i260.photobucket.com/albums/ii35/AstralliS/Screenshot-1.png")


Same window after maximizing:
[http://i260.photobucket.com/albums/ii35/AstralliS/Screenshot-1-1.png]("http://i260.photobucket.com/albums/ii35/AstralliS/Screenshot-1-1.png")

Hi and the first screen shot is when you just open the app correct. Then I would think this would have to do with the place windows pulgin in advance desktop settings.

---

### Post by AstralliS on 2008-05-16
So, what I'm supposed to do?

---

### Post by overdrank on 2008-05-16
> **AstralliS said:**
> So, what I'm supposed to do?

In CCSM under system, preference find the place windows  and make sure it is checked and I have mine set to center.

---

### Post by AstralliS on 2008-05-16
I did that, but nothing changed, just get worst, because now I don't see titlebars in the cases when windows are and minimized and maximized. :confused:

---

### Post by overdrank on 2008-05-16
> **AstralliS said:**
> I did that, but nothing changed, just get worst, because now I don't see titlebars in the cases when windows are and minimized and maximized. :confused:

Ok can you use the alt key and single click with the mouse both at the same time and move the window at all?

---

### Post by AstralliS on 2008-05-18
> **overdrank said:**
> Ok can you use the alt key and single click with the mouse both at the same time and move the window at all?

No. :(

I am forced to turn off the effects...

---


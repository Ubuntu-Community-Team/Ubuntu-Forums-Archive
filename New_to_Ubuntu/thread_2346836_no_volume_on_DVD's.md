---
title: "no volume on DVD's"
date: 2016-12-19
forum: New to Ubuntu
---

### Post by abartomak on 2016-12-19
I installed lubuntu-16.04.1 (my first ever in ubuntu-world)
It works nicely, but I found out there's no volume while playing DVD's (Gnome Player)
How to fix that?

EDIT: there's a volume in DVD menu, but not in the movie itself!

---

### Post by minecraft-electricity on 2016-12-19
Hi !
If, by volume you mean sound I don't really understand the question ?
[IMG]http://image.noelshack.com/fichiers/2016/51/1482154871-gnome-media-player.png[/IMG]
Do you mean that there is no sound icon (red circle) If yes try to click on view/preferences on the blue circle; [ if you don't see these menu put your mouse next to the red cross (on the title of the windows)]

---

### Post by abartomak on 2016-12-19
sorry, yes I meant sound. No sound. Sound icon is there; it says Volume is FULL.

also the DVD player is keeping a lot of sound while playing the DVD (the sound comes in waves... 5 seconds louder sound, then 5 seconds quiet)

---

### Post by Geoffrey_Arndt on 2016-12-19
Have you checked what the system sound volume slider is set at?   (in the panel . . . top right . . . allows for sound test (right & left speakers). . ).

If above doesn't do it . . . try installing "pavu control" for more granular sound output controls.

---

### Post by abartomak on 2016-12-19
> **Geoffrey_Arndt said:**
> Have you checked what the system sound volume slider is set at?   (in the panel . . . top right . . . allows for sound test (right & left speakers). . )

I didn't find that. system sound should be fine, as volume works in menu of the dvd, and in youtube for example.
or if you mean system sound of Gnome, I don't know how. 

I installed VLC player and the DVD sounds are working fine with it.

---

### Post by minecraft-electricity on 2016-12-19
as geoffrey said, try to install pavu control
```
sudo apt-get install pavucontrol && pavucontrol

```
once opened, click on the first tab and see if the sliders are okey

---

### Post by abartomak on 2016-12-20
Pavucontrol installed, and it looks nice and practical, but it didn't solve the problem. I am using VLC player now.

---


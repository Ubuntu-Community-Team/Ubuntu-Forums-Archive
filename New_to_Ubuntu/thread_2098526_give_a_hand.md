---
title: "give a hand"
date: 2012-12-26
forum: New to Ubuntu
---

### Post by geooilhunter on 2012-12-26
i have installed all formats but i couldn't listen to music just i watching only video without sound. what should i do

---

### Post by fdrake on 2012-12-26
> **geooilhunter said:**
> i have installed all formats but i couldn't listen to music just i watching only video without sound. what should i do

something is telling your your sound is muted. type into the terminal
```

alsamixer

```

---

### Post by geooilhunter on 2012-12-26
alsamixer that where must be written i dont know where
thanx for answer

---

### Post by fdrake on 2012-12-26
> **geooilhunter said:**
> alsamixer that where must be written i dont know where
thanx for answer

use the terminal

---

### Post by geooilhunter on 2012-12-26
terminal! where it is. please explain me in detail since i am fresh user of ubuntu

---

### Post by audiomick on 2012-12-26
That is a command that must be typed in a terminal. It will open the mixer application that deals with your sound. The mixer is operated with the cursor arrows and the enter key.

You can open a terminal with  ctrl+alt+t

---

### Post by fdrake on 2012-12-26
> **geooilhunter said:**
> terminal! where it is. please explain me in detail since i am fresh user of ubuntu

[http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)

---

### Post by fdrake on 2012-12-26
> **audiomick said:**
> y.

You can open a terminal with  ctrl+alt+t
+1
tend to forget all the time the short key

---

### Post by geooilhunter on 2012-12-26
anyway there is no any sound.  i installed mixer by terminal

---

### Post by geooilhunter on 2012-12-26
is there any video which can help to learn ubuntu

---

### Post by Impavidus on 2012-12-27
Step by step:


[LIST]
[*]Open a terminal (control-alt-t).
[*]Type **alsamixer** and hit enter.
[*]You will get some sort of graphical representation of a sound mixing panel. Use arrows left and right to select a control, up or down to set volume or use "m" to mute or unmute one of the controls. If muted, there will be two Ms below the column, else two Os on a green background.
[*]If you have set the volume and have unmuted the sound, close using escape.
[*]If you still don't have sound, PulseAudio may be muted. This should be coupled to alsamixer, but this doesn't always work. In this case, type **pavucontrol** in your terminal and hit enter.
[*]Click on **output devices** (or something like it, I'm translating from dutch). There are three small buttons in the upper right, one (the left most, at least with me) is a mute button. Click it to unmute. The volume control bars below will no longer be grayed out.
[*]If you still don't have sound it was not muted, but there is a different problem.
[/LIST]
I hope this helps.

Edit: All these things can be done using a graphical interface, without the terminal, but not everyone has the same menus or the same way to get into the settings. I don't know what your desktop looks like, but the terminal looks the same for everyone, so it's easiest problem solving using the terminal.

---


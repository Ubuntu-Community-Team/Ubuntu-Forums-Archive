---
title: "Virtual Gamepad/joystick (evdev/uinput/input)"
date: 2008-07-17
forum: Programming Talk
---

### Post by Felson on 2008-07-17
I have a couple questions really. I am trying to write an app to do input output macros using Keyboard/mouse/gamepad.

1) Is there a way to "create" a new joystick on the fly with code and no need for user intervention? This one is my main show stopper right now. I can make an output using uinput, but that doesn't make a new js#. Unless I am doing something wrong.... Which entirely possible. 

2) Is there some patent or law that makes this illegal? I would have thought someone would have done this by now, but that doesn't seem to be the case. At least not any that work with a game pad.

---

### Post by Felson on 2008-07-18
Bump

---

### Post by kaligus on 2008-07-19
> **Felson said:**
> I have a couple questions really. I am trying to write an app to do input output macros using Keyboard/mouse/gamepad.

1) Is there a way to "create" a new joystick on the fly with code and no need for user intervention? This one is my main show stopper right now. I can make an output using uinput, but that doesn't make a new js#. Unless I am doing something wrong.... Which entirely possible. 

2) Is there some patent or law that makes this illegal? I would have thought someone would have done this by now, but that doesn't seem to be the case. At least not any that work with a game pad.

I have just started looking into this myself.

I want to take all input (keyboard, mouse, gamepad) and run them through a program which has profiles Act on that input, even switching events from mouse to keyboard, keyboard to mouse, etc.

Ideally the profiles would be switched by what app has focus but that is a dream never realized in windows.

I did use a combination of  "total game control" and a keyboad macro program I forget the name of to accomplish this feat with the need to manually select "google earth", "secondlife", "gimp" etc. to get my desired functions.

You are one step farther along than I as I havent written code yet LOL.

Hopefully one of us can figure out how to do this :)

---

### Post by Felson on 2008-07-21
Ya, I have spent quite some time looking for this, off and on for the last few years. Started on this program a while ago, but had to put it down for a while or loose all my hair. I "plan" on going with the daemon/client model. Where a daemon fires on startup, and a client talks to it to tell it what set of rules to follow. In theory, it should be possible to write an app that switches based on focus. Heck, [devils pie]("http://burtonini.com/blog/computers/devilspie") may just work as it is now for that. Config syntax will probably be lisp like for mine as well. It's pretty easy to write interpreters for that syntax style.

---

### Post by kaligus on 2008-07-22
I hadnt thought of using devilspie, but I already have it running and I suppose that would be easy enough to use now that it has sunk in LOL.

yeah I have had the same hair problem...

---


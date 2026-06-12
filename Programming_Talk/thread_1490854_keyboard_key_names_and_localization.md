---
title: "keyboard key names and localization"
date: 2010-05-22
forum: Programming Talk
---

### Post by vek on 2010-05-22
Greetings.  I'm porting a game from windows to linux, and am running into the usual issues.

One is localization.  I don't want to leave anyone out!  On windows, it was possible to ask the operating system what the "name" of all keys on the keyboard was.  For example, you could ask it what the key with scancode 32 was.  And in english it'd return the wide-char string "SPACE", but if the user was on a german computer it might return "Leertaste" (no, I don't know that is correct).

Is there a corresponding function on linux?  I can't really afford to do it myself with some sort of huge case statement :P

For now, I'm going to leave english as the default language, but I don't want to leave anyone out :)

---


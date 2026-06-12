---
title: "Using Emerald theme manager"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by CommanderOne on 2008-07-13
Hey,

I have just started using Ubuntu, and so far I am having quite a good experience. One thing has been bothering me though.

I have downloaded a few themes, to make things look a bit more meish, but I am having problems using them.

I have installed them, using the Emerald theme manager that I installed earlier, but I can't seem to get them to work. I can see them, but I can't use them. Can anyone help?

Thnaks heaps.

---

### Post by overdrank on 2008-07-13
> **CommanderOne said:**
> Hey,

I have just started using Ubuntu, and so far I am having quite a good experience. One thing has been bothering me though.

I have downloaded a few themes, to make things look a bit more meish, but I am having problems using them.

I have installed them, using the Emerald theme manager that I installed earlier, but I can't seem to get them to work. I can see them, but I can't use them. Can anyone help?

Thnaks heaps.

HI and welcome, you will need to be using compiz (desktop effects) and if you select the theme in emerald then try using the alt, F2 keys and enter ```
emerald --replace
``` You may also look at the link in my signature on desktop effects.

---

### Post by mempman on 2008-07-13
1) sudo apt-get install compizconfig-settings-manager"  in a terminal
2) Go into System->Preferences->Advance Desktop Effect Settings
3) Search and Activate "Window Decoration"
4) In command box, enter: "/usr/bin/emerald --replace"

The above will make emerald your default windows themer.

---

### Post by CommanderOne on 2008-07-13
Hey,

Thanks for that guys, that kinda seems to work.

The problem I am having now is that the actual windows seem to get the new theme, but the two process bars don't seem to have.

I have included a screenshot to hopefully explain what I mean.

Do you know if this is a problem with theme, or something I have done?

Thanks!

---

### Post by overdrank on 2008-07-13
> **CommanderOne said:**
> Hey,

Thanks for that guys, that kinda seems to work.

The problem I am having now is that the actual windows seem to get the new theme, but the two process bars don't seem to have.

I have included a screenshot to hopefully explain what I mean.

Do you know if this is a problem with theme, or something I have done?

Thanks!

HI and are you meaning the panels at the top and bottom of the screen. Emerald is the window manager, to change your panels you will need to right click on them and select properties and then change the transparency.

---

### Post by CommanderOne on 2008-07-13
> **overdrank said:**
> HI and are you meaning the panels at the top and bottom of the screen. Emerald is the window manager, to change your panels you will need to right click on them and select properties and then change the transparency.

Thanks for all your help guys!

---


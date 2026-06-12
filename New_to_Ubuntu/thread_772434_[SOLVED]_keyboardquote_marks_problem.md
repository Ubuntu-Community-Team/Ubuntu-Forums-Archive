---
title: "[SOLVED] keyboard/quote marks problem"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by person8451 on 2008-04-28
Just installed 8.04, and am having an odd little issue. It does not seem to like it when I type a quote mark.  I can do it, but I have to type it a couple of times, and it beeps at me the first time or two.

´ single ones and ¨ double ones do the same thing.

I installed with the alternate CD in order to use encryption, and it asked me to type in various things and tell it whether I had keys for like odd Greek or Russian characters, which I do not, so I told it ¨no¨.  (total of 8 button-pushes there to put quotes around the word no).  Anyhow, I assume I did something wrong at the install, but I dont know what or how to fix it now.  

uhh...current keyboard setting is Generic 105-key (Intl) PC, USA International with dead keys (if that helps).

Help would be greatly appreciated.  :)

---

### Post by Golem XIV on 2008-04-28
The US International keyboard layout uses the quotes and other keys to create "composite" characters like á, &#263;, ñ etc.  If you type the quote first and the character second, it creates the composite character.  If you type the quote twice (or quote then space) it creates just the quote.

If you have no use for this functionality just switch your keyboard layout to a standard US one (System -> Preferences -> Keyboard -> Layout tab)

Good luck!

---

### Post by person8451 on 2008-04-28
Thanks!  With your help I got it working normally.

"""""woo!!  quote marks!  lol

---

### Post by iced_tea on 2008-05-12
I am having this exact problem. 
My setup determined my layout the same, so I´m confident I can fix it using the same method. 

The only problem is that I am using Fluxbox as my WM, and I have no idea how to change the keyboard language. 

FB depends on configuring through text files more than menus, and fixing problems is a little less intuitive. 

Any help would be appreciated

---

### Post by Weidbrewer on 2008-05-12
The auto-detect for the keyboard layout can be wonky.  On my test machine, where I reinstall the OS often, it has "detected" the international layout maybe a quarter of the time (In 7.10.)  I know I'm hitting the same keys every time, as it has become habit...but every now and again, I'll be typing, try to quote something and, whoops! 

Not a big deal, and I haven't run in to it with 8.04 yet.

---

### Post by iced_tea on 2008-05-12
Well, after a bit of research I was able to find an incredibly simple fix for it.
Just pull up a console:
[INDENT]setxkb us[/INDENT]
And then you're mapped as US standard.

So there's a fix for fellow Fluxboxers.

---

### Post by alciono on 2008-05-12
Thanks Golem, I had the exact same issue with my keyboard. Recently I added the Dvorak keyboard to my xorg.conf so that I may switch between the Qwerty and Dvorak layouts. At that time, I inadvertently changed the standard US layout to international. Now that I have learned about this, I think I might retain the international layout anyway. :)

---

### Post by iced_tea on 2008-05-13
> **iced_tea said:**
> Well, after a bit of research I was able to find an incredibly simple fix for it.
Just pull up a console:
[INDENT]setxkb us[/INDENT]
And then you're mapped as US standard.

So there's a fix for fellow Fluxboxers.

Funny enough, I rebooted this morning and "setxkb" disappeared
Maybe I was using "setxkbmap"

---


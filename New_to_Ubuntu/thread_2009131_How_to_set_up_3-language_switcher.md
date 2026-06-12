---
title: "How to set up 3-language switcher?"
date: 2012-06-24
forum: New to Ubuntu
---

### Post by ThrashManiac on 2012-06-24
Hi, 

I've read documentation on 'setxkbmap' utility, but it seems like it doesn't have support for 3 languages switcher... :confused: 

All the standard menus do not help either.

---

### Post by Ampi on 2012-06-24
If you're talking about only input, so keyboard use, for me ibus ([http://code.google.com/p/ibus/](http://code.google.com/p/ibus/)) works very well, but that is mostly good for languages like Chinese. For other languages I simply add them in the keyboard menu in the system settings. Then a keyboard icon shows up that gives you the possibility to switch with on click of the mouse.

---

### Post by ThrashManiac on 2012-06-24
> **Ampi said:**
> If you're talking about only input, so keyboard use, for me ibus ([http://code.google.com/p/ibus/](http://code.google.com/p/ibus/)) works very well, but that is mostly good for languages like Chinese. For other languages I simply add them in the keyboard menu in the system settings. Then a keyboard icon shows up that gives you the possibility to switch with on click of the mouse.
Yes, I'm talking about the input languages. I have no problem at all with definition of 2 input languages, but I fail to define 3 input languages. I've tried all the standard menus - no use. 
I need to define 3 languages.

---

### Post by Ampi on 2012-06-24
I just added 3 keyboard layouts myself, it seems to work. What I did (I am in Gnome 3.0):

* System Settings
* Keyboard Layout (via Keyboard there is also a shortcut to Layouts)
* Tab Layouts
* Left lower corner you can add languages.

You can also add a shortcut to switch layouts but that doesn't seem to work for me right now (I chose ctrl+space).

Hope this works!

---

### Post by ThrashManiac on 2012-06-24
> **Ampi said:**
> I just added 3 keyboard layouts myself, it seems to work. What I did (I am in Gnome 3.0):

* System Settings
* Keyboard Layout (via Keyboard there is also a shortcut to Layouts)
* Tab Layouts
* Left lower corner you can add languages.

You can also add a shortcut to switch layouts but that doesn't seem to work for me right now (I chose ctrl+space).

Hope this works!

Thank you. I'll try that at home, *although* I doubt that it's possible in Lubuntu - there's a different window manager ([http://lxde.org](http://lxde.org)) and the set of programms and settings is also different.

---

### Post by Ampi on 2012-06-24
Aah, I missed that part.

Well I have no clue about Lubuntu but here some threads that for *some* people have worked. But I reckon you already have seen these :-(. But just maybe one of them can help.

Also, installing software like iBus and SCIM might make it easier if you can't do it directly via the system settings?

Good luck!

lubuntu/lxde keyboard layout switching?
[http://ubuntuforums.org/showthread.php?t=1455877](http://ubuntuforums.org/showthread.php?t=1455877)

Change keyboard layout (Lubuntu)
[http://ubuntuforums.org/showthread.php?t=1659607](http://ubuntuforums.org/showthread.php?t=1659607)

change keyboard language (post #5)
[http://ubuntuforums.org/showthread.php?t=1502679](http://ubuntuforums.org/showthread.php?t=1502679)

Switching keybourd layouts in Lubuntu 11.10
[http://askubuntu.com/questions/102344/switching-keyboard-layouts-in-lubuntu-11-10](http://askubuntu.com/questions/102344/switching-keyboard-layouts-in-lubuntu-11-10)

Lubuntu Keyboard problem
[http://askubuntu.com/questions/85054/lubuntu-keyboard-problem](http://askubuntu.com/questions/85054/lubuntu-keyboard-problem)

---

### Post by ThrashManiac on 2012-06-24
> **Ampi said:**
> Aah, I missed that part.

Well I have no clue about Lubuntu but here some threads that for *some* people have worked. But I reckon you already have seen these :-(. But just maybe one of them can help.

Also, installing software like iBus and SCIM might make it easier if you can't do it directly via the system settings?

Good luck!

lubuntu/lxde keyboard layout switching?
[http://ubuntuforums.org/showthread.php?t=1455877](http://ubuntuforums.org/showthread.php?t=1455877)

Change keyboard layout (Lubuntu)
[http://ubuntuforums.org/showthread.php?t=1659607](http://ubuntuforums.org/showthread.php?t=1659607)

change keyboard language (post #5)
[http://ubuntuforums.org/showthread.php?t=1502679](http://ubuntuforums.org/showthread.php?t=1502679)

Switching keybourd layouts in Lubuntu 11.10
[http://askubuntu.com/questions/102344/switching-keyboard-layouts-in-lubuntu-11-10](http://askubuntu.com/questions/102344/switching-keyboard-layouts-in-lubuntu-11-10)

Lubuntu Keyboard problem
[http://askubuntu.com/questions/85054/lubuntu-keyboard-problem](http://askubuntu.com/questions/85054/lubuntu-keyboard-problem)
Thank you :) 
I have seen some of those posts, and the command: 
```
setxkbmap -layout "us,bl" -option "grp:alt_shift_toggle"
``` ...is familiar to me. The strange thing is, that some of the posts use three-language combination and they claim that this work (although I've tried this one - unsuccessfully). Oh, well, I'll try that again, at home - may be there's something else wrong with my installation. 

Thanks for being helpful :) Where's that button to add bonus points? :)

---

### Post by Ampi on 2012-06-24
Hmm :-(, well some posts seem to talk about some extra configuration to make that specific command work. So maybe if you read well through them you might find something you haven't tried yet :-).

Give it a try and we'll see! :-)

There use to be a "Thank You" button, but I think they removed it. But no problem, happy to (hopefully) help! :-D

---

### Post by ThrashManiac on 2012-06-24
Solved! 

I've been using incorrect format! 

The correct one is: 
```
setxkbmap -option grp:alt_shift_toggle "us,ru,il"
```
:guitar:

---

### Post by Ampi on 2012-06-24
Really? Awesome! :-)

---


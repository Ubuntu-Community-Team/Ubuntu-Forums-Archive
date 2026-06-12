---
title: "[SOLVED] newbie help"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by jim_in_dorris on 2008-06-05
ok, I installed ubuntu 8 and it booted just fine.  however after running the first set of updates, I have to boot from the recovery boot then select continue normal boot to be able to boot into ubuntu.  Also what the heck do i have to do to run the games in sudoku.com

---

### Post by kesman on 2008-06-05
Please don't post under topics "help noob" or such, it gives no idea of what's your problem.

Why do you have to boot from the recovery mode? Does it give you some error messages during normal boot?

---

### Post by warbread on 2008-06-05
Specifics will be needed to help you.  What's stopping you from booting into Ubuntu?  What happens when you go to Sudoku.com?

---

### Post by jim_in_dorris on 2008-06-05
sorry.  The reason I have to use the the recovery option in the grub loader is that the normal boot gets to a blank screen, before loading the brown screen, and just hangs there forever.  no error messages, just hangs. Using the recovery option it boots fine.  
In Sudoku.com the error console states
"void window.open (getlaunchwebgameurl ("
when I click on gamehouse sudoku or Ancient Sudoku.

---

### Post by jim_in_dorris on 2008-06-05
ok, the latest release of updates seems to have fixed my problem loading, If I just let it boot, now it boots fine, so that problem is fixed.  Now if I can just get the problem with sudoku.com fixed.....

---

### Post by Xiong Chiamiov on 2008-06-05
Does it work in other browsers?  What about other OSs?  It sounds like a Javascript bug to me.

---

### Post by kesman on 2008-06-05
Have you installed flash plugin? You can do this easily with
```

sudo apt-get install ubuntu-restricted-extras

```

it will install a bunch of other usefull codecs, media players and stuff too, so if you only want to install the flash plugin, install it with:

```

sudo apt-get install flashplugin-nonfree

```
and restart your browser

---

### Post by jim_in_dorris on 2008-06-06
yes I have flash installed, it appears to be a java script error.  I only have the Firefox browser loaded in Ubuntu, so I haven't tried another browser yet.  It works fine in WinBlows, just trying to do everything in Ubuntu to get used to using it.

---


---
title: "msttcorefonts installation question"
date: 2012-04-23
forum: New to Ubuntu
---

### Post by feralfinds on 2012-04-23
hi ! 
im installing msttcorefonts, and im having a weird obstacle. im sure theres a really obvious way to proceed, and that im having a total dork moment. but, if you can, help, id love it! 

im at a screen in my terminal where the installation is stopped, and im supposed "ok" the end-user license agreement...pretty standard stuff. theres the following at the bottom of the page:
< ok > 
which i assumed i was to click, or something. but, i cant click on the ok, i cant type ok anywhere.....any ideas? ive hit enter bunches of times. 

thanks! jenn

---

### Post by qamelian on 2012-04-23
Press the Tab key on your keyboard and the Okay button should highlight. Then just press Enter.

---

### Post by na5h on 2012-04-23
Make sure that the window is selected and then try using the arrow keys.

---

### Post by Frogs Hair on 2012-04-23
What version of Ubuntu ? I was wondering because 10.10 has reached end of life . I installed the MS core fonts  via the software center on 11.10 and 12.04 and accepted the agreement using a GUI . If you are using 10.10 you may have had to install a different way.

---

### Post by Curtis6767 on 2012-04-23
I went through this yesterday. [http://ubuntuforums.org/showthread.php?t=1963638](http://ubuntuforums.org/showthread.php?t=1963638)

If your problem is the same as mine, which is not necessarily the case, then you are missing a key. 

The way I discovered that was closing the terminal, despite the error message, restating my computer, then ran:

```
sudo apt-get update
```

At the end of the process, I was met with error message indicating I was missing a key.

copy that key number and then follow the instructions in post #4 of the linked thread.

If that doesn't work, then you'll need to do a search. I found several sites with several different solutions, though none of them worked until I stumbled upon the solution that is in post #4.

Sorry can't be of more help.

---

### Post by feralfinds on 2012-04-23
oh awesome! thanks. the tab trick worked. i was highlighting the word ok with my cursor, but the tab button made it highlighted in red...which i guess made all the difference. 

thanks!!! 
jennifer

---


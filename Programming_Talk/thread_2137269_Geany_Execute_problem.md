---
title: "Geany Execute problem"
date: 2013-04-20
forum: Programming Talk
---

### Post by dippyes on 2013-04-20
Hello there, first of all I want to apologize for my bad explanation, and if there is another topic like this, I just didn't find it. Ok here is my problem I try to run a C program under Geany, it compiles and builds fine, but when it comes to the execution, it just gives me a blank page, with no response. I am not sure what can be causing this...
I hope this Screenshot helps finding the problem
[ATTACH=CONFIG]241556[/ATTACH]

---

### Post by MG&amp;TL on 2013-04-20
If you look into the directory you saved your source code/project into, is there an executable file in there? If so, run that file from the terminal, and see if you get anything then. (You may have a bug in your program) 

If you get something in your terminal you probably want to fix the geany settings. I believe there's a [build menu.]("http://wiki.geany.org/howtos/configurebuildmenu")

---

### Post by dippyes on 2013-04-20
Thank you, just found it about 10 mins ago, yea I can run it in the terminal, but it's kinda annoying, having to run it every time from there, I should look for some problem in the settings. Thank you mate!

---

### Post by steeldriver on 2013-04-20
Yes if you go to the Build --> Set Build Commands menu item you should see an 'Execute' action at the bottom -  mine says "./%e" (which is the default value, afaik) which says 'run the executable in the current directory' (your 'Build' action should set the output file as -o "%e")

---


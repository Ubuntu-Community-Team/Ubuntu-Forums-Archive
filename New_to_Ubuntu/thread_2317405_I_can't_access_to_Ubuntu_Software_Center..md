---
title: "I can't access to Ubuntu Software Center."
date: 2016-03-16
forum: New to Ubuntu
---

### Post by Abdullah_Al_Faruqu on 2016-03-16
USC just crashes, what can i do??.. & i can't play any mp3 file with Rhythmbox. It's just show error and requirres plugin for rhythmbox. What should i do now???..

---

### Post by howefield on 2016-03-16
What is the error that you get when USC crashes ?

You could install Synaptic Package Manager by opening a terminal and using the command

```
sudo apt-get install synaptic
```

This will give you an alternative package manager to the Ubuntu Software Centre, which also has a GUI.

Are you trying to install ubuntu-restricted-extras by any chance to play the mp3 files ?

---

### Post by Abdullah_Al_Faruqu on 2016-03-16
Thanks!..

---

### Post by Edward_Fish on 2016-03-16
If that fixed the problem, you should mark this thread as solved...
If that did not fix the problem, press Ctrl-Alt-T, and enter: *sudo apt-get install <package-name>*

---


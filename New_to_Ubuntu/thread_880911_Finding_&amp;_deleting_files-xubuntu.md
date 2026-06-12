---
title: "Finding &amp; deleting files-xubuntu"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by faron45 on 2008-08-05
Quick post before taking off.Had to do it this way.Been putting this post off for 2 days now.Downloaded a couple of things from the internet that I've now decided that I really don't want on my pc.Problem is...I'm extremely new to the [linux/xubuntu] operating system & now I need to know how to find these files & delete them.For any/all help.....thanks in advance.Be back in a few hours.Again,thank you all very,very much.
                           
                               Jerry Garcia:guitar:

---

### Post by kk0sse54 on 2008-08-05
Most likely they are either downloaded to your Desktop or home folder. To check precisely and if you used firefox just go into Firefox then Edit > Preferences and check where all downloads are saved to. Once you find out press alt + f2 and type in thunar which is you file browser and then just navigate to the files and press delete and your set. Alternatively if you know where the files are stored you can use the rm command in the terminal. Type man rm to find out more about it but be very careful when deleting files this way as you might end up deleting things you need.

---

### Post by cpetercarter on 2008-08-05
What sort of files are they, and where did you get them from? If you downloaded them using Add/Remove or Synaptic Package Manager, you can simply use these programmes to remove them. 
Depending on the sort of file they are, and where they are located, you may be able to use "whereis" to find them. In a terminal:
```
whereis <name of the thing you're looking for>
```

---


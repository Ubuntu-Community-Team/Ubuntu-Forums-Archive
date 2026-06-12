---
title: "[SOLVED] Questions Concerning the Hard Drive"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by RedStarYellowSun on 2008-09-27
Hello again!
Being new to Ubuntu, my mind is still set on Windows-mode. Thus, I get confused with the way that the hard drive is arranged. Back in Windows "My Computer", I would see (the CD/DVD Drive and) the "C:" Drive and under that, I would see things like "Documents and Settings", "Program Files", other stuff like my personal "Joey" folder, and "Windows".
Here, I open "Computer" and in it I would see more than just "C:" Drive and the CD/DVD Drive. I see three additional drives: "ServiceV002", "SW_Preload", and "File System". They all seem to be related to the system. Where do I put my personal files?
In Windows, I had some in "Joey's Documents" (in "Documents and Settings") and, outside S&D, "Joey". Where do I put things in Ubuntu?

Likewise, in Windows, the "My Computer" window had a pie-graph stating how much of the disk was used and how much was free. Where is this in Ubuntu?

Thanks again!

Take care,
RedStarYellowSun

---

### Post by Mindzai on 2008-09-27
You should keep all of your files in your 'home' directory. Think of this as the equivalent to your 'my documents' on windows - it is your own personal space to do what you like with. You can get there by going to Places > Home Folder.

In Ubuntu, all of the files (system files, your files, everything) live under a directory called / (slash). The actual location of your home directory is /home/your_name, but you don't need to worry too much about that, because you have the menu item i mentioned above to get you there quickly.

As for the info about disk usage, there are a few ways. Firstly you can look in the status bar at the bottom of any nautilus window and it will tell you how much free space you have (nautilus is like the equivalent of windows explorer - if you go to your home directory, the window you use to see your files and folders is nautilus). If you want more detail you can go to Applications > Accessories > Disk Usage Analyzer.

As you can see there is quite a difference between how windows and linux organize files, but personally I found that once I got used to it, the Linux way made much more sense. For the most part you don't need to venture outside of your home directory, but if you do everything is organized very logically.

---


---
title: "Desktop slow"
date: 2015-10-13
forum: New to Ubuntu
---

### Post by ttocstn on 2015-10-13
I installed ubuntu onto a server and since I am new to linux I decided to install a desktop environment (Ubuntu Desktop) the problem is its so slow. takes over 5 seconds for the menu to pop up is there a setting to alter it for better performance? kind of like in windows you can disable all the visual effects to improve performance.

CPU opteron 4180 x2 (12 cores total)
Ram 32gb ddr3 ecc
HD1 sata2 500gb system drive
HD2 2 x sata3 500gb hardware raid 0
Onboard Video Matrox G200eW
ubuntu 14.04 LTS 64bit


Sorry if this has been discussed or if this is the wrong section

---

### Post by v3.xx on 2015-10-14
Your video card has a max 32M of ram from what I see on line.  I think the Unity desktop may be too much for it.  I suggest installing the "Fallback" desktop and see how it runs.  To install..

```
sudo apt-get install gnome-panel

```
At login, click on the icon and choose Flashback (metacity)

---

### Post by ttocstn on 2015-10-14
> **v3.xx said:**
> Your video card has a max 32M of ram from what I see on line.  I think the Unity desktop may be too much for it.  I suggest installing the "Fallback" desktop and see how it runs.  To install..

```
sudo apt-get install gnome-panel

```
At login, click on the icon and choose Flashback (metacity)

Thank you, this is working much better now

---

### Post by v3.xx on 2015-10-14
Your welcome :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---


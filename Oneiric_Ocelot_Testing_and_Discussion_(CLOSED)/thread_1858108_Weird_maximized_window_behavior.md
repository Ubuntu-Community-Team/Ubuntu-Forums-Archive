---
title: "Weird maximized window behavior"
date: 2011-10-11
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sundowndk on 2011-10-11
Hello,

Ok, I've run into this problem alot, and I've have not been able to find any bug reports about the problem. I'm sure there must be a report somewhere, since this is a very annoying bug.

Lets say I open up Firefox, maximize its window and then minimize so it hides in the Unity launcher. I then open up a second program, let say gedit, it makes no difference if the second window is maximized or not, but when ever I close the second window focus is given back to the Firefox window, even tho it never had focus in the first place since it was minimized. 

The problem is that Unity thinks the window has focus and that its visible, but its not. I cant press its icon in the launcher to bring up the window, I have to set to the focus to either the desktop or a new window to be able to bring the window out from hidding.

The bug only shows up when dealing with windows on the same desktop.

Has anyone noticed this behavior ?

---

### Post by BrownE on 2011-10-12
> **sundowndk said:**
> Hello,

Ok, I've run into this problem alot, and I've have not been able to find any bug reports about the problem. I'm sure there must be a report somewhere, since this is a very annoying bug.

Lets say I open up Firefox, maximize its window and then minimize so it hides in the Unity launcher. I then open up a second program, let say gedit, it makes no difference if the second window is maximized or not, but when ever I close the second window focus is given back to the Firefox window, even tho it never had focus in the first place since it was minimized. 

The problem is that Unity thinks the window has focus and that its visible, but its not. I cant press its icon in the launcher to bring up the window, I have to set to the focus to either the desktop or a new window to be able to bring the window out from hidding.

The bug only shows up when dealing with windows on the same desktop.

Has anyone noticed this behavior ?
No, but I have seen the behaviour before (in Natty). The problem resolved itself when I 'upgraded' to Oneiric. I too cannot find a bug report.

---

### Post by ikt on 2011-10-12
Maybe: [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/859885](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/859885)

?

---

### Post by sundowndk on 2011-10-12
BrownE: You are right the problem was in Natty as well. For me the problem did go away as well when I installed Oneiric, but its back, and on two separate machines.

ikt: Thats exactly the bug, thanks alot.

Looks like they tried to fixed it, hope they nail it before release since its really gonna confuse a lot of people.

---


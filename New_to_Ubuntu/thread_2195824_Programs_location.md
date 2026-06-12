---
title: "Programs location"
date: 2013-12-26
forum: New to Ubuntu
---

### Post by mlvmhn on 2013-12-26
In order to open a certain file, i must know the way of where the program is located on my harddrive. 

i must choose the location, but where do i find all the installed programs on my system?

---

### Post by FiremanEd on 2013-12-26
Hi Mikael, If I remember from your last thread on the forum, you installed Ubuntu 12.04, so my guess is that you have the default desktop which is "Unity".  You can tell if it is Unity by looking at your desktop and you will see a dock, broken down into tiles on the left side of the screen.  On the very top of this dock is a icon, sort of looks like a swirl, it is the first tile , click on that and it will open your programs installed on your computer.  It should open up into a large rectangle, which you can make bigger if you like.  In this large rectangle, you will see some icons on the bottom of the large rectangle.  An icon that looks like a house and so on.  The second icon, after the house will display your applications (programs).  I am trying to keep this as simple for you as possible, by not using the ubuntu names for all of the steps I gave you.  Take it from there!

Ed

---

### Post by kajoky on 2013-12-26
You can find the installed applications by 
1) click the Dash Home icon at the top of the launcher, it has the Ubuntu logo on it
2) at the bottom there should be a row of icons, the left most one is a house, click the one that looks similar to a ruler, pencil and pen
3) there should now be a row above that says: Installed see x more results >
4) click see x more results >
you should now be looking at the icons for the main programs installed.

---

### Post by deadflowr on 2013-12-26
Most programs launch from /usr/bin
Probably look there first.

If the program isn't listed in the "open with" section of the file's properties(right click on file > properties).

---

### Post by Impavidus on 2013-12-26
If you know the command that can open the file (say, it's called *program-name*) you can use the command **which *program-name*** to find out where it is. It's usually in /usr/bin/.

---


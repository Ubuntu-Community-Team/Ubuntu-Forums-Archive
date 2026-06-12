---
title: "Screenshot problem in gnome"
date: 2012-09-16
forum: New to Ubuntu
---

### Post by 3dmatrix on 2012-09-16
When we press the print screen button on the keyboard it never asks us where to save the file, it just saves it silently in the pictures folder. This is very annoying. Does any one has a solution for this ? These are some solutions mentioned here : [https://bugs.launchpad.net/ubuntu/+source/gnome-screenshot/+bug/927952](https://bugs.launchpad.net/ubuntu/+source/gnome-screenshot/+bug/927952) but none of them work for me.

---

### Post by black veils on 2012-09-17
use xfce4-screenshooter intead?

you can assign the new screenshot app to the Print key:

1. go to **system settings** >> **keyboard** >> **shortcuts** tab >> **custom shortcuts** from the left pane

2. select the plus sign from the bottom, enter name and command.

3. it will show in the list, then select where **disabled** shows, and enter your keys. you may or may not have to disable the other Print shortcut first. if Print doesnt work, simply use another key combination.

---

### Post by vasa1 on 2012-09-17
I have set **gnome-screenshot** to save its screenshots to my Desktop.

Open **dconf-editor**. (You may have to install it from the Software Center, if you don't have the program.)
Click on **org** in the left side panel to expand its contents.
Click on **gnome** in the left side panel to expand its contents.
Scroll down till you come to **gnome-screenshot**.
Click on it.
In the right side panel, look at the top line.
Click on it.
Press the right arrow on your keyboard. Delete the word **Pictures** and replace it with the name of the folder you want. I have **Desktop** instead of **Pictures**.
Close dconf-editor.
Now, any gnome-screenshot will be in the folder you have specified.

---

### Post by vasa1 on 2012-09-17
> **3dmatrix said:**
> When we press the print screen button on the keyboard it never asks us where to save the file, it just saves it silently in the pictures folder. This is very annoying. Does any one has a solution for this ? These are some solutions mentioned here : [https://bugs.launchpad.net/ubuntu/+source/gnome-screenshot/+bug/927952](https://bugs.launchpad.net/ubuntu/+source/gnome-screenshot/+bug/927952) but none of them work for me.

BTW, is this on the minimal OS you've posted about?

---

### Post by 3dmatrix on 2012-09-17
No it is not on the minimal ubuntu but on the regular ubuntu with gnome shell.

For the dconf solution does it silently saves in the new location or it shows it on a pop up ?

I tried Xfce4 screenshooter and it works very well.

---


---
title: "Graphics drivers"
date: 2018-11-05
forum: New to Ubuntu
---

### Post by behemoth62 on 2018-11-05
Hi,
I decided to replace XP on an old laptop with Xubuntu, never having used Linux before, and the installation went smoothly and is now operational. I have just one problem which I can't find the solution to.
The screen resolution is 'stuck' on 640x480 with no apparent alternatives available. This means the display is way over the edge of the screen which is very awkward and in some cases making windows unusable.
I'm assuming I need to find a driver for the display but I can't figure out what to do. I expect there's a simple answer, but it's beyond my limited knowledge. Help!

---

### Post by ajgreeny on 2018-11-05
What graphics hardware does the computer use?

Have you fully updated the Xubuntu install yet with commands ```
sudo apt update
sudo apt upgrade
``` as that may be all that's necessary?

However, to help us, please show the output of ```
lspci
``` in terminal.
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---


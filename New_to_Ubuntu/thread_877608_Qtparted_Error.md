---
title: "Qtparted Error"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by a1anm on 2008-08-01
Hi

I just installed qtparted, however when i try and open it i get this error:

Could not launch menu item
Failed to execute child process "qtparted-root" (No such file or directory)

I can access it by going terminal > gksu qtparted

Is there a way I can fix it so i can access it without having to go through the terminal?

cheers!

---

### Post by collinp on 2008-08-01
You have to run Qtparted as root, that is what gksu is for. The error is probably telling you that you are not running it as root.

---

### Post by a1anm on 2008-08-02
ok, gotcha.

in that case why does the app even get added to the application list if you can only run it through terminal?

sorry if these questions sound dumb/don't make sense but i'm still getting to grips with linux.


cheers!

---

### Post by collinp on 2008-08-02
> **a1anm said:**
> ok, gotcha.

in that case why does the app even get added to the application list if you can only run it through terminal?

sorry if these questions sound dumb/don't make sense but i'm still getting to grips with linux.


cheers!

Its ok, we was all there at sometime. The reason is that they are still runnable, just through a different method. And i dont know how to make it runnable by a regular user.

---

### Post by clivelr on 2008-11-01
I had the same problem, and fixed it this way:

This is on Ubuntu 8.04 - so the steps may not be exactly the same, just as long as you can get to edit the "Main Menu" of your system.

On the Menu Toolbar click on "System", then click "Preferences", finally click on "Main Menu". This will bring up a new window with all of your items listed on the menu items.

Find the QtParted entry by navigating down the left part of the window until it is listed in the right hand part. Mine is located under "System Tools". 

When you have found QtParted right-click it and select "Properties" - this will then show the command used to launch the application. Change the 3rd entry from "qtparted-root" to "gksu qtparted" and click "Save".

---


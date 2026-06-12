---
title: "Can't Find Installed Apps in Dash"
date: 2016-05-23
forum: New to Ubuntu
---

### Post by louis31 on 2016-05-23
I know the title sounds familiar, but after searching this problem all I have found was people who didn't know about the unity dash.

I have downloaded software from the software center, I check the installed list, it has installed. I search for it, no results. I hav echecked spelling and I have also clicked the apps filter and looked manually without entering anything, nothing. This has happened before ( I think with every app I have installed, but it appears after a couple of minutes) This time I downloaded Clementine, and nothing, I can't find it, any help on how to find it and solve this problem would be greatly appreciated.
   [ATTACH=CONFIG]269250[/ATTACH][ATTACH=CONFIG]269251[/ATTACH]

---

### Post by 0N3 on 2016-05-23
Try running the apps from a terminal see if it makes a .desktop file for you. Sometimes in a hidden folder in your home folder .local/share/applications

---

### Post by buzzingrobot on 2016-05-23
A bug exists that occasionally produces this behavior on newly installed packages.  Logging out and logging back seems to be the remedy.

---

### Post by djheadley on 2016-05-24
same problem - apps not making it into dash, tried to run "apps" from terminal and it said:

apps
No command 'apps' found, did you mean:
 Command 'apbs' from package 'apbs' (universe)
 Command 'yapps' from package 'yapps2' (main)
 Command 'apxs' from package 'apache2-dev' (main)
 Command 'paps' from package 'paps' (universe)
 Command 'a2ps' from package 'a2ps' (universe)
apps: command not found


now what should I try

---

### Post by mc4man on 2016-05-24
> **djheadley said:**
> same problem - apps not making it into dash, tried to run "apps" from terminal and it said:

apps
No command 'apps' found, did you mean:
 Command 'apbs' from package 'apbs' (universe)
 Command 'yapps' from package 'yapps2' (main)
 Command 'apxs' from package 'apache2-dev' (main)
 Command 'paps' from package 'paps' (universe)
 Command 'a2ps' from package 'a2ps' (universe)
apps: command not found


now what should I try
log out/in

---


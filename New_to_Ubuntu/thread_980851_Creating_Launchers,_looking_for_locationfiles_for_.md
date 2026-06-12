---
title: "Creating Launchers, looking for location/files for executing apps."
date: 2008-11-13
forum: New to Ubuntu
---

### Post by Brage Robotpacifist on 2008-11-13
Hello.
I'm fairly new too Ubuntu and recently I installed AWN. I want to get rid of my panels and use only AWN combined with widgets. As I understand it with AWN, if you drag and drop a shortcut from the main menu you would still need to have the main menu operative because the shortcuts in AWN only "points" to the main menu launcher.
Basically what I need help with is creating a launcher. I can't find out what or where "executives" are located so that I (hopefully) can get rid of all my panels. After some searching on the web I found out that Ubuntu uses .debs as .exes and that they are located at /var/cache/apt/archives but making a launcher to a .deb there (firefox) didn't seem to work. Can anybody help me out, or maybe tell me if this will work at all?

Thanks!

---

### Post by lovinglinux on 2008-11-13
The deb files are installation files, so you click them to install the applications not to run them. Most executables in Linux do not have an extension like "exe". They don't need an extension to work. What makes them executables is their permission to run as application (executable). When you set the permission of a file to run as application, it's icon changes, so you can identify which files are executables.

I think you will find most executables you need under the following directories:

/bin
/usr/bin

---

### Post by Brage Robotpacifist on 2008-11-13
Thanks! That worked out perfectly.

---

### Post by lovinglinux on 2008-11-13
You are welcome.Please don't forget o mark the thread as [SOLVED] using the Thread Tools menu. This helps other people find th same solution.

---

### Post by Paqman on 2008-11-13
Also, on Linux you don't need to know the full path to the executable to launch it. Creating a launcher that simply invokes "firefox" works just as well as "/usr/bin/firefox" (or whatever it is)

---


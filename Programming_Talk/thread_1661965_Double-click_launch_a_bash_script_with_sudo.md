---
title: "Double-click launch a bash script with sudo"
date: 2011-01-07
forum: Programming Talk
---

### Post by japhyr on 2011-01-07
Hello,

I am writing a bash script to automate the installation of packages when I configure a new computer.  The script is working, but since many of the commands need root privileges, I have to run the script from the terminal, ie "sudo /home/username/Desktop/script.sh".  If I double click the script icon on the Desktop, the program runs but fails quickly because it does not have root privileges.

Is there a way to gain root privileges after clicking the script icon?

---

### Post by psusi on 2011-01-07
Have the script use sudo.

---

### Post by MadCow108 on 2011-01-07
you probably want gksudo not sudo for a gui password prompt.

---


---
title: "gcc"
date: 2007-05-15
forum: Programming Talk
---

### Post by jmwalloh on 2007-05-15
****i've got this .c files on my desktop that i want to compile using gcc in the terminal. how do i go about doing this:lolflag:

---

### Post by LaRoza on 2007-05-15
gcc sourceFile.c -o executablesName

There are many more options but this will compile and name the executable.

You have to be in the .c's directory, if it is in /home/me/Desktop, type cd Desktop to move to the desktop to compile. (Remember, it's case sensitive)

-edit to find out where you are, type "pwd" which means "Print Working Directory", if it is /home/me, like it usually is, type "cd Desktop", "me" is whatever your username is.

- \/ "sudo aptitude install build-essential", sorry I thought you had it.

---

### Post by bukwirm on 2007-05-15
You also need to install the build-essential package.

---


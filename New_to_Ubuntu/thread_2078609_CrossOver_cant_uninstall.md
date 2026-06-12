---
title: "CrossOver cant uninstall"
date: 2012-10-31
forum: New to Ubuntu
---

### Post by vibaviattigala on 2012-10-31
i just downloaded it and install it i cant uninstall from softweare center and when i click uninstall from dash it wont get uninstall just bottles

is there a terminal code to uninstall it
?

---

### Post by Mark Phelps on 2012-10-31
The command would be:

> sudo apt-get remove package-name

Where package-name is the full name of the package.

If you don't know the full name, you can use something like:

> crossover*

If you want to also purge all data associated with the package, insert "--purge" (without the quotes) before the package-name parameter in the command.

---

### Post by wheeze on 2012-10-31
> **Mark Phelps said:**
> TIf you want to also purge all data associated with the package, insert "--purge" (without the quotes) before the package-name parameter in the command.

Or you can simply use **apt-get purge packagename** as your command line.

---


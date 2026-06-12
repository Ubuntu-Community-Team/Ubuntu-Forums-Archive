---
title: "Compiling Kmymoney"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by rpete on 2008-10-17
[B][/B

Hi, I need  help compiling kmymoney.  I'm used to Windows just clicking on the .exe file if it doesn't install itself. I clicked on the kmymoney README file and it has instructions for compiling.  The only problem is I can't figure out what the first step means.  

It reads "cd' to the directory containing the package's source code and type ./configure"   Could someone explain what this instruction means?  Should I go to the terminal?  Once I understand this I can probably follow the other steps as they involve typing more commands.

rpete

---

### Post by gletob on 2008-10-17
You don't have to compile it unless you want the absolute newest version  that's not optimized for ubuntu or want a very small (I think unnoticeable) speed boost.  To install go to applications add/remove search for Kmymoney check it and it will install.

Another way to do this (I think it's easier to do it this way) is to open a terminal and copy and paste the following commands

sudo apt-get update

(it will ask for a password)

then

sudo apt-get install kmymoney2

---


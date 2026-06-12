---
title: "Update Error"
date: 2011-12-05
forum: New to Ubuntu
---

### Post by spsanderson on 2011-12-05
Hi everyone, 

I'm a noob and therefore quite un-knowledgeable.  I'm trying to update my system by typing in the following:

sudo apt-get update && sudo apt-get upgrade in the terminal.  I get the following message:
See attached screenshot please

spsanderson
noob non-extrodinaire

---

### Post by fantab on 2011-12-05
Welcome to the forum!

Run the following commands in the terminal one by one:[INDENT]```
$ sudo -i
 # apt-get clean
 # cd /var/lib/apt
 # mv lists lists.old
 # mkdir -p lists/partial
 # apt-get clean
 # apt-get update
 # cd
 # exit
``` [/INDENT]

---

### Post by spsanderson on 2011-12-05
sweetness thank you!!!!! I followed the lines exactly, then after it updated there was nothing new to upgrade lol. I typed exit and it brought me back to my original command line where I again typed sudo apt-get update && sudo apt-get upgrade, it went through with no errors and there was nothing to upgrade.

Thank you so much for your help!!!

---


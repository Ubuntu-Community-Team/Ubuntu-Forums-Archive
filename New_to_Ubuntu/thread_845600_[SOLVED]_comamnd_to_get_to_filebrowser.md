---
title: "[SOLVED] comamnd to get to filebrowser?"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by tjwoosta on 2008-06-30
ok i had all my desktop icons setup perfectly, untill i decided to put all my launchers on awn and delete the desktop icons


i restarted ubuntu and awn (as it turns out) is not reliable because now all the launchers that i put on awn had dissapeared

now im left with no icons on my desktop or awn, so i have to make them again

the problem is that i cant remember the command to get to the filesystem

(for instance i want a desktop icon to get to my / directory)

i remember the command goes something like this
```
file:///
```

but it wont work

what is the correct command?

---

### Post by dje on 2008-06-30
try:
```
nautilus /
```
just replace / (which is the filesystem) with any path ;)

dje

---

### Post by Mornedhel on 2008-06-30
The simplest command to open a navigator to the folder "yourfolder" is nautilus yourfolder .

---

### Post by nowshining on 2008-06-30
Put the below in the command box, etc.. - it should auto-icon, etc..

```
 
system:/
trash:/

**or if that doesn't work:**

system://
trash://

```

system- my computer like
trash - like recycle bin

---

### Post by tjwoosta on 2008-07-01
yea thanks guys,  nautilus /  works fine


although its not what i was using before to do the same thing

---

### Post by nowshining on 2008-07-01
lolz

---


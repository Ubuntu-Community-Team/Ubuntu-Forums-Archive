---
title: "moving duplicate file names..help.."
date: 2008-07-01
forum: New to Ubuntu
---

### Post by hopelessone on 2008-07-01
Hi,

I move alot of duplicate files (p2p) from 1 folder to another and the only option is to SKIP or REPLACE..

I want to put a (1) after it like firefox does...

as sometimes the same files name but different sizes...

Can this be possible in some setting somewhere..?

thanks

---

### Post by ChameleonDave on 2008-07-01
I don't believe there is a setting for that, but a simple BASH script would achieve your objective very easily.  I'm sure an experienced basher will oblige.

---

### Post by ChameleonDave on 2008-07-01
OK, I've found a very easy way of doing it from the command line.

Let's say you have a directory on your desktop called "fruit", in which are files named "apples", "oranges" and "tomatoes".  You also have a directory called "veg", in which are files named "potatoes", "cucumbers" and "tomatoes".

You can set up this situation easily by pasting this:

```
cd ~/Desktop && mkdir fruit veg
cd fruit && touch apples oranges tomatoes
cd ../veg && touch potatoes cucumbers tomatoes
```

Let's say you want to throw all the fruit in with the veg.

Type this in at a terminal:

```

cd ~/Desktop
**mv --backup=t   fruit/*   veg/**
ls -l fruit
ls -l veg
```

You will see that "fruit" is now empty, and that veg contains all the files, including "tomatoes.~1~".

I'm sure you can adapt this for your media files.

---


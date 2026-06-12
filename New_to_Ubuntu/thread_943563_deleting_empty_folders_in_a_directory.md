---
title: "deleting empty folders in a directory"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by kaston on 2008-10-10
is there a quick and easy way of deleting all the empty folders in a directory?  there's no option of doing that in nautilus but i figure there is probably a quick line of unix code that i can run, i just don't know it.  thanks

---

### Post by aeiah on 2008-10-10
there is a way with nautilus. click 'view as list' (or hit ctrl+2) and click the size column so it displays the folders in order of how many items it contains. then just select all the ones with 0 items, which will be all at the top.

there will be a commandline way of doing it, and if you want it to do it recursivley then that'll be what you need, but this seems easier than writing a bash script that'll iterate through directories if what i described is all you need.

---

### Post by kaston on 2008-10-10
sorry, i should have specified that i have a lot of folders that contain 2 or 3 other empty folders.  so yeah i'd like to have a recursive script

---

### Post by Dacker on 2008-10-10
first alias this command to get the confirmation: 
[HTML]alias rm -r='rm -i'[/HTML]

therefore you can remove the directory within the confirmation.

---

### Post by kaston on 2008-10-10
thanks, i'm going to have to figure out what alias means though

---


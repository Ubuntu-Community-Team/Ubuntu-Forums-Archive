---
title: "can't suspend and hibernate on notebook"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by ziedrich on 2008-06-17
Hi all.

I can' suspend and hibernate my notebook using ubuntu >.<.. I don't use swap partition but I use swap file. MY notebook's RAM is 1.5 gb, and my swap file is 512 mb.

WHen I wanted to suspend, it said error cpu0 bla8.. and I couldn't return to desktop menu.. so I had to shut it down manually.. 

Help me and thanks!

---

### Post by Colin82 on 2008-06-17
In order to hibernate or suspend, I believe your swap has to be at least the same size as your physical memory.  I was having problems with hibernation failing sometimes, and my swap partition was the same size as my memory.  Increased my swap partition to double my memory and now works like a champ.  Try increasing your swap file to 2GB and see if that works.

---

### Post by hyper_ch on 2008-06-17
it has to be at least equal in size because it will require to dump all ram into the swap.

---

### Post by ziedrich on 2008-06-17
how to resize the swap file, can u give me the command ^^? thanks a lot.

---

### Post by Colin82 on 2008-06-17
You could just add another swap file of 1GB (1024 MB) and set its priority when you add it to your fstab.

See this [[COLOR="Blue"]post[/COLOR]]("http://ubuntuforums.org/showthread.php?t=89782") to add another swap file (just don't give it the same path as your old swap file).  Particularly post #3, then see post #4 to set the priority in fstab.

There is probably a way to resize it by turning off the swap file, creating a bigger swapfile with the same name of a larger size (overwriting your old swapfile) and then turning it back on, and your fstab shouldn't need to be updated that way.  Someone else might be able to confirm this, I've never tried it and don't have my Ubuntu computer with me (stuck at work on Windows).

---


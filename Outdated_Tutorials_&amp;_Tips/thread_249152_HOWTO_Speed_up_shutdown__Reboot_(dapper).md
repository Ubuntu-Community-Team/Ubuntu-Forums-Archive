---
title: "HOWTO: Speed up shutdown / Reboot (dapper)"
date: 2006-09-02
forum: Outdated Tutorials &amp; Tips
---

### Post by yopnono on 2006-09-02
Ok this is taken from Efty, in Efty they are going to remove some shutdown/reboot scripts. So I tried it myself on my dapper... it works great, much faster shutdown and reboot.

Read the section "Shutdown scripts in ubuntu-desktop" at
```
https://wiki.ubuntu.com/Teardown
```

I also attached two script for removal and restore on the shutdown/reboot scripts. 

This scripts are from my rc0.d and rc6.d content, it means that I may have more scripts to remove than you may have. Or less.

This is not a problem since I have included all the *original* scripts as well to be removed.

Extract the files from the compressed archive.
Then open the terminal in the location where you have extracted the files from the archive.

Then run the script as sudo 
To remove shutdown/reboot scripts.
```
sudo sh remove_shutdown_services.sh
```
To restore the shutdown/reboot scripts.
```
sudo sh restore_shutdown_services.sh
```

EDIT: Replaced the scripts, done a small modification

---

### Post by 2shanfernando on 2006-09-02
awesome thanks, what previously took (benchmarked before this script was run) about 1:05 now takes about 20 seconds in total to shutdown (almost as good as Windows with the User Profile Hive Cleanup utility - around 10 seconds!)

Would it be possible to first check that the file exists before removing it so we can tell what was disabled/removed? Maybe create a generic function, parse the file to remove as the argument and output if it was disabled... I had several items not found but all is good:-)

Thanks!

---

### Post by User_Program on 2006-09-03
Wow! Very nice thank you!

---

### Post by yopnono on 2006-09-03
> **2shanfernando said:**
>  I had several items not found but all is good:-)
Thanks!

Well thats what I said I may have more items to remove than you. But thats no problems, if the file is missing there is nothing to remove. So it's safe that way.

And this is only a simple script. If some one like they are free to make the scripts better.

---

### Post by tymek666 on 2006-09-03
thx, works great!

---

### Post by yopnono on 2006-11-28
Replaced the scripts, done a small modification

---

### Post by mid_night gypsy on 2006-11-28
Howdy,
 sounds cool,but I'm a little lost. how bout a how-to Thanks gypsy
[LEFT][/LEFT]

---

### Post by yopnono on 2006-11-28
> **mid_night gypsy said:**
> Howdy,
 sounds cool,but I'm a little lost. how bout a how-to Thanks gypsy
[LEFT][/LEFT]

Done, sorry that I did not included how to.

---

### Post by mid_night gypsy on 2006-11-28
thanks, big improvement in shutdown/reboot

---

### Post by jdong on 2006-11-28
> **2shanfernando said:**
> 
Would it be possible to first check that the file exists before removing it so we can tell what was disabled/removed? Maybe create a generic function, parse the file to remove as the argument and output if it was disabled... I had several items not found but all is good:-)


Removing a nonexistent file just prints out a harmless error message anyway.

It'd be even sweeter if we can get a script that parses the init scripts to determine if it does anything other than killing the process... 
 * opens up his todo-when-bored list *

---

### Post by yopnono on 2006-11-28
> **jdong said:**
> Removing a nonexistent file just prints out a harmless error message anyway.

It'd be even sweeter if we can get a script that parses the init scripts to determine if it does anything other than killing the process... 
 * opens up his todo-when-bored list *

Do you volunteer ;)

---


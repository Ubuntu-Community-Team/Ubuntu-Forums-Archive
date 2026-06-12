---
title: "Update manager not working"
date: 2011-10-06
forum: New to Ubuntu
---

### Post by Vanity on 2011-10-06
Hello, 

after spending a few days working on enabling my wifi through the forum under enable/disabe wifi button does nothing I performed a clean install of the latest ubuntu and went to run the updates then began working with an experienced member of the forum on trying to install firmware for the Broadcom drivers he then had me run a command to check on the updates I had done and I got an entire list of errors. here is the list of errors. 

I am by all means an absolute beginner to ubuntu but I am very impressed with the community through this forum I wanna thank all of the experienced ubuntu users for helping and teaching us newbies.

---

### Post by Vanity on 2011-10-06
if anyone has some idea of what I can do to make this all work I would be greatly appreciative and I am more than willing to learn and spend the time reading and doing research if someone could at least point me in the right direction. 

V

---

### Post by wolfen69 on 2011-10-06
Open Synaptic and see if your software sources are enabled. It's under Settings>Repositories.

---

### Post by wackawacka on 2011-10-07
> **Vanity said:**
> Hello, 

after spending a few days working on enabling my wifi through the forum under enable/disabe wifi button does nothing I performed a clean install of the latest ubuntu and went to run the updates then began working with an experienced member of the forum on trying to install firmware for the Broadcom drivers he then had me run a command to check on the updates I had done and I got an entire list of errors. here is the list of errors. 

I am by all means an absolute beginner to ubuntu but I am very impressed with the community through this forum I wanna thank all of the experienced ubuntu users for helping and teaching us newbies.


i had an issue with updates, i kept getting errors.  check your settings first.  

goto 

system/administration/software sources

then goto the updates tab and make sure the "X" is on the first two listed (important and recommended).  

go back to the first tab 

you may want to goto "download from:" and "choose best server" or "server from united states"  .... the latter works for me.  

maybe even goto the terminal and run this command:  

sudo apt-get clean

then run this command:  

sudo apt-get update

that's what worked for me.  sorry if it doesn't help but if you don't know these steps, they are a good experience to understand.

---

### Post by amjjawad on 2011-10-07
To make it easier for you, I attached a screen shot.

Also, to post the output of any Terminal Command here in the forum, please copy the output from terminal, write CODE between [] then paste the output on your thread and then finally put /CODE between [] at the end.

It will look like this:

```
 terminal output here 
```Or paste it here, select all and then click "#".

[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=8148[/IMG]

---


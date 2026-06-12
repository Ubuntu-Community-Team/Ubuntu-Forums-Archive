---
title: "sysvutils not upgrading"
date: 2013-05-21
forum: New to Ubuntu
---

### Post by mreyna16 on 2013-05-21
everytime i try and upgrade via ubuntu software center or synaptics package manager that package gives me an error and cant upgrade. ive had ubuntu for about 2 weeks and during these 2 weeks about 3 days running ubuntu i had the same problem. only thing back then was that when i got the error, i didnt ask how to solve it and tried to reinstall it. turns out i messed up my ubuntu like that and would like some help as to how to do this upgrade. so, any help?

---

### Post by Cheesemill on 2013-05-21
Can you run the following commands in a terminal and post the output back here please...
```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by mreyna16 on 2013-05-21
> **Cheesemill said:**
> Can you run the following commands in a terminal and post the output back here please...
```
sudo apt-get update
sudo apt-get dist-upgrade
```
[http://paste.ubuntu.com/5688776/](http://paste.ubuntu.com/5688776/)

---

### Post by arpanaut on 2013-05-21
I know nothing about sysvutils, but it looks like the .deb package from the hardy repositories is incompatible with raring.
Why, may I ask, do you have all those hardy repositories on your sources list?

Hardy has been dead and gone for many moons, I'm surprised you are even getting hits there.
Are you using the default mirrors that came with your system ?
The only thing I can suggest is to comment (#) those hardy entries in your sources and trying to update and upgrade again.

EDIT:  I just checked synaptic on my raring install and sysvutils is not installed nor is it available.
So, I would say that there lies your problem.

Is this a fresh install or have you been upgrading for a long time?

---

### Post by mreyna16 on 2013-05-22
this is a fresh install, so what exactly do i need to remove? because last time i was trying to upgrade the same package, it wouldnt do it, so i pressed the reinstall button and it messed up my ubuntu and had to do a fresh install, again.

---

### Post by arpanaut on 2013-05-22
The question is, what did you try to install and/or where did the references to hardy in your software sources.
I think that if you edit out i.e. place a # in front of any references to hardy in your /etc/apt/sources.list.
then save the file, and run 
```
sudo apt-get update && sudo apt-get upgrade
```
This should clear up the problem.
take a look at this: [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

But first answer how those entries got in your sources.list.
Did you add any PPA's, did you follow any tutorial that had you add things to your repositories.
I don't know what you have done so I don't know if this will cause problems.
It shouldn't but who knows.

---

### Post by mreyna16 on 2013-05-22
to be honest i dont know how they got there, my guess, and i think im right is when i installed all the android repositories to build my own android rom but i could be wrong

---

### Post by arpanaut on 2013-05-22
From where did you get the instructions for getting the android repos installed?
They may have been for an older version of Ubuntu. 
What is trying to be installed is the package from hardy and I would presume is incompatible with raring.

building android roms may need this package, but since newer Ubuntu releases don't use sysv I don't know how this would work.

Look for some instructions for building android stuff specific to the version of Ubuntu you are running.
You may need to back out of what you have done to proceed

Good Luck.
Hopefully someone who knows more about this comes along,
Try correcting your sources.list and see if this fixes things.

---

### Post by mreyna16 on 2013-05-22
whats the easiest way to start off fresh? if possible id like to keep my apps installed

---


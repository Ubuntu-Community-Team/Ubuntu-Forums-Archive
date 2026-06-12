---
title: "how to delete file named &quot; $ sudo chmod"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by melbourne on 2008-05-26
hi ther 
 i am a linux newbie,
now on my first day wid ubuntu , follwed a how to (actually didnt follow) change mac address , i have accidentally created a file in my /etc/init.d  directory wid the name " $ sudo chmod +x changemac"...hhahahaha.now even i laugh at it ..now i want to delete this file ,wen i try to do so it says  

----------------- ----------------------------------
rm: cannot remove `$': No such file or directory
rm: cannot remove `sudo': No such file or directory
rm: cannot remove `chmod': No such file or directory
rm: cannot remove `+x': No such file or directory
rm: cannot remove `changemac': No such file or directory
--------------------------------------------------------
i used sudo rm .please help me delete this file

---

### Post by Primefalcon on 2008-05-26
try running thing command

sudo nautilus

in that window navigate to where the file is and delete it

---

### Post by philinux on 2008-05-26
Make sure you use 

gksudo nautilus

To use rm put "" marks round the names of files with spaces.

Or use the tab key in terminal for it to autocomplete the file name.

---

### Post by quinnten83 on 2008-05-26
> **melbourne said:**
> hi ther 
 i am a linux newbie,
now on my first day wid ubuntu , follwed a how to (actually didnt follow) change mac address , i have accidentally created a file in my /etc/init.d  directory wid the name " $ sudo chmod +x changemac"...hhahahaha.now even i laugh at it ..now i want to delete this file ,wen i try to do so it says  

----------------- ----------------------------------
rm: cannot remove `$': No such file or directory
rm: cannot remove `sudo': No such file or directory
rm: cannot remove `chmod': No such file or directory
rm: cannot remove `+x': No such file or directory
rm: cannot remove `changemac': No such file or directory
--------------------------------------------------------
i used sudo rm .please help me delete this file

$ is part of your command prompt name (when you don't have administrator rights)
Sudo is the command you use to give you administrator rights
chmod is the command you use to change the filetype, +x is an argument of the chmod command, 
the only thing that might be a file is the changemac, So that is the only thing you can delete.

---

### Post by Primefalcon on 2008-05-26
i was talking about running 

sudo nautilus 

from the terminal that'll open up the window still I just tested it, you only need to use gksudo in front of a command in the menu or such from the graphical side

---

### Post by Xiong Chiamiov on 2008-05-26
> **Primefalcon said:**
> i was talking about running 

sudo nautilus 

from the terminal that'll open up the window still I just tested it, you only need to use gksudo in front of a command in the menu or such from the graphical side
I'm not sure who you're responding to, but I'm pretty sure they weren't talking to you.

It's a good habit to get into to use gksudo (or kdesudo) for launching graphical apps.  Before doing so, I noticed that Konqueror would always have a tendency to change the permissions of my bookmarks.xml and then bug me later that it couldn't modify it until I chown-ed it.

---

### Post by Primefalcon on 2008-05-26
when running from the terminal didn't realize there was that much of a difference, I've not had anything buggy yet, but I'll take your advise as your probably been at this longer than I

---

### Post by Xiong Chiamiov on 2008-05-26
> **Primefalcon said:**
> when running from the terminal didn't realize there was that much of a difference, I've not had anything buggy yet, but I'll take your advise as your probably been at this longer than I
Just coming on 5 months Linux experience.  Learned quite a bit in that time, but I know a lot less than many people here.  I'm just speaking from experience.

---

### Post by Primefalcon on 2008-05-26
been about 1 month here, so thats 4 months more than me lol, so far I have the graphical interface down.

Have most of the basics down with the terminal such as editing, copying moving chmoding and so forth, but still getting with the finer points so to speak

---

### Post by Xiong Chiamiov on 2008-05-26
I'm slowly getting more comfortable in a terminal window, as it tends to be faster for some things.  Chmod is something I most certainly haven't mastered yet, but in case anyone wants to know, there is an excellent explanation [here]("http://ubuntuforums.org/showthread.php?t=425260").

---

### Post by philinux on 2008-05-26
I found this last year. I always gksudo for graphical apps like nautilus.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---


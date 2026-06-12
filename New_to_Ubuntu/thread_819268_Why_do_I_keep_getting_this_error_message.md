---
title: "Why do I keep getting this error message??"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by dunbrokin on 2008-06-05
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/Release](http://archive.ubuntu.com/ubuntu/dists/hardy/Release) Unable to find expected entry web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...pdates/Release](http://archive.ubuntu.com/ubuntu/dis...pdates/Release) Unable to find expected entry web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...curity/Release](http://archive.ubuntu.com/ubuntu/dis...curity/Release) Unable to find expected entry web/binary-i386/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

Why do I keep on getting this message when I try to update my packages?

---

### Post by powerpleb on 2008-06-05
> **dunbrokin said:**
> Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/Release](http://archive.ubuntu.com/ubuntu/dists/hardy/Release) Unable to find expected entry web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...pdates/Release](http://archive.ubuntu.com/ubuntu/dis...pdates/Release) Unable to find expected entry web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...curity/Release](http://archive.ubuntu.com/ubuntu/dis...curity/Release) Unable to find expected entry web/binary-i386/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

Why do I keep on getting this message when I try to update my packages?

No idea if this will work but it's worth a shot.
Go into System>>Administration>>Software Sources

Click on the Download From button>>Other
Click on Select Best Server

Wait till it finds the best one, then update by pressing Reload button.

---

### Post by drs305 on 2008-06-05
The problem is a corrupted sources.list. Something has added extra information to the addresses, probably the word *web*. If you post the results of the following we can clean it up for you. It's a pretty easy fix.

```
cat /etc/apt/sources.list
```

To see just the active lines:
```
cat /etc/apt/sources.list | grep -v "#"
```

---

### Post by plucky on 2008-06-05
Your **Sources.list** file is the problem

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.old
```
This will make a copy of your sources list file in case of mistakes. 
```
gksudo gedit /etc/apt/sources.list
```
Enter password and you will start to edit your sources list file

Scroll down and examine the lines that begin with **deb**,for example:-
> deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy multiverse web

On each line that has [color=red]web[/color] remove the word web from each of the lines.When you have finished,save the file and then in a terminal window ```
sudo apt-get update
sudo apt-get upgrade
```

Your problem should be fixed.

Good Luck

---

### Post by dunbrokin on 2008-06-05
> **powerpleb said:**
> No idea if this will work but it's worth a shot.
Go into System>>Administration>>Software Sources

Click on the Download From button>>Other
Click on Select Best Server

Wait till it finds the best one, then update by pressing Reload button.

No, sorry, it went through the whole thing and still came up with the same error.....

---

### Post by dunbrokin on 2008-06-05
> **plucky said:**
> Your **Sources.list** file is the problem

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.old
```
This will make a copy of your sources list file in case of mistakes. 
```
gksudo gedit /etc/apt/sources.list
```
Enter password and you will start to edit your sources list file

Scroll down and examine the lines that begin with **deb**,for example:-


On each line that has [color=red]web[/color] remove the word web from each of the lines.When you have finished,save the file and then in a terminal window ```
sudo apt-get update
sudo apt-get upgrade
```

Your problem should be fixed.

Good Luck

Thanks....that seemed to work a treat.....

---


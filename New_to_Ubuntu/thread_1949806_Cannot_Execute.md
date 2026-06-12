---
title: "Cannot Execute"
date: 2012-03-31
forum: New to Ubuntu
---

### Post by lemonlimecrime on 2012-03-31
I want to install the Sims 2 but I cannot mark the file as executable, the box unchecked itself. I don't know anything about using the terminal. Help please!

---

### Post by zombifier25 on 2012-03-31
It seems you need to be root to change its permission.
Open a terminal, and
```
**sudo** chmod +x /link/to/executable
```

---

### Post by lemonlimecrime on 2012-03-31
> **zombifier25 said:**
> It seems you need to be root to change its permission.
Open a terminal, and
```
**sudo** chmod +x /link/to/executable
```
   
I typed in exectly that and it said No such file or directory.

---

### Post by codemaniac on 2012-03-31
lemonlimecrime
**/link/to/executable** should be the absolute path to the file you want to make it executable .Replace it with your files's absolute path .

---

### Post by jerome1232 on 2012-03-31
Is the file on a cd?

if so then open a terminal (ctrl+alt+t)

type 'wine' without the quotes, hit space, then drag and drop the file you want to run. Hit enter.

If it's on your actual computer, then you need to subsitute the actual path to the file in that chmod command, just drag and drop it in for an easy way to do that.

---

### Post by lemonlimecrime on 2012-03-31
> **codemaniac said:**
> lemonlimecrime
**/link/to/executable** should be the absolute path to the file you want to make it executable .Replace it with your files's absolute path .

Very sorry! What is the absolute path? I am very new!

---

### Post by zombifier25 on 2012-03-31
:shock:
You need to replace /link/to/executable with the location of the Sims executable.


...wait, The Sims 2 is a Windows game, correct? If so, you need to use Wine in order to run Windows games under Linux.
Install Wine by
```
sudo apt-get install wine1.4
```If that doesn't work, try
```
sudo apt-get install wine1.3
```

---

### Post by lemonlimecrime on 2012-03-31
> **zombifier25 said:**
> :shock:
You need to replace /link/to/executable with the location of the Sims executable.


...wait, discard everything I have said. The Sims 2 is a Windows game, correct? If so, you need to use Wine in order to run Windows games under Linux.
Install Wine by
```
sudo apt-get install wine1.4
```If that doesn't work, try
```
sudo apt-get install wine1.3
```
 
I have Wine. So let me try to understand. The Sims installation is on 4 disks, divided up into 4 parts. Because disks are Read-Only (I think), would I be modifying the disk?  I am very sorry! I don't quite understand. :/

---

### Post by lemonlimecrime on 2012-03-31
> **jerome1232 said:**
> Is the file on a cd?

if so then open a terminal (ctrl+alt+t)

type 'wine' without the quotes, hit space, then drag and drop the file you want to run. Hit enter.

If it's on your actual computer, then you need to subsitute the actual path to the file in that chmod command, just drag and drop it in for an easy way to do that.


I did and nothing happened.

---

### Post by jerome1232 on 2012-03-31
Instead of saying nothing happened, please post what the terminal output of each command was. Include the command you ran in the output. Highlight what you want to copy in your terminal, then middle click to paste, or ctrl+shift+c to copy, then the regular ctrl+v in your browser to paste.

Wrap the output in code tags by going advanced, highlighting all of the output, and click the # symbol in your toolbar.

---

### Post by jerome1232 on 2012-03-31
on another note, I doubt you'll get sims 2 to play, always check the wine database when you want to try and run something in wine

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2633](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2633)

---

### Post by lemonlimecrime on 2012-03-31
> **jerome1232 said:**
> Instead of saying nothing happened, please post what the terminal output of each command was. Include the command you ran in the output. Highlight what you want to copy in your terminal, then middle click to paste, or ctrl+shift+c to copy, then the regular ctrl+v in your browser to paste.

Wrap the output in code tags by going advanced, highlighting all of the output, and click the # symbol in your toolbar.
My input
```
ray@Fonzie:~$ wine '/media/Sims2_1/setup.exe' 

```

output```

ray@Fonzie:~$ 

```

Very sorry. That is all that it said. Copy/pasted exactly as shown.

---

### Post by lemonlimecrime on 2012-03-31
> **jerome1232 said:**
> on another note, I doubt you'll get sims 2 to play, always check the wine database when you want to try and run something in wine

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2633](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2633)


So there is no way to get it to work?

---

### Post by jerome1232 on 2012-03-31
unfortunately I don't know how to proceed to figure it out, if you check the link I provided, you should get further than that, but currently wine won't run sims 2 anyways.

---

### Post by lemonlimecrime on 2012-03-31
> **jerome1232 said:**
> unfortunately I don't know how to proceed to figure it out, if you check the link I provided, you should get further than that, but currently wine won't run sims 2 anyways.
Thank you for your help.

---


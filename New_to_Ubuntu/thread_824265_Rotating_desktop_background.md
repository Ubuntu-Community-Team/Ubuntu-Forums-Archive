---
title: "Rotating desktop background"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by lsaplai on 2008-06-09
Hello all,

I'm currently using Ubuntu 8.04 with Gnome desktop.

I'm using to the KDE desktop where I can set a "rotating" desktop background so that every so often (interval that I decide), the background changes. This way I can use several background images that I like and they keep changing automatically.

How can I do this in Ubuntu? The Desktop Background setup only allowa to choose 1 picture.

Thanks in advance!

---

### Post by chinchilla2392 on 2008-06-09
thats a KDE only feature.. not gnome
```
sudo apt-get install kubuntu-desktop
```
if you want KDE
then click on session and select KDE at the login screen

---

### Post by jordanmthomas on 2008-06-09
You can change the wallpaper with gconftool-2

It would be fairly trivial to write a bash script that reads a file of approved wallpapers and sets the wallpaper to a random one.  This script could be run by cron and voila!  

Here's how I would do it:
1.  Store all my wallpapers in a single folder.
2.  make a file in my home directory called randomwalls
3.  In this file, put the names of the wallpapers you want to randomly add:
```

a.jpg
b.jpg
c.png
...

```
4.  Write a bash script that works something like this:
```

#!/bin/bash

#number of wallpapers you have available
NUM=$(wc -l ~/randomwalls | awk '{print $1}')

#get a random number between zero and the end of your file
CHOOSE=`echo "($RANDOM % $NUM) + 1" | bc`

#pick the line out of the list of wallpapers with the name of the file
WALLPAPER=$(head -n $CHOOSE randomwalls | tail -n 1)

#actually set the wallpaper using gconf
gconftool-2 --set /desktop/gnome/background/picture_filename --type string $HOME/wallpaper/$WALLPAPER

```

5. chmod +x your script and add it to cron to be run however-so-often you want.

---

### Post by chinchilla2392 on 2008-06-10
i was giving an easier option ;)
also assuming he is a KDE fan.
your solution is better though..

---

### Post by asrai on 2008-06-10
An even easier option is to install a little app called drapes.  It is in the repos and will do just what you're after.  Hope that helps.

---

### Post by lsaplai on 2008-06-10
Thanks everyone for the replies. For the time beimg I'm going to go for the easy, lazy solution and try Drapes, unless something better is suggested.

I use KDE on my laptop but I like the simplicity of Gnome on my desktop so I'm staying with it. Installing KDE edsktop would therefore not be the solution.

And writing a script, even with such good example, I'm not sure I'd do that at the moment. But I should keep it and study it for the future!

Cheers!

---


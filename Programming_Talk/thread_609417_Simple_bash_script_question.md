---
title: "Simple bash script question"
date: 2007-11-10
forum: Programming Talk
---

### Post by harold4 on 2007-11-10
I am currently using this script in kde to change my wallpaper to a random wallpaper and it works for the most part.  (Original script found on appleInsider.com)  

I'd like to snag only .png and .jpg out of the $dir.  
The commented line illustrates what I'm trying to accomplish, with a generic regular expression.  Using the commented line, the script breaks.

Any suggestions are appreciated.


```
#!/bin/bash
dir=/usr/share/wallpapers/

pics=(${dir}*)
#pics=$(ls $dir | grep [.]...$)

numpics=${#pics}
img=${pics[$((RANDOM%numpics))]}
dcop kdesktop KBackgroundIface setWallpaper $img 6

```

---

### Post by arsenic23 on 2007-11-10
I think you should just be able to do this:

```
 pics=(${dir}*.[pPjJ][nNpP][gG])
```

I think.

---

### Post by harold4 on 2007-11-10
It's always the simple stuff that gets overlooked.  

That did the trick, thanks.  :)

---

### Post by stroyan on 2007-11-11
You can use 
pics=(${dir}*.{png,jpg})
to match a list of specific suffixes.

The 
numpics=${#pics}
line looks wrong.  That evaluates to the number of chars in $pics[0].
You want
numpics=${#pics[@]}
to evaluate to the number of elements in the "pics" array.

---

### Post by harold4 on 2007-11-11
Current script:

```
#!/bin/bash
dir=/usr/share/wallpapers/
pics=(${dir}*.{png,jpg})
numpics=${#pics[@]}
img=${pics[$((RANDOM%numpics))]}
curImg=$(dcop kdesktop KBackgroundIface currentWallpaper 1)

if [ $img = $curImg ]; then
        change_wallpaper #script name
        exit
fi
dcop kdesktop KBackgroundIface setWallpaper $img 6
```

Only other change I see is the 1 in this line to "currentDesktopNumber."
```
curImg=$(dcop kdesktop KBackgroundIface currentWallpaper 1)
```

---

### Post by Whiffle on 2007-11-11
Am i missing something, or can you not just right click the desktop, select slide show, and check the  "random" box?

---

### Post by harold4 on 2007-11-11
Random on demand, not on a set time.

---

### Post by Whiffle on 2007-11-11
Okay just checking :)

---

### Post by harold4 on 2007-11-11
:-P

Originally, I was using the KDE built-in functionality, but with a script like this, any new images are automatically added when they are saved to the $dir.

Then if you cron the script, it's just a little more versatile version of what currently exists.  IMO

---

### Post by harold4 on 2007-11-12
Most recent version :-P

```
  GNU nano 2.0.6       File: /home/ac/bin/change_wallpaper

#!/bin/bash
function getNewPaper {
        dir=/usr/share/wallpapers/
        pics=(${dir}*.{png,jpg})
        numpics=${#pics[@]}
        img=${pics[$((RANDOM%numpics))]}
}

function getCurPaper {
        curImg=$(dcop kdesktop KBackgroundIface currentWallpaper 1)
}

while [ $img = $curImg ]
do
        getNewPaper
        getCurPaper
done

dcop kdesktop KBackgroundIface setWallpaper $img 6

exit 0
```

Going to add a counter to the while at some point to avoid an infinite loop.

---


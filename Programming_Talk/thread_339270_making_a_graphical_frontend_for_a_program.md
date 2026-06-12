---
title: "making a graphical frontend for a program"
date: 2007-01-15
forum: Programming Talk
---

### Post by xmastree on 2007-01-15
Hi guys. First of all, I have **no** programming experience at all. None. Nada. :confused: 

So, with that in mind, here goes:

I have a command-line program which I currently run with a script to pass all the parameters to it. If I want to alter something, I edit the script.

How can I make a graphical front end with which I can select the various options by clicking them rather than editing the script all the time?

The program normally runs like:
./foo -a 0 -b 3 -c 3 -d +2.0
followed by
./bar -a 0 -b 3 -e 999
and I want to run it a number of times and put the output (jpg files) in DIR

```


#Set up the parameters here

NUMBER=50
PARAM1=0
PARAM2=3
PARAM3=3
PARAM4=+2.0
PARAM5=999
DIR=testing

# next we create the output directory

mkdir ${DIR}

# let's go

for ((n=1; n<=${NUMBER}; n++))
do
    ./foo -a ${PARAM1}     \
           -b ${PARAM2} \
           -c ${PARAM3} \
           -d ${PARAM4}

    ./bar -a ${PARAM1}     \
           -b ${PARAM2} \
           -e ${PARAM5}
     mv *.jpg ${DIR}/
done

```
Apart from NUMBER, all the other parameters are limited to one of about 5 options. I would also like the option to run ./bar after or before the **done**, so it either runs every time or just at the end.


Where would I start? :-k

---

### Post by peabody on 2007-01-15
Zenity comes to mind for this purpose.  I confess I'm no zenity expert, but I believe it should be installed per default in Ubuntu.  "man zenity" in a terminal comes to mind.

---

### Post by Wybiral on 2007-01-15
I'm sorry if I misread your post, but if it's a graphical frontend for shell your looking for... zenity is amazing.

Type "man zenity" in the command line and it will come up with some cool stuff.

Zenity allows you to do this kind of stuff...

```

#!/bin/bash

if $(`zenity  --question --title "???"   --text  "Ok or cancel?"`); then
	zenity --info --text "You selected OK!"
else
	zenity --info --text "You selected Cancel!"
fi

file1=`ls |  zenity  --list  --title "Contents viewer" --text "Contents of directory" --column "Files"`

name=`zenity --title  "Name?" --entry --text "Whats your name?"`

file2=`zenity --title="Well $name, select a file!" --file-selection`

choice=`zenity  --list --title "$name, does this look right?" --checklist --text "" --column "Install" --column "File" TRUE $file1 TRUE $file2`

zenity --info --text "You selected: $choice"

```

That example doesn't actually DO anything, it's just showing off zenity.

---

### Post by Wybiral on 2007-01-15
Lol, you beat me to it by a few seconds!

---

### Post by chocolatemintmocha on 2007-01-15
Very cool!

---

### Post by xmastree on 2007-01-16
Zenity, huh? Ok, thanks guys, I'll do some reading and see what I can come up with.

---

### Post by xmastree on 2007-01-28
Right, I've had a little read, and done a little messing around, and come up with something workable. It's not exactly what I was looking for, but it's a step in the right direction. (I really wanted to see all the parameters at once, rather than setting each one individually)

Anyway, I've hit a slight problem.

The actual program is for controlling a camera, and one of the parameters is exposure compensation. Valid values are -2.0 to +2.0 in 0.5 steps.

Here's the problem command:

```
zenity --height 350 --list --title "Exposure" --radiolist --text "Exposure Compensation" --column "" --column "stops" FALSE +2.0 FALSE +1.5 FALSE +1.0 FALSE +0.5 TRUE 0.0
```

As it stands that works, but if I add FALSE -0.5 (or "-0.5") to the end, it spits the dummy. [-( 

Is there a way round this?


Secondly, this line:

```
zenity --height 150 --list --title "Resolution" --radiolist --text "Image Dimensions" --column "" --column "" --column "" TRUE 0 "640x480" FALSE 1 "1152x864"
```

It works fine, but is there a way to hide the second column? I want to select either 640 or 1152, but pass 0 or 1 to the program. That's not really a major issue, it would just look better.

Edit: found it:  --hide-column 2
```
zenity --height 150 --list --title "Resolution" --radiolist --hide-column 2 --text "Image Dimensions" --column "" --column "" --column "" TRUE 0 "640x480" FALSE 1 "1152x864"
```

---


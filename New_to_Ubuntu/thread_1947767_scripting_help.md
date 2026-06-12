---
title: "scripting help"
date: 2012-03-27
forum: New to Ubuntu
---

### Post by rburkartjo on 2012-03-27
since ldxe doesnt have a wallpaper changer i am using the following script to rotate my wallpapers-works great
#!/bin/bash

DIR=/home/ray/pictures
FLOOR=1
RANGE=`ls -1 "$DIR"/*.jpg | wc | awk '// {print $1}'`

number=0

while [ 1 -eq 1 ]; do
   
   number=$RANDOM
   while [ "$number" -le $FLOOR ]; do
        number=$RANDOM
   done
   let "number %= $RANGE"  # Scales $number down within $RANGE.
   COUNTER=1
   for X in "$DIR"/*.jpg
   do
      if [ $number -eq $COUNTER ]; then
         pcmanfm --set-wallpaper "$X"
      fi
   COUNTER=$(($COUNTER+1))
   done
   COUNTER=1
   sleep 2m
done

i need a separate script to stop changing wallpapers if possible.
tks

---

### Post by Paqman on 2012-03-27
> **rburkartjo said:**
> 
i need a separate script to stop changing wallpapers if possible.


Under what conditions? Couldn't you just add this functionality to your existing script?

---

### Post by rburkartjo on 2012-03-27
paq just want to be able to stop the wallpaper changer if i want and dont know how to do. like changing the wallpapers but at times need to stop the slideshow. tks

---

### Post by kevdog on 2012-03-27
So your stop script should basically query ps to find the process number of your wallpaper changer process, and then send a command to kill the process.

---

### Post by Paqman on 2012-03-27
Yeah, the straightforward option would be to simply kill your script. 

If you wanted something you could toggle I'd just go for something simple like an addition to your script. Have it check for the presence of a file on your desktop called "stop" or something, and sit there and wait if it's present. So to stop and start the script all you need to do is create or delete the file.

---

### Post by rburkartjo on 2012-03-27
i dont know how to write the script. i just found this one thru searching. so if someone could show me what to add etc. would appreciate it tks for the extra effort

---

### Post by rburkartjo on 2012-03-28
could not figure out how to do. so i am just using the system monitor application to kill process

---

### Post by WasMeHere on 2012-03-28
> **rburkartjo said:**
> could not figure out how to do. so i am just using the system monitor application to kill process
Start the script in the background with the command
```
wallpaper-changer & pid=$!
```
and then stop it with
```
kill $pid
```

---

### Post by asmoore82 on 2012-03-28
This line is really impressive: ```
for X in "$DIR"/*.jpg
```

That is the only perfect way to step through filenames in a shell loop.

This line could be re-written in a similar fashion: ```
RANGE=`ls -1 "$DIR"/*.jpg | wc | awk '// {print $1}'`
```

This would stamp out a bug for files that have extra special characters (newlines, etc.) in them:
```
RANGE="$(
for file in "$DIR"/*.jpg
do
    echo countme
done | wc -l
)"
```

Here's the script re-hacked to operate based on a "lock-file" and using a shell array so that you only have to "for-loop" the files once. The array also makes the script more awesome but maybe not more readable :P

```
pdir="$HOME/Pictures/Wallpapers"

picsa="none"
counter="0"
for pic in "$pdir"/*.jpg
do
    [ -f "$pic" ] || exit 1 
    picsa[$((counter++))]="$pic"
done

lock="$HOME/.config/cycle-wallpaper"
touch "$lock"
while [ -f "$lock" ]
do
   pcmanfm --set-wallpaper "${picsa[$(( RANDOM % ${#picsa[@]} ))]}"
   #OR
   #pcmanfm --set-wallpaper "${picsa[$(( RANDOM % counter ))]}"
   sleep 2m
done
```

Then the "stop" script could be like this:
```
lock="$HOME/.config/cycle-wallpaper"
[ -f "$lock" ] && unlink "$lock"
```

---


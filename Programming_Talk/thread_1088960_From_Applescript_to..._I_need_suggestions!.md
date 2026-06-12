---
title: "From Applescript to...?? I need suggestions!"
date: 2009-03-06
forum: Programming Talk
---

### Post by Jeby on 2009-03-06
Hi to all! :-)
I'm a Mac user, but I want to set up an ubuntu based dowload center/basic home server/basic media center. At now I'm using a MacBook Pro for all my tasks and when I need a solution for a repetitive task I use *Applescript* and *launchd* to launch the script.

For example, I've created a script that watch in a folder, search for .srt file, rename the file running "tvnamer.py", then move the renamed files in a prescribed folder and then notify me. Now I need to translate it in a scripting language compatible with linux.
First of all: what language? bash? python? I don't know, I'm only familiar with applescript... I'm not a programmer, my knowledge of scripting it's very basilar.

Then, once I've choosed the scripting language, I how can I traslate these:

```

tell application "Finder"
set added_items to name of every file of folder "Macintosh HD:Users:Jeby:Downloads:"
set added_items_e to name extension of every file of folder "Macintosh HD:Users:Jeby:Downloads:"
end tell

```

(Finder is the Mac file manager)

```
repeat with i from 1 to number of items in added_items
tell application "Finder"
set the the_file_name to the item i of added_items
set nameExt to item i of added_items_e
if nameExt is "srt" then
set cmd to "python tvnamer.py -ba " & quoted form of the_file_name
do shell script cmd
end if
end tell
end repeat

```

			
```

if the_file_name contains "]-Being Human" then
...			
else if the_file_name contains "]-Forbidden Science" then
...
end if

```



thanks and sorry for my bad English! :-)

---

### Post by jimi_hendrix on 2009-03-06
this screams bash to me, but bash looks...kinda...alien some times with a lot of different brackets (you get used to it fast though)...bash is also installed on macs by default so if you want to mess around with it pop open terminal

---

### Post by linuxisevolution on 2009-03-06
You would use linux shell scripting. Basically, pop open a terminal on Ubuntu and start playing around :D

---

### Post by Jeby on 2009-03-07
> **jimi_hendrix said:**
> this screams bash to me, but bash looks...kinda...alien some times with a lot of different brackets (you get used to it fast though)...bash is also installed on macs by default so if you want to mess around with it pop open terminal

I'm trying bash, it's cool! :D

I've done this preliminary script:

```
#!/bin/bash
#This is my first bash script and it's not working! :-)

#Change IFS because of space in name
original_ifs="$IFS";
IFS=$'\n';

#Set the TV Shows list and its length
Stitle=("Being Human" "Fringe")
ls="${#Stitle[@]}";

#Set working dir
dir1="/Users/Jeby/Desktop"

#loop for TV Shows title
for (( i=0; i<ls; i++ ))
do
    st=${Stitle[i]}
#loop for episode number
    for (( ep=1; ep<=30; ep++ ))
    do
#because I want 2 digit number
        if (( $ep <= 9 ));
            then
                e="E0$ep"
            else
                e="E$ep"
        fi
#loop for series number
        for (( sn=1; sn<=30; sn++ ))
        do
#because I want 2 digit number
            if (( $sn <= 9 ));
                then
                    s="S0$sn"
                else
                    s="S$sn"
            fi
#loop for file name
# k --> /Users/Jeby/Desktop/'[S02S01]-Being Human'*.*
            for k in "$dir1/'[$s$e]-$st'*.*"
            do
#check if file exist... I don't know why, this is not working
                if [ -e $k ];
                    then
#check if exist a folder for the TV Show: incredible, this work!!
                        fld="$dir1/'$st-$s'"
                        if [ -d $fld ];
                            then
# if exist, move file. I don't know why, this is not working
                                mv $k $fld
                            else
#if not, make the dir: incredible, this work!!
                                mkdir $fld
#and then move the file: "obviusly", this not works
                                mv $k $fld
                        fi
                fi       
            done
        done
    done
done

#restoring IFS
IFS="$original_ifs"
```

then I've created a lot of file on Desktop, like [S02E01]-Being Human-Title Here.png and so on and run the script, but it's doen't work.
First of all ```
[ -e $k ]
``` always return false althougth if i check with copy and past in Terminal
```
if [ -e /Users/Jeby/Desktop/'[S02E01]-Being Human'*.* ]
then
echo "true"
else
echo "false"
fi
```
this return me true.

then i delete  ```
if [ -e $k ]...
``` and I notice that something similar happens with mv.
```
mv $k $fld
```
doesn't work, althougth
[code]mv /Users/Jeby/Desktop/'[S02E01]-Being Human'*.* Users/Jeby/Desktop/'Being Human-S02']
works.

What's wrong?I think that the problem is "*.*" because the same operation with folder works.

---

### Post by jtourville on 2009-03-07
In bash, if you're using a variable that might have spaces in it, you should wrap it with quotes to pass it as a single argument to whatever command you're trying to use.

So try
```
if [ -e "$k" ]
```
and
```
mv "$k" "$fld"
```
instead.

---

### Post by jimi_hendrix on 2009-03-07
or use if [[ $foo = $bar ]]; then #i dont think you need quotes with double ['s

---

### Post by Jeby on 2009-03-07
thanks to all, still not working... maybe there is another error... :(

---


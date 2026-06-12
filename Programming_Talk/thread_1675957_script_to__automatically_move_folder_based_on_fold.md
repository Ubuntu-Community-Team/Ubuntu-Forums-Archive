---
title: "script to  automatically move folder based on folder name"
date: 2011-01-26
forum: Programming Talk
---

### Post by mbeltoft on 2011-01-26
I'm on the lookout for a script that automatically can move folders in my incoming folder based on their name (or some of it)
 
I had a look at this but it's not quite working for me.
[FONT=Calibri][http://art.ubuntuforums.org/showthread.php?t=1350251&page=2](http://art.ubuntuforums.org/showthread.php?t=1350251&page=2) [/FONT]
[FONT=Calibri][/FONT] 
[FONT=Calibri]what i want is:[/FONT]
[FONT=Calibri]If a folder containing the word simpsons in its name is in /incoming it should be moved to ~/tv/simpsons/[/FONT]
[FONT=Calibri]if a folder containing family.guy is in /incoming then it should be moved to ~/tv/family guy/[/FONT]
[FONT=Calibri]if a folder in /incoming don't match any of the above then it should be moved to ~/videos/[/FONT]
[FONT=Calibri][/FONT] 
[FONT=Calibri]Can anyone help me with as my script skills are somewhat none existing?[/FONT]
[FONT=Calibri]Thanks :D[/FONT]

---

### Post by ajgreeny on 2011-01-26
If you are doing all this from Firefox, install the add-on called **download sort** and use keywords to put the things in the right folder.

---

### Post by mbeltoft on 2011-01-26
I'm not doing it from firefox. The script is meant to run on a headless server and should be triggered whenever a folder is created in the incoming folder

---

### Post by hakermania on 2011-01-26
```
#!/bin/bash
touch /tmp/testdirb.$$
while true
do
ls /incoming > /tmp/testdira.$$
echo $(diff /tmp/testdira.$$ /tmp/testdirb.$$ | egrep '^[<>]' | cut -b 3- | grep simpsons)
mv /incoming/$(diff /tmp/testdira.$$ /tmp/testdirb.$$ | egrep '^[<>]' | cut -b 3- | grep simpsons) /home/alex/tv/simpsons/ 2> /dev/null
mv $(diff /tmp/testdira.$$ /tmp/testdirb.$$ | egrep '^[<>]' | cut -b 3- | grep family.guy) "/home/alex/tv/family guy" 2> /dev/null
cp /tmp/testdira.$$ /tmp/testdirb.$$
sleep 2 #EDIT THIS IF YOU WANT
done
```it works for me(if diff outputs more than one filename this doesn;t work. This means that this will work only if you have e.g. one file named simpsons.avi and a folder named family.guy_folder but not by having multiple files of simpsons or family.guy. If you want to work this way, you can output the diff's output to a file and then move with mv each line of the file wherever you want. ).

---

### Post by Vaphell on 2011-01-26
```

#!/bin/bash

incoming='~/incoming'
def_dest='~/movies'

# patterns and destinations, modify to suit your needs
pattern[0]='*simpsons*';   dest[0]='~/tv/simpsons'
pattern[1]='*family*guy*'; dest[1]='~/tv/family guy'
# can be written as
# pattern=( pat0 pat1 ...)
# dest=( dest0 dest1 ...)


# iterate the pattern array and move matching folders to proper destination
for (( i=0; i<${#pattern[@]}; i++ ))
do 
  echo pattern = ${pattern[i]}
  find "$incoming" -mindepth 1 -maxdepth 1 -type d -iname "${pattern[i]}" -exec mv -v "{}" "${dest[i]}" \;
  echo ---------
done

#move remaining folders to default destination
find "$incoming" -mindepth 1 -maxdepth 1 -type d -exec mv -v "{}" "$def_dest" \;

```

does the script need to empty the /incoming folder or should it leave already existing folders in place? my lameass script doesn't detect anything and doesn't know which folder is new. Once run it searches for patterns, moves found stuff to the appropriate dest dir, the rest is moved to the default dest dir.
Detection of new folders is a bit trickier but can be done. You really need to detect new folder once it's created or checking every 1 min or so is enough?

---

### Post by kurum! on 2011-01-26
> **Vaphell said:**
> ```

# patterns and destinations, modify to suit your needs
pattern[0]='*[sS][Ii][Mm][Pp][Ss][Oo][Nn][Ss]*';       dest[0]='~/tv/simpsons'
pattern[1]='*[Ff][Aa][Mm][Ii][Ll][Yy]*[Gg][Uu][Yy]*';  dest[1]='~/tv/family guy'

```


you can use find's -iname option

---

### Post by Vaphell on 2011-01-26
indeed, i modified the code

---

### Post by mbeltoft on 2011-01-27
> **Vaphell said:**
> ```

#!/bin/bash
 
incoming='~/incoming'
def_dest='~/movies'
 
# patterns and destinations, modify to suit your needs
pattern[0]='*simpsons*';   dest[0]='~/tv/simpsons'
pattern[1]='*family*guy*'; dest[1]='~/tv/family guy'
# can be written as
# pattern=( pat0 pat1 ...)
# dest=( dest0 dest1 ...)
 
 
# iterate the pattern array and move matching folders to proper destination
for (( i=0; i<${#pattern[@]}; i++ ))
do 
  echo pattern = ${pattern[i]}
  find "$incoming" -mindepth 1 -maxdepth 1 -type d -iname "${pattern[i]}" -exec mv -v "{}" "${dest[i]}" \;
  echo ---------
done
 
#move remaining folders to default destination
find "$incoming" -mindepth 1 -maxdepth 1 -type d -exec mv -v "{}" "$def_dest" \;

```
 
does the script need to empty the /incoming folder or should it leave already existing folders in place? my lameass script doesn't detect anything and doesn't know which folder is new. Once run it searches for patterns, moves found stuff to the appropriate dest dir, the rest is moved to the default dest dir.
Detection of new folders is a bit trickier but can be done. You really need to detect new folder once it's created or checking every 1 min or so is enough?
 
The script should empty the /incoming folder. I havent thought about detecting new folders but if it's possible to run the move part whenever there's a new folder in the incoming it would be great. I shouldn't be run right away though coz maybe there's still being written to the folder - Maybe it could run on folders that havent changed for 10 sek or something

---

### Post by Vaphell on 2011-01-27
i assume you have some ~/temp directory where stuff is downloaded and finished things are moved to incoming? If that's the case and both directories are on the same partition it should be instant and there is no risk of having incomplete data. You can run the script every minute or so without thinking too much

```
#!/bin/bash

while ((1))
do
  ./move_incoming.sh # that script above
                     # alternatively put the script's code
                     # for iteration and remaining stuff here
                     # and don't forget to put definitions before the while loop
  sleep 60
done

```
infinite loop where every 60 seconds the script is activated


of course it depends on your scenario. How long does it take to write a complete data of a single item in the incoming folder?

EDIT: uglier version of previous script with delay, in an infinite loop
```

#!/bin/bash

delay=60
incoming="$HOME/incoming"
def_dest="$HOME/movies"
 
# patterns and destinations, modify to suit your needs
pattern[0]='simpsons';    dest[0]="$HOME/tv/simpsons"
pattern[1]='family.*guy'; dest[1]="$HOME/tv/family guy"

while ((1))
do
    echo Checking folder...
    # generate list of folders
    find "$incoming" -mindepth 1 -maxdepth 1 -type d > "$incoming"/todo.txt
    # wait
    sleep $delay 

    while read dir
    do
        count=0
        for (( i=0; i<${#pattern[@]}; i++ ))
        do
            count=$( echo "${dir}" | grep -ice "${pattern[i]}" )
            if [ "$count" != "0" ]
            then
              # if dir matches, move to destination
              echo "$dir" matches "${pattern[i]}" pattern
              mv -v "$dir" -t "${dest[i]}"
              break
            fi
        done
        if [ "$count" = "0" ]
        then
          mv -v "$dir" -t "$def_dest" # not matching -> move to default dest dir
        fi
    done < "$incoming"/todo.txt
done

```
between generating the folder list (temporary file) and operating on it there is a delay of $delay seconds, so the new folder noticed by the script is at least $delay seconds old. It would be prettier if i knew what atime/ctime/mtime do in find command exactly - i don't so i hacked around

---

### Post by Bodsda on 2011-01-27
> **mbeltoft said:**
> 
[FONT=Calibri]Can anyone help me with as my script skills are somewhat none existing?[/FONT]

 
Based on that statement, you shouldnt run anything in this thread. You should be understanding what your going to copy and paste into a file and run. 
 
Crack open a couple of bash tutorials and see if you can work out what these scripts do, line by line. Start with Vaphell's latest one (the short one), that shouldn't take long to figure out, the go back and study his first post. Once your head hurts a bit and your begging for it to stop, type
```

man bash

```
 
Bodsda

---

### Post by mbeltoft on 2011-01-28
@Bodsda - You're right but I simply don't have the patience to learn it. I've tried more than once but after a few hours of trial and lots of errors and nothing working I give up.

@Vaphell - I tried your latest script. I modified the folder paths to match my setup but I get these errors:

move.sh: 8: pattern[0]=simpsons: not found
move.sh: 8: dest[0]=$HOME/Tv/Simpsons: not found

move.sh: 26: Syntax error: Bad for loop variable



oh and thanks for your help so far :)

---

### Post by Vaphell on 2011-01-28
my fault. I changed ~ to $HOME in paths but skipped testing it and left ' '. I had a brainless moment apparently. The problem is that ' ' treats the string literally and in such case $HOME is not substituted by its value. Change ' ' to " " in path definitions and try again.

I'll check what's going on with the loop, could you paste your current script?

EDIT: updated script

```

#!/bin/bash

delay=60
incoming="$HOME/incoming"
def_dest="$HOME/movies"
 
# patterns and destinations, modify to suit your needs
pattern[0]='simpsons';    dest[0]="$HOME/Tv/Simpsons"
pattern[1]='family.*guy'; dest[1]="$HOME/Tv/Family Guy"

# make sure target directories exist
for (( i=0; i<${#dest[@]}; i++ ))
do
    mkdir -p "${dest[i]}"
done
mkdir -p "$def_dest"

# main loop
while ((1))
do
    echo Checking folder...
    # generate list of folders
    find "$incoming" -mindepth 1 -maxdepth 1 -type d > "$incoming"/todo.txt
    
    if [ -s "$incoming"/todo.txt ]
    then
        echo 'Folders found!'
    fi
   
    # wait
    sleep $delay 

    while read dir
    do
        count=0
        for (( i=0; i<${#pattern[@]}; i++ ))
        do
            count=$( echo "${dir}" | grep -ice "${pattern[i]}" )
            
            if [ "$count" != "0" ]
            then
                # if dir matches, move to destination
                echo "$dir" matches "${pattern[i]}" pattern
                mv -v "$dir" -t "${dest[i]}"
                break
            fi
        done
        
        if [ "$count" = "0" ]
        then
            mv -v "$dir" -t "$def_dest" # not matching -> move to default dest dir
        fi
    done < "$incoming"/todo.txt
done

```
copied pretty much verbatim from my test script file

---

### Post by mbeltoft on 2011-01-28
hmm..

it's still making the same errors:


move.sh: 8: pattern[0]=simpsons: not found
move.sh: 8: dest[0]=/home/beltoft/Tv/Simpsons: not found
move.sh: 9: pattern[1]=family.*guy: not found
move.sh: 9: dest[1]=/home/beltoft/Tv/Family guy: not found
move.sh: 12: Syntax error: Bad for loop variable


The folders are present and is spelled correct so it's not that :confused:

---

### Post by Vaphell on 2011-01-28
could you paste your script?

upgraded to skip temporary file to save file list, variable holds it now... and it's definitely working on my system in my test case with dummy folders :) i have few directories that i cut paste from target dir to incoming dir and check if the condition is triggered and if they are moved again.

```
#!/bin/bash

IFS=$'\n'  # newline as separator to tackle spaces in names
           # and generally make life easier

delay=10
incoming="$HOME/test/inc"
def_dest="$HOME/test/movies"
 
# patterns and destinations, modify to suit your needs
pattern[0]='simpsons';    dest[0]="$HOME/test/tv shows/"
pattern[1]='family.*guy'; dest[1]="$HOME/test/tv shows/"

# make sure target directories exist (try to create them)
for (( i=0; i<${#dest[@]}; i++ ))
do
    mkdir -p "${dest[i]}"
done
mkdir -p "$def_dest"

# main loop
while ((1))
do
    echo Checking folder...
    # generate list of folders
    dirs=$(find "$incoming" -mindepth 1 -maxdepth 1 -type d)
    
    if [ ! -z "$dirs" ]
    then
        echo 'Folders found!'
        echo "$dirs"
        echo ------------------------------
    fi

    # wait
    sleep $delay 

    for dir in $dirs
    do
        count=0
        for (( i=0; i<${#pattern[@]}; i++ ))
        do
            count=$( echo "${dir}" | grep -ice "${pattern[i]}" )
            
            if [ "$count" != "0" ]
            then
                # if dir matches, move to destination
                echo "$dir" matches "${pattern[i]}" pattern
                mv -v "$dir" -t "${dest[i]}"
                break
            fi
        done
        
        if [ "$count" = "0" ]
        then
            mv -v "$dir" -t "$def_dest" # not matching -> move to default dest dir
        fi
    done
done
```

---

### Post by mbeltoft on 2011-01-28
Strange. Still the same errors:

move.sh: 8: pattern[0]=simpsons: not found
move.sh: 8: dest[0]=/home/beltoft/Tv/Simpsons: not found
move.sh: 9: pattern[1]=family.guy: not found
move.sh: 9: dest[1]=/home/beltoft/Tv/Family guy: not found
move.sh: 12: Syntax error: Bad for loop variable


ls of my ~/
move.sh <- this is your script
ready <- this is my incoming folder
Flim <- this is my movie folder
Tv <- my Tv folder

the script:

```


#!/bin/bash

IFS=$'\n'  # newline as separator to tackle spaces in names
           # and generally make life easier

delay=10
incoming="$HOME/ready"
def_dest="$HOME/Film"

# patterns and destinations, modify to suit your needs
pattern[0]='simpsons';    dest[0]="$HOME/Tv/"
pattern[1]='family.*guy'; dest[1]="$HOME/Tv/"

# make sure target directories exist (try to create them)
for (( i=0; i<${#dest[@]}; i++ ))
do
    mkdir -p "${dest[i]}"
done
mkdir -p "$def_dest"

# main loop
while ((1))
do
    echo Checking folder...
    # generate list of folders
    dirs=$(find "$incoming" -mindepth 1 -maxdepth 1 -type d)

    if [ ! -z "$dirs" ]
    then
        echo 'Folders found!'
        echo "$dirs"
        echo ------------------------------
    fi

    # wait
    sleep $delay

    for dir in $dirs
    do
        count=0
        for (( i=0; i<${#pattern[@]}; i++ ))

        do
            count=$( echo "${dir}" | grep -ice "${pattern[i]}" )

            if [ "$count" != "0" ]
            then
                # if dir matches, move to destination
                echo "$dir" matches "${pattern[i]}" pattern
                mv -v "$dir" -t "${dest[i]}"
                break
            fi
        done

        if [ "$count" = "0" ]
        then
            mv -v "$dir" -t "$def_dest" # not matching -> move to default dest dir
        fi
    done
done


```

---

### Post by Vaphell on 2011-01-28
what the hell?! your script doesn't feel like treating parameters as strings and i am not that much into shell scripting to know why such a thing could happen

different version of bash? bash being a symlink to some other shell?
what do
```
ls -l /bin/bash
bash --version
``` say?

---

### Post by mbeltoft on 2011-01-28
It's a almost clean install of Ubuntu server 10.10
I've installed a few programs but I don't know if any of them could cause something out of the normal....

ls -l /bin/bash gives me:
-rwxr-xr-x 1 root root 917888 2010-08-10 22:47 /bin/bash

and bash --version says:

GNU bash, version 4.1.5(1)-release (x86_64-pc-linux-gnu)
Copyright (C) 2009 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>

This is free software; you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

---

### Post by Vaphell on 2011-01-28
and what happens when you construct arrays this way?
```
pattern=( 'simpsons' 'family.*guy' )
dest=( "tv/simpsons" "tv/family guy" )
```
?

---

### Post by mbeltoft on 2011-01-28
```


# patterns and destinations, modify to suit your needs
#pattern[0]='simpsons';    dest[0]="$HOME/Tv/"
#pattern[1]='family.*guy'; dest[1]="$HOME/Tv/"

pattern=( 'simpsons' 'family.*guy' )
dest=( "tv/simpsons" "tv/family guy" )

```

gives me 

move.sh: 14: Syntax error: "(" unexpected

---

### Post by mbeltoft on 2011-01-28
```


# patterns and destinations, modify to suit your needs
#pattern[0]='simpsons';    dest[0]="$HOME/Tv/"
#pattern[1]='family.*guy'; dest[1]="$HOME/Tv/"

pattern=( 'simpsons' 'family.*guy' )
dest=( "tv/simpsons" "tv/family guy" )

```

gives me 

move.sh: 14: Syntax error: "(" unexpected

and without the () around the patteren and dest it gives me the same as before:

move.sh: 14: simpsons: not found
move.sh: 15: tv/simpsons: not found
move.sh: 18: Syntax error: Bad for loop variable

---

### Post by Vaphell on 2011-01-28
i don't get it, your bash is exactly like mine and yet it has a problem with arrays?

EDIT: let me guess, you run the script by
```
sh move.sh
```?
i just checked, when you force the script to be opened with sh (dash) it returns the errors exactly like yours. Bash is fatter but more feature rich than dash and apparently arrays are one of the differences.

---

### Post by mbeltoft on 2011-01-29
yeah I run it by

```
 sh move.sh 
```

could I run it in some other way to make it work?

---

### Post by Vaphell on 2011-01-29
yes, by running it with a proper shell (bash)
```
bash move.sh
```
or by letting the first line of the script (shebang) decide, that's what it's for
```
#!/bin/bash
```
to do so, make the script executable and run it without calling shell explicitly
```
chmod +x move.sh
./move.sh
```

---

### Post by mbeltoft on 2011-01-29
well #!/bin/bash is in the top of the script so that should work however when I try to run it with ./move.sh and with bash move.sh it works :D

strange - I can how see that it runs in a loop which might not be a good idea as files could be open somehow not ready to be moved when the script runs. 
I was thinking about using incron ( [http://inotify.aiken.cz/?section=incron&page=about&lang=en](http://inotify.aiken.cz/?section=incron&page=about&lang=en) ) to call the script whenever a folder was created but not changed in X seconds

Anyway... Thank you so much for your help :D

Edit - I just saw that all the folders was moved to the default destination ~/Film even if the folder name contained simpsons

---

### Post by Vaphell on 2011-01-29
that's what delay was for
moving elements around happens after $delay seconds - list of folders is generated, **wait**, stuff is moved around. This prevents something jumping in the last second and being moved. Of course more specialized software is probably more foolproof. If you decide to use that tool, remove the while loop.

> Edit - I just saw that all the folders was moved to the default destination ~/Film even if the folder name contained simpsons

damn it. I test my script on such set of folders
```
some-junk
FAMILY.GUY
family _ guy
-simpsons
simpsons wtf onoz
THE SIMPSONS
[xyz]simpsons 2

```
and it doesn't fail. What is the exact name of the simpsons folder so i can investigate that?

---

### Post by mbeltoft on 2011-01-29
both simpsons and family guy fails. 
the folders is named: 
Family.Guy.S08E01.Road.to.the.Multiverse.PDTV.XviD-FQM
The.Simpsons.S21E06.Pranks.and.Greens.HDTV.XviD-FQM
The.Simpsons.S22E10.HDTV.XviD-LOL

---

### Post by Vaphell on 2011-01-29
-_-

so you don't get that '.... matches ... pattern' line?
what does your definition of patterns and destinations currently look like?
for improved readability add empty **echo** command after each mv so there is an empty line after each move operation

---

### Post by mbeltoft on 2011-01-29
I made a typo in the pattern so thats why it didn't work at first but now everything is just perfect :D

Thank you very much for your help. :D

---

### Post by Vaphell on 2011-01-29
glad it worked finally :-)
in case you want to add some other pattern it's obvious - pattern[2] dest[2] etc
if you want some fancy pattern, read about syntax of regular expressions

---

### Post by mbeltoft on 2011-01-29
> **Vaphell said:**
> glad it worked finally :-)
in case you want to add some other pattern it's obvious - pattern[2] dest[2] etc
if you want some fancy pattern, read about syntax of regular expressions

Got it... and if you ever come by Copenhagen, Denmark I owe you a beer .. or 3 :D

---


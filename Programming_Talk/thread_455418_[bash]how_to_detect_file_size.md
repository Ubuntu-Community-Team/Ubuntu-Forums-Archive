---
title: "[bash]how to detect file size?"
date: 2007-05-26
forum: Programming Talk
---

### Post by kilyx on 2007-05-26
hi , i need to do a little linux script

i need to create a file where all the results of a search are stored but i need to stop saving this file if it increse too much its size (like 1mb for exemple)

it's good to create an if cicle? but what's the correct option to discover the file size?

in my excercise trace, it's told to use the "-o option".does anyone know it?

sorry for the english and thanks for the helps

---

### Post by Metacarpal on 2007-05-26
A quick way to get a file's size (in bytes):
```
stat -c %s *filename*
```
It's generally a good idea to include the full path to the file, rather than just the filename.

As for how to use that, it depends on what your script does.  One way to go would be:
```
RESULTS_SIZE=`stat -c %s *filename*`
if [ "$RESULTS_SIZE" -gt 32768 ]
then
[INDENT]echo "Results file has exceeded 32MB in size."
exit 1;[/INDENT]
fi
```

(That example is for a max file size of 32MB.)

How you'd use it really depends on what you want your script to do.  You could even use the if statement to move your existing (and oversized) results file to another file name, then create a new, empty results file to continue the script.

If you need more tips, let me know.

---

### Post by kilyx on 2007-05-26
thanks very much for the tip

how can I stop saving a file if it exceed the size?

my script stores in a file named list.log the results of all the searches but i need to stop saving at the next start of the script


thanks

---

### Post by Metacarpal on 2007-05-27
```
RESULTS_SIZE=`stat -c %s filename`
while [ "$RESULTS_SIZE" -lt 32768 ]
do
[INDENT]place your search script here
RESULTS_SIZE=`stat -c %s filename`[/INDENT]
done
```

---

### Post by kilyx on 2007-05-27
thanks

do you know how I can save a file named "<dir>.list.log" where <dir> is the name of the directory where I searched?

thanks,bye

---

### Post by kilyx on 2007-05-27
and how can I use "set -o" with the stat command so I can activate the stats option typing ./script.sh -o or do not activate it only typing ./script.sh?

thanks

here is my script 
```
#!/bin/bash 
echo "specifica una directory"
read dir  
echo "fornisci un parametro di ricerca"
read x
nomefile=$(echo "$dir" | sed s/'\/'/'-'/g | sed s/'^-'//)
trovati=$(find $dir -name "$x")
if [ "$trovati" != "" ]
then
     echo "Ho trovato questi file:" > $nomefile.list.log
     echo "$trovati" >> $nomefile.list.log
else
     touch $nomefile.list.log
fi

touch list.log
RESULTS_SIZE=`stat -c %s "list.log"`
if [ -s "$nomefile.list.log" ] 
then   
    if [ "$RESULTS_SIZE" -gt 1000000 ]
    then
    echo "il file supera le dimensioni consentite e non sarà salvato"
    exit 1;
    else
    echo "sto cercando in $dir e ho trovato" >> list.log 
    fi
else 
echo "sto cercando in $dir e non ho trovato" >> list.log 
fi    
sort -o  list.log list.log   
exit


```


I need to set an -o option:
when the -o option is active, the file list.log stop saving exceeded 1mb
when the option is not active the file list.log go on saving til I want to

---

### Post by kilyx on 2007-05-28
up^^

---

### Post by Metacarpal on 2007-05-31
Sorry for the delayed response - was either out of the house or sick all week.

At work right now, have to keep it short, will post on this from home later.

Out of curiosity, is this for a class or something?  The -o switch seems like a textbook exercise.

Don't get me wrong, I'll still help ya - just want to know what kind of help to provide.  :)

---


---
title: "Another question to understand bash scripting better"
date: 2011-04-30
forum: Programming Talk
---

### Post by CaptainMark on 2011-04-30
im really getting into bash scripting, its so useful and theres so much to do, 
im a little stuck on one bit thats confusing me,

i have the variables "source" and "destination" which are directory names and "file" that is a file name, that have all been input by the user, in order to read the directories again the next time i run my script i have been trying to store them to a text file, ive played around storing and retrieving variables from a text file and id normally use
```
$variable > $file
```to store and ```
 read variable < $file
``` to retrieve it again, the problem with using this method ive found is that the behaviour of bash seems to be to attempt to copy the directory itself to $file, resulting in a error that '/home/mark is a directory' what i need is to store the directory name to the text file,

so, how to get bash to recognise $source as the string "/home/mark" and save it as text inside the file "./test_config"

I can post more specific details about my directory names and the current script if you need to see the variables so far.

Thanks for any help,
much appreciated 
Mark

---

### Post by Vaphell on 2011-04-30
details would be nice
```
#!/bin/bash

var='wtf'
d="$HOME/test"
f="var.txt"

echo var=$var
echo $var > "$d"/"$f"

var=''
echo var=$var

read var < "$d"/"$f"
echo var=$var

```
returns
```
var=wtf
var=
var=wtf
```
as expected

---

### Post by hakermania on 2011-04-30
To store to file:
```
echo $variable > /path/to/destination/file
```To read from file
```
variable=$(cat /path/to/source/file)
```

---

### Post by CaptainMark on 2011-04-30
this worked perfectly, thank you, i will try to look more into what echo does soon as well, ive only used it for printing to the terminal so far, i didnt know it did anything else, but for now this will do fine
Thanks 
Mark

ps, nice avatar btw ;)

---

### Post by CaptainMark on 2011-04-30
however :)
if i use ```
echo $source $destination > $targets
```this works if $targets is a path in relation to the current directory but if i use an absolute path it wont work, why is that?? i need my script to be able to be run from any folder so this is quite important,

for example i have ```
source="/home/mark"
destination="/media/passport/mark"
targets="????"

echo $source $destination > $targets
```lets say im running this from my desktop directory if
targets="./targets"

i get a plain text file placed on my desktop called "targets" and it contains the text "/home/mark /media/passport/mark"
perfect

but if 
targets="./Desktop/targets"    or    targets="/home/mark/Desktop/targets"
then i get an error telling me that the file or directory does not exist??

I could use 'touch' to create the file first but id like to understand why first, also this part of the script is only used if $targets does not exist,

edit: it gets even more confusing now, i tried adding <touch $targets> in as well before the last line and i get the message "cannot touch '~/Desktop/targets' : No such file or directory

---

### Post by hakermania on 2011-04-30
I think you are quite confused.
Make  a script that conatains tha following:
```
echo "I exist!" > ~/Desktop/exist
```Note that the path should be in quotes (") if it has spaces in it, otherwise you'll get a doesn't exist error.

You;re actual fault is that you use the '~' This one can be used normally, but i'm not sure why, but it doesn't work if you declare a normal variable as a string.
For example:
```
targets="~/home/Desktop/exist"
touch $targets
``` won't work, but
```
targets=~/home/Desktop/exist
touch $targets
``` or
```
targets=~/home/Desktop/exist
touch "$targets"
``` will !
Quite confusing, isn't it :P?

---

### Post by CaptainMark on 2011-04-30
yes i agree, very confused indeed, 

i understand what > does (basics) but confused why the absolute path doesnt work, (normally absolute paths work where relative paths dont, not the other way around)

i seem to have it now, its crucial for me to use the ~/ suffix because this script needs to run on any users setup so i couldnt put my own home path in there, hence the need to store the path in a separate file,

it works fine if i just use 

target=~/.config/homesync/targets

(which is the actual file for my script)

im just in the habit of quoting everything because usually theres no reason not to, in this case however, it works perfectly unquoted,

Thanks for your help

---

### Post by Vaphell on 2011-04-30
use $HOME variable in "" (to protect against spaces) instead of ~
~ is risky but i don't remember why

---


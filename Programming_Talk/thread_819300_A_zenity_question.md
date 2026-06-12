---
title: "A zenity question"
date: 2008-06-05
forum: Programming Talk
---

### Post by Green_Star on 2008-06-05
Hi I am trying to make a shell script combining with zenity for some GUI. My target is to merge couple of bigger files into one file, it takes around 3-5mins. So I want to display a progress bar when it is doing this merging work. 

I have following bash command.

```
cat file1 file2 file3 > file4
```

I used following two kinds of syntax to show some gui but no luck.

```
cat file1 file2 file3 >(zenity --progress --pulsate) > file4
```

above one is not at all working, i mean there is progress bar display but no merging process is going on. so i tried following

```
cat file1 file2 file3 > file4 | zenity --progress --pulsate
```

when i executed above one the progress bar just flashes and closed immediately but merging process going fine. 

I want to keep progress bar until merging process completes, any help?

---

### Post by chewearn on 2008-06-05
Unfortunately, I don't know of any easy way to do this.  The cat command does not output a status to the stdout.  For "zenity --progress" to work, you need to feed it a number 0 to 100, which will correspond to the progress bar position.

E.g.
```

for i in $(seq 0 20 100); do echo $i; sleep 1; 2>&1; done | zenity --progress

```If you run the command above, you get a zenity progress bar that moves forward every second.

So, the trick is to find a way to get the progress number from cat process.  This entails calculating the total filesize after the cat, break up the cat into multiple equal chunks, calculate the percentage progress for each chunk, and finally feed the percentage into zenity.

Someone made a complicated script to achieve this for the cp command here:
[http://thesweeheng.wordpress.com/2008/01/03/a-progress-bar-for-bash-scripts/](http://thesweeheng.wordpress.com/2008/01/03/a-progress-bar-for-bash-scripts/)

Not sure if you would even want to rewrite the script for your purpose.

EDIT:
A less cumbersome, but less accurate way is to take each file to be concatenated as one step in the progress bar.

.

---

### Post by geirha on 2008-06-05
I've spent some time with this. For some reason zenity refused to kill the cat process so I eventually had to use a trap to do it. Anyway:

[PHP]
#!/bin/bash

srcfiles=( "file1" "file2" "file3" )
# sum up the size of all the source files
srcsize=`stat -c %s "${srcfiles[@]}" |  awk '{s += $1}END{print s}'`

destfile="file4"
destsize=0

# Run the merging in the background and save its pid.
cat "${srcfiles[@]}" > "$destfile" & 
catpid=$!

# In case we aborted zenity, kill cat if it is still running
trap '[ -d /proc/$catpid ] && grep -q ^cat /proc/$catpid/cmdline && kill $catpid' SIGHUP

# Poll the detination file every second, printing the percentage to zenity.
while [[ $destsize -lt $srcsize ]]; do
    echo $(( 100 * destsize / srcsize ))
    sleep 1
    destsize=$(stat -c %s "$destfile")
done | zenity --progress --auto-close --auto-kill
[/PHP]

---

### Post by Green_Star on 2008-06-05
Thanks Guys,

Actually I do not need progress bar which moves from left to right, i am also fine with if it continuesly moves from left to right and right to left. Or I am fine with a dialog box saying 'merging in process' and it should auto close when the merging is done. 

I tried to follow this [example]("http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/"). but no luck for my cat command.

geirha, I will try your method and see how it goes.

---

### Post by Green_Star on 2008-06-06
is there any way to delete partially merged file when we aborted zenity? just like how we are killing cat.

---

### Post by geirha on 2008-06-06
Yes, and it's probably a good idea to do so. Just add it to the trap: ```
trap '[ -d /proc/$catpid ] && grep -q ^cat /proc/$catpid/cmdline && kill $catpid ; rm "$destfile" ' SIGHUP
```

btw you can do ```
srcfiles=( *.txt /some/dir/*.list )
``` etc. to get other sourcefiles in there. (Don't use `ls something` or $(ls something) )

---

### Post by Green_Star on 2008-06-06
Thanks geirha,

I will try as soon as I go home. 

Acutally what I am trying to do is I get files like following

file1.report.100
file1.report.101
file1.report.102
file2.report.155
file2.report.156
file2.report.157 .....etc

file names may be different depending on what they are sending but it is always three digits at the end. So I wrote a script to merge all file1.report* into one file and the destination file name should be file1.report. same way for file2.report.* should be merged to file2.report. To delete last three digits I followed thes [thread]("http://ubuntuforums.org/showthread.php?t=817276").

i pass one file to script as parameter and script will delete last theree digits with 'dot' and saves that name into a variable called destfilename.

> destfilename=${1%.???}

 next it will do 'ls $destfilename*` and saves the list into sourcefilenames.

> sourcefilesnames= ( `ls $destfilename*` )

later I followed your steps from post #3. then it delets all source files. 

so I may have difficulty using **srcfiles=( *.txt /some/dir/*.list )**

by the way I learned so much about shell scripting in these thereads.

---

### Post by geirha on 2008-06-06
> **Green_Star said:**
> 
i pass one file to script as parameter and script will delete last theree digits with 'dot' and saves that name into a variable called destfilename.



 next it will do 'ls $destfilename*` and saves the list into sourcefilenames.



later I followed your steps from post #3. then it delets all source files. 

so I may have difficulty using **srcfiles=( *.txt /some/dir/*.list )**

by the way I learned so much about shell scripting in these thereads.

Not at all. If you can do scrfiles=( `ls $destfilesname*` ) you can also do srcfiles=( $destfilesname* ). It's important to know that the patterns are interpreted by bash, not ls (ls treats * as any other character). 

E.g. if you are in a directory with the files: "file1", "file2" and "some other file", and you do ```
ls file*
``` then bash first replaces that pattern with file1 file2, so you are actually running ```
ls file1 file2
``` Try with ```
echo file*
``` for example. It will list the same as ls for just this reason.

---

### Post by Green_Star on 2008-06-06
I didnt know that I can do **srcfiles=( $destfilesname* )**, I will try this in the evening and see how it goes.

---

### Post by Green_Star on 2008-06-06
**srcfiles=( $destfilesname* )** this this working, great. thanks again.

---


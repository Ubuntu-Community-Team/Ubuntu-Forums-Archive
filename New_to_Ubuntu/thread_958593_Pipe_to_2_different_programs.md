---
title: "Pipe to 2 different programs?"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by john.hall on 2008-10-25
Is it possible to do a pipe to two different programs?  Something like 

```

arecord -D hw:1,1 -f cd

```

Being piped to both

```

lame -h - file.mp3

```

and

```

aplay -D hw:0 -f cd

```

I'm using bash, by the way.

---

### Post by Catalyst2Death on 2008-10-25
I'm not sure what your trying to do.  Bash piping usually refers to changing where stdin, stdout, and stderr are read from/ written to.

stdin -> standard input -> keyboard
stdout -> standard output -> terminal window
stderr -> standard error -> terminal window

simple bash redirection, runs a program and pipes one output to another, for instance:

ls -la | grep ^d | awk '{print $8}'

lists all directories in the folder by taking the output of ls -la and using it as input to grep (via | ) and then takes the output of grep and pipes it into awk (again via | ).

You can also do stuff like:

grep myString < MyFile > MyResults.txt

this takes grep, and runs the contents of MyFile as if you typed it into the keyboard, searches for my string, and writes the results of grep to file named MyResults.txt

So, If you want to redirect the same output to two different programs, you'll likely need a bash script, and then change the stdout pipe to two custom ones, and then use the two custom pipes as input to the separate programs:

```
# Save keyboard input and re-route stdin to our file
exec 6<&0
exec < $path_to_txt
numLines=`wc -l < $path_to_txt`
for i in `seq 1 "$numLines"`
do
    read filename
    files["$i"]="$filename"
done

#Restore Keyboard input
exec 0<&6 6<&-

```

hacked from: 
[http://ubuntuforums.org/showthread.php?t=546495&highlight=bash+script+redirect+file+input](http://ubuntuforums.org/showthread.php?t=546495&highlight=bash+script+redirect+file+input)

---

### Post by sdennie on 2008-10-25
It sounds like you want to use the tee command.  I don't know exactly what you are trying to accomplish so I can't give exact syntax but, I would google for "unix tee" and see if you can find an example of how to use it in the manner you want.

---

### Post by dracayr on 2008-10-25
The only method I can think of is quite ugly (there probably is an elegant way to solve this), and I don't know if it works, but you could try:

arecord -D hw:1,1 -f cd|tee /dev/stderr|aplay -D hw:0 -f cd 

simultaneously execute (in a different Tab perhaps):

lame -h /dev/stderr file.mp3

note that I replaced the - in the lame command by /dev/stderr. 

dracayr

---

### Post by bodhi.zazen on 2008-10-25
tee FTW !!!!

[http://linux.byexamples.com/archives/144/redirect-output-to-multiple-processes/](http://linux.byexamples.com/archives/144/redirect-output-to-multiple-processes/)

---

### Post by wd5gnr on 2008-10-25
If I recall, tee is going to force one side of the stream to a file. Which would be ok with a named pipe. For example:

#!/bin/bash

# Take output from program A and run it through program B and C 
# at the same time


# create Named pipe
mknod /tmp/np$$.pipe p
# just for pretty output
echo Forward:
# Set up "2nd program" to read from pipe and write somewhere else
# be sure to not block (use & at end of line)
sort -r </tmp/np$$.pipe >/tmp/t.out &  
# Now get output (ls here), use tee, and sort
# This will print the files forward sorted
ls / | tee /tmp/np$$.pipe | sort 
# Now write out the reverse sort just so we can see it
echo Reverse:
cat /tmp/t.out

#remove pipe (ought to catch all ways with a trap
rm -f /tmp/np$$.pipe

---

### Post by john.hall on 2008-10-25
> **bodhi.zazen said:**
> tee FTW !!!!

[http://linux.byexamples.com/archives/144/redirect-output-to-multiple-processes/](http://linux.byexamples.com/archives/144/redirect-output-to-multiple-processes/)

Wonderful!  This is exactly what I was looking for.  Thanks!

---

### Post by wd5gnr on 2008-10-25
Note the mechanisms used in the linux by example link are bash-specific as far as I know. Of course, as long as you are using bash, no problem.

---

### Post by spupy on 2008-10-25
Check the command **mkfifo**. It creates files that are pipes. The source program outputs to that pipe file, and on the other end someone else (i guess two programs simultaneously) can read from the pipe.

---


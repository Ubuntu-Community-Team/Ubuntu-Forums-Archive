---
title: "How to use FOR loops in bash"
date: 2009-05-31
forum: Outdated Tutorials &amp; Tips
---

### Post by lavinog on 2009-05-31
The linux command line is very handy for performing tasks very quickly.  For loops can be used to accomplish repetitive tasks that would take forever in a GUI enviroment.
Although the for loop is normally used in programing, it is still handy for single line commands.

The for command works like this:
```

for *VAR* in *LIST*
do
  COMMANDS
done

```

example:
```

for name in joe betty sue
do
echo $name
done

```
This can be used on one line like so:
```

for name in joe betty sue ; do echo $name ; done

```
[i]
Note: There can't be a semicolon between the do and the first command. After the first command you can use a semicolon to separate further commands.[/i]

**Working with variables:**
Looking at the above code I used 'name' as the variable.
Variables in bash can be assigned with an equal sign:
```
var=data
```
The for command does this automatically, so an equal sign is not needed.
Variables need to have a dollar sign to be referenced.
```

name=hank
echo name         #prints name
echo $name        #prints hank
echo ${name}      #prints hank
echo ${name}y     #prints hanky
echo $namey       #prints a blank because namey wasn't assigned anything
echo ${name%k}dy  #prints handy (The %string removes the trailing string from the variable)
echo t${name#h}   # prints tank (The #string removes the leading string from the variable)

```
Those are just a few things about bash variables. Notice the usefulness of the curly braces. These will become very handy in future examples.

Ok, thats great if you want to make a list of names, but how can this be useful for anything else?
Lets say you have a bunch of files in a folder that you want to change their extension from .txt to .bak
a for loop can be used for this task:
```

for file in *.txt ; do mv -v $file ${file%.txt}.bak ; done

```

```

for i in {1..3} ; do touch ${RANDOM}.txt ; done    #Makes a couple of random files

ls -1
12548.txt
1539.txt
16840.txt

for file in *.txt ; do mv -v $file ${file%.txt}.bak ; done

ls -1
12548.bak
1539.bak
16840.bak

```
This works great as long as the file names don't contain spaces.

Note: $RANDOM is a special variable that creates a random number between 0 and 65536 (I think that is the correct range)

```

for i in {1..3};do touch temp\ ${RANDOM}.txt ;done

for file in *.txt ; do mv -v $file ${file%.txt}.bak ; done
mv: target `13187.bak' is not a directory
mv: target `19202.bak' is not a directory
mv: target `31571.bak' is not a directory

```
This is because the command that is being used is:
```
mv -v temp 13187.txt temp 13187.bak
```
which is trying to move the files temp and 13187.txt to a nonexistant folder 13187.bak.
We were lucky in this case.
To fix this we need to enclose our variables in double quotes:
```
for file in *.txt ; do mv -v “$file” “${file%.txt}.bak” ; done

```


**Making Lists:**
In the above example I used a {1..3} to make the list: 1 2 3
I also didn't use the variable. This was only used to make the loop repeat 3 times.
The list could have been *bobby joe sue* and it still would have iterated 3 times.
By using * for file in *.txt*, the shell will automatically replace the *.txt with a list of filenames matching that pattern.

Numerical lists can be created by using {START .. END} or using the seq command
```

echo {5..20}
5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20

echo {5..-10}
5 4 3 2 1 0 -1 -2 -3 -4 -5 -6 -7 -8 -9 -10

# now using seq
seq 5 10
5
6
7
8
9
10

seq 5 -5
#No output

seq 5 -2 -5   #the middle number is the increment
5
3
1
-1
-3
-5

seq -w 0 25 100
000
025
050
075
100

```

The seq command gives you the ability to skip digits, and also with the -w switch can add leading zeros if needed.
To use the seq command to make a list we need to enclose the command in $(  ).
```

echo $( seq 1 3 )
1 2 3

echo `seq 1 3`   # This is the old way and can cause problems, but it is still commonly used.
1 2 3

```
The $( ) are very handy for converting a command into a string such as the date:
```

echo $(date '+%m-%d-%y')
05-31-09

```

Now lets try and find a use for all of this so far.
My digital camera creates files with a IMGP####.JPG format
I want to append a date string to all of the pictures in the range 4580 to 4679.
```

for num in {4580..4679} ; do echo mv IMGP${num}.JPG IMGP${num}_$(date '+%m-%d-%y').JPG ; done
mv IMGP4580.JPG IMGP4580_05-31-09.JPG
mv IMGP4581.JPG IMGP4581_05-31-09.JPG
mv IMGP4582.JPG IMGP4582_05-31-09.JPG
…
mv IMGP4677.JPG IMGP4677_05-31-09.JPG
mv IMGP4678.JPG IMGP4678_05-31-09.JPG
mv IMGP4679.JPG IMGP4679_05-31-09.JPG

```
Notice that I prepended echo in front of mv. This is a good way to test your command beforehand so that you can catch mistakes that you might regret.  After the output looks good I just press the up arrow on the keyboard and remove the echo from the line and watch my photos get their datestamp.

If your camera started at IMGP0001, you may have a problem using {1..300} because it will try and find file IMGP1.JPG instead.
This is why I mentioned using seq -w.  A little bit of forethought is needed though. Using $(seq -w 1 300) will look for IMGP001.JPG through IMGP300.JPG...so you will need to leave one leading zero:
```

for num in $(seq -w 1 300) ; do echo mv IMGP0${num}.JPG IMGP0${num}_$(date '+%m-%d-%y').JPG ; done

```

**Using a file for a list:**

I have a file named list.txt. The contents of the file are:
frank
betty sue
optimus prime
A whole bunch of words

See what happens when I use this list for a for loop:
```

for x in $(cat list.txt) ;do echo “$x”;done
frank
betty
sue
optimus
prime
A
whole
bunch
of
words

```
This time the quotes didn't fix the problem.
What we need to do is change the delimiter so that only newlines separate the list.  The IFS (Internal Field Separator) variable is what determines what separates the list.
```

IFS='
'    #only a newline between the quotes

for x in $(cat list.txt) ; do echo “$x” ; done
frank
betty sue
optimus prime
A whole bunch of words

unset IFS         # unset the change to IFS back to normal

```

alternatively, we could put the unset line at the end of the for loop, so we don't forget to unset it later:
```

for x in $(cat list.txt) ;do echo “$x” ; done ; unset IFS

```
unsetting IFS isn't needed if you plan on closing out the terminal afterwards anyway.

**Some Practical Applications:**

*Convert images using imagemagick:*
Many programs can't work with multiple files even if it would be handy.  Imagemagick's convert is very cool tool to manipulate images. The most common feature I can see is its ability to convert formats.
```

# This converts all png files to jpg (echo added to show progress)
for pic in *.png ; do echo “$pic” ; convert “$pic” “${pic%.png}.jpg” ; done

```

*Transcode videos for use in a media player:*
Very similar as above, but using mencoder and relocating the files to a different folder.
```

mkdir transcoded
for video in *.avi ; do mencoder -o "transcoded/$video" -vf scale=320:240 -oac mp3lame -ovc xvid -xvidencopts bitrate=800 “$video”; done

```

*Transfer files to media player using mtp-sendfile*
For a while I had to use mtp-sendfile to upload files to my zen. gnomad kept crashing at that time.
```

for file in *.mp3 ; do mtp-sendfile "$file" "$file" ; done

```

*Track cpu load averages for 1 hour:*
This can be done with a while loop also, but this gives the ability to exit after a certain amount of time
You may not care about load averages, but you can replace the command with any type of monitor like watching cpu temps or number of users logged in.
```

for x in {1..60} ; do cut -d ' ' -f 1-3 /proc/loadavg ; sleep 60 ; done

```

*Make a siren on a remote machine:*
Some computers still have a pc speaker, if so you can use the beep command to play noises at different frequencies. You can use the for command to make a siren. (ssh to a remote machine and have fun watching your mark try and figure out what is going on)
```

for n in {1..10}; do for f in {100..1500} ; do beep -f $f -l 10; done ; for f in {100..1500} ; do beep -f $f -l 10 ; done ; done

```
A for loop inside of a for loop is called a nested for loop.

---


---
title: "[SOLVED] Batch compression operations"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by GepettoBR on 2008-06-27
EDIT: Hospadar's script (post #2) worked great, but not 100% like I wanted. I made a slightly altered version that you can find in pot #4, but all credit still goes to him)

This should be a breeze for people who know bash, but unfortunately I don't.

I have a directory full of highly compressible files, all with the same extension. I want to take all these same-extension files and compress each to its own archive on a separate directory. This is because I want to be able to access any one of them without having to extract all the others in the process. The archive names would be the names of each file (with or without the extension, doesn't matter). How do I do it?

Thanks in advance,

Paulo

---

### Post by Hospadar on 2008-06-27
I think the easiest way would be with a bash script and some command-line compression.

It's relatively easy to loop through all the files in a directory and run a command on each one.
You'll have to do some googling on bash scripting if you arn't familiar with it.  Basically you just enter the commands you want to run into a text file, line by line, and then execute that text file.  There are some special command that allow you to loop and such.  To compress each file in a directory, and move each compressed file to a different subdirectory might be something like this (i'm sure some syntax here will be wrong, so use the googletron to get it right```

#this is the loop that will go through all the files, the $1 is a special bash variable. It is the first #argument passed to the script on the command line.  In this case it will be the directory containing #the files you want to compress

for files in `ls $1`
do

#This is the beginning of the loop.  First, we're going to use the "cut" command to seperate the meat 
#of the filename from the extension (assuming your files have extensions) We'll assign the result to 
#another variable

subdir=`echo $files | cut -f1 -d.`

#let's print out the name we generated so you can see what's going on
echo $subdir

#now make the new directory

mkdir $subdir

#now let's compress the file.  This command will vary based on what you use to compress (rar, tar, 
#gzip, zip, etc.  You'll have to look up the synax for the particular program you want to use.  But let's 
#say you're using a program where the only two arguments are the input file, and the output #filename

<command> $files $subdir"/"$files"<appropriate extension>

#end the loop here
done
```Keep in mind, when I say that I think bash scripting is the "easiest" way to do this, that doesn't imply it to be super easy if you've never scripted in bash or programmed before.  I think with some dilligence and intelligent googling you'd be able to figure it out though.  If you don't have a ton of files though, or if your files need to be grouped in irregular ways it may end up being easier to just do this stuff by hand.  It would also be helpful to be familiar with the basic bash text processing commands, grep, cut, diff, maybe sed if you're feeling adventerous.

Welcome to the wonderful world of simple task automation!

PS if you don't know, you'd run this script by doing something like ```
./<name of the script file> <name of the folder with stuff to be compressed>
```

---

### Post by GepettoBR on 2008-06-27
EDIT: Ignore this post, everything works. See post below it for details.

Hmm, I'm a little confused here. I copied that into gedit and got a bunch of different colors. From what I make of it, text in grey appears to be variables, so let's see if I got this straight:

$1 --> I replace this with the name of the directory, in full form, in this case /home/paulo/project-files

$subdir -->name of the subdirectory I want to create inside the working directory

so what about "files" and "$files"? Are these already wildcards, or do I change them to something?

Sorry for being a bash noob, I do intend to learn this, but don't really have the time now - have to study for semester finals

---

### Post by GepettoBR on 2008-06-27
Hey, it worked! Thanks a lot! In case anyone finds this thread who is trying to do the same thing as me, here's a summary of what happened:

Other than adding the compression program and proper arguments where Hospadar left blank, I made one important change: the $subdir thing made the script create one separate subdirectory for each archive. For me, that was a bit messy. I wanted all the archives to be in the same folder, so I changed the mkdir line to "mkdir compressed" and put the line before the first line in Hospadar's version, to keep it outside the loop (otherwise it'd try to create the directory again anyways and output a "File exists" error - it still works, but it wastes precious CPU cycles!). Then, I made the mistake of executing the script from the same directory as the files, so the subdirectory itself (and the script) was also compressed along with every file that was already in it (luckily, there were only four in alphabetical order). This is a waste of time and space, so don't do that!

First I tried using xarchive to compress the files, but it kept prompting me to confirm adding the file before making each archive. Since there's no "--quiet" option, I had to try another solution. I used tar, which just made an archive with 1:1 compression ratio. Wrong again, it seems. adding a gzip line after tar was what finally made it work. I ended up with a nice group of compressed .tar.gz files inside my "compressed" subdirectory.

For any people who are lazy like me, here's the final version of the bash script I used. Since I was very excited that this thing actually worked, I added a few comments of my own about the changes and a few friendly echo lines since the script can take a while if you have lots of files.

```
#!/bin/bash

#This line will create a subdirectory to store the compressed files. Don't mind all the "echo" lines, they're just here to give the script a friendlier feeling. Remove them if you like.

mkdir compressed
echo "Let's begin, shall we?"
echo

#this is the loop that will go through all the files, the $1 is a special bash variable. It is the first argument passed to the script on the command line.  In this case it will be the directory containing the files you want to compress

for files in `ls $1`
do

#This is the beginning of the loop.  We'll use tar to create an archive for each file in our working folder. The -c argument tells tar to create an empty archive and -f tells it to use that archive. So tar will make an archive for each file and then append that file to the archive.

tar -cf compressed/"$files".tar $1/$files

#now let's compress the files.  We'll use gzip to compress the tar files. -9 means I want gzip to compress the files as much as possible. If this is too slow, try lowering the value. -1 is maximum speed.

gzip -9 compressed/"$files".tar

#Wondering if it's working? This can take a while, so let's output a confirmation message for each file that completes.

echo "$files succesfully compressed!"

#end the loop here
done

#Now we're done!
echo
echo "That was fun, wasn't it?"
echo "Goodbye!"
```

Save the script to a text file, and remember to chmod +x the file or it won't be executable! Just type this in a terminal: ```
sudo chmod +x ./<name of the script file>
```
Then, just like Hospadar said, execute the file with ```
./<name of the script file> <name of the folder with stuff to be compressed>
```

The compressed files will be saved to a subdirectory of your current working folder (the default is the home folder) named "compressed" (you can change that by opening the script in your favorite text editor).

---


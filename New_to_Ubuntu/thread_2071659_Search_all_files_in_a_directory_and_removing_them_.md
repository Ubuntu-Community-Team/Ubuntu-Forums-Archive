---
title: "Search all files in a directory and removing them if they do not contain a string"
date: 2012-10-16
forum: New to Ubuntu
---

### Post by Dabo Ross on 2012-10-16
I have been running a server with ubuntu server, and am not that sure how I would do this.
Let me explain what I want to do.
I have been running this server for a while, and I have written a lot of shell scripts for it, but I am not that good at them. If it is relevant I am using ubuntu server 12.04.

I would like to have a .sh file that goes through all files in the directory /home/newlanders/files/ (Doesn't matter if it includes sub folders) and deletes every file without the text "ipAddress:". That is if a file does NOT contain that text, delete it.
 Is that possible?
I know it will probably entail a for loop and grep command, this language is not my strong suite.\

Ok, I have been looking around and I found that I could use 
$ grep "ipaddress" /home/newlanders/files/*.yml -i -L
To find the files, now how would I delete all files that came up in that search?

---

### Post by shreepads on 2012-10-16
Try find with -exec

---

### Post by SWGraphics291 on 2012-10-16
This is not much of a beginner thing, you should post this somewhere more complicated.

---

### Post by drmrgd on 2012-10-16
What you'll need here is a couple things.  First, you'll need grep to search the files for the string you want.  Then you'll need to pipe that grep command to a rm command using 'xargs'.  Finally, (I know I said a couple...maybe more like a few depending on your goal!), you'll need to enable the globstar option if you want recursion (i.e. look in subdirectories for files to delete).  So, let's say I have something like this:

```
$ ls -R
.:
file1  file2  file3  file4  file5  testdir1  testdir2  testdir3  testdir4

./testdir1:
file1

./testdir2:

./testdir3:

./testdir4:
file1
```

I have 4 files in the top directory, along with 4 subdirectories, some of which contain a file.  File's 1 and 3 contain the string "ipAddress:":

```
$ grep "ipAddress:" *
file1:ipAddress:
file3:ipAddress:
```

So, there's the first clue, grep will return files that match a string.  That's a little too much information for the shell, though as we want to pass that to a 'rm' command.  So, we'll suppress some output with the '-l' option:

```
$ grep -l "ipAddress:" *
file1
file3
```

You'll now notice that the output is much more reduced and ready to pipe into another command.  So, if I now want to delete those files that matched, I'll just pipe it to the 'rm' command using 'xargs' (note: I precede 'rm' with 'echo' just to see what's going to be deleted without deleting anything...sort of a dry run to make sure everything's working as I expect it):

```
$ grep -l "ipAddress:" * | xargs echo rm
rm file1 file3
```

So, the command (when I remove 'echo') will delete files 1 and 3 since they contain the string "ipAddress".  However, we didn't delete any of the files that were in the subdirectories as glob alone ('*') is not enough for recursion.  For that we'll need globstar ('**'), which needs to be turned on in the shell with a simple command:

```
shopt -s globstar
```

So, once we turn on the shell globstar option and use it:

```
$ shopt -s globstar
$ grep -l "ipAddress:" ** | xargs echo rm
rm file1 file3 testdel.sh testdir1/file1 testdir4/file1
```

You now see that not only was file1 and file3 in the top directory deleted, but the shell also found the matches in 'testdir1' and 'testdir4' and deleted those too.  

You can go further if you want to actually make a script by using variables to hardcode the directories to search in (again taking advantage of globstar), or even take those directories in as command line arguments.  

Hope that helps!

---

### Post by Vaphell on 2012-10-16
> **drmrgd said:**
> 
However, we didn't delete any of the files that were in the subdirectories as glob alone ('*') is not enough for recursion.  For that we'll need globstar ('**'), which needs to be turned on in the shell with a simple command:

```
shopt -s globstar
```

So, once we turn on the shell globstar option and use it:

```
$ shopt -s globstar
$ grep -l "ipAddress:" ** | xargs echo rm
rm file1 file3 testdel.sh testdir1/file1 testdir4/file1
```

You now see that not only was file1 and file3 in the top directory deleted, but the shell also found the matches in 'testdir1' and 'testdir4' and deleted those too.  


two words: **grep -r** ;)

---

### Post by drmrgd on 2012-10-16
Sheesh!  I have two more words for myself: **man grep**.  I totally forgot about the -r option!

Ok, in that case, ignore all the globbing non-sense I posted above and just use:

```
grep -rl "ipAddress:" * | xargs echo rm
```

Again, remove the 'echo' part when you're satisfied it's working the way you want it to.

Thanks Vaphell!

---

### Post by Dabo Ross on 2012-10-22
Thank you all for the help. I believe I have found the answer though. I kind of forgot about this thread while I continued searching, and for some reason the email subscription notifications were not working, so I forgot to post what I had found.
This is the script I am currently using, that seems to work.
```
for i in /home/newlanders/files/*
do
grep "ipaddress" $i -i -c | grep 0 -q && rm $i
done
```

Thank you all, and for future reference, where should I post bash scripting things?

---

### Post by dannyboy79 on 2012-10-22
how often do you want to run it? it should be placed in your environments path.

/usr/local/ is where I put my sheel scripts. Also, if you want it to run on a regular basis, add it as a cron job. Good luck

---

### Post by Dabo Ross on 2012-10-22
> **dannyboy79 said:**
> how often do you want to run it? it should be placed in your environments path.

/usr/local/ is where I put my sheel scripts. Also, if you want it to run on a regular basis, add it as a cron job. Good luck

This is actually part of a bigger script, that I use in an auto-restart of My Server every day. It is a crontab job :P

I keep all my scripts in /home/newlanders/ because there is nothing else in my home folder, and I like to have access to them without having root rights. I can show you the whole Restart script if you want, including a lot more than just this.
Also I substitute a few things when I post stuff like this on the forums, I am actually using the script for a different directory.

---

### Post by drmrgd on 2012-10-22
Glad you got that sorted out.  In regard to your question about posting these kinds of things, you can post just about anywhere I suppose.  There is, however, a sub-forum called "Programming Talk" under the Development and Programming forum that's ideal for this kind of thing.

Also, wanted to point out that you can create a 'bin' directory in your home directory that will be part of your path.  You'll have to log out and in again in order for the change to take effect.  Afterward, though, you'll be able to dump your scripts in there and call them from anywhere just as if they were in /usr/bin or a system wide bin folder. However, they'll be limited to just you.

---


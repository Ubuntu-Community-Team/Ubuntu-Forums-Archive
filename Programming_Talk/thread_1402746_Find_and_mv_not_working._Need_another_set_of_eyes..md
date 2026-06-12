---
title: "Find and mv not working. Need another set of eyes. Operator error."
date: 2010-02-09
forum: Programming Talk
---

### Post by Kayone on 2010-02-09
files:
they are 1-5 digit numbers (ephemeral ports). They are named #.bin. 
ex: 31337.bin

current directory structure:
/var/www/html/thing/place/data/2010/1/18/   

** the problem here is that there are multiple locations for .bin files that I need to pull out. This is the main/common location/path. I am trying to find the files recursively and then put them in a location that I can eventually SSH them from. Since I am noob, I am trying to do this in steps so I can learn.

needed directory structure:
/var/www/html/thing/place/data/kayone/2010/1/18/

** kayone is the location that I am creating for all of the interesting files. I want to keep the 2010/1/18 so I can maintain some sense of structure. I can keep the original path past the date. I don't care what happens after that point as long as all of the files reside there. Ultimately, I am going to re-run this command line function on all of the dates manually. I would like to do it so I don't have to do that but I think the process will be too complicated to make the time saved worth the effort... 




I don't really know what I need. I don't know what I am doing wrong. This is where I am stuck. Any suggestions? 

```
find . -size +1k -type f -name *.bin -printf 'mv "%h%f" "%h/kayone/"\n'
```

-size=  I want to make sure I am cutting out some of the crapola. This ensures that.
-type= I only want to look at files.
-name= I only want files that have the .bin file name/extension
-printf= once I have found all of the above parameters, I want to move the files to another location. I want to keep the same file structure. I want to move the full contents of the files as well. I don't want to get rid of the original files. I need them to stay in the same place. I basically want to make a copy of them.  

Should I be using -exec instead of -printf?
Shouldn't I be using cp instead of mv? I am clueless as usual.

---

### Post by cariboo on 2010-02-10
A bump for the move.

---

### Post by saulgoode on 2010-02-10
> **Kayone said:**
> I don't really know what I need. I don't know what I am doing wrong. This is where I am stuck. Any suggestions? 

find . -size +1k -type f -name *.bin -printf 'mv "%h%f" "%h/kayone/"\n'

I didn't really read all of your details, but your use of -name seems problematic, since the ****.bin*** will be expanded by the shell interpreter to a list of matching files in the current directory (e.g., "file1.bin file2.bin file3.bin" -- perhaps nothing at all if no files match).

Try disabling expansion with either 

```
find . -size +1k -type f -name '*.bin' -printf 'mv "%h%f" "%h/kayone/"\n'

find . -size +1k -type f -name \*.bin -printf 'mv "%h%f" "%h/kayone/"\n'
```

---

### Post by Kayone on 2010-02-10
> **cariboo907 said:**
> A bump for the move.

I am a noob so I always post in the newbie section. You rock. Much appreciated. 

Will post here for now on when it comes to command line questions.

---

### Post by Kayone on 2010-02-10
> **saulgoode said:**
> I didn't really read all of your details, but your use of -name seems problematic, since the ****.bin*** will be expanded by the shell interpreter to a list of matching files in the current directory (e.g., "file1.bin file2.bin file3.bin" -- perhaps nothing at all if no files match).

Try disabling expansion with either 

```
find . -size +1k -type f -name '*.bin' -printf 'mv "%h%f" "%h/kayone/"\n'

find . -size +1k -type f -name \*.bin -printf 'mv "%h%f" "%h/kayone/"\n'
```

I really need to start using the CODE tag. I fail :)

I am kind of confused about your post though. I thought I wanted to view matching files in the current directory (as well as all of the subdirectories)!? 

Basically, I want to grab all of the bin files that are greater than 1k in size and place them in a happy place. Won't the single quotes and escape character look for the exact filename of *.bin?

Either way, thanks for looking at my post. I usually give myself 2-3 days to find an adequate solution. If I cant figure one out, I do it the long way. I am trying to avoid it if possible. This forum is always helpful. I'm still learning (or doing my best to learn). Hopefully one of these days, I will be on here helping someone else. Hopefully :P

---

### Post by Hellkeepa on 2010-02-10
HELLo!

The reason you have to add quotes, or escape the star, is because if you don't then the shell (Bash) will think that the star is meant for it, instead of the "find" command. Replacing it with a list of all of the BIN-files in the current folder, before sending the entire line to "find".
By escaping it, you're telling the shell that it should treat the star as normal text, and send it unchanged to the command in question.

Happy codin'!

---

### Post by Kayone on 2010-02-10
> **Hellkeepa said:**
> HELLo!

The reason you have to add quotes, or escape the star, is because if you don't then the shell (Bash) will think that the star is meant for it, instead of the "find" command. Replacing it with a list of all of the BIN-files in the current folder, before sending the entire line to "find".
By escaping it, you're telling the shell that it should treat the star as normal text, and send it unchanged to the command in question.

Happy codin'!

I was lost but I think I was found. 
Much appreciation goes out to the both of you for the explanations. 

I actually had to call in one of my co-workers to break it down further for me. I was lost because I tested out the find command before I moved further and it did exactly what I wanted it to. I think I get why you both were saying it though. Please correct me if I am wrong.

Bash interprets the find command. Find has a set of parameters that it understands/interprets. Find understands -size for instance (bash doesn't). The reason you need to isolate the * in find is because bash knows how to use utilize it (and may take it and run with it in some cases).  (<-- I pray that makes sense...). You are pointing out a logic problem more so than a functionality issue. Honestly, I need logic (lots of it). 

I was totally lost because, at the time I wrote this, I thought that the escape character (and single quotes) would make the -name command look for the exact file name of *.bin. I was sitting here thinking WTF are these guys talking about. 

Man, I still have so much to learn. 
I think my foo skill just got +1.  
woot!

:popcorn:

---

### Post by Kayone on 2010-02-10
I think I am going to need to write a for loop for this one. I am not 100% sure about this. The more I look at it, the more I am starting to think that I need to. 

I might try out find + -exec together (and -exec my loop with cp and awk). Cringe. More craziness OTW I'm sure.

---

### Post by Hellkeepa on 2010-02-10
HELLo!

You're entierly correct in your analysis of the star-issue, and your post made sense. :-)

As for the whole For-loop thingy: You should not have to, though I suspect you don't need to use "-printf" in this case, but "-exec mv {} <target> \;"

Happy codin'!

---

### Post by Kayone on 2010-02-10
> **Hellkeepa said:**
> HELLo!

You're entierly correct in your analysis of the star-issue, and your post made sense. :-)

As for the whole For-loop thingy: You should not have to, though I suspect you don't need to use "-printf" in this case, but "-exec mv {} <target> \;"

Happy codin'!

I left out the part where I didn't want to move the files really. I liked the options mv had so I was thinking about it. I actually need to leave the original files were they were. I was hoping mv could accomplish that. I don't think it can. I'll post my thoughts when I get them together. 

I guess I could probably just cp them exactly as they are and reorganize them later. I will just need to think about it for a minute.

---

### Post by Hellkeepa on 2010-02-10
HELLo!

Just use CP instead of mv then.

Happy codin'!

---

### Post by saulgoode on 2010-02-10
> **Kayone said:**
> I left out the part where I didn't want to move the files really. I liked the options mv had so I was thinking about it. I actually need to leave the original files were they were. I was hoping mv could accomplish that. I don't think it can. I'll post my thoughts when I get them together. 

I guess I could probably just cp them exactly as they are and reorganize them later. I will just need to think about it for a minute.

Here is a "loopless" approach:
[B][INDENT]cd /var/www/html/thing/place/data 
mkdir -p ./kayone
find . -path ./kayone -prune -o -name '*.bin' -type f -print0 | xargs -0 cp -v -u --parents -t ./kayone[/INDENT][/B]
First change to the top-level data directory, then make a subdirectory called *kayone* (the '-p' option ignores this step if *kayone* already exists).

**find** -- use the find command
**.** -- work with the current directory and all of its subdirectories
**-path ./kayone -prune **-- this evaluates to TRUE for any results that contain the string "./kayone" in the full path (i.e., all files in *kayone*)
**-o** -- the OR operator: if the result up till now is TRUE (i.e., all files in *kayone*) then we have done what we needed (and we do NOT print the file). If the result is FALSE (all other files/directories) then we continue testing.
**-name '*.bin'** -- result is TRUE if name includes ".bin"
**-type f** -- and it is a regular file (no operation specified defaults to the AND operation)
**-print0** -- print the filename with a zero-byte at the end (to allow for spaces in the filename)
**|** -- pipe the output of the find command to...
**xargs** -- process each filename using the specified command using 'find' output as arguments
**-0** -- treat filenames as zero-delimited (permitting spaces in filenames)
**cp** -- we are going to copy the files
**-v** -- be verbose (i.e., list the files that are copied). Optional.
**-u** -- don't replace existing files unless a newer one is available. Optional.
**--parents** -- copy not just the file, but its location in the original directory tree (from the toplevel parent on down)
**-t ./kayone** -- the target for all the copied files should be the *kayone* directory

The '-t' option to the **cp** command is important. XARGS is (to my knowledge) only able to work with commands that accept a single set of inputs which are each treated in the same manner. The **cp** command normally uses the last argument provided as the target file/directory. If the target directory were not provided with the '-t' option then the last file produced by the 'find' would be treated as the target file.

---

### Post by Kayone on 2010-02-12
> **saulgoode said:**
> Here is a "loopless" approach:
<b>[INDENT]cd /var/www/html/thing/place/data 
mkdir -p ./kayone
find . -path ./kayone -prune -o -name '*.bin' -type f -print0 | xargs -0 cp -v -u --parents -t ./kayone[/INDENT]</b>
First change to the top-level data directory, then make a subdirectory called *kayone* (the '-p' option ignores this step if *kayone* already exists).

**find** -- use the find command
**.** -- work with the current directory and all of its subdirectories
**-path ./kayone -prune **-- this evaluates to TRUE for any results that contain the string "./kayone" in the full path (i.e., all files in *kayone*)
**-o** -- the OR operator: if the result up till now is TRUE (i.e., all files in *kayone*) then we have done what we needed (and we do NOT print the file). If the result is FALSE (all other files/directories) then we continue testing.
**-name '*.bin'** -- result is TRUE if name includes ".bin"
**-type f** -- and it is a regular file (no operation specified defaults to the AND operation)
**-print0** -- print the filename with a zero-byte at the end (to allow for spaces in the filename)
**|** -- pipe the output of the find command to...
**xargs** -- process each filename using the specified command using 'find' output as arguments
**-0** -- treat filenames as zero-delimited (permitting spaces in filenames)
**cp** -- we are going to copy the files
**-v** -- be verbose (i.e., list the files that are copied). Optional.
**-u** -- don't replace existing files unless a newer one is available. Optional.
**--parents** -- copy not just the file, but its location in the original directory tree (from the toplevel parent on down)
**-t ./kayone** -- the target for all the copied files should be the *kayone* directory

The '-t' option to the **cp** command is important. XARGS is (to my knowledge) only able to work with commands that accept a single set of inputs which are each treated in the same manner. The **cp** command normally uses the last argument provided as the target file/directory. If the target directory were not provided with the '-t' option then the last file produced by the 'find' would be treated as the target file.


WOW!!! That was amazing!!! It appears to have sanity checks built in. I was about to crack open rsync and see if I could do it that way if I could not figure this out. 

I had to read it a few times to grasp it (the AND/OR/TRUE/FALSE always throw me off if I don't read them a few times). 

I am going to crack open the man pages again to fully understand it. When I am done, I'm gonna test it.  I am pretty excited. I think this is exactly what I wanted. /bow

It is so much easier for me to learn command line when I practice what works first and try to comprehend exactly what it is doing. I have been trying to do this on my own, writing my own based off of someone else's work, and it's kicking my butt. I think I need to start doing basic functions via command line so I get more familiar with the man pages and options (I totally missed the --parents when I looked up cp). I tend to only open up the prompt when I am trying to do something complex. I think that's what is killing me.

My hat goes off to everyone.

---

### Post by Kayone on 2010-02-12
It didn't work for some reason. I got the following error (and nothing went into the directory I created):

cp: cannot make directory `./kayone/./01': Permission denied

I had a lot of those over and over. There might have been other errors but it scrolled too fast. I used sudo before I ran it. I don't know. Any ideas?

Are the errors because of the ./ in front of the directory name?  Looking at the shell script created, I was thinking that the ./ stored the binfiles' directory location in PATH so I didn't need to list the absolute path every time (like you can do with executables). 

Now, after thinking about it, I assume the dot stands for current directory. Like           current_directory/kayone/next_directory

Looking at the error, I "think" the problem has to do with:

a. the cp command
b.  the periods in the directory structure


This makes me think it might be the -0 (just a guess though). Maybe I am reading this wrong. 

 "Input  items are terminated by a null character instead of by whitespace, and the quotes and backslash are not special (every character is
 taken literally).  Disables the end of file string, which is treated like any other argument.  Useful when input items might contain white
 space, quote marks, or backslashes.  The GNU find -print0 option produces input suitable for this mode."

I am wondering is this turns the ./ in find into the literal dot forwardslash (./)?

---

### Post by saulgoode on 2010-02-12
> **Kayone said:**
> It didn't work for some reason. I got the following error (and nothing went into the directory I created):

cp: cannot make directory `./kayone/./01': Permission denied

I had a lot of those over and over. There might have been other errors but it scrolled too fast. I used sudo before I ran it. I don't know. Any ideas?
If you create the top-level ('mkdir -p kayone') directory as root then the 'xargs cp' command must also be run as root. A better solution might be to change the owner of the *kayone* directory to the user that is running the command. 

```
sudo mkdir -p kayone
sudo chown $(whoami) kayone
```


> **Kayone said:**
> Are the errors because of the ./ in front of the directory name?  Looking at the shell script created, I was thinking that the ./ stored the binfiles' directory location in PATH so I didn't need to list the absolute path every time (like you can do with executables). 

Now, after thinking about it, I assume the dot stands for current directory. Like           current_directory/kayone/next_directory
Your assumption in the second paragraph is correct. The dot stands for the current directory and can appear anywhere in the path.

[INDENT]**cd /home/kayone/./Images/././Vacation/././Belize**[/INDENT]

is equivalent to 

[INDENT]**cd /home/kayone/Images/Vacation/Belize**[/INDENT]

The periods in the paths produced by 'find' are not a problem.

---

### Post by Kayone on 2010-02-16
When I do the find command without the xargs, I get back results that **do not** show up line by line (delineated?). Is that because of the print0? Will that create an error as well?

I am not sure if this is the expected output though because I have never really messed around with print0. I assume that the print0 is causing it to remove spacing?

**Well, I guess the issue was permission related. I "think" the problem was solved by changing the kayone file permissions. I didn't think it mattered because the files I was copying from (with the find command) were owned by root.  I guess it did matter apparently. When I sudo'd my mkdir, it created the files as root. I guess I need to read up on sudo (again). 

I can't wait for this thing to stop working so I can see what I screwed up :)  Thank Al Gore for inventing backups! **

---

### Post by saulgoode on 2010-02-21
> **Kayone said:**
> When I do the find command without the xargs, I get back results that **do not** show up line by line (delineated?). Is that because of the print0? Will that create an error as well?

I am not sure if this is the expected output though because I have never really messed around with print0. I assume that the print0 is causing it to remove spacing?
The -print0 option specifies that filenames should be separated by NULLs (chars with a value of zero); normally the filenames would be separated by newlines. 

The problem is that newlines are treated the same as spaces when piped as arguments to 'xargs'. So what prints out as:
[INDENT]Some File 1.txt
Some File 2.txt
Some File 3.txt[/INDENT]
would appear to the 'mv' as:
[INDENT]Some File 1.txt Some File 2.txt Some File 3.txt[/INDENT]
and you will receive 'file not found' errors.


-print0 (combined with the -0 option of 'xargs') causes the arguments to effectively appear as:
[INDENT]'Some File 1.txt' 'Some File 2.txt' 'Some File 3.txt'[/INDENT]

---


---
title: "What is wrong with this TINY bash command/script?"
date: 2006-09-05
forum: Programming Talk
---

### Post by em3raldxiii on 2006-09-05
I am attempting to rename multiple .m4b files to .m4a files (because xmms doesn't know how to handle m4b even though it's identical to m4a as far as I know).  Here's the command I am attempting to use:

```
for i in *.m4b ; do sudo mv $i hpcos$((++c)).m4a ; done
```

I get the following errors:

```
mv: target `hpcos1.m4a' is not a directory
mv: target `hpcos2.m4a' is not a directory
mv: target `hpcos3.m4a' is not a directory
mv: target `hpcos4.m4a' is not a directory
mv: target `hpcos5.m4a' is not a directory
mv: target `hpcos6.m4a' is not a directory
mv: target `hpcos7.m4a' is not a directory
mv: target `hpcos8.m4a' is not a directory
mv: target `hpcos9.m4a' is not a directory
mv: target `hpcos10.m4a' is not a directory
mv: target `hpcos11.m4a' is not a directory
mv: target `hpcos12.m4a' is not a directory
mv: target `hpcos13.m4a' is not a directory
mv: target `hpcos14.m4a' is not a directory
mv: target `hpcos15.m4a' is not a directory
mv: target `hpcos16.m4a' is not a directory
mv: target `hpcos17.m4a' is not a directory
mv: target `hpcos18.m4a' is not a directory

```

I don't understand why it thinks I am trying to move them to a directory, instead of just renaming the files.

I just want it to work, gall-darnit.  That or some other lickedy-split way of changing mass filename extensions.

Or just a way to make xmms accept m4b as m4a files.

Thanks for y'er input!

*EDIT:  Also, the filenames were originally very long and contain a LOT of spaces, hence my shortening to the smaller filename.  Unfortunately, the files are in sequence too - is there something I should do to retain the sequence?*

---

### Post by TLE on 2006-09-05
> **em3raldxiii said:**
> 
```
for i in *.m4b ; do sudo mv $i hpcos$((++c)).m4a ; done
```

*EDIT:  Also, the filenames were originally very long and contain a LOT of spaces, hence my shortening to the smaller filename.  Unfortunately, the files are in sequence too - is there something I should do to retain the sequence?*

Yeah it's the spaces that's the problem. Somewhere along that command the different parts of the filenames seperated by spaces get enterpreted as individual filenames, that why it start talking about directories, the shell thinks you want to move severel files to one destination, hence a directory. So the only thing you need to do is to quote the $i variable, so that it gets interperted as one filename.

```
for i in *.m4b ; do sudo mv "$i" hpcos$((++c)).m4a ; done
```

That should work. You gotta love the terminal.

---

### Post by em3raldxiii on 2006-09-05
Ye know, I tried putting quotes around just about everything, but somehow the $1 escaped my quotation-madness.  LOL!  Thanks!

PS.  I think Nautilus could really use a mass-rename option, it would be prettier for people who don't like CLI.

---

### Post by em3raldxiii on 2006-09-05
Okay, so this script now works beautifiully - but it has the annoying tendency to place files in the wrong order.

Files originally go from "file number 1.m4b" up to "file number 17.m4b"

this script has the following results:
```

"file number 1.m4b" is moved to "hpcos9.m4a"
"file number 2.m4b" is moved to "hpcos10.m4a"
...
"file number 9.m4b" is moved to "hpcos17.m4a"
"file number 10.m4b" is moved to "hpcos1.m4a"
"file number 11.m4b" is moved to "hpcos2.m4a"
...
"file number 17.m4b" is moved to "hpcos8.m4a"

```

Luckily I caught this in the 17 file directory which is relatively easy to deal with.  If I had this problem in the 85 file directory, it would have been rather irritating.  So, what would be a better way to rename these files?  I assume that somehow changing "file 1.m4b" to "file 01.m4b" would likely be the right path?  Any recommendations?

---

### Post by nereid on 2006-09-05
Hi, maybe you could try something along the way with find and rename.

```

find DIRECTORY -type f -print0 | xargs -0r rename 's/(.*)\.m4b$/hpcos$1\.m4a/' *.m4b

```

I don't know if it works alright but something along this way.

---

### Post by etank on 2006-09-05
I would just do what you have already said and use 01.m4b instead of 1.mdb.

---

### Post by TLE on 2006-09-05
> **etank said:**
> I would just do what you have already said and use 01.m4b instead of 1.mdb.

if the original files all have the same name exept for the number you could make it pull the number out of the old file and put it into the new on. I would do that in a script though.

If that is possible and you want to try it let me know and I'll help you with the script if nescesary.

---

### Post by em3raldxiii on 2006-09-05
Well you've all been very helpful!  I ended up just grabbing the single-digit numbers and manually changing them to double-digit numbers, considering there were only 9 of them ;)

However, since I am a relative noob to the whole scripting world, this would be an excellent learning exercise.

So lets go hog wild and say we have a directory with 200 (well, 199 anyway) numbered files, with no leading zeros.  The files have tons of spaces, and we want to change the extension.

The directory contains this:
```

our experimental file number 1.foo
...
our experimental file number 200.foo

```

and we want to change it to this:
```

exfil001.bar
...
exfil200.bar

```

Now, with my rudimentary coding skillz, I am thinking a couple of nested if/then statements would probably work to first add leading zeros as required, and then we would change the filenames by either stripping all but the numbers and prefixing it with our new filename, or by using the renaming code we've already used here.

So, how far out to lunch am I?

Just an interesting autobiographical note: I have very limited "real-world" coding experience.  I took a horrendous course years ago in Turbo Pascal which I have mostly forgotten; I can do some basic javascript, HTML, PHP; and when I was a kid I was pretty good with uber-leet Commodore 64 basic.  LOL!  Wow, nice resume LOL ... I'm not that old, really ...

Anyhoo ... I really appreciate the time you (TLE) and the other's have taken to help me out.

---

### Post by TLE on 2006-09-05
> **em3raldxiii said:**
> 
Now, with my rudimentary coding skillz, I am thinking a couple of nested if/then statements would probably work to first add leading zeros as required, and then we would change the filenames by either stripping all but the numbers and prefixing it with our new filename, or by using the renaming code we've already used here.

So, how far out to lunch am I?
Yeah that sounds about right. I would probably strip all but the number, then turn that number into the apropriate string(adding zero and all that) and then rename.

If you are interessted in scripting in Linux you can have a look at the following resources:

[http://www.freeos.com/guides/lsst/]("http://www.freeos.com/guides/lsst/")
[http://www.faqs.org/docs/abs/HTML/index.html]("http://www.faqs.org/docs/abs/HTML/index.html")

> **em3raldxiii said:**
> Anyhoo ... I really appreciate the time you (TLE) and the other's have taken to help me out.
No problem at all. Have fun.

---

### Post by ifokkema on 2006-09-07
Euhm... guys, maybe I'm not getting this, but why not just used:
```
rename 's/\.m4b$/\.m4a/' *.m4b
```
Seems to me it would've saved you a lot of hassle. Also, for the graphical bulk-renaming: I vaguely remember thunar had this option, but can't clearly remember. It was a file manager and I think it had even a separate package for a GUI file renaming program.

---

### Post by nereid on 2006-09-07
@ifokkema

But it is not exactly what he wanted. He wanted to rename the files XY.m4b into hpcosXY.m4a with a padding of zeros.

As I posted earlier a combination of find and rename would just do the job. Bash scripting makes this only more complicated.

---

### Post by ifokkema on 2006-09-07
> **nereid said:**
> @ifokkema

But it is not exactly what he wanted. He wanted to rename the files XY.m4b into hpcosXY.m4a with a padding of zeros.
Ah, missed the 'hpcos' in the original post.

But as far as I understand, he needed the padding just to prevent the troubles resulting from using the mv command in stead of rename... figured it was a 'patch' not necessary when using rename.

> **nereid said:**
> As I posted earlier a combination of find and rename would just do the job.
```
find DIRECTORY -type f -print0 | xargs -0r rename 's/(.*)\.m4b$/hpcos$1\.m4a/' *.m4b
```
Is n't the *.m4b at the end redundant or even possibly causing unexpected behaviour in some situations?

> **nereid said:**
> Bash scripting makes this only more complicated.
I completely agree, as was the reason for my post :)

---

### Post by nereid on 2006-09-07
> **ifokkema said:**
> Is n't the *.m4b at the end redundant or even possibly causing unexpected behaviour in some situations?


Maybe, I haven't tested the command. But it should work as expected ;)

> **ifokkema said:**
> I completely agree, as was the reason for my post :)

Behold the power of the mighty commandline :D

---

### Post by TLE on 2006-09-07
Well I don't entirely agree with you guys ;)

Yes I agree that if a simpel command can do the trick, as it probably can in this case, there's no need to script.

But I do not agree that:
> **nereid said:**
> ...the mighty commandline...
is the solution for everything. I suggested scripting tutorials because em3raldxiii shoved an interest in it, and because I think it is a nice supplement to the CLI. Sometimes it almost seems to become a sport to concentrate the most complex of tasks in one command, making it complete unreadable and therefore non-instructive as a learning example for a newcomer. In such cases I think it is an easier solution to write a script and utilize the structure that you can make when you have more than one line to do it on.

Cheers TLE

---

### Post by richardhp on 2006-09-07
> **em3raldxiii said:**
> PS.  I think Nautilus could really use a mass-rename option, it would be prettier for people who don't like CLI.

Coincidence, but just after reading this I saw if you go to applications, Add/Remove, there is a Mass Renamer in the System Section.

---

### Post by nereid on 2006-09-07
@TLE
But scripting is also using the commandline :p And it wasn't even a Perl oneliner ;)

But IMHO you should know your way around your system (in my opinion also if you are using Windows or Mac OS) and, ok you could do it with a GUI application, but you won't learn anything about your system this way. Maybe not everybodies opinion, but hey, thats me ;).

---

### Post by em3raldxiii on 2006-09-07
Wow ... I've sparked quite a little discussion here LOL ... :D

Okay, here's the whole rundown of what, why & how I decided to tackle this plan.

1.  I wanted to take a large directory of files and change the *truly gargantuan* filenames to something more manageable (in one directory, this was hpcos00x).

2.  I wanted to convert the files to .m4a (read change the extension) so they could be handled by xmms because I am not prepared to recompile a plugin at this point (I lack the expertise, despite how simple the task might seem to some of you).

3.  I wanted to learn a little more about scripting.

4.  Some of those "one-liners" you guys post, while they likely do the job, are not very ... conducive to a person learning to use the CLI.  In many cases I don't understand why certain symbols go where they do, and they are not intuitive enough for me to figure out what to change when I a) want to change the outcome, or b) run into errors.

5.  If I come up with a super-handy script, and I fully understand it, I can post the file and I can explain it to other people (read *noobs like me*) which has the positive side effects of bringing more people to the world of CLI/Scripting and inducing me to learn more in the process.

LOL ... and as you can see I am highly verbose, which I think lends itself well to scripting! ;)

Anyway ... I am slowly but surely learning, and what TLE has posted for me has been the most beneficial - not to discredit those who have posted alternatives!  And I think others who encounter similar issues may find this thread useful. :D

Thanks again everyone!

---

### Post by nereid on 2006-09-08
Hey, no problem at all:

```
find DIRECTORY -type f -print0 | xargs -0r rename 's/(.*)\.m4b$/hpcos$1\.m4a/' *.m4b
```

uses find and rename.

**find:**
-type f
is setting find to get only files
-print0
is a switch to get the whole pathnames of the files, so that you can use them in a shell script or like here with xargs

**xargs:**
is used to generate an input for rename
-0r
this switch allows spaces and newlines in filenames

**rename:**
does that the name implies and renames files
's/(.*)\.m4b$/hpcos$1\.m4a/'
is a regular expression to grab everything before the dot in the filename, put hpcos before it and change the extension
*.m4b
rename all files with the m4b extension

Hope I could explain this horrid looking oneliner ;)

---

### Post by em3raldxiii on 2006-09-08
HAHA!  Someone else who uses the word *horrid* ;)  LOL!

Okay, this is good for me too.  Here are some NOOB questions for you (I know, I could read about this elsewhere, but this is just so uber handy haha)

** s/ ** - what exactly is that?  And why are their brackets in this:  **(.*)**

I *think* I sorta understand all the bla/bla\bla/bla\ stuff; though I am not 100% sure.  It's like you are dividing up the filename, but it's still somewhat confusing.

what's with DIRECTORY?  would that be /the/location/of/my/specific_files in which I want to do the searching/renaming?  If so, this one-liner could be changed to a VERY short script that could take an argument that would be used for the DIRECTORY portion.  But I am unsure how to pass such a variable into the script ...

./name_of_script.sh /location/of/files

would pass /location/of/files INTO the script which would use it.  This way, one could put the script in within the $path so it can be called from anywhere in the filesystem?  Could be handy.

Mmmm ... one more thing, is it possible to force this to add leading zeros into the filename?  

Now, when I do a man -k xargs, all it gives me is this:  **- build and execute command lines from standard input** ... um ... yeah ... okay .... that explains everything!  I can see the light!!  It all makes SO much sense when you put it THAT way ... not.  ;)  LOL, I suppose I am REALLY showing off my Newb-ness hey?  I am thinking perhaps going and reading those tutorials might be a good idea ....

Well, I have to say one thing though - I can understand from "simple" oneliners like this one why some people are "afraid" of the command line.  This is the sort of "horrid" thing that really freaks people out.  Luckily *I* am not one such ... for the most part.  I just like to understand what the heck is happening.

Bla bla bla ... I gotta go get some sleep.  Rochelle (my wife) has a band rehearsal tomorrow night so I am going to need my sleep tonight.  I tell ya, having a rock band in your basement is ... *interesting*.

---

### Post by nereid on 2006-09-08
Ok, this is a little bit longer and I hope you're still with me ;)

**s/FROM/TO/** starts a Regular Expressions substitution
We want to subtitute the extension and we want to add the hpcos to the front of the filename. The slashes divide the command into a FROM section and a TO section.

**(.*)**
The brackets denote a group. We do want to save the original name from the FROM section and use it in the TO section. The dot means that it should match every character and the star means that it should continue until it finds the **\.** (an escaped real dot, not the magic sign for every character). So we can relate to this group in the TO section with the $1.

**m4b$**
The dollar sign here means that the string m4b should be at the end of the working string not somewhere in the middle (match something like x.m4b but nothing like m4b.txt).

**hpcos$1\.m4a**
This is the TO section. This means nothing else than: Put hpcos in the front, add the saved filename and append .m4a.

**DIRECTORY**
Substitute this with your target directory

To save this thing as a script (beware no error checking and no questions):

```

#!/bin/bash
find -type f -print0 | xargs -0r rename 's/(.*)\.m4b$/hpcos$1\.m4a/' *.m4b

```

Save it for example as my_rename.sh, chmod +x my_rename.sh and call it like this: ./my_rename.sh /location/of/your/directory

I'm not sure about the padding of zeros but if you ask someone with a little bit more experience I'm sure there is someone who knows how to do it.

**xargs**
It does that the man page implies ;) You need it to generate the input for the rename command. find returns a long list of all files. rename can't do anything with this list. xargs splits the list into single commands and handles whitespaces and newlines in the filenames.

I hope that I haven't put you of ;) And I also like to know what is going on. So I can understand your need for answers :) Nothing wrong with questions, we were all noobs sometimes.

---

### Post by em3raldxiii on 2006-09-08
I think I am beginning to wrap my head around it.  It's not terribly difficult really, once some of the fundamentals are understood.  But I think that's where most people get lost, the fundamentals don't always seem particularly intuitive.  I think this is why scripting languages like javascript are more easily understood.

I don't have time to reply at length just now, but I will perhaps later.  It turns out that Rochelle's rehearsal got moved into Edmonton (we're actually a little ways out of Edmonton), so I have a much busier day ahead of me than I originally planned.

Thank you very much for your explanation.  I'll have more questions for you soon enough ;)

---

### Post by nereid on 2006-09-09
Than I'm glad you understood the most if not all of this.

And I'm happy to answer your questions if I can ;)

---

### Post by ghostdog74 on 2006-09-09
> **em3raldxiii said:**
> I am attempting to rename multiple .m4b files to .m4a files (because xmms doesn't know how to handle m4b even though it's identical to m4a as far as I know).  

hi
just want to rename .m4b to .m4a right?
here's an alternative, in Python

```

>>> import os
>>> for files in os.listdir(os.getcwd()):
... 	path,ext = os.path.splitext(files)
... 	if ext == ".m4b":
... 		try:
... 			os.rename(i, path + ".m4a")
... 		except Exception,e:
... 			print e

```

spaces taken care of.
cheers

---

### Post by ifokkema on 2006-09-11
> **em3raldxiii said:**
> Now, when I do a man -k xargs, all it gives me is this:  **- build and execute command lines from standard input** ... um ... yeah ... okay .... that explains everything!  I can see the light!!  It all makes SO much sense when you put it THAT way ... not.  ;)  LOL, I suppose I am REALLY showing off my Newb-ness hey?

So why not try `man xargs` and read the whole thing? :)
Quit the man page by pressing q.

---

### Post by ifokkema on 2006-09-11
> **nereid said:**
> ```

#!/bin/bash
find -type f -print0 | xargs -0r rename 's/(.*)\.m4b$/hpcos$1\.m4a/' *.m4b

```

Save it for example as my_rename.sh, chmod +x my_rename.sh and call it like this: ./my_rename.sh /location/of/your/directory

Hi Nereid,

Have been away for a couple of days so could not reply. I'm afraid the script doesn't work, because it's not catching the used argument and using it in the find command. I think it needs to be:

```

#!/bin/bash
find -type f -print0 $1 | xargs -0r rename 's/(.*)\.m4b$/hpcos$1\.m4a/' *.m4b

```

The $1 in the find command catches the script's first argument.

Ivo

---

### Post by nereid on 2006-09-11
I do know that $1 is used for the argument but I discovered that find works without it. Just try it out using only the find command

```

#!/bin/bash

find -type f
```

Save the script and execute it with an directory as argument. You should get a list of all files contained in the target directory.

---

### Post by ifokkema on 2006-09-12
> **nereid said:**
> I do know that $1 is used for the argument but I discovered that find works without it. Just try it out using only the find command

```

#!/bin/bash

find -type f
```

Save the script and execute it with an directory as argument. You should get a list of all files contained in the target directory.

Tried it before I posted yesterday, and tried your suggested code again. Sorry, doesn't work for me :)

In ~/tmp:
```
  12:07:09 ifokkema@5-HKG-02-0098:tmp$ ./test .
./test
  12:08:45 ifokkema@5-HKG-02-0098:tmp$ ./test ~/www
./test

```

---

### Post by TLE on 2006-09-12
Hey everybody. I hope em3raldxiii will forgive me for using this thread for this question, it is on another matter so please everyone do answer if you can but not at the expence of focus on the original subject so I don't become guilty of thread hijacking. But since there seems to be so many commandline/script competent people here it seems like an apportunity. I was wondering, do any of you know if it, in a bash script, is possible to replace one of the script commandline arguments, say $2. I'm asking this beacuse I want to implement a few long options ala --version, but the bashinternal getopts don't handle them and I would rather not use external commands. If this is possible I could just loop thorugh $@ and test if there was a long option and then replace it with a short, and then use getopts.

---

### Post by nereid on 2006-09-12
@ifokkema
This is really strange. On my system this is working all right.

@TLE
Sure, as far as I know, you can replace $2 with any value. It is nothing else than a simple variable.

---

### Post by TLE on 2006-09-12
@nereid
But how do I acces it. If it were an ordinary variable, like say $input I would do:
```
unset input
input="New value"
```
But I can't do that for $2

---

### Post by ifokkema on 2006-09-12
> **nereid said:**
> @ifokkema
This is really strange. On my system this is working all right.

Huh? Just to make sure we're not missing anything:

```
  14:37:18 ifokkema@5-HKG-02-0098:tmp$ pwd
/home/ifokkema/tmp
  14:37:21 ifokkema@5-HKG-02-0098:tmp$ cat test
#!/bin/bash
find -type f
  14:37:23 ifokkema@5-HKG-02-0098:tmp$ ./test
./test
  14:37:24 ifokkema@5-HKG-02-0098:tmp$ ./test .
./test
  14:37:27 ifokkema@5-HKG-02-0098:tmp$ ./test ../
./test
  14:37:29 ifokkema@5-HKG-02-0098:tmp$ ./test ../../
./test
  14:37:32 ifokkema@5-HKG-02-0098:tmp$ ./test ~/www/
./test
```

---

### Post by nereid on 2006-09-12
@ifokkema
This **is** really weird

```

bin $ cat test.sh
#!/bin/bash

find -type f
bin $ ls .
createiso.sh  emacs.sh  mp3_noexec.sh  run.py  test.sh  warcraft  win_perm.sh
bin $ ./test.sh .
./createiso.sh
./warcraft
./run.py
./mp3_noexec.sh
./test.sh
./win_perm.sh
./emacs.sh

```

On my machine

@TLE
Ok, I tried it and it did not work that was my bad. Can't you use other variables? Or maybe you would like to take a look at bashburn, a cdrecord frontend written as bash script.

---

### Post by ifokkema on 2006-09-12
> **nereid said:**
> @ifokkema
This **is** really weird

```

bin $ cat test.sh
#!/bin/bash

find -type f
bin $ ls .
createiso.sh  emacs.sh  mp3_noexec.sh  run.py  test.sh  warcraft  win_perm.sh
bin $ ./test.sh .
./createiso.sh
./warcraft
./run.py
./mp3_noexec.sh
./test.sh
./win_perm.sh
./emacs.sh

```

On my machine
That's still expected, since . is the current directory, but what about ```
./test.sh ../
```
Does it return the same, or the files in the parent directory?

---

### Post by em3raldxiii on 2006-09-13
@ TLE:  itsallgood, my friend - you are welcome to "hijack" this thread all ya want :D.  I've got a few other little CLI and Scripts to talk about ... just not ATM, it's too late and I don't really feel like it LOL.

---

### Post by nereid on 2006-09-13
@ifokkema
I am sorry to disappoit you ;) but using .. as an argument produces the list of files from the parent directory.

---

### Post by ifokkema on 2006-09-13
> **nereid said:**
> @ifokkema
I am sorry to disappoit you ;) but using .. as an argument produces the list of files from the parent directory.

OMG... Could this be a **K**ubuntu thing?

---

### Post by nereid on 2006-09-13
No, I wouldn't say that. I used Gentoo before and it also worked there.

---


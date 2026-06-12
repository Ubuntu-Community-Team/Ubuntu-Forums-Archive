---
title: "Bash Script"
date: 2008-05-18
forum: Programming Talk
---

### Post by LookUpSeeBlu on 2008-05-18
Hi,

I would like to write a bash script to go through a directory structure and find any files that are .wma and use lame to convert them to mp3's, then remove the wma.

I am not exactly sure how to start as I have never written a bash script.  Can someone give me some direction?

Thanks.

---

### Post by chewearn on 2008-05-18
Fasten your seat belt, boys and girls, it's going to be a bumpy ride.

Kindergarden:
[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)

Primary school:
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)


Seriously, what you want is a directory listing using "ls", plus "for" loop to walking thru:

```

#!/bin/bash

for i in $( ls ); do
    # the conversion here
done

```For the conversion part, you need a command line codec tool.  e.g. memcoder.

Manual:
```
man mencoder
```EDIT:
Scratch that.  Just realized, mencoder is audio video conversion, not audio only.

---

### Post by LookUpSeeBlu on 2008-05-18
Thanks for the advice.

I found this script which does exactly what I want, except I want it to traverse all the subdirectories when it is run.

```
#!/bin/bash

current_directory=$( pwd )

#remove spaces
for i in *.wma; do mv "$i" `echo $i | tr ' ' '_'`; done

#remove uppercase
for i in *.[Ww][Mm][Aa]; do mv "$i" `echo $i | tr '[A-Z]' '[a-z]'`; done

#Rip with Mplayer / encode with LAME
for i in *.wma ; do mplayer -vo null -vc dummy -af resample=44100 -ao pcm -waveheader $i && lame -m s audiodump.wav -o $i; done

#convert file names
for i in *.wma; do mv "$i" "`basename "$i" .wma`.mp3"; done

rm audiodump.wav
```

This was found here (to make sure I give due credit).

[http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Convert_WMA_to_MP3](http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Convert_WMA_to_MP3)

How can I make this traverse all the subdirectories too?

Thanks.

---

### Post by LookUpSeeBlu on 2008-05-18
Okay, here's a thought, can I walk each subdirectory and in each one, call the above script?

---

### Post by chewearn on 2008-05-18
If the subdirectories are of indeterminate depth, then one (only?) way is to use recursion, which is a tough subject.


If you already know it's always one level deep, then yes, just put an outer for loop for the subdir.

.

---

### Post by vanadium on 2008-05-18
We are just having a thread on a similar question here

[http://ubuntuforums.org/showthread.php?t=797368](http://ubuntuforums.org/showthread.php?t=797368)

---

### Post by chewearn on 2008-05-18
> **vanadium said:**
> We are just having a thread on a similar question here

[http://ubuntuforums.org/showthread.php?t=797368](http://ubuntuforums.org/showthread.php?t=797368)

Cool!

Now I knew the "find" command is good for something. :lol:

.

---


---
title: "Bash rename script"
date: 2007-03-03
forum: Programming Talk
---

### Post by mynamewastaken on 2007-03-03
Hello everyone, I have a bit of a problem. I have a bunch (650+) screenshots with names in this format: ACscrn0001.jpg . Now thats fine except I have duplicate numbers over 2-3 folders. 

Basically what I want to do is rename them all but have them in ascending order. Some of the bash scripts I have come across will do the job nicely as far as renaming them, but my main holdup on the script I have is getting it to increment the number in that same format.

Any help would be appreciated.

---

### Post by picpak on 2007-03-03
Do you want something like this?:

[http://www.getdeb.net/search.php?keywords=Metamorphose](http://www.getdeb.net/search.php?keywords=Metamorphose)

---

### Post by s1ightcrazed on 2007-03-03
I'm not going to script it for you (because what kind of learning experience would that be for YOU, huh?), but I will outline how I would do it. 

You'll need to for loops, one to loop through the directories, and another too loop through and then re-name the files. The loops will be nested, the rename loop inside the directory loop. 

For each of however many directories, you will need to loop through the files to be renamed, and using a numeric variable will rename them. The variable will increment by 1 and will NOT be reset in the loop, meaning that all files will have unique names. the script can even move the files to a different directory at the same time. 

Now get to it boy, go GO!

If you're new to scripting and need more detail, let me know. :-)

---

### Post by mynamewastaken on 2007-03-03
Thank you Picpak, that will be my fallback :)

Crazy if I come up with some code you think you can take a look at it?

---

### Post by Mr. C. on 2007-03-04
Here's a programming problem I gave some students a while back.  It has a pretty nifty rename problem, and solution.  If I recall correctly, it has an increment feature, so it should do what you want and more, including adding or remove suffixes, prefixes, regular expressions, etc.  Look at the week 10 Homework, and Answers.

[http://cis68b1.mikecappella.com/calendar.php](http://cis68b1.mikecappella.com/calendar.php)

Knock yourself out !
MrC

---

### Post by s1ightcrazed on 2007-03-04
> **mynamewastaken said:**
> Thank you Picpak, that will be my fallback :)

Crazy if I come up with some code you think you can take a look at it?

Be happy to. :-)

---

### Post by mynamewastaken on 2007-03-06
```
#!/bin/bash
number=`printf %04d`
for i in `ls *.jpg`; do
  cp $i ../ACscrn"$number".jpg
  number=`expr $number + 1`
done
```


That is what I have right now, this works well except I cannot maintain the 4 number scheme:

ACscrn0000.jpg  ACscrn1.jpg   ACscrn2.jpg   ACscrn3.jpg   ACscrn6.jpg
ACscrn10.jpg    ACscrn20.jpg  ACscrn30.jpg  ACscrn40.jpg  ACscrn7.jpg
ACscrn11.jpg    ACscrn21.jpg  ACscrn31.jpg  ACscrn41.jpg  ACscrn8.jpg
ACscrn12.jpg    ACscrn22.jpg  ACscrn32.jpg  ACscrn42.jpg  ACscrn9.jpg

---

### Post by Mr. C. on 2007-03-06
Don't assign the output of printf to a variable outside the loop.  It will lost the 0's in the arithmetic.

In other words, what does this return?

$ expr 0000 + 0001

Hmmm.  ;-)

In fact, you don't need to assign it at all.

As an extra bonus, bash has built-in arithmetic.  Try :

  (( number += 1 ))

instead of:

  number=`expr $number + 1`

And here's a final bonus for you:

Declare:

debug=echo

at the top of your program.  Then, change your "cp...." line to "$debug cp ..."

Now, you get a fast way to debug the program.  Just set debug to nothing (eg: debug=) when you are ready to let 'er rip.

MrC

---

### Post by mynamewastaken on 2007-03-07
I have played around with the some of the tips you gave me and still can't manage to get the extra 0's to stick on anything other then the first iteration. Any other tips? Btw the $debug one was great, very useful thanks.

---

### Post by Mr. C. on 2007-03-07
Ok, so I asked some questions, but see no answers! :-)

What is the result of this?
```

expr 0000 + 0001
```

And what is the result of this:

```

$number=5
(( number += 1 ))
```

And what is the result of this:
```

$number=6
(( number += 1 ))
printf %04d $number
```


And finally, what is the result of this:
```

$number=3
(( number += 1 ))
echo cp $i ../ACscrn`printf %04d $number`.jpg
(( number += 10 ))
echo cp $i ../ACscrn$(printf %04d $number).jpg
```

---

### Post by mynamewastaken on 2007-03-07
Ahh guess I just needed to have it right up in my face. :) Thanks Mr. C., I modified my script and it works like a charm now.

```
#!/bin/bash
debug=echo

number=0
for i in `ls *.jpg`; do
  $debug cp $i ../ACscrn`printf %04d $number`.jpg
  (( number += 1 ))
done

```

> cp ACscrn0001.jpg ../ACscrn0000.jpg
cp ACscrn0002.jpg ../ACscrn0001.jpg
cp ACscrn0003.jpg ../ACscrn0002.jpg
cp ACscrn0004.jpg ../ACscrn0003.jpg
cp ACscrn0005.jpg ../ACscrn0004.jpg
cp ACscrn0006.jpg ../ACscrn0005.jpg
cp ACscrn0007.jpg ../ACscrn0006.jpg
cp ACscrn0010.jpg ../ACscrn0007.jpg
cp ACscrn0011.jpg ../ACscrn0008.jpg
cp ACscrn0012.jpg ../ACscrn0009.jpg
cp ACscrn0013.jpg ../ACscrn0010.jpg
cp ACscrn0014.jpg ../ACscrn0011.jpg
cp ACscrn0015.jpg ../ACscrn0012.jpg
cp ACscrn0016.jpg ../ACscrn0013.jpg
cp ACscrn0017.jpg ../ACscrn0014.jpg
cp ACscrn0018.jpg ../ACscrn0015.jpg
cp ACscrn0019.jpg ../ACscrn0016.jpg
cp ACscrn0020.jpg ../ACscrn0017.jpg
cp ACscrn0021.jpg ../ACscrn0018.jpg
cp ACscrn0022.jpg ../ACscrn0019.jpg
cp ACscrn0023.jpg ../ACscrn0020.jpg
cp ACscrn0024.jpg ../ACscrn0021.jpg
cp ACscrn0025.jpg ../ACscrn0022.jpg
cp ACscrn0026.jpg ../ACscrn0023.jpg
cp ACscrn0027.jpg ../ACscrn0024.jpg
cp ACscrn0028.jpg ../ACscrn0025.jpg
cp ACscrn0029.jpg ../ACscrn0026.jpg
cp ACscrn0030.jpg ../ACscrn0027.jpg
cp ACscrn0031.jpg ../ACscrn0028.jpg
cp ACscrn0032.jpg ../ACscrn0029.jpg
cp ACscrn0033.jpg ../ACscrn0030.jpg
cp ACscrn0034.jpg ../ACscrn0031.jpg
cp ACscrn0035.jpg ../ACscrn0032.jpg
cp ACscrn0036.jpg ../ACscrn0033.jpg
cp ACscrn0037.jpg ../ACscrn0034.jpg
cp ACscrn0038.jpg ../ACscrn0035.jpg
cp ACscrn0039.jpg ../ACscrn0036.jpg
cp ACscrn0040.jpg ../ACscrn0037.jpg
cp ACscrn0046.jpg ../ACscrn0038.jpg
cp ACscrn0048.jpg ../ACscrn0039.jpg
cp ACscrn0049.jpg ../ACscrn0040.jpg
cp ACscrn0050.jpg ../ACscrn0041.jpg
cp ACscrn0051.jpg ../ACscrn0042.jpg
cp ACscrn0084.jpg ../ACscrn0043.jpg

Now I'll just have to change it so it will cd into the next directory after finishing with the current one ;)

---

### Post by Mr. C. on 2007-03-07
Here's a little magic for you.

Run your script with this:

find . -type d -execdir MyScript {} \; -print

from the top directory from where you want changes to occur.

Replace the word MyScript with the full pathname of your script (eg. /home/mynamewastaken/myscript )

and let it rip.

---

### Post by mynamewastaken on 2007-03-07
That works well except it restarts the number count each time it hits a new directory. ;)

I tried for i in `ls * ACscrn*.jpg`; do, hehe however that copies everything including the directories over and renames it which isn't ideal.

---

### Post by gradedcheese on 2007-03-07
[http://andrey.thedotcommune.com/rename.html](http://andrey.thedotcommune.com/rename.html)

:)

---

### Post by mynamewastaken on 2007-03-07
hehe thx cheese. that one as well as the one posted earlier is/was backups. I like getting it to work myself.

(with some help from C. :-D  )

---

### Post by Mr. C. on 2007-03-07
Arg, you never said you wanted continuously increasing numbers!

Hint: you'll have to use an an environment variable or pass an argument.  Don't initialize it to 0 each time in your script.

MrC

---


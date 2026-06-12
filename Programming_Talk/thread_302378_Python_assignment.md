---
title: "Python assignment"
date: 2006-11-18
forum: Programming Talk
---

### Post by ZankerH on 2006-11-18
Hi

I have a Python assignment for school to complete in one week. We weren't given any particular instructions, but the script has to be at least 50 lines long and include some for/while/if loops, def function(s), and some basic string manipulation. Now, I know how to work with all of those, I'm just completely clueless about what to do. I'm used to people telling me what they wan a script to do, not thinking of it on my own. So, I'm not asking anyone to write me a script, I'd just like to hear some ideas on what to do at all. 

Thank you,
ZankerH

---

### Post by DaveBorealis on 2006-11-18
Hello,

Have you tried jumping into the assignment with both feet and no hesitation?  You have creativity, it just needs to be dusted off and exercised a little.  Perhaps use
```
strng = raw_imput('Type some long sentence: ')
```
to get started, then maybe use
```
strng_list = strng.split(' ')
``` to dice the sentence into single word elements, and have fun.  Use loops and do goofy things to the words.  See what unexpected things crop up as you use some of these methods:
[http://docs.python.org/lib/string-methods.html]("http://docs.python.org/lib/string-methods.html")

Crank up your favorite music, sip a little caffeine (if you're into it), and enjoy yourself!

Just a suggestion....
Dave

---

### Post by ZankerH on 2006-11-18
> **DaveBorealis said:**
> Hello,

Have you tried jumping into the assignment with both feet and no hesitation?

I have. I ended up looking at the IDE for 90 minutes, waiting for the assignment to complete itself.




> **DaveBorealis said:**
> You have creativity, it just needs to be dusted off and exercised a little.  Perhaps use
```
strng = raw_imput('Type some long sentence: ')
```
to get started, then maybe use
```
strng_list = strng.split(' ')
``` to dice the sentence into single word elements, and have fun.  Use loops and do goofy things to the words.  See what unexpected things crop up as you use some of these methods:
[http://docs.python.org/lib/string-methods.html]("http://docs.python.org/lib/string-methods.html")


That actually sounds like a good idea, I'll see if I can stretch it to 50 lines :mrgreen: 

> **DaveBorealis said:**
> Crank up your favorite music, sip a little caffeine (if you're into it), and enjoy yourself!

Just a suggestion....
Dave

Thanks for the suggestion and trying to raise my enthusiasm :)

---

### Post by christhemonkey on 2006-11-18
How about writing a program that asks the user a question randomly from one stored in a dictionary of questions, takes the answer and says whether its right or wrong.

Then if your feeling like going above an beyond, you could make it save the amount of times you have a correct answer an the amount of tries to a file.

---

### Post by ZankerH on 2006-11-18
> **christhemonkey said:**
> How about writing a program that asks the user a question randomly from one stored in a dictionary of questions, takes the answer and says whether its right or wrong.

Then if your feeling like going above an beyond, you could make it save the amount of times you have a correct answer an the amount of tries to a file.

I think that'd be a bit too long, and not really complex enough (just choose random question, input answer, check IF it's correct)...

---

### Post by Note360 on 2006-11-18
I have a idea. Write watered down versions of the gnu apps. It is a good way to get to know python librarys, how to use cli options (which is one big for loop), defs and if you want classes. You can even make modules. I created a few apps like that most of them are good for 10 - 60 lines if you stay simple. You can then combine the ideas togetyher to make a trash can application or something. These are the harder ones but the ones the teacher would go, WOW at. If you need any info just ask here are some lines of code to start you off.

```

#!/usr/bin/env python
import sys
import os
args = sys.argv[1:] # Just makes it simpler for quick glances.

def del_item( item ):
    """ Describe what it does """
    # Insert code to tell if it is a file or directory (GOOGLE)
    # Insert code to delete the file
    # Insert code to scan the directory tree and delete each file an directory in it so that the directory can be deleted
    # This will probably pass the new dir back into this def. If the teacher asks why just say you where trying out some functional programming techniques.

for arg in args[]:
    # Insert code here

```
Unfortuantly this project requires alot of looking on Google. So go on and figure it out from here I gave you a head start. Go on. Oh and write documentation.

EDIT: I messed something up and I used the ruby version of argv I corrected it.

---

### Post by po0f on 2006-11-18
ZankerH,

You've got a week to do it, and it has to be *at least* 50 lines long, you didn't give a maximum limit.  Why not go for it?  50 lines is a really short script IMO.

---

### Post by ZankerH on 2006-11-18
> **Note360 said:**
> I have a idea. Write watered down versions of the gnu apps. It is a good way to get to know python librarys, how to use cli options (which is one big for loop), defs and if you want classes. You can even make modules. I created a few apps like that most of them are good for 10 - 60 lines if you stay simple. You can then combine the ideas togetyher to make a trash can application or something. These are the harder ones but the ones the teacher would go, WOW at. If you need any info just ask here are some lines of code to start you off.

```

#!/usr/bin/env python
import sys
import os
args = sys.argv[1:] # Just makes it simpler for quick glances.

def del_item( item ):
    """ Describe what it does """
    # Insert code to tell if it is a file or directory (GOOGLE)
    # Insert code to delete the file
    # Insert code to scan the directory tree and delete each file an directory in it so that the directory can be deleted
    # This will probably pass the new dir back into this def. If the teacher asks why just say you where trying out some functional programming techniques.

for arg in args[]:
    # Insert code here

```
Unfortuantly this project requires alot of looking on Google. So go on and figure it out from here I gave you a head start. Go on. Oh and write documentation.

EDIT: I messed something up and I used the ruby version of argv I corrected it.

It has to work in windows (we use that at school).

---

### Post by DaveBorealis on 2006-11-18
> **ZankerH said:**
> I have. I ended up looking at the IDE for 90 minutes, waiting for the assignment to complete itself.

Means you forgot to jump.  It's like standing at the water's edge waiting to plunge into the cold.  Ya gotta just do.  Surprisingly it's rather easy...once you simply begin moving your fingers over the keyboard.

---

### Post by Note360 on 2006-11-19
Oh dont worry it will work in windows as long as you use all of pythons built ins and don't start calling rm or anything. Trust me you'll be fine if you do this one. One day to write one day to debug one day to write a stupid backup program incase this one doesnt run oon windows. 3 days out of a 7 day week. (assuming you program for 2 - 4 hours aday)

---


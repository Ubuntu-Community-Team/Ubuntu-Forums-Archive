---
title: "here's a python snippet that's so easy i usually type it instead of saving it"
date: 2009-12-06
forum: Programming Talk
---

### Post by openuniverse on 2009-12-06
.

---

### Post by Greyed on 2009-12-06
Other than breaking the while 1 idiom, not bad.  ;)

[php]
import os 
while 1:
    q = raw_input()
    if q = "q":
        break
    q = os.system("mplayer -framedrop -zoom \"" + q + "\"")
[/php]

No need to repeat the test twice.  Once for the command line and again for the while loop.

Hmmmm, come to think of it, wouldn't that have to be q.lower() = "q" to get around the dreaded capslock.  ;)

Grrrr, stop making me putter around in Python on UF.  I'll waste hours!  So fun to play in the language.

---

### Post by openuniverse on 2009-12-06
.

---

### Post by MadCow108 on 2009-12-06
I use a similar bash script.
if you have opera you can use opera buttons to link your script to a browser button.
Then you only have to click a button (or mouse gesture) instead of pasting a url.

---

### Post by openuniverse on 2009-12-06
.

---

### Post by Greyed on 2009-12-06
> **openuniverse said:**
> i was looking at it as i posted it, trying to think of a pythonesque (sorry mr. jones) way to avoid the double test, but i couldn't remember which version would be the conventional (thus not silly) one. it's while 1, eh? i can do that, but actually making a habit of it is another thing.

In the many, many... maaaaaaannnnnyyyyy discussions in trying to get BDFL to implement do..until or some similar construct the same thing comes up time and again.  Yes, while 1 is idiomatic but it is an intuitive idiom and the do..until loop really adds nothing that while 1..if:break doesn't do.  So, yeah, within the Python community if your intent is to enter an endless loop which might be broke out of at a later time, while 1 is the way to signal "here there be infinite dragons."  We'll know to bounce around for a break point.  :)

---

### Post by CptPicard on 2009-12-06
I am not really sure that an end-terminated loop is any more of a potential infinite loop than a top-terminated one is, and that it would as such deserve some warning-idiom of its own. do..until just lets you execute stuff at least once... IMO BDFL is wrong on this matter but who am I to complain :p

---

### Post by Greyed on 2009-12-06
Digressing but...  I disagree and find it surprising you would want the including of do..until given your penchant for reducing languages to their inner Lisp.  ;)

while and do..until are both just loops.  However while provides to be both top terminating or, with the idiomatic while 1, terminating anywhere below that.  do..until is the same except not explicitly top terminating, IE

```

do:
    if spam:
        break
    do_something_here()
until 1

```IE, they are the same thing in the end because of the inclusion of continue and break.  the main difference is that do..until doesn't clue you in at the top of the block which it might be.  You always have to read the entire block to find any break condition.  At the very least you have to go to the bottom of the block to see what condition you're testing for and, if infinite, go back to the top of the loop and read it.

While, with the idiomatically optional terminating condition at the top, lets you know in the first line if it is top terminating (while not spam) or terminating elsewhere in the loop (while 1).  Therefore while provides a method of performing do..until more compactly than do..until provides for performing a while.  That's even ignoring the whole mess of where the until is supposed to go as deindenting is the end of the code block.  Since both are functionally identical we should (and do) default to the more efficient of the two. 

Frankly, in my time programming Python, I have made more internally terminating while loops than top terminating.  I'm of the opinion that while should be scrapped.  do..until advocates kicked in the shins and both crowds told they get by with a single keyword, loop.

Top terminating loop:
```

loop: 
    if spam:
        break
    do_something()

```Bottom terminating loop:
```

loop: 
    do_something()
    if spam:
        break

```There, one word, functionality of while and do..until both retained, no idiom since we know when we see loop we just search for break in either case.  Talk about consistency!  Maybe in Python4000.  *cough*

Of course the CptPicard response to this is to point out that by reducing all cases of while to a generic loop keyword we're moving slightly closer to a slightly less half-assed implementation of lisp iterating over lists.  ;)

---

### Post by openuniverse on 2009-12-06
.

---

### Post by Greyed on 2009-12-06
> **openuniverse said:**
> i would bet there are **"**no workarounds**" **in lisp, and it makes more sense (it's so much more reasonable semantically) to have two basic loops than one loop and one workaround.

3.  We already have 2, while and for.  Condensing while cond and while 1 to a generic loop: makes sense since it really changes nothing.  As I pointed out while and do..until are the same side of the same coin, just from different mints.  For is a completely different entity.  Cramming that into a generic loop keyword would do no good since it would take several lines of Python code to reinvent the 1 keyword that is implemented efficiently in C.

SA in SABDFL?  Google sez Self-Appointed.  Though I've never heard GVR referred to as SABDFL, only BDFL.  I think there's some consensus on the appointment outside of his person.  ;)

---

### Post by CptPicard on 2009-12-06
Oh noes, I've been called on my secret *modus operandi* of seeing everything as a corner case of Lisp... :o

Interesting reasoning, Greyed. I guess I don't really mind an alternate structure in a language for some special case if it's useful (in this case, helps with an "execute at least once" case which seems to be common enough that people complain) as long as it is well-defined and -behaved and optional, and keeps the language consistent. The position of the "until" is an interesting consistency thing I haven't considered before, actually.

Your "loop" idea sounds interesting... initially it looked more like a BASIC line label-based loop that is just missing a "goto loop" at the end. Yes, it was Dijkstra I thought I heard rolling in his grave...

Of course in Lisp you can write a macro for any wild control structure you can dream of, so there this is again a complete non-issue.

---

### Post by Greyed on 2009-12-06
> **CptPicard said:**
> The position of the "until" is an interesting consistency thing I haven't considered before, actually.

Actually I think this was more the reason than anything.  Because the real noodle cooker isn't where to put the until, it is where to put the else.  ;)

[php]
x = 1
while x < 10:
    stuff()
    if not spam:
        break
    x = x + 1
else:
    other_stuff()
[/php]The above is valid.  The do..until of the while portion is simple, and we can argue about the until being on the same indent level as the block or the same level as the do.  But when you toss in the else it gets really bead-bangingly frustrating.

[php]
do:
until x < 10
else:
#or
do:
    until x < 10
else:
[/php]> Your "loop" idea sounds interesting... initially it looked more like a BASIC line label-based loop that is just missing a "goto loop" at the end. Yes, it was Dijkstra I thought I heard rolling in his grave...Hehe.  Although I think in this discussion I just saw why they don't do a loop keyword.  Else, again.  Else is invoked when the loop's condition is successfully met.  If we have a loop which, by definition, has no ending condition except for break we then either lose the functionality of else or we have to introduce a keyword other than break to end the loop "successfully".  Which puts us right into the do..until problem with do as "loop" and until the keyword to successfully end the loop.


> Of course in Lisp you can write a macro for any wild control structure you can dream of, so there this is again a complete non-issue.Zzzipit.  I still haven't gotten around to learning lisp.  All the parens make my wrists ache.  So I have to make do with the imperfect languages with which I am familiar.  ;)

Anyway, sorry, Openuniverse, for the slight derailment there.  Actually what you've posted is the basis of one of my favorite control structures in Python for basic CLI functionality.  I toss a couple of functions in a dict with their command words as keys and pull the user input through raw_input().  Something like this:

[php]
def spam():
    blahblahblah

def eggs():
    halbhalbhalb

def quit():
    baddabing

cmds = {"spam" : spam,
              "eggs" : eggs,
              "q" : quit }

while 1:
    incmd = raw_input('Commad: ')
    if incmd.lower() in cmds:
        cmds[incmd]()
    else:
        print("Come again?")
[/php]The real fun part is writing doc strings for each function then having a help command which pulls the functions from the cmds dict, reads their __doc__ string and presents that as the in program help menu.  :)

---

### Post by openuniverse on 2009-12-06
.

---


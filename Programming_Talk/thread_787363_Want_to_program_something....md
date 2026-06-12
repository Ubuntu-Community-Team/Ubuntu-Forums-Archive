---
title: "Want to program something..."
date: 2008-05-08
forum: Programming Talk
---

### Post by gkrules on 2008-05-08
I'm new to programming and i wanna try an experiment
next year im gonna take the SAT
wat i wanna program is a little application that will popup every 15-30min and show a word and definition
just something simple nothing really fancy or complicated
what i wanna know is 
1. what wud be the easiest language to do it in?
2. how would i go about doing it?
3. how do i make sure it works with ubuntu?
4. wud i somehow be able to get definitions directly from a website? like [http://www.merriam-webster.com/?](http://www.merriam-webster.com/?)

---

### Post by LaRoza on 2008-05-08
> **gkrules said:**
> I'm new to programming and i wanna try an experiment
next year im gonna take the SAT
wat i wanna program is a little application that will popup every 15-30min and show a word and definition
just something simple nothing really fancy or complicated
what i wanna know is 
1. what wud be the easiest language to do it in?
2. how would i go about doing it?
3. how do i make sure it works with ubuntu?
4. wud i somehow be able to get definitions directly from a website? like [http://www.merriam-webster.com/?](http://www.merriam-webster.com/?)

That would be simple. For me, if I were to do something like that, I would first have some sort of database of words and definitions. 

I would then create a Python program that takes a random word and its definitions and display it. I would have cron run it at the desired interval.

```

#!/usr/bin/python
import easygui

def getdefinition():
    #a simple function which would get the definition 
    #from the source. Exactly how would depend on the source.

easygui.msgbox(message=getdefinition(),title="SAT Prep")

```

easygui is a single file (see my wiki for where to get it if you are interested), it requires tkinter to be installed.

This would be equally trivial to write in Perl or Tcl.

It would be possible to get the definitions of words from a website, but that would require a bit more work. A local database or file would be best I think.

---

### Post by johnl on 2008-05-09
I think that you might be able to do this with even a simple bash script...

Make sure that you have installed the packages: dict zenity athena-jot

```

#!/bin/bash

# get the number of words in the dict file
COUNT=$(cat /usr/share/dict/words | wc -l)
# pick a random word from the file
WORD=$(cat -n /usr/share/dict/words | grep -w $(jot -r 1 1 $COUNT) | cut -f2)
# use dict program to lookup the definition online
DEF="$(dict $WORD)"

# display it in a window
echo "$DEF" | zenity --text-info --title "$WORD"

```

I would add a loop around the first three commands to loop while $DEF contains "Definition not found" as the words in the list don't always match up with the words in the online dictionary.

I pulled the first two lines from some blog, can't remember where exactly it was, but it's a nifty trick, so thanks :)

---

### Post by xelapond on 2008-05-09
If you were to do it in Python(Which I highly recommend) You could use the included pynotify library.  That will display a notification at the bottom right, like when you remove a device without ejecting it.  It would be better because its a little less intrusive, and does not force you to dismiss it.

---

### Post by johnl on 2008-05-09
> **xelapond said:**
> If you were to do it in Python(Which I highly recommend) You could use the included pynotify library.  That will display a notification at the bottom right, like when you remove a device without ejecting it.  It would be better because its a little less intrusive, and does not force you to dismiss it.

I think you can even add a --timeout parameter to the zenity call to cause the window to disappear after a certain amount of time.
With that said, I totally agree -- you could definitely get a lot more functionality if you were to write it in a 'real' language like python.

---

### Post by evymetal on 2008-05-09
> **xelapond said:**
> You could use the included pynotify library...

Thank you - I hadn't ever come across that - that's going into my bookmarks.

---

### Post by gkrules on 2008-05-09
oo i see
it seems pretty easy
ill give it a go tonight

---

### Post by solarwind on 2008-05-09
> **gkrules said:**
> oo i see
it seems pretty easy
ill give it a go tonight

Yes, I would say use Python and use Pynotify. You have half the program done in a few lines. The rest of the program comes from getting the word from somewhere itself. You could try to pull it out of an online dictionary.

How old are you by the way?

Check out [http://www.freerice.com/](http://www.freerice.com/), you will learn a lot of words from it ;)

---

### Post by gkrules on 2008-05-09
im 16
yea i jus started programming it

and freerice is a good idea

---

### Post by solarwind on 2008-05-09
> **gkrules said:**
> im 16
yea i jus started programming it

and freerice is a good idea

I'm 17, I could help you with it, sounds like an interesting project. I'm interested in it. The most important thing here is getting a database of words. You got MSN? What's popular over where you live? Wanna come to my IRC channel? We can talk there...

---

### Post by gkrules on 2008-05-10
nah i dont hav msn...i use AIM
and wats ur irc?


i messed up the code and cant seem to find wat i did wrong so im gonna have to start over

---

### Post by solarwind on 2008-05-10
> **gkrules said:**
> nah i dont hav msn...i use AIM
and wats ur irc?


i messed up the code and cant seem to find wat i did wrong so im gonna have to start over



I'll PM you.

---


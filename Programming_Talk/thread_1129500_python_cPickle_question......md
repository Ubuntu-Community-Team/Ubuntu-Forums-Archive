---
title: "python cPickle question....."
date: 2009-04-18
forum: Programming Talk
---

### Post by originalsynthesis on 2009-04-18
hey all, just another wannabe programmer with a question. I'm writing a high score thinger for a simple game i made using cPickle as the data medium.  I've already done this using text files, and shelves, and i just want to do it every way i can to get a good feel for the stuff. 
Sooo, i need to know what i can use to test if a list of scores is already in the cP file (that doesn't necessarily exist yet) the code looks like :

```
prompt = ask_yes_no('do you wish to save your score?(y or n)')

if prompt == ('y'):
    name = raw_input("Enter a name, bigshot!")
    sentry = (name,score)
    load = open("highscores.dat","w+")
    if #what_variable?# in load:
        sdata = cPickle.load(sdata)
        sdata.append(sentry)
        cPickle.dump(sdata, load)
        load.close()
        print"Well Jim, I'd say that went pretty well..."
    else:
        sdata = [entry]
        cPickle.dump(sdata, load)
        load.close()
        print "Well Jim, I'd say that went pretty well..."
```

The main thing is that the data should not have to exist yet, so i need to pick a generic variable or condition to test for so Py knows which save method to use (adding an entry to a prev list, or making a new one which will be added to later)  

thanks!

---

### Post by Pollox on 2009-04-22
I don't know a lot about python, but seeing as this question has been sitting a few days without a response, here goes.

It seems to me you have a list of scores.  You want to add another score to it.  And you might already have some scores stored in a file.  So, initialize the list with sdata = list().  Then check if the file exists, and if it does, set sdata = the unpickled data from the file.  Then append on your score.  This only leaves you with the problem of checking if the file exists, which a quick google search seems to indicate that there are a few ways to check that.  I hope that helps.

---

### Post by unutbu on 2009-04-22
This is the main problem:

[PHP]sdata = cPickle.load(sdata)[/PHP]

cPickle.load() expects a file handle, not sdata.

The other thing I suggest is use a try...except block instead of an if...else block.

[PHP]import cPickle
prompt = ask_yes_no('do you wish to save your score?(y or n) ')
if prompt.lower().startswith('y'):
    name = raw_input("Enter a name, bigshot! ")
    sentry = (name,score)
    scorefile="highscores.dat"
    try:
        sdata = cPickle.load(file(scorefile))
        sdata.append(sentry)
    except IOError:
        sdata = [sentry]                         # not [entry] 
    cPickle.dump(sdata,file(scorefile,'w'))  # You don't have to close file(...)
                                             # python closes it for you since
                                             # there are no references to it
    print "Well Jim, I'd say that went pretty well..."   # Pull out of the if...else...
                                                         # since it is printed in 
                                                         # either case[/PHP]

---

### Post by originalsynthesis on 2009-04-30
First I'd like to say sorry for not explaining things a little better. That's probably why no one responded, that and it probably seems like a boring homework assignment. (it is, sort of, i'm teaching myself from a book...) I got a bit frustrated and just slapped together a post real quick. So thank you guys for responding, I got some good food for thought out of your posts.

unutbu:

The try...except block is perfect here, i had not really done much with those before. also the syntax you used for writing to the pickle files is new to me. 

```
sdata = cPickle.load(file(scorefile)) 
```

the load(file(x)) definitely simplifies things. Also, thought I had to specify "r" for reading so i could extract the list out of it.  

Also, you mentioned that i don't have to close the file in this case because that is done automatically. So, when would i need to use close()? Should that lead me to believe that I never technically need to close a file, even if it is referenced again? I figure if it does that, even if I reference it say, two or three more times down in the code, Python would know when the file was no longer referenced and it would close it.

---

### Post by unutbu on 2009-04-30
file(x) opens x in read mode by default.
see help(file) for more details on its calling signature.

file() returns an instance of class file.
open() is a builtin function which returns an instance of class file.

As far as I can tell, the resulting instance of class file is the same. (They have the same dir's).

Here are some situations when you might want to use close():
[list]
[*]You want to reopen the file in a different mode
[*]On Ubuntu, by default, (due to the shell, not Python), you can open a max of 1024 files simultaneously. You should use close() to avoid this limit.
[/list]

In the idiom
```

cPickle.load(file(scorefile))
```

file(scorefile) returns an unnamed file handle. It is fed to cPickle.load(). Once cPickle.load() is done, there is no other reference to file(scorefile). So Python knows it is free to garbage collect file(scorefile). Python kindly closes the file handle for you in this case.

---


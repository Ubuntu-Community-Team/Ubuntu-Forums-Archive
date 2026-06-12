---
title: "Run python function each minute"
date: 2010-07-18
forum: Programming Talk
---

### Post by aktiwers on 2010-07-18
Hey mates,

I'm trying to run my small python program each minute.
But it seams to give me some kind of memory leak doing it this way:


[php]
def start():
    while True:
            Check(hosts)
            time.sleep(60)

start()
[/php]

Check() is the one I want to run every 60 secs. Any ideas?

---

### Post by Bachstelze on 2010-07-18
Run it in a cron job?

---

### Post by aktiwers on 2010-07-18
Thanks for your suggestion Bachstelze.
I thought about that, but running it without cron would be nice.

Is there any better ways doing this then my method?

---

### Post by Bachstelze on 2010-07-18
That's how I would do it, then, what makes you think it memory leaks?

---

### Post by aktiwers on 2010-07-18
> **Bachstelze said:**
> That's how I would do it, then, what makes you think it memory leaks?

Because memory consumption keeps going up :)
Then it must be my check() function that memory leaks.. 

Okay this is how it looks:

[php]
import urllib
import re
import time

hosts = [
    'www.google.com', 
    'www.Fail22222.com' # Fails 
    ]


def Check(hosts):
    for hosts in hosts:
        try:
            f = urllib.urlopen("http://"+hosts).read()
            find = re.findall("word" ,f)
             find2 = re.findall("DOCTYPE" ,f)
            print hosts
            try:
            if find[0] == "word":
                 print "Found word"       
            genPHPuP(hosts)
            except IndexError:
            try:
                if find2[0] == "DOCTYPE":
                print "Found DOCTYPE"
                genPHPuP(hosts)
            except IndexError:
                    print "Page does not contain DOCTYPE or word"
                genPHPwarn(hosts)
        except IOError:
            print hosts
            print "Page does not contain DOCTYPE or word! Server is down!"
            genPHPdown(hosts)



def genPHPuP(hosts):
       
    try:
        filename = hosts+".php"
        print "PHPuP: Writing file: %s" % filename
        file = open(filename, 'w')
        file.write("<img src=pics/greenV.jpg>" )
        file.close()
    except IOError:
        print "PHPup: Couldn't write to file %s" % filename



def genPHPdown(hosts):

    try:
        filename = hosts+".php"
        print "PHPdown: Writing file: %s" % filename
        file = open(filename, 'w')
        file.write("<img src=pics/redX.png>" )
        file.close()
    except IOError:
        print "PHPdown: Couldn't write to file %s" % filename



def genPHPwarn(hosts):

    try:
        filename = hosts+".php"
        print "PHPWarn: Writing file: %s" % filename
        file = open(filename, 'w')
        file.write("<img src=pics/warn.png>" )
        file.close()
    except IOError:
        print "PHPWarn: Couldn't write to file %s" % filename



# Starts Check() every 60 sec
def start():
    while True:
            Check(hosts)
            time.sleep(60)

start()
[/php]What I am trying to do is to go through the lists of hosts, check them for 2 different words, and write to a file if it finds the word, does not find the word or if the server is down.

Can you spot any leaks in that? I'm still learning Python.

Thanks a lot!

---

### Post by aktiwers on 2010-07-18
No one? :)

---

### Post by soltanis on 2010-07-18
Python manages its own memory. Memory usage may go up, but this is a consequence of you not having control over how Python decides to allocate/deallocate memory for things, the point being that you shouldn't worry about it.

EDIT:

But as a manner of style, I wouldn't do this:

[php]
for hosts in hosts:
[/php]

While it works, it's confusing. My personal idiom in these situations is to do this:

[php]
for host in hosts:
[/php]

Which (at least to me) is clearer.

---

### Post by aktiwers on 2010-07-18
Thanks a lot Soltanis!

I will fix that :) 

Actually after letting the script run all day, memory usage seams to increase slower and slower, but still it is growing. after running for about 8 hours it was taking up 10,7mb.

Do you think it would stall at some point or just keep going up? Since my plan is to have the script running 24/7.

---

### Post by Can+~ on 2010-07-18
[PHP]f = urllib.urlopen("http://"+hosts).read()[/PHP]

Do you close that file-like object, somewhere? I don't know if this is the responsible for the memory consumption, but you should consider it, nonetheless.

[PHP]def genPHPuP(hosts):
    pass

def genPHPdown(hosts):
    pass

def genPHPwarn(hosts):
    pass[/PHP]

This three functions are exactly the same, except for a few variable elements, I suggest merging them in one. (For readability)

[PHP]print "Page does not contain DOCTYPE or word! Server is down!"[/PHP]

Have you thought on just "pinging" the server?

> Do you think it would stall at some point or just keep going up? Since my plan is to have the script running 24/7.

That's an undecidable problem. But I would assume that it will grow indefinitely (as there are no clues that suggest otherwise). Try switching to python3 or newer, in case it's an old bug.

---

### Post by aktiwers on 2010-07-18
I really appreciate your inputs! Thanks alot.

The reason I did not choose to ping the sites, is that pinging will only show if the server is online, but not if the specific page is up.

I actually started out trying to write those together in one function, but my newbieness made me lazy! In the end I want to rewrite the whole thing and somehow make it check if the file it is writing to, already contains the info it is writing, and only write when the file need to be updated. Right now it writes everytime.

And you are perfectly correct, I don't close that thing anywhere.. Let me try that and see what happends.

---

### Post by aktiwers on 2010-07-18
I just rewrote the thing to Python 3.x and the memory leak is gone!
I guess this was a bug in python 2.x.

Thanks for all the help :)

Btw:
closing 
[php]
f = urllib.urlopen("http://"+hosts).read()  [/php]
Didnt work..

---


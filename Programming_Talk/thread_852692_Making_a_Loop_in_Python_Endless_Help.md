---
title: "Making a Loop in Python Endless: Help?"
date: 2008-07-07
forum: Programming Talk
---

### Post by mtgmutton on 2008-07-07
In Python 2.5, I'm trying to write a program that will download a file from a url that I already know. I would like to be able to run it and leave it alone while it keeps running indefinitely (because of the "while" loop) until the file is posted on the server. Problem being: I can't seem to get it to run that way. Any ideas? The code is placed below (although I can't seem to get it to put in four spaces before the "f()" in the while loop:()

import urllib

f = urllib.urlopen("FileURL")
while "FileURL" is 'false':
(imagine 4 spaces here)f()

g = f.read()
file = open("FileLocation", "w")
file.write(g)
file.close()

---

### Post by Wybiral on 2008-07-07
Assuming that the site isn't there, "openurl" will throw an IOError exception when it tries to read it. You can catch this, sleep for a second, then try again, breaking the "while" if the exception isn't raised.

Something like this:
```

import time
import urllib

url = "your site here"
out_file = "temp.txt"

while True:
    try:
        f = urllib.urlopen(url)
        break
    except IOError:
        time.sleep(1)

out = open(out_file, "w")
out.write(f.read())
out.close()
print "Done!"

```

But, if the page IS there, and you're just waiting for it to not be empty you can avoid the "try/except" and just do the read in the loop and break if it isn't empty.

EDIT:

BTW, you can post sourcecode using the "[ code ]" tags.

---

### Post by ghostdog74 on 2008-07-07
use code tags when posting code.
try this pseudocode
```

while 1:
    try:
     f=urllib2.urlopen(URL)
    except Exception,e:
     print e
    else:      
      open("file","a").write(f.read())


```

---

### Post by mtgmutton on 2008-07-07
Wow, thanks for the quick replies!

I'm not sure if the page is there... It's just a bunch of links to files... I guess that means the page is there? because the page is always there, it's just the files that change...:confused:

Anyway, I tried mixing the code... No errors came up in the IDLE check module... Tell me what you think?

```
import time
import urllib

f = urllib.urlopen("url")
while 1:
    try:
        f()
    except Exception,e:
        print e
        time.sleep(1)
    else:
        g = f.read()
        file = open("file", "w")
        file.write(g)
        file.close()
print "Done!"
```

Now when I run the module, every second it says "addinfourl has no instance call method". I'm guessing this means it's working because the file isn't on the webpage yet....?

---

### Post by ghostdog74 on 2008-07-07
> **mtgmutton said:**
> Wow, thanks for the quick replies!

I'm not sure if the page is there... It's just a bunch of links to files... I guess that means the page is there? because the page is always there, it's just the files that change...:confused:

Anyway, I tried mixing the code... No errors came up in the IDLE check module... Tell me what you think?

```
import time
import urllib

f = urllib.urlopen("url")
while 1:
    try:
        f()  <<<<------ f  is not a function. put f = urllib.urlopen("url") here. And what is "url"?? you should put the variable that stores the actual url here.
    except Exception,e:
        print e
        time.sleep(1)
    else:
        g = f.read()
        file = open("file", "w") <<<<--- short form: open("file","w").write(g). 
        file.write(g)
        file.close()
print "Done!" <<<<---- you don't have break in your while loop, so you can't get here.

```

Now when I run the module, every second it says "addinfourl has no instance call method". I'm guessing this means it's working because the file isn't on the webpage yet....?


I would suggest not to jump ahead of yourself and learn the basics of Python first. Read the tutorials and library references at the Python doc site. (see my sig)

---

### Post by mtgmutton on 2008-07-07
Well, I did read Python For Dummies... I know that doesn't make me an expert, but it did help. Where should I put the "break" in my while block? Doesn't that make the program stop?

New Code:

```
import time
import urllib

while 1:
    try:
        f = urllib.urlopen("url")
    except Exception,e:
        print e
        time.sleep(1)
    else:
        g = f.read()
        file = open("file", "w")
        file.write(g)
        file.close()
print "Done!"
```

---

### Post by ghostdog74 on 2008-07-07
> **mtgmutton said:**
> Well, I did read Python For Dummies... I know that doesn't make me an expert, but it did help. Is there something wrong with the code?

Read the Python tutorial. I have shown you what's wrong in the code. see the <<<---- arrows

---

### Post by mtgmutton on 2008-07-07
Oh, OK. The book didn't explain it very well :(

NOW let's see.... I can't seem to find a place where it needs a "break"... Did you have a particular spot in mind?

---

### Post by pmasiar on 2008-07-07
> **mtgmutton said:**
> Well, I did read Python For Dummies... I know that doesn't make me an expert, but it did help. 

Python for Dummies is decent book for absolute beginners, but does not build on that, I am disappointed with it.

CHeck my wiki: [http://learnpython.pbwiki.com/PythonBooks](http://learnpython.pbwiki.com/PythonBooks) . I highly recommend "Python for Absolute Beginners in 3 afternoons"

---

### Post by ghostdog74 on 2008-07-07
> **mtgmutton said:**
> Oh, OK. The book didn't explain it very well :(

NOW let's see.... I can't seem to find a place where it needs a "break"... Did you have a particular spot in mind?

I will let you have a go at it yourself, after you read [this](http://docs.python.org/tut/node6.html). See how the break is used. then put it where ever you need it to be in your logic. Besides break and depending on what your purpose is, exit/return (from function) can also be used.

---

### Post by mtgmutton on 2008-07-07
I am definitely reading that book :)

And, now that I've read that section... How about this break?

```
import time
import urllib

while 1:
    try:
        f = urllib.urlopen("url")
        if "url" == 'true':
            break
    except Exception,e:
        print e
        time.sleep(1)
g = f.read()
file = open("file", "w")
file.write(g)
file.close()
print "Done!"
```

Does an "if" statement absolutely require an "else" statement?

---

### Post by Wybiral on 2008-07-07
HINT: "url" == 'true' is comparing two strings

---

### Post by mtgmutton on 2008-07-07
Ooops! Would this work?

```
if "url":
    break
```

---

### Post by ghostdog74 on 2008-07-07
> **mtgmutton said:**
> Ooops! Would this work?

```
if "url":
    break
```

why are you putting this inside the while loop? the try:except already verifies whether its ok or not.

---

### Post by mtgmutton on 2008-07-07
ok i have to sleep... be back in like 10-11 hrs...

---

### Post by Wybiral on 2008-07-08
> **mtgmutton said:**
> Ooops! Would this work?

```
if "url":
    break
```

No, now you're checking a string for boolean value. Non-empty strings always return true :)

---

### Post by estyles on 2008-07-08
> **mtgmutton said:**
> Ooops! Would this work?

```
if "url":
    break
```

a) What, exactly, are you trying to do with the string?  if "*string*" doesn't make a whole lot of sense.

b) They're telling you to put in a break so that your code will terminate.  i.e. you want a condition where your code will quit at some point.  break will jump you out of your loop.  If you're not interested in the code ever terminating (I suppose you'll just force quit it at some point?), then a "while TRUE" loop will do the job without using break.  It's good coding practice to not create infinite loops, especially not on purpose.

---

### Post by mtgmutton on 2008-07-08
I am back, and after reading some of the other comments made while I was sleeping, I have decided to put the "break" here

```
import time
import urllib

while 1:
    try:
        f = urllib.urlopen("url")
        break
    except Exception,e:
        print e
        time.sleep(3000)
g = f.read()
file = open("file", "w")
file.write(g)
file.close()
print "Done!"
```

---

### Post by mtgmutton on 2008-07-08
OK never mind... that just ignores the exception part. I don't think the code needs a break... It will just keep waiting and starting over until there is no exception (because the page was created), right?

---

### Post by WW on 2008-07-08
Actually, that code (with the break) worked for me.  If I leave the argument as "url", it repeatedly fails and tries again (as it should).  If I change the argument to "http://www.google.com", it successfully puts the HTML of the google home page in the file called "file", and prints "Done!".  The only change I made was to decrease the argument of sleep() from 3000 to 3 (those are seconds, you know :) ).

---

### Post by Wybiral on 2008-07-08
> **mtgmutton said:**
> OK never mind... that just ignores the exception part. I don't think the code needs a break... It will just keep waiting and starting over until there is no exception (because the page was created), right?

No, it does need a break to exit the loop. The last code you posted looks fine. My advice would be to refresh on some of the basics, like types, conditions, and exceptions before starting a project like this.

---

### Post by mtgmutton on 2008-07-08
BUT! if the "break" makes it exit the loop, it won't print the IOError, and it won't repeat, making my little program not run like I want it to. :( Can I switch it like this so that it will repeat unless there isn't an exception?

```
import time
import urllib

while 1:
    try:
        f = urllib.urlopen("url")
        except Exception, e:
            print e
            time.sleep(300)
        break
g = f.read()
file = open("url", "w")
file.write(g)
file.close()
print "Done!"
```

---

### Post by Wybiral on 2008-07-08
> **mtgmutton said:**
> BUT! if the "break" makes it exit the loop, it won't print the IOError, and it won't repeat, making my little program not run like I want it to. :(

No, it wont. Because the statement before it is the one raising the exception, the break will never be reached if an exception is raised because the program flow will be moved to the "except" case. If there is no exception, THEN it will reach the break. Test it.

---

### Post by mtgmutton on 2008-07-08
OK now I understand the reasoning for the break point :) And I did test it. On the nonexistent page I'm trying to get it to check for. It just checks and follows the final command, printing "done!". Grrrrrrrr...:mad:

---

### Post by Wybiral on 2008-07-08
> **mtgmutton said:**
> OK now I understand the reasoning for the break point :) And I did test it. On the nonexistent page I'm trying to get it to check for. It just checks and follows the final command, printing "done!". Grrrrrrrr...:mad:

OK, does the page actually exist? The only way it throws that exception is if there is no page there. If the page is empty, or just doesn't contain the text you want yet, you will need to check the results of reading to determine when to break the loop.

Also, by "exists" I also mean if there's a "page not found" page that the server serves in place of non-existent pages too.

---

### Post by mtgmutton on 2008-07-08
Well, I decided to find out... So I typed in the url of the file-to-be and it brought me to some random page which froze firefox. I'm not sure what this means...:confused: I tried it again, with the same result. What should I do about that? And what do you mean by "throw the exception"?

---

### Post by Wybiral on 2008-07-08
> **mtgmutton said:**
> Well, I decided to find out... So I typed in the url of the file-to-be and it brought me to some random page which froze firefox. I'm not sure what this means...:confused: I tried it again, with the same result. What should I do about that? And what do you mean by "throw the exception"?

"openurl" raises/throws an exception if the url isn't found (such is the case when a webpage doesn't exist). But if it reads anything... Even an empty page... It will not throw the exception.

So there is a page already? If so, then this try/except model isn't going to help you, you need to parse the results and determine if it contains the data you want yet.

---

### Post by ghostdog74 on 2008-07-08
> **mtgmutton said:**
> Well, I decided to find out... So I typed in the url of the file-to-be and it brought me to some random page which froze firefox. I'm not sure what this means...:confused: I tried it again, with the same result. What should I do about that? And what do you mean by "throw the exception"?

what has firefox got to do with your script?? If you don't know what is "throw exception" , i think you really need to read more and understand more about Python/(or programming) basics.

---

### Post by WW on 2008-07-08
> **mtgmutton said:**
> OK now I understand the reasoning for the break point :) And I did test it. On the nonexistent page I'm trying to get it to check for. It just checks and follows the final command, printing "done!". Grrrrrrrr...:mad:

If your URL is [HTTP://.](HTTP://.).., then openurl may not be doing what you expect.  If the attempt to access the file results in a 404 error, you might get a valid connection, but the contents of the file will contain the HTML code that is spit out by the server when a 404 occurs. Or the server might just kick you back to the home page. I think the behavior depends on the server.

For example, the following surely don't exist, but they do not result in an exception:
> 
   [http://www.google.com/does_not_exist](http://www.google.com/does_not_exist)
   [http://ubuntuforums.org/does_not_exist](http://ubuntuforums.org/does_not_exist)
   [http://www.python.org/does_not_exist](http://www.python.org/does_not_exist)

and even
> 
   [http://x.y.org/does_not_exist](http://x.y.org/does_not_exist)


On the other hand, **[http://blah/does_not_exist](http://blah/does_not_exist)** does cause an exception.


Take a look at the contents of "file" to see what the server is returning.

---

### Post by mtgmutton on 2008-07-08
In response to Ghostdog74: Firefox is my web browser... That's how I go to web pages. Wybiral asked me if the page existed, so I decided to find out by typing in the url. That's what it has to do with my code. And I apologize for only reading one book that never used that term. This is my first piece of real code... I didn't know I had to be an expert to do something so simple... Sorry if the basics I know aren't good enough. :(

---

### Post by pmasiar on 2008-07-08
> **mtgmutton said:**
>  And what do you mean by "throw the exception"?

You are out of your depth. Try to learn basic before taking on more advanced topics. You are wasting your time and time of people who are helping you.

Solve 20 tasks in Project Euler, then come back to this one.

---

### Post by estyles on 2008-07-08
I wouldn't worry too much about "wasting the time of people that are trying to help", man.  If they had something better to do, they would do it.  Me personally, I have a little bit of time to waste, but not enough to go into detail on programming, so my responses have been somewhat general.  The other people that have been posting specific python help have either way more python knowledge or more time to waste.

But it's true that you should try something simpler until you are a more accomplished programmer.  "Something so simple" would be something like printing "hello world" or asking for 2 numbers and adding them together.  Put it this way - if you're having enough trouble with a program to ask about it on a forum, and it's not something where it's just a single line tripping you up because you think it should work and it doesn't - well, then you may be trying something too hard.

If you must do something web-based, start with a program that asks for a string-input and then tries to open a web-page with the name of the input by calling firefox.  If you get that working easily enough, then try to interpret the input by adding "http://" or ".com" if necessary.  Then, try to find out if the page exists by looking for a 404 page coming back.  Then once you get that working, try to interpret misspellings by searching for a similar page if a 404 comes back.

The best way to do a beginner program is start with something extremely simple.  First step might be just to ask for a string and then echo it back to the user.  Then, as you get the simple things working, add to it, little by little, and you'll learn more and more about python as you go.

I hate to be a jerk, but it's true - if you don't know what "throw and exception" means, or "break", or that comparing a string to a boolean isn't going to work very well - then you've probably got some work to do before you're going to write a program that does something useful.  Don't ask how to fly if you're not entirely sure how to crawl.

But don't let this discourage you.  Once you get all of the basic concepts down, you'll be able to do some really cool things in python.  And once you know python - it won't be nearly as difficult to learn other languages as you need them, java, c++, god-forbid VBA - the syntax is different, but the concepts are very similar.  And trust me, knowing the concepts is very important.  How popular do you think python was 5 years ago?

Anyway, keep on trucking, man.  :guitar:

---

### Post by pmasiar on 2008-07-09
> **estyles said:**
> I hate to be a jerk, but it's true 

Since when saying truth counts as being jerk? Just the opposite: not saying truth does not show where challenges are, and where growth is needed and possible. Not saying the truth let's him to continue making fool of himself, and later he could be ashamed of such posts. Is better to avoid it, no?

And my concern is also a little about "forum level" - will other posters want to post more sophisticated questions if most posts will be as above?

I did not grow in USA, and find this "feel good" education ("all our children are above average") ridiculous. For me, it's much simpler just ignore poster than saying what to do, how to improve.

I am not saying "shut beginners out of forum", no such thing. I am saying let's beginners help to learn fundamentals first, don't fool them that they can skip over basic. Point them where fundamentals are, so they can grow competent programmers if they want to.

That's why I maintain wiki for Python beginners.

Maybe I am just too old school, and too old :-)  Feel free to ignore me, it it will help your self-satisfaction.

---

### Post by estyles on 2008-07-09
> **pmasiar said:**
> Maybe I am just too old school, and too old :-)  Feel free to ignore me, it it will help your self-satisfaction.

Not trying to ignore you, or tell the OP to ignore you, but I do think you were a little harsh.  Wasn't there ever a time when you were learning to program or learning to use an OS when you jumped in a little too deep?  More or less, I was trying to expand on what you said without being as harsh - I don't want the OP to be scared off of programming (or Linux) for good!

---

### Post by pmasiar on 2008-07-09
When I was learning programming (on punchcards :-) ) you were lucky to get three runs of your code per week (including syntax errors). So you better think not only twice before another run: you had time to think twenty times before jumping too deep...

---


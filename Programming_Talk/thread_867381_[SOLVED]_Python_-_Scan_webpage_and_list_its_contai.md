---
title: "[SOLVED] Python - Scan webpage and list its containing links (urls)"
date: 2008-07-22
forum: Programming Talk
---

### Post by aktiwers on 2008-07-22
I am trying to learn Python and already created my first GUI app.

Now I want to try something a little bigger, and therefore I have a small question.

Could anyone help me or point me to a place where I can read more about how to use python to scan webpages for URLs?

What I want to do is to input an URL and then create a program that scans this url and list the links (urls) on that particular site. I have searched google but not found anything yet..

any pointers or help would be very nice :)

---

### Post by aktiwers on 2008-07-22
Found it here:
[http://www.java2s.com/Code/Python/Network/URLopenandread.htm](http://www.java2s.com/Code/Python/Network/URLopenandread.htm)

---

### Post by ghostdog74 on 2008-07-22
urllib, urllib2

---

### Post by Torajima on 2008-07-22
Might be a better way, but here's how I got the links:

import urllib                                                                                                         
mypath = "http://ubuntuforums.org"                                                                                    
mylines = urllib.urlopen(mypath).readlines()                                                                          
for item in mylines:                                                                                                 
    if "http://" in item:                                                                                             
        print item[item.index("http://"):]

---

### Post by aktiwers on 2008-07-22
> **Torajima said:**
> Might be a better way, but here's how I got the links:

import urllib                                                                                                         
mypath = "http://ubuntuforums.org"                                                                                    
mylines = urllib.urlopen(mypath).readlines()                                                                          
for item in mylines:                                                                                                 
    if "http://" in item:                                                                                             
        print item[item.index("http://"):]

Sorry I am a beginner but that looks like something I want to do. But it does not run?

I get an error in the "if" statement.
> IndentationError: expected an indented bloc

---

### Post by loell on 2008-07-22
it should be

```

if "http://" in item:
    print item[item.index("http://"):]



```

---

### Post by aktiwers on 2008-07-22
Still get the same thing:
> File "ap.py", line 6
    if "http://" in item:
     ^
IndentationError: expected an indented block


---

### Post by loell on 2008-07-22
oh sorry,

```


for item in mylines:
    if "http://" in item:
        print item[item.index("http://"):]


```

---

### Post by aktiwers on 2008-07-22
> **loell said:**
> oh sorry,

```


for item in mylines:
    if "http://" in item:
        print item[item.index("http://"):]


```


Thanks a lot! Worked great! 
:guitar:

---

### Post by aktiwers on 2008-07-22
One last thing..  Say I want it to search for .extension"
How do I go about that? then it will be ".extention"" and I get syntax error :(

Sorry if this is a very noobish question..

---

### Post by pmasiar on 2008-07-22
in strings, begin/end characters are special, but you can use '...' or "..." for single lines text constants, and """...""" or '''...''' for multilines, and r"..." for "raw" string (see docs).

Simple options:
[php]
# if you need ' or ", use the other one as begin/end:
'string with " ' 
"string with ' "
# use multiline string markers: 
"""string with both " and ' """
[/php]

You just need to force yourself read docs once to see what is possible. See also wiki in my sig for more Python links for beginners.

---

### Post by ghostdog74 on 2008-07-22
you can use endswith(). 
I suggest you read more on Python. See my sig for python docs.

---

### Post by aktiwers on 2008-07-22
Thanks a lot guys!
I also found this
[http://docs.python.org/ref/strings.html](http://docs.python.org/ref/strings.html)

---

### Post by nanotube on 2008-07-23
> **Torajima said:**
> Might be a better way, but here's how I got the links:

import urllib                                                                                                         
mypath = "http://ubuntuforums.org"                                                                                    
mylines = urllib.urlopen(mypath).readlines()                                                                          
for item in mylines:                                                                                                 
    if "http://" in item:                                                                                             
        print item[item.index("http://"):]

you are missing out on /at least/ the following:
all the relative links (i.e., a href="stuff.html")
links to other protocols (i.e. a href="ftp://server.com/")
variant capitalization (i.e. a href="HTTP://blabla.com")

at the very least, you'd do better to scan for "a href" rather than "http://".

and at best, use a prebuilt html parser, like beautifulsoup ([http://crummy.com/software/BeautifulSoup](http://crummy.com/software/BeautifulSoup))

all the special and corner cases have been taken care of. all you have to do is put the webpage through the parser, and then tell it "give me all the links", and there they are.

in other words, use the right tool for the job. :)

---

### Post by aktiwers on 2008-07-23
Thanks for the reply. The reason I want to make this is more because I know I website with a lot of links ending on .mp3, so I simply replaced the http:// with mp3.

But I have one more newbie question. I am trying to make this into a function I can call. Like this:

```
 def search():    
        word = Entry.get(self.aar)
        path = "http://skreemr.com/results.jsp?q="+word+"&l=10&s=200"
        mylines = urllib.urlopen(path).readlines()

        i = ".mp3\""
    for item in mylines:
        if i in item:
            print item[item.index(""):]
```this gives me a syntax error. Is there different rules when creating functions?

Thanks a lot and sorry for my newbieness :)

---

### Post by loell on 2008-07-23
```
 def search():    
        word = Entry.get(self.aar)
        path = "http://skreemr.com/results.jsp?q="+word+"&l=10&s=200"
        mylines = urllib.urlopen(path).readlines()

        i = ".mp3\""
        for item in mylines:
            if i in item:
               print item[item.index(""):]
```

 you'll get used to the indentation rules in no time. 
:biggrin:

---

### Post by aktiwers on 2008-07-23
Wow thanks! Man you are right, I really don't understand indentation rules.. have a link?
Is this just a matter of how many times I hit <tab> for each line of code and so on? We had nothing like this in Java :D

---

### Post by LaRoza on 2008-07-23
> **aktiwers said:**
> Wow thanks! Man you are right, I really don't understand indentation rules.. have a link?

Just indend the way you normally do...unless you are one of those people who don't indent...

Each block must be indented and each subblock, four spaces is the norm. 

So, for a class, with a method, with a loop:

```

class LaRoza:
    def assimilate():
        while True:
            assimilate()
        return Resistance

```

As you can see, it follows the same indentation schemes that should be used in Java and most other languages, just without braces. Also, I realise the code doesn't make sense.

---

### Post by aktiwers on 2008-07-23
Thanks LaRoza,

I don't really have that much experience with coding in general yet, but in Java I just "made it look pretty".

I better get used to this way of doing it :)

I know the code does not make much sense right now, I am basically just practicing the syntax and hopefully I will be able to end up with a program where you can search SkreemR and get the results(at least from page one) listed inside a Tkinter GUI. 

I guess later I will have to separate the Entry.get() from the actual listing of urls, to get the listings to show correct.

---

### Post by mssever on 2008-07-23
> **LaRoza said:**
> ```

class LaRoza:
    def assimilate():
        while True:
            assimilate()
        return Resistance

```[...]
Also, I realise the code doesn't make sense.
It makes perfect sense if resistance is indeed futile, since nobody even gets an opportunity to resist. Of course, when you smash the stack from recursively assimilating too many people, resistance will be unnecessary. :) So on second thought, this code would defeat your plans to take over the world.
> **aktiwers said:**
> I don't really have that much experience with coding in general yet, but in Java I just "made it look pretty".

I better get used to this way of doing it :)
One thing Python will force you to do is indent your code like you should in many languages, including Java.

---

### Post by pmasiar on 2008-07-23
Adding spaces to reveal code structure is common practice, and Python just makes this practice a part of syntax (so program has to have proper structure visually to be correct, and all programmers use the same standard so can read each other's code).

Read also [Myths about Indentation](http://www.secnetix.de/~olli/Python/block_indentation.hawk)

---

### Post by LaRoza on 2008-07-23
> **mssever said:**
> So on second thought, this code would defeat your plans to take over the world.


Petty minds... I want the Universe.

---


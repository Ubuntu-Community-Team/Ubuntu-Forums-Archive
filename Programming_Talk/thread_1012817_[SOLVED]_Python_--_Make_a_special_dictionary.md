---
title: "[SOLVED] Python -- Make a special dictionary"
date: 2008-12-16
forum: Programming Talk
---

### Post by robz0rz on 2008-12-16
Hello all.

I'm trying to create something here, but I don't know enough python to accomplish this. Could someone please tell me how to do this, or which python libraries I need to get forward?


Let's say I have a folder icons/.
```
rob@rob-thinkpad:~ $ ls icons/
foo.16.png      bar.icon
foo.22.png      bar.svg
foo.32.png      baz.16.png
foo.icon        baz.22.png
foo.svg         baz.32.png
bar.16.png      baz.icon
bar.22.png      baz.svg
bar.32.png      junk.txt
```

Each *.icon file just holds the name of the icon, for example, the contents of foo.icon would be
```
rob@rob-thinkpad:~ $ cat icons/foo.icon
The Great Foo
```

What I would like to create in python is the following dictionary:
```
{ 'foo' : "The Great Foo",
  'bar' : "Awesomest Bar",
  'baz' : "Dazzing Baz" }
```


What I need to do for this is
· List the files in the directory
· Extract only the files that end with '.icon'
· Store the name of those *.icon files without the extention
· Read the first line of every *.icon file


I don't have a clue how to archieve these things. Could someone please help me? Thanks

---

### Post by ghostdog74 on 2008-12-16
> **robz0rz said:**
> 
What I need to do for this is
· List the files in the directory
· Extract only the files that end with '.icon'
· Store the name of those *.icon files without the extention
· Read the first line of every *.icon file

the above are simple to do, should have done more reading up.
> **robz0rz said:**
> 
· List the files in the directory

os.listdir() , os.walk()


> 
Extract only the files that end with '.icon'

str.endswith()

> 
Store the name of those *.icon files without the extention


os.path.split()
> 
Read the first line of every *.icon file


firstline = open("file").readline()

---

### Post by Martin Witte on 2008-12-16
also you can look into the [glob module]("http://docs.python.org/library/glob.html") for pathname expansion

---

### Post by fiddler616 on 2008-12-16
Look into the file module for reading the file, the os module for directory work (this was mentioned before) string methods for tampering with what you scrape off the file, and dictionary methods for adding/sorting/editing/etc. the dictionary.

Reading [tutorials]("http://www.ibiblio.org/g2swap/byteofpython/read/") is always recommended...

---

### Post by snova on 2008-12-16
Four line script that will probably work:

[PHP]
import glob
icons = {}
for i in glob.glob('icons/*.icon'):
    icons[i[:-5]] = open(i).readline().strip()
[/PHP]

Yeah, I gave it away. :)

A more explicit version:

[PHP]
import glob
# Obtain list of .icon files
icon_files = glob.glob('icons/*.icon')
# Dictionary
icons = {}
# Iterate over file list
for icon in icon_files:
    # Open file
    file = open(icon)
    # Read line from file. The strip() call just removes the trailing newline, which readline() leaves on.
    first_line = file.readline().strip()
    # Removes the last five letters of the filename, the '.icon' part.
    icon_name = icon[:-5]
    # Sets the entry in the dictionary
    icons[icon_name] = first_line
    # Closes the file
    file.close()
[/PHP]

---

### Post by fiddler616 on 2008-12-16
> **snova said:**
> Four line script that will probably work:

[php]
import glob
icons = {}
for i in glob.glob('icons/*.icon'):
    icons[i[:-5]] = open(i).readline().strip()
[/php]Yeah, I gave it away. :)

A more explicit version:

[php]
import glob
# Obtain list of .icon files
icon_files = glob.glob('icons/*.icon')
# Dictionary
icons = {}
# Iterate over file list
for icon in icon_files:
    # Open file
    file = open(icon)
    # Read line from file. The strip() call just removes the trailing newline, which readline() leaves on.
    first_line = file.readline().strip()
    # Removes the last five letters of the filename, the '.icon' part.
    icon_name = icon[:-5]
    # Sets the entry in the dictionary
    icons[icon_name] = first_line
    # Closes the file
    file.close()
[/php]
Elegant--I haven't seen/heard of glob before. I think I'm a fan. +2
-1 for encouraging through your actions that the OP not bother with a tutorial.
-1 for giving away *whole* code, not just outline and snippets.

---

### Post by snova on 2008-12-16
> **fiddler616 said:**
> Elegant--I haven't seen/heard of glob before. I think I'm a fan. +2

:)

> -1 for encouraging through your actions that the OP not bother with a tutorial.
-1 for giving away *whole* code, not just outline and snippets.

It was with trepidation I wrote that. I fully expected that sort of criticism and wondered whether it was worth it.

On the other hand, is it wrong to teach through example?

And, on its own, this dictionary is useless anyway- he'll still have to write the rest of the program.

---

### Post by scooper on 2008-12-16
Just to be redundant, added exception handling and different file name parsing...
```
import sys
import os.path
from glob import glob
icons = {}
for icon in glob('icons/*.icon'):
    try:
        file = open(icon)
        name = os.path.splitext(os.path.basename(icon))[0]
        try:
            icons[name] = file.readline().strip()
        except IOError, e:
            sys.stderr.write('Failed to read "%s" (%s)\n' % (icon, str(e)))
        finally:
            file.close()
    except IOError, e:
        sys.stderr.write('Failed to open "%s" (%s)\n' % (icon, str(e)))
```

---

### Post by fiddler616 on 2008-12-17
> **snova said:**
> 
It was with trepidation I wrote that. I fully expected that sort of criticism and wondered whether it was worth it.

On the other hand, is it wrong to teach through example? Hmm...where's LaRoza when you need him? That's quite the conundrum...I guess the difference lies not in what *you* post, but how the OP responds to it. If the OP takes the time to read it, understand it, tweak it, even grok it--then we'll all walk away smiling. However if he just says "Oh, all I need to do is copy snova's snippet right *here*, and I need to feed it ___ variables, and it'll return ____, then nobody gains.

---

### Post by digitalvectorz on 2008-12-18
hrm...I agree with both of you in a sense.  The short version, imo, seems more of a bragging piece of code (though a fine piece of code that looks to be);  the commented version however, is a better solution, cause then it gives people the opportunity to read and dissect.  That's how I learn best, typically.

However, what irks me, is why in the world you're defining the code as "PHP Code" ?  Though I must say, the color is attractive.

Just adding two-cents and some irony to the potluck.

cheers.

---

### Post by fiddler616 on 2008-12-18
> **digitalvectorz said:**
> 
However, what irks me, is why in the world you're defining the code as "PHP Code" ?  Though I must say, the color is attractive.
The four options are quote, code, HTML and PHP. Quote and HTML are both bad. Code may be technically more correct, but the syntax highlight PHP provides makes everything much more readable. If only the forum staff would add a Python button...:)

---

### Post by nvteighen on 2008-12-18
> **fiddler616 said:**
> Hmm...where's LaRoza when you need him?

LaRoza is a she :)

> That's quite the conundrum...I guess the difference lies not in what *you* post, but how the OP responds to it. If the OP takes the time to read it, understand it, tweak it, even grok it--then we'll all walk away smiling. However if he just says "Oh, all I need to do is copy snova's snippet right *here*, and I need to feed it ___ variables, and it'll return ____, then nobody gains.

My policy is to analize whether the poster knows what he/she's doing or not. I just don't reply to a forum regular or a someone that seems an experienced programmer the same way as to a newbie. First of all, the type of question reveals the level of the poster and also if code is posted or not.

> **fiddler616 said:**
> The four options are quote, code, HTML and PHP. Quote and HTML are both bad. Code may be technically more correct, but the syntax highlight PHP provides makes everything much more readable. If only the forum staff would add a Python button...:)

If you want color, use code and [http://www.challenge-you.com/bbcode](http://www.challenge-you.com/bbcode) but I have stepped back to non-color code... it's neutral.

---

### Post by fiddler616 on 2008-12-18
> **nvteighen said:**
> LaRoza is a she :)
Ladies and gentlemen:

We have been decieved.

[http://laroza77.blogspot.com/2008/12/end-of-secret-and-observations.html](http://laroza77.blogspot.com/2008/12/end-of-secret-and-observations.html)

(If you're too lazy to read it all: )

[QUOTE=LaRoza's_blog]

The truth is, I'm just a laid back male, who was mistaken for a female, and I didn't care to correct it [/QUOTE]

---

### Post by digitalvectorz on 2008-12-18
Okay this thread has exceeded beyond it's point of discussion.  Let's keep it to the topic;

The starter of this topic escapes me atm, but if you feel that your question(s) have been answered, please mark this as SOLVED or provide us with some more feedback so that we can better try to get an answer to you :-)


Thanks,
dvz

---

### Post by fiddler616 on 2008-12-18
> **digitalvectorz said:**
> Okay this thread has exceeded beyond it's point of discussion.  Let's keep it to the topic;

The starter of this topic escapes me atm, but if you feel that your question(s) have been answered, please mark this as SOLVED or provide us with some more feedback so that we can better try to get an answer to you :-)


Thanks,
dvz
+1
Although the OP seems to have gone AWOL.

---

### Post by robz0rz on 2008-12-18
Still here ;) I haven't had time to get on the forums

This is how my code looks now ```
for foo in os.listdir(".icons/branding/"):
	if foo.endswith(".svg"):
		temp = foo[:-4]
		brandCodes.append(temp)
		if os.path.exists(".icons/branding/"+temp+".name"):
			brandNames[temp] = open(".icons/branding/"+temp+".name").readline()[:-1]
		else:
			brandNames[temp] = temp
```

It's not perfect code, right now, my main concern is that this script works. If I want to write nice code, I'll program in C++ like I usually do. Also, this is part of an initialization process near the start of my script, nothing can go wrong due to faulty input really.

Thanks for all your help

---

### Post by fiddler616 on 2008-12-18
> **robz0rz said:**
> Still here ;) I haven't had time to get on the forums

This is how my code looks now ```
for foo in os.listdir(".icons/branding/"):
    if foo.endswith(".svg"):
        temp = foo[:-4]
        brandCodes.append(temp)
        if os.path.exists(".icons/branding/"+temp+".name"):
            brandNames[temp] = open(".icons/branding/"+temp+".name").readline()[:-1]
        else:
            brandNames[temp] = temp
```It's not perfect code, right now, my main concern is that this script works. If I want to write nice code, I'll program in C++ like I usually do. Also, this is part of an initialization process near the start of my script, nothing can go wrong due to faulty input really.

Thanks for all your help
Great!
(It'd be even a little bit greater if you marked the thread as solved, by the way...)

---


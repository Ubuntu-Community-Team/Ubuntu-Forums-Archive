---
title: "Parsing menu.lst [Python]"
date: 2007-03-14
forum: Programming Talk
---

### Post by tonyr1988 on 2007-03-14
I'm working on my very first Python program ever (I figure it's the easiest / most exciting way to learn it), and I ran into one (hopefully simple) problem. I need to be able to open and parse the user's /boot/grub/menu.lst file.

I plan on creating a list for each part of the menu entries, such as:

title = ["Ubuntu", "Winblows"]
root = ["(hd0,0)", "(hd0,1)"]
kernel = ["blah blah blah", ""]
initrd = ["blah blah blah", ""]
other = [["quiet", "savedefault"], ["makeactive", "chainloader"]]

Would that be the best way to lay it all out? Would there be an advantage to arrays over lists? (I read that lists will automatically resize, unlike arrays)

My other situation is parsing all the right information. In the default menu.lst file, there is an example entry, like so:

> #
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

How can I prevent it from parsing this? Is there a method to say:

1) find "title"
2) grab that line and throw it in "line"
3) if "line" starts with #, forget about it (what's the equivalent of "continue" a loop in python?)

Or, alternatively, I figure I could first find:

> BEGIN AUTOMAGIC KERNELS LIST

and only search *after* that point. 

So...my problem isn't so much parsing a file, but parsing the right stuff in a file. Please help a n00bie out? :)

---

### Post by raja on 2007-03-14
To check if the line starts with '#' denoting a comment, you would do something like this :
```

# open file to read
fi = open("/boot/grub/menu.lst",'r')

#read line by line
for line in fi.readline():

    #does line have a '#' as first non-space character?
    if line.strip()[0] == '#':

        #do nothing, go to next line
        continue 

    #And now do whatever else you want to...

```

Also, there is no inbuilt 'array' type in python. 
Have fun !

---

### Post by tonyr1988 on 2007-03-14
Oh wow, python **is** as easy / powerful as everyone makes it out to be. :) I've gotten tons of syntax errors so far (mainly for semicolons and brackets), but I'm slowly getting used to it all.

Thanks a ton. Also, if there are no arrays built-in to python, does that mean that lists are the best way to do it?

---

### Post by po0f on 2007-03-14
Sorry, wrong topic.  :/

---

### Post by pmasiar on 2007-03-15
> **tonyr1988 said:**
> I'm working on my very first Python program ever (I figure it's the easiest / most exciting way to learn it)

You are right, writing a program is easiest way to learn it. But you are jumping little ahaead - you cannot write a program before you learned basics. Wikibooks have good Python tutorial with basics only (no OOP), here is chapter about lists: [http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python/Lists](http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python/Lists)

You may want to read whole tutorial to get bigger picture. And knowing language does not teach you about designing data structures - it is orthogonal skill, independent of language syntax. I have collection of links to learn Python and data structures, with simple tasks to solve:  [http://learnpydia.pbwiki.com/](http://learnpydia.pbwiki.com/)

> Would there be an advantage to arrays over lists? (I read that lists will automatically resize, unlike arrays)

Lists are implemented using arrays (of objects), and you can resize them: mylist.append() or mylist.extend() l. Neither list or array resizes automatically (you cannot assign element out of index range). Python has also dictionaries (called Associative array == hash == map in other languages) where you can assign to any key (if not existing, will be created == resizes automatically) but keys are not sorted (you can sort them if you wish).

> 1) find "title"
2) grab that line and throw it in "line"
3) if "line" starts with #, forget about it (what's the equivalent of "continue" a loop in python?)

```

for line in open('path/to/your/file.lst'):
    if line.startswith('#'): 
        continue
    if line.find('title'):
        # 'title' found - do something

```

Just read up lists, loops, and string methods. Do read it, as my example shows, method names are pretty obvious - that's exactly mantra of Python: **"There should be one obvious way to do it right"**

And do try command shell - it is best way to poke around a list and found what you can do with it, and how.

---

### Post by raja on 2007-03-15
> **pmasiar said:**
> You are right, writing a program is easiest way to learn it. But you are jumping little ahaead - you cannot write a program before you learned basics. Wikibooks have good Python tutorial with basics only (no OOP), here is chapter about lists: [http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python/Lists](http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python/Lists)

```

for line in open('path/to/your/file.lst'):
    if line.startswith('#'): 
        continue
    if line.find('title'):
        # 'title' found - do something

```
.

line.startswith('#') will miss a comment if there is a space before the '#'. So would it not be better to check it as line.strip().startswith('#')?

---

### Post by pmasiar on 2007-03-15
> **raja said:**
> line.startswith('#') will miss a comment if there is a space before the '#'. So would it not be better to check it as line.strip().startswith('#')?

Good catch. You might be right. Depends if '   #' is valid comment or not. But I still like startswith() more than line[0]. 

Another easy way to find a substring is: if 'title' in line: As I said, I like Python because it is so obvious to read the code. :-)

---

### Post by Endolith on 2009-01-07
How did you do on this?  There's a simple thing for grabbing the titles in *bootnext*, but it doesn't seem very robust:

[php]def grub_title_list():
    f = open(GRUB_CONFIG, 'r')
    lines = f.readlines()
    f.close()

    p = re.compile('^\s*title\s*(.*)')
    tlist = []

    for line in lines:
        m = p.match(line)
        if m : 
            tlist = tlist + [ m.group(1) ]

    return tlist
[/php]

---


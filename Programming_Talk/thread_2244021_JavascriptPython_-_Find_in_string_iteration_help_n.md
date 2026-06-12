---
title: "Javascript/Python - Find in string iteration help needed"
date: 2014-09-12
forum: Programming Talk
---

### Post by slooksterpsv on 2014-09-12
Here's what I'm trying to do. I have an array setup with some titles in it - lets start small 2 (but I'll use 2 different examples):

```

titles = ["New World", "World"]

```

Now if I want to search a string and pull out just the specific title, I'm having trouble doing so because it finds the other one as well. So let's say I iterate through the array:

```

//...
info = "New World is on shelf 7B"
//...
for item in titles:
 if info.find(item) > -1:
  // do some stuff

```

Now, I understand why that fails there, but how can I check for a specific but skip the other? The other issue I have is this one:

```

titles = ["New", "New Mountain"]

```

If I iterate through those when search for New, it'll pick out New and New Mountain.

If I can see the code in Python I can translate into javascript, or vice versa. The project I'm working on is in Javascript, but I can't wrap my brain how to code it. Initially I'm thinking:
check through the titles and match them, search through the titles and find close resembling titles, check for titles to see if it's 1 or the other. Choose particular one.

But I'm doing this for a list that can be as large as 300 items! So If you know of anyways I can do this.

Now to be honest, I need the javascript code to work in IE8 - jquery would be beautiful but I can't have external sources.

EDIT: This is not for school, this is for work.

---

### Post by Vaphell on 2014-09-12
so you want the longest match satisfying *title in sentence* condition?

```
sorted( ( t for t in titles if t in info ), key=len, reverse=True )[0]
```

---

### Post by slooksterpsv on 2014-09-13
Well that's tricky too because I may have it listed in the info like this:
```

info = "New World and World are on shelf 7A"

```

So if I need to pull out both titles to another variables.

EDIT: OH I see how that works. Now if I can implement that into Javascript

---

### Post by slooksterpsv on 2014-09-13
I figured it out!!!! Now I'm just going to have to iterate to find all the similar items first instead of knowing them off hand, here's my code if anyone needs help with it in python:
```

count = 0
match = 0
for title in titles:
    match = 0
    if comments.find(title) > -1:
        count = 0
        for ctitle in copy_titles:
            if comments.find(title) + len(title) == comments.find(ctitle) + len(ctitle) and ctitle != title:
                if comments.find(ctitle, comments.find(ctitle)+1) > -1:
                    print "EX1: ", ctitle
                    match = 1
                if (len(ctitle) > len(title) and comments.find(ctitle) + len(ctitle) == comments.find(title) + len(title)):
                    print "EX2: ", ctitle
                    match = 1
            elif ctitle != title and comments.find(ctitle) == comments.find(title):
                    if comments.find(ctitle) + len(ctitle) > comments.find(title) + len(title):
                        print "EX3: ", ctitle
                        match = 1
                    elif comments.find(ctitle, comments.find(ctitle)+1) > -1:
                        print "EX4: ", ctitle
                        match = 1
        if match == 0:
            print "INIT: ", title

```

EDIT: Found another flaw, this one works! =D

---

### Post by Vaphell on 2014-09-13
could you explain what the code is supposed to do? Your solution looks kinda large for python ;-)

---

### Post by ofnuts on 2014-09-14
If you want only the titles that contains your string and nothing else, why aren't you use an equality comparison instead of find() (if info==item)?

---

### Post by slooksterpsv on 2014-09-15
It's for work, and I translated the code to javascript (that was easy). Pretty much, when we document certain items we will sometimes gather a list of titles (for whatever). Well when documenting our information, I wanted to be able to pull those titles out for quicker access. I'm working in a limited list range of 100 items at most, granted the code is inefficient, and Python was used pretty much as a testing solution (I code a lot better in Python than I do in JavaScript). So I may have items like the following:
Crash Bandicoot
Crash Bandicoot 2
Five
Five More Monsters
Five The Quest

Well I need to search for the specific items, but if my documentation like this is:
[b]
Tried locating Five More Monsters in database CQ513. Wasn't able to locate particular title. Searching through advanced database ADB1172.
[/b]
So if I tried searching for any of the titles, it would come up with Five and Five More Monsters. Well I didn't explicitly search for Five, just Five More Monsters, so I had to check and see what string it was exactly.

That's the basis.

---

### Post by Vaphell on 2014-09-15
Without some data in comments, titles and copy_titles it's rather hard to decypher the logic.
*comments * is probably a set of things like:
*Tried locating Five More Monsters in database CQ513. Wasn't able to locate particular title. Searching through advanced database ADB1172.*
Are comments in a finite set of predictable formats?

titles probably stores
[I]Crash Bandicoot
Crash Bandicoot 2
Five
Five More Monsters
Five The Quest[/I]

what is copy_titles for?

Also is there a reason to go with find() instead of *'pattern' in 'string'* which kinda makes the code look unpythonic?

---

### Post by slooksterpsv on 2014-09-17
Again, it's a Javascript implementation I was after.

And I found a bug in it. In the second if statement, I don't compare the title's themselves and just use the lengths which is troublesome if the title lengths equal the same length another title.

With Javascript I"m having to use this in IE8, which makes it very cumbersome.

---

### Post by Vaphell on 2014-09-17
javascript justifies find() instead of x in y, but i still don't get the idea/algo behind the code, what copy_titles is, why there are 4 different branches in the code and what subproblems they are supposed to solve

---

### Post by slooksterpsv on 2014-09-17
You know that's too funny that you mention that, but when I developed the code, I tested it, and certain examples would hit every one of those conditional loops for specific titles. So I just remember coding it and thinking through it at the time, yet, I don't really understand how I came to the conclusion that it works how it works. It's odd, but sometimes when I get into my programming fits, I just figure things out. If I could post what I do for work, I would give you really really really good examples, but due to NDA's I can't say.

---

### Post by Vaphell on 2014-09-18
you don't have to put your real stuff here. I am just curious what the copy_title is (not seeing its purpose in the original description of the problem) and for all i care the few example strings showcasing corner cases could be of the "this is OmgWtfBbq" variety.

if you got titles "ABC" "ABC DEF" and "GHIJKLMNOP", what should be picked when tried against "something ABC DEF something GHIJKLMNOP"? Always the longest match? What if there is a draw?

---


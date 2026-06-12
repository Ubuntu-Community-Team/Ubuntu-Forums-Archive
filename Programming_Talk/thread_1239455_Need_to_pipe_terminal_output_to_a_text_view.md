---
title: "Need to pipe terminal output to a text view"
date: 2009-08-13
forum: Programming Talk
---

### Post by M4rotku on 2009-08-13
Hey guys,

This one has had me stumped for a while now, and I can't go any further with my project until I solve it.  I need to be able to pipe the text that normally would go to the terminal to a text view widget within my GUI.  In the context of my tv episode ripping application, this would allow me to prompt the user for x amount of titles based on how many episodes they want to rip.  Very rough example of what I need:

The user inputs how many titles they want to rip and then the text view prompts them:

> What is the title of episode one: 

and so on, gathering the titles similar to how a raw_input() would.

As far as I can see, this would be the easiest way to ask within the GUI for the titles since they might want to rip up to 20 episodes or more.  I can't see doing it outside of a text view because with that many titles to input, there would have to be some way to scroll it.

The other option which I have considered is to, in a loop for x times, have a popup window come up and ask for title x.

Any advice on either of these approaches would be greatly appreciated.

Much thanks,
M4rotku

---

### Post by geirha on 2009-08-14
Some example code that shows what you're trying to do would help. And also, at the very least you should mention which language you are programming in. Since you mentioned raw_input though, I assume you're using python, and as such I recommend you read the help on subprocess.

```
>>> help('subprocess')
```

---

### Post by M4rotku on 2009-08-14
Oh, sorry for not including that info, for some reason I thought that I had Python in the title of the thread.  As for the code to get the idea of what I need to do, I can include what I have so far, but I don't really think it will help because I haven't really made an attempt at it yet.  However, it is now attached.

I will look into the help info that you listed.  Thank you for your advice.

---

### Post by M4rotku on 2009-08-14
I read the info about subprocess and all of it went way over my head.

---

### Post by unutbu on 2009-08-14
Maybe some example code (and nice explanation) will help:
[http://blog.doughellmann.com/2007/07/pymotw-subprocess.html](http://blog.doughellmann.com/2007/07/pymotw-subprocess.html)

---


---
title: "Python Comic"
date: 2007-12-05
forum: Programming Talk
---

### Post by skeeterbug on 2007-12-05
[http://www.xkcd.com/353/](http://www.xkcd.com/353/)

---

### Post by Anzan on 2007-12-05
Yes, this is all over the Pythonista blogs.

But just importing shouldn't run it, should it?

---

### Post by Can+~ on 2007-12-05
THAT'S IT, I'm learning python.

I've been wondering long time if it was worth the time, as my University doesn't teach python (I think). But now xkcd is just the signal I've been waiting for.

Here I come pythonland.

---

### Post by cwaldbieser on 2007-12-05
> **Anzan said:**
> Yes, this is all over the Pythonista blogs.

But just importing shouldn't run it, should it?

def statements are executed when you import a module.  So are class statements.  A function call could also be executed.  That is why most executable scripts have
```

if __name__ == "__main__":
    #Run code

```
Otherwise, the script would be executed when imported.

---

### Post by ThinkBuntu on 2007-12-05
The alt text is "I wrote 20 short programs in Python yesterday.  It was wonderful.  Perl, I'm leaving you." for those that don't see long alt text.

---

### Post by LaRoza on 2007-12-05
> **cwaldbieser said:**
> def statements are executed when you import a module.  So are class statements.  A function call could also be executed.  That is why most executable scripts have


By def statements, are you saying Functions are executed? They are not when imported, only function calls.

---

### Post by ThinkBuntu on 2007-12-06
[Here's the discussion on the xkcd forums.]("http://forums.xkcd.com/viewtopic.php?f=7&t=15797") I think that this actually will give Python a push for young developers - many of us read xkcd, which is why the cartoonist recently spoke at MIT. I think that Perl is going the way of a legacy language, since most adherents stick with it only because they're already comfortable with or learned on the language.

---

### Post by pmasiar on 2007-12-06
> **LaRoza said:**
> By def statements, are you saying Functions are executed? They are not when imported, only function calls.

Yes, even def statements are executed. def statement links name of the function to the body. Later, you can relink if you need to, this is what decorators do.

Code in the module outside of def blocks is executed when imported.

---

### Post by christhemonkey on 2007-12-06
Love it.

This is one of my favourites:
[IMG]http://imgs.xkcd.com/comics/brick_archway.png[/IMG]

---

### Post by pmasiar on 2007-12-06
> **ThinkBuntu said:**
> I think that this actually will give Python a push for young developers 

Even bigger push will be that Python is main development language for OLPC. Thousands of hackers (from millions of users) for whom Python was the first and only language are in the pipeline. :-)

> I think that Perl is going the way of a legacy language, since most adherents stick with it only because they're already comfortable with or learned on the language.

Yup, and new development (Perl 6) is going nowhere. No support from big companies, it is hobby project. Cannot compete with Python, where many gurus are employed by Google and work 50% on Python, Microsoft (IronPython), PyPy (paid by EU), etc.

I loved Perl for a time, learned to love duck typing, but I divorced it couple years ago and will never return.

---

### Post by pmasiar on 2007-12-06
My favorites are:
[http://imgs.xkcd.com/comics/sandwich.png](http://imgs.xkcd.com/comics/sandwich.png)

[http://imgs.xkcd.com/comics/goto.png](http://imgs.xkcd.com/comics/goto.png)

---

### Post by ThinkBuntu on 2007-12-06
What will Android support? Too lazy to Google. I'd guess Java, but that's just a guess...

---

### Post by aks44 on 2007-12-06
> **Can+~ said:**
> THAT'S IT, I'm learning python.

I've been wondering long time if it was worth the time, as my University doesn't teach python (I think). But now xkcd is just the signal I've been waiting for.

Here I come pythonland.

Oh my... I can't believe that some people actually rely on a _*comic*_ to choose what language they'll learn.

Oh Lord, not even tinfoil can save us now. (® theregister)

---

### Post by Can+~ on 2007-12-06
> **aks44 said:**
> Oh my... I can't believe that some people actually rely on a _*comic*_ to choose what language they'll learn.

Oh Lord, not even tinfoil can save us now. (® theregister)

I'm not relaying on a comic. I've tried python before, but I had to drop it because of studies.

Now, XKCD reminded me that I was learning it.

Tin foil hat? I have a body armor in case of alien invasion.

---

### Post by jespdj on 2007-12-06
> **pmasiar said:**
> My favorites are:
[http://imgs.xkcd.com/comics/sandwich.png](http://imgs.xkcd.com/comics/sandwich.png)

[http://imgs.xkcd.com/comics/goto.png](http://imgs.xkcd.com/comics/goto.png)

[IMG]http://imgs.xkcd.com/comics/sandwich.png[/IMG]
:lolflag:
I wish everything was so easy!

---

### Post by tyoc on 2007-12-06
amm go to windows?? (you are almost a user as root :P) hehehe

---

### Post by Can+~ on 2007-12-06
We should learn LOLCODE

[http://lolcode.com/](http://lolcode.com/)

```
HAI
CAN HAS STDIO?
PLZ OPEN FILE "LOLCATS.TXT"?
	AWSUM THX
		VISIBLE FILE
	O NOES
		INVISIBLE "ERROR!"
KTHXBYE
```

---

### Post by aks44 on 2007-12-06
> **Can+~ said:**
> I'm not relaying on a comic. I've tried python before, but I had to drop it because of studies.

Now, XKCD reminded me that I was learning it.

Heh, sorry that I misunderstood you... to me your post looked like that comic was the reason you decided to learn Python. No hard feelings. :)


(BTW one of my favourites is the "breakout" one too... it literally made me laugh out loud when I saw it)

---

### Post by tyoc on 2007-12-06
I dont know what is a "breakout"

---

### Post by aks44 on 2007-12-06
> **tyoc said:**
> I dont know what is a "breakout"

This one:
> **christhemonkey said:**
> [IMG]http://imgs.xkcd.com/comics/brick_archway.png[/IMG]

"Breakout" is an old Atari game where you're supposed to break bricks... (thanks Wikipedia for that screenshot)
[IMG]http://upload.wikimedia.org/wikipedia/en/c/c6/Breakout2600.png[/IMG]

There has been many clones, Arkanoïd being one I really enjoyed at the time... :)

---

### Post by cwaldbieser on 2007-12-06
> **LaRoza said:**
> By def statements, are you saying Functions are executed? They are not when imported, only function calls.

No, I mean a statement such as:
```

def foo():
    print "Whee!"

```

creates a function object when the module is imported.  "def" is not a static declaration.  It is actually a statement that is executed.

---

### Post by Wybiral on 2007-12-07
I think you guys/girls are basically saying the same thing. That's the interesting thing about Python, function declarations are a statement that gets executed and appends that method to the module. So, in a sense it's importing, and in a sense it's executing "def" statements that build the function.

---

### Post by pmasiar on 2007-12-07
... and code outside of def blocks gets executed on import, too.

---

### Post by jespdj on 2007-12-07
> **aks44 said:**
> "Breakout" is an old Atari game where you're supposed to break bricks... (thanks Wikipedia for that screenshot)

There has been many clones, Arkanoïd being one I really enjoyed at the time... :)
That reminds me that long ago I wrote my own version of Breakout in Pascal, on my 386SX 20 MHz (in about 1992...) :D

---


---
title: "Python: set time for user input"
date: 2009-07-23
forum: Programming Talk
---

### Post by lordhaworth on 2009-07-23
Hi,

I am trying to get a piece of code going, in which the user has a set amount of time in which to enter some text. If they do not and the time expires or if they do before the time has expired it should move (instantly) on depending on whether anything has been entered.

Therefore using sleep wont work because I want the code to move on as soon as the user has finished entering text.

I have also looked at threading which seems to work better, I can get it to wait for user input but not sure how to make it stop once it is found! Ill show you the relevant code bits (obviously incomplete):

```

	t = threading.Timer(30.0, listening(thisWord)
	t.start()

```

where listening is something like:

```

def listening(thisWord):
	signal = raw_input(thisWord)
	return signal

```

I have tried added conditionals 

```

        If signal != None:
               set some kind of flag or force exit...

```


M questions are - 
is threading the way I want to do my original task?
how can I escape the thread early if signal becomes != None ? 

I am rather new to python by the way

Cheers

Tom

---

### Post by lordhaworth on 2009-07-25
bump,


at the least - is my question unanswered because it is hard, or because it is stupidly easy?

Cheers

---

### Post by y-lee on 2009-07-25
> **lordhaworth said:**
> bump,


at the least - is my question unanswered because it is hard, or because it is stupidly easy?

Cheers

no not stupidly easy, but i think ya going about it a hard way. See [timing out a function]("http://code.activestate.com/recipes/307871/")

Edit: Also what version of python ya using?

---

### Post by lordhaworth on 2009-07-26
Cheers for the response,

that link does look like it should provide what I need. I'm new to python and still havnt quite grasped the scope of whats available, still thinking in terms of lower level programming!


EDIT: I am using 2.6.2, I understand v3.0.1 has been released - would it be best to move straight to this (since I am still just really beginning in python)?

---

### Post by y-lee on 2009-07-26
> **lordhaworth said:**
> I am using 2.6.2, I understand v3.0.1 has been released - would it be best to move straight to this (since I am still just really beginning in python)?

Well my advice to you is to stick with python 2.6 for now, just be aware that python 3.* is not[ backwards compatible]("http://stackoverflow.com/questions/340530/will-python-3-0s-backwards-incompatibility-affect-adoption") with prior versions of python. Thus is especially annoying as it effects the print statement:

> The print statement has been replaced with a print() function, with keyword arguments to replace most of the special syntax of the old print statement. (see [what is new in python 3.0]("http://docs.python.org/3.0/whatsnew/3.0.html"))


---


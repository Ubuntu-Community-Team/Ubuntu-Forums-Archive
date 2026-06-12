---
title: "Program to read gmail."
date: 2011-07-28
forum: Programming Talk
---

### Post by Mathew Roy on 2011-07-28
Hi, all..
I am trying to make a program, and it requires to download email attachment by itself. Any Idea?
All I want is to download attachment of emails from selected persons automatically, and process the downloaded files.. So I need to study about gmail API and all...Also I am just a beginner level programmer. So, can anyone of you kindly help me in this direction? Tips, and links that I should refer. I am also very happy to accept code if any one contributes.

Please I desperately need some help...Wont you help?? My preferred language is C. Didn't ii tell you I am just a beginner? (I know only C and C++, and a little python)

Thanks in advance...

---

### Post by MadCow108 on 2011-07-28
its probably simplest in a high level language like python, have a look at imaplib and pop3lib

e.g. some basic imap stuff to get you started:
```

import getpass, imaplib

m=imaplib.IMAP4_SSL("imap.googlemail.com","993")
m.login("yourlogin", getpass.getpass())
#select some folder
m.select("somefolder", readonly=True)
#search unseen messages
m.search(None, '(UNSEEN)')
#fetch message 1832
m.fetch(1832, '(RFC822)')
#fetch only subject and from
m.fetch(1832, '(BODY[HEADER.FIELDS (SUBJECT FROM)])')
m.close()
m.logout()

```

the imap commands can be found in section 6.4 of [http://james.apache.org/server/rfclist/imap4/rfc2060.txt](http://james.apache.org/server/rfclist/imap4/rfc2060.txt)

---

### Post by Mathew Roy on 2011-07-29
Hi MadCow,
Thank you for helping me..Can you please explain this code.. Cuz I am a beginner... 
Ok i will use python.. but before that i have study it.. I just know how to find sum and all in python.. So it will be really helpful if you explain it..
Also is it possible to combine C and python in any way?. Cuz I am more comfortable with C.
Thanks a lot....

---

### Post by DangerOnTheRanger on 2011-07-30
I think you're slightly confused about this "GMail API". GMail is just a normal mail service, provided by Google.
Thus, you can interact with it using the standard IMAP email protocol, which Python has built-in support for - see [http://docs.python.org/release/2.6.6/library/imaplib.html](http://docs.python.org/release/2.6.6/library/imaplib.html) and the link MadCow108 provided.
Try figuring his example out all by yourself - it's very simple, so you should be able to understand it in no time. The link he gave explains all the IMAP commands he used in his script.

Addressing one of your other questions, there are many ways to combine Python and C. In fact, the mainstream Python interpreter (the one you're probably using) is written in C. 
Here's the main way to do it: [http://docs.python.org/release/2.6.6/extending/](http://docs.python.org/release/2.6.6/extending/)

On the other hand, if you want to interact with an already-existing C library, then look at the built-in Python module ctypes ([http://docs.python.org/release/2.6.6/library/ctypes.html](http://docs.python.org/release/2.6.6/library/ctypes.html)).

---

### Post by Mathew Roy on 2011-07-30
[DangerOnTheRanger]("http://ubuntuforums.org/member.php?u=984580"), you are exactly right. I dont know about "GMail API" or about IMAP4. And even python, I just attended a half day class about it. What I am really comfortable with is C and C++. Well the fact is I am an electronics engineering student and we are not required to learn any programming language till now. But I have great interest in programming and so I learned C and C++.
But, well python seems interesting/powerful and I am ready to learn.. but don't know where I should start from.
Right now I am going through the links you provided. They seem just the same I am looking for..
Thank u so much... And expecting more help...

---

### Post by DangerOnTheRanger on 2011-07-30
No problem - I'm always glad to help :)

Here are some more links you might find useful:

[LIST]
[*]The official Python tutorial - [http://docs.python.org/release/2.6.6/tutorial/index.html](http://docs.python.org/release/2.6.6/tutorial/index.html)
[*]Dive into Python (slightly dated) - [http://diveintopython.org/toc/index.html](http://diveintopython.org/toc/index.html)
[*]Learn Python The Hard Way - [http://learnpythonthehardway.org/book/](http://learnpythonthehardway.org/book/)
[/LIST]

---

### Post by Mathew Roy on 2011-07-31
Thank u [DangerOnTheRanger]("http://ubuntuforums.org/member.php?u=984580"). 
My first impression about python is that, "It is just the language that I am looking for". I have already started reading the tutorial. But It may take some time as, I have to give more preference to my studies. But, never the less, I will find time to learn python , may be late night everyday..
Happy to know that C, C++ and python can be combined(!?) so that I do not have to change the main program, that is written in C..

---


---
title: "[Python] Check if file exists"
date: 2011-03-23
forum: Programming Talk
---

### Post by ki4jgt on 2011-03-23
How do you check if a file exists in Python?

---

### Post by LemursDontExist on 2011-03-23
Take a look at os.path.isfile() and os.path.isdir().

---

### Post by oedipuss on 2011-03-23
Also, os.path.exists and os.path.lexists

---

### Post by rabbitdaone on 2011-03-23
```


import os

try:
    os.path.exists(/path/to/file)

except Exception, e:    
    print e, ":File does not exist"


```OR

```


import os

try:
    os.path.isdir(/path/to/dir)

except Exception, e:    
    print e, ":Directory does not exist"


```
The difference between **os.path.isdir()** & ** os.path.exists() **, is the the first only returns True if its a directory, the second will return true for both directories and files.

Hope this helps (ima newbie myself)

PS.
you could also use **os.path.isfile()**

---

### Post by cgroza on 2011-03-23
One more alternative is to try to open it in a try except block, and if it throws an error, it does not exist.

But I really recommend the os.path.exists() way.

---

### Post by thornmastr on 2011-03-24
A number of people answered this question. Assume for every time this question is asked 5 people answer it. These same people could have spent their time on  more challenging questions.

What is a challenging question? Perhaps we should look at the inverse: What is not a challenging question. Perhaps a question that can be answered using the following pattern: 'How do I open a file in Python' passed to Google. In short, any question that can be reasonably answered in one pass through Google is not challenging. If it takes an algorithm. If it evokes wonder as to how to even ask the question, that becomes a challenge. 

All beginners need help. Google is a great teacher. So are the tutorial programming pages. Use them.

Stepping off soap box,

Robert Berman

---

### Post by cgroza on 2011-03-24
> **thornmastr said:**
> A number of people answered this question. Assume for every time this question is asked 5 people answer it. These same people could have spent their time on  more challenging questions.

What is a challenging question? Perhaps we should look at the inverse: What is not a challenging question. Perhaps a question that can be answered using the following pattern: 'How do I open a file in Python' passed to Google. In short, any question that can be reasonably answered in one pass through Google is not challenging. If it takes an algorithm. If it evokes wonder as to how to even ask the question, that becomes a challenge. 

All beginners need help. Google is a great teacher. So are the tutorial programming pages. Use them.

Stepping off soap box,

Robert Berman

In other words ignore the user because his question does not require the intervention of some expert in the field?

---

### Post by thornmastr on 2011-03-24
> **cgroza said:**
> In other words ignore the user because his question does not require the intervention of some expert in the field?

Ouch!

I hope you know I neither said nor implied to ignore the OP. I do think you would have helped the user more if you pointed him to Google or one of the excellent beginner Python tutorials.


Robert

---

### Post by robots.jpg on 2011-03-24
> **thornmastr said:**
> A number of people answered this question.  Assume for every time this question is asked 5 people answer it. These  same people could have spent their time on  more challenging questions.

What is a challenging question? Perhaps we should look at the inverse:  What is not a challenging question. Perhaps a question that can be  answered using the following pattern: 'How do I open a file in Python'  passed to Google. In short, any question that can be reasonably answered  in one pass through Google is not challenging. If it takes an  algorithm. If it evokes wonder as to how to even ask the question, that  becomes a challenge. 

All beginners need help. Google is a great teacher. So are the tutorial programming pages. Use them.

Stepping off soap box,

Robert Berman

This sounds like something ripped straight from a newsgroup in the 90s.  I'm not saying you're wrong,  just that it's been a long time since I've seen someone  spend so many words on "Google it."

---

### Post by ki4jgt on 2011-03-24
I searched google and got the os.path.isfile() every response I got was false, whether the file existed or not :-(

---

### Post by cgroza on 2011-03-24
> **thornmastr said:**
> Ouch!

I hope you know I neither said nor implied to ignore the OP. I do think you would have helped the user more if you pointed him to Google or one of the excellent beginner Python tutorials.


Robert

Yes, but spending the time on answering other advanced questions after seeing this post and knowing the answer and not giving it is ignoring to me.

---

### Post by thornmastr on 2011-03-24
> **ki4jgt said:**
> I searched google and got the os.path.isfile() every response I got was false, whether the file existed or not :-(

OK. But your question was "How do you check if a file exists in Python?". The statement I put into Google: 'How do I tell if a file exist using python'. Leave out the quotes.
I think you will find a correct answer as well as a few different approaches to solving your question as well.

Robert

---

### Post by Tony Flury on 2011-03-25
> **ki4jgt said:**
> I searched google and got the os.path.isfile() every response I got was false, whether the file existed or not :-(

Do you want to show us the code ?

One gotcha that some people fall over is that the os.path functions don't expand "~" automatically - you have to use os.path.expanduser first to expand "~" to "/home/tony" - or whatever your home directory is called.

---

### Post by rabbitdaone on 2011-03-25
Have you tried any of the first replies to your thread?

---


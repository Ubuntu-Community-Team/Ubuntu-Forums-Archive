---
title: "First programming language to start?"
date: 2014-12-03
forum: Programming Talk
---

### Post by flaymond on 2014-12-03
Hello guys! Today I would like to get some opinions from you guys about easy, elegant and good programming language to start. I'm actually in C++ learning. But, I find it difficult to understand. It was a very big programming and too powerful for me because I even don't understand how the concepts and how it worked. I want to get myself involved in Ubuntu developing (maybe, someday...:KS, 5-10 years more to count). I tried Python ( since it's the most high-rated and most popular for beginners), and found it easy to coding since it's a high-level language and straight forward syntax. Then, I also tried the Perl language. I still don't know what it used for, but also found it was easy...but slightly difficult than Python. I really want to understand and learn to code with a great understanding..and can move on to C++ language. There's a lot of programming languages to learn  . I don't know which to choose.

 So my question is, which programming language that you think suitable and highly recommend for me to start with as the first one?

Thanks for all of your helps and opinions!

* Sorry for terrible grammar, I'm not an native English speaker. Forgive me  :icon_frown:

---

### Post by slickymaster on 2014-12-03
There's loads and loads of threads about this on the [Programming Talk]("http://ubuntuforums.org/forumdisplay.php?f=39") sub-forum. Do we really need to start a new one?

Just from this year:
[http://ubuntuforums.org/showthread.php?t=2204979](http://ubuntuforums.org/showthread.php?t=2204979)
[http://ubuntuforums.org/showthread.php?t=2208632](http://ubuntuforums.org/showthread.php?t=2208632)
[http://ubuntuforums.org/showthread.php?t=2222587](http://ubuntuforums.org/showthread.php?t=2222587)
[http://ubuntuforums.org/showthread.php?t=2221991](http://ubuntuforums.org/showthread.php?t=2221991)
[http://ubuntuforums.org/showthread.php?t=2249224](http://ubuntuforums.org/showthread.php?t=2249224)
[http://ubuntuforums.org/showthread.php?t=2250365](http://ubuntuforums.org/showthread.php?t=2250365) (you posted on this one)
[http://ubuntuforums.org/showthread.php?t=2250922](http://ubuntuforums.org/showthread.php?t=2250922) (thread started by you on the same subject)

---

### Post by flaymond on 2014-12-03
Sorry if I'm duplicating the same one....I just wanna fresh infos and opinions since there's a lot of update and upgrade with several majors programming language like C++11, Perl 6, Julia etc. I should find if there is similar question before asking. (advice to myself)

---

### Post by coldraven on 2014-12-03
More links!
[http://lifehacker.com/which-programming-language-should-i-learn-first-1477153665](http://lifehacker.com/which-programming-language-should-i-learn-first-1477153665)
[http://www.eweek.com/developer/slideshows/top-10-programming-languages-for-job-seekers-in-2014.html/](http://www.eweek.com/developer/slideshows/top-10-programming-languages-for-job-seekers-in-2014.html/)

---

### Post by ofnuts on 2014-12-03
> **InterProg said:**
> Sorry if I'm duplicating the same one....I just wanna fresh infos and opinions since there's a lot of update and upgrade with several majors programming language like C++11, Perl 6, Julia etc. I should find if there is similar question before asking. (advice to myself)

A new popular programming language doesn't show up every month. Answers from 2014 are still valid...

From  your other posts you are likely trying to eat more than you can chew.  Try to become a bit more competent in the simpler languages before moving to  the next. And don't get too focused on languages. Programming languages  are just tools. You need to know how to use them but the real thing is  the concepts that they carry (objects, functions....) and general  programming knowledge (data structures, algorithms...). Languages are to  the programmer what paintbrushes are to the artist, and Leonardo da  Vinci didn't become famous because he used better paintbrushes than the  others.

Read [books]("http://www.amazon.com/s/ref=nb_sb_noss?url=search-alias%3Daps&field-keywords=data+structures&rh=i%3Aaps%2Ck%3Adata+structures").

---

### Post by flaymond on 2014-12-04
Thanks for the links! Now, I've decided to take Python as my first programming language to start. ***But, ***what version should I choose? Python 2.x or Python 3.x. When I search them, some said that Python 3.x is nice, but lack of Library Support ( I don't even understand what that mean). However, Python 2.x is more wide-used and compatible with Linux than Python 3.x (unstable, maybe?). Which one should I chose? Python 2.x for compatible and stable? or Python 3.x for new and maybe will be wide-used in the future?

---

### Post by pauls2 on 2014-12-04
I believe Ubuntu ships with Python 3.x and 2.x. Updates are performed as available.

---

### Post by flaymond on 2014-12-04
I chose Python 3.x because the the python 2.x supports has ended....Well, on lifehacker pages and some sites said...that you better choose Python 3 because the Unicode were made as default in Python 3.x. I'm downloaded Python 3.4.0 IDLE from software centre....for highlighting feature. and, I just found a problem when I try this code on Terminal (after switching to python3 mode).

```
def test():
               print("Hello World")

```

and I got an error that not happened in IDLE.

```
def test():
... print("Hello World")
  File "<stdin>", line 2
    print("Hello World")
        ^
IndentationError: expected an indented block


```

It only happened on terminal (in python3 mode)..and not on IDLE. Is this bugs, or I just made a syntax error? Any idea?

---

### Post by spjackson on 2014-12-05
You need to indent the print statement (e.g. with 2 spaces, or 4 spaces or whatever you prefer). 
```

$ python3
Python 3.4.0 (default, Apr 11 2014, 13:05:11) 
[GCC 4.8.2] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> def test():
...   print("Hello World")
... 
>>> test()
Hello World
>>> 

```

---

### Post by flaymond on 2014-12-05
Thank you spjackson! Now it going good....I don't know that space also effecting the codes...well..in C++..spaces are not that critical. But, yeah! Thanks!

---

### Post by veddox on 2014-12-05
Definitely go for Python 3. At your stage you don't need to worry about  library support yet, and by the time you do, it won't be an issue any  more... Everything else is in favour of Python 3.

---

### Post by flaymond on 2014-12-05
Thanks for the advice veddox! ;)

---


---
title: "What version of Python should I look for a tutorial for? And where?"
date: 2010-10-23
forum: Programming Talk
---

### Post by ThePhysician on 2010-10-23
I'm quite new to this whole application programming thing. I've done extremely extensive work in HTML and CSS, but those of course are just for making websites.

This whole week I scoured through these and other forums trying to decide which language to start on and finally decided on Python (although Ruby was a close second, and I am still interested to hear your persuasions, should you have valid ones).

Well today I go to the "Non-Programmers Tutorial for Python" and there's one for 2.6 and one for 3.0. Although I'm sure there are others, as I just realized from typing "Python" into the tag box.

Should I learn the newest one? Is there any advantage to learning the older version, as I had seen some users show general disapproval with Python 3.0 but they didn't give any reasoning. 

Also, if you know of a better place to start off learning Python, or a program I should be doing it all in, I'm open to recommendations.

Good to meet all of you who reply by the way, I'm going to be spending more and more time in these forums, I'm sure.

---

### Post by worksofcraft on 2010-10-23
I also started to learn Python recently and I discoverd that a lot of usefull libraries are not yet supported for version 3. The one I really needed was gstreamer and so I stayed with Python 2.6

Apparently it will be quite easy to upgrade once you are ready because there is an automatic conversion tool.

---

### Post by ThePhysician on 2010-10-23
Ah, I wasn't aware of there being a conversion tool at all. That will be quite nice. 

I am leaning more towards 2.6 now.

What are you using to learn Python? Like, books or a certain website? And are you writing it in any certain application?

---

### Post by el_heffe on 2010-10-23
I am by no means a programmer.  That having been said, Google has a cool python tutorial I liked.

[http://code.google.com/edu/languages/google-python-class/index.html](http://code.google.com/edu/languages/google-python-class/index.html)

Never hurts to check it out, but the dude in the videos drives me bonkers!  I find it easier to just listen to the videos, not actually watch them.  Good info never the less.  Enjoy!

---

### Post by el_heffe on 2010-10-23
I am by no means a programmer.  That having been said, Google has a cool python tutorial I liked.

[http://code.google.com/edu/languages/google-python-class/index.html](http://code.google.com/edu/languages/google-python-class/index.html)

Never hurts to check it out, but the dude in the videos drives me bonkers!  I find it easier to just listen to the videos, not actually watch them.  Good info never the less.  Enjoy!

---

### Post by worksofcraft on 2010-10-23
> **ThePhysician said:**
> Ah, I wasn't aware of there being a conversion tool at all. That will be quite nice. 

I am leaning more towards 2.6 now.

What are you using to learn Python? Like, books or a certain website? And are you writing it in any certain application?

I wanted to test out my idea for [internationalization of computer speech]("http://code.google.com/p/speaknumber/") and decided to do it in a programming language I never tried before. That way it kept me focussed on what I needed to learn and I just googled bits as I went (e.g [getting started with gstreamer & python]("http://www.jonobacon.org/2006/08/28/getting-started-with-gstreamer-with-python/")). The online [Python language reference manual]("http://docs.python.org/index.html") is indispensable :)

However I haven't had incentive to do much Python since then.

p.s. the conversion tool is called "2to3"

---

### Post by James78 on 2010-10-24
It's simple. You should learn both, however, if you're intending your application to be using third party libraries, most of those are not yet compatible with 3.1, so go with 2.6 in that case. However if you're not going to be using third party libraries primarily, or you have verified they work with 3.1, then go with 3.1.

Both versions work great, but of course 3.1 is better. So go with 3.1 if you can, otherwise you'll have to use 2.6. But there's no issues, security wise or anything related, if you use 2.6 over 3.1.

---

### Post by OgreProgrammer on 2010-10-24
Learning 2.6 isnt going to make 3.1 hard. The changes are pretty minor, and most of them work already in 2.6.

---

### Post by MadCow108 on 2010-10-24
you could also argument the other way round:
you better learn 3.X because the most important stuff of that also works in 2.7.

It doesn't really make a big difference. once you understand the basics of python, learning the differences between 2.X and 3.X is easy.

---

### Post by schryer on 2010-10-24
Greg Wilson has done a great job upgrading the Software Carpentry course.
Here is the section introducing python.  Very good.

[http://software-carpentry.org/4_0/python/](http://software-carpentry.org/4_0/python/)

---


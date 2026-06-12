---
title: "Python/gtk2.0  function improvement advice needed"
date: 2009-12-06
forum: Programming Talk
---

### Post by OgreProgrammer on 2009-12-06
This is my python function for counting the length of a string of words typed into a text entry box. It is terribly slow and delays the display in the text entry. 

Right now the function is being called by the exposure event for the status bar. I think its being called far too often.

The gtk2.0 documentation seems to be doing things in a different way from that of quickly/glade which I am using. I think it assumes one is using C rather than python.

What is a more correct and efficient way for my status bar to watch that text entry box?


```

    def det_count(self, widget, data=None):
        tPost = self.builder.get_object("entry1").get_text()
        tCount = len(tPost)
        Mlen = self.builder.get_object("label1").set_text(str(tCount))

```

I am just getting started with glade and python(through use of quickly), so a little example of signalling between widgets would be excellent. From there I will understand how to progress to things such as drawing areas.

---

### Post by OgreProgrammer on 2009-12-06
Sometimes asking a question phrases it in a way that allows you to consider the problem more carefully. 

After a little reading I solved my problem easily. 

What I had to do was call my function from the entry1 objects changed signal, under gtkeditable. 

That was it. I'm marking this solved.

---


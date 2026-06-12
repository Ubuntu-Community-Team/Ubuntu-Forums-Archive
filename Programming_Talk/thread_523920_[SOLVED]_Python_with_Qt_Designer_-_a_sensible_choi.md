---
title: "[SOLVED] Python with Qt Designer - a sensible choice?"
date: 2007-08-12
forum: Programming Talk
---

### Post by NeillHog on 2007-08-12
Hello!

I came to Kubuntu about three weeks ago and have had a fun time finding out what everything does, how it does it and why. These forums are all that have kept me from returning to Windows. Read some of my other posts and you will see that I have had real problems but now everything works.

On Windows I used a programme called GPSBabel which is a command line programme that converts GPS data backwards and forwards. It also exists in Linux :-) but without the nice GUI that you can call it from.

So I decided that as this was all Linux was missing I better write it myself.

I have read many many threads about programming in Ubuntu and eventually decided to write a Python  utility (I used to write C and still write php but never really got in to C++). The first version was also run from the command line and worked so then I looked for a possibilityto graphically create GUIs as I know from Windows.

At [http://www.cs.usfca.edu/~afedosov/qttut/](http://www.cs.usfca.edu/~afedosov/qttut/) I found a tutorial that explained how to do exactly what I was looking for with QT Designer and PyQt. And it worked. I now have my application working.

But:
1.I can find almost no documentation about developing python programmes with this combination and I am now totally stuck trying to create and use a fileopen dialogue.
2.The editor keeps messing up my inserts. I can find no way to get the editor to act &#8222;python sensibly&#8220; like for example Kate.

This makes me think that I am following a blind alley here and should be maybe going another way.

I would appreciate any encouragement or suggestions before I put a lot of time in to something that can not even open a fileopen dialogue.

Thanks!
Neill

---

### Post by Mirrorball on 2007-08-12
Read the Qt documentation. It's for C++, but the PyQt code will be almost identical, just change the syntax.

---

### Post by NeillHog on 2007-08-12
Thanks. That is what I am trying to do.

I found the following page.
[http://vizzzion.org/?id=pyqt](http://vizzzion.org/?id=pyqt)

and this seems sensible. Only make the pretty GUI in qt designer and do all the coding elsewhere.
I can not get the example to work but I will.

Please give me a tip QFileOpen, KFileOpen or what?
and what do I need to import - sys?

Thanks!
Neill

---

### Post by NeillHog on 2007-08-13
I got the examples working. It was a small but stupid mistake.

And I am a lot happier about the whole concept.
What I did with my first test program was write all the code in QT Designer as well.

What I have now done is just created a GUI in QT Designer with no functionality at all. I then created a python file from this and imported this in to my main python file.

This means that I can change the look and feel without having to touch my code and the code without making any changes to the GUI. Very nice and exactly what I wanted (until someone produces a IDE that offers both functionalities in one.

Neill

---

### Post by 8086 on 2008-11-07
Hi, as you said, not a lot of information on this combination. I would be very interested in testing it out. Care to disclose some example code for us beginners to see how you seperate the code and design?

---


---
title: "flex mxmlc command question with reward!"
date: 2013-02-02
forum: Programming Talk
---

### Post by faceshed on 2013-02-02
solved: mxmlc autocratically compiles all classes in the same directory unless they have named packages (those need imported but name). My problem was due to some special code. I'm leaving the original question here for your enjoyment:

I've been reading guides and stuff for weeks now and I can't figure this thing out. IT'S DRIVING ME CRAZY!!!

I can't get mxmlc to compile more then one .as file into a .swf.
The first one to give me a working command for mxmlc to compile 3 .as type files into one .swf file will be granted, there name or a phrase of there choice, made into THREE bad haiku poems _and_ a poorly drawn person saying poorly worded Norwegian insults.

I might add in more junk for the winner depending on what I can think of and if I have time.

---

### Post by faceshed on 2013-02-03
The first correct answer will also get there name in the credits of my first published flash game under the title "mxmlc linux terminal command line script coordinator" or a title of there choosing if we can work something out.

---

### Post by iMac71 on 2013-02-03
perhaps the reply in the following topic might help:
[http://forums.adobe.com/message/4184424?tstart=0#4184424](http://forums.adobe.com/message/4184424?tstart=0#4184424)

---

### Post by faceshed on 2013-02-03
Sounds like he's talking about the ```
-compiler.source-path+=
``` option, but I haven't managed to get that to do anything more then the exact same thing as if I didn't use it or give me errors for an incorrect path.

---

### Post by faceshed on 2013-02-07
I think it's about time to add more junk prizes!

If you solve my problem I'll tell you a cool trick I learned about how to swap 2 variables without using a temp, it works in c++, c, java and many other lower level languages. Don't google it because.... it would spoil my leverage.

Also a lot of online services offer rewards for getting others to sign up for it so if you solve my problem I'll sign up for 3 things and list you as the person that recommended me to it. I'll only do this if it's something free, but I will be willing to spend some time on it if it's required or asked for.

The list so far is:
A stupid drawing.
Three bad haiku poems.
Your name in the credits of my first game.
Three try outs of online things with you as my recommendation.
And a cool programming trick you can find on google.

---

### Post by faceshed on 2013-02-08
I'm going to claw my freaking eyes out, but I did it!
So I'm going to cash in all three haikus now:

I hate you flash,
and those stupid arrays of yours.
Learn 2 data type shiz.

Computers are fun.
They make me feel wonderful.
Then I turn it on.

I wasted a month.
With nothing to show for it.
Except some haikus.

The answer is "mxmlc [main].as". That's it! Turns out I wasted a month on this because my preloader class didn't compile the same with the new environment.

---


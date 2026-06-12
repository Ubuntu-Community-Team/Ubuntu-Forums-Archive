---
title: "KDevelop killed my arrow keys"
date: 2011-08-10
forum: Programming Talk
---

### Post by PenguinLust on 2011-08-10
That's right, delete and backspace, too. I just can't use them in the editor, but most other keys seem to work. If I open one of the dialogue boxes I can use them in the textboxes, but I can't use them in the editor. Even restarting my system didn't fix anything. I have no idea what could have caused this. There wasn't anything noteworthy about what I was doing when I had this problem.

I installed it from the less supported repository, so it's 4:4.0.0-0ubuntu1 (lucid-backports). My system is 10.04.

Maybe the solution is a different version of KDevelop. This build has frustrated me on a number of occasions, but this one takes the cake.

---

### Post by PenguinLust on 2011-08-10
Oh this just keeps getting better and better. I can fix this problem by going back to the default shortcut profile. Unfortunately, I made my own shortcut profile because the bloody shortcuts I'd assign kept resetting!!!!!!!!!!!

So my question about a better KDevelop stands, because I'm ready to put this monitor through the window.

---

### Post by Ravenshade on 2011-08-10
What are the advantages of KDevelop anyway? I'm not used to IDE's (I usually use gedit) so I'm currently working with Code::Blocks, seems really functional nowadays. (compared to how it used to be ¬_¬).

---

### Post by PenguinLust on 2011-08-10
What sorts of things do you develop? I'm a C++ developer and previously it was great for finding definitions of things, or adding members to classes and all kinds of things like autocompletion.

But it seems that the answer is just to go back to good old 3.5. Either 4 is a mess or the version of 4 that comes with Lucid is a mess. [These directions]("http://www.elphel.com/wiki/kdevelop#Installation_of_KDevelop_3.5_on_.28K.29Ubuntu_10.04") worked for me.[URL="http://www.elphel.com/wiki/kdevelop#Installation_of_KDevelop_3.5_on_.28K.29Ubuntu_10.04"]
[/URL]

---

### Post by adymo on 2011-08-11
Make sure you did not activate "vi mode" in the editor by accident. It's under Edit -> Advanced -> VI Input Mode.
I don't think ubuntu has vi mode enabled by default, but if it does, then it's their bug for sure.

PS: going back to 3.5 is not a solution, c++ in 4.x is significantly more stable and feature-complete.
PPS: you'd better ask in kdevelop mailinglists about such things, I found this question only because I've subscribed to google alerts for "kdevelop" keyword.

---

### Post by GeneralZod on 2011-08-11
(adymo is a KDevelop developer, BTW, so he's worth listening to ;))

---


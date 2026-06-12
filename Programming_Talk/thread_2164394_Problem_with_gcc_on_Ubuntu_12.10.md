---
title: "Problem with gcc on Ubuntu 12.10"
date: 2013-07-31
forum: Programming Talk
---

### Post by seriouslylinux on 2013-07-31
I don't know if I'm in the right forum but I will describe my problem anyway.  I am using Teach Yourself C to learn the C language.  I am using the Netbeans 7.3.1 IDE and the gcc compiler from the Ubuntu Software center.  Three weeks ago everything was working fine.  There have been some updates on Ubuntu 12.10 in the meantime and I haven't been in the IDE for three weeks because of other personal matters.  Now when I try to compile my source, none of the keyboard functions work: scanf, gets, or fgets.  In addition to that the Netbeans IDE seems to hang when I try to go to the project properties section to check the linkers.  Is this a bug with Ubuntu 12.10 or something else?

---

### Post by GwL3eNC on 2013-07-31
Hallo,

evtl. you have to give a bit more information. What means work not. Do you get an
error message during compilation or linking? You can try another IDE to find out
that Netbeans is guilty. Try Eclipse or DevC++. There are much you can choose.

I would also try to reeinstall some packages 

sudo apt-get install --reinstall build-essential 

Keep learnig C. It never dies!

---

### Post by Tony Flury on 2013-08-01
I would also suggest checking that the code compiles without using an IDE at all - i.e. from the command line. That way you can actually see the error messsages if any. It also helps in future to understand what the IDE is doing under the skin.

I would go so far as to suggest that a beginner should not use an IDE - it gets in the way of learning.

---

### Post by seriouslylinux on 2013-08-02
Thank you both for the reply.  I will try what you have suggested and see if it makes a difference.  If I have further trouble or different info I will pass it on.

---

### Post by seriouslylinux on 2013-08-11
HI,
I finally had a chance to try the gcc compiler in the terminal and it is working so my problem is with Netbeans IDE.  I think I will take Tony's advice and learn the language in the terminal and editor rather than using an IDE.  I am not new to programming just new to C.  Thanks for the advice and the answer.

---


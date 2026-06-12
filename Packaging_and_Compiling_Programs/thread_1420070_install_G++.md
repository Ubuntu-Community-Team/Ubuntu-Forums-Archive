---
title: "install G++"
date: 2010-03-02
forum: Packaging and Compiling Programs
---

### Post by antobbo on 2010-03-02
Hi guys, I wonder if anybody can help me to get G++ running. I installed on my machine (I run sudo get-app install build-essential ) and then sudo apt-get install g++...but how I run it? Ah, I am relatively new to ubuntu...
thanks

---

### Post by matthew.ball on 2010-03-02
Have a read of this: [http://www.programmingforums.org/thread7219.html](http://www.programmingforums.org/thread7219.html)

Edit: You should also look into Makefiles - an easy tutorial can be found here: [http://www.opussoftware.com/tutorial/TutMakefile.htm](http://www.opussoftware.com/tutorial/TutMakefile.htm)

---

### Post by antobbo on 2010-03-03
Hi thanks for that. I had a look at the first tutorial which is ok, but it doesn't actually explain how to use the flags so I got a bit confused. Can you suggest an alternative, a tutorial that explains everything? I am used to Visual C++, but I want to use linux and not windows. The second tutorial, do I need this makefile thingy? what's that for?
thanks

---

### Post by matthew.ball on 2010-03-04
How far into the tutorials did you read? Both explain your questions.

---

### Post by antobbo on 2010-03-04
hi there, well I have just read the compiler bit, on the main page, but to be honest that's it because there are bits that are not clear like the ./a.out, and it is not explained why you do this. The thing is that, as I mentioned, I have been using Visual C++ so far, so I am used to it, and this seems quite hard. The thing is that I want to use linux and G++ but I would like some tutorial where everything is explained, or something like step by step if available.

---

### Post by matthew.ball on 2010-03-04
Not even a quarter down the page of the g++ tutorial and the text says:
> Cool! We compiled a C++ program ^_^ but many question still lie unanswered such as why it is called a.out and how to change that name

Further down he explains both how to use compilation flags, and how to rename executable files during compilation. These are exactly your questions.

If you're seriously intending on doing some Linux development, chances are you're going to have to read something.

Maybe try reading [this]("http://pages.cs.wisc.edu/~beechung/ref/gcc-intro.html") tutorial, though I think it's going to be roughly the same.

---

### Post by antobbo on 2010-03-09
Hi ya,
thanks for that, I will have a look at the other one.
I know, I read the old one but I still don't understand what the ./a.out is. ANyway, as said I will try the other one. If I have more questions after that, can I post them here on this forum?
thanks

---


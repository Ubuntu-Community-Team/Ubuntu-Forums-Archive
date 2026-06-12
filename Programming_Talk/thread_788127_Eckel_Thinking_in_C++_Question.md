---
title: "Eckel Thinking in C++ Question"
date: 2008-05-09
forum: Programming Talk
---

### Post by Quailman on 2008-05-09
Hello! I have been teaching myself C++ for about half a year now. I started out with John Kopplin's Computer Science Lab. Now I am working my way slowly through Bruce Eckel's Thinking in C++. I've hit a few walls on some of the example programs in the book since I don't have anybody to go to for help, but I've been able to work out my problems for the most part. However, I am pretty well stuck on one of the problems right now and I was hoping someone here would be able to guide me.

Your sticky on posting homework problems has scared me from posting my question for a day and a half, but I am at the point where I must ask ;). I don't expect to be spoon fed, but a bit of guidance would be appreciated. Anyway, on to the problem.

I am stuck on example 16 in chapter 4.
[http://www.codeguru.com/cpp/tic/tic0059.shtml](http://www.codeguru.com/cpp/tic/tic0059.shtml)

Here is a link to the Stash program referred to in the question:
[http://www.codeguru.com/cpp/tic/tic0057.shtml](http://www.codeguru.com/cpp/tic/tic0057.shtml)

Ok, I have spent at least 2-3 hours trying to solve this, all to no avail. My main difficulty is in understanding exactly what Eckel is asking me to do. When he referrs to changing the "underlying data structure" of Stash, does he mean to use a vector instead of a struct to construct a Stash-like object, or does he mean to use a vector inside of the struct instead of the data members in the original Stash struct?

Not really knowing what to do, I tried both approaches. I thought the first was the most logical, but I kept getting a strange compiler error for my code before I even got far. The second approach yielded the same results. 

If someone will clarify for me what they think Eckel is asking I will give this another shot. I am very persistent, so even if I hit another wall I will probably work another 2+ hours trying to solve this. The only thing is, I don't want to waste that much time on an aproach that isnt going to work anyway. I know learning programming is all about trial and error, but that much error is unacceptable to me ;). 

Sooooo, if someone could answer my question from paragraph 3, I would greatly appreciate it. I will try to solve this problem using the information you give, and I will post my code if I continue to have aneurysm-inducing problems. I would have posted my other code, but I was so frustrated I scrapped it xD.

Sincerely,

Quailman, the lost programming noob.

---

### Post by LaRoza on 2008-05-09
I didn't follow the entire book, just what you referenced.

This is the underlying data structure of that program, a linked list.
[php]
//Snipped from Stack.h
struct Link {
    void* data;
    Link* next;
    void initialize(void* dat, Link* nxt);
  }* head;
[/php]

Alter the code of this struct to use a vector. That is what I got from it, I see no references to "Stash" in the book pages I read.

Is this your first language?

---

### Post by Quailman on 2008-05-09
Oops, I'm sorry. The correct link to the Stash struct is:
[http://www.codeguru.com/cpp/tic/tic0052.shtml](http://www.codeguru.com/cpp/tic/tic0052.shtml)

Thanks for your response! Even though I gave you the wrong link I still think I can get the program to work from what you gave me.

And yes, C++ is my first language. I know it is supposed to be more difficult for a beginner to learn than, say Python, but I am a glutton for punishment xD.

---

### Post by LaRoza on 2008-05-09
> **Quailman said:**
> Oops, I'm sorry. The correct link to the Stash struct is:
[http://www.codeguru.com/cpp/tic/tic0052.shtml](http://www.codeguru.com/cpp/tic/tic0052.shtml)

Thanks for your response! Even though I gave you the wrong link I still think I can get the program to work from what you gave me.

And yes, C++ is my first language. I know it is supposed to be more difficult for a beginner to learn than, say Python, but I am a glutton for punishment xD.
This seems to be the data structure to alter in that case:
```

unsigned char* storage;

```

C++ was my first language also, I never did fully get it until I learned many other languages.

---

### Post by Quailman on 2008-05-09
Thanks very much for your help!

After I finish Eckel's books I'll probably try to pick up another language. I don't want to sell myself short until I've given C++ all I've got though ;).

---

### Post by LaRoza on 2008-05-09
> **Quailman said:**
> Thanks very much for your help!

After I finish Eckel's books I'll probably try to pick up another language. I don't want to sell myself short until I've given C++ all I've got though ;).

I hope it helps you do the exercise. 

C++ won't stop until you have given all you've got, it is like a vampire with an addiction.

Just kidding of course, you got this far, might as well keep going.

---

### Post by Quailman on 2008-05-09
lol ;)

I know you guys hate people asking what the "best language" is, but do you have a language you would recommend learning after I get thoroughly disgusted with C++? I know this is the proverbial noob question and that it really depends on numerous personal preferences, but what do you think would be most helpful for all around programming knowledge? /noob (I know I just lost all credibility asking this question :D )

---

### Post by LaRoza on 2008-05-09
> **Quailman said:**
> lol ;)

I know you guys hate people asking what the "best language" is, but do you have a language you would recommend learning after I get thoroughly disgusted with C++? I know this is the proverbial noob question and that it really depends on numerous personal preferences, but what do you think would be most helpful for all around programming knowledge? /noob (I know I just lost all credibility asking this question :D )

Since you have shown extreme diligence in your studies (trying for hours on a single exercises) I will give an honest answer.

I suggest after you feel you are ready to learn another, I suggest you chose for yourself. My intial reaction would be "Python", but that is just me. You can browse my wiki and find a language that intrigues you. Lars found Lisp after C++, I found Python. 

For all around programming knowledge, I have suggestions on my site. It is similar to what others would say. Basically, it is learn a "high level language", a "low level langage" and a "different paradigm". Python -> C -> Lisp is what I would personally recommend. However, that is just general advise. Perhaps you could make a better move by browsing my wiki to see what I have found. If you have no job requirements, I recommend staying away from Java and C# for now. You will need time to heal after C++.

On my Learn to Program site, I have a [[color="blue"]Language Selector[/color]]("http://laroza.freehostia.com/home/apps/programming/index.php") that I programmed. It may be helpful.

---

### Post by Quailman on 2008-05-09
Thanks a lot for the info! I will make good use of it. Who knows, maybe some day I will become a useful member of this community... :)

---


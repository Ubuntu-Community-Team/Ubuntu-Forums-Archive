---
title: "newbie in c asking for adwise"
date: 2008-06-10
forum: Programming Talk
---

### Post by cmay on 2008-06-10
hi.
i am new to programmering and linux.
 i want in time  (say over six or twelwe years from now) if possible at all
 to learn something that has to do whit sound communication and language . that is teching tools and plugins music applications and if i ever get to be good in programmering maybe something for peopel sligtly handicapped  like esound and orca. 

i am coding everyday and my eyesight are very bad at times ,which explains the esound and orca idea,
i think of this not as a developer or proffesional but just as a hobby if  can learn these things in time of course.

 i learn c now as i found 3 years ago a book in the library that i read whitout any background knowlegde about programmering at all. it was the k&r c programmering language second editon.
 so i went around the different tutorials i could find on the internet  and therefor m i learned over the next couple of monht the very basics of turbo pascal 7.0 (free pascal)

 then i used on and of devc++ and wxdevc++ when i had time .
 and in the end it was only to gain insight in programmering enough to start learning c. 

i have bought the same books as i know are used here in denmark for educating programmers and ohter computer related educations 
and last night i comleted every singel lesson and assigment in the book.
 (i had a littel help from this forum whit filehandling)

 now i feel i have to learn c other than the syntaxt which i from my book proberly  learned poorly i think now after reading and following the gnu c tutorial link in the sticky tread.
my book was not a good book for learning anything usefull compared to tutorials i found on internet from the gnu linux authors.

i wanna ask for the most easy sources and programs from linux to study .
wc grep and these kind of programs .
 what source packages should i install.
are there other small programs i can learn from reading.
and then  i would be very happy if someone have links to other tutorials that are fun and i can learn from. 


thanks for reading this and thanks to this forums for the help so far.

---

### Post by KingTermite on 2008-06-11
I'm not familiar with any programs in particular to know if their source is easy to read and understand. I could recommend though, when you are ready to start learning some sound technology to download source of a good sound program (Audacity maybe??) and start examining its source code.

---

### Post by nvteighen on 2008-06-11
1. First, you should activate the sources repositories. Go to Synaptic, Configuration->Repositories. Check the "Source code" (or similar) box.
2. Then, if you want the source for package x, open a terminal and type:
```

apt-get source x

```
No sudo needed. This will download the source to the current folder.
3. There it is!

The problem I see is that these sources are highly complicated, usually...

Source for grep, wc, cat, etc. are included in the coreutils package.

---

### Post by cmay on 2008-06-11
hi.
thanks a lt for the reply.
i have read trough the forums and found a link to a tutorial on how alsa works.
 so i wanna see how this works first maybe if i could understand how that works .
any way i am very gratefull  for the input and i will install the coreutils
source once i had my morning coffee.
thank you.

---

### Post by cmay on 2008-06-11
> i have read trough the forums and found a link to a tutorial on how alsa works.
so i wanna see how this works first maybe if i could understand how that works .
this makes no sense !
 i can see i did not have my morning coffee when i wrote this.

thanks for the help i have found the sources i was looking for and i start to read tonight when i have time.

---

### Post by Kinnza on 2008-06-11
hey cmay,
as a programmer i wanna say this: reading source code can ofcourse help you learn, but its is definnatly not enough

what i suggest is this
first, dont jump from language to language
if you wanna study C, focuse on that
other languages have a very similar syntax and are easy to move to once you know how to program.

second, pick a project to write. just think of a small application that you wish to have, if you cannot think of one just make one up, just for the practice. and just start to write it
that is the only way you can really learn how to program
while you program it, you will have questions on how to do this and that, then you turn into some online help, look in similar source code and etc.

i hope this helps you out :D

---

### Post by cmay on 2008-06-11
thanks.
its true what you say.
i also dont jump no more after i first found out there was a trap hidden there. 
i consider my experience as stepping stones towards the one goal i was aiming to achieve.
 maybe i overdid it at a time but then i also learned that.
 but its a really good adwise you give.
i wanna start by writing some small things .
thats the funny thing about linux. a lot of the small programs like cat and grep wc and so on is as far as the one program it selve not that impressive but put all of them togheter and then its impressive the way they support each other. 

thanks for the input .

---

### Post by Kinnza on 2008-06-11
no prob
and good luck

---

### Post by pmasiar on 2008-06-11
Is some CompSci program in some school (which I bookmarked on my other computer I think) there was experiment: Teach students C++ or Java directly, and teach Python first for 3 months, then Java. Funny thing happened: because students were able to grasp basics of programming in Python in 3 months, they were able to get father in Java in 7 months than doing it 10 months.

If you plan to become programmer, you will learn more than one language, so it makes sense to start with simple and useful one like Python. And there might be music apps in Python too: non-professional programmers like Python more than C. 

Of course if the only thing you plan to do is to understand single source code of single program, you need to learn that language and nothing else. But I doubt this is the case - and it would not work anyway.

---

### Post by cmay on 2008-06-11
> Of course if the only thing you plan to do is to understand single source code of single program, you need to learn that language and nothing else. But I doubt this is the case - and it would not work anyway.

why do you doubt that is the case.?
i already wrote in the first post that i only see 
this as a hobby and nothing more.

---

### Post by pmasiar on 2008-06-11
> **cmay said:**
> why do you doubt that is the case.?
i already wrote in the first post that i only see 
this as a hobby and nothing more.

because becoming competent in a single (and non-simple) language like C requires much more effort (in time) than hobby warrants.

But I re-read post#1, if you have poor eyesight, I am not sure how so sight-related occupation as programming makes sense. But certainly, language like Python which uses significant whitespace will be less optimal than say C.

I'll try to dig you out some usability-related links. You may want to try Project Euler - plenty of tasks to solve.

---

### Post by cmay on 2008-06-11
>  
But I re-read post#1, if you have poor eyesight, I am not sure how so sight-related occupation as programming makes sense. 
i have as a hobby also studied pshykology in the last twenty years. 
before i was retired and is permantly out  the working mans world
 so i get bored and unhappy if i am supposed to just sit and do nothing. so there you go-> in time say six or twelve years to learn c and maybe even help someone as the primary motivation. if i can do that of course.
 i have a kidney disease so i doubt very much that i could even work as full time programmer anyway.
but to live and learn is what is important isent it
> 
I'll try to dig you out some usability-related links. You may want to try Project Euler - plenty of tasks to solve.

thanks.:)

---

### Post by nvteighen on 2008-06-11
> **cmay said:**
> 
but to live and learn is what is important isent it

Of course! Go ahead!

---

### Post by cmay on 2008-06-11
> 
Of course! Go ahead!
working on it :)

---

### Post by pmasiar on 2008-06-11
OK, following on my promise:

There is whole ubuntu subforum for assistive technologies: [ Assistive Technology & Accessibility](http://ubuntuforums.org/forumdisplay.php?f=145) - you may want to join as tester and later developer, they may know better what exactly is the state of the art - I don't follow it (yet?). There is also [Accessibility page](http://www.ubuntu.com/products/whatisubuntu/accessibility) on Ubuntu homesite. I have no idea what are your needs, but those are projects (and people) to look at, IMHO. You may know about them, sorry then.

I found also [Gnome magnifier](https://lists.ubuntu.com/archives/ubuntu-accessibility/2006-December/001587.html) discussion.

Re tasks to solve: [http://www.spoj.pl/](http://www.spoj.pl/) [http://projecteuler.net/](http://projecteuler.net/) will keep you busy for a while. Enjoy! :-)

---

### Post by cmay on 2008-06-12
thank you.
i gonna see what this is and of course see if i
 can be a beta tester on some thing.
 maybe something needs a translator. .

thank you  for this .

---


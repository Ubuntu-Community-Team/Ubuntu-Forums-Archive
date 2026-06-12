---
title: "Learning Fortran"
date: 2007-07-30
forum: Programming Talk
---

### Post by LaRoza on 2007-07-30
I am starting to learn Fortran, and am wondering if anyone has any tutorials, links, or suggestions. I am using XP at school now, but I will be using Ubuntu at home, so Linux specific advice is good.

Also, any Windows advice would be nice also, I like to be able to program in both platforms.

---

### Post by mips on 2007-07-30
I googled FORTRAN Tutorial and it gave me a gazillion hits.

---

### Post by LaRoza on 2007-07-30
> **mips said:**
> I googled FORTRAN Tutorial and it gave me a gazillion hits.

Ah, that is part of the confusion, FORTRAN has many manifestations it seems, and all of them slightly different. It has been around for a while, and was once the dominant language. I am studying Fortran 77 now, although that isn't the most recent version.

I sifted through the search results, after posting and found a few good sites that I saved--page by page. (I don't have an internet connection at home, hence my address)

Well, thanks for looking. I already got a few tools for Windows, I know Ubuntu has it in the repos, so I didn't look. 

It is an interesting language, I see now why it caused such an uproar when it came out.

I was hoping a Fortran programmer would answer, like when a Python or C question comes up.

---

### Post by Taum on 2007-07-30
Is this part of a College course or other institutionalized class, or are you learning for fun and profit?

---

### Post by xtacocorex on 2007-07-30
LaRoza, do you have a reason to learn F77? I only say this since it is more complex than F90/95 with the fixed format and trying to remember to start on column 7 get's annoying IMO - although it does help if you look at old FORTRAN codes.
 
I have a really good syntax site bookmarked, but somehow it didn't make my del.icio.us account, I'll put it up here when I get a chance tonight.
 
Feel free to PM me if you need help with FORTRAN. I do hang around in #ubuntu-programming on freenode, so if you want live help, I'm bound to be around there.
 
Use cygwin for Windows; all the FORTRAN compilers for that platform cost $$$. Or, you can get gfortran as a Win executable; there is another one called g95, but I can't remember the state of both of them.
 
As for tutorials, I learned FORTRAN as part of my major in college, brainwashed in to me from day one and I learned from a single course book - *Introduction to FORTRAN 90 for Scientists and Engineers*. I will say that you'll program slightly different programs than you would with C++/Python since the language is made for math. The newer standards will let you do more C++ like stuff.
 
One way you could go about learning FORTRAN is finding some math problem you can't easily solve by hand and developing the algorithm in FORTRAN to solve it. Granted that's trial-by-fire, so maybe mess with simple loops and arrays before doing that. 
 
Here is a some simple code of mine that I made for a friend; it rotates a set number of points (x&Y coords) by a given angle.  This will be a slightly more real world program than *Hello World!* that you could learn from.
[http://robert.wolterman.googlepages.com/rotate.f90](http://robert.wolterman.googlepages.com/rotate.f90)

---

### Post by roncrump on 2007-07-30
> **LaRoza said:**
>  I am studying Fortran 77 now, although that isn't the most recent version.

Can I ask why you are learning F77? You would be much better off to learn Fortran 95 (nb not much difference from Fortran 90), even if you need access to old Fortran 77 code (newer versions of Fortran compile Fortran 77).

There are a few tutorials listed [here]("http://www.fortran.com/tutorials.html") which may be of use.

Ron.

---

### Post by jss43 on 2007-07-30
Fortran 90/95 is *much* nicer to write and understand than 77.  The added implicit functions, modules and derived types make coding much easier.  Also, the free formatting is more aesthetically pleasing... :-)  If only I didn't have to work with incomprehensible, poorly commented legacy code! :mad:

I haven't used gfortran much as I ran into a long existing bug almost straight away. g95 is nice, and the developer fixes bugs reported bugs quickly.

I learnt from doing and googling when I couldn't do something or asking friends.  The man style pages are useful, but initially incomprehensible!

Something that helped me was to choose a non-trivial project, ask for help along the way and then get someone more experienced to critique the code when it's done.  

Other hints: comment lots and use source code management (seriously,  you'll wonder how you got by without it, if you're not already a convert).

---

### Post by xtacocorex on 2007-07-30
LaRoza, here is the link I promised: [http://www.pcc.qub.ac.uk/tec/courses/f90/stu-notes/F90_notesMIF_1.html](http://www.pcc.qub.ac.uk/tec/courses/f90/stu-notes/F90_notesMIF_1.html)  It is for F90, but everything is pretty consistent with F77, with the exception of using numbers for do-loops.

Definitely learn F77 first if you choose, it could come in handy one day knowing the fixed format stuff of FORTRAN.  Didn't mean to push for a change in your learning direction.  I had to pick up F77 formatting after F90 and it caused a few problems trying to get the old codes to compile.

---

### Post by jeremytaylor on 2007-07-31
Hi 

Learn 90/95, it's a much nicer language than 77. 

You might find these course notes useful
[http://www.liv.ac.uk/HPC/F90page.html](http://www.liv.ac.uk/HPC/F90page.html)

If you're not doing commercial work then the linux versions of the intel compilers are free and very good. gfortran is getting better all the time.

My recommended book is fortran 95/2003 explained by metcalf, reid and cohen. Not great to work through but a very useful reference.

Jeremy

---

### Post by LaRoza on 2007-07-31
Thanks everyone! xtacocorex, for the link, and possible future help :D and everyone else.

To answer the questions:

0. I am learning it for Fun, I like to learn a lot of languages and am entirely self taught.
1. For Windows, and Linux, I am using GFortran and G77.
2. As to why I am learing Fortran 77, goto 0. As to why I am not learning Fortran 90/95, give me time, I'll do that soon :D, possibly today. (I learn really fast, and have no trouble with learning more than one language at a time, and I enjoy it, which is key)
3. I already adapted to the fixed format, and I didn't feel any hinderance. Being a Python fan, it was kind of nice to have such rules.

Thanks for all the help.

By the way, I got GFortran working on XP, but it won't work on Vista, I'll figure it out, but can any one tell me, while I am at school (and away from my computers), what environment variables are needed? (Other than PATH=C:\gfortran\bin)

-EDIT Is fortran at all case sensitive? Should I use capitals or lowercase for key words?

---

### Post by xtacocorex on 2007-07-31
FORTRAN is not case sensitive, I just got used to typing everything in all caps since it looks cooler IMO.

The fixed format will work for F90, so make note of that.  

I haven't tried gFortran on Vista, mainly because I don't have a Vista machine, so I can't help with the environment variables.

---

### Post by LaRoza on 2007-08-01
> **xtacocorex said:**
> FORTRAN is not case sensitive, I just got used to typing everything in all caps since it looks cooler IMO.

The fixed format will work for F90, so make note of that.  

I haven't tried gFortran on Vista, mainly because I don't have a Vista machine, so I can't help with the environment variables.

Thanks for the info.

I gave up on Vista, it isn't worth the trouble.

---

### Post by jdrodrig on 2007-08-11
Just for completeness (I did not see it mentioned), Sun just released their SunStudio 12 for Linux, available at their website. The IDE is Java based so it is not superfast, but it is useful if you like to do extensive debugging...on Optetron machines it generates faster code than Intel's as far as I have been able to test.

I learned from Chapman Fortran 90/95. Numerical Recipies for Fortran has been quite useful for me too (it is accesible online).

My impressions, for serious calculations, Fortran gets the job done pretty fast. Just need to be careful with those double_precisions, quad_precisions concepts.

Welcome to the Fortran World!

---

### Post by gnuman on 2007-08-12
If you like learning comp languages for fun, tackle the emulator for Charles Babbages Analytical Engine, and Ada Lovelace's programs for it.  This is going WAAAAY back:

[http://www.fourmilab.ch/babbage/contents.html](http://www.fourmilab.ch/babbage/contents.html)

I'm joking a little, but I also find it fascinating to go back and see that in the 1850 the concepts of loops, variables, subroutines were all being developed.  Check out the source code on that site :)

You never know where this knowledge could lead.  Maybe one could end up programming a little mechanical nano computer using these methods--that is, if you don't lose the little thing somehow.....

---


---
title: "help with segmentation error"
date: 2008-05-18
forum: Programming Talk
---

### Post by akimatsu123 on 2008-05-18
Hi, can someone please tell me why this little snippet of code is generating a segmentation error? I'm pushing an integer in the end of an integer vector why can't i do that?...

```

cin >> num;
vector<int> remainders;
do
{
	remainders.push_back(num % 36);
	num /= 36;
} while(num / 36 != 0);

```

---

### Post by Lster on 2008-05-18
Can you post the whole code? I'm not too sure of C++ myself but may be able to help if you do.

---

### Post by supirman on 2008-05-18
I was able to run it with no errors.  Perhaps post more of the code so we can help diagnose the issue.

---

### Post by JupiterV2 on 2008-05-18
Code runs for me also. As the above posters have suggested, perhaps include the rest of the code so we can help diagnose the problem. Also, consider copying the output showing the segfault.

---

### Post by dempl_dempl on 2008-05-18
You don't need to post your code, I'm so smart that I can diagnose it from here :D




Here are the couple of possible scenarios:

(1 case ) n just might be **float** . If it happens to be  the case, I'll kill you :twisted: .

-----------------------

(2 case) More likely Nothing to do with you at all :)  . Try 2a and 2b 

--------
(2a) Do you get  Segmentation Fault for **any** program you try to compile or for just this **particular** one? 
 
If it throws with **any program you try to compile **

-->>There might be an error with Linking to the libraries.
 Reintall libc, g++ , gcc , includes , sources etc.  
That usually helps. 

-----
**else, If** it throws only with this particular program, **delete  program ( .exe :)  ) , object files , etc. ** and recompile all over again. 


If you use Kdevelop, you can just  go to  Project->Clean  ( or Project->DistClean ) , and it'll do that for you.
Then rebuild the program with F8 .



Cheers!




-----------------

---

### Post by dwhitney67 on 2008-05-18
See my comments below...

> **dempl_dempl said:**
> You don't need to post your code, I'm so smart that I can diagnose it from here :D

Here are the couple of possible scenarios:

(1 case ) n just might be **float** . If it happens to be  the case, I'll kill you :twisted: .

[COLOR="Blue"]NOPE!  A float will be truncated to form an (unsigned) integer.  If num is declared to be a float/double, then an error would be generated to indicate that a modulo operation is not permitted on such type. [/COLOR]

-----------------------

(2 case) More likely Nothing to do with you at all :)  

[COLOR="Blue"]That's it!!!  You are such a genius.  Unfortunately, it does not help the OP whatsoever with a comment like this.  IMO, it is better not to make any comment that is not helpful.[/COLOR]

--------
(2a) Do you get  Segmentation Fault for **any** program you try to compile or for just this **particular** one? 
 
If it throws with **any program you try to compile **

-->>There might be an error with Linking to the libraries.
 Reintall libc, g++ , gcc , includes , sources etc.  
That usually helps. 

-----
**else, If** it throws only with this particular program, **delete  program ( .exe :)  ) , object files , etc. ** and recompile all over again. 

[COLOR="Blue"]... And watch the program seg fault again.[/COLOR]

If you use Kdevelop, you can just  go to  Project->Clean  ( or Project->DistClean ) , and it'll do that for you.
Then rebuild the program with F8 .

Cheers!
-----------------

[COLOR="Blue"]Really, what is needed is for the OP to post the entire source code, so that someone here on the forum can compile it, run it and indeed determine if the seg fault is occurring.  If it is, then it would be easy to find where by using the gdb debugger.[/COLOR]

---

### Post by dempl_dempl on 2008-05-19
> 
NOPE! A float will be truncated to form an (unsigned) integer. If num is declared to be a float/double, then an error would be generated to indicate that a modulo operation is not permitted on such type.


Yeap, my error.   modulo tricked me :)   .

> (2 case) More likely Nothing to do with you at all

That's it!!! You are such a genius. Unfortunately, it does not help the OP whatsoever with a comment like this. IMO, it is better not to make any comment that is not helpful.


I meant, the previous one did not work, try **2a** and **2b**
.

I'll edit the post and clarify that  now.. thanks for pointing that out .

> 
... And watch the program seg fault again.


This is actually known to work, actually it's the workaround most of the time, provided that is, the code is correct. Compilers mess up from time to time. You know , Gcc has bugs  :)  .

---

### Post by johnl on 2008-05-19
> **dempl_dempl said:**
> 
This is actually known to work, actually it's the workaround most of the time, provided that is, the code is correct. Compilers mess up from time to time. You know , Gcc has bugs  :)  .

Generally you'll run into this when you change the definition of a C++ class in a header (ie, add an inline function, more members, etc)  and some already compiled object files don't pick up on the change.  As a result, different object files may have different ideas about the size and layout of your class, which can never end well.

---


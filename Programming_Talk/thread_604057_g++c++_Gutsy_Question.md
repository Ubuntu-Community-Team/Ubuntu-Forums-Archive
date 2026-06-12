---
title: "g++/c++ Gutsy Question"
date: 2007-11-05
forum: Programming Talk
---

### Post by vladan.b on 2007-11-05
Hello!

I am a new Ubuntu Gutsy 7.10 user (loving it!).

I have a question about the version of g++/c++ that I got from the repository by apt-get (version info follow):

```

Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.1.3 --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)

```

Using this version of g++/c++ compiler and version 3.4, by compiling and running the same cpp file I get answers that are totally different.  Version 4.1.3 gives garbage, while 3.4 works well.

I tried version 4.2 as well, getting the same results as with 4.1.3.

Is it possible that the files in the repository are not up to date and that it may be the compiler issue?  I would not mind using the older version either, but for whatever reason it does not like MPFRCPP library (for multiple precision calculations).  Note that the problems occur when compiling the file only with regular precision, not extended.

Thank you in advance,
vlad

---

### Post by vladan.b on 2007-11-06
Could an Admin/Mod move this post in the Absolute n00b group, if there is one.  Thank you :p

---

### Post by bruce89 on 2007-11-06
> **vladan.b said:**
> Could an Admin/Mod move this post in the Absolute n00b group, if there is one.  Thank you :p

Well done, I've reported this.

Perhaps the program is at fault.

---

### Post by vladan.b on 2007-11-06
> **bruce89 said:**
> Well done, I've reported this.
Perhaps the program is at fault.

Many thanks.

---

### Post by Bachstelze on 2007-11-06
@bruce89 : There's no rule that forbids calling oneself a n00b...

@vladan.b : I don't think this would fit well in Absolute Beginners Talk (an Absolute Beginner doesn't even know what gcc is ;)). Would you llike to have it moved to Programming Talk instead ?

---

### Post by vladan.b on 2007-11-06
HymnToLife: That would be great!  My apologies for sticking it into wrong place.

---

### Post by Bachstelze on 2007-11-06
Okey dokey, done :)

---

### Post by bruce89 on 2007-11-06
> **HymnToLife said:**
> @bruce89 : There's no rule that forbids calling oneself a n00b...

Oh, I am a massive idiot.

---

### Post by hod139 on 2007-11-06
You will have to show us the offending code.

---

### Post by vladan.b on 2007-11-06
> **hod139 said:**
> You will have to show us the offending code.

Easier said than done unfortunately...  It is a total of 4 files containing the new method my supervisors work on (solutions of ordinary differential equations).  If there was a place that I can upload it, or perhaps have someone using 7.10 Gutsy that could try it for me, I would not mind emailing the 'offenders'.

Again, the code offends only on g++ >= 4.1.3.

---

### Post by dwhitney67 on 2007-11-07
Surely there must be an error generated when you compile with 4.1.3 or you would not have created your OP.  What is the error?  Can you provide a code snip of the area where the error is occurring?

There are tools for posting code; all you have to do is cut/paste the code, then highlight it, then select either the # or PHP buttons above.

---

### Post by vladan.b on 2007-11-07
> **dwhitney67 said:**
> Surely there must be an error generated when you compile with 4.1.3 or you would not have created your OP.  What is the error?  Can you provide a code snip of the area where the error is occurring?

There are tools for posting code; all you have to do is cut/paste the code, then highlight it, then select either the # or PHP buttons above.

I think I was not too clear when I posed my question.  The code compiles without problems on the Ubuntu compiler, my problem is that once the program runs, I have different answers between version 3.4 and 4.1.3.

gcc v. 3.4
```
cD5: i= 776 tvals= 50.2655, fabs(y-sol[j]) =2.4869e-13, maxGE =1.0057e-10
```

gcc v. 4.1.3
```
cD5: i= 30 tvals= 50.2655, fabs(y-sol[j]) =1.23901e-12, maxGE =1.24545e+16
```

Thank you.

---

### Post by hod139 on 2007-11-07
Have you tried running the code using valgrind to check for any memory errors?  Are you using the same version of the MPFRCPP library on both machines?  Are you positive it is only different versions of gcc between the two test cases.

I've never used that library, but my guess is that it is their fault, not gcc's (but who knows). You might consider browsing their mailing list, or even posting this question there.  Feel free to email the code to me, but I don't know when I'll have the time to look at it.

---

### Post by aks44 on 2007-11-07
AFAIK g++ 3.x is barely standard-compliant while 4.x is greatly enhanced on this matter. Maybe the code relies on a 3.x non-standard feature which behaves differently in 4.x?

FWIW, have you tried compiling your code with 4.1.2 (the one which comes with Feisty)? If you get the same behaviour (as I suspect) this would definitely rule out the Ubuntu repositories "theory".

---

### Post by vladan.b on 2007-11-07
@hod139: I only compiled the base cpp file on different versions of gcc, without the MPFRCPP, so yes only the versions of gcc were different.

@aks44: I tried it on Fedora and CentOS with their version of gcc, with 
```
g++ filename.cpp
```
which worked, but I have not tried it on Fiesty.

---

### Post by vladan.b on 2007-11-07
I had help from a friend of mine who suggested passing the optimization flag -O3 to g++ at compile time, which solved the problem.  So, 
```
g++ -O3 filename.cpp
```
works like a charm.

Thank you all for your help.
vladan

---

### Post by aks44 on 2007-11-07
There is definitely a problem. Using optimization flags should NOT change your program's behaviour under any circumstance.

---

### Post by vladan.b on 2007-11-07
I thought that too, but that was my original problem.  Now, should someone else be advised of this?

---

### Post by vladan.b on 2007-11-07
@ aks44:
If that didn't fry your noodle, how about this: passing -O and -O1 flags gives one result, -O2 gives another, and -O3 gives yet another.  All different results come from a for-loop which iterates the same number of times with all -O* options, but gives different answers.

```

for(...snip
if(fabs(y-sol[j])>maxGE)
    maxGE=fabs(y-sol[j]);


if(i>=nbpos+res[2]-5) 
    cout << " cHH: i= " << i << " tvals= " << tvals[i] 
           << ", fabs(y-sol[j]) =" << fabs(y-sol[j]) 
           << ", maxGE =" << maxGE << endl ;

 ...end for-loop

```

The very last line in my program's output is:
-O:   cHH: i= 411 tvals= 70, fabs(y-sol[j]) =4.86833e-14, maxGE =1.80564e-13
-O1: cHH: i= 411 tvals= 70, fabs(y-sol[j]) =4.86833e-14, maxGE =1.80564e-13
-O2: cHH: i= 411 tvals= 70, fabs(y-sol[j]) =5.46785e-15, maxGE =5.47895e-14
-O3: cHH: i= 411 tvals= 70, fabs(y-sol[j]) =6.68077e-14, maxGE =2.45248e-13

According to man pages, -O and -O1 should give the same result (which they do), but from what I understand -O2 should optimize less in terms of speed than -O3, but for me it produces smaller values.

Anyhow, these intricate details drive me up the wall.

---

### Post by aks44 on 2007-11-07
If I understand your code snippet correctly, the problem should be that depending on the optimization level, sol[] may contain different values (even though it is not supposed to).

Now that would be scary... but honestly, I still believe the problem is more likely to lie in your own code than in the compiler.

Would you mind posting an archive here that contains your project? I thought that compiler bugs were patented by Borland long ago and that they never licensed it...

---

### Post by vladan.b on 2007-11-07
aks44, I wish that the code was mine, but it is my advisor's.  I am yet to gut it out, and slap some work of mine into it.  So, please go easy on me on how it looks :p

Thank you.

---

### Post by DMills on 2007-11-07
I have not looked at the code, but one thing that springs to mind that could cause this is the fact that the X86 FPU has excess precision (a double is internally 80 bits, not 64) so code that manages to keep intermediate values in the FPU registers will give a different result to code that ends up needing to move the data to memory (truncates to 64 bits, this can particularly be a problem in iterative methods)....

There are various FPU control flags that you can pass to control this behaviour, and looking at the magnitude of the errors I would not be surprised if this was the problem (possibly aggravated by marginal numerical stability in your solver?). 

It is even possible that the compiler  default FPU setup has changed between versions....

Just a thought.

Regards, Dan.

---

### Post by dwhitney67 on 2007-11-07
Your program is crashing here:
[FONT="Courier New"]
665       for ( int i = 1; i <= nbcmp; i++ )
666       {
667          yc[ i ] = ynew[ i ];
668          **yvals[ jpnbposp1 ][ i ] = yc[ i ];**[/FONT]

This snippet comes from HBT12310dODES.cpp.

The reason for the crash (in this case a SIGSEGV, or segmentation violation), is because the value of the index 'jpnbposp1' is 6001, or one more than should be used to address the array.  The array, if I recall correctly, was initialized with 6001 entries (in the main function), thus the index used to access it should be a number from 0 to 6000.

This crash occurred on my Fedora 7 system, which uses g++ (gcc) version 4.1.2.

My system and my compiler are fine.  I wish I could say the same about your professor's code.  Looks like a hack from old Fortran code.

If you are serious about using this code, I would rewrite the thing.  Everything you need is there, except perhaps some better comments.

P.S.  I compiled the code with these options:
[FONT="Courier New"]g++ -g HBT123E10dcMLHH.cpp -o app1[/FONT]

and then used "ddd" to debug the program.  One should also compile/link with the math library (-lm), but apparently it was not required.

---

### Post by vladan.b on 2007-11-07
Dan,

Thank you for this great insight, as that did not even occur in my mind.  Now, I can only hope that once I start fiddling with extended precision this won't come back to haunt me.

Thank you,
vladan

---

### Post by vladan.b on 2007-11-07
> **dwhitney67 said:**
> Your program is crashing here:
[FONT="Courier New"]
665       for ( int i = 1; i <= nbcmp; i++ )
666       {
667          yc[ i ] = ynew[ i ];
668          **yvals[ jpnbposp1 ][ i ] = yc[ i ];**[/FONT]

This snippet comes from HBT12310dODES.cpp.

The reason for the crash (in this case a SIGSEGV, or segmentation violation), is because the value of the index 'jpnbposp1' is 6001, or one more than should be used to address the array.  The array, if I recall correctly, was initialized with 6001 entries (in the main function), thus the index used to access it should be a number from 0 to 6000.

This crash occurred on my Fedora 7 system, which uses g++ (gcc) version 4.1.2.

So you mean, you were not able to get an executable when you compiled it with g++?  

Now, I am new to g++ command line compiling, so how in the world did you fish it out this quickly?  Is there a flag passed to the compiler that will point out where the segmentation violation occurs?  

> 
My system and my compiler are fine.  I wish I could say the same about your professor's code.  Looks like a hack from old Fortran code.


I can believe that your system compiles the code well, and BINGO on the hack from Fortran (frustration started when I realized that).

> 
If you are serious about using this code, I would rewrite the thing.  Everything you need is there, except perhaps some better comments.

LOL!  The comments, tell me about it.  It turns out a student wrote this thing a while back, professor updated it, and now I am hacking this Franken-code apart, hoping after some botox it might look and work better.

Thank you for looking into this for me.
vladan

---

### Post by Tuna-Fish on 2007-11-07
he probably used a debugger.

---

### Post by DMills on 2007-11-07
You can pass a flag to gcc to make it use SSE instead of the FPU if you are working with single precision floats, or you can do something like this (Warning, non portable, Linux, X86 only):

```
  
    #include <fpu_control.h>

      main(argc, **argv)
      {
        fpu_control_t cw;
        _FPU_GETCW(cw);
        cw &= ~_FPU_EXTENDED;
        cw |= _FPU_DOUBLE;
        _FPU_SETCW(cw);
.
.
.
 
```

Found here: [http://www.wrcad.com/linux_numerics.txt](http://www.wrcad.com/linux_numerics.txt)

HTH.
Regards, Dan.

---

### Post by vladan.b on 2007-11-07
> **DMills said:**
> 
Found here: [http://www.wrcad.com/linux_numerics.txt](http://www.wrcad.com/linux_numerics.txt)


Thank you.

---

### Post by vladan.b on 2007-11-07
@Tuna-Fish and dwhitney67: thank you for pointing me to 'ddd'...that thing looks like it will help a LOT!

---

### Post by vladan.b on 2007-11-07
> **dwhitney67 said:**
> 
P.S.  I compiled the code with these options:
[FONT="Courier New"]g++ -g HBT123E10dcMLHH.cpp -o app1[/FONT]

and then used "ddd" to debug the program.  One should also compile/link with the math library (-lm), but apparently it was not required.

Pass it -O3 and it's happy...what?

---

### Post by dwhitney67 on 2007-11-07
Vladan.b

It doesn't matter (well, at least in theory) how much you pretty up the code or rely on compiler optimizers, the code has a bug.  When accessing (writing to) the array I pointed out earlier, you are trampling on other memory.

Every system is different, and thus on my system the OS reported a SIGSEGV, which in English means that I attempted to access memory that is out of the scope of the running application.

If on your system you do not get a SIGSEGV, that means that you are spanning a memory location that is still within your application (program) space.  It is highly probable that this event is corrupting the contents of stack upon which your program relies upon to store data.

You asked how I found the results so "quickly".  Easy... I untarred your source package, look (grepped) for main(), and then examined the code until I was bored.  Then I compiled it using this command:

```
g++ -g HBT123E10dcMLHH.cpp -o app1
```

The -g option tells the compiler to include debugging symbols.  For grins I ran the program (without a debugger), and voila it crashed.  When I ran it with a debugger, once again it crashed.  I was able to examine the indices that the code was using to access the array, and recalled that the program allocates 6000+1 elements for the array.  With an index of 6001, I knew there was a problem.

The debugger I used is called "ddd".  I'm sure you can get it using apt-get.

P.S.  It has been 22 years since I programmed in Fortran, but if I recall, indices into arrays begin with a 1, not a zero as in C, C++, Java, etc.  I would scrutinize your code for suspicious for-loops and the like... or like I suggested earlier, just rewrite the code.

---

### Post by vladan.b on 2007-11-07
dwhitney,

I apologize if I sounded off-ish when I replied, didn't mean to.  I greatly appreciate you looking into this for me.

The code has a bug, I see that too, and I am glad that with the hints of you and the other kind folks I now know of the debugger that will be kind to point me in the right direction when it comes to solving my problems.  

I see that I will be rewriting the code too, as (from what I heard) this used to be a Fortran code (hence the indices starting at 1), then an grad student translated into Matlab (also starting the count at 1), then from there via another grad student went into C, then via another into C++.  From what I can see no one spent time looking into it where it may crash, dump stuff, or incorrectly reference memory locations.  The motivation might have been to make it work, without paying attention as to -how well- it works.

Thank you, and the others, I am heading upwards on the learning curve right now.

vladan

---

### Post by aks44 on 2007-11-08
My first thought when I watched the code: better rewrite that thing from scratch! ;)

I failed to see how it is C++ code, apart that it uses new/delete/std::cout. To me it's more C code than anything else.


If I may give you a few advices:

- use *static const* declarations whenever you can. You have a great deal of constants that can be made *static const* (ie. compile-time constants).
- for those very few constants that can't be made *static*, make them *const* anyway.
- use STL containers (std::vector comes to mind) instead of those ugly, unsafe arrays. Use iterators whenever possible, otherwise use the at() member (at least during the initial development, it will let you catch index overruns, later you can replace at() by the unchecked [] operator).


Honestly there's no point trying to fix this, if you know the maths behind it it will be way faster to rewrite it. You have something like 2500 loc, so it shouldn't be long anyway.


Now I have yet to try and find out why you get that behaviour, but others already mentioned possible causes:
- FPU settings (wow, I wouldn't ever have thought of that, I'm not used to deal with values that require so much precision)
- but more likely IMHO array overruns (or other unseen bugs) may corrupt some other data, which leads to those incorrect results.


All I need is to find some time to really examinate the code. :oops:

---

### Post by vladan.b on 2007-11-08
Hola!

That is a great list you've put up for me, and THANK YOU!  It seems that I am going to turn this thread into my start page so I can refer to it whenever I need a reminder as to what I am doing wrong.

Please don't spend much time looking through code for improvements or bugs, seeing that I am bound to rewrite this thing to a certain extent.  If you have spare time and would like to, then please go ahead, but I am learning about different improvements that I can make, so I would rather get some help later on (when I implement some of them).

Thank you again, your help is greatly appreciated.
vladan

---

### Post by aks44 on 2007-11-08
To put you on the tracks:

```
double* arr = new double[dim];
// whatever...
delete[] arr;

// this is equivalent to:

std::vector<double> vec(dim);
// whatever...
// no need to delete[] :-)
```

and

```
double** arr = new (double*)[dim1];
for (int i=0; i<dim1; ++i)
  arr[i] = new double[dim2];
// whatever...
for (int i=0; i<dim1; ++i)
  delete[] arr[i];
delete[] arr;

// this is equivalent to:

std::vector< std::vector<double> > vec(dim1); // see NOTE below
for (std::vector< std::vector<double> >::iterator i = vec.begin(); i != vec.end(); ++i)
  i->resize(dim2);
// whatever...
// no need to delete[] :-)


// NOTE: you could avoid the "for" loop altogether
// but this would be WAY less efficient (involves many useless copying)
// so better stick with the previous example
std::vector< std::vector<double> > vec(dim1, std::vector<double>(dim2));
```


Hope this helps a bit. :)

---

### Post by vladan.b on 2007-11-08
This will help a lot!  Luckily, I went on a rampage looking for c++ books a while back, so I got a stash of reading material (so I can look up vectors and such).

Thank you :)
vladan

---


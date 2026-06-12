---
title: "[SOLVED] writing awk in bash / more than one line"
date: 2007-09-25
forum: Programming Talk
---

### Post by Claus7 on 2007-09-25
Hello,

At first I have to say that it is very nice that in these forums before you post a thread ubuntu searches for you similar posts by title. 
Unfortunately I couldn't find an answer to my question.

What I want to do is write a script file. In this I want to use awk commands. Most of the time I come accross awk commands inside bash scripts that they occupy only one line.
What I want to do is to use commands like for, if and print and (also for readability issues) I want these commands to be in different lines.
I do know that in bash in order to "inform" the program that your command continues also to the next line you type \. Yet, in my situation that doesn't seem to work.
I provide also the command that I 'm interested in:

#ii)Choose the first two columns and type C in front of these
```
awk '{                                                     \
      for (i=1; i=NR; i++) {                               \
         if (fmod(NR==0)                                   \
            printf"%c%d %c%d %c%d \n","H",$1,"C",$2,"C",$3 \
         else                                              \
            printf"%c%d %c%d %c%d \n","C",$1,"C",$2,"H",$3}\
                           }                               \
      }' inputfile > outputfile
```

Is is possible to inform me where I'm wrong in providing awk commands in bash in more than one line?

Thank you in advance,
Regards!

---

### Post by Jussi Kukkonen on 2007-09-25
put all of the awk code in another file and run that with *"awk -f file"*. See any one of the many awk tutorials around the web, e.g. [http://www.vectorsite.net/tsawk.html](http://www.vectorsite.net/tsawk.html) or the manual: [http://people.cs.uu.nl/piet/docs/nawk/nawk_toc.html](http://people.cs.uu.nl/piet/docs/nawk/nawk_toc.html)

---

### Post by ghostdog74 on 2007-09-25
> **Claus7 said:**
> Hello,

At first I have to say that it is very nice that in these forums before you post a thread ubuntu searches for you similar posts by title. 
Unfortunately I couldn't find an answer to my question.

What I want to do is write a script file. In this I want to use awk commands. Most of the time I come accross awk commands inside bash scripts that they occupy only one line.
What I want to do is to use commands like for, if and print and (also for readability issues) I want these commands to be in different lines.
I do know that in bash in order to "inform" the program that your command continues also to the next line you type \. Yet, in my situation that doesn't seem to work.
I provide also the command that I 'm interested in:

#ii)Choose the first two columns and type C in front of these
```
awk '{                                                     \
      for (i=1; i=NR; i++) {                               \
         if (fmod(NR==0)                                   \
            printf"%c%d %c%d %c%d \n","H",$1,"C",$2,"C",$3 \
         else                                              \
            printf"%c%d %c%d %c%d \n","C",$1,"C",$2,"H",$3}\
                           }                               \
      }' inputfile > outputfile
```

Is is possible to inform me where I'm wrong in providing awk commands in bash in more than one line?

Thank you in advance,
Regards!

your example does not warrant the need for  "\" . Remove them , and it will look nicer. If not, provide a more concrete example of a situation that happens to you that needs "\". also provide sample inputfile if possible

---

### Post by Claus7 on 2007-09-25
Hello,

first of all thank you for your immediate responses. 

My imput file, ghostdog74, looks like this :

 7    10     9
 9    10   13
13   16   15
15   16   19
...
...
...

My output file I want to look like this:
  C7    C10    H9
  H9    C10   C13
C13   C16   H15
H15   C16   C19
...

In the odd lines I want to add the C C H pattern and in the even lines the H C C pattern.

I modified my code so as to look like this :
awk '{
      for (i=1; i=NR; i++) {
         if (fmod(i,2) == 0))
            printf"%c%d %c%d %c%d \n","H",$1,"C",$2,"C",$3
         else
            printf"%c%d %c%d %c%d \n","C",$1,"C",$2,"H",$3}

      }' tmp1CCcH.ndx > tmp2CCcH.ndx

Yet I get the following error :

awk: cmd. line:3:          if (fmod(i,2) == 0))
awk: cmd. line:3:                             ^ parse error
awk: cmd. line:5:          else
awk: cmd. line:5:          ^ parse error

Thank you Jussi Kukkonen for your suggestion, yet I would prefer to have all my commands in one file, as I run many of these and if I "break" them in different files it would be awkward for me.

Thank's again,
Regards!

---

### Post by Claus7 on 2007-09-25
Hello,

even if I write it like this I get a parse error in "else":

```
awk '{
      for (i=1; i=NR; i++) {
         if (i%2== 0) ;
            printf"%c%d %c%d %c%d \n","H",$1,"C",$2,"C",$3 ;
         else
            printf"%c%d %c%d %c%d \n","C",$1,"C",$2,"H",$3};
      }' tmp1CCcH.ndx > tmp2CCcH.ndx
```

Regards!

---

### Post by ghostdog74 on 2007-09-25
```


awk '{
      for (i=1; i=NR; i++) {
         if (i%2== 0) {
            printf"%c%d %c%d %c%d \n","H",$1,"C",$2,"C",$3 
		 }
         else {
            printf"%c%d %c%d %c%d \n","C",$1,"C",$2,"H",$3
		 }
      }
	  }' "file"

```

there's no need for ";" at every end of statement. Follow each "if" and "else" with its corresponding open and close bracket.
the code above at least runs now, but there's still errors. Hint: fix the for loop.
good luck

---

### Post by Claus7 on 2007-09-25
Hello,

your hint was very useful. Up to now I have done this : (the {} I removed seemed to have no effect at all, either way I got no errors)

```
awk '{
        for (i=1; i**<=**NR; i++)
           if (i % 2 == 0)
               printf"%c%d %c%d %c%d \n","H",$1,"C",$2,"C",$3
            else
               printf"%c%d %c%d %c%d \n","C",$1,"C",$2,"H",$3
     }' tmp1CCcH.ndx > tmp2CCcH.ndx
```

I realised the following :

i) If I write awk and then : ```
 '{ ....
``` then everything will be concidered as awk code no matter how many lines I will use, till I write```
 ...}'
```

ii) cause my initial knowlege relied on fortran, I supposed that I had to transfer the mod command to awk via c, writing fmod. Yet, the corresponding mod to awk is the symbol **%**.
For that see "9.1 The if statement, The AWK Manual Edition 1.0 Dec '95 by Diane Barlow Close et al, [http://people.cs.uu.nl/piet/docs/nawk/](http://people.cs.uu.nl/piet/docs/nawk/) ".

iii) The mistake I had about the for command was that I had written :
i=1; i=NR
instead of
i=1; i**<=**NR

Yet, my output is not the one I expect. I get, instead of one line per if as ouput, half the number of i. For example if i is 10 then the output is 5 lines. I'm working on it. 

Thank you ghostdog74 once again!
Regards!

---

### Post by ghostdog74 on 2007-09-25
> **Claus7 said:**
> (the {} I removed seemed to have no effect at all, either way I got no errors)

be careful with that because the statement follow "if" is only one statement. Awk understands that. If you insert another statement with the open/close braces , ie
```

 ...
 if ( ) 
    print "blah
    print "blah blah"
....

```
it will give error. So for best practice, and less chances of error, I always enclose in open/close braces....

---

### Post by Claus7 on 2007-09-27
Hello all,

The answer to my question finally is the following:

```
awk '{

           if (i % 2 == 0) {
               printf"%c%d %c%d %c%d \n","C",$1,"C",$2,"H",$3
            i++ }
            else {
               printf"%c%d %c%d %c%d \n","H",$1,"C",$2,"C",$3
            i++ }

     }' tmp1CCcH.ndx > tmp2CCcH.ndx
```

The initialization of i seems to be 0. Also it seems that that way i is the number of records (lines). My output file is the one I wanted it to be. I have not found out why the for command didin't work though.

Thank you very much for your answers,
Regards!

---


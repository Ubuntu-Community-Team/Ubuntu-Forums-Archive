---
title: "code improvement? Fortran"
date: 2012-10-07
forum: Programming Talk
---

### Post by conradin on 2012-10-07
Hi All, I have a program that calculates the helicity of an alpha helix.
full source here:
[http://130.111.192.241/MHelicity.f](http://130.111.192.241/MHelicity.f)
Im using gfortran, fortran95
While the code at large is not great, only 2 things really bug me. 
first, how do I give the newline command? I tried \n but that didnt work

also, the default write output writes numbers like 0.0345E02
which makes it hard to export data into a csv. 
in my code I just wrote a blank line but Im hoping there is a newline character. 

```
       WRITE(2,*)
       WRITE(2,*)'TOTAL HELICITY:',FHELIX/REAL(NRES)
```

if anyone would like to set in to help me improve my code, even slightly I would be greatly appreciative. I mean it, ill put you name in the comments of the source. The source is going into a PHD students thesis.

---

### Post by bouncingwilf on 2012-10-07
In the old FORTRAN IV days it used to be a $ sign on the end of the format descriptor but now I believe they've standardized on advance='no' as the method of supressing linefeed.

ergo you're output descriptor should be 

WRITE(2,*,advance="no") 'TOTAL HELICITY :' ,FHELIX/REAL(NRES)

or something along those lines.

Bouncingwilf

Apologies - I've realized I've completely misread your post please ignore my idiot comments!

---

### Post by bouncingwilf on 2012-10-07
First off, looking at your code it looks like F77 to my old eyes.  i.e. it, fixed format and in the "old" upper case norm. Modern fortrans are usually written free form and lower case.

Secondly, the program is too short and relatively uncomplicated to require much more in the way of commenting (in my view but maybe not your tutors).

Thirdly, Fortran has an extensive array of output formatting options to control the appearance of output via the format statement, I suggest you look them up.


apologies for the earlier c***-up Bouncingwilf

---


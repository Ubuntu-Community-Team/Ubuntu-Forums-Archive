---
title: "c++ giant number loop ~ help"
date: 2012-02-07
forum: Programming Talk
---

### Post by highspider on 2012-02-07
Im trying to loop through till all r values equal 4 or found.

NOTE the infinite loop - don't worry about the found part that will come later
         I need all the int r's for something else.

Note i tried to push r and i into ri meaning r44 r43 r42 r41 ect

```


    int r00 = 0, r01 = 0, r02 = 0, r03 = 0, r04 = 0;
    int r10 = 0, r11 = 0, r12 = 0, r13 = 0, r14 = 0;
    int r20 = 0, r21 = 0, r22 = 0, r23 = 0, r24 = 0;
    int r30 = 0, r31 = 0, r32 = 0, r33 = 0, r34 = 0;
    int r40 = 0, r41 = 0, r42 = 0, r43 = 0, r44 = 0;
      
    while ( found = false)
    {
        for (int i = 44; i > 0; i--;)
           [COLOR=Red] if (ri > 4){
                r(i + 1)++;
                ri = 0;        [/COLOR]
         [COLOR=Red]}[/COLOR]
    }

```what im trying to do is this in a shorter way
```
 
while ( found == false || r44 < 5)
    {
        if (r00 > 4) { r00=0; r01++; }
        if (r01 > 4) { r01=0; r02++; }
        if (r02 > 4) { r02=0; r03++; }
        if (r03 > 4) { r03=0; r04++; }
        if (r04 > 4) { r04=0; r10++; }

        if (r10 > 4) { r10=0; r11++; }
        if (r11 > 4) { r11=0; r12++; }
        if (r12 > 4) { r12=0; r13++; }
        if (r13 > 4) { r13=0; r14++; }
        if (r14 > 4) { r14=0; r20++; }
                 
        if (r20 > 4) { r20=0; r21++; }
        if (r21 > 4) { r21=0; r22++; }
        if (r22 > 4) { r22=0; r23++; }
        if (r23 > 4) { r23=0; r24++; }
        if (r24 > 4) { r24=0; r30++; }
                
        if (r30 > 4) { r30=0; r31++; }
        if (r31 > 4) { r31=0; r32++; }
        if (r32 > 4) { r32=0; r33++; }
        if (r33 > 4) { r33=0; r34++; }
        if (r34 > 4) { r34=0; r40++; }

        if (r40 > 4) { r40=0; r41++; }
        if (r41 > 4) { r41=0; r42++; }
        if (r42 > 4) { r42=0; r43++; }
        if (r43 > 4) { r43=0; r44++; }
        
        Streets[0][0][0] = r44;
        Streets[0][1][0] = r43;
        Streets[0][2][0] = r42;
        Streets[0][3][0] = r41;
        Streets[0][4][0] = r40;


        Streets[1][0][0] = r34;
        Streets[1][1][0] = r33;
        Streets[1][2][0] = r32;
        Streets[1][3][0] = r31;
        Streets[1][4][0] = r30;

        Streets[2][0][0] = r24;
        Streets[2][1][0] = r23;
        Streets[2][2][0] = r22;
        Streets[2][3][0] = r21;
        Streets[2][4][0] = r20;

        Streets[3][0][0] = r14;
        Streets[3][1][0] = r13;
        Streets[3][2][0] = r12;
        Streets[3][3][0] = r11;
        Streets[3][4][0] = r10;

        Streets[4][0][0] = r04;
        Streets[4][1][0] = r03;
        Streets[4][2][0] = r02;
        Streets[4][3][0] = r01;
        Streets[4][4][0] = r00;

       r00++;
   }
  
```

---

### Post by cgroza on 2012-02-07
I think what you need to use is a data structure such as an array or a vector.
You could then iterate through it and perform your operations.

The resulting code will be much cleaner and a lot less clumsy.

---

### Post by trent.josephsen on 2012-02-08
Yep, in C++ if you want to test against 44 variables, you have to write 44 different tests longhand -- doesn't matter what they're named.  You could shorten it somewhat with preprocessor macros but that wouldn't address the real problem.

```
In a perfect world my college professors would allow assignment as .odt openoffice.org files! And code as Eclipse projects.
```

I think in a perfect world my profs would take assignments as .txt files and code as tarballs ;)

---

### Post by highspider on 2012-02-08
> **trent.josephsen said:**
> yep, in c++ if you want to test against 44 variables, you have to write 44 different tests longhand -- doesn't matter what they're named.  You could shorten it somewhat with preprocessor macros but that wouldn't address the real problem.

Well pooh pooh that stinks.  Ty
 
> **trent.josephsen said:**
> 
```
in a perfect world my college professors would allow assignment as .odt openoffice.org files! And code as eclipse projects.
```i think in a perfect world my profs would take assignments as .txt files and code as tarballs ;)
LOL thats good

---


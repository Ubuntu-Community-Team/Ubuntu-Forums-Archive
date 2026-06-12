---
title: "C: adding a printf changes the result???"
date: 2011-06-21
forum: Programming Talk
---

### Post by tomkat3 on 2011-06-21
Hello people,

I've been coding in C for about 6 months. I'll just say that I'm using a program designed to preform a simulation of cells. I'll try to skip over the details. At the end of the simulation they form this column structure thing and I have to calculate the width and some other statistics from it and put it into a short output file.

The typical output file looks like this:
```
  137.47    10.24
  616.00    35.78
   38.22    23.15
```But sometimes I get something like this:
```
472604372093897390883776495616.00 1494506247970435899442579111936.00
  616.00    65.86
     inf     -nan
```I spent a lot of time looking for the problem, but I found out that if I make a printf statement that prints the value of the divisor after a division statement, it works perfectly, and I get a normal answer! What is happening?:confused:

---

### Post by gmargo on 2011-06-21
> **tomkat3 said:**
> What is happening?:confused:
You have a bug in your code.
If adding printfs fixed it, you're probably stepping on stack or freed memory.

---

### Post by nvteighen on 2011-06-21
> **tomkat3 said:**
> What is happening?:confused:

The wise dwhitney67 would tell you that we're not psychics so we can't know your source code if you don't post it.

Please, post us the faulty code or at least some reduced version of it that also produces the same error.

---

### Post by tomkat3 on 2011-06-21
This is ture:|

The whole thing is about 3000 lines, so it would be a lot of work to create a reduced version (or rather, it might not be the same). I should say that the simulation takes place inside a 50x50x50 lattice. site and boundary are structs that hold data about the lattice. This is supposed to give a reasonable estimate of the width of a horizontal slice of sites with type MARROW.

The printf of interest is about 9 or 10 lines from the end. I print out the value of n_boundaries to make sure it isn't 0 or something else before the division.

Here's the problem area:

```

for(j=minH; j<=maxH-1; j++) { ///Starts at the bottom of the column and moves up
            check = 0;
            n_boundary = 0;
            check_boundary = 0;
            for(i=0; i<nX; i++) {
                for(k=0; k<nZ; k++) {
                    if(site[i][j][k].type == MARROW) {///MARROW sites are the column being analyzed.
                        for(x1=-1; x1<=1; x1++) {
                            for(z1=-1; z1<=1; z1++) {
                                if(x1==0 && z1==0) ;
                                else {
                                    if(site[i+x1][j][k+z1].type != MARROW) { // This site[i][j][k]) is on a boundary
                                        boundary[n_boundary].x = i;
                                        boundary[n_boundary].z = k;
                                        n_boundary++;
                                        check_boundary = 1;
                                        break;
                                    }    
                                }    
                            }
                            if(check_boundary) break;
                        }    
                    }
                }
            }
            if(check_boundary) {
//calculate the center of mass of the slice
                for(i=0; i<n_boundary; i++) {
                    cmx += boundary[i].x;
                    cmz += boundary[i].z;
                }
                cmx /= (double)n_boundary;
                cmz /= (double)n_boundary;
                w = 0.0;
                for(i=0; i<n_boundary; i++) {
                    w += sqrt((boundary[i].x-cmx)*(boundary[i].x-cmx)+(boundary[i].z-cmz)*(boundary[i].z-cmz));
                }
////////////******************************************/////////////////
                printf("(double)n_boundary = %f\n", (double)n_boundary);//This is the printf that magically makes the output reasonable
                w /= (double)n_boundary;
                width[0] += 1.0;
                width[set] += w;
                width_roughness[(int)width[0]] = w;// This is used later
            }
        }
        width[set] /= width[0];
    }
```

---

### Post by Arndt on 2011-06-21
Run your program under 'valgrind'. It detects many/most cases where you use memory in undefined ways. One drawback is that the program runs much slower.

---

### Post by tomkat3 on 2011-06-21
> One drawback is that the program runs much slower.     How much slower? The simulation takes about 3 minutes to run as it is and uses well over 200 different variables and functions.

Yesterday the professor I work for suggested that it might have something to do with how the compiler (gcc) optimized the code to run. Could that be it?

---

### Post by psusi on 2011-06-21
Where is the other printf?  The one whose output is changed?

---

### Post by tomkat3 on 2011-06-21
After averaging it with other runs of the simulation, the width is written into a file later in the function like the code below:

```
        
for(i=1; i<=n_set; i++) {
            avg_width += width[i];
        }
        avg_width /= (double)n_set;
...
        fp = fopen(file_name, "w");
            fprintf(fp, "%8.2f %8.2f\n", avg_width*sigma, sd_width*sigma);
            fprintf(fp, "%8.2f %8.2f\n", (avg_height-n_blood_gap)*sigma, sd_height*sigma);    
            fprintf(fp, "%8.2f %8.2f\n", avg_roughness*sigma, sd_roughness*sigma);
   1.0/sqrt(2.0)*sd_roughness*sigma);
        }
        fclose(fp);
    }    
```

EDIT: Basically every output variable changed except the height values.

---

### Post by psusi on 2011-06-21
Are these variables all global?  Are you doing any threading?

---

### Post by dwhitney67 on 2011-06-21
The last time I checked, 0 + (-1) is equal to -1.

Take a close look at the following code:
```

...

                for(k=0; k<nZ; k++) {
                    if(site[i][j][k].type == MARROW) {///MARROW sites are the column being analyzed.
                        for(x1=-1; x1<=1; x1++) {
                            for(z1=-1; z1<=1; z1++) {
                                if(x1==0 && z1==0) ;
                                else {
                                    if(site**[i+x1]**[j]**[k+z1]**.type != MARROW) { // This site[i][j][k]) is on a boundary
...

```
Is it possible that the condition is true; that is, the 'site' is equal to MARROW?

---

### Post by tomkat3 on 2011-06-21
The struct site is global. Width, height, etc. and all the output variables (avg_width, avg_height, sd_etc) are global as well, but I don't think they're ever modified by another part of the code.. Everything else is local to the function that writes the file.

I googled threading, and I don't think that's happening.

Thanks for the responses!

EDIT: just saw dwhitney67's post. That's an excellent observation, but site *should* never be MARROW anywhere near x = 0 or z =  0.

More specifically, my question is this: how can the addition of a printf statement at a seemingly unremarkable part of the code change the outputs from garbage to something reasonable?

---

### Post by psusi on 2011-06-21
Without looking at the actual code and/or debugging it, I'm not sure.

---

### Post by gmargo on 2011-06-21
You make it difficult with only partial code.  but whatever MARROW is, you have written code that indexes a 3-dimensional array improperly.

On the very first pass, your code references
```

site[-1][minH][-1]

```How can that be correct?

---

### Post by psusi on 2011-06-21
> **gmargo said:**
> You make it difficult with only partial code.  but whatever MARROW is, you have written code that indexes a 3-dimensional array improperly.

On the very first pass, your code references
```

site[-1][minH][-1]

```How can that be correct?

Good catch.

---

### Post by Arndt on 2011-06-22
> **tomkat3 said:**
> How much slower? The simulation takes about 3 minutes to run as it is and uses well over 200 different variables and functions.

Yesterday the professor I work for suggested that it might have something to do with how the compiler (gcc) optimized the code to run. Could that be it?

valgrind reports the problems as they happen, so you may not have to wait for the whole run to finish.

Conceivably, the compiler may do something wrong, but that's true maybe one time out of thousand when one suspects it. The behaviour of incorrect code can very well depend on how the code is optimized, that's for sure.

To test that hypothesis, what would you do?

---

### Post by Arndt on 2011-06-22
> **tomkat3 said:**
> 
More specifically, my question is this: how can the addition of a printf statement at a seemingly unremarkable part of the code change the outputs from garbage to something reasonable?

The printf call may put values on the stack and then return, and later those places may be assigned to variables in your code, and if you happen not to initialize them correctly, you will get what printf put there, which is different from if you didn't call printf.

For example. It may do things with malloced memory, too.

---

### Post by tomkat3 on 2011-06-22
> On the very first pass, your code references
```
      site[-1][minH][-1] 
```How can that be correct?     The column of MARROW sites grows in the middle of the lattice, centered around x = 25, z = 25 (The earlier measurements I showed were converted into different units. Usually the width isn't more than 6 or 7 sites). If I had MARROW at x = 0 or z = 0, I'd be in trouble, but that never happens. I have a way to see the entire lattice after the simulation, so I know this isn't happening.

> To test that hypothesis, what would you do? Is there a way to change the way the compiler optimizes the code? I checked the man page for the gcc command, but it was 9000 lines long.   tl;dr :mrgreen:

> The printf call may put values on the stack and then return, and later  those places may be assigned to variables in your code, and if you  happen not to initialize them correctly, you will get what printf put  there, which is different from if you didn't call printf.Is there a way to achieve this effect without a printf statement that spams my terminal?

Also, where can I learn more about this "stack"? In other programs, I've smashed it in other programs before, so I'm kinda interested.

---

### Post by psusi on 2011-06-22
Step through your code in the debugger.  I'll bet you will find that your assumptions about MARROW are wrong, and that you are in fact, using an index of -1.

Or add some assert() macros to make sure that the index is never < 0.

---

### Post by Arndt on 2011-06-22
> **tomkat3 said:**
> 

Is there a way to change the way the compiler optimizes the code? I checked the man page for the gcc command, but it was 9000 lines long.


How did you learn about optimization to begin with?

Not all of it is about optimization, but there are some things you can turn on and turn off, yes.

What I meant was much simpler: you can test whether it's optimization that brings about the behaviour you're seeing, by trying the program without optimization.

> 
Is there a way to achieve this effect without a printf statement that spams my terminal?

Also, where can I learn more about this "stack"? In other programs, I've smashed it in other programs before, so I'm kinda interested.

You shouldn't be satisfied when the particular error you're seeing vanishes. Since there really must be an error in the code, which printf just happens to make visible (or invisible), the computations may still be wrong, just not as noticably.

Are there tutorials and books about C which don't mention how local variables are stored on a stack? For the concept of execution stack in general, read for example [http://en.wikipedia.org/wiki/Call_stack](http://en.wikipedia.org/wiki/Call_stack)

---


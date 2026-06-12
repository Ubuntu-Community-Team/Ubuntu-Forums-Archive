---
title: "Error running MED2.0 progam"
date: 2012-11-27
forum: Programming Talk
---

### Post by cdlam on 2012-11-27
Hey guys I'm pretty new at this but I'd figured I'd ask here...

I'm trying to run a program called MED2.0, which is a gene prediction program. I've had some errors that I got help with resolving in other threads, but I'm getting a new error now and I'm not sure whether it's an error with the code (like the others) or if it's an error with my input sequences (i.e some error of biological significance). Anyway, here's the error I get:

```
chris@ubuntu:~/Documents/IS/Bioinformatics-Software/MED/LINUX/bin$ ./MED2 DownstreamEXONS-40.fasta
Wellcome to MED2.0
Genome file is DownstreamEXONS-40.fasta
sequence size: 711577
GC%: 0.246209

Number of exactcted ORFs: 7848
Select root ORFs and first running of TIS model...
 iteration      Selected as coding    rejected as non-coding
       0                        2                      119
       1                        0                     1475
       2                        0                     2762
       3                        0                     1023
       4                        0                      286
       5                        0                       98
       6                        0                       31
       7                        0                        4
       8                        0                        0
Selected root coding ORFs number: 2
Rejected non-coding ORFs number: 5798
Remaining ORFs number: 2048
MED2: Matrix.h:19: Type_T& Matrix_T<Type_T>::operator()(unsigned int, unsigned int) [with Type_T = double]: Assertion `i<line&&j<colum' failed.
Aborted (core dumped)

```

here is Matrix.h:14-20
```
Matrix_T(unsigned rows, unsigned cols,Type_T init=Type_T(0)):
      line(rows),colum(cols),data(rows*cols, init ){};
      Matrix_T(){}
    inline Type_T& operator()(unsigned i,unsigned j)                            //operator () 
    {
       ** assert (i<line&&j<colum);**
        return data[i*colum+j];
```

This is the program, in case any of you are interested: [http://bioinfo.ctb.pku.edu.cn/med2_1/MED2.htm](http://bioinfo.ctb.pku.edu.cn/med2_1/MED2.htm)

I guess I'm just wondering whether something is wrong with the code or if the error comes from my input data. Any help is greatly appreciated, thanks!

---


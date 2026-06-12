---
title: "Rearranging Tab-Delimited Data in Text File"
date: 2010-04-08
forum: Programming Talk
---

### Post by divxmp4 on 2010-04-08
I have text files with X Y Z  data. 

There are three columns, one each for X, Y and Z and the files  are tab delimited.
 The values of Y increase over a given range and then repeat. The value of X is constant over one repetition of the range in Y. Z is a  dependent variable.
 

For example:
 0    1    44
 0        2   32
 0        3       22
 0        4        14
 5       1        66
 5        2       11
 5        3        32
 5        4   16
 9       1      51
 9    2    72
 9         3       85
 9        4       57
  
 I'm trying to take these three columns and break them into multiple  tab-delimited columns. In the output, I'm trying to get a single repetition of Y  to be the first column (1 to 4 in example). 



Then, the second column should have  the Z values for the first range of Y (where X=0 in above example). Then, the next  column should have the Z values for the next range of Y (where X=5 in above example) and so on. 



Also, I'd like the  first line value in each of the new columns containing Z values to be  the X-value they were originally associated with.




 Thus, I'm trying to get the output file to look like:


 Y   0         5         9
 
 1   44     66     51
 
 2   32   11   72
 
 3        22     32   85
 
 4   14   16   57


I don't think this operation is that hard, but I don't know where to begin. If anybody could provide a script or code that can do the trick, I'd really appreciate it.

---

### Post by lisati on 2010-04-08
Homework? If so, we won't actually do it for you, but might be able provide a hint or two if you get stuck.

---


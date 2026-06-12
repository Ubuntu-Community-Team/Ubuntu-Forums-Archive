---
title: "Help with AWK (not reading first line)"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by wess126 on 2008-06-19
Hi All,

I am having trouble with AWK and was hoping someone here could help.
This command is being used to extract information from a raster image in GRASS. The cat file contains coordinates plus x & y plus height (LiDAR ascii file)

cat file.txt | r.what in=grd_dtm | awk '{FS = "|"; print $1, $2, $3, $4, $3-$4}'

The file.txt looks like this

-73151.430 -3302499.830 972.550 
-73148.120 -3302499.930 971.450 
-73146.510 -3302499.780 971.430 
-73143.450 -3302499.970 973.220 
-73141.890 -3302499.990 974.610 
-73138.490 -3302499.790 973.760 
-73136.910 -3302499.890 973.840 
-73135.220 -3302499.820 973.810 
-73100.690 -3302499.950 974.920 
-73100.560 -3302499.810 974.850 

The command essentially gets the value of the raster using r.what based on the geographic coordinates in file.txt Awk then prints all the columns out and differences column 3 and 4.

Everything works fine except that the first line is not split properly and does not perform the differencing. result is as follows:

-73151.430|-3302499.830|972.550 |969.0281982422   0
-73148.120 -3302499.930 971.450  969.1377563477 2.31224
-73146.510 -3302499.780 971.430  969.2705688477 2.15943
-73143.450 -3302499.970 973.220  969.7659912109 3.45401
-73141.890 -3302499.990 974.610  969.9495239258 4.66048
-73138.490 -3302499.790 973.760  970.1778564453 3.58214
-73136.910 -3302499.890 973.840  970.3128662109 3.52713
-73135.220 -3302499.820 973.810  970.4539794922 3.35602
-73100.690 -3302499.950 974.920  972.056640625 2.86336
-73100.560 -3302499.810 974.850  972.0620117188 2.78799

It is only one point (I have about 20 million) but I would still like to know why FS is not working on the first line.

I am using Ubuntu 7.10 on a dell optiplex gx620.

Many thanks for all your help and suggestions

WEs

---

### Post by HalPomeranz on 2008-06-19
> **wess126 said:**
> 
cat file.txt | r.what in=grd_dtm | awk '{FS = "|"; print $1, $2, $3, $4, $3-$4}'

... snip ...

It is only one point (I have about 20 million) but I would still like to know why FS is not working on the first line.


The reason it's not working like you expect is that the way you have things written the assignment to FS isn't executed until awk has read/parsed the first line of input.  awk's normal behavior is to execute your code blocks on each line of input, but the parsing of the lines happens before the block is triggered.  So in this case awk is parsing the first line with its default delimiter (whitespace) and then executing the block, which sets FS to the "pipe" ("|") for all *subsequent* lines.

In general, you set variables like FS with a BEGIN block like so:

```

... | awk 'BEGIN { FS = "|" } { print $1, $2, $3, $4, $3-$4 }'

```

BEGIN blocks are triggered before awk processes any of its input.

But really the best way to set FS is with the -F command line argument.  So your command line should be:

```

cat file.txt | r.what in=grd_dtm | awk -F'|' '{ print $1, $2, $3, $4, $3-$4 }'

```

---


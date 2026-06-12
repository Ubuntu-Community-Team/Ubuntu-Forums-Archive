---
title: "Java Read Text Column function similar to ReadLine()?"
date: 2010-01-15
forum: Programming Talk
---

### Post by SNYP40A1 on 2010-01-15
I have a text file containing vector information by pin.  It looks like this:

[PHP]
               xxxxxxxxxxxxxxxxxxxx
               pppppppppppppppppppp
               iiiiiiiiiiiiiiiiiiii
               nnnnnnnnnnnnnnnnnnnn
               12345689111111111122
                       012345678901
									
                                   
                                   
                                   
Count  PatAdr                      
(Main) (Main)                      
     1      0  1000000000000010XXXX
     2      0  1000000000000010XXXX
     3      0  1000000000000010XXXX
     4      0  1000000000000010XXXX
     5      0  1000000000000010XXXX
     6      0  1000000000000010XXXX
     7      0  1000000000000010XXXX
     8      0  1000000000000010XXXX
     9      0  1000000000000010XXXX
    10      0  1000000000000010XXXX
    11      0  1000000000000010XXXX
    12      0  1000000000000010XXXX
    13      0  1000000000000010XXXX
    14      0  1000000000000010XXXX
    15      0  1000000000000010XXXX
    16      0  1000000000000010XXXX
    ...
[/PHP]

I want to extract the information column by column.  So I would like to be able to write or store each pin by line such as:

xpin1   11111...
xpin2   10000...
xpin3   10000...

Basically, what I am looking for is exactly the Java readLine() function described here:

[http://java.sun.com/javase/6/docs/api/java/io/BufferedReader.html](http://java.sun.com/javase/6/docs/api/java/io/BufferedReader.html)

but instead of reading a text file line-by-line.  I want to read column by column.  Anyone know of such a function or way to do this?

---

### Post by Axos on 2010-01-15
What is actually in the file? Only the part in the center?...

1000000000000010XXXX
1000000000000010XXXX
1000000000000010XXXX
1000000000000010XXXX
1000000000000010XXXX
1000000000000010XXXX
1000000000000010XXXX
.
.
.

If that's all there is, one way to do it is to create an array for each pin and then read each line and assign each character to the nth element in each array (increment n each time you go through the loop). That is, the first line contains all the 0th array elements, the second line contains all the 1st array elements, etc.

I may be misunderstanding what you are trying to do. If so, please clarify.

---

### Post by baizon on 2010-01-15
As far as i know there is no way to read a file by column. Because "Java" reads the File from the 1 byte until it gets to the "EOF" parameter. ReadLine() is the best solution i think. 
If you want you can do it "smarter" with StringTokenizer(), it's a little bit more complicated then ReadLine() but it's easier (IMHO) putting your "results" into (for example) an list.
[http://java.sun.com/javase/6/docs/api/java/util/StringTokenizer.html]("http://java.sun.com/javase/6/docs/api/java/util/StringTokenizer.html")

---

### Post by SNYP40A1 on 2010-01-24
> **Axos said:**
> What is actually in the file? Only the part in the center?...

1000000000000010XXXX
1000000000000010XXXX
1000000000000010XXXX
1000000000000010XXXX
1000000000000010XXXX
1000000000000010XXXX
1000000000000010XXXX
.
.
.

If that's all there is, one way to do it is to create an array for each pin and then read each line and assign each character to the nth element in each array (increment n each time you go through the loop). That is, the first line contains all the 0th array elements, the second line contains all the 1st array elements, etc.

I may be misunderstanding what you are trying to do. If so, please clarify.

Actually, all the code that I posted is part of the file.  The count and patAddr columns can be ignored as they are not needed.  However, up above the binary data are the pin names (verticall) such as xpin1, xpin2, xpin3...  The hard part is matching up the pin names with their data which is in the same column.  So if I can read by column, then it's easy.

baizon, I'll checkout string tokenizer.

---


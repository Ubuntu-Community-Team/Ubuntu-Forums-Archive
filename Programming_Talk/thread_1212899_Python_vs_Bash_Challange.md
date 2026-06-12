---
title: "Python vs Bash Challange"
date: 2009-07-14
forum: Programming Talk
---

### Post by gazmac on 2009-07-14
Hi Guys and Girls,

I have written some bash to solve a little issue I have, but would be interested in the performance difference of doing it in Python. Hopefully a few people here will think this is quite fun and a little challenge!

I have a huge text list of over 1 million URL's (generated from my own site XML). They are in a file called "allurls.txt" and in the format...

```

http://www.mydomain.com/5560000043-Some_Words
http://www.mydomain.com/6263403333-Different_things_here
http://www.mydomain.com/5562344287-Not_even_in_English
http://www.mydomain.com/9962458778-Why

```

And so on...
(Format is: ```
up to the first slash is always the same, then a 10 digit number, then a hyphon and some text
```)

What I need to do is to create a CSV called "data.csv" that looks like this...

```

"5560000043","556000-0043","http://www.mydomain.com/5560000043-Some_Words","http://www.myNEWdomain.com/5560000043"
"6263403333","626340-3333","http://www.mydomain.com/6263403333-Different_things_here","http://www.myNEWdomain.com/6263403333"
"5560000118","556000-0118","http://www.mydomain.com/5562344287-Not_even_in_English","http://www.myNEWdomain.com/5562344287"

```

and so on and so on...
(Format of data.csv should be: ```
"numbers after the first / but before the first hyphon","those numbers again, but split with a hyphon after the first six digits","The original URL","The new URL with just the number after the first slash"
```)

I have written the following bash script called createCSV.sh which works great and does exactly what it should, except that it takes over 3 hours to create the CSV out of the 1 million plus URLS. :guitar:

```

#!/bin/sh
# createCSV.sh
# Author: Me

rm data.csv
fname="allurls.txt"
PS1=$(date '+%Y%m%d_%H%M%S')
while read a;
do
comma=","
hyphon="-"
quote='"'
orgnumber=`expr substr $a 22 10`
orgnumberfirsthalf=`expr substr $orgnumber 1 6`
orgnumbersecondhalf=`expr substr $orgnumber 7 4`
orgwithhypon="$orgnumberfirsthalf$hyphon$orgnumbersecondhalf"
oldurl="$a"
newurl1stpart="http://www.myNEWdomain.com/"
newurl2ndpart="$orgnumber"
newurl="$newurl1stpart$newurl2ndpart"
total="$quote$orgnumber$quote$comma$quote$orgwithhypon$quote$comma$quote$oldurl$quote$comma$quote$newurl$quote"
echo "$total" >> data.csv
done < "$fname"
PS2=$(date '+%Y%m%d_%H%M%S')
echo "$PS1" >> data.csv
echo "$PS2" >> data.csv

```

Beautiful eh? :)

So the challenge is can anyone write a python script that will beat my great bash script time of over three hours to make the CSV?

Add in a time stamp when it starts and a time stamp when it ends into the end of the CSV as I have and I'll run all suggestions and we can see who is the fastest!

Good luck :)

---

### Post by ghostdog74 on 2009-07-14
are you sure your bash script gives the correct output. 

here's an awk solution

```

awk 'BEGIN{
    FS="[/-]"
    OFS=","
    q="\042"
}
{
    org=q $0 q
    o = q $4 q
    newdom = q "http://mynewdomain.com/"$4 q
    $4 = q substr($4,1,6)"-"substr($4,7) q
    print o,$4,org,newdom    
}' file

```

---

### Post by gazmac on 2009-07-14
That is immense...

The time using my bash script that I wrote with my general lack of knowledge (but it did work ;) ) was over 3 hours...

Ghostdog74, powered by awk... 9 seconds. :lolflag:

Just shows what you can do when you know what to do...

Here's the completed code:

```
#!/bin/sh
# createCSVawk.sh
# Author: GhostDog74

awk 'BEGIN{
    FS="[/-]"
    OFS=","
    q="\042"
}
{
    org=q $0 q
    o = q $4 q
    newdom = q "http://www.myNEWdomain.com/"$4 q
    $4 = q substr($4,1,6)"-"substr($4,7) q
    print o,$4,org,newdom >> "data.csv"  
}' allurls.txt
```

9 seconds. Unbelievable. I'm going for lunch. Thanks man!

---

### Post by ghostdog74 on 2009-07-14
for 9 seconds, i am guessing you have a VERY big file.

---

### Post by gazmac on 2009-07-14
> **ghostdog74 said:**
> for 9 seconds, i am guessing you have a VERY big file.


The output CSV is 256Mb. :)

---

### Post by ghostdog74 on 2009-07-14
word of advice: Don't use bash's while read loop to parse big files.

---

### Post by Paul Miller on 2009-07-14
So, is this challenge closed (awk FTW?), or are you still looking for a python version for comparison?

---

### Post by ajackson on 2009-07-14
This is a good example of using the right tool for the job.

---

### Post by drubin on 2009-07-14
> **Paul Miller said:**
> So, is this challenge closed (awk FTW?), or are you still looking for a python version for comparison?

There are more then 1 way to skin a cat. If you want to give a python example I don't think any one viewing this thread later would mind. Also I don't think the OP would mind seeing other alternatives to the solution.

---

### Post by unutbu on 2009-07-14
> **ghostdog74 said:**
> word of advice: Don't use bash's while read loop to parse big files.

What is the correct bash idiom for reading large files line by line?

What is "while read" doing that makes it so slow?

---

### Post by ajackson on 2009-07-14
> **unutbu said:**
> What is the correct bash idiom for reading large files line by line?

What is "while read" doing that makes it so slow?
My guess is the extra IO requests are the slowing factor, a better approach might be to read it in chunks or maybe all at once (of course depending on file size that could get tricky).

---

### Post by ghostdog74 on 2009-07-14
> **unutbu said:**
> What is the correct bash idiom for reading large files line by line?

internally, its just (commonly) the while read loop. BUT for large files, try to use tools like awk which is meant for parsing files. Other tools like grep/sed/cat/cut/more/head/tail are all meant to parse files BUT they  can only do specific task, so much so that if a coder is not careful, excessive use of these tools together can hurt the performance of the script. (their functions overlap). awk , OTOH, is able to perform similar capabilities that those tools can since its a small programming language by itself. one can reduce a lot of process overheads just by using awk.

> 
What is "while read" doing that makes it so slow?
awk is compiled c program that takes in an input file. Internally, its doing a "while loop" to read the file. whereas with bash's while loop, its not "compiled" in that sense. (i hope you understand what i am saying). Further, in OP's code, there are some use of external commands like expr, which is unnecessary because bash internally has "substringing" functions.

how nice can it be if bash can do this too
```

bash "{print $0}" file

```

---

### Post by howlingmadhowie on 2009-07-14
> **unutbu said:**
> What is the correct bash idiom for reading large files line by line?

What is "while read" doing that makes it so slow?

bash loves to start (fork) a new shell for every task. this has considerable overhead. i don't know what commands are doing this here, but i'd point my finger at 'expr'.

---

### Post by tribaal on 2009-07-14
Here's my attempt to a Python script for your problem. Probably not as elegant and fast as awk, but it was fun to code :)

```

#!/usr/bin/env python
from string import split
from string import join

original_site = "http://www.mydomain.com"
new_site = "http://www.myNEWdomain.com"

input_file_name = "input.txt"
output_file_name = "output.txt"

in_file = file(input_file_name,"r")
out_file = file(output_file_name,"w")

for line in in_file:
  last_part = split(line,'/')[3]
  number = split(last_part,'-')[0]
  hyphen_number_low = number[6:]
  hyphen_number_high = number[:6]
  out_file.write(join(['"',number,'","',hyphen_number_high,'-',hyphen_number_low,'","',line[:-1],'","',new_site,'/',number,'"','\n' ],''))

```

Let me know how fast this is, i'm curious :)

- Trib'

---

### Post by unutbu on 2009-07-14
Thank you for the explanation, ajackson, ghostdog74 and howlingmadhowie.

> awk is compiled c program that takes in an input file. Internally, its doing a "while loop" to read the file. whereas with bash's while loop, its not "compiled" in that sense. (i hope you understand what i am saying).

Let me see if I'm following you: awk's read-in-file loop is hard-coded and compiled into awk itself. This loop is run with every invocation of the awk program. In contrast, bash's "while read" is a combination of two bash commands. Although each command is implemented in C, the loop itself is not compiled. Do I have that right?

Still, there must be something very complicated (or wrong?) that bash's "while read" is doing since
python's "for line in open(...)" is also not compiled (in the sense that awk's loop is compiled), and yet it is much faster than bash's "while read":
```

% wc allurls.txt 
 1000000   999997 49250130 allurls.txt
```
```

% cat ~/bin/test.awk
#!/bin/sh
awk '
{
}' allurls.txt
```
```

% cat ~/pybin/test.py
#!/usr/bin/env python
for url in open('allurls.txt','r'):
    pass
```
```

% cat ~/bin/test.sh
#!/bin/bash
while read a; do
    :
done < allurls.txt
```
```

% time test.awk

real	0m0.254s
user	0m0.196s
sys	0m0.052s
```
```

% time test.py

real	0m0.335s
user	0m0.280s
sys	0m0.056s
``````


% time test.sh

real	0m34.004s
user	0m31.126s
sys	0m1.852s

```

---

### Post by Jacks0n on 2009-07-14
Another python solution.. in theory it *should* work...

```
input_file_name = 'data'
output_file_name = 'output.csv'
olddomain = 'http://mydomain.com'
newdomain = 'http://mynewdomain.com'

input = open(input_file_name, 'r')
output = open(output_file_name, 'a')

for line in input.readlines():
	num, words = line.split('/')[-1].split('-')

	output.write('"%s", "%s-%s", "%s/%s-%s", "%s/%s"\n' % (num,
								num[0:-4],
								num[-4:],
								olddomain,
								num,
								words,
								newdomain,
								num
								)
	)


input.close()
output.close()

```

---

### Post by unutbu on 2009-07-14
Jacks0n, I like your solution except that the OP does not guarantee that the text at the end does not contain '/' or multiple '-', only that the first (3?) slash(es) is always the same. 

That could throw a wrench into
```

num, words = line.split('/')[-1].split('-')
```

Also, since we are dealing with a 10^6 line data file, 
```

for line in input.readlines():
```
might be a burden on memory since it
would force python to load the entire contents of 'data' into a list.
If you use
```

for line in input:
```

then python will only read one line of input at a time (lessening the burden on memory).

---

### Post by Can+~ on 2009-07-14
[PHP]#!/usr/bin/env python

from urlparse import urlparse

original = open('asdf.txt', 'r')
output = open('output.txt', 'w')

for line in original:
	# Get the piece after ther / (end of domain name) with urlparse
	urlparsed = urlparse(line)
	urlfilename = urlparsed.path[1:]
	
	# Split once and get the number
	number = urlfilename.split('-', 1)[0]
	
	output.write('"%s", "%s-%s", "%s", "http://%s/%s"\n' % 
	(number, number[0:6], number[6:], line.rstrip(), urlparsed.netloc, number))

original.close()
output.close()
[/PHP]

Using urlparse to avoid problems with adomain/with/multiple/things/before/the/12345678-something_lalala

I'm not sure how this will perform, as I write it thinking on solving the problem, and not speed.

Edit: I forgot the "quotes" that CSV expects.

---

### Post by gazmac on 2009-07-14
Really enjoying reading this thread, think I've even learned something too :)

Just to thank everyone for their efforts so far, I will try each solution when I get back to my own PC tomorrow morning and post the results here.

As Ghostdog74 says, parsing a million + lines using bash is maybe not the most robust thing to do :)

Interesting to see some python and even php solutions as I was thinking that holding all this data in a CSV file is stupid. It would be mutch better off in a SQL database.

The CSV we are producing is nearly 300Mb, so can't be imported to an SQL easily through something like phpMyAdmin. It could be that the script that we are writing here could record the values directly into the database.
That would slow it down a lot, but would increase the amount of automation which I think is very important.

---

### Post by lavinog on 2009-07-14
> **gazmac said:**
> 
The CSV we are producing is nearly 300Mb, so can't be imported to an SQL easily through something like phpMyAdmin. It could be that the script that we are writing here could record the values directly into the database.
That would slow it down a lot, but would increase the amount of automation which I think is very important.

I would think it should still take less than 3 hours.

I have never messed with a large mysql database, but it looks like you can import csv files into mysql (a search for mysql import csv pulls up some information)

---

### Post by ghostdog74 on 2009-07-14
> **tribaal said:**
> Here's my attempt to a Python script for your problem. Probably not as elegant and fast as awk, but it was fun to code :)

```

#!/usr/bin/env python
from string import split
from string import join

original_site = "http://www.mydomain.com"
new_site = "http://www.myNEWdomain.com"

input_file_name = "input.txt"
output_file_name = "output.txt"

in_file = file(input_file_name,"r")
out_file = file(output_file_name,"w")

for line in in_file:
  last_part = split(line,'/')[3]
  number = split(last_part,'-')[0]
  hyphen_number_low = number[6:]
  hyphen_number_high = number[:6]
  out_file.write(join(['"',number,'","',hyphen_number_high,'-',hyphen_number_low,'","',line[:-1],'","',new_site,'/',number,'"','\n' ],''))

```

Let me know how fast this is, i'm curious :)

- Trib'

don't have to import string module for split and join.
```

line.split()
' '.join(line)

```

---

### Post by ghostdog74 on 2009-07-14
> **unutbu said:**
> Let me see if I'm following you: awk's read-in-file loop is hard-coded and compiled into awk itself. This loop is run with every invocation of the awk program. In contrast, bash's "while read" is a combination of two bash commands. Although each command is implemented in C, the loop itself is not compiled. Do I have that right?

that's roughly it. pardon me for not explaining in good english. 

> 
Still, there must be something very complicated (or wrong?) that bash's "while read" is doing since
python's "for line in open(...)" is also not compiled (in the sense that awk's loop is compiled), and yet it is much faster than bash's "while read":
depends on how the internal C implementation is coded for each tool. Python's for loop is optimized for reading files. For further understanding, one has to look at the source codes and see how the C code looks like.

---

### Post by gazmac on 2009-07-15
> **lavinog said:**
> I would think it should still take less than 3 hours.

I have never messed with a large mysql database, but it looks like you can import csv files into mysql (a search for mysql import csv pulls up some information)

Normally that is correct, you can even use phpMyAdmin to import via a CSV. The issue here is that both mySQL and phpMyAdmin have max uploads and time outs which in a file this size screw things up.

I'm sure that with the right settings you could import such a large CSV, but not "out of the box".

---

### Post by gazmac on 2009-07-15
OK, time for another result, remember my script was 3 hours plus (still people doubting that it worked, but it did... :p ), Ghostdog74 showed how it could be done in AWK and done it in 9 seconds...

Time for a python solution from Tribaal...

First of all, it worked great and the data output all looked correct!

Secondly, it was fast. 14.5 seconds to produce the 238.6Mb CSV file.

Thanks Trib' good work!

---

### Post by gazmac on 2009-07-15
And another python entry from Can+~

This one used urlparse and again a quick check through the output data shows everything to be as it should...

The execution time:
48 seconds

Good work!

---

### Post by gazmac on 2009-07-15
> **Jacks0n said:**
> Another python solution.. in theory it *should* work...


Oops, prints out two lines of the CSV and then crashes with the following...

```
Traceback (most recent call last):
  File "./can.py", line 12, in <module>
    num, words = line.split('/')[-1].split('-')
ValueError: too many values to unpack

```

---

### Post by ssam on 2009-07-15
> **unutbu said:**
> Jacks0n, I like your solution except that the OP does not guarantee that the text at the end does not contain '/' or multiple '-', only that the first (3?) slash(es) is always the same. 


would it be better to use
```
line.partition('/')
```
instead of split?

---

### Post by tribaal on 2009-07-15
> **ghostdog74 said:**
> don't have to import string module for split and join.
```

line.split()
' '.join(line)

```

Thanks, I didn't know that! Will save me some keystrokes :)

[QUOTE=gazmac]
Time for a python solution from Tribaal...

First of all, it worked great and the data output all looked correct!

Secondly, it was fast. 14.5 seconds to produce the 238.6Mb CSV file.

Thanks Trib' good work![/QUOTE]

Yay! 15 seconds isn't so bad... I wonder if reading the input file in one sequence, copying to memory then doing the parsing would be faster...
Still, I'm surprised it was so fast. 6 seconds overhead sounds good compared to AWK, given the difference in readability.

Cheers

- Trib'

---

### Post by tribaal on 2009-07-15
Here's an slightly different version, which reads lines from the file in one pass, and does the actual parsing from memory...

I'm curious if it provides any performance improvement over my previous version.

```
#!/usr/bin/env python

from string import split, join

original_site = "http://www.mydomain.com"
new_site = "http://www.myNEWdomain.com"

input_file_name = "input.txt"
output_file_name = "output.txt"

in_file = file(input_file_name,"r")
out_file = file(output_file_name,"w")

lines = in_file.readlines()

for line in lines:
  last_part = split(line,'/')[3]
  number = split(last_part,'-')[0]
  hyphen_number_low = number[6:]
  hyphen_number_high = number[:6]
  out_file.write(join(['"',number,'","',hyphen_number_high,'-',hyphen_number_low,'","',line[:-1],'","',new_site,'/',number,'"','\n' ],''))
```

---

### Post by unutbu on 2009-07-15
ssam, the problem with
```

line.partition('/')
```

is that 
```

http://domain/...
```

contains 3 '/'s so "line.partition('/')" would split on the first '/' found.
This would work:
```

line[7:].partition('/')
```

but this might be faster:
```

idx=line.find('/',7)
```
[PHP]
#!/usr/bin/env python
fh=open('allurls.txt')
new_domain='http://www.myNEWdomain.com/'
for line in fh:
    idx=line.find('/',7)
    url,other=line[:idx],line[idx:]
    idx=other.find('-')
    number=other[1:idx]    
    print('"%s","%s-%s","%s","%s%s"'%(number,number[:6],number[6:],line[:-1],
                                      new_domain,number))
[/PHP]

---

### Post by gazmac on 2009-07-15
> **tribaal said:**
> Here's an slightly different version, which reads lines from the file in one pass, and does the actual parsing from memory...

I'm curious if it provides any performance improvement over my previous version.



Tried this one and it actually took about 1 second longer. Still great though :)

---

### Post by gazmac on 2009-07-15
> **unutbu said:**
> 
but this might be faster:
```

idx=line.find('/',7)
```


I edited Unutbu's code a little so that it wrote to a output file like everyone else's to keep it a level playing field. The code looks like this

```
#!/usr/bin/env python

output_file_name = "dataub.csv"
out_file = file(output_file_name,"w")


fh=open('allurls.txt')
new_domain='http://www.myNEWdomain.com/'
for line in fh:
    idx=line.find('/',7)
    url,other=line[:idx],line[idx:]
    idx=other.find('-')
    number=other[1:idx]    
    out_file.write('"%s","%s-%s","%s","%s%s"\n'%(number,number[:6],number[6:],line[:-1],new_domain,number))  
```


And the test results...

11 seconds!

---

### Post by Finalfantasykid on 2009-07-15
I have a Java solution.

```
// Written by David Turner
// Last edited, July 16, 2009

import java.io.BufferedReader;
import java.io.File;
import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.FileReader;
import java.io.IOException;
import java.io.PrintStream;

public class createCSV {
    private static final String QUOT = "\"";
    private static final String QUOTCOMQUOT = "\",\"";
    private static final String QUOTNL = "\"\n";
    private static String domain;
    private static String newDomain;

    public static void main(String[] args){
        long start = System.currentTimeMillis();
        if(args.length < 2){
            System.out.println("Expecting 2 arguments.  Program will terminate.");
            System.exit(0);
        }
        domain = args[0];
        newDomain = args[1];
        BufferedReader reader = createBufferedReader("allurls.txt", "");
        String line;
        StringBuilder builder = new StringBuilder();
        try {
            File file = new File("data.csv");
            if(file.exists()) 
                file.delete();
            PrintStream stream;
            stream = new PrintStream(new FileOutputStream("data.csv", false));
            while((line=readLine(reader)) != null){
                parse(line, builder);
                if(builder.length() > 100000){
                    stream.print(builder.toString());
                    builder.replace(0, builder.length(), "");
                }
            }
            try {
                reader.close();
            } catch (IOException e) {
                e.printStackTrace();
            }
            stream.print(builder.toString());
            long finish = System.currentTimeMillis();
            stream.println("start:" + start + "ms");
            stream.println("finish:" + finish + "ms");
            stream.println("total:" + (finish - start)/1000 + "s");
            System.out.println("total:" + (finish - start)/1000 + "s");
        } catch (FileNotFoundException e) {
            e.printStackTrace();
        }
    }
    
    private static void parse(String line, StringBuilder builder){
        // Parses the string so that it fits these specifications...
        // "numbers after the first / but before the first hyphon",
        // "those numbers again, but split with a hyphon after the first six digits",
        // "The original URL","The new URL with just the number after the first slash"
        // ie.  "5560000043","556000-0043","http://www.mydomain.com/5560000043-Some_Words","http://www.myNEWdomain.com/5560000043"
        StringBuilder number = new StringBuilder(line);
        number.replace(0, domain.length(), "").replace(10, number.length(), "");
        builder.append(QUOT).append(number).append(QUOTCOMQUOT)
               .append(number.substring(0, 6)).append("-").append(number.substring(6)).append(QUOTCOMQUOT)
               .append(line).append(QUOTCOMQUOT)
               .append(newDomain).append(number).append(QUOTNL);
    }
    
    private static String readLine(BufferedReader reader){ 
        // Reads a String line from a file
        try { 
            return reader.readLine();
        } catch (IOException e){
            e.printStackTrace();
        }
        return null;
    }
    
    public static BufferedReader createBufferedReader(String which, String folder){ 
        // Creates a BufferedReader
        File file = new File(folder+which);
        try {
            return new BufferedReader(new FileReader(file));
        } catch (FileNotFoundException e) {
            e.printStackTrace();
        }
        return null;
    }
}

```Its probably the longest solution, but with my input file of size 1,000,000 it takes 11 seconds on average.  If you have a faster computer than mine, it may take significantly less.  It does however use a massive amout of memory(about 1GB!).  I'm still trying to reduce that, but so far I have had no luck.  Oh well I might work on it later, but for now I'll see how I do...

If you edit the createSCV.sh file which is attached, you can change some of the parameters around.

EDIT:  I made a few minor changes, and it seems to have improved the speed by 1 or 2 seconds.

EDIT2:  I made some more changes.  Now in my computer with that same input file, takes around 7 seconds to execute.

EDIT3: If you wanted a version which uses less ram(about 100MB as opposed to the current 1GB), I have figured out a way to do so, but it adds 1 to 2 seconds.  If the amount of ram used right now is no problem, then I would use the one that I have posted already.

EDIT4:  I managed to reduce the ram usage significantly without sacrificing any speed(as far as I can tell).  Here is the new version

---


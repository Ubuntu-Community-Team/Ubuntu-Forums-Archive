---
title: "Help AWK script"
date: 2012-10-09
forum: Programming Talk
---

### Post by drmrgd on 2012-10-09
I've been working on this for some time, but being a complete AWK novice, I'm a bit stumped at the moment.  

My goal is to join together a number of tables based on the first column of data.  I want to do something similar to the BASH 'join' command, but have 60 tables to join.  The other caveat is that each table will have a different number of rows, depending on the results of the upstream processing, and so the final number of rows needs to be equal to the table with the most rows.  The final rule is that I only need the first and second columns of data, and I need to change the header of the second column of data in order to identify which original table contributed the table to the final output.  

Here is an example of my input tables (I'm attaching a couple just to play around with):

Table 1
```
Amp     median  Width
AMPL387948860   45      173
AMPL414952472   294     172
AMPL391478722   37.5    158
AMPL392076156   31      169
AMPL535375693   12      176
AMPL396629974   249     177
AMPL408948551   386     129
AMPL413431337   444     174
AMPL401922916   297     75
AMPL405468071   2       172
AMPL408440700   0       173

```

Table 2
```
Amp     median  Width
AMPL387948860   101     173
AMPL391478722   74      158
AMPL392076156   50      169
AMPL396629974   483     177
AMPL401922916   451     75
AMPL405468071   4       172
AMPL408440700   0       173
```

Ultimately, I want to have a large table, with the first row representing all "AMPL..." from all subtables, and column two with either the data from that subtable, or a placeholder if there was no data corresponding with the value in column 1:

```
Amp     subTable1       subTable2
AMPL387948860   45      101
AMPL414952472   294     ---
AMPL391478722   37.5    74
AMPL392076156   31      50
AMPL535375693   12      ---
AMPL396629974   249     483
AMPL408948551   386     ---
AMPL413431337   444     ---
AMPL401922916   297     415
AMPL405468071   2       4
AMPL408440700   0       0
```

So far I've come up with the following:

```
awk '{ HEAD=gensub(/median/,substr(FILENAME,1,20),1,$2); } $0 {arr[$1]=arr[$1] "\t" HEAD } END { for(i in arr) print i, arr[i] }' *.tsv
```

I thought this was working until I realized that it was not padding the null entries a tab, but rather just pushing everything to the left-most column.  So, the header no longer corresonds with the correct table.  I tried to add an if statement in there to substitute "---" if there was no data in that field ($2), but I can't seem to get it to work right:

```
awk '{ HEAD=gensub(/median/,substr(FILENAME,1,20),1,$2); } $0 {arr[$1]=arr[$1] "\t" HEAD } END { for(i in arr) { if(i == 0) print "---", arr[i]; else print i, arr[i] }  }' *.tsv
```

Does anyone have a suggestion on how to get this to work correctly?

---

### Post by Vaphell on 2012-10-09
```
awk '    { row[$1]=$1; col[FILENAME]=FILENAME; val[$1":"FILENAME]=$2; }
     END { for (x in row)
           {
             printf("%s", x);
             for(y in col)
             {
               printf("\t%s", ((val[x":"y]=="")?"---":val[x":"y]) );
             }
             printf("\n");
           }
         }' *.tsv
```
output:
```
Amp	median	median
AMPL414952472	---	294
AMPL408948551	---	386
AMPL396629974	483	249
AMPL405468071	4	2
AMPL391478722	74	37.5
AMPL401922916	451	297
AMPL408440700	0	0
AMPL535375693	---	12
AMPL413431337	---	444
AMPL392076156	50	31
AMPL387948860	101	45
```
it's a proof of concept so you need to fix column headers :)

---

### Post by conradin on 2012-10-09
Any way to get those tables as a csv?
I would try using the cat command, to concatenate, then try to parse out that recurring line "Amp     median  Width"
with awk or sed. 
```

#!/bin/bash

cat m1 m2 >> output
sed '/Amp     median  Width/d' ./output >> tmp
sed -i '1iAmp     median  Width' tmp


```

this code puts out in file tmp:
```

Amp	median	median
AMPL414952472	---	294
AMPL408948551	---	386
AMPL396629974	483	249
AMPL405468071	4	2
AMPL391478722	74	37.5
AMPL401922916	451	297
AMPL408440700	0	0
AMPL535375693	---	12
AMPL413431337	---	444
AMPL392076156	50	31
AMPL387948860	101	45
AMPL387948860   45      173
AMPL414952472   294     172
AMPL391478722   37.5    158
AMPL392076156   31      169
AMPL535375693   12      176
AMPL396629974   249     177
AMPL408948551   386     129
AMPL413431337   444     174
AMPL401922916   297     75
AMPL405468071   2       172
AMPL408440700   0       173

```  

could use the sort command to sort. Im sure theres easy ways to remove duplicates.

---

### Post by drmrgd on 2012-10-10
Wow!  Thanks for the help guys!  

Vaphell your solution is perfect; a little over my head, but perfect.  I'm going to have to study this for a while to completely understand how you've constructed this.  In particular, when you're calling the index of the array 'val' what is the ":" notation?  I'm thinking that you're reading each .tsv file in and delimiting the data with a colon stored in the array val.  Is this right? I can't seem to find the right documentation to describe in detail how to parse arrays like this.  

Nevertheless, following your lead, I'm able to add the filename as the header by adding another conditional argument to the list (although I'm not quite sure if this is the correct way to do this):

```
awk '   { row[$1]=$1; col[FILENAME]=FILENAME; val[$1":"FILENAME]=$2; }
        END { for (x in row)
                  {
                          printf("%s", x);
                          for(y in col)
                          {
                                  printf("\t%s", ((val[x":"y]=="median")?FILENAME:(val[x":"y]=="")?"---":val[x":"y]) );
                          }
                          printf("\n");
                  }
          }' *.tsv
```

Thanks for another elegant solution to a problem!

Thank you, conradin, for your solution as well.  However, there are a very large number of tables to parse, and it would be too consuming to have to create a bunch of intermediate tables and then clean up the output once finished.  I quickly realized this after starting down a similar path to what you proposed :p

---

### Post by Vaphell on 2012-10-10
lol, it's not a notation at all, i merely emulate 2d array with associative array with index made of x and y glued together with ':' (index="x:y" -> array(x,y)), : is not needed, but i put it there for visual purposes.
[https://en.wikibooks.org/wiki/An_Awk_Primer/Arrays#Dimensions](https://en.wikibooks.org/wiki/An_Awk_Primer/Arrays#Dimensions)
> Awk arrays are only single-dimensional. That means there is exactly one index. However, there is a built-in variable called SUBSEP, which equals "@" unless you change it. If you wish to create a multi-dimensional array, in which there are two or more indexes for each element, you can separate them with a comma.
i didn't know that comma would work, interesting :)



will that FILENAME in the END section work correctly?
i'd split the block where the array is populated to 2 sections and use $2 for table body and FILENAME for headers
```
$1=="Amp" { row[$1]=$1; col[FILENAME]=FILENAME; val[$1":"FILENAME]=FILENAME; }
$1!="Amp" { row[$1]=$1; val[$1":"FILENAME]=$2; }
```
and print the array the old way, only testing for nulls.*col[FILENAME]=FILENAME* was redundant (it was required only once per file) and assuming that the header is always there it's now possible to skip it in the content part of tables.


```
awk '$1=="Amp" { row[$1]=$1; col[FILENAME]=FILENAME; [COLOR="SeaGreen"]val[$1":"FILENAME]=FILENAME[/COLOR]; }
     $1!="Amp" { row[$1]=$1; [COLOR="RoyalBlue"]val[$1":"FILENAME]=$2;[/COLOR] }
           END { for(x in row)
                 {
                   printf("%s", x);
                   for(y in col)
                     printf("\t%s", ((val[x":"y]=="")?"---":val[x":"y]) );
                   printf("\n");
                 }
               }' *.tsv

Amp	[COLOR="SeaGreen"]2.tsv	1.tsv[/COLOR]
AMPL414952472	[COLOR="RoyalBlue"]---	294[/COLOR]
AMPL408948551	---	386
AMPL396629974	483	249
AMPL405468071	4	2
AMPL391478722	74	37.5
AMPL401922916	451	297
AMPL408440700	0	0
AMPL535375693	---	12
AMPL413431337	---	444
AMPL392076156	50	31


```

---

### Post by drmrgd on 2012-10-10
> **Vaphell said:**
> lol, it's not a notation at all, i merely emulate 2d array with associative array with index made of x and y glued together with ':' (index="x:y" -> array(x,y)), : is not needed, but i put it there for visual purposes.
[https://en.wikibooks.org/wiki/An_Awk_Primer/Arrays#Dimensions](https://en.wikibooks.org/wiki/An_Awk_Primer/Arrays#Dimensions)

i didn't know that comma would work, interesting :)


Ahhh....very interesting.  Now I understand what's going on here. Having a look at that AWK primer, it looks pretty good.  Would you recommend this or something else as a reference?  I really need to read up on AWK to be able to better use it.  My skills are very weak with this tool, and with all of the data processing I'm doing these days, it would really be beneficial to be able to make better use of it! 

> 
will that FILENAME in the END section work correctly?
i'd split the block where the array is populated to 2 sections and use $2 for table body and FILENAME for headers
```
$1=="Amp" { row[$1]=$1; col[FILENAME]=FILENAME; val[$1":"FILENAME]=FILENAME; }
$1!="Amp" { row[$1]=$1; val[$1":"FILENAME]=$2; }
```
and print the array the old way, only testing for nulls.*col[FILENAME]=FILENAME* was redundant (it was required only once per file) and assuming that the header is always there it's now possible to skip it in the content part of tables.


Putting FILENAME in the END section does work.  However, I think it wasn't the best way to do it, and I wondered about modifying the first block to add it there as you did.  I think it'll also give me a bit more flexibility to name the column headers (some filenames are long and I think I want to trim them a bit before using them as column headers).

Once again, you've taught me some valuable lessons!  Thank you so much!

---

### Post by Vaphell on 2012-10-10
> Putting FILENAME in the END section does work.

but FILENAME in END section will always be the name of last processed file, won't it? test yields this:
```
$ ./awk-test.sh 
Amp	**2.tsv**	**2.tsv**
AMPL414952472	---	294
```
**y** would be more like it, loop modifies it to necessary values.
```
$ ./awk-test.sh 
Amp	2.tsv	1.tsv
```


> Would you recommend this or something else as a reference? I really need to read up on AWK to be able to better use it. My skills are very weak with this tool, and with all of the data processing I'm doing these days, it would really be beneficial to be able to make better use of it! 

to be honest i suck at awk, my knowledge is a mixture of trivia picked up from forums and google. AWK = conditional blocks, BEGIN and END, few builtin variables like NR, NF..., bash-like $number and the rest is a mixture of C and maybe bash-like string concatenation and associative arrays :)
i guess whipping up tons of quick and dirty bash scripts made me proficient in solutions made with rudimentary tools ;-)

---

### Post by drmrgd on 2012-10-11
Yes, you're right!  Too many things going on at the same time, and I didn't notice it!  

The big drawback, though is that the headers are not always at the top, depending on the tables to be input, so I have to pipe it to 'sort' (example below without sort):

```
AMPL409941289   ---     ---     390     ---
AMPL407894270   ---     ---     413     ---
AMPL391478722   37.5    43      13      74
AMPL405474583   ---     ---     475     ---
AMPL535530158   ---     ---     468     ---
AMPL434795757   ---     ---     461     ---
AMPL391701334   ---     ---     320     ---
Amp     run133.IonXpress_007.lowamps.tsv        run133.IonXpress_007.lowamps.tsv        run133.IonXpress_007.lowamps.tsv  run133.IonXpress_007.lowamps.tsv
AMPL387806497   ---     ---     467     ---
AMPL431125124   ---     ---     477.5   ---
AMPL637290055   ---     ---     398     ---
AMPL401922916   297     365     118     451
AMPL417520594   ---     ---     410     ---
AMPL413618402   ---     ---     488     ---

```  

I thought it might be because I was calling FILENAME in the END section.  However, even removing it from that block and adding it to the top induces the same behavior.  I think I know how to fix it, though, and I'll work on that plus truncating the FILENAME variable before it prints as it can be a little too long to be useful for a header.

I found a great AWK tutorial that I'm going to follow as a introductory crash-course:

[http://www.selectorweb.com/awk.html](http://www.selectorweb.com/awk.html) 

The extent of my AWK knowledge is to just pull columns of data from tables with simple print statements.  If I can get better at it, though, I think it'll really help me with future data parsing.  

Thank you again for all of your help!  With your guidance, I've literally shaved hours off my data analysis time so I could focus on trying to understand the data!

---

### Post by Vaphell on 2012-10-11
that's the thing with associative arrays, you don't control the order :)

you could try ditching the idea of a single array for everything and use 2: header and values.

```
awk '$1 == "Amp" { col[FILENAME]=FILENAME; hdr[FILENAME]=FILENAME; }
     $1 != "Amp" { row[$1]=$1; val[$1":"FILENAME]=$2; }
             END {
                   printf("Amp");
                   for(y in col)
                     printf("\t%s", hdr[y]);
                   printf("\n");
                   
                   for(x in row)
                   {
                     printf("%s", x);
                     for(y in col)
                       printf("\t%s", ((val[x":"y]=="")?"---":val[x":"y]));
                     printf("\n");
                   }
                 }' *.tsv
```
I hope both for(y in col) produce the same sequence :)

---

### Post by drmrgd on 2012-10-11
Wow!  This is definitely starting to scramble my brains a bit. I think I'm going to have to ready up on associative arrays more to get a better understanding of how they work and how to manipulate them.  My background on using arrays is pretty weak to begin with (last time was about 15 years ago in an intro C++ course).  This modification, of course, works beautifully!  

What I can't seem to wrap my head around, is how the variable FILENAME is being used in the arrays.  I've been trying to modify the FILENAME to trim it on the fly, and just can't seem to get the output correct for the rest of the table (as soon as I change it, it all falls apart).  If I try to make a variable that I can call in the table (for example):

```
colheader=$(sub(/\.lowamps\.tsv/,"",FILENAME)); #Just as an example of something to trim
```

I can't quite grasp how to load it into the array(s) correctly, and the table doesn't print the data correctly.  If I try to take the easy way out and instead of assigning a trimmed FILENAME to a variable and just do a general sub, the table mostly prints correctly, but with 4 extra rows that just say "Amp    median".  

BAH!  Just figured it out....need a BEGIN statement when I'm defining that variable for some reason.  I guess I assumed that BEGIN was implicit if END was already defined. Now I at least have it printing something different without majorly modifying the table.  Just need to figure our my syntax deficiency since it's either printing a null string or "0".

Getting very close here!

---

### Post by Vaphell on 2012-10-11
associative arrays are indexed by arbitrary strings, and the order will depend on how it was implemented internally. Let's say it's a binary tree using string hashes. In such a scenario the string hash would be 1 level of 'randomness' and the comparison function that decides what a>b means another.

In order to control the sequence by hand, you have to use integers in some way
```
awk '$1=="Amp" { col[size++]=FILENAME; **sub(/lowamps[.]tsv$/, "", col[size-1])**; }
     $1!="Amp" { row[$1]=$1; val[$1":"col[size-1]]=$2; }
           END {
                 printf("Amp");
                 for(i=0; i<size;i++)
                   printf("\t%s", col[i] );
                 printf("\n");
                 
                 for(r in row)
                 {
                   printf("%s", r);
                   for(i=0; i<size; i++)               
                     printf("\t%s", ((val[r":"col[i]]=="")?"---":val[r":"col[i]]) );
                   printf("\n");
                 }
               }' *.tsv

$ ls *tsv
1lowamps.tsv  2lowamps.tsv  3lowamps.tsv
$ ./awk-test.sh 
Amp	1	2	3
```
sub takes the variable (3rd param) and modifies its content in place

---

### Post by drmrgd on 2012-10-11
OH!  I see what I've been doing wrong.  I've been trying to run sub on FILENAME or assign that sub statement to a variable that I would pass to the hdr array below instead of just simply passing the whole hdr array to the sub statement.  Now that I see it, it make so much sense! Making that modification, the script is working perfectly now.

Yeah, it's a bit hard to track the associative arrays to find what's happening.  I'm definitely going to have to study up on that in future - or find a way to avoid them at all costs :p

I can't thank you enough for helping me out with this.  I've learned tons in this exersise!

---

### Post by Vaphell on 2012-10-11
look at my previous post, i redid it and columns are driven by integers now :)
using for(a in array) syntax would still yield unpredictable results because it's still an associative array at its core, but since we manually call elements by integer index everything is in initial order.

>  I would pass to the hdr array below instead of just simply passing the whole hdr array to the sub statement.

technically it was not the whole hdr array, but the element of it, the one that just got created :)
```
new_elem_of_hdr_array=initial_value;
sub( /regex/, "", new_elem_of_hdr_array );
```

---

### Post by drmrgd on 2012-10-11
This is great!  Originally (after my first bumbling attempt in the first post!) I was trying to build for statements a little more like this, as this makes a little more sense to me (or is at least a little easier for me to read through).  I like taking some of the randomness out of the data output as I'll ultimately need to do a lot of comparisons between these data sets and the less post sorting and manipulating the better.  

You're really teaching this poor biologist some great tips and tricks!  I feel like I need to start paying you some tuition or something :p

---

### Post by Vaphell on 2012-10-12
lol, i certainly wouldn't complain ;-)
i could have used the integer driven columns right off the bat but assumed it was not a big deal (preserving logical bonds was) and the single array approach more or less worked.
Do you need rows in some special order? Because they are more annoying due to semi-random occurences

---

### Post by drmrgd on 2012-10-12
> **Vaphell said:**
> lol, i certainly wouldn't complain ;-)
i could have used the integer driven columns right off the bat but assumed it was not a big deal (preserving logical bonds was) and the single array approach more or less worked.
Do you need rows in some special order? Because they are more annoying due to semi-random occurences

No, special order is not really needed.  I expect these different runs to have a lot of variation, and cross comparing between these different final output tables, regardless the real order, will be the real goal.  Now that the data is formatted in clean tables and much less random (and without extraneous data) than it was before, it'll will be a snap to compare across the many different data sets that I have.

---


---
title: "SED command  for comparing"
date: 2014-03-07
forum: New to Ubuntu
---

### Post by sbz on 2014-03-07
Hi 
I am new to programming and I am trying to use  sed and awk for comparing within a file

 I have a file which looks like this

```

source1 LEN predictive 347320 348798 0.485927 - . Name=sa000006.1;ID=sa000006;Alias=sa121750.;
source1 LEN descriptive_1 348799 351449 . . . Parent=sa000006.1;supp_id=1800.1;
source1 LEN descriptive_3 347154 347319 . . . Parent=sa000006.1;supp_id=1800.1;

```

Basically ,I need to change the start and end locations of predictive statement in accordance to descriptive_1 and descriptive_3
if line containing PREDICTIVE statement has start locations > descriptive_1 or descriptive_3 start location then i have to replace start location of predictive by descriptive_1 or or descriptive_3
if line containing PREDICTIVE statement has end location < descriptive end .then replace end location of predictive by descriptive1 or descriptive_3
Basically all descriptive locations should fall under all predictive start and end locations.

The end result should look like :
```

source1 LEN predictive 347154 351449 0.485927 - . Name=sa000006.1;ID=sa000006;Alias=sa121750.;
source1 LEN descriptive_1 348799 351449 . . . Parent=sa000006.1;supp_id=1800.1;
source1 LEN descriptive_3 347154 348319 . . . Parent=sa000006.1;supp_id=1800.1;

```
thanks in advance

---

### Post by Vaphell on 2014-03-07
is there something else in these files? because i wrote a quick and dirty python script that takes advantage of the fact that these 3 are in order with no other data.

```
#!/usr/bin/env python

import sys

for l in open( sys.argv[1] ):
    if 'predictive' in l:
        prow = l.strip().split()
    elif 'descriptive_1' in l:
        d1row = l.strip().split()  
    elif 'descriptive_3' in l:
        d3row = l.strip().split()
        prow[3] = str( min( int(prow[3]), int(d1row[3]), int(d3row[3]) ) )
        prow[4] = str( max( int(prow[4]), int(d1row[4]), int(d3row[4]) ) )
        print ' '.join( prow )
        print ' '.join( d1row )
        print ' '.join( d3row )
```

```
$ cat in.txt
source1 LEN predictive 347320 348798 0.485927 - . Name=sa000006.1;ID=sa000006;Alias=sa121750.;
source1 LEN descriptive_1 348799 351449 . . . Parent=sa000006.1;supp_id=1800.1;
source1 LEN descriptive_3 347154 347319 . . . Parent=sa000006.1;supp_id=1800.1;
$ ./somejunk.py in.txt
source1 LEN predictive 347154 351449 0.485927 - . Name=sa000006.1;ID=sa000006;Alias=sa121750.;
source1 LEN descriptive_1 348799 351449 . . . Parent=sa000006.1;supp_id=1800.1;
source1 LEN descriptive_3 347154 347319 . . . Parent=sa000006.1;supp_id=1800.1;
```

---

### Post by sbz on 2014-03-08
Thanks so much for helping .
However my values in my infile  are separated by tab . They are not seperated columnwise nor  by space.Could this work on files which are separated by tabs?

Also there were few entries in original file which needed no correction.


[COLOR=#000000][FONT=Ubuntu Mono]source1 LEN predictive 347310 348798 0.485927 - . Name=sa000007.1;ID=sa000006;Alias=sa121750.; [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono][/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]source1 LEN descriptive_1 347900 348600 . . . Parent=sa000007.1;supp_id=1800.1[/FONT][/COLOR] 


However these entries were  removed  in outfile?Since they dont need correction,  can they be retained in the outfile as it is?

---

### Post by Vaphell on 2014-03-08
tab is no problem - just replace ' '.join( ... ) with '\t'.join( ... ) in last 3 lines

could you give more lines in original format as an example and point what needs to change and what need to be preserved so i have something to debug on?

---

### Post by sbz on 2014-03-08
thanks!
Here is a small sample original file

```
source1 LEN predictive 347320 348798 0.485927 - . Name=sa000006.1;ID=sa000006;Alias=sa121750.;
source1 LEN descriptive_1 348799 351449 . . . Parent=sa000006.1;supp_id=1800.1;
source1 LEN descriptive_3 347154 347319 . . . Parent=sa000006.1;supp_id=1800.1;

source1 LEN predictive 347310 348798 0.485927 - . Name=sa000007.1;ID=sa000006;Alias=sa121750.;
source1 LEN descriptive_1 347900 348600 . . . Parent=sa000007.1;supp_id=1800.1;

```

The output file didn't have the  entries  corresponding to which were originally  correct and needed no editing.
For eg  in this case it removed the lines 
```

source1 LEN predictive 347310 348798 0.485927 - . Name=sa000007.1;ID=sa000006;Alias=sa121750.;
source1 LEN descriptive_1 347900 348600 . . . Parent=sa000007.1;supp_id=1800.1;



```Also, is it possible to  not remove any spaces as its required  for further parsing.

outfile obtained :

```
source1 LEN predictive 347154 351449 0.485927 - . Name=sa000006.1;ID=sa000006;Alias=sa121750.;
source1 LEN descriptive_1 348799 351449 . . . Parent=sa000006.1;supp_id=1800.1;
source1 LEN descriptive_3 347154 347319 . . . Parent=sa000006.1;supp_id=1800.1;




```

---

### Post by sbz on 2014-03-08
Intended result : 

> source1 LEN predictive 347154 351449 0.485927 - . Name=sa000006.1;ID=sa000006;Alias=sa121750.;
source1 LEN descriptive_1 348799 351449 . . . Parent=sa000006.1;supp_id=1800.1;
source1 LEN descriptive_3 347154 347319 . . . Parent=sa000006.1;supp_id=1800.1;

source1 LEN predictive 347310 348798 0.485927 - . Name=sa000007.1;ID=sa000006;Alias=sa121750.;
source1 LEN descriptive_1 347900 348600 . . . Parent=sa000007.1;supp_id=1800.1

---

### Post by Vaphell on 2014-03-08
are these empty lines between the blocks in original data or it's only for visual purposes? These empty lines would be convenient to have.

Having only 3 lines of example I assumed descriptive_3 is always there and only after that line i made comparisons and fixes.
I'll fix it.

Also where are the spaces and tabs and in what numbers? I can't figure that out from the example that lost that info already. 
It's easier for me to break the line apart to extract relevant numbers and then rebuild it than jump through the hoops to do direct replacements on the whole line. It's possible but you need to tell such things explicitly upfront so the dead end approaches can be avoided.

---

### Post by sbz on 2014-03-08
Oh! Sorry for being unclear in my first  post!

[FONT=arial]My file has cases of  both descriptive_1 and descritpive_3.[/FONT]
[FONT=arial]In some cases of a particular group there is existence of  only one descriptive statement then we would have to compare the predictive value with  the existent descriptive_ statement.[/FONT]
here is the original file with some more lines

```
[FONT=arial]source1 LEN predictive 347320 348798 0.485927 - . Name=sa000006.1;ID=sa000006;Alias=sa121750.;[/FONT]
[FONT=arial]source1 LEN descriptive_1 348799 351449 . . . Parent=sa000006.1;supp_id=1800.1;[/FONT]
[FONT=arial]source1 LEN descriptive_3 347154 347319 . . . Parent=sa000006.1;supp_id=1800.1;[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]source1 LEN predictive 347310 348798 0.485927 - . Name=sa000007.1;ID=sa000006;Alias=sa121750.;[/FONT]
[FONT=arial]source1 LEN descriptive_1 347900 348600 . . . Parent=sa000007.1;supp_id=1800.1;[/FONT]
[FONT=arial]source1 LEN predictive 346210 349798 0.485927 - . Name=sa000009.1;ID=sa000006;Alias=sa121750.;[/FONT]
[FONT=arial]source1 LEN descriptive_3 346900 349200 . . . Parent=sa000009.1;supp_id=1800.1;[/FONT]
[FONT=arial]
[/FONT]

```[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]There are tabs between source1 and LEN and predictive and so on.All of the words in a single line are separated by tabs and the next line is next statement.[/FONT]
[FONT=arial]What I implied was I dont want to lose any spaces in between each new statement.[/FONT]
[FONT=arial]I would like to retain everything but correct the wrong values.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]I hpe am not confusing [/FONT]

---

### Post by Vaphell on 2014-03-08
try this

```
#!/usr/bin/env python

import sys

def fix_lines( rows ):
    if len(rows) > 0:
        rows[0][3] = str( min( int(r[3]) for r in rows ) )   
        rows[0][4] = str( max( int(r[4]) for r in rows ) )   
        for r in rows:
            print '\t'.join( r )

rows = []
for l in open( sys.argv[1] ):
    if 'predictive' in l:
        fix_lines( rows )
        rows = []
        rows.append( l.strip().split() )
    elif 'descriptive' in l:
        rows.append( l.strip().split() )
    else:
       fix_lines( rows )
       rows = []
       print l.strip()
fix_lines( rows )
```

---

### Post by sbz on 2014-03-08
Sorry for the doubt!
will this script  take into account for both descriptives ? descriptive_1 and descriptive_5.

Its my mistake as I should have given all the possible variations in this file.

I didnt want to fill up the page with many lines of file


This is part of file  which I tried but it didn't quite work.

> source1      LEN        predictive    392879  394347  0.955489        +       .       Name=sa3.1;ID=sa3;source_id=shLEN_10020387;identical_supp_id=.;p_supp_id=CUFF14.1805.1,CUFF14.1805.1;Alias=sa121751.1;
source1      LEN        malign    392879  394347  0.955489        +       .       Name=sa3.1;ID=sa3.1;source_id=shLEN_10020387;identical_supp_id=.;p_supp_id=CUFF14.1805.1,CUFF14.1805.1;Alias=sa121751.1;
source1      LEN        descriptive_5   391082  392878  .       .       .       Parent=sa3.1;supp_id=CUFF14.1805.1;
source1      LEN        Cancer     392879  393028  .       +       0       Parent=sa3.1;
source1      LEN        predictive    408863  416522  0.999853        -       .       Name=sa4.1;ID=sa4;source_id=shLEN_10020388;identical_supp_id=CUFF14.1812.2;p_supp_id=.;
source1      LEN        malign    408863  416522  0.999853        -       .       Name=sa4.1;ID=sa4.1;source_id=shLEN_10020388;identical_supp_id=CUFF14.1812.2;p_supp_id=.;
source1      LEN        descriptive_5   416523  416853  .       .       .       Parent=sa4.1;supp_id=CUFF14.1812.2;
source1      LEN        Cancer     416403  416522  .       -       0       Parent=sa4.1;
source1      LEN        descriptive_3   408716  408862  .       .       .       Parent=sa4.1;supp_id=CUFF14.1812.3;
source1      LEN        predictive    159485  170778  0.999006        -       .       Name=sa5.1;ID=sa5;source_id=shLEN_10020383;identical_supp_id=.;p_supp_id=CUFF14.1731.2,CUFF14.1731.2;
source1      LEN        malign    159485  170778  0.999006        -       .       Name=sa5.1;ID=sa5.1;source_id=shLEN_10020383;identical_supp_id=.;p_supp_id=CUFF14.1731.2,CUFF14.1731.2;
source1      LEN        descriptive_5   170779  174239  .       .       .       Parent=sa5.1;supp_id=CUFF14.1731.2;
source1      LEN        Cancer     168139  170778  .       -       0       Parent=sa5.1;
source1      LEN        predictive    347320  348798  0.485927        -       .       Name=sa6.1;ID=sa6;source_id=shLEN_10020386;identical_supp_id=CUFF14.1800.1;p_supp_id=.;Alias=sa121750.1,sa57152.1;
source1      LEN        malign    347320  348798  0.485927        -       .       Name=sa6.1;ID=sa6.1;source_id=shLEN_10020386;identical_supp_id=CUFF14.1800.1;p_supp_id=.;Alias=sa121750.1,sa57152.1;
source1      LEN        descriptive_5   348799  351449  .       .       .       Parent=sa6.1;supp_id=CUFF14.1800.1;
source1      LEN        Cancer     347320  348798  .       -       0       Parent=sa6.1;
source1      LEN        descriptive_3   347154  347319  .       .       .       Parent=sa6.1;supp_id=CUFF14.1800.1;




Sorry for the inconvenience!

---

### Post by Vaphell on 2014-03-08
yep, examples don't have to be long, but should represent raw real life data accurately enough to allow for taking care of all the caveats. btw ```
 tags are better than [quote] because they don't obfuscate original format with word wrapping.

what to do with all these lines with cancers and maligns? Do they end the data block (in the 'descriptive'/'predictive' context) or are they just noise within it that needs to be copied verbatim?
What exactly constitutes a data block? Is it 'everything starting from predictive to the next predictive/empty line'?

is the sequence at the end (predictive/malign/desc5/Cancer/desc3) a single unit where desc3/5 have to influence the 'predictive' line?


assuming that's the case, try this

[code]#!/usr/bin/env python

import sys

def fix_and_print( rows ):
    if len(rows) > 0:
        start = [ int(r[3]) for r in rows if isinstance( r, (list) ) ]
        end = [ int(r[4]) for r in rows if isinstance( r, (list) ) ]
        rows[0][3] = str( min( start ) )   
        rows[0][4] = str( max( end ) )   
        for r in rows:
            if isinstance( r, (list) ):
                print '\t'.join( r )
            else:
                print r

rows = []
for l in open( sys.argv[1] ):
    if 'predictive' in l:
        fix_and_print( rows )
        rows = []
        rows.append( l.strip().split() )
    elif 'descriptive' in l:
        rows.append( l.strip().split() )
    else:
        rows.append( l.strip() )
fix_and_print( rows )     
 
```

---


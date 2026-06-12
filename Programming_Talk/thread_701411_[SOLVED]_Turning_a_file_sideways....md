---
title: "[SOLVED] Turning a file sideways..."
date: 2008-02-19
forum: Programming Talk
---

### Post by CptPicard on 2008-02-19
Ok, here's something I'd rather not start coding from scratch if I can avoid it... I've got files with records such as 

```

  
Hinta euro:  1,50
Pelin nro:   050-04298388-021

-------------------------------------------------------
Pelattu:     19.02.2008 14:21:07, Veikkauksen pelipalvelu
Kierros      8/2008
Tulosnumero  945
Peli:        Vakioveikkaus - Hajarivit
                                                                                                                                                        

Nr Ottelu                          Rivit
-- ------------------------------- ABCDEF

 1 Liverpool - Middlesbr           XXX1XX
 2 Wigan - Derby                   111221
 3 Fulham - West Ham               111X12
 4 Portsm. - Sunderl.              2222X2
 5 QPR - Sheff.U                   112111
 6 Crystal P - Wolves              222222
 7 Stoke - Ipswich                 2XX111
 8 Scunthorp - Southampt           221122
 9 Norwich - Barnsley              111212
10 Blackpool - Charlton            222222
11 Coventry - Leicester            2XX112
12 Watford - Preston               X11X2X
13 Sheff.W - Cardiff               X21XXX
(* = pikapeli)                     ******

```

and I need to parse out all the columns of 1,X,2s, so that the output is one column of 1X2X12X... on each line. Now, the simplest way to do this would be to be able to just turn the entire file 90 degrees to the left and then grep, but I'm not sure if that's doable... ideas?

---

### Post by ghostdog74 on 2008-02-19
can you show how the output looks like. sorry, can't understand the description. A picture is better:)

---

### Post by Siph0n on 2008-02-19
This seems like a really good assignment!!! :) So the longest (height) of the converted file would be the same as the longest (width) of the file before conversion?

Like in this case, this line is the longest: Pelattu:     19.02.2008 14:21:07, Veikkauksen pelipalvelu

So instead of being a row, it would turn into a column, with height 57, because thats how many characters are in it?

But if your original file is really long(height), than won't the converted file be really long(width) and wont fit across in anything u try and open it with?

Thanks!

---

### Post by CptPicard on 2008-02-19
> **ghostdog74 said:**
> can you show how the output looks like. sorry, can't understand the description. A picture is better:)

Turn the rectangle of 1s, Xs and 2s 90 degrees to the left -- onto its side -- and you've got the output record :)

Anyway, I'm already almost done with this in Python, but it may be of academic interest to someone. :)

---

### Post by popch on 2008-02-19
I would import that as a fixed length record file into OpenOffice Calc. Copy the desired columns, paste 'special'  with the option 'transpose' selected.

Sorry, I can not tell you what the commands and options are called. I am not ATM at a PC with OO, and it would not be an English language version, anyway.

---

### Post by Siph0n on 2008-02-19
If thats the case, can't you just read in each line into their own seperate list, than print it to a seperate file by looping through each list? Like after u have all your lists, than you print out the 1st char from each list, than the 2nd char, and so forth? I just thought of it tho, and didn't test it out....

---

### Post by Wybiral on 2008-02-19
If you can isolate the table, it's pretty trivial in Python. I'm not sure how efficient this would be (depends how big these records are).

```

data = """ 1 Liverpool - Middlesbr           XXX1XX
 2 Wigan - Derby                   111221
 3 Fulham - West Ham               111X12
 4 Portsm. - Sunderl.              2222X2
 5 QPR - Sheff.U                   112111
 6 Crystal P - Wolves              222222
 7 Stoke - Ipswich                 2XX111
 8 Scunthorp - Southampt           221122
 9 Norwich - Barnsley              111212
10 Blackpool - Charlton            222222
11 Coventry - Leicester            2XX112
12 Watford - Preston               X11X2X
13 Sheff.W - Cardiff               X21XXX"""

NEWLINE = '\n'
chars = 6
out = [[] for i in xrange(chars)]

for line in data.split(NEWLINE):
    ending = line[-chars:]
    for i in xrange(chars):
        out[i].append(ending[i])

for line in reversed(out):
    print "".join(line)

```

---

### Post by CptPicard on 2008-02-19
Yes... something like that is what I've got in Python right now :p Just thought to ask if someone has a quicker idea (yes ghostdog, sometimes the shell tools come in handy...) :)

Thanks for the OpenOffice suggestion, I'll have to remember that...

---

### Post by ghostdog74 on 2008-02-19
oh then its called a transposition :) .
In Python
```

a= [list(line.split()[-1]) for line in open("file")]
for i in apply(zip,a):  print ''.join(i)

```

Using awk
```

awk 'BEGIN{FS=""}
   {
       ++numrows
       for ( col=1; col<=NF; ++col ) {
           array[numrows, col] = $col
       }
       numcols = NF
   }
   END {
       for ( c=1; c<=numcols; ++c ) {
           for ( r=1; r<=numrows; ++r ) {
               if ( r>1 ) printf FS
               printf "%s", array[r, c]
           }
           print ""
       }
   }
' "input"

```

---

### Post by pmasiar on 2008-02-19
How big is the file? Can you keep it all in RAM, or you cannot, so you need to process it in parts?

---

### Post by CptPicard on 2008-02-19
> **ghostdog74 said:**
> oh then its called a transposition :) .


Actually, a transposition is a flip across the diagonal :) This isn't strictly a transposition, but actually a transposition works just as well, just returns the rows in reverse order.

@pmasiar, yes it fits in RAM and I've done it already in Python :p

---


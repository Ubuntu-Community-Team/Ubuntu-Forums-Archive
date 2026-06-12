---
title: "Python for text parsing"
date: 2009-07-22
forum: Programming Talk
---

### Post by crownedzero on 2009-07-22
Supposing you had a massive text file with tagged data, if you wanted to parse this into some nice and neat package what would be the best way to go about this? By tagged I mean each row starts with TXID and ends with CLTX. However, the information in between does not always match up. For instance one transaction may have only needed 1 column for an address ADD1, while another needed 2 ADD1 and ADD2 respectively. 

```

TXID    ADD1            CLTX
TXID    ADD1    ADD2    CLTX
TXID    ADD1    ADD2    CLTX
TXID    ADD1            CLTX

```

I thought I had it figured out until I realized my columns didn't match up. Thoughts?

---

### Post by The Cog on 2009-07-22
That all depends on how you want the data summarised. This might do for starters but it's not python:
sort bigfile.txt | uniq -c

What do you want to do with it?

---

### Post by wmcbrine on 2009-07-22
Yeah, the problem needs better specification.

But I assume you're looking at that data, and thinking that you can't use .split(), since the columns wouldn't line up. But if it's all space-padded like that, you could use substrings:

```
add1 = data[8:12]
add2 = data[16:20]
```

---

### Post by raf_kig on 2009-07-22
> **crownedzero said:**
> 
```

TXID    ADD1            CLTX
TXID    ADD1    ADD2    CLTX
TXID    ADD1    ADD2    CLTX
TXID    ADD1            CLTX

```

I thought I had it figured out until I realized my columns didn't match up. Thoughts?
Depends heavily on what you really want to end up with.
For the following I'll be assuming that TXID is some sort of unique transaction id and that the delimiter is a tab character.

```

parsed = {}
for line in infile:
  split = line.split('\t')
  parsed[split[0]] = split[1:-1]

```

This will give you a dictionary with TXID as key and a list [ADD1, ..., ADDN] excluding CLTX as value.
Of course you could just use a list for storing everything if TXID was irrelevant:
```

parsed = [line.split('\t')[1:-1] for line in infile]

```

Regards,

raf

---

### Post by soltanis on 2009-07-22
According to what you specified, each "tagged" row beings with TXID and ends with CLTX.

Use a regular expression.

```

import re

# open file up here

p = re.compile("^TXID\t([\w\t]*?)\tCLTX$");
for line in file:
    if p.search(line):
        columns = p.groups()[0].split("\t")
        # do something with the columns...

```

---

### Post by crownedzero on 2009-07-22
Not at work anymore but an example of the data would be:

```

*TXID0123*ADD123SomewhereStr*CLTX1*TXID0124*ADD1AptF*ADD2Building9*CLTX1*TXID0125*
ADD1Apt4*ADD2BuildingP*CLTX1*TXID0126*ADD1234NowhereBlvd*CLTX1
```

with the end result being:

```

TXID    ADD1            CLTX
TXID    ADD1    ADD2    CLTX
TXID    ADD1    ADD2    CLTX
TXID    ADD1            CLTX

```

I had assumed I could remove the whitespace and just delimit by the *, at this point I realized not ever row contains all the same headers. Still pretty new to Python and as you can imagine I got lost quick.

---

### Post by crownedzero on 2009-07-22
> **soltanis said:**
> According to what you specified, each "tagged" row beings with TXID and ends with CLTX.

Use a regular expression.

```

import re

# open file up here

p = re.compile("^TXID\t([\w\t]*?)\tCLTX$");
for line in file:
    if p.search(line):
        columns = p.groups()[0].split("\t")
        # do something with the columns...

```
I did something similar more or less with a find/replace function creating each record on a new row.

---

### Post by ghostdog74 on 2009-07-22
> **crownedzero said:**
> Not at work anymore but an example of the data would be:

```

*TXID0123*ADD123SomewhereStr*CLTX1*TXID0124*ADD1AptF*ADD2Building9*CLTX1*TXID0125*
ADD1Apt4*ADD2BuildingP*CLTX1*TXID0126*ADD1234NowhereBlvd*CLTX1
```

with the end result being:

```

TXID    ADD1            CLTX
TXID    ADD1    ADD2    CLTX
TXID    ADD1    ADD2    CLTX
TXID    ADD1            CLTX

```

I had assumed I could remove the whitespace and just delimit by the *, at this point I realized not ever row contains all the same headers. Still pretty new to Python and as you can imagine I got lost quick.

not Python, but awk
```

awk 'BEGIN{RS="CLTX1"}
{
 gsub(/^\*|\*$/,"")
 m=split($0,t,"*")
 for(i=1;i<m;i++){
    printf "%s ",t[i]
 }  
 print t[m],RT
}' file

```
output
```

# ./test.sh
TXID0123 ADD123SomewhereStr CLTX1
TXID0124 ADD1AptF ADD2Building9 CLTX1
TXID0125 ADD1Apt4 ADD2BuildingP CLTX1
TXID0126 ADD1234NowhereBlvd CLTX1


```

---

### Post by crownedzero on 2009-07-23
> **ghostdog74 said:**
> not Python, but awk
```

awk 'BEGIN{RS="CLTX1"}
{
 gsub(/^\*|\*$/,"")
 m=split($0,t,"*")
 for(i=1;i<m;i++){
    printf "%s ",t[i]
 }  
 print t[m],RT
}' file

```
output
```

# ./test.sh
TXID0123 ADD123SomewhereStr CLTX1
TXID0124 ADD1AptF ADD2Building9 CLTX1
TXID0125 ADD1Apt4 ADD2BuildingP CLTX1
TXID0126 ADD1234NowhereBlvd CLTX1


```

I wish I understood awk a little better lol =0

---

### Post by crownedzero on 2009-07-23
Ok, so I'm thinking recompile would be the best way to work through this.
The tag TXID begins a new row, re.compile then takes all of the needed information from that row that I need.
The tag CLTX would end the row so the next could begin with TXID.
Examples of the tags I need to find in between would be *13G, *1HG, *1D8, *16V.

So upon running the code it should leave me with:
```

*TXID0123*13G(12 digit num)*16V(Style)*1HG(Size)*1D8(Price)*CLTX1
*TXID0124*13G(12 digit num)*16V(Style)*1HG(Size)*1D8(Price)*CLTX1

```
and dump everything else.

I attempted to run this on a smaller level i.e. 
```

import re

inputFile = file('test.txt','r')
text = inputFile.read()
inputFile.close()
data = re.compile(r'''\*13G+\*)''', text)
outputFile = file('compile.txt', 'w')
outputFile.write(data)
outputFile.close()

```
But my expression is off as its raising TypeError: unsupported operand type(s) for &: 'str' and 'int'

Any thoughts?

Thanks in advance,

---

### Post by smartbei on 2009-07-24
That isn't how you use re - that is the problem. See the example below:
```

import re
reobj = re.compile(pattern)
matches = reobj.findall(text)
## matches now holds a list of matches.

```
Here is a regex (relatively complicated, maybe there is a simpler way)
```

import re
reobj = re.compile("TXID(\d{4})\*ADD1([^\*]*)\*(?:(?:ADD2([^\*]*)\*)|(?:))CLTX1")
matches = reobj.findall(text)
## this works for me... try printing out matches.

```
As for what it does, lets break it up:
[list=1]
[*]```
TXID(\d{4})
``` Here we are simply matching the string TXID, and the 4 digits after it. We put parentheses around the digit-matching because we want to return it.
[*]```
ADD1([^\*]*)
``` Here we are matching ADD1, and then all the characters after it up to the first * we find. Again, parentheses mean that the address string itself is returned.
[*]```
(?:(?:ADD2([^\*]*)\*)|(?:))
``` The syntax (?: ...) works like you would expect parentheses to - it groups together pieces of RE pattern that would otherwise work independently. We need this because we have a bit of logic in the pattern - the | character means that it will try to match the pattern on its left, and failing that, will match the one on its right. Lets break that up now.
[list=1]
[*]```
(?:ADD2([^\*]*)\*)
``` This is very similar to what we had before - we are trying to match the string ADD2, and after it all the characters until the next *. This we stick in normal parentheses so it will be returned. Note that after the parentheses we match the ending * (It is escaped because * is a special character).
[*]```
(?:)
``` Just an empty group, because we need to have something on the right.
[/list]
[*]```
CLTX1
``` We match the ending tag just to complete the line.
[/list]

---

### Post by unutbu on 2009-07-24
Building off of smartbei's work, 
[list]
[*] you could shorten the regex a little bit by changing

```
([^\*]*)
```

to

```
([^*]*)
```

Inside brackets [...], the * is automatically treated as a literal '*' character.
Outside the brackets, * matches 0-or-more occurrences of a pattern, and \* is needed to indicate a literal '*' character.

[*]
```
(?:(?:ADD2([^\*]*)\*)|(?:))
```
can be shortened to
```
(?:ADD2([^*]*)\*|(?:))
```
The (?:...) pattern is used when you want to collect a pattern together, but do not want the re pattern matcher to return it as a matched group. Since ADD2 is already surrounded by (?:...), (tests corroborate) you don't have to do it again.
[/list]

---

### Post by crownedzero on 2009-07-24
Thanks guys I'm going to play with this and see if I can get a better grasp on it.

---

### Post by ghostdog74 on 2009-07-24
much said about regex, however, you could do what you want, without regex. just so to let you know.

---

### Post by ptmcg on 2009-07-26
Here is a stab at your problem using the pyparsing module. I assumed that you would be more interested in the data associated with the tags, as opposed to the tags themselves:
```
 
data  = """*TXID0123*ADD123SomewhereStr*CLTX1*TXID0124*ADD1AptF*ADD2Building9*CLTX1*TXID0125*
ADD1Apt4*ADD2BuildingP*CLTX1*TXID0126*ADD1234NowhereBlvd*CLTX1"""
 
from pyparsing import *
STAR = Suppress("*")
start = Literal("TXID")
end = Literal("CLTX1")
add1 = Literal("ADD1")
add2 = Literal("ADD2")
field = SkipTo("*")
entry = STAR + start + field("txid") + STAR + \
        add1 + field("add1") + STAR + \
        Optional(add2 + field("add2")+STAR) + \
        end
 
# use the entry definition to search data for matching text
for e in entry.searchString(data):
    print e.txid
    print e.add1
    if e.add2: print e.add2
    print

```
 
Prints:
```
 
0123
23SomewhereStr
 
0124
AptF
Building9
 
0125
Apt4
BuildingP
 
0126
234NowhereBlvd

```
 
Pyparsing wont run as fast as re's, but it is often quicker to whip something together.
 
You can read more about pyparsing at [http://pyparsing.wikispaces.com](http://pyparsing.wikispaces.com).
 
-- Paul

---

### Post by crownedzero on 2009-07-27
I'm still going around in circles with this, so I'm sharing some the actual data(tags + data has been changed to protect the innocent.=))This is something I normally do by hand and to shorten this up to a small script would be great.

*TG1 starts the transaction *TG31 is the end of that transaction.
*From each string I'm looking to pull several tags containing data. In this example they are numbered TG1-TG31. 

```

TG01*TG1Customer1*TG2000*TG300   *TG4SA   *TG50000000001*TG6MM/DD/YYYY*TG7IA   *TG8000001*TG9N    *TG1001   *TG1101*TG12Shipping terms*TG13001  *TG14MM/DD/YYYY*TG15001  *TG16000001*TG17BY   *TG18TSC*TG1901   *TG200001*TG2110*TG221*TG23EA   *TG249.99*TG25IN   *TG267472062*TG27VN   *TG28JD0185*TG29UP   *TG30679145773751*TG2120*TG221*TG23EA   *TG249.99*TG25IN   *TG267472070*TG27VN   *TG28JD0185*TG29UP   *TG30679145773768*TG2130*TG221*TG23EA   *TG249.99*TG25IN   *TG267472088*TG27VN   *TG28JD0185*TG29UP   *TG30679145773775*TG2140*TG221*TG23EA   *TG249.99*TG25IN   *TG267472096*TG27VN   *TG28JD0185*TG29UP   *TG30679145773782*TG2150*TG221*TG23EA   *TG249.99*TG25IN   *TG267472101*TG27VN   *TG28JD0185*TG29UP   *TG30679145773799*TG2160*TG221*TG23EA   *TG249.99*TG25IN   *TG267472119*TG27VN   *TG28JD0186*TG29UP   *TG30679145773805*TG2170*TG221*TG23EA   *TG249.99*TG25IN   *TG267472127*TG27VN   *TG28JD0186*TG29UP   *TG30679145773812*TG2180*TG221*TG23EA   *TG249.99*TG25IN   *TG267472135*TG27VN   *TG28JD0186*TG29UP   *TG30679145773829*TG2190*TG221*TG23EA   *TG249.99*TG25IN   *TG267472143*TG27VN   *TG28JD0186*TG29UP   *TG30679145773836*TG21100*TG221*TG23EA   *TG249.99*TG25IN   *TG267472151*TG27VN   *TG28JD0186*TG29UP   *TG30679145773843*TG21110*TG221*TG23EA   *TG249.99*TG25IN   *TG267472169*TG27VN   *TG28JD0188*TG29UP   *TG30679145775168*TG21120*TG221*TG23EA   *TG249.99*TG25IN   *TG267472177*TG27VN   *TG28JD0188*TG29UP   *TG30679145775175*TG21130*TG221*TG23EA   *TG249.99*TG25IN   *TG267472185*TG27VN   *TG28JD0188*TG29UP   *TG30679145775182*TG21140*TG221*TG23EA   *TG249.99*TG25IN   *TG267472193*TG27VN   *TG28JD0188*TG29UP   *TG30679145775199*TG21150*TG221*TG23EA   *TG249.99*TG25IN   *TG267472208*TG27VN   *TG28JD0188*TG29UP   *TG30679145775205*TG311

```
Now bear with me in my crappy execution of pseudocode.
```

open file.txt
read file.txt and assign it to data var
close file.txt

set a string var TG1 thru TG31 in data
create regex expression for re.compile(exp) of string
(unclear whether I need to create a var for each expression)
set matches to all regex expressions found in string

create outfile.txt
for each string in data
for each match in string
write each match within string to outfile.txt
close file.txt

```

This is the end desired result.
```

*TG1Customer1
*TG249.99*TG267472062*TG28JD0185*TG30679145773751
*TG249.99*TG267472070*TG28JD0185*TG30679145773768
*TG249.99*TG267472088*TG28JD0185*TG30679145773775
*TG249.99*TG267472096*TG28JD0185*TG30679145773782
*TG249.99*TG267472101*TG28JD0185*TG30679145773799
*TG249.99*TG267472119*TG28JD0186*TG30679145773805
*TG249.99*TG267472127*TG28JD0186*TG30679145773812
*TG249.99*TG267472135*TG28JD0186*TG30679145773829
*TG249.99*TG267472143*TG28JD0186*TG30679145773836
*TG249.99*TG267472151*TG28JD0186*TG30679145773843
*TG249.99*TG267472169*TG28JD0188*TG30679145775168
*TG249.99*TG267472177*TG28JD0188*TG30679145775175
*TG249.99*TG267472185*TG28JD0188*TG30679145775182
*TG249.99*TG267472193*TG28JD0188*TG30679145775199
*TG249.99*TG267472208*TG28JD0188*TG30679145775205
*TG3115

```

Again thanks for all your help with this.

---

### Post by wmcbrine on 2009-07-28
Still underspecified. It's not at all clear why you're selecting the specific parts you're selecting, nor are the "numbers" you mention (TG1-TG31) present, as far as I can see.

If you could adequately describe the problem, then the solution should just about present itself. Forget the pseudocode you showed above; it doesn't tell us anything. You say you normally do this process manually -- describe *that*, in enough detail that one of us could repeat it, and get the desired result. Don't worry about putting it into computer-oriented terms yet.

---

### Post by The Cog on 2009-07-29
Actually, the string "*TG1" appears 12 times in that sample. 

What prevents the first "*TG1" introducing a customer with the name "1"? What prevents the third "*TG1" introducing a customer with the name "001"? 

What makes "TG311" special so you know it's the end of the transaction?

---

### Post by crownedzero on 2009-07-30
> **The Cog said:**
> Actually, the string "*TG1" appears 12 times in that sample. 

What prevents the first "*TG1" introducing a customer with the name "1"? What prevents the third "*TG1" introducing a customer with the name "001"? 

What makes "TG311" special so you know it's the end of the transaction?

It's TG1 only in the sense your not looking far enough to the right i.e. TG10, TG11, TG12, TG13. And 'TG31' is the end sequence tag.

---

### Post by The Cog on 2009-07-30
Something like this might do the trick:
```
f = open(FILENAME)
records = f.read().split("*TG0")
f.close()
for record in records:
    fields = record.split("*")
    print "*" + fields[1]
    line = ""
    for field in fields[5:]:
        if field.startswith("TG24"):
            line += "*" + field
        elif field.startswith("TG26"):
            line += "*" + field
        elif field.startswith("TG28"):
            line += "*" + field
        elif field.startswith("TG30"):
            line += "*" + field
            print line
            line = ""
        elif field.startswith("TG31"):
            print "*" + field + "5"
   
```
but it makes many assumptions about your data that you haven't specified:
* Records always start with "*TG0" and that can't appear elsewhere
* The second tag is always TG1
* There are at least 5 tags before tags before the interesting ones
* Tags 2 and 3 never repeat after the first 5 positions.
* Tag 31 is the one that ends a line in the output and always needs that 5 adding at the end
* tag numbers are only 1 or 2 digit numbers

This is a crap format. Whoever invented it should be shot. Slowly.

---

### Post by crownedzero on 2009-07-31
> 
This is a crap format. Whoever invented it should be shot. Slowly.
^ Truer words were never spoken.
```

Traceback (most recent call last):
  File , line 6, in <module>
    print "*" + fields[1]
IndexError: list index out of range

```

---

### Post by The Cog on 2009-07-31
Then I think the file format is different to what you posted. I can't really help exscept to suggest that you put a try/except round the loop body and print out the offending record to see what is in it.

---


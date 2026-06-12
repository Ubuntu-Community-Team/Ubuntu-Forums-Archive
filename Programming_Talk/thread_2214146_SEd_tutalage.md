---
title: "SEd tutalage"
date: 2014-03-30
forum: Programming Talk
---

### Post by ylafont on 2014-03-30
was wonder if any experienced SED programmer would point me the right direction with SED. I have  the following  command:

sed -ne '/[A-Z][0-9]\{1,\}\.[0-9]\{1,\}\.[0-9]\{1,\}/p'  which correctly prints the correct contents, However it prints the entire line. as follows.


        <channel id="I9.1.43584439.microsoft.com">
        <channel id="I9.3.273073824.microsoft.com">
        <channel id="I9.4.290647859.microsoft.com">
        <channel id="I24.1.273073819.microsoft.com">
        <channel id="I25.1.195990922.microsoft.com">
        <channel id="I25.3.290208797.microsoft.com">
        <channel id="I31.1.195990477.microsoft.com">
        <channel id="I47.1.195990900.microsoft.com">

i wanted to have only the results of the pattern printed , so i modified the line as follows

sed -ne '/**\(**[A-Z][0-9]\{1,\}\.[0-9]\{1,\}\.[0-9]\{1,\}**\)**/**\1**/p'  - to included the results of pattern  as a backreference wiht **\(  \)**, and the proceeded to print out the back reference with **\1 ** 

however i get the following error

sed: -e expression #1, char 49: unknown command: `\'

I though i had correct, but maybe i am missing something.  thanks for the assistance.

---

### Post by dragonfly41 on 2014-03-30
I'm also playing around with / learning sed expressions .. 

thought you might find these useful for testing expressions ..

[http://www.regexr.com/](http://www.regexr.com/)

[http://www.hongkiat.com/blog/regular-expression-tools-resources/](http://www.hongkiat.com/blog/regular-expression-tools-resources/)

---

### Post by ylafont on 2014-03-30
The first may not be useful, as it related to regular regex expression. I found it difficult to troubleshoot. for instance. 

[COLOR=#000000][FONT=Arial]i have figure out that there is no \d (any digit) in SED, [0-9] must be used instead. the command line

[/FONT][/COLOR][COLOR=#000000][FONT=Arial]**sed -ne '/[A-Z]\d+\.\d+\.\d+/p' INPUTFILE **has to be express as    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]**sed -ne '/[A-Z][0-9]\{1,\}\.[0-9]\{1,\}\.[0-9]\{1,\}/p' INPUTFILE**

Also, the bracket { } must be escaped. \{ \} when they are used to specify one or many.[/FONT][/COLOR]



There is a  SedCBT that  helps.  but does not fully encompass nuances between version between regex and sed

[http://www.linuxcbt.com/products_linuxcbt_awk-sed_edition.php](http://www.linuxcbt.com/products_linuxcbt_awk-sed_edition.php)

---

### Post by steeldriver on 2014-03-30
It's only valid in a substitution command, I think

```

$ sed -ne '**s/.*\(**[A-Z][0-9]\{1,\}\.[0-9]\{1,\}\.[0-9]\{1,\}**\).***/\1/p' *yourfile*
I9.1.43584439
I9.3.273073824
I9.4.290647859
I24.1.273073819
I25.1.195990922
I25.3.290208797
I31.1.195990477
I47.1.195990900

```

EDIT: it might be easier to do it with **grep -o** or grep -Eo - the -E (extended regex) works much the same as sed's -r , allowing unescaped {} () sequences

```

grep -o '[A-Z][0-9]\{1,\}\.[0-9]\{1,\}\.[0-9]\{1,\}' *yourfile*

grep -Eo '[A-Z][0-9]{1,}\.[0-9]{1,}\.[0-9]{1,}' *yourfile*

sed -nre 's/.*([A-Z][0-9]{1,}\.[0-9]{1,}\.[0-9]{1,}).*/\1/p'

```

---

### Post by ylafont on 2014-03-30
[COLOR=#000000][FONT=Ubuntu Mono]steeldriver,  you are right!
[/FONT][/COLOR][FONT=Ubuntu Mono][COLOR=#000000]
[/COLOR][/FONT][FONT=Ubuntu Mono][COLOR=#000000]sed -ne '[/COLOR][/FONT]**s/.*\(**[FONT=Ubuntu Mono][COLOR=#000000][A-Z][0-9]\{1,\}\.[0-9]\{1,\}\.[0-9]\{1,\}[/COLOR][/FONT]**\).***[FONT=Ubuntu Mono][COLOR=#000000]/\1/p' [/COLOR][/FONT][I][FONT=Ubuntu Mono][COLOR=#000000]yourfile  does work. 
[/COLOR][/FONT][FONT=Ubuntu Mono][COLOR=#000000]
[/COLOR][/FONT][FONT=Ubuntu Mono][COLOR=#000000]just for my clarification, can you explain why the .* needs to be included at the beginning and end of the expression?  the expression already contains all proper patterns?
[/COLOR][/FONT][/I]
::Just took a look the CBT on this topic, and  it  mentioned that  you can use Substitute or find to be able to use the back-reference.  
 I wonders why so many inconsistencies across platforms on SED.

Will try to experiment with grep on this topic.

**one other question.- how would one concatenated  results from two or more lines?**

---

### Post by steeldriver on 2014-03-30
The .* parts just match everything before and after the thing you're trying to match - so it's a way of saying "replace everything on the line (including the matching text) with \1". Without them, it replaces the matching text with itself *but leaves the remainder of the line unchanged* (which is the same as not replacing anything).

---

### Post by ylafont on 2014-03-30
Thanks for the explanation. it helps..

---

### Post by Vaphell on 2014-03-30
> sed -ne '/[A-Z]\d+\.\d+\.\d+/p' INPUTFILE has to be express as sed -ne '/[A-Z][0-9]\{1,\}\.[0-9]\{1,\}\.[0-9]\{1,\}/p' INPUTFILE

not really, because **+** does work in sed: **\+** by default, **+** in case of "tidy" *sed -r*. Unsupported \d stuff is true though

```
$ echo 'a1b2' | sed -r 's/[0-9]+/X/g'
aXbX
$ echo 'a1b2' | sed 's/[0-9]\+/X/g'
aXbX
```



What do you mean by concatenation?

---

### Post by ylafont on 2014-03-30
I need to place the result of 3 or more lines on two one. as a full example.  the text being parsed is. 

	<channel id="I2.1.28459048.microsoft.com">
		<display-name>2.1 WCBSDT</display-name>
		<display-name>2.1</display-name>
		<display-name>33 WCBSDT fcc</display-name>
		<display-name>WCBSDT</display-name>
		<display-name>WCBSDT (WCBS-DT)</display-name>
		<display-name>CBS Affiliate</display-name>
	</channel>
	<channel id="I3.1.290921215.microsoft.com">
		<display-name>3.1 WBQMLD</display-name>
		<display-name>3.1</display-name>
		<display-name>50 WBQMLD fcc</display-name>
		<display-name>WBQMLD</display-name>
		<display-name>WBQMLD (WBQM-LD)</display-name>
		<display-name>Low Power</display-name>
	</channel>

my my completed file should look like

I2.1.28459048  2.1 WCBSDT   2.1  33 WCBSDT fcc  ect... 


there should be about 1000 entries. thanks,

---

### Post by Vaphell on 2014-03-30
Sed is not for that kind of things, really. Generally you shouldn't try to parse xml with 'dumb' tools like sed and even awk would be iffy. They are inherently unreliable for that because they don't understand the structure of xml and inconsistent formatting can make them fail easily.

script using xml parser in python
```
#!/usr/bin/env python

import sys
import xml.etree.ElementTree as ET

f = open( sys.argv[1] )
tree = ET.parse( f )
xmlroot = tree.getroot()

for node in xmlroot:
    print '{0}\t{1}'.format( '.'.join( node.get('id').split('.')[0:3] ), '\t'.join( x.text for x in node ) )
```

result
```
$ cat channels.xml
<xml>
<channel id="I2.1.28459048.microsoft.com">
<display-name>2.1 WCBSDT</display-name>
<display-name>2.1</display-name>
<display-name>33 WCBSDT fcc</display-name>
<display-name>WCBSDT</display-name>
<display-name>WCBSDT (WCBS-DT)</display-name>
<display-name>CBS Affiliate</display-name>
</channel>
<channel id="I3.1.290921215.microsoft.com">
<display-name>3.1 WBQMLD</display-name>
<display-name>3.1</display-name>
<display-name>50 WBQMLD fcc</display-name>
<display-name>WBQMLD</display-name>
<display-name>WBQMLD (WBQM-LD)</display-name>
<display-name>Low Power</display-name>
</channel>
</xml>
$ ./channels.py channels.xml 
I2.1.28459048	2.1 WCBSDT	2.1	33 WCBSDT fcc	WCBSDT	WCBSDT (WCBS-DT)	CBS Affiliate
I3.1.290921215	3.1 WBQMLD	3.1	50 WBQMLD fcc	WBQMLD	WBQMLD (WBQM-LD)	Low Power


```

---

### Post by ylafont on 2014-03-30
argh! thought that was the fastest method  of getting what i needed without learning a new language. Guess I am going to have to start learning python. 

Thank you for the script! helps EXTRANEOUSLY!

---

### Post by Vaphell on 2014-03-31
well, you've made a classic noob mistake :-) you imagined a solution and asked for help with its building blocks without explaining the greater picture, when in reality you should have asked "how do i get from this data format to that one". Extracting 'words' matching some regex? Sure, sed grep or whatever. Parsing everything and reformatting it? Solution you had for 1 'word' doesn't scale well and the whole thing becomes more "dirty" and fragile with every additional requirement you add.

It is possible to whip up a somewhat working solution with command line tools if you are sure your data format is consistent, for example something like this - assuming 1 record is 7 lines, with simplified regex for the first datafield, just to make the whole thing shorter:
```
sed -rn '/channel/ s/.*"(.*)\.[^.]+\.[^.]+".*/\1/p; /display-name/ s/.*>(.*)<.*/\1/p;' channels.xml | awk '{ printf $0 ((NR%7)?"\t":"\n") }'
I2.1.28459048	2.1 WCBSDT	2.1	33 WCBSDT fcc	WCBSDT	WCBSDT (WCBS-DT)	CBS Affiliate
I3.1.290921215	3.1 WBQMLD	3.1	50 WBQMLD fcc	WBQMLD	WBQMLD (WBQM-LD)	Low Power
```

It doesn't change the fact you pretty much write a barebone xml parser using regexes and hope for the best, given that the layout of the text != xml structure. As the old adage goes
*Some people, when confronted with a problem, think "I know, I'll use regular expressions." Now they have two problems.* ;-)

in case you want to play with the python script, here is the doc of the parser used
[https://docs.python.org/2/library/xml.etree.elementtree.html](https://docs.python.org/2/library/xml.etree.elementtree.html)

---

### Post by dragonfly41 on 2014-03-31
You did not have "\d" in your first example ..

Just to expand further on suggestion of using [www.regexr.com]("http://www.regexr.com") as a validator

If you had broken your sed expression into two regex expressions 

/substitute_this/with_this/

you can validate each of the two strings .. before concatenation into an sed expression

**/**[COLOR=blue]\([A-Z][0-9]\{1,\}\.[0-9]\{1,\}\.[0-9]\{1,\}\)[/COLOR]**/g**   ... validates o.k.

**/**[COLOR=blue]\1[/COLOR][COLOR=blue]/[/COLOR][COLOR=blue]p[/COLOR]**/g**  ... error due to forward slash not being escaped

---

### Post by steeldriver on 2014-03-31
If you absolutely can't use the nice python-based parser that Vaphell provided, then something like this in awk *might* work for you - although you should regard it as 'not robust' for the reasons Vaphell already mentioned. Note that it takes the approach of matching the tag structure and **removing** that, rather than matching and retaining the tag **contents** (which is where the thread started).

```

#!/usr/bin/awk -f

BEGIN {
  RS="</channel>\n"
  ORS="\n"
  FS="\n"
  OFS=" "
}

{
  # remove leading and trailing enclosures from <channel_id="XXX"> tag
  sub("<[^=]*=\"","",$1)
  sub("\"[^>]*>","",$1)

  # remove leading and trailing tags from <fieldname>YYY</fieldname> fields
  gsub("<[^>]*>","",$0)
  gsub("</[^>]*>","",$0)

  print 
}

```

---

### Post by ylafont on 2014-03-31
> **Vaphell said:**
> 

It doesn't change the fact you pretty much write a barebone xml parser using regexes and hope for the best, given that the layout of the text != xml structure. As the old adage goes
*Some people, when confronted with a problem, think "I know, I'll use regular expressions." Now they have two problems.* ;-)

in case you want to play with the python script, here is the doc of the parser used
[https://docs.python.org/2/library/xml.etree.elementtree.html](https://docs.python.org/2/library/xml.etree.elementtree.html)

You are correct about the problems - one thing leads to another.   All ready found the doc, I need to study it a bit to understand its structure. Never used python but I rather use the right tool for the job.

---

### Post by ylafont on 2014-03-31
I tried the /d -did not work with sed so i used [0-9]\{1,\}

**/[COLOR=blue]\1[/COLOR][COLOR=blue]/[/COLOR][COLOR=blue]p[/COLOR][B]/g ... error due to forward slash not being escaped -**[/B] HUmmm,  Would i will have to try this.  did not notice the it was not escaped.

---


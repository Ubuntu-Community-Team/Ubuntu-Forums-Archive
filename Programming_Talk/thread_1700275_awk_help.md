---
title: "awk help"
date: 2011-03-04
forum: Programming Talk
---

### Post by wtfacoconut on 2011-03-04
Hey there. Here's my issue. 

I need to use either awk, grep, sed, or what ever it is so that I can use a regular expression to extract the information that I want from a block of text and append it a variable.  

Example text block:
asdfjkhawelkj Rev.0.1 034987ryhiduf0 Rev. 0.1 
Rev.0.1 lkjoijndfpowieofenapowe4o Rev 0.1 84puio 498r4n9pf8

Example regular expression:
/Revs[0-9]\.[0-9]/

Example 0utput:
Rev 0.1

Please, the answer must use regular expressions inorder to search through a block with no consistent formatting in order to get the desired output.

I've looked at a $|-|1t ton of regular expression and AWK tutorials and looked at enough threads without getting much luck. So if there is already a tutorial out there, my bad, I'm not a lazy mofo, I just honestly couldn't find it. 

Thanks to everyone in advance!

---

### Post by gmargo on 2011-03-05
You'll have to give better examples of input and expected output.  The regular expression you gave does not match anything in your example input.

---

### Post by wtfacoconut on 2011-03-05
Well it was just an example. Right now I kinda suck at regexp, but I simply need how to utilize/setup the awk, sed, or grep tool to utilize a regular expression to extract the desired text. 

In my example, if you ignore my horribly crafted regexp, and only look at the example text block and example output, I still feel that it should be pretty clear what it is that I'm after. Thanks again in advance :D

---

### Post by Rushyang on 2011-03-06
> **gmargo said:**
> You'll have to give better examples of input and expected output.  The regular expression you gave does not match anything in your example input.

agree with gmargo. 

You need to elaborate your question via better example.

---

### Post by Vaphell on 2011-03-06
```

#!/bin/bash

text='asdfjkhawelkj Rev.0.1 034987ryhiduf0 Rev. 0.1
Rev.0.1 lkjoijndfpowieofenapowe4o Rev 0.1 84puio 498r4n9pf8
Something Rev 66.666 some stuff
some other line Rev 0.0011
Rev 0.1'

i=0
echo $text | grep -oP 'Rev\s[0-9]+[.][0-9]+' | sort -u | while read match
do
  (( i++ ))
  echo \#$i: "$match"
done

```

test string is echoed, checked with grep for matches according to Perl style regular expression, results are sorted and duplicates removed, then while loop reads results one line at a time and does stuff with it. Usefulness of that depends on how much it fits your actual needs of course. You need to be more specific: what the input is, what to do with duplicates/multiple matches if they exist, do you need to transform the source text in place or you need that extracted data for something else, etc and what the output should look like.

---

### Post by wtfacoconut on 2011-03-06
Vaphell, thank you! This is what I was looking for! Thank you ans everyone else for your help and consideration. Sorry that I gave a vague and $hi77y example. Marking thread as solved.
:KS

---


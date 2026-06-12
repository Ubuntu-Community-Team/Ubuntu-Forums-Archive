---
title: "Brain Dead ! - This is probably basic (BASH?, SED?, AWK?, GREP?)"
date: 2005-11-25
forum: Programming Talk
---

### Post by JustRandomName on 2005-11-25
Hi,

I am experimenting with bash scripts, I think I am suffering from an information overload, but this is what I want to do:

I have the data:
 
99098909
01 A A X A
02 A W A A
03 A W X A
99889909
01 W X X A
... etc ...
 
and I want to convert it into:
 
99098909
01AAAX
02AAAW
03AAWX
99889909
01AWXX
... etc ...
 
Basically what I am struggling with is changing the order of A , W and X.

I want the order to be like so: `A's, `W's, `X's

I can easily remove the spaces by doing:

sed 's/ //' file

Now I have been searching around the internet for similar problems to this and I don't know the best approach.

From what I have read I could use. SED, AWK or GREP

Now I really don't want to use AWK so that leads GREP and SED

My brain is REALLY hurting atm and ANY help would be splendid

---

### Post by CArenas2 on 2005-11-26
i am not claiming this is pretty, but it works and i didn't use awk:

```

for LINE2 in $( for LINE1 in $( cat sample.txt );
                       do
                           echo $LINE1 | sed 's/[AWX]/\n&/g' | grep '.' | sort;
                           echo %;
                       done );
do
    echo -n $LINE2;
done | sed 's/%/\n/g'

```

assuming the input is contained in **sample.txt**, i break up each line of text into fragments so that each letter is in its own line, sort the fragments, and put it back together.  and i use '%' to keep track of the real (ie, original) newlines.

hope this works for you.  :)

---

### Post by JustRandomName on 2005-11-26
Thanks for the reply CArenas2.

I tried your propsed solution and unfortunatly it didn't work.

The output is the following:
```

96543482
01
A
A
X
A
... etc ...

```

---

### Post by CArenas2 on 2005-11-26
It may not seem obvious, but my solution is a single pipeline -- i just formatted it a bit so you could see it better.  did you run it as such?

if you have a sample data file i can run it on my end to verify that it works.

---

### Post by JustRandomName on 2005-11-26
I have attached a sample.

I appreciate your help, but rather than *do it for me* could you explain to me in psuedo code.

Here is my thinking:

grep for AXD's out put to awk, get awk to order the AXD's, output to sed, get sed to strip the spaces, output to a file

The  only problem with this is that I lose the ID number (the eight numbers every 7 lines.

Regards

---

### Post by CArenas2 on 2005-11-26
ok, here is the explanation:

i use a pipeline with 2 FOR loops, one nested in the other.  the inner loop takes each line of the input file and prepends a newline before each letter, so that SORT can be used to get them in the right order.  the GREP is used to get rid of blank lines.  i also add a delimiter (%) to mark a real newline.

the output of this inner loop is processed in the outer loop, in which i ECHO each line (ie, each fragment of line from the original input) sans newline, so that i get one single line of output.  the final step is to replace the % delimiter with \n, and voila!

hope this helps.  BTW: i did not see any attachment.

---


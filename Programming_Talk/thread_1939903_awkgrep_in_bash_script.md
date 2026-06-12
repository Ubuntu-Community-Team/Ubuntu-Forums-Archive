---
title: "awk/grep in bash script"
date: 2012-03-12
forum: Programming Talk
---

### Post by screechy on 2012-03-12
There is a file xyz.txt, the third line of which can be something like one of the following cases:

 a)  random word, random word , word1, word2, word3, word4, random word
 or
 b) random word, random word, word1, random word
or
 c) random word, word2, word3, random word, random word
or 
d) random word, random word, random word

I want to do the following using awk or grep in bash script.

{
If word1, word2, word3, and word4 all are absent
print 'a' in file output.txt

if only word1 is present
print 'b' in file output.txt

if  word1 && word2 are present
print 'c' in file output.txt


}

Is there a very efficient and fast method of doing it? :confused:

---

### Post by ofnuts on 2012-03-13
> **screechy said:**
> There is a file xyz.txt, the third line of which can be something like one of the following cases:

 a)  random word, random word , word1, word2, word3, word4, random word
 or
 b) random word, random word, word1, random word
or
 c) random word, word2, word3, random word, random word
or 
d) random word, random word, random word

I want to do the following using awk or grep in bash script.

{
If word1, word2, word3, and word4 all are absent
print 'a' in file output.txt

if only word1 is present
print 'b' in file output.txt

if  word1 && word2 are present
print 'c' in file output.txt


}

Is there a very efficient and fast method of doing it? :confused:
Yes, there are two efficient ways, that both involve regular expressions:

Awk: The typical awk process is "if this line matches  the filter, then do this" where the filter can be a regular expression and "do this" can be printing something: some arbitrary string, or the line itself (or part of it). 

Sed: Using very similar regexps to those used with awk, you  substitute the matching lines with a, b, c, or d.

So your only problem with both methods is to come up with regular expressions that match each case (and don't match the others of course).

---

### Post by binouche22 on 2012-03-13
Hi,

Here is a proposal :

```
awk 'NR == 3 {if(/.*word.*word2.*word3.*/) print "a"; else if(/.*word.*word2.*/) print "b"; else if(/.*word.*word2.*word3.*/) print "c"}' input.txt > output.txt
```

hth,
binouche22

---

### Post by screechy on 2012-03-13
thank you binouche22! But, does it suffice the first condition of the words being absent?

---

### Post by binouche22 on 2012-03-13
oops! I answered too hastly ;)!
There's probably a more elegant way to do it but this should work:

```

awk 'NR == 3 {
	if (/.*word1.*/ && $0 !~ /.*word2.*word3.*word4.*/ ) print "b";
	else if ($0 !~ /.*word1.*word2.*word3.*word4.*/) print "a";
	else if (/.*word1.*word2.*/) print "c";
	}' input.txt > output.txt

```

---

### Post by screechy on 2012-03-13
I am trying to test the code! I still have a question! What if instead of the third line, it is the last line of the input file that the operation needs to be done? What can we use instead of NR == 3 ? Thanks a lot!

---

### Post by screechy on 2012-03-13
and what if the word1, word2 and word3 are not necessarily in the same order. i.e. if it is word3, word2, word1, does the regular expression change? :s I think i solved the last line problem. awk 'END{print}'  should solve it, I think!

---

### Post by binouche22 on 2012-03-13
If the order is not predictable, you can use the index() function to check whether a word is present or not:
```

awk 'END{	
	if (!index($0,"word1") > 0 &&
		!index($0,"word2") > 0 && 
		!index($0,"word3") > 0 && 
		!index($0,"word4") > 0 ){
		print "a";
	} else if (index($0,"word1") > 0 &&
		!index($0,"word2") > 0 && 
		!index($0,"word3") > 0 && 
		!index($0,"word4") > 0 ){
		print "b";
	} else if (index($0,"word1") > 0 &&
		index($0,"word2") > 0 && 
		!index($0,"word3") > 0 && 
		!index($0,"word4") > 0 ){
		print "c";
	}     
}' input.txt > output.txt

```

---

### Post by screechy on 2012-03-13
I removed the .* part from /.*word/ and it worked too! But, this is more elegant! Thank you! :)

---

### Post by ofnuts on 2012-03-13
> **binouche22 said:**
> If the order is not predictable, you can use the index() function to check whether a word is present or not:
```

awk 'END{    
    if (!index($0,"word1") > 0 &&
        !index($0,"word2") > 0 && 
        !index($0,"word3") > 0 && 
        !index($0,"word4") > 0 ){
        print "a";
    } else if (index($0,"word1") > 0 &&
        !index($0,"word2") > 0 && 
        !index($0,"word3") > 0 && 
        !index($0,"word4") > 0 ){
        print "b";
    } else if (index($0,"word1") > 0 &&
        index($0,"word2") > 0 && 
        !index($0,"word3") > 0 && 
        !index($0,"word4") > 0 ){
        print "c";
    }     
}' input.txt > output.txt

```
If you want to go this way, wouldn't 
```

    if ($3 == "word1" && $4 == "word2" && $5 == "word3" && $6 == "word4")
        print "a";

```
cover all bases for "a") (once you add a check for the presence of a 7th word) ?

---

### Post by binouche22 on 2012-03-13
> If you want to go this way, wouldn't 
Code:
    if ($3 == "word1" && $4 == "word2" && $5 == "word3" && $6 == "word4")
        print "a";
cover all bases for "a") (once you add a check for the presence of a 7th word) ?

This only works if "word1" is in 3rd position, "word2" in 4th position, etc... but afaiu screechy needs the script to work whatever the positions of the words are.

---


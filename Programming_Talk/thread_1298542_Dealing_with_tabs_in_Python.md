---
title: "Dealing with tabs in Python"
date: 2009-10-22
forum: Programming Talk
---

### Post by GammaPoint on 2009-10-22
Hi, I'm reading in a bunch of files and converting them from one format to another. Anyway, in doing so I need to be able to read what the 6th character is of each line. However, this is assuming that the previous 5 characters are whitespaces. If the original file was created instead with a 'Tab' then if I index the 6th character of the line I'll get something totally different than what I expected to get.

So my question is, when reading a file is there a way in Python to tell if there are any 'tabs' in the line? I know that there is a string method called .expandtabs() but I *think* that only works if the tab is explicitly written like '\t'. Thanks for your time :)

---

### Post by ghostdog74 on 2009-10-22
> **GammaPoint said:**
> 
So my question is, when reading a file is there a way in Python to tell if there are any 'tabs' in the line? 
split on tabs eg string.split("\t")  and count the length of the returned list? OR you may try  ```
 if "\t" in string 
``` (not tested, just came out of my mouth and left for you to try )

---

### Post by Tony Flury on 2009-10-23
Assuming you can detect the tab characters (which should be equivalent to '\t'), how many spaces are you going to assume is a tab character - bear in mind you could assume 4 spaces - but the author of your document might assume that a tab is 6, or 8 - or something else, and therefore throw off your processing. 

Is there a reason why you are using an absolute position (i.e. the 6th character/position) rather than using something like the first non-whitespace character.

---


---
title: "Text replacement algorithm"
date: 2009-08-14
forum: Programming Talk
---

### Post by mahajanudit on 2009-08-14
Can someone provide me with an algorithm to replace text in a file...
like there is sed tool in unix.. i want to make something like this.
So is there an efficient way to implement text replacment.. any ideas?

---

### Post by Finalfantasykid on 2009-08-14
I don't think there is really any way other than linearly going through all the text in the file.

It would be pretty simple in Java since it has a built in String.replace("Old String", "New String");  You would do this for every line that has been read from a BufferedReader.  Then output the replaced text.

There is probably a super simple way to do it with some scripting language to...

---

### Post by ghostdog74 on 2009-08-14
seriously, i don't understand what you want to do actually. tools designed for text replacement already is created, eg sed, awk, even programming languages like Perl or Python (among others) has internal string replacement functions/methods. Unless you are testing your programming skills or for school work, otherwise, just use these tools straightaway without inventing the wheel...

---

### Post by Can+~ on 2009-08-14
There's no particular way to create a more efficient algorithm for replacing: exhaustive search, write string, repeat until EOF.

Really, if you don't know anything else from the file, there's no other way, mostly because:
[LIST=1]
[*]There's no guarantee that you have finished searching strings (thus you should read all the file)
[*]There's no way you can tell that you can skip any amount of bytes (thus you don't have random access)
[/LIST]

Unless there's another property to this file (structure, order, ...) or other means to treat it (create an index, ...) there's nothing you can build on.

---

### Post by ratcheer on 2009-08-14
I agree with the above - just use sed or Perl.

Tim

---

### Post by kjohansen on 2009-08-14
there are more efficient string searching algorithms than pure brute force, things like knuth-morris-pratt, and boyer-moore...

they basically work by knowing after a miss where the next possible match could be.

---

### Post by Finalfantasykid on 2009-08-15
> **kjohansen said:**
> there are more efficient string searching algorithms than pure brute force, things like knuth-morris-pratt, and boyer-moore...

they basically work by knowing after a miss where the next possible match could be.

Wow I had never thought of that before, that would reduce the number of iterations significantly since instead of going 1 character at a time, you could potentially skip the entire length of the string that is being searched for.  Though I'm sure built in methods/functions already implement these algorithms.

---

### Post by mahajanudit on 2009-08-15
Ya algorithms for string matching exists like rabin-karp, knuth-moriis-pratt etc, the problem is not string matching but replacing it.. like for example i have this fraction of a text file.
```

.....
.....
Except for the naive brute-force algorithm, ech string-matching algorithm performs some preprocessing based on the pattern and then finds all valid shifts. the total running time of each algorithm is the sum of the preprocessing and matching times.
.....
.....

```

now i have to replace the phrase "the total running time" by " running -time", i can find the string, identify it's position bt how to replace it? and by that i mean replacing the text in the file. like Java String.replace() function replaces the particular string and returns a new string variable. that i can do in c++ too, but i am not able to replace the string in the file. all i can do is make a copy, edit the text and then copy it back.. or something similar, which is somehow really inefficient.
and i know many tools already exist and even databases, but i don't want to use a database.. though if i could use sed with c++, i would actually love that.. i am just trying to create an application to store records and i don't want to use database for the application.. so i just want an efficient way to edit records, i.e. replace text. but in c++ or c..

---

### Post by nvteighen on 2009-08-15
Heck... really, if you are not doing this for school or algorithm research, please use Perl:

```

my $string = "Except for the naive brute-force algorithm, ech string-matching algorithm ...";
$string =~ s/ech/each/; # Substituting!
print $string;

```

---

### Post by mahajanudit on 2009-08-15
> **nvteighen said:**
> Heck... really, if you are not doing this for school or algorithm research, please use Perl:

```

my $string = "Except for the naive brute-force algorithm, ech string-matching algorithm ...";
$string =~ s/ech/each/; # Substituting!
print $string;

```

In C++ string object exists and if i want to replace some text in the string with another text i can use the replace function..
for example:
```

string str("This is the original string");
string replace("replaced");
string toreplace("original");
str.replace(str.find("original"),toreplace.length(),replace);

```

the problem is how to replace this string in the file... right now the only option is to copy the whole content of a file in a string, then replace the text and copy it back.. this process is really inefficient, even more so if the file size is large...
i want a good algorithm to achieve this...

---

### Post by Can+~ on 2009-08-15
> **mahajanudit said:**
> the problem is how to replace this string in the file... right now the only option is to copy the whole content of a file in a string, then replace the text and copy it back.. this process is really inefficient, even more so if the file size is large...
i want a good algorithm to achieve this...

Your problem are not the algorithms, but with the language itself.

The correct mode is fill a buffer in memory, work it out, and put it back in place, that way the processor can go do something more useful while the file is being uploaded to memory.

---

### Post by Marco A on 2009-08-15
.

---


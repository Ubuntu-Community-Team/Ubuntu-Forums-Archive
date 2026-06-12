---
title: "[SOLVED] Multi-line searching (grep? python? sed?)"
date: 2008-11-22
forum: Programming Talk
---

### Post by madaozeki on 2008-11-22
I'm doing some analysis of large corpora of tagged speech data, and occasionally have to write my own scripts. Since I'm not a programmer by training, I run up against the occasional wall. This is one of them.

I have several thousand text files with data organized as follows:

```
  0.476089 121 B
  4.138613 121 C
  4.290600 121 D
  4.485095 121 A
  4.743169 121 B
  5.645032 121 C
  6.272983 121 D
  6.483542 121 E
  7.113355 121 D
  7.239517 121 B
  7.409629 121 B
  7.707767 121 A
  8.042237 121 D
  8.154970 121 A
  8.266893 121 B
  8.955280 121 C
  9.077330 121 D
  9.313045 121 E
  9.399589 121 A
  9.514288 121 E
  9.614908 121 B
  9.666150 121 A

```

The left-most column indicates a time-stamp in a wav file. The middle column is irrelevant, and the right-most column is the one I'm interested in.

**What I need to do**
The goal is to extract all sequences of A-B-C-D-E in the right-most column, and output the respective time-stamps to a separate file. 

The above extract contains 2 relevant such sequences:

```
  0.476089 121 B
  4.138613 121 C
  4.290600 121 D
[COLOR="Red"][B]  4.485095 121 A
  4.743169 121 B
  5.645032 121 C
  6.272983 121 D
  6.483542 121 E[/B][/COLOR]
  7.113355 121 D
  7.239517 121 B
  7.409629 121 B
  7.707767 121 A
  8.042237 121 D
 [COLOR="red"][B] 8.154970 121 A
  8.266893 121 B
  8.955280 121 C
  9.077330 121 D
  9.313045 121 E[/B][/COLOR]
  9.399589 121 A
  9.514288 121 E
  9.614908 121 B
  9.666150 121 A

```

And the desired output file would be:

```
  4.485095
  4.743169
  5.645032
  6.272983
  6.483542
  8.154970
  8.266893
  8.955280
  9.077330
  9.313045
```

I've tried using a combination of grep, sed and awk as follows:

```
grep -A4 " A$" DATAFILE | grep -A3 -B1 " B$" | grep -A2 -B2 " C$" | grep -A1 -B3 " D$" | grep -B4 " E%$" sed -e '/^--$/d' | awk '{print $1 > "OUTPUTFILE"}'
```

This actually does catch all the relevant sequences, but it catches a bunch of other junk as well.

Any help would be very much appreciated!

---

### Post by WW on 2008-11-22
Here's a python script you can try:

findpattern.py
```

import sys

pattern = sys.argv[1]
filename = sys.argv[2]

data = [line.split() for  line in open(filename,'r')]
for k in range(len(data)-len(pattern)):
    s = ''.join([data[k+j][2] for j in range(len(pattern))])
    if s == pattern:
        for j in range(len(pattern)):
            print data[k+j][0]

```

E.g.
```

$ python findpattern.py "ABCDE" times.dat 
4.485095
4.743169
5.645032
6.272983
6.483542
8.154970
8.266893
8.955280
9.077330
9.313045
$ python findpattern.py "BA" times.dat 
7.409629
7.707767
9.614908
9.666150
$ 

```

---

### Post by madaozeki on 2008-11-22
> **WW said:**
> Here's a python script you can try:

findpattern.py
```

import sys

pattern = sys.argv[1]
filename = sys.argv[2]

data = [line.split() for  line in open(filename,'r')]
for k in range(len(data)-len(pattern)):
    s = ''.join([data[k+j][2] for j in range(len(pattern))])
    if s == pattern:
        for j in range(len(pattern)):
            print data[k+j][0]

```

E.g.
```

$ python findpattern.py "ABCDE" times.dat 
4.485095
4.743169
5.645032
6.272983
6.483542
8.154970
8.266893
8.955280
9.077330
9.313045
$ python findpattern.py "BA" times.dat 
7.409629
7.707767
9.614908
9.666150
$ 

```


Thanks! This is precisely the type of code I was looking for. I was going to add that a generic solution to search for any sequence of any length would be preferable, but you beat me to the punch :)

I'll give it a try when I get home and update this thread with the results.

Very much appreciated!

---

### Post by ghostdog74 on 2008-11-22
```

awk '{ a[NR]=$1; b[NR]=$3}
END{
 for (i=1;i<=NR;i++){
   if ( b[i]b[i+1]b[i+2]b[i+3]b[i+4] == "ABCDE"){
     for(j=0;j<5;j++){  print a[i+j]  }
   }
 }
}' file

```

---

### Post by madaozeki on 2008-11-22
Thanks ghostdog!

I should've mentioned one added quirk...

The 3rd column, with A, B, C, etc. isn't necessarily individual letters. It could potentially look like this:

%L
H-
A
L%

...and so on.

I've tweaked WW's python script above to include a 3rd command-line argument specifying the number of distinct values in the 1st command-line argument.

So for example:

myscript.py "%LH-AL%" 4 filename.data

That way the script knows to take the file lines in chunks of 4, and doesn't care about the boundaries between the actual values. This is useful because there is some inherent ambiguity:

Potential values:
%L
L%
%LL%
H-
A
wL
...and so on...

So the script now let's me search for:

"%LL%" 1
"%LL%" 2

returning different results!

I think the awk solution could be genericized, too, but since the python solution is working, I'm going to stick with it :)

Thanks again to both of you!

For what it's worth, here's what my (now-ugly!) code looks like. If anyone can comment on making it more elegant, I'd be very grateful:

```
#!/usr/bin/env python

# this script take 3 command-line arguments: 
# 1. the tone-sequence pattern to be searched for
# 2. the number of tones in the tone-sequence pattern
# 3. the name of the file to be parsed
# sample usage:
# extract_tone_sequence_phrases.py "%LH-AL%" 4 Filename
# the random-seeming '8' that pops up is due to the fact that
# the data actually begins on the 9th line of each data file, 
# following a header

import sys

pattern = sys.argv[1]
patternLength = int(sys.argv[2])
basename = sys.argv[3]
infilename = basename+r'.tone'
outfilename = basename+r'.times'
OUTPUT=open(outfilename, 'w')
tonelist = []

data = [line.split() for line in open(infilename,'r')]
for k in range(len(data)-patternLength-8):
    s = ''.join([data[k+j+8][2] for j in range(patternLength)])
    if s == pattern:
      for j in range(patternLength):
        tonelist.append(data[k+j+8][0]+'\n')
      OUTPUT.writelines(tonelist)
      tonelist=[]
OUTPUT.close()
```

---

### Post by WW on 2008-11-23
> **madaozeki said:**
> 
I've tweaked WW's python script above to include a 3rd command-line argument specifying the number of distinct values in the 1st command-line argument.

So for example:

myscript.py "%LH-AL%" 4 filename.data

That way the script knows to take the file lines in chunks of 4, and doesn't care about the boundaries between the actual values. This is useful because there is some inherent ambiguity:

Potential values:
%L
L%
%LL%
H-
A
wL
...and so on...

So the script now let's me search for:

"%LL%" 1
"%LL%" 2

returning different results!

Is it possible for such a string to have more than one interpretation, even when the number of tones is known?  For example, if A, AA, AB, and B are valid symbols, then the pattern AAB could be (A, AB) or (AA,B).  If that is the case, you could use commas (or spaces, or some other separator) to separate the tones in the pattern.  Then you wouldn't need the number of tones as a command line argument.  Instead, just split the pattern on the separator; the length of the resulting list is the length of the pattern.

If cases like the AAB example can't occur, then you're good to go.

---

### Post by WW on 2008-11-23
Unless you plan on adding code later that will do something with the tonelists as they are found, you could remove the use of the tonelist variable, and replace this
```

      for j in range(patternLength):
        tonelist.append(data[k+j+8][0]+'\n')
      OUTPUT.writelines(tonelist)
      tonelist=[]

```
with this
```

      for j in range(patternLength):
          OUTPUT.write(data[k+j+8][0]+'\n')

```

---

### Post by madaozeki on 2008-11-23
> **WW said:**
> Is it possible for such a string to have more than one interpretation, even when the number of tones is known?  For example, if A, AA, AB, and B are valid symbols, then the pattern AAB could be (A, AB) or (AA,B).  If that is the case, you could use commas (or spaces, or some other separator) to separate the tones in the pattern.  Then you wouldn't need the number of tones as a command line argument.  Instead, just split the pattern on the separator; the length of the resulting list is the length of the pattern.

If cases like the AAB example can't occur, then you're good to go.

WW, that's a good point that I hadn't considered! The way the data is structured leads me to believe that the case you mentioned isn't possible, but it still might be beneficial to add in that piece of handling just in case I'm wrong.

And thanks for the 2nd suggestion. That will be more elegant and I won't need to keep building data structures I'm never going to use.

---


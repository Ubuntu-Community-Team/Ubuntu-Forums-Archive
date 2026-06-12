---
title: "bash scripting"
date: 2010-07-15
forum: Programming Talk
---

### Post by jhurley03 on 2010-07-15
I need to make my own utility which will scan in a text file and search and replace strings. I also want to keep track of how many strings I've replaced. So my command would go something like:

<utility name> <filename> <stringToSearchFor> <stringToReplaceWith>

---

### Post by howlingmadhowie on 2010-07-15
maybe something like:
```

NUMLINES=`grep -o $SEARCHSTRING $FILENAME`
cat $FILENAME | sed -e 's/$SEARCHSTRING/$REPLACESTRING/g' > tmp.file
mv tmp.file $FILENAME
echo $NUMLINES

```

---

### Post by Iowan on 2010-07-15
From the Code of Conduct:
> While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums should not be thought of as a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will be taken offline and warnings or infractions may be issued.Giving you the benefit of the of the doubt, what hints would you like?

---

### Post by jhurley03 on 2010-07-16
> **Iowan said:**
> From the Code of Conduct:
Giving you the benefit of the of the doubt, what hints would you like?

```
#!/bin/bash
# code for reading in a file line by line.
fileIn=$1

while read linein
do
echo $linein
done < $fileIn

${stringZ//$2/$3}
```

The above is the code that I have so far. 

As of now stringZ is nothing. I need it to be the line being read in. I also need to figure out how to write linein back into a file.

---

### Post by geirha on 2010-07-16
Well, you cannot edit a file with bash, not without using an external tool designed for the purpose, like ed and ex. What you can do, however, is write a new (temporary) file, then move it over the old file when it's done.

```

while IFS= read -r line; do
  if [[ $line = *"$2"* ]]; then
  ...
done < "$1" > tmpfile
mv tmpfile "./$1"

```

---

### Post by jhurley03 on 2010-07-16
> **geirha said:**
> Well, you cannot edit a file with bash, not without using an external tool designed for the purpose, like ed and ex. What you can do, however, is write a new (temporary) file, then move it over the old file when it's done.

```

while IFS= read -r line; do
  if [[ $line = *"$2"* ]]; then
  ...
done < "$1" > tmpfile
mv tmpfile "./$1"

```

The code that I have so far, I've done in the vi editor. I have to do all of this using Putty.

---

### Post by geirha on 2010-07-16
> **jhurley03 said:**
> The code that I have so far, I've done in the vi editor. I have to do all of this using Putty.

I'm not talking about the editor you use to edit the script with, I'm talking about editors to edit files (from a script), which is what you said you wanted to do.

E.g. the following will search through file.txt using the basic regular expression *foo*, replace all occurances with *bar* and then write the changes.
```
printf "%s\n" "g/foo/s//bar/g" w | ed -s file.txt
```

Since you're familiar with vi, that command will do the same as typing the following in vi:
```
:g/foo/s//bar/g
:w

```

---

### Post by jhurley03 on 2010-07-16
Something very handy to do in a Linux shell, is manipulating files and strings - essentially parsing data. Write a utility which will scan in a text file and search and replace strings. We also want to keep track of how many strings we've replaced.

This time we're going to write an utility to change the matching string for us.

"Bill Gates" with "Mr. Noodles",
"Gates" with "Noodles",
"Paul Allen" or "Allen" as "The Other Guy",
"Altair" as "WTF",
"Apple" as "The Prodigal Son",
"Tandy" as "Who?"
and "Microsoft" as "Blue Screen of Death"

"Bill Gates was born in Seattle in 1955, the second of three children in a well-to-do family. His father, William H. Gates II, was a lawyer, while his mother, Mary Gates, was a teacher, a regent of the University of Washington, and member of several corporate boards. Gates was first exposed to computers at school in the late 1960s with his friend Paul Allen, the son of two Seattle librarians. By the time Gates was 14, the two friends were writing and testing computer programs for fun and profit. 
 In 1972 they established their first company, Traf-O-Data, which sold a rudimentary computer that recorded and analyzed traffic data. Allen went on to study computer science at the University of Washington and then dropped out to work at Honeywell, while Gates enrolled at Harvard. Inspired in 1975 by an issue of* Popular Electronics* that showed the new Altair microcomputer kit just released by MITS Computer, Gates and Allen wrote a version of BASIC for the machine. Later that year Gates left college to work full time developing programming languages for the Altair, and he and Allen relocated to Albuquerque, New Mexico, to be near MITS Computer, where Allen took a position as director of software development. Gates and Allen named their partnership Micro-soft. Their revenues for 1975 totaled $16,000. 
 A year later, Gates published "An Open Letter to Hobbyists" in the Altair newsletter, in which he enjoined users to avoid illegally copied software. Arguing that software piracy prevented "good software from being written," Gates wrote prophetically, "Nothing would please me more than being able to hire ten programmers and deluge the hobby market with good software." In November 1976 Allen left MITS to devote his full attention to Microsoft, and the company's tradename was registered. In 1977 Apple and Radio Shack licensed Microsoft BASIC for their Apple II and Tandy computers, with the Apple license going for a flat fee of $21,000. As Apple sold a million machines complete with BASIC, Microsoft's unit revenues dropped to two cents a copy. 
 That same year Microsoft released its second programming language, Microsoft FORTRAN, which was followed in 1978 by a version of COBOL. Both were written for the CP/M operating system, one of many available in the rapidly expanding but still unstandardized microcomputer market. As CP/M was adopted by computer manufacturers including Sirius, Zenith, and Sharp, Microsoft became the leading distributor for microcomputer languages. By the end of 1978 Microsoft had 13 employees, a sales subsidiary in Japan, and $1 million in revenues. The following year Gates and Allen moved the company to Bellevue, Washington."


The following script reads in a file (supplied by a line argument) line by line into a varilable called linein:

#!/bin/bash
#sample code for reading in a file line by line.
fileIn=$1

while read linein
do
echo $linein
done < $fileIn

The following snippet replaces the first occurance of a substring inside of a string variable:

${stringZ/abc/xyz}  #This looks at a string named 'stringZ' and would replace the first occurance 'abc' with 'xyz'

This snippet replaces ALL occurances of the substring inside of a string variable:

${stringZ//abc/xyz}

So now you need to put it all together:
your script will work like this:

fileStringReplace <filename> <stringToSearchFor> <stringToReplaceWith>

It will replace 'stringToSearchFor' with 'stringToReplaceWith' inside 'filename'.  It will return how many strings were replaced.

This is the code that I have so far:

```
#!/bin/bash
# code for reading in a file line by line.
fileIn=$1

while read linein
do
echo $linein
done < $fileIn

${stringZ//$2/$3}
```

My code has to use the snippets of code supplied by my teacher. I don't think I can use another editor to search through the text file, I have to make my own utility with VI that will do it for me. As of now stringZ is nothing. I need it to be the line being read in. I  also need to figure out how to write linein back into a file. I'm just asking for hints.

---


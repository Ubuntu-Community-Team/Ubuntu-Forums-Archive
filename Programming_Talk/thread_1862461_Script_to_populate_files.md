---
title: "Script to populate files"
date: 2011-10-16
forum: Programming Talk
---

### Post by MaindotC on 2011-10-16
I'm trying to touch a list of filenames and then populate them with contents from another file - 1 line per new filename.

For example, the list of filenames (file_list.txt) would contain this:

```

server1.mydomain.com_oracle
server11.mydomain.com_sybase
server85.mydomain.com_adobe
server86.mydomain.com_trimark
server91.mydomain.com_credit

```

And when I execute the script it would create the file and populate it with 1 line from a list of entries (entries.txt):
```

oracle:x:12:3000:oracle, created 10/10/11:/home/oracle:/bin/bash
sybase:x:19:5000:sybase create 10/7/11:/opt/sybase:/bin/csh
adobe:x:43:700:adobe, system account:/opt/adobe:/bin/bash
trimark:x:91:700:trimark system account:/opt/trimark:/bin/bash
credit:x:99:5001:credit, created 10/1/11:/home/credit/:/bin/csh

```

What I want to achieve is for the script to read the first line of file_list.txt, which would be server1.mydomain.com_oracle, create a file by that name, then echo the associative line of text from entries.txt into that that file - server1.mydomain.com_oracle.  So, the result would look like this:

```
Filename                    Contents

server1.mydomain.com_oracle     oracle:x:12:3000:oracle, created 10/10/11:/home/oracle:/bin/bash
server11.mydomain.com_sybase    sybase:x:19:5000:sybase create 10/7/11:/opt/sybase:/bin/csh
server85.mydomain.com_adobe     adobe:x:43:700:adobe, system account:/opt/adobe:/bin/bash
server86.mydomain.com_trimark   trimark:x:91:700:trimark system account:/opt/trimark:/bin/bash
server91.mydomain.com_credit    credit:x:99:5001:credit, created 10/1/11:/home/credit/:/bin/csh
```

The filenames and contents are arbitrary but that is the gist of what I'm trying to accomplish.  I have to upload a list of /etc/passwd entries daily and they have to be in a file named relative to the server where the /etc/passwd entry goes.

---

### Post by Vaphell on 2011-10-16
are these identifiers (oracle, sybase, ...) unique or should one expect that the order in both files matches?
if they are unique then this should do
```
#!/bin/bash

while read f
do
  echo file: "$f"
  id="${f##*_}"
  content=$( grep -E "^$id:" entries.txt )
  echo content: "$content"
  echo "$content" > "$f"
done < file_list.txt
```

---

### Post by MaindotC on 2011-10-16
> **Vaphell said:**
> are these identifiers (oracle, sybase, ...) unique or should one expect that the order in both files matches?
if they are unique then this should do
```
#!/bin/bash

while read f
do
  echo file: "$f"
  id="${f##*_}"
  content=$( grep -E "^$id:" entries.txt )
  echo content: "$content"
  echo "$content" > "$f"
done < file_list.txt
```

The should match the order in both files.  Perhaps this is better but each line of the file_list.txt should match an entry in entries.txt for populating.  What I was going to do is just duplicate the filename in file_list.txt if there was a file that should contain more than 1 entry.  I'll test this out.

Thank you for this - let me just see if I can grasp what it is doing:

"while read f" means "do this while there is something in f" and I believe "f" is whatever value I pass into the script?

do echo file: "$f" - means create a file named whatever is stored in f at that time?

What does the reverse bracket mean?  For example, I'm used to executing something and outputting the result into a file using ">".  What does it mean that you have "< file_list.txt" - does that mean file_list.txt is in the input - each line being passed in for f?

Thanks.

---

### Post by Vaphell on 2011-10-16
**while .... done < file_list.txt** means that the while loop is fed with data from a file_list.txt and each iteration corresponds to a single line. If you want to do input-output thingie with files, you can do **while .... done < input.file > output.file**

**read f** here means get the current piece of data and put it in variable f (so f = line from file)

**echo file: "$f"** only prints text to stdout so you get a visual feedback, it's entirely superficial for what you need. Same thing with the **echo content: "$content"** line 

id is a substring of f remaining part after removing _ with anything preceding it, so in theory it should contain identifier from the end of filename

content is a variable that holds a line from entries.txt that matches ^IDENTIFIER: (^ being start of line)

**echo "$content" > "$f"** is the actual line that does what you want - it echoes $content but redirects it to file with name equal to value of f ( > $f )

---

### Post by MaindotC on 2011-10-17
Thank you for this - you've got me on a good start.  I'm not receiving the desired result.  I keep getting:
```

./cr_id: line 6: f##*_: command not found

```

I changed the following to get part-way there:
```

content=$(grep -E "^$id:" entries.txt)

```

To:

```

content=$(cat entries.txt)

```

However that put all entries into every file from file_list.txt.  Any chance you can make it just pop the first line of entries.txt into the first file created from file_list.txt, and repeat for each line of file_list.txt?  Each file should have 1 line from entries.txt in it (for now).

---

### Post by Vaphell on 2011-10-17
which shell do you use?

```
#!/bin/bash

lnum=0
while read f
do
  echo "#$(( ++lnum ))"
  echo file: "$f"
#  id="${f##*_}"
#  id=$( echo "$f" | sed -r 's/.*_(.*)$/\1/' )
#  echo  id: $id 
#  content=$( grep -E "^$id:" entries.txt )
  content=$( awk ' NR=='$lnum' { print $0 }' entries.txt )
  echo content: "$content"
  echo "$content" > "$f"
  echo -------------------------------
done < file_list.txt
```

in the commented part there is an alternative to ${f##*_} using $( echo | sed ) combo, you can check that out. It's commented because i get content with awk and line number (NR) which is paramertized with lnum variable acting as a loop counter.

---

### Post by sisco311 on 2011-10-17
You can read multiple files line by line with a single loop:
```

while read -ru 6 filename && read -ru 7 content
do
    printf '%s\n' "$content" > "$filename"
done 6< file_list 7< entries
```

---

### Post by MaindotC on 2011-10-25
> **Vaphell said:**
> which shell do you use?

```
#!/bin/bash

lnum=0
while read f
do
  echo "#$(( ++lnum ))"
  echo file: "$f"
#  id="${f##*_}"
#  id=$( echo "$f" | sed -r 's/.*_(.*)$/\1/' )
#  echo  id: $id 
#  content=$( grep -E "^$id:" entries.txt )
  content=$( awk ' NR=='$lnum' { print $0 }' entries.txt )
  echo content: "$content"
  echo "$content" > "$f"
  echo -------------------------------
done < file_list.txt
```

in the commented part there is an alternative to ${f##*_} using $( echo | sed ) combo, you can check that out. It's commented because i get content with awk and line number (NR) which is paramertized with lnum variable acting as a loop counter.

I think this is it :)  It's going to take me a bit to become familiar with some of this syntax but in the meantime this will save me the mind-numbing task of populating about 150 files every two days - copying them from an excel sheet into a for loop to vi each filename in a list of filenames :)  Thank you very much for your assistance.

---

### Post by MaindotC on 2011-10-26
Ok so let me see if I understand this - check my comments:

```
#!/bin/bash

#initialize variable "lnum" to 0 as it will be used as a counter
lnum=0

#while there is something in the file being passed in as "f"
while read f
do

#print the current value of lnum incremented by 1
  echo "#$(( ++lnum ))"

#print the filename being created
  echo file: "$f"

#  id="${f##*_}"
#  id=$( echo "$f" | sed -r 's/.*_(.*)$/\1/' )
#  echo  id: $id 
#  content=$( grep -E "^$id:" entries.txt )

#Little confused here
#initialise the variable content to the value of the expression.
#I believe NR has something to do with printing the number of #records and is this some sort of a condition?  If the number of #records is equal to the value of lnum print $0 which would be #nothing?  Or is this looking for the line of entries.txt that 
#has nothing so it will end?
  content=$( awk ' NR=='$lnum' { print $0 }' entries.txt )

#print the value of content that this iteration
  echo content: "$content"

#print the value of content into a text file named after the #current line in f that is being read
  echo "$content" > "$f"
  echo -------------------------------

#accept file_list.txt as the input - it will serve as the values #of f at the given iteration
done < file_list.txt
```

> It's commented because i get content with awk and line number (NR) which is paramertized with lnum variable acting as a loop counter.

Still a little unclear about the NR.  I'm reading up more on it at this time.

---

### Post by Vaphell on 2011-10-26
NR is simply an index of the record (record = line by default, but by defining record separators you can change it), first line NR=1, 10th line NR=10. Awk simply picks the N=th line from file.

either way, use sisco's idea. It will read corresponding lines from two files at once without any hassle.

---


---
title: "need to read two files simltaneosly needed urgently"
date: 2008-07-03
forum: Programming Talk
---

### Post by umshiva on 2008-07-03
Hi expert ,

I am a new bie to scripting ,

I need a awk script to read two files simultaneosly and write it in a file urgently if possible in 30 min- 1hr

file1 and file 2 > 1024 records so i cannot use array 

file1

898
989
878
879
780

File2
doc1
doc2
doc3
der4
dss5

OUtput

898 doc1
989 doc2
878 doc3
879 der4
780 dss5    

Thanks in advance ...

---

### Post by WW on 2008-07-03
You could use awk (cue ghostdog74 :)), but it is probably even easier with the **paste** command:
```

$ ls
file1  file2
$ paste -d ' ' file1 file2
898 doc1
989 doc2
878 doc3
879 der4
780 dss5
$ paste -d ' ' file1 file2 > file3
$ cat file3
898 doc1
989 doc2
878 doc3
879 der4
780 dss5
$ 

```

---

### Post by fifth on 2008-07-03
> **umshiva said:**
> Hi expert ,

I am a new bie to scripting ,

I need a awk script to read two files simultaneosly and write it in a file urgently if possible in 30 min- 1hr

file1 and file 2 > 1024 records so i cannot use array 

file1

898
989
878
879
780

File2
doc1
doc2
doc3
der4
dss5

OUtput

898 doc1
989 doc2
878 doc3
879 der4
780 dss5    

Thanks in advance ...

I dont know awk, but you shouldnt need an array to hold the file for this.

All you should need to do is open both files for input and one for output. Loop through both files reading one line at a time. Join the two strings read from the files and write the new screen to your output file.

Kind of like;
```

inFile1 = open input file ("a")
inFile2 = open input file ("b")
outFile = open write file ("c")

while inFile1 not at end
   line1 = read line from inFile1
   line2 = read line from inFile2 // Checking not at end of file
   newLine = line1 + line2 // Concat the 2 lines
   write newLine to outFile
end
close outFile
close inFile2
close inFile1

```

As I said, I don't know awk, so not sure if the above is possible, but should be able to do something similar.

---

### Post by ghostdog74 on 2008-07-03
awk
```

 awk 'BEGIN {OFS=" "}
{
  getline f2line < "file2"
  print $1,f2line
} '  file1

```

use paste, as WW has mentioned.

---

### Post by dtmilano on 2008-07-03
Or simply:
> paste file1 file2
gives
> 898	doc1
989	doc2
878	doc3
879	der4
780	dss5


---


---
title: "Output all occurences of matching line in text files?"
date: 2007-11-06
forum: Programming Talk
---

### Post by balloons on 2007-11-06
Ok, laugh and then tell me how to do this a better way - indeed any other way. This worked, and since I was in a rush and couldn't think I used it. I had originally thought to do it in perl - but feel free to include a solution using python, perl, bash, awk, grep ,sed . . .
```

#/!bin/bash
cat file1.txt |while read line; do
	egrep "${line}" file2.txt >> output.txt
done
```

I'm trying to write out a file which contains each occurrence of lines from file1 that match to a line in file2. IE,

File #1
123
345
566
566
456
123

File #2
566
123

Output
123
566
566
123

---

### Post by ghostdog74 on 2007-11-07
more "efficient" method
```

awk 'FNR==NR{a[++c]=$1;next}
{ for(i=1;i<=c;i++) { 
    if ( $1 == a[i] ) print $1
  }
}
' "file2" "file1"

```

---

### Post by balloons on 2007-11-07
Nice - I'll have to do a runtime on each of them and see.. The files are about 30 mb each, so runtime makes a difference.

---

### Post by slavik on 2007-11-07
in case you don't have the perl code ...

[php]
open $in1, "file1" or die $!;
open $in2, "file2" or die $!;

while ($line1 = <$in1>) {
  $lines{$line1} = 1;
}

while ($line2 = <$in2>) {
  print $line2 if ($lines{$line2} == 1);
}

close $in1;
close $in2;
[/php]

---

### Post by stylishpants on 2007-11-07
'join' is fairly fast, but requires sorted input.

```

# '123' result is missing when using join on unsorted input
fhanson@fhanson:/tmp$ join file1 file2
566
566

# sorting first fixes it
fhanson@fhanson:/tmp$ (sort file2) | join - file1
123
566
566

```

---

### Post by balloons on 2007-11-07
The join is interesting - and as it happens the files are already sorted (sort -u) to eliminate dupes. But I can't get it to work. Nothing outputs.. Hmmm

---

### Post by stylishpants on 2007-11-08
The lines must match exactly, character-for-character.  Whitespace differences count.

For example, if one of the files were created with Windows-style CRLF line endings and the other has had those stripped by some UNIX-based processing programs, no lines would match.
This little perl snippet prints all lines in the file that have CRLF line endings.  No output means you have standard UNIX line endings.
```
perl -ne 'print if /\r/' file
```

---

### Post by balloons on 2007-11-12
Thanks - the join works amazingly. I ended up having to do this on quite a few files, and i just scripted to clean, sort, join. You were correct, I ended up doing a tr command to convert to unix line endings, and it worked.

---

### Post by kefler on 2007-11-15
couldn't you have run [\r\n] in your regx expression to catch both endings ?

---


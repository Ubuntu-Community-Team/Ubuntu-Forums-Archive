---
title: "(Shell script) while loop: read two files at same time"
date: 2009-10-18
forum: Programming Talk
---

### Post by agnes on 2009-10-18
I have this code, it reads a file line by line, and for every line it calls another script with the currently-read line as parameter.

```

#!/bin/sh

  echo enter file name
  read fname

   exec<$fname
  
   while read line
   do
        ./script4b.sh $line  
   done

```

But what I want is it to call script4b.sh with *two* lines as parameter, where the first line comes from one file, and the other from another file.

So I need it to loop through (read) two files (both the same length) at once.

Does anybody know how to do this?

---

### Post by ghostdog74 on 2009-10-18
give the second file another file descriptor number. see [here]("http://tldp.org/LDP/abs/html/x17434.html")

---

### Post by agnes on 2009-10-18
Ok your link was also about using stdin/stdout which was a bit confusing.
But searching on "exec" I found the solution, for the people who came here searching:

```
#!/bin/sh

  echo enter file name
  read fname

  echo enter filename two
  read fname2

   exec 3<$fname
   exec 4<$fname2

   while IFS= read -r line1 <&3
   IFS= read -r line2 <&4
   do
  
        echo $line1
        echo $line2

        sleep 1
   done

```

---

### Post by Arndt on 2009-10-18
> **agnes said:**
> Ok your link was also about using stdin/stdout which was a bit confusing.
But searching on "exec" I found the solution, for the people who came here searching:

```
#!/bin/sh

  echo enter file name
  read fname

  echo enter filename two
  read fname2

   exec 3<$fname
   exec 4<$fname2

   while IFS= read -r line1 <&3
   IFS= read -r line2 <&4
   do
  
        echo $line1
        echo $line2

        sleep 1
   done

```

You will need to decide what to do if the files don't contain the same number of lines, too.

---

### Post by agnes on 2009-10-18
You're right.
I'm not that far with shell scripts yet.
But I assume you do this by checking every iteration if the file is (still) readable? (Within the while loop.)

Like
```

if [ -r $fname -a -r $fname2 ] 
then
    blabla..
else
    exit $E_FILE_ACCESS
fi

```
?

---

### Post by geirha on 2009-10-18
When read reads a line from the file, it will return true, and thus the while loop will do an iteration. When there's nothing more to read, it will return false, and the while loop will end. That's easy with just one file. 
```
while read -r line; do echo "$line"; done < "$file"
```

Now, with two files like you have (this is the same loop as yours, I'm just using bash instead of dash) it gets a little more complicated
```
fname=/tmp/file1 fname2=/tmp/file2
echo -e 'a\nb\nc' > "$fname"
echo -e 'd\ne\nf\ng' > "$fname2"
while read -r -u3 line1; read -r -u4 line2; do echo "$line1:$line2"; done 3< "$fname" 4< "$fname2"
*a:d*
*b:e*
*c:f*
*:g*

```
When you have two commands between the "while" and "do", it will evaluate the return value of the **last** command, so in this case, it will read until it reaches the end of the second file. If the first file ends before the second, "$line1" will be empty in those iterations.

If you want it to stop reading when either of the files reaches the end, then use logical and (&&)
```
while read -r -u3 line1 && read -r -u4 line2; do echo "$line1:$line2"; done 3< "$fname" 4< "$fname2"
*a:d*
*b:e*
*c:f*

```
If either of the reads return false now, the loop will end.

Oh, and I recommend [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide) for learning bash. I recommend against ABS as it doesn't teach good coding practice.

---

### Post by agnes on 2009-10-23
I don't fully understand, 
I've read logical AND is "-a"  in bash.

So it could be

   ```

   while IFS= read -r line1 <&3 -a IFS= read -r line2 <&4
   do
      stuff
   done
```

?

Anyway thanks for the Bash guide link.

---

### Post by geirha on 2009-10-24
No, -a is an argument to the test and [ commands (type «help [» and «help test» in a bash shell). With bash's [[ and ((, and between commands, you use && and || instead. 

```
line="foo bar"
if [[ $line = *bar* || $line = *baz* ]]; then 
  echo "Line contains 'bar' or 'baz'";
fi

a=2
if (( a >= 0 && a < 5 )); then 
  echo "a is between 0 and 5"
fi


if grep -Fq 'foo' file1 && grep -Fq 'bar' file2; then
  echo "file1 contains 'foo' and file2 contains 'bar'"
fi

```

[ is something still hanging around from bourne, and should only be used if you need your script to be able to run in other posix shells.

---


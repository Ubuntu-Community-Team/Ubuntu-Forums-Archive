---
title: "Separating concatenated files"
date: 2009-12-05
forum: Programming Talk
---

### Post by silentrebel on 2009-12-05
I have put two binary files into one single file with the *cat* command as follows:
```
cat file1 file2 > bothfiles
```
I do not know how to retrieve the files separately afterwards though...  

I came up with two possible solutions:
1)
```
echo " separationMarker " > tmp
cat file1 tmp file2 > bothfiles
```
How would you then use *separationMarker* to send part of bothfiles to one output location and send the other part to another output location?
2)
Record the size of both files before packaging them.
But how would one instruct the shell to output the first x bytes to one location and the next x bytes to another location.

Any help with the implementation of any of these two solutions or with a completely different approach to separating the concatenated files is appreciated.
Please do not suggest the use of *tar* instead of *cat*; I recognise its relevance to this question, but am searching specifically for a way to separate concatenated files.

---

### Post by slavik on 2009-12-05
1. Something like the following would work.
```

flag=0; cat file | while read line; do
  if [ flag -eq 0 ];then
    if [ "$line" != " separationMarker " ]; then
      echo $line >> file1
    else
      flag=1; echo $line >> file2; 
    fi
  else
    echo $line >> file2
  fi
done

```
2. look into the size command.

---

### Post by silentrebel on 2009-12-05
Ah!  That *cat bothfiles | while read line* is brilliant.  Much more likely to work than my previous *for piece in `cat bothfiles`* attempt.
However, when I try your code it does not seem to ever find the *separationMarker*.  It creates the first file (which, in the end, is too small) and never makes the second...  
I was also wondering if you really meant to put 
```
flag=1; echo $line >> file2
```
Wouldn't that put *separationMaker* at the beginning of the second file?
Thanks!

---

### Post by slavik on 2009-12-05
good point, I also haven't really tested the code. :P

---

### Post by LKjell on 2009-12-05
don't you need to put the separtionMarker in one line?
```

echo -e "\n separationMarker " > tmp
```

---

### Post by silentrebel on 2009-12-05
I thought cat started every new file on a new line... 
Bad assumption, maybe...
--------------
This code creates both files, but they are way too small!!! Can anyone justify this?
```

cat bothfiles | while read line
do 
     if [ $flag -eq 0 ]
     then 
          if [ -z "`echo "$line" | grep "separation"`" ]
          then 
               echo "$line" >> file1
          else 
               flag=1
          fi
     else 
          echo "$line" >> file2
     fi 
done

```

Remember, 
bothfiles is the result of 
```
cat file1 tmp file2 > bothfiles
```
and tmp is now the result of
```
echo -e "\n separationMarker " > tmp
```

---

### Post by ghostdog74 on 2009-12-06
cat + while read = UUOC. 
a question, why do you want to combine 2 binaries together? does it work properly when the application calls it? 

```

awk 'FNR==1{print "marker" > "output"}{print $0 > "output"} ' binary1 binary2

```

---

### Post by ratcheer on 2009-12-06
I have always split files using the csplit command, but I don't know if that will meet your needs. I do recommend looking at it to see, though.

Tim

---

### Post by ghostdog74 on 2009-12-06
yes you can use csplit, provided it knows what to look for as "marker" to split

---

### Post by silentrebel on 2009-12-06
> **ghostdog74 said:**
> ```

awk 'FNR==1{print "marker" > "output"}{print $0 > "output"} ' binary1 binary2

```
This code returns the following error when executed "awk: (FILENAME=binary1 FNR=1) fatal: cannot open file `binary1' for reading (No such file or directory)." I created empty files named binary1 and binary2, but then, though it did not complain, it did not do anything.  I also tried piping *bothfiles* into the awk command to no avail.  
I'm not entirely familiar with all the logic of this awk command, though.  Perhaps if you explained it, I could fix it...

> **ghostdog74 said:**
> 
yes you can use csplit, provided it knows what to look for as "marker" to split

I'm not able to get csplit look for the marker, but not copy it to either of the output files.  One of the files always ends up bigger than it was originally, because, the marker is included? How would one go about fixing this?
So far I have :
```
csplit bothfiles '/marker/'
```
Thanks for your help...
silentrebel
P.S. I'm trying to make a bidirectional-patch wrapper for rdiff ([http://ubuntuforums.org/showthread.php?t=1344415](http://ubuntuforums.org/showthread.php?t=1344415)).  The finished product should consist of a script, which depends on rdiff, and which uses it to create a single patch-file that offers a bidirectional patch.  The same script could then be used to patch or reverse-patch depending on the file on which the patch is applied.  I'll post the finished product on the thread cited above.

---

### Post by lswb on 2009-12-06
Why reinvent the wheel? tar will do all this and more.

If you need to make your own tool for some reason, the approach you have outlined will have a problem if by some chance either file contains the text " SeparationMarker " Perhaps you could record the file names and sizes in some kind of header, then use dd, head, or similar utilities to extract the files.

---


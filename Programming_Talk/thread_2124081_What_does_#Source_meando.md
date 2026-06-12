---
title: "What does #Source: mean/do?"
date: 2013-03-09
forum: Programming Talk
---

### Post by toad3000 on 2013-03-09
Some example scripts I see on the top after #!/bin/bash I see #Source: ......
The .... contains just random words. I suppose they are other script names. 

Thanks

---

### Post by lisati on 2013-03-09
Sometimes it depends on the context. Do you have an example?

---

### Post by toad3000 on 2013-03-09
I have a hunch that it means run this script first and use the variables but when I tried an example of my own it didn't work. Like I made a script with variables x=100. I made another script with variable y with value 50. And in that script I said if [ $x -le $y ] ........
But when I ran the second script it says unary operator expected.

---

### Post by toad3000 on 2013-03-09
This is one of the examples I'm studying from 

```
#!/bin/bash
#Source: countod
#read in a number of strings from user (until
#user enters  END  or end) and output the total
#number of strings that are  files  & the total
#number that are directories.
#note: if the user enters more than one string on a line,
# will get if [ -f str1 str2 etc ] bash syntax error


typeset -i  ordfile=0
typeset -i  dirfile=0


while  [ true ]
do
     echo  Enter a file name or  END to quit
     read filenam
     if  [ "$filenam" = "END" -o "$filenam" = "end" ]
     then
          break       #breaks out of the while loop, like in C
                  #continue statement also available
     fi
     if   [ -f  $filenam ]
     then
          ordfile=ordfile+1
     elif  [ -d $filenam ]
     then
          dirfile=dirfile+1
     fi
done
echo -e "The number of ordinary files:\t  $ordfile"
echo -e "The number of directories:\t  $dirfile"
exit 0
```

I understand the body of the script I just don't understand the #Source: part...

---

### Post by lisati on 2013-03-09
*Thread moved to **Programming Talk**.*

In a script such as the one you're studying, the "#" at the start of a line usually indicates a comment intended for use by a person rather than a computer. 

The first line, **#!/bin/bash**, is a special case, sometimes known as a "shebang", which helps the command line interpreter know how to interpret the contents of a file.

I'm not familiar with "countod", it could refer to another script made by the person who produced the tutorial you are following.

---

### Post by bab1 on 2013-03-09
This ```
#Source: countod
#read in a number of strings from user (until
#user enters  END  or end) and output the total
#number of strings that are  files  & the total
#number that are directories.
#note: if the user enters more than one string on a line,
# will get if [ -f str1 str2 etc ] bash syntax error
```

Is just the comments about the script.

The hash (#) causes the interpreter to ignore the line.  In other words, it's a note for humans to read.

Without the hashes:
[COLOR="#0000FF"]Source: countod
read in a number of strings from user (until user enters  END  or end) and output the total number of strings that are  files  & the total number that are directories.
note: if the user enters more than one string on a line, will get if [ -f str1 str2 etc ] bash syntax error[/COLOR]

---

### Post by sisco311 on 2013-03-09
Could you provide the [s]source :P[/s] author and title of the book or post a link to the tutorial  are you studying from?

---


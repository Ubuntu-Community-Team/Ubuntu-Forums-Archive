---
title: "awk: manage multiple files"
date: 2009-02-06
forum: Programming Talk
---

### Post by Claus7 on 2009-02-06
Hello awk gurus,

I would like your help in a topic about awk, which I think that not only is of vital importance, but also if clarified will help a lot of people.

My question has to do with something like this:
awk *pattern* file1 file2 file3 (...up to 10) > finalfile

Awk can manage up to ten files simultaneously, if I have searched correctly. 

Also, it reads file by file until it reaches the final one.

If someone wants to discriminate the first file from a second one, then something like this would suffice:

```
awk ' NR=FNR { if (FNR==2) x=$1 ; next }
             { if (FNR==2) y=$1 }
             { if (FNR==2) print x+y }' file1 file2 > file3

```
The NR=FNR condition sais that while the :
FNR    The ordinal number of the current record in the current file **is equal to**
NR     The ordinal number of the current record from the start of input **then**

x=$1 (for file1)

Next it reads file2, takes from the second line the first element, assigns it to y and it prints in file3 the entire file2, except that the second line is substituted by x+y.

So far so good.

How about when we want to do the above procedure to more than two files? How can I control in which file it enters, takes the value from the second line and in the last file I add all these values and print them to the second line?

very nice links are the following:
[http://www.unix.com/shell-programming-scripting/70269-gawk-reading-two-files-re-arrange-columns.html](http://www.unix.com/shell-programming-scripting/70269-gawk-reading-two-files-re-arrange-columns.html)
[http://oreilly.com/catalog/unixnut3/chapter/ch11.html](http://oreilly.com/catalog/unixnut3/chapter/ch11.html)
[http://www.tek-tips.com/viewthread.cfm?qid=1281506&page=1](http://www.tek-tips.com/viewthread.cfm?qid=1281506&page=1)
[http://www.issociate.de/board/post/465434/merge_two_files_line_by_line....html](http://www.issociate.de/board/post/465434/merge_two_files_line_by_line....html)
[http://groups.google.com/group/comp.lang.awk/msg/e9622cad4b072635](http://groups.google.com/group/comp.lang.awk/msg/e9622cad4b072635)

Regards!

---

### Post by unutbu on 2009-02-06
I don't know awk very well, but it appears FNR resets to 1 at the beginning of every file. Therefore, if you count how many times FNR equals 1, you will know which file you are currently parsing.

You could then build conditions based on the value of file_num:
```

awk '{ if (FNR==1) file_num+=1 } { if (file_num==1) print "File 1: "$0 } { if (file_num==2) print "Second file: "$0 } { if (file_num==3) print "Yahoo: "$0 } '  a b c
```

---

### Post by ghostdog74 on 2009-02-06
yes, you can use FNR==1 as unutbu described. Other ways include using nextfile and the while/getline construct.

---

### Post by Claus7 on 2009-04-06
Hello,

thank you for your answers. I bypassed a little this issue, because the time I had in order to include this in my analysis was too demanding. A helpful post is:
[http://www.tek-tips.com/viewthread.cfm?qid=1466678&page=9](http://www.tek-tips.com/viewthread.cfm?qid=1466678&page=9)

which deals more or less with the same subject. If I find time I would like to return with the entire coding. 

Regards!

---

### Post by Claus7 on 2009-09-09
Hello,

after a long time since I last dealt with issue, this is what I came out with:

```
awk '{
       { getline < "test1" ; if (FNR==2) x=$1 } 
       { getline < "test2" ; if (FNR==2) y=$1 }
       { getline < "test3" ; if (FNR==2) z=$1 }
     }
     END {print x+y+z}' test1 > output
```

What this code does is:
while reading test1 file in *test1 > output*

it opens with getline files test1, test2 and test3 (getline < "test#" , where #=1,2,3)

and applies the condition that if the number of line equals with 2, it assigns that value to a variable (if (FNR==2) x=$1)

In the end (END...) it sums all the variables and prints them in the file output.

That way I think that this code can be generalized in many files so as to post process them. We just have to read the first one, assign also one output, and while doing so we open all the other files that we need to take values from them.

Regards!

---


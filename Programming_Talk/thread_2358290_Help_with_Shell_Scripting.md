---
title: "Help with Shell Scripting"
date: 2017-04-11
forum: Programming Talk
---

### Post by thao83 on 2017-04-11
Hello,
I am new to Ubuntu OS.  Just converted my old Dell Dimension desktop to Ubuntu OS for testing school work.  I'm not going to lie, I do need help on one of my assignment.  
Not looking for the answers as I know I won't learn anything.  

I am working on a Korn shell script to allow user to copy a file to multiple directory. 
My question is....When I put the echo command first, my IF statement won't execute.  When I move my IF statement to the top, both IF and echo execute.
Is there something that I am missing?

Thanks

---

### Post by sisco311 on 2017-04-11
Hi, next time you post code please use [code] tags: [https://ubuntuforums.org/showthread.php?p=12776168#post12776168]("https://ubuntuforums.org/showthread.php?p=12776168#post12776168")

Do you really want to exit with a status of 0 after the echo commands?

---

### Post by thao83 on 2017-04-12
Thanks for your reply.  I figured it out.  To answer your question, no I don't want to exit with a status of 0.  I see what I did wrong.
Half way through this assignment.  Might seems easy to some but it's a lot of going back and fourth for me.

```
  
  6 # Allowing user to copy a file or directory to multiple location
  7 
  8 
  9 echo The number of parameter for $0 is $#
 10 
 11 
 12 if [ $# -lt 2 ]; then
 13         echo You need to provide at least 2 parameters
 14         echo Usage: $0 file1 dir1 dir2 dir3
 15         exit 99
 16 else
 17         echo The parameters are $@
 18         echo
 19 
 20 fi
 21 
 22 for file in $@
 23 do
 24         let value=$value+1
 25         echo parameter $value found is $file
 26 
 27 done
 28 exit 0


```

---

### Post by slickymaster on 2017-04-12
*Thread moved to **Programming Talk**.*

---

### Post by steeldriver on 2017-04-12
Just a couple of suggestions:

[LIST]
[*]you may find the [FONT=courier new]shift [/FONT]operator useful (it will allow you to assign the first script argument or "positional parameter" to a variable, and then simply loop over the remaining parameters as destination directories) 
[*]don't forget to double-quote "[FONT=courier new]$@"[/FONT] so that the expansion doesn't break if given a file / directory name with spaces in it 
[/LIST]

---


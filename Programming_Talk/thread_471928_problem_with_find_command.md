---
title: "problem with find command"
date: 2007-06-12
forum: Programming Talk
---

### Post by silverfox1981 on 2007-06-12
Hi, im new to linux and this forum. so if i posted this in the wrong place, i apologise in advance.

im trying to get this script working, it looks in a folder (pages_in) for files starting with the letter "a" and prints "yes files are here!"  
i have placed files starting with the letter a in this folder. and keep getting "no files here".

ive typed    

  $ -find /root/pages/pages_in/a* 

in to the terminal and it shows me the files begining with the letter a.

below is the script.

#checks for documents in pages_in
a=1

while [ $a = 1 ]
do 

if [[ -find /root/pages/pages_in/a* ]]
then

echo "yes files are here!!"

else

echo "no files here!!"

fi  
a=0
done

thanks

---

### Post by bscbrit on 2007-06-12
I don't want to appear negative, but there are several problems with your script.  You don't need an Ubuntu forum but you do need to learn more about bash.  The following link might be of interest: 

[http://www.gnu.org/software/bash/manual/bashref.html](http://www.gnu.org/software/bash/manual/bashref.html)

Good Luck. :D

---

### Post by abc123456 on 2007-06-12
find /long/path/name/   -name 'a*'

---

### Post by Ramses de Norre on 2007-06-12
Read up on if clauses, the use of "[" in your script is plain wrong...

---

### Post by HackingYodel on 2007-06-12
If you save this file as, let's say **hasa.sh **
```
#!/bin/bash
 
if [ -f $1 ];
 then
  echo "Yes files are here!!" 
 else
  echo "Not in here"
fi

```

then from the command line, with **hasa.sh** in your current directory, enter:

**chmod +x hasa.sh**
**./hasa.sh /root/pages/pages_in/a***

you should get your desired output.


The **find** command will iterate through a directory automatically, making the use of a **while** loop unneeded.  

The example I show does a simple test to see if a/the file you passed to the **if** exist or not.  Let Bash do the work for you, I always say. :wink:

---

### Post by ghostdog74 on 2007-06-12
> **silverfox1981 said:**
> Hi, im new to linux and this forum. so if i posted this in the wrong place, i apologise in advance.

im trying to get this script working, it looks in a folder (pages_in) for files starting with the letter "a" and prints "yes files are here!"  
i have placed files starting with the letter a in this folder. and keep getting "no files here".

ive typed    

  $ -find /root/pages/pages_in/a* 

in to the terminal and it shows me the files begining with the letter a.

below is the script.

#checks for documents in pages_in
a=1

while [ $a = 1 ]
do 

if [[ -find /root/pages/pages_in/a* ]]
then

echo "yes files are here!!"

else

echo "no files here!!"

fi  
a=0
done

thanks

frankly speaking you don't need to actually echo "yes files are here" or "no not there" because the find command will do that for you, by giving you the necessary output. If files are found, find will show you where its found plus others, if you give it the correct flags.

---

### Post by silverfox1981 on 2007-06-13
thanks for you help.  I think ive tried to run before ive learnt to walk.  back to the basics for me. :p

---


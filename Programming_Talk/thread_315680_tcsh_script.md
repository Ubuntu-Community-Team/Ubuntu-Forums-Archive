---
title: "tcsh script"
date: 2006-12-09
forum: Programming Talk
---

### Post by bajetownrep on 2006-12-09
hello all 

I am just beginning to teach myself to write scripts.I am using tcsh(yes yes I know tcsh is not the best shell to learn how to write scripts but the group that I am in is using it)

Her is my dilemma. I want to write a script called Greetme which will ask the user for their firstname and echo that name back to the screen.

sounds simple enough right? but I am getting a peculiar error and I would like some advice.

the script follows below

#! /bin/tcsh -f

echo Hello What is your name
     $argv[0]
echo your name is $argv[0]


I also tried an alternative which was this

#! /bin/tcsh -f

echo Hello What is your name
      set name=$<
echo Your name is $name


After making the script executable by chmod +x Greetme and running it I receive this error

echo:No match

Can you give any suggestions. I tried googling the error message but some of the pages I found were not the most clear on how to go about fixing syntax problems if any on my part

---

### Post by slavik on 2006-12-09
try 'print' instead of echo ...

also, that $argv[0] doesn't make sense to me since it would be something passed to the script and known before you even do the first echo.

---

### Post by bajetownrep on 2006-12-09
will try print instead

---

### Post by bajetownrep on 2006-12-10
I tried print and that did not work.

I just got print no match found as well. I feel as if I am missing something really simple on my part. :-k :-k

---

### Post by bajetownrep on 2006-12-10
i am still stumped on this one, does anybody know of any information as to how to use some of these errors to troubleshoot scripts

---

### Post by slavik on 2006-12-10
look into tcsh man pages or documentation ...

I am not really big on shell scripts unless they start with '#!/usr/bin/perl'. ;)

---


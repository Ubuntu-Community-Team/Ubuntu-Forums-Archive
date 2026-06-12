---
title: "changing output medium"
date: 2011-01-03
forum: Programming Talk
---

### Post by vivek.pandey on 2011-01-03
suppose i write a program in c++ in a text editor and then ompile and run it on termainal we receive the output on terminal itself.. byt say i m using python as a calulator and want that the output its producing on terminal should instead go on a particular line in a text editor or a particular cell in spreadsheet.. how can i do this... pls somebody help..thanx a lot  :confused::confused::confused:

---

### Post by vivek.pandey on 2011-01-03
> **neo_aryan said:**
> suppose i write a program in c++ in a text editor and then ompile and run it on termainal we receive the output on terminal itself.. byt say i m using python as a calulator and want that the output its producing on terminal should instead go on a particular line in a text editor or a particular cell in spreadsheet.. how can i do this... pls somebody help..thanx a lot  :confused::confused::confused:

somebody pls come up wid a solution

---

### Post by vivek.pandey on 2011-01-05
any1 pls come up wid a suggestion

---

### Post by vivek.pandey on 2011-01-09
well no answer yet..pls som1 give me a solution to this question:o:o:o:o:o

---

### Post by nick_goodfate on 2011-01-09
check this which explains piping: 

[http://www.datasavantconsulting.com/roland/piping.html](http://www.datasavantconsulting.com/roland/piping.html)

---

### Post by vivek.pandey on 2011-01-09
> **nick_goodfate said:**
> check this which explains piping: 

[http://www.datasavantconsulting.com/roland/piping.html](http://www.datasavantconsulting.com/roland/piping.html)

well thanx for the link but the tutorial is too concise and i need bit in detail

---

### Post by nick_goodfate on 2011-01-09
well at least now you know that what you want to do is called piping, in case you didn't already knew...

from the moment you send the output of your program to an other device/program instead of the standard output (your terminal), it's up to this device/program what will do with this output. So you may need to check the manual of gedit(if you want to send the output to a txt)
> "man gedit" in terminal without "" 

and of course you can search Google for mare details about piping and redirection...

---

### Post by QLee on 2011-01-09
Marke this thread as solved and post in the Programming Talk forum.
[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

Post your complete program and indicate where it's not doing what you want it to do. Other coders will be able to see what you need to change. Don't just ask general questions, be specific.

...Or you could ask a moderator to move your question but still be more specific if you want useful help.

---

### Post by vivek.pandey on 2011-01-09
> **nick_goodfate said:**
> well at least now you know that what you want to do is called piping, in case you didn't already knew...

from the moment you send the output of your program to an other device/program instead of the standard output (your terminal), it's up to this device/program what will do with this output. So you may need to check the manual of gedit(if you want to send the output to a txt)


and of course you can search Google for mare details about piping and redirection...

thanx for ur help sir but pls see my original question it needs a bit of more understanding like to output a result on a particular line.. i wud really be grateful if som1 gives me a simple example to illustrate wat i want.. thanx

---

### Post by Elfy on 2011-01-09
moved to programming

please post in english - thank you

---

### Post by nick_goodfate on 2011-01-09
> **neo_aryan said:**
> thanx for ur help sir but pls see my original question it needs a bit of more understanding like to output a result on a particular line.. i wud really be grateful if som1 gives me a simple example to illustrate wat i want.. thanx

Be more specific on what you want. Give an example. For example, which is the form of the file in which you want to send your output? It's an empty one and you want to write to the end of it? is it something like that:
> line1
line2
line3 
and you want to put it after "line2"? Then you have to read the file line after line and when you read "line2" write your output. 
Anyway i hope you find someone to help you, but i'm really suggesting you to do what QLee told you...

---


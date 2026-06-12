---
title: "shell script to find the trafic of a website"
date: 2008-04-18
forum: Programming Talk
---

### Post by psychobeauty on 2008-04-18
hhello all!!!

i want to create a shell script!!
in which the user will input the period of time that is interested...and then the script will find  the number of ip hits in all webpages of my website! and  the number of hits from unique IP addresses i.e. counting two or more hits from a single IP address as one.and to Present this infos in a  table with the headings..

is that possible?

---

### Post by mssever on 2008-04-18
> **psychobeauty said:**
> is that possible?
Yes.

---

### Post by psychobeauty on 2008-04-18
ok!!! bu thow can i do it//??

---

### Post by mssever on 2008-04-18
You'll need to have a logfile with your raw data, of course. Then you'll have to parse that file and filter it according to what you want.

Two observations: First, you need to learn some programming basics before you can tackle this project. See the sticky for more.

Second, this task would be MUCH easier in Ruby or Python than in Bash.

To tell you how to write this program would require me to write it myself and give you the code, which I don't have time to do.

---

### Post by ghostdog74 on 2008-04-18
> **mssever said:**
> 
Second, this task would be MUCH easier in Ruby or Python than in Bash.

you know that's not true right? :) What is easy or not easy does not depend on the language/tools itself. It depends on one's intellect.

---

### Post by mssever on 2008-04-19
> **ghostdog74 said:**
> you know that's not true right? :) What is easy or not easy does not depend on the language/tools itself. It depends on one's intellect.

I disagree. Some languages provide convenient shortcuts for certain tasks. For example, parsing a logfile in pure bash could--depending on the format--require either a lot of code or code that resembles line noise. Using awk doesn't count, since awk is its own language.

In other words, while you can theoretically accomplish any task in any turing-complete language, in practice some languages are much easier than others for a given task.

All the intellect in the world won't add convenient shortcuts, unless you spend time writing them yourself.

---

### Post by ghostdog74 on 2008-04-19
> **psychobeauty said:**
> ok!!! bu thow can i do it//??

provide your sample web log file and describe clearly what you want the output to be.

---

### Post by ghostdog74 on 2008-04-19
> **mssever said:**
> I disagree. Some languages provide convenient shortcuts for certain tasks. For example, parsing a logfile in pure bash could--depending on the format--require either a lot of code or code that resembles line noise. Using awk doesn't count, since awk is its own language.

so what is the "convenient shortcut" that you can use , for example, if you want to parse a log file of a certain format in Python or Ruby?

---

### Post by psychobeauty on 2008-04-19
im sorry i didnt explain well and u missunderstand!!
i have a directory named hits!
there i kept all the hits from ips that visit  the website..


what i want is my script to ask me what i want to view!!
i ll input eg 28 april  10.13
and then the script to dispay to me the ips in the interested date and time!

---

### Post by ghostdog74 on 2008-04-19
> **psychobeauty said:**
> 
what i want is my script to ask me what i want to view!!
i ll input eg 28 april  10.13
and then the script to dispay to me the ips in the interested date and time!

```

read -p "what ?" vardate
echo $vardate
awk -v d="$vardate" '$0 ~ d{print}' weblog

```

---

### Post by psychobeauty on 2008-04-20
thanx alot ghost dog..

and if i want the script to search through all the files in the director that is in..what should i change??

---

### Post by ghostdog74 on 2008-04-20
> **psychobeauty said:**
> thanx alot ghost dog..

and if i want the script to search through all the files in the director that is in..what should i change??

i will leave it to you to try out. Its no fun if i do it for you. Here's a [guide]("http://tldp.org/LDP/abs/html/loops1.html"). Use a for loop to go through the files , read example 10-4 especially.

---

### Post by psychobeauty on 2008-04-20
thanx a lot ghostdog
```


#!/bin/bash
# list-glob.sh: Generating [list] in a for-loop, using "globbing"

echo

for file in *
do
  ..... 
```

can i use this!! for the script to work in the pwd..
but then how can i make it to search the contents of all files..

i know i cant do it with find...what command should i use//?
sorry i am a ittle numb11:)

---

### Post by ghostdog74 on 2008-04-20
```

read -p "what ?" vardate
echo $vardate

for files in *.ext
do
  awk -v d="$vardate" '$0 ~ d{print}' $files
  read -p "Press enter to continue "
done

```

---

### Post by psychobeauty on 2008-04-24
> **ghostdog74 said:**
> ```

read -p "what ?" vardate
echo $vardate

for files in *.ext
do
  awk -v d="$vardate" '$0 ~ d{print}' $files
  read -p "Press enter to continue "
done

```


its getting me an error..
```
what ?28
28
Press enter to continue read: 8: arg count
Press enter to continue read: 8: arg count
Press enter to continue read: 8: arg count
Sun Apr 20 19:12:28 BST 2008
Press enter to continue read: 8: arg count
awk: read error (Is a directory)
Press enter to continue read: 8: arg count
Press enter to continue read: 8: arg count
Press enter to continue read: 8: arg count
 
```


and is only getting numbers input...

---

### Post by ghostdog74 on 2008-04-24
> **psychobeauty said:**
> its getting me an error..
```
what ?28
28
Press enter to continue read: 8: arg count
Press enter to continue read: 8: arg count
Press enter to continue read: 8: arg count
Sun Apr 20 19:12:28 BST 2008
Press enter to continue read: 8: arg count
awk: read error (Is a directory)
Press enter to continue read: 8: arg count
Press enter to continue read: 8: arg count
Press enter to continue read: 8: arg count
 
```


and is only getting numbers input...
what's the difference between the syntax in first read and the read in the loop?

---

### Post by skeeterbug on 2008-04-24
> **ghostdog74 said:**
> so what is the "convenient shortcut" that you can use , for example, if you want to parse a log file of a certain format in Python or Ruby?

Well if you were writing a log parser in Python or Ruby, you can store the parsed data in an object oriented way. A nice re-usable library in Python in Ruby could go a long way, depending on your needs. Maybe later on he would want that output to go somewhere else, etc. I have no bash experience, so I can't speak for that (I skimmed the overview, and saw no object oriented section).

---

### Post by psychobeauty on 2008-04-26
> **ghostdog74 said:**
> what's the difference between the syntax in first read and the read in the loop?



nothing!!!! i just type a number!!!

the loop is has errors it doesnt let me to re-enter a number as it is suppose to!!

---

### Post by ghostdog74 on 2008-04-26
it works for me.

---


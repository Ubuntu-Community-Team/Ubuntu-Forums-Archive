---
title: "Getting creative with SED - removing string and x digits after"
date: 2013-06-17
forum: Programming Talk
---

### Post by cbillson on 2013-06-17
Hi, HELP!

i have a file i'd like to shrink in size a little, and as the date appears twice, i've decided thats a good start.

the file appears as:

< Jun 17 00:00:00 - some data

I'm using sed -e 's/.*$mmm $dd //' myfile

This removes everything up to ' 00:00:00 - '

how can i get rid of the time too, is there any way i can amend the above statement to either remove the next x digits (9 in this case) or make 00:00:00 some form of formatted wildcard?

Thanks in advance

Chris

---

### Post by codemaniac on 2013-06-17
Thread moved to "Programming Talk" sub-forum.

---

### Post by varunendra on 2013-06-17
> **cbillson said:**
> 
the file appears as:

< Jun 17 00:00:00 - some data

I'm using sed -e 's/.*$mmm $dd //' myfile

This removes everything up to ' 00:00:00 - '

how can i get rid of the time too, is there any way i can amend the above statement to either remove the next x digits (9 in this case) or make 00:00:00 some form of formatted wildcard?

I'm not a programming guy and can't understand how the $mmm $dd is working in your example above (is it a predefined variable in your file?). But here's a variation of the sed command that works for the above example (can't say if it has a caveat) -
```
sed 's/.* \([0-9]*:.*\)/\1/'
```
(you don't really need the "-e" option unless the command/script is not the first argument after sed)

I tested it on -
```
echo "Jun 17 00:00:00 - some data" | sed 's/.* \([0-9]*:.*\)/\1/'
```
Returns -
> 00:00:00 - some data

**EDIT:**
Just to be clear, my approach above is to 'keep' a desired part (everything between the "\(..and..\)) and drop the rest.
You can divide a string/line in more than one such groups and keep them by referring as \1, \2, \3 etc.

---

### Post by Vaphell on 2013-06-17
read about regexes, if you need to manipulate text from time to time, few hours you put into reading is about the best long term investment you can possibly make.

you can match digit with [0-9] (range of chars 0-9), capital letters [A-Z], all letters [A-Za-z] etc

if you want to simply remove a part of string
```
$ data="Jun 17 00:00:00 - some data"
$ echo "$data" | sed -r 's/[A-Z][a-z]{2} [0-9]{1,2} [0-9]{2}:[0-9]{2}:[0-9]{2} - //'
some data
```

i use sed with -r option that makes regexes more readable (fewer \ to achieve cool stuff)

as poster above mentioned you can also capture parts of the text and reuse them in a format of your choice, eg
```
$ echo "$data" | sed -r 's/.*[COLOR="#0000FF"]([A-Z][a-z]{2} [0-9]{1,2})[/COLOR][COLOR="#008000"] ([0-9]{2}:[0-9]{2}:[0-9]{2})[/COLOR] - [COLOR="#800080"](.*)[/COLOR]/**[COLOR="#0000FF"]\1[/COLOR]**[COLOR="#800080"]\3[/COLOR]**[COLOR="#008000"]\2[/COLOR]/'
**[COLOR="#0000FF"]Jun 17[/COLOR]**[COLOR="#800080"]some data[/COLOR]**[COLOR="#008000"]00:00:00[/COLOR]
```

---

### Post by cbillson on 2013-06-18
Thanks for the info, makes total sense, and could prove very useful in some other things i'm trying to do - cheers :)

---

### Post by varunendra on 2013-06-18
> **cbillson said:**
> Thanks for the info, makes total sense, and could prove very useful in some other things i'm trying to do - cheers :)

Try and have fun with it. And pleas consider marking the thread as **[Solved]** unless you have any more questions on the topic. If you have questions on a different topic, start a new thread.

Thanks !

---

### Post by Cheesemill on 2013-06-18
This would remove everything up to and including the first ' - '.
```
sed 's/.* - //'
```

---


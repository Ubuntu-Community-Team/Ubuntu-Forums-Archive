---
title: "sed Question"
date: 2007-06-08
forum: Programming Talk
---

### Post by janga on 2007-06-08
Hi guys,
I am just about to learn sed, the stream editor.
Now I hav a problem that i cannot resolve with the help of google.

Basically, I want to format the output of amulecmd into something more readable.

This is my current script:

```
#!/bin/sh
amulecmd -c "show dl" | grep Herunterladen | sed -e 's/^ .\{35\}//g' -e 's/Herunterladen //g' -e [COLOR=Red]MISSING CODE[/COLOR]  | grep --color '\[[0-9]\{1,3\},[0-9]\{1,2\}%\]'
```The output looks something like this (the last grep command is just to colorize the %):

> Alpha Centauri - 2x04 - Wie Ist Die Milchstraße Aufgebaut.mpg      [COLOR=SeaGreen][73,2%][/COLOR] 1/19 - 7,19 kB/s
Alpha Centauri - 2x07 - Gibt Es Schnapps Im All.mpg [COLOR=SeaGreen]     [64,8%][/COLOR] 1/13 - 72 bytes/secNow, you might not see it, but there is a TAB between .mpg and [XX,X%]. What I want to do is to cut the lines into 2 parts around the TAB and switch them. It should look like this:

> [COLOR=SeaGreen][73,2%][/COLOR] 1/19 - 7,19 kB/s - Alpha Centauri - 2x04 - Wie Ist Die Milchstraße Aufgebaut.mpg
[COLOR=SeaGreen][64,8%][/COLOR] 1/13 - 72 bytes/sec - Alpha Centauri - 2x07 - Gibt Es Schnapps Im All.mpgAny Ideas?

---

### Post by Mr. C. on 2007-06-08
echo -e 'dog\tcat' | sed 's/\(.*\)\t\(.*\)/\2\t\1/'

---

### Post by janga on 2007-06-08
Wow, that was really quick! Thank you.
However, i didn't need the echo command. Works without it.

---

### Post by Mr. C. on 2007-06-08
Right, the echo was simply to show an example usage.  I figured you'd grab just the send part.

MrC

---

### Post by janga on 2007-06-09
I am facing another problem...
The script works well now, but...
When I try to sort the output (with sort -nr) it looks like this:

> [73,2%]...
[7,2%]...
[69,8%]...so the command doesn't seem to recognize dezimals...
What can I do?

---

### Post by Mr. C. on 2007-06-09
For your example above: 

```
   sort -n --key=1.2
```

Be sure to set the LC_ALL environment variable in your script if you need different locales.

MrC

---

### Post by janga on 2007-06-09
Thanks again! Now It's perfect.

---

### Post by geekgod on 2007-06-09
I just saw this on stumbleupon...

[http://www.student.northpark.edu/pemente/sed/sed1line.txt](http://www.student.northpark.edu/pemente/sed/sed1line.txt) <<sed refrence (kinda)

---

### Post by janga on 2007-06-09
Me again.
Sorry, but the LC_ALL thing didn't work out for me after all.
but i found out that "sort" has no problems sorting if the numbers have the same amount of digits.

So how would i sed [X,X%] into [0X,X%] ?

Sorry, I'm not lazy at RTFM, but this sed thing is SO sensitive with little mistakes...

---

### Post by Mr. C. on 2007-06-09
Works fine for me:

```
[glacier:tmp] $ cat /tmp/data
[69,83%]
[73,2%]
[7,2%]
[69,81%]
[69,8%]
[glacier:tmp] $ LC_ALL=fr_FR sort -n --key=1.2 < data
[7,2%]
[69,8%]
[69,81%]
[69,83%]
[73,2%]
```

Your idea of trying to make the numbers have the same number of digits is ok, but you don't want to always at a leading 0 (consider 100%, or 0%).  It sounds like you want to make all numbers have exactly 3 digits, but then you have to also ensure the same concept for the decimal digits.  It will not be trivial in sed to do this (it will require multiple expressions); it is the wrong too for the job.  Instead, learn how locale's work, since that will be critical for correct sort or collation used by any program.

Regular expressions require precision and attention to details.  You'll get the hang of it.  Wait until you starting using PCRE!

MrC

---

### Post by janga on 2007-06-09
Well it sure does work with your example, but it doesn't work with my file. Try It.

>  [90,5%] 1/3 - 200 bytes/sec     xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx.ogm
 [82,9%] 1/16 - 5,81 kB/s     xxxxxxxxxxxxxxxxxxxxxxxxxxxxx.avi
 [4,0%] 1/11 - 4,03 kB/s     xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx.mpg
 [22,5%] 1/51 - 4,42 kB/s     xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx.rar
 [13,8%] 1/5 - 7,51 kB/s     xxxxxxxxxxxxxxxxxxxxxxxxxxxxxx.ogm

---

### Post by janga on 2007-06-09
HAHA!
Thats weird! I copied it back from the browser to a text file and it works! But the direct output of my script doesnt.
EDIT: Now I know what was wrong, I had spaces as the first character in every line. That's why it didn't work.
But thank you very much, anyway.

---

### Post by Mr. C. on 2007-06-09
Now would I steer you wrong ?! :-)

Cheers,
MrC

---


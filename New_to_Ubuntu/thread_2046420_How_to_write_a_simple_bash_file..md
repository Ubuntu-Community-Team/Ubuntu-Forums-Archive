---
title: "How to write a simple bash file."
date: 2012-08-22
forum: New to Ubuntu
---

### Post by honey_bee on 2012-08-22
hi,
       I am new in Ubuntu Linux.I want to write a basic bash file with a simple wording "I love Ubuntu Linux". This will be my 1st bash file to understand.
Please guide me the steps taht how can I write a simple bash file.I know vi editor as well.
 
Thanks.
Honey

---

### Post by sandyd on 2012-08-22
**Nano version**
```

nano bash_script.sh

``````

#!/bin/bash
echo "Ubuntu is Good"

```Press control +x, and then 'y' to save and exit.

[B]Vi version
[/B]```

vim bash_script.sh

```Press control + i to enter write mode

```

#!/bin/bash
echo "Ubuntu is Good"

```Press Control +c to exit the write mode

Type ":w" to write the changes
Type ":q" to quit
---------------------------------------------------------------

Make the file readable
```

chmod +x bash_script.sh

```Run
```

./bash_script.sh
```

A few explanations
 - The first line states the script enviroment, which I set to the bash shell (it could be set to sh as well, csh, zsh, .etc .etc)
 - The echo line outputs the text within the quotation marks

---

### Post by Bashing-om on 2012-08-22
X_bee ; Hi, welcome to the forum....
Here is a great tutorial on bash scripting.
[http://mywiki.wooledge.org/FullBashGuide](http://mywiki.wooledge.org/FullBashGuide)

  Enjoy <==BDQ

---

### Post by honey_bee on 2012-08-22
Thanks "sandyd" for your kind help.The steps which you have write are absolute correct. Actually i am new in ubuntu and for write a simple bash file it is a :confused: for me.
Well the thing which I have understand is 
 
1- 1st i have to create open a file like touch  
# touch bash_script.sh
 
2- Now add the code in the blanck file
 
  #!/bin/bash
  echo "Ubuntu is Good"
 
The question which trigger in my mind is why we write **#!/bin/bash** in the top of the  code ?
 
what[COLOR=red]** !**[/COLOR] means  in the line ?
 
Thanks
honey

---

### Post by sandyd on 2012-08-23
the #! states the shell the script uses

For example, if that was python code, not bash,
I could use
```

#!/usr/bin/python

```and 
```

./path/to/python/script

```would run it.

It would be the same as
```

python /path/to/python/script

```In the example above, it would run
```

/bin/bash echo "Ubuntu is Good"

```But immagine having to write thousands of lines beginning with /bin/bash:lolflag:
That would be horrific, so we use this instead ;)

---

### Post by honey_bee on 2012-08-23
Thanks " "sandyd" one again  for the reply. It is now clear. One thing more I want to discuss ,though it is out of the scope of this thread but just for me own practive i was interested to use bash file with [COLOR=red]Crontab [/COLOR][COLOR=black]command.This will be a combination of my bash file and crontab .[/COLOR]
 
Suppose I want to execute this file "bash_script.sh" in the Morning 9 AM in my pc
 
# crontab -e
 
[COLOR=black][COLOR=black][FONT=Verdana]**00 09 * * * **[COLOR=seagreen]/path/to/bash/file/location[/COLOR]/[COLOR=blue]bash_script.sh[/COLOR][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][/FONT][/COLOR] 
[COLOR=black][FONT=Verdana][COLOR=#0000ff] [/COLOR][COLOR=black]which is[/COLOR][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][/FONT][/COLOR] 
[COLOR=black][FONT=Verdana][COLOR=#0000ff][COLOR=black][FONT=Verdana]**00 09 * * * **[COLOR=seagreen]/home/[/COLOR][COLOR=blue]bash_script.sh[/COLOR][/FONT][/COLOR][/COLOR][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][COLOR=#0000ff][/COLOR][/FONT][/COLOR] 
[COLOR=black][FONT=Verdana][COLOR=black]Is it correct ?[/COLOR][/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Honey[/FONT][/COLOR]
[/COLOR]

---

### Post by codemaniac on 2012-08-23
looks ok for a daily 9 am process .

I use the below comments in my cron to remember cron entry syntax .
```

# minute (0-59),
# |      hour (0-23),
# |      |       day of the month (1-31),
# |      |       |       month of the year (1-12),
# |      |       |       |       day of the week (0-6 with 0=Sunday).
# |      |       |       |       |       commands
```

---

### Post by honey_bee on 2012-08-23
Thanks a lot for helping me.
Regards
Honey

---

### Post by sandyd on 2012-08-23
Btw. heres a generator I found useful for crontabs. 
Very exact, and creates timing that would be quite hard to do by hand. 

[http://crontab-generator.com/](http://crontab-generator.com/)

---

### Post by honey_bee on 2012-08-23
Thanks :guitar:

---


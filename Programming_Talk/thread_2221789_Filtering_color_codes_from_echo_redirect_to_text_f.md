---
title: "Filtering color codes from echo redirect to text file."
date: 2014-05-03
forum: Programming Talk
---

### Post by octius4u on 2014-05-03
I am writing a script that shows some system specs.
Since the specs list is longer then a screen I am running 
it through '| less -R'. A short version of the code looks
like this:
```

ColRESET="\e[0m"
ColGREEN="\e[1;32m"
SpecCPUarch=`uname -p`
SpecCPUvendor=`cat /proc/cpuinfo | grep -m 1 vendor_id`
SpecCPUmodel=`cat /proc/cpuinfo | grep -m 1 model\ name`
SpecCPUamount=`cat /proc/cpuinfo | grep -m 1 siblings` 
SpecRam=`free | grep total && free -h | grep -v buffers`

function sysspecs {
   echo -e ColGREEN"--- Processor/s ---------------------------------------------------------------------"ColRESET
   echo -e "$SpecCPUvendor"
   echo -e "$SpecCPUmodel "
   echo -e "architecture    : $SpecCPUarch"
   echo -e "$SpecCPUamount "; echo
   echo -e ColGREEN"--- Memory --------------------------------------------------------------------------"ColRESET
   echo -e "$SpecRam "; echo
}
sysspecs | less -RKeX
```

Sometimes I need to save the output. In that case I am redirecting it to a text file,
like this:

```
bash myspecs.sh > $HOME/MySpecs.txt
```

In the terminal the colors are not absolutely necessary but  they sure help. 
However when I redirect it to a text file I see the color codes.
I need a clean text file, therefor I would like to know if the color codes
 can be filters or removed. I'd like to see them on the display but not in 
text file. Currently I have abandoned the color code in favor of a clean
text file.

Any help is much appreciated. Thank you.

---

### Post by Vaphell on 2014-05-03
maybe a simple parameter?

```
#!/bin/bash

[[ $1 == "-c" ]] && colors=yes

...

if [[ $colors == "yes" ]]
then
    ColRESET="\e[0m"
    ColGREEN="\e[1;32m"
fi
...
```

calling with -c would yield colors but plain text otherwise.
```
./script -c   # colors
./script      # plaintext
```

---

### Post by octius4u on 2014-05-03
It seems remarkably smart and ease. As soon as I get around to try it I'll get back with the outcome.
Thanks a lot for the idea.

---

### Post by octius4u on 2014-05-03
This code is actually part of the script I was asking about on Thread [2220629]("http://ubuntuforums.org/showthread.php?t=2220629"). I am actually calling up the specs with a parameter to begin with, but it's still a great idea. 

```

bash Tweaks1404.sh --sysinfo
# with no color or
bash Tweaks1404.sh --sysinfoC
# with colors.
```

I would have considers some kind of filter to be the ideal scenario but I'm still glad. Thanks. Maybe when I'm done with it I can post it somehow for people to see and try if anyone wishes, and maybe give me some feedback....

---

### Post by octius4u on 2014-05-04
I just thought about using your solution as a condition towards $2 being the '>' or a pattern including '>' and the delimiter '/', when entering something like: "> $HOME/MySpecs.txt". That way I can keep using only one parameter for the same function. Thanks again.

---

### Post by sisco311 on 2014-05-04
You can use the test command to check if stdout is a terminal or not:

```


if [ -t 1 ]
then
    ColRESET="\e[0m"
    ColGREEN="\e[1;32m"
fi
```

---

### Post by octius4u on 2014-05-04
That sounds great, thanks. As soon as I have a moment I'll run a test  and try to understand it better, because the test command is new to me.

---

### Post by octius4u on 2014-06-15
Just wanted to say thanks. It worked very nicely. I consider this matter solved and closed. Thanks again.

---


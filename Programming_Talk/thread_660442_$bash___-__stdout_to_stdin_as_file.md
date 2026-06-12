---
title: "$bash   -  stdout to stdin as file"
date: 2008-01-06
forum: Programming Talk
---

### Post by kutlu on 2008-01-06
how can I pipe stdout to stdin as file?

Example: 
xwdtopnm temp.xwd > temp.pnm
pnmtopng temp.pnm > $1.png

I do not want to create temp.pnm here. I want to pipe the first command's output as an input file to second command without creating file.

---

### Post by stroyan on 2008-01-06
You can use a "|" symbol to connect the stdout of one command to the stdin of another```
xwdtopnm temp.xwd | pnmtopng > $1.png
```

---

### Post by kutlu on 2008-01-08
oh thanks. I always misunderstood the meaning of pipe symbol |  . I always complained about why I cannot use it. Now I understand. :)

now I can use it like that :
xwd -silent -root |  xwdtopnm | pnmtopng > temp.png

It takes a printscreen.

---

### Post by Crinos512 on 2008-10-09
At the risk of getting burned for performing 'Thread Necromancy' I have an issue with Bash and Pipes I do not quite get.

I have written a script (colorize.sh)
```
[COLOR="SeaGreen"]#!/bin/bash[/COLOR]

[COLOR="DarkOrchid"]WARM[/COLOR][COLOR="Red"]=[/COLOR][COLOR="Blue"]80[/COLOR]
[COLOR="DarkOrchid"]COOL[/COLOR][COLOR="Red"]=[/COLOR][COLOR="#0000ff"]65[/COLOR]

if [COLOR="#ff0000"][[[/COLOR] [COLOR="#9932cc"]$1[/COLOR] [COLOR="#ff0000"]<[/COLOR] [COLOR="#9932cc"]$COOL[/COLOR] [COLOR="#ff0000"]]][/COLOR] then echo [COLOR="#8b0000"]"\${color7}"[/COLOR][COLOR="#9932cc"]$1[/COLOR]    [COLOR="SeaGreen"]# COOL[/COLOR]
elif [COLOR="#ff0000"][[[/COLOR] [COLOR="#9932cc"]$1[/COLOR] [COLOR="#ff0000"]>[/COLOR] [COLOR="#9932cc"]$WARM[/COLOR] [COLOR="#ff0000"]]][/COLOR] then echo [COLOR="DarkRed"]"\${color9}"[/COLOR][COLOR="#9932cc"]$1[/COLOR]  [COLOR="#2e8b57"]# HOT[/COLOR]
else echo [COLOR="#8b0000"]"\${color8}"[/COLOR][COLOR="#9932cc"]$1[/COLOR]                       [COLOR="#2e8b57"] # WARM[/COLOR]
fi

exit [COLOR="Blue"]0[/COLOR]

```

When I invoke the script with [COLOR="Blue"]./colorize.sh 10[/COLOR] I get [COLOR="Purple"]${color7}10[/COLOR], which is the output I want...

But, when I invoke the script with [COLOR="Blue"]sensors | grep Core0 | paste -s | cut -c15-18 | ./colorize.sh[/COLOR] I get [COLOR="Purple"]${color7}[/COLOR]
(*Note the conspicuous lack of a temperature.)

it is like the piped input is somehow only valid outside the script... :confused:


(Also feel free to coment on any logical issues or improvements on the script itself, but that was not the primary reason for posting. :) )

---

### Post by geirha on 2008-10-09
Your script is not reading from stdin, it's reading arguments. You can make the stdin into arguments with xargs:
```
sensors | grep Core0 | paste -s | cut -c15-18 | xargs ./colorize.sh
```

---

### Post by Crinos512 on 2008-10-09
Thanks, I can't wait to try it out when I get home. :D

---


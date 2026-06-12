---
title: "Need Help with a Bash/Perl Script"
date: 2008-04-06
forum: Programming Talk
---

### Post by BIGtrouble77 on 2008-04-06
I basically need to write a script that will execute the following:
metacity --replace
wine "myprogram"
on exit compiz --replace


I have no problem doing the first two steps, but I'm not sure how to get it to execute the compiz --replace on exit.  Any suggestions?

-bt

---

### Post by dje on 2008-04-06
Just try this:
```
#!/bin/bash

metacity --replace
wine "my program"
compiz --replace
```
When "my program" exits it will execute the next line, which is 'compiz --replace'

Hope that helps you,
dje

---

### Post by slavik on 2008-04-06
> **dje said:**
> Just try this:
```
#!/bin/bash

metacity --replace
wine "my program"
compiz --replace
```
When "my program" exits it will execute the next line, which is 'compiz --replace'

Hope that helps you,
dje
that is not always the case as 'my program' could be a launcher which will then run the real application.

---

### Post by unutbu on 2008-04-06
I'm no expert at scripting, but I think this works. HIH.

```
#!/bin/bash
function procnumber () {
    echo `ps ax | awk -v var=$1 '{if($1==var){printf("%d", $1)}}'`
}

metacity --replace
wine "my program"
PID=$!

while [ "$PID" != "" ]; do
    PID=`procnumber $PID` 
    sleep 2
done

compiz --replace

```

---

### Post by dje on 2008-04-07
@slavik
Yes you are correct on that although the OP did not specify what "my program" was, it may or may not work for him ;)

dje

---

### Post by BIGtrouble77 on 2008-04-07
Thanks guys.  I should have played with the actual script a bit more before I posted...  Turns out running wine and then replace --compiz works perfectly, but having it change over to metacity first is an issue.  

The problem is that the metacity process never ends so my wine instruction can't start.  Somehow I need to run the metacity --replace independently of the other commands so that they are not waiting for the process to end before they execute.

The reason I have to do this is because I have a game I'm running through wine that doesn't like compiz.  If I just kill compiz and don't load metacity my keyboard stops working 50% of the time, but the game seems to otherwise work fine.  

unutbu, I'll try your suggestion when I get home later today.

-bt

---

### Post by dje on 2008-04-07
Try this:
```
#!/bin/bash

metacity --replace &
wine "my program"
compiz --replace
```

glad you're getting there ;)
dje

---

### Post by BIGtrouble77 on 2008-04-07
dje, that worked perfectly.  Thanks again.

-bt

---

### Post by dje on 2008-04-08
No problem :KS
Glad you got it working

dje

---


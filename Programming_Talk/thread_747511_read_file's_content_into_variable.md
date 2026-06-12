---
title: "read file's content into variable"
date: 2008-04-06
forum: Programming Talk
---

### Post by jmehdi on 2008-04-06
I try to put the content of a file into a variable by doing:

```
$value=`cat sources.xml`
```

but I get this error:

test.sh: line 9: =[<?xml: command not found


Here is my sources.xml file:

```
[<?xml version="1.0"?>
<group.....
.....
/>
]
```

---

### Post by WW on 2008-04-06
Don't put the dollar sign ($) in front of the variable name in an assignment.
Try
```

value=`cat sources.xml`

```

---

### Post by jmehdi on 2008-04-07
> **WW said:**
> Don't put the dollar sign ($) in front of the variable name in an assignment.
Try
```

value=`cat sources.xml`

```

Then I have this error:

Error: Parse error: Didn't understand `[<?xml' (list must end with a ']')

:confused:

---

### Post by ghostdog74 on 2008-04-07
show your whole code. what shell are you using.

---

### Post by jmehdi on 2008-04-07
I use bash, and this line is the first one of my script. I want to retrieve the whole content of the file in a variable ; maybe there is another way to do...

---

### Post by ghostdog74 on 2008-04-07
yes of course there are other ways to do it. What are trying to do actually? where is your code?

---

### Post by jmehdi on 2008-04-07
> **ghostdog74 said:**
> yes of course there are other ways to do it. What are trying to do actually? where is your code?

So, my script tries to update a gconf value:

```

# get the value
gconftool-2 --get /apps/evolution/calendar/sources > sources.xml

# update it
sed  "s|\(name=\"On This Computer\".*\)</group>|\1<source uid=\"my.calendar\" name=\"my calendar\" relative_uri=\"mycal\" color_spec=\"#095401\"/></group>|" $SOURCES  > /dev/null

# read the file
NewValue=`cat sources.xml`

# set the value
gconftool-2 --type list --list-type string --set /apps/evolution/calendar/sources $NewValue
```

---

### Post by ghostdog74 on 2008-04-07
and you said you put it on the very first line ?? remove the other commands first, and make sure you really have sources.xml in your current directory and run this script.
```

#!/bin/bash
value=`cat sources.xml`
echo $value

```
if you are able to run this, then the problem lies with the other commands...where is your $SOURCES variable defined in you sed statement ?

---

### Post by jmehdi on 2008-04-07
> and you said you put it on the very first line ??

Sorry I was a doing a test in which I put it on the first line, but actually I found the error comes from the line after (the set value) ; I need to put the variable between quotes:

```
gconftool-2 --type list --list-type string --set /apps/evolution/calendar/sources "$NewValue"
```

Thanks anyway!

---


---
title: "Printing global variables in shell scripting"
date: 2008-01-05
forum: Programming Talk
---

### Post by evaklo on 2008-01-05
Hi all, this question is kind of dumb, but I can't get the output from a shell script correctly.

```
#! /bin/sh
#lot of code...

echo "1 printing name: $HOSTNAME"
HNAME=`hostname`
echo "2 printing name: $HNAME"

```

This script print:
"1 printing name: "
"2 printing name: myHostName"

The estrange thing is, if I execute the same code in a terminal  I got "good" results.
```

evaklo@myHostName:/$ echo  $HOSTNAME
myHostName
evaklo@myHostName:/$ 

```

Any ideas to solve this?
Thanks in advance.

---

### Post by cmnorton on 2008-01-05
Where and how are you running this that it is not working?

#! /bin/sh
#lot of code...

HOSTNAME=`uname -n`
echo "1 printing name: $HOSTNAME"
HNAME=`hostname`
echo "2 printing name: $HNAME"

As a side note, please remember that !/bin/sh in Ubuntu is a link to dash, not bash. I had to change over my #!/bin/sh scripts from Red Hat to be explicitly #!/bin/bash.

---

### Post by evaklo on 2008-01-05
> **cmnorton said:**
> Where and how are you running this that it is not working?
Q:Where;
[INDENT]A: in a shell[/INDENT]
Q:How;
[INDENT]A: through a .sh file, is something like this:
```
In a mpjfile:
#! /bin/sh
#lot of code...

ssh $host  "cd $MPJ_HOME/bin;./mpjdaemon_linux_x86_32 start "

```
*note: $host is "localhost"*

and the file for what I asked is:
```
 in the $MPJ_HOME/bin/mpjdaemon_linux_x86_32 file
#! /bin/sh
#lot of code...

echo "1 printing name: $HOSTNAME"
HNAME=`hostname`
echo "2 printing name: $HNAME"

```
[/INDENT]

> 
HOSTNAME=`uname -n`

This line works too, thanks.

> 
As a side note, please remember that !/bin/sh in Ubuntu is a link to dash, not bash. I had to change over my #!/bin/sh scripts from Red Hat to be explicitly #!/bin/bash.

Thanks, changing  !/bin/**sh** for  !/bin/**[COLOR="Red"]ba[/COLOR]sh** works.
But I don't know the differences between **dash** and **bash**. I'm going to search them now.

Thanks **cmnorton** for your quickly answer :KS
Lautaro/evaklo

---


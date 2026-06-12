---
title: "How do you find the Directory of the open Shell Script File?"
date: 2011-08-31
forum: Programming Talk
---

### Post by x-D on 2011-08-31
Say if I have a Shell Script, and it sets up a program that can be downloaded, so the file could be anywhere. How to I (in Shell, or some other means), get the directory of the Current Shell Script which is open (the one that sets up the program)?

Cheers for any help....
x-D :guitar:

---

### Post by hyper2hottie on 2011-08-31
Do you want: 
```

pwd

```
Print working directory

---

### Post by apmcd47 on 2011-08-31
> **x-D said:**
> Say if I have a Shell Script, and it sets up a program that can be downloaded, so the file could be anywhere. How to I (in Shell, or some other means), get the directory of the Current Shell Script which is open (the one that sets up the program)?

You have the *$PWD* environment variable and also the builtin *pwd *command and */bin/pwd*. Take your pick. If you want the working directory in which the shell script is invoked because you intend to change the directory try
[PHP]startDir=$PWD[/PHP]somewhere near the start of your script (ie before the first cd command).

Andrew

---

### Post by ofnuts on 2011-08-31
$PWD gives you the current directory, which isn't the directory where the shell script file is (can be invoked with an explicit path, or be somewhere in the PATH). The directory where the script comes from is obtained by:
```

mydir=$(dirname $0)

```
In other words:
```

#! /bin/bash

me=$0
mydir=$(dirname $0)

echo "Me: $me"
echo "My dir: $mydir"

```

---

### Post by x-D on 2011-09-01
So if I wanted to use this information to copy the folder the shell script was in, to another folder how would I go about doing so?

---

### Post by Smart Viking on 2011-09-01
```
cp -r $mydir /location/dir
```

---

### Post by x-D on 2011-09-01
> **Smart Viking said:**
> ```
cp -r $mydir /location/dir
```

Spot on mate :). I'm so bad at shell, just need to know this little thing for a small script. Then how does that paste into another folder? :)

---

### Post by x-D on 2011-09-01
> **ofnuts said:**
> $PWD gives you the current directory, which isn't the directory where the shell script file is (can be invoked with an explicit path, or be somewhere in the PATH). The directory where the script comes from is obtained by:
```

mydir=$(dirname $0)

```In other words:
```

#! /bin/bash

me=$0
mydir=$(dirname $0)

echo "Me: $me"
echo "My dir: $mydir"

```

Hey, I was getting errors, so I tried echo "hello: $mydir" - then it just printed out a plain line - as if there was no Directory?

---

### Post by ofnuts on 2011-09-01
In  many cases $mydir is just a mere dot: ".".

---

### Post by x-D on 2011-09-01
> **ofnuts said:**
> In  many cases $mydir is just a mere dot: ".".
So, I don't understand, could you walk me through how to set it up, so that the folder in which the shell script is located, is copied to a different folder?

---

### Post by apmcd47 on 2011-09-01
> **ofnuts said:**
> $PWD gives you the current directory, which isn't the directory where the shell script file is (can be invoked with an explicit path, or be somewhere in the PATH). The directory where the script comes from is obtained by:
```

mydir=$(dirname $0)

```
Actually OP was so badly worded I didn't know what he wanted. It occurred to me that was what he wanted but I dismissed it.
My preference would be:[PHP]myname=${0##*/}
mydir=${0%/\*\}
[/PHP]
> **ofnuts said:**
> In other words:
```

#! /bin/bash

me=$0
mydir=$(dirname $0)

echo "Me: $me"
echo "My dir: $mydir"

```

The problem is when you invoke the code as[PHP]sh myprog[/PHP]you end up with mydir being null. You then have to add something like [PHP]mydir=${mydir:-$PWD}[/PHP]And don't forget that if you invoke it with a relative path and then want to move to a different directory in the script ...

[PHP]#!/bin/bash
myname=${0##*/}
mydir=${0%/\*\}
mydir=${mydir:-$PWD}
mydir=$(cd $mydir; pwd -p)

printf "mydir is %s\n" $mydir[/PHP]

Basically what should happen is that mydir is set to something which is not null and then a subshell is invoked to go to the location of mydir and pass back the absolute path. But I haven't tested this so I may have it wrong.

Andrew

---

### Post by ofnuts on 2011-09-01
> **apmcd47 said:**
> Basically what should happen is that mydir is set to something which is not null and then a subshell is invoked to go to the location of mydir and pass back the absolute path. But I haven't tested this so I may have it wrong.

AndrewThe absolute path of a file or dir can be obtained with readlink.
```

>pwd
*/usr/lib*
>readlink -e ../../usr/share/../local/man/man1/../man5/gimprc-2.7.5 
*/usr/local/share/man/man5/gimprc-2.7.5*

```

---

### Post by x-D on 2011-09-02
> **ofnuts said:**
> The absolute path of a file or dir can be obtained with readlink.
```

>pwd
*/usr/lib*
>readlink -e ../../usr/share/../local/man/man1/../man5/gimprc-2.7.5 
*/usr/local/share/man/man5/gimprc-2.7.5*

```

I really need to learn Shell and PHP. Spent far too much time on C++ and Python.

---


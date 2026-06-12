---
title: "Problem with Python"
date: 2006-07-29
forum: Programming Talk
---

### Post by tseliot on 2006-07-29
Hi, I'm trying to write a little script in Python which checks Ubuntu's version and prints the output.

I have written this:

```
#/usr/bin/python
import os, sys
  
def archit_system():
    release = os.system('cat /var/log/installer/lsb-release | grep RELEASE | sed s/.*=//')
    if release == '5.10':
        print release + 'ubuntu_breezy'
       
    elif release == '6.06':
        print release + 'ubuntu_dapper'
        
    else:
        print "Your Operative System does not seem to be supported by Envy"
        
    print release   

archit_system
```

If I run the script in the following way it doesn't work:
```
python prova.py
```


I'm a newbie in Python. Please, tell me what's wrong.


Thanks in advance

---

### Post by agger on 2006-07-29
Well, the reason it doesn't seem to run is that you need to call the archit-system function.

```
archit-system
```

is an expression which denotes the function "archit-system" - it doesn't call the function. If you replace that line with

```
archit-system()
```

you get some output.
However, the output I get is this:

```

cat: /var/log/installer/lsb-release: No such file or directory
Your Operative System does not seem to be supported by Envy
0

```
So /var/log/installer also doesn't seem to be the right place to look for this.

---

### Post by Thirsteh on 2006-07-29
nevermind :)

---

### Post by tseliot on 2006-07-29
> **agger said:**
> Well, the reason it doesn't seem to run is that you need to call the archit-system function.

```
archit-system
```

is an expression which denotes the function "archit-system" - it doesn't call the function. If you replace that line with

```
archit-system()
```

you get some output.
My bad ;) 

[QUOTE=agger;1313407]However, the output I get is this:
```

cat: /var/log/installer/lsb-release: No such file or directory
Your Operative System does not seem to be supported by Envy
0

```
So /var/log/installer also doesn't seem to be the right place to look for this.

If I type this command in Terminal:
```
cat /var/log/installer/lsb-release | grep RELEASE | sed s/.*=//
```

it returns:
```
6.06
```

Therefore the command is right.

Any ideas?

---

### Post by tseliot on 2006-07-29
If I use the script in Python I get this:
```
$ python prova.py
6.06
Your Operative System does not seem to be supported by Envy
0
```

---

### Post by agger on 2006-07-29
Maybe for some reason I didn't get a file called "lsb-release" during the install process?

The "var" hierarchy is for transient stuff like log files anyway, so most of it may usually be safely deleted - which means that you can't count on configuration data to stay there in the general case.

The reason I don't tell you what's the right place to look, then, is I don't know - but I suspect somewhere in /etc.

---

### Post by Lord Illidan on 2006-07-29
> **tseliot said:**
> If I use the script in Python I get this:
```
$ python prova.py
6.06
Your Operative System does not seem to be supported by Envy
0
```

I am not super at python, but it seems to me that this is the problem:

```
    release = os.system('cat /var/log/installer/lsb-release | grep RELEASE | sed s/.*=//')
```

Instead of putting the result of the command in release, it justs outputs the result of the command to the terminal.

---

### Post by tseliot on 2006-07-29
> **Lord Illidan said:**
> I am not super at python, but it seems to me that this is the problem:

```
    release = os.system('cat /var/log/installer/lsb-release | grep RELEASE | sed s/.*=//')
```

Instead of putting the result of the command in release, it justs outputs the result of the command to the terminal.

And how could I solve it?

---

### Post by tseliot on 2006-07-29
> **agger said:**
> Maybe for some reason I didn't get a file called "lsb-release" during the install process?

The "var" hierarchy is for transient stuff like log files anyway, so most of it may usually be safely deleted - which means that you can't count on configuration data to stay there in the general case.
Ok, I'll change that when the biggest problem is solved

---

### Post by tseliot on 2006-07-29
Ok, maybe this recipe can help me :D :
[http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/52296](http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/52296)

---

### Post by Wallakoala on 2006-07-29
umm...when I run ```
cat /var/log/installer/lsb-release | grep RELEASE | sed s/.*=//
```

the output is 5.10

but I am running dapper...

this is weird...

---

### Post by Lord Illidan on 2006-07-29
> **Wallakoala said:**
> umm...when I run ```
cat /var/log/installer/lsb-release | grep RELEASE | sed s/.*=//
``` 
the output is 5.10

but I am running dapper...

this is weird...

Did you install dapper or upgraded from breezy?

---

### Post by asimon on 2006-07-29
Why is /var/log/installer/lsb-release checked instead of /etc/lsb-release?

On many systems these files are different!

---

### Post by tseliot on 2006-07-29
I've found out that the right command is:
```
lsb_release -c
```

which gives me:
```
$ lsb_release -c
Codename:       dapper
```

---

### Post by tseliot on 2006-07-29
> **tseliot said:**
> Hi, I'm trying to write a little script in Python which checks Ubuntu's version and prints the output.

I have written this:

```
#/usr/bin/python
import os, sys
  
def archit_system():
    release = os.system('cat /var/log/installer/lsb-release | grep RELEASE | sed s/.*=//')
    if release == '5.10':
        print release + 'ubuntu_breezy'
       
    elif release == '6.06':
        print release + 'ubuntu_dapper'
        
    else:
        print "Your Operative System does not seem to be supported by Envy"
        
    print release   

archit_system
```

If I run the script in the following way it doesn't work:
```
python prova.py
```


I'm a newbie in Python. Please, tell me what's wrong.


Thanks in advance

And the solution to my question is.....

this function (which I saw in EasyUbuntu):

```
def codename():
    p = os.popen("lsb_release -c")
    try:
        codename = p.readline().strip()
        tokens = codename.split("\t")
    finally:
        p.close()
    return tokens[-1].lower()
```

---


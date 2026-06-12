---
title: "Stuck on a simple script, bash beginner"
date: 2012-10-24
forum: Programming Talk
---

### Post by CaptainMark on 2012-10-24
I need a little help with a bash script, I think I'll always be a beginner on it buts it only a tiny hobby so I wont beat myself up over asking for help on this one, 
Basically my question is how can I have bash script with an if statement that will only execute if a certain package is installed, so far I have this much which doesn't yet work```
if [ $"dpkg-query -l qdbus" ]; then echo success; fi
```I was hoping that if the package qdbus was not installed then the statement would evaluate to false and the "then echo success" would not run, but it runs regardless of what I type here, is there a way of bash evaluating an if statement and basically say "If this command gives an error then evaluate to false"

Alternatively I could append 2>/dev/null to the command and basically ask bash "If this command gives any output, evaluate to true, otherwise evaluate to false"

I hope I've explained myself well. If not please ask me any questions

Thanks for any help you offer

Mark

---

### Post by Lars Noodén on 2012-10-24
You're probably looking for something like this:

```

if dpkg-query -l qdbus > /dev/null 2>&1; then echo success; fi

```

But that will return success even if the package was once installed but has subsequently been uninstalled (rc rather than ii) .

---

### Post by papibe on 2012-10-24
Hi CaptainMark.

Yo can do as simple as:
```
if dpkg-query -l qdbus; then echo success; fi
```
although, redirecting both standard and error outputs would look better:
```
if dpkg-query -l qdbus &> /dev/null; then echo success; fi
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by Lars Noodén on 2012-10-24
After a bit of trying the following should work in that it gets only installed packages.

```

if [ "install" = "$(dpkg --get-selections dbus | awk '{print $2}')" ];
then echo success ;
fi

```

Edit: That has bugs, too.  A package that is not installed but is in queue to be installed will still pass.  It should have been done with dpkg-query, as you began with, which will give the actual status in the second character of the first column of output.

```

if  [ "i" = "$(dpkg-query -l | awk '$2 == "dbus" {print substr($1,2,2)}')" ];then echo success;fi

```

---

### Post by CaptainMark on 2012-10-24
Wow, I sorta got a bit lost there. I've found the command 'which' I think this will be accurate enough for my purposes for now, so I'm going to use```
if which qdbus; then echo sucess; fi
```I dont need to worry about the output looking good, basically I'm using qdbus to check once banshee has correctly started to automatically play music on login. so the output will be hidden,
thanks for your help, I'll definitely have another look at both responses to understand them better.

Regards
Mark

---

### Post by Lars Noodén on 2012-10-24
Along those lines, you might look at using a [test](http://manpages.ubuntu.com/manpages/precise/en/man1/test.1.html).  For example, -x means the file exists and it is executable.

```

if [ -x /usr/bin/qdbus ];then echo success;fi

```

---

### Post by CaptainMark on 2012-10-24
More good ideas, thanks

---


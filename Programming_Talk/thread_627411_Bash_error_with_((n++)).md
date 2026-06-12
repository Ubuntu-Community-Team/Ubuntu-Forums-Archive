---
title: "Bash error with ((n++))"
date: 2007-11-30
forum: Programming Talk
---

### Post by flinkdeldinky on 2007-11-30
Following a bash tutorial located here:
[http://www.bit-tech.net/bits/2007/11/26/bashing_through_scripts/2](http://www.bit-tech.net/bits/2007/11/26/bashing_through_scripts/2)

I run this simple piece of code:
#! /bin/bash

n=1
while [ $n -le 10 ]
do
   echo $n
   (( n++ ))
done
and the terminal spits out:

while: 8: n++: not found 

but it spits it repeatedly and I've got to Ctrl-C my way out.

I'm running kubuntu 7.10

---

### Post by Trumpen on 2007-11-30
How do you run it? I hope not with sh like:

```
sh script.sh
```

Try using bash instead of sh or better make it "executable" with:

```
chmod a+x script.sh
```
and then
```
./script.sh
```

---

### Post by geirha on 2007-11-30
In ubuntu, sh is a symlink to dash, which is a less feature rich shell than bash (and does not understand the (( )) syntax that bash does). On some distros, sh is a symlink to bash, and on such systems, doing "sh a_bash_script.sh" will work. That guide wrongfully assumes that sh is bash on all systems.

---

### Post by flinkdeldinky on 2007-11-30
Thanks. That did it.  I was using sh to run the script. Usually I do set my scripts as executable, the only reason I didn't here was because the author mentioned that using sh was his prefered method and I figured I would be writing a lot of 'one of' scripts so would save the time of chmod.

---

### Post by flinkdeldinky on 2007-11-30
Yes I was using sh to run the script.  Is there a reason not to link sh to bash?

I'm just curious.

---

### Post by geirha on 2007-11-30
If you're curious, you should read this: [http://en.wikipedia.org/wiki/Bourne_shell](http://en.wikipedia.org/wiki/Bourne_shell). 

Basicly there's nothing wrong with having sh point to bash, but dash is more lightweight, and if you have a script that doesn't utilize any of the extra features bash has to offer, you'll use a little less resources by running it with dash.

---

### Post by Trumpen on 2007-11-30
I would just like to add this quote:

> "dash" is a POSIX compliant shell that is much smaller than "bash". We take advantage of that by making it the shell on the installation root floppy, where space is at a premium.

It can be usefully installed as /bin/sh (because it executes scripts somewhat faster than "bash"), or as the default shell either of root or of a second user with a userid of 0 (because it depends on fewer libraries, and is therefore less likely to be affected by an upgrade problem or a disk failure). It is also useful for checking that a script uses only POSIX syntax.


directly from [http://packages.ubuntu.com/gutsy/shells/dash](http://packages.ubuntu.com/gutsy/shells/dash)

By the way, bash has an option, "--posix", which should make it respect the posix standard. However I haven't seen any difference in executing a script with or without that option yet.

---


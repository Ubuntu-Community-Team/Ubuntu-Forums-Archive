---
title: "Shell script Shebang problem"
date: 2011-10-10
forum: New to Ubuntu
---

### Post by Targettio on 2011-10-10
Hi I am new to the whole world of shell scripting and I am having some trouble. I am running 11.04 desktop 64bit with all the current updates. Python is Python 2.7.1+ (checked with 'Python -V')

I am trying to run a simple 'hello world' python script

test2.py:
```

#!/usr/bin/env python
print "Python hello world"

```

If I go to the director which holds test2.py and type "python test2.py" I get:
```

Python hello world

```

Which is great. But if I try ". test2.py" I get:
```

Warning: unknown mime-type for "Python hello world" -- using "application/octet-stream"
Error: no such file "Python hello world"
chris@TargServ1:/var/www/cgi-bin$ . test2.py
Warning: unknown mime-type for "Python hello world" -- using "application/octet-stream"
Error: no such file "Python hello world"

```

The first check was to ensure it had all the necessary permissions:
```

$ ls -l test2.py
-rwxrwxrwx 1 nobody nogroup 49 2011-10-10 09:05 test2.py

```
Which seemed in order.

This made me assume it is the shebang that is wrong in some way, so started googling. I tried:
#!/usr/bin/env python
#!/usr/bin/python
#!/usr/local/bin/env python
#!/usr/local/bin/python
#! /usr/bin/env python
#! /usr/bin/python
#! /usr/local/bin/env python
#! /usr/local/bin/python
And they all gae the same result.

I then tried 'which python' to confirm that it was installed and check the director and got:
```

/usr/bin/python

```

So I know python is installed where it is supposed to be and works (if I type /usr/bin/python it opens python terminal), but for some reason my script still wont work. 

Next I checked 'echo $PATH' and got:
```

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```

Which shows /user/bin so that is all in order. 

Next I tried using perl as it maybe a python install error or something else python specific. But that gave me exactly the same problem. 

Finally I tried a bash script in the same folder with the same permissions
test2.sh:
```

#!/bin/sh
echo "hello worlD"

```

This will run correctly by typing ". test2.sh". Which is really frustrating as I can't see why the bash script will run but the python/perl won't.

```

$ which bash
/bin/bash

```

I am sure it is something incredibly simple, like an option or setting that is stopping me, but I can't find it.

I am trying to make these scripts into cgi scripts for my webserver, so I want to use python and I need the shebang to work .

p.s. sorry for the long post, but I wanted to give you as much info as possible. I didn't want to be the noob who types "why doesn't my script work?" and expect everyone to magically know. :lolflag:

---

### Post by sisco311 on 2011-10-10
Hi and welcome to the forums.

Hmmm, it sounds like an encoding problem. What text editor are you using?

In nano you can press Ctrl+o, then Alt+d or Alt+m to toggle between Dos/Mac and Unix formats. 

See: BashFAQ #52 (link in my signature).

---

### Post by papibe on 2011-10-10
I think that way of calling works for shell scripts only. Try this for anything else:
```
$ ./test2.py
```
Regards.

EDIT: **confirmed**. See point 3 [here]("http://www.thegeekstuff.com/2010/07/execute-shell-script/"). So 'print' is being executed by the shell. Try this on the command line
```
$ print "Hello"
Warning: unknown mime-type for "Hello" -- using "application/octet-stream"
Error: no such file "Hello"

```

---

### Post by Targettio on 2011-10-10
> **papibe said:**
> I think that way of calling works for shell scripts only. Try this for anything else:
```
$ ./test2.py
```
Regards.


This sorted it. Thank you.

I have also tested the actual cgi scripts and they are working as well (probably should have rechecked them before posting).

---


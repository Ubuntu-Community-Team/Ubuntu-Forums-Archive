---
title: "bash script: making variable the result of a command"
date: 2007-01-03
forum: Programming Talk
---

### Post by Mateo on 2007-01-03
I'm trying to mark my variable to be the result of a command.  Here's what my script looks like:

```
#!/bin/bash
today="date +%Y_%m_%-e"
echo 'today is '$today
```

but it returns this:

> today is date +%Y_%m_%-e

so, obviously, my "today" variable is not the **result** of the date command, but the actual command line itself.  How do I achieve what I'm trying to achieve here?  Thanks.

---

### Post by IYY on 2007-01-03
Here's how:

```
#!/bin/bash
today=`date +%Y_%m_%-e`
echo 'today is '$today
```

The backquote key is often above the tab key.

---

### Post by Mateo on 2007-01-03
great, thanks, that's simple enough.

---

### Post by pmasiar on 2007-01-03
> **IYY said:**
> The backquote key is often above the tab key.

backquote means "evaluate" in bash and perl, it is different from simple and double quote.

---

### Post by F W Adams on 2009-02-14
It's not quite that simple. If you use an _ to put in leading zeros as spaces ( between the date and time, on the hours ) then as the example below shows, the first two lines with backquote as shown above doesn't work properly whereas the last two lines with single quote does.

```
#!/bin/bash
starx=`date  +%y.%m.%d%_6H:%M:%S`
echo $starx

starx='date  +%y.%m.%d%_6H:%M:%S'
eval $starx

```

---

### Post by F W Adams on 2009-02-14
Actually it's more complicated than I thought. For a longer process you can see that the second method doesn't give the correct result either, or not what was intended. The first method is a bug? The second evaluates the date and time at the time of execution and not as I intended, to display the original date and time.

---

### Post by argie on 2009-02-14
That is how echo works. To preserve whitespace, use double-quotes. Like so:

```

#!/bin/bash
starx=`date  +%y.%m.%d%_6H:%M:%S`
echo "$starx"

```

---

### Post by F W Adams on 2009-02-14
ok, thanks, that's fixed it. I was just trying "echo abc  def" at the command line and beginning to realise the problem was in echo. Why can't something like that be mentioned under "man echo".

---

### Post by geirha on 2009-02-14
> **F W Adams said:**
> ok, thanks, that's fixed it. I was just trying "echo abc  def" at the command line and beginning to realise the problem was in echo. Why can't something like that be mentioned under "man echo".

Well, it has nothing to do with echo really, echo just outputs what it gets. Bash uses, by default, any number of spaces, tabs and newlines as seperators. So, if you do ```
echo abc     def
``` bash will see that you want to run the command echo, with two arguments, abc and def. So it starts the command echo and passes it those two arguments.

If you do ```
echo "abc      def"
``` bash will consider everything inside the two "" as one argument, and starts echo with the one argument, abc      def.

---

### Post by andman on 2009-03-01
Hi I'm running ubuntu 8.10 2.6.27-11-generic.  I'm having trouble with back quoting in bash in the script below.  In both examples the results of command are not being stored in the variable.  I've got to be missing something pretty simple...


#!/bin/bash

echo attempt one
version=$(encfs --version)
echo ${version}

echo attempt two
version=`encfs --version`
echo ${version}


root@andman-laptop:/scripts/back# ./back.sh 
attempt one
encfs version 1.4.2

attempt two
encfs version 1.4.2

---

### Post by geirha on 2009-03-01
It is likely that encfs --version outputs the version to stderr. The `` and $() only catch stdout, so try redirecting stderr to stdout so any output of the command gets caught.
```

version=$(encfs --version 2>&1)

```

---


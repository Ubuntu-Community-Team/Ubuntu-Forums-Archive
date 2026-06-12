---
title: "What does &quot;grep &quot;something&quot; &gt; /dev/null&quot; do?"
date: 2013-10-13
forum: Programming Talk
---

### Post by vasa1 on 2013-10-13
[Stinkeye posted a code]("http://ubuntuforums.org/showthread.php?t=2180156&p=12814007#post12814007") using **wmctrl** to detect whether a window is present (minimized or not). If it is present, it is brought into focus. If the window doesn't exist, the application is run:```
sh -c "wmctrl -a <str> || <start command>"
```

I came across a lengthier version [here]("http://askubuntu.com/a/157787/25656"), and in the context of using **wmctrl**, it would look something like this:```

#!/usr/bin/env bash

if wmctrl -l | grep -i "Firefox" > /dev/null
then
  wmctrl -a firefox
else
  firefox
fi

```

My question is about "**grep -i "Firefox" > /dev/null**": how does that work? What does "**> /dev/null**" do?

A second point is that the author used "[f]irefox" instead of just "firefox" but I couldn't understand the reason for that.

---

### Post by Vaphell on 2013-10-13
/dev/null is a pseudodevice that acts as a garbage bin. Redirect there as if you redirected to a file, the difference being there will be no trace of output anywhere
That said, the redirection was not necessary as grep has -q option that suppresses its output

```
$ x='something firefox something'
$ if echo "$x" | grep -i Firefox; then echo TRUE; else echo FALSE; fi
something [COLOR="#FF0000"]firefox[/COLOR] something  [COLOR="#0000FF"]<- we don't want to see this[/COLOR]
TRUE
$ if echo "$x" | grep -i Firefox > /dev/null; then echo TRUE; else echo FALSE; fi
TRUE
$ if echo "$x" | grep -iq Firefox; then echo TRUE; else echo FALSE; fi
TRUE
$

```


as for bracketed first char. In comments below he explains it's there to avoid grep finding itself in case of *ps aux | grep program.*
grep will show up as 'grep program' on the list of processes and will find itself and you will get something like this
```
$ ps aux | grep bash
me   2017  0.0  0.1  22432  5220 pts/0    Ss   07:43   0:00 **bash**
me   2072  0.0  0.1  22428  5200 pts/1    Ss+  07:53   0:00 [**bash**]
me   2747  0.0  0.0   7652   920 pts/0    S+   09:19   0:00 grep --color=auto **bash**
```
but when you run *ps aux | grep [p]rogram*
```
$ ps aux | grep [b]ash
me   2017  0.0  0.1  22432  5220 pts/0    Ss   07:43   0:00 bash
me   2072  0.0  0.1  22428  5200 pts/1    Ss+  07:53   0:00 [**bash**]
```
grep --color auto [b]ash wont get matched because [b]ash regex doesn't match '[b]ash' string

that said, *pgrep* is a better tool for that

---

### Post by vasa1 on 2013-10-13
> **Vaphell said:**
> /dev/null is a pseudodevice that acts as a garbage bin. Redirect there as if you redirected to a file, the difference being there will be no trace of output anywhere
That said, the redirection was not necessary as grep has -q option that suppresses its output
...[/code]

Okay, so in grep's specific case we can use **-q** but otherwise can use **> /dev/null**.

> **Vaphell said:**
> as for bracketed first char. ... because [b]ash regex doesn't match '[b]ash' stringYet another type of regex! From [here]("http://mywiki.wooledge.org/BashGuide/Patterns"), it appears that the rules change with bash updates!
BTW, this link also says that "*we highly recommend you just never quote your regex*". Is that why the string wasn't between double quotes? So we should just do```
 grep -options string
``` and not ```
grep -options "string"
```
> **Vaphell said:**
> that said, *pgrep* is a better tool for thatIs that because of "*The running pgrep or pkill process will never report itself as a match*." (from man pgrep)?

---

### Post by dwhitney67 on 2013-10-13
> **vasa1 said:**
> Okay, so in grep's specific case we can use **-q** but otherwise can use **> /dev/null**.

The -q option is not portable to all Unix-like systems.  So if you are interested in developing portable scripts, I would recommend using /dev/null to dispose of unwanted output.

---

### Post by vasa1 on 2013-10-13
> **dwhitney67 said:**
> The -q option is not portable to all Unix-like systems.  So if you are interested in developing portable scripts, I would recommend using /dev/null to dispose of unwanted output.
Thanks for that! Despite my bean count, I'm just a beginner in scripting and by no means close to developing anything. But I'm enjoying learning the tricks of the trade.

---

### Post by Vaphell on 2013-10-13
> **vasa1 said:**
> Okay, so in grep's specific case we can use **-q** but otherwise can use **> /dev/null**.

Yet another type of regex! From [here]("http://mywiki.wooledge.org/BashGuide/Patterns"), it appears that the rules change with bash updates!
BTW, this link also says that "*we highly recommend you just never quote your regex*". Is that why the string wasn't between double quotes? So we should just do```
 grep -options string
``` and not ```
grep -options "string"
```

there are 2 kinds of patterns
- shell globs: eg [abc]*, used in shells to match files
- regular expressions: eg [abc].*, used to match text in grep, sed, awk, you name it + bash [[ ]]

in case of bash globs you don't want to quote it too much, because quoted wildcards like * lose their magic
```
ls 'abc*' # literal 'abc*'
ls 'abc'* # anything that matches 'abc'+<whatever>
ls "$var"/* # anything under dir named $var
```

in case of globs  used with **find -name** you need to quote them to prevent upacking the expression before find runs ( shell: step1 - expand parameters and globs, step2 - run command with the results)
let's say you have a dir tree with few avi files at top level
```
find -iname *.avi # will expand glob to find -iname 'file1.avi' 'file2.avi' = error
```
```
find -iname '*.avi' # passes the glob unchanged to find, only there it gets used properly
```

inside [[ ]] test brackets different rules apply. It's the only place where you can use unquoted variables and get away with it.
```
$ x='abc def'
$ [[ $x =~ 'abc.*' ]] && echo true # didn't work because regex assumed by =~ operator included quotes
$ [[ $x =~ abc.* ]] && echo true
true
$ [[ $x = 'abc def' ]] && echo true  # would fail in [ ] with too many arguments error
true
```

Any other case of using regexes falls under standard rules and you want to always wrap them, preferably in single quotes to avoid surprises, because yet again shell would try to expand the parameter and if there is a matching file, grep would get things other than what you intended.

> Is that because of "*The running pgrep or pkill process will never report itself as a match*." (from man pgrep)?
yes, besides it's a tool that specializes in processes, why not use that instead of parsing outputs by hand?

---

### Post by vasa1 on 2013-10-14
> **Vaphell said:**
> there are 2 kinds of patterns
- shell globs: eg [abc]*, used in shells to match files
- regular expressions: eg [abc].*, used to match text in grep, sed, awk, you name it + bash [[ ]]

in case of bash globs you don't want to quote it too much, because quoted wildcards like * lose their magic ...

in case of globs  used with **find -name** you need to quote them to prevent upacking the expression before find runs ( shell: step1 - expand parameters and globs, step2 - run command with the results) ...
...
inside [[ ]] test brackets different rules apply. It's the only place where you can use unquoted variables and get away with it.
...
Any other case of using regexes falls under standard rules and you want to always wrap them, preferably in single quotes to avoid surprises, because yet again shell would try to expand the parameter and if there is a matching file, grep would get things other than what you intended.
...
I've saved this post for future reference. I came across globbing first when using Privoxy's user.action file for making blocking rules. I'm not sure I fully grasped the subtleties involved but went ahead by trial-and-error and looking at Privoxy's logs.
**Find** also gave me quite a bit of grief but I'll give it another go with the knowledge I gained here. But I'm going to make another post about 
> grep --color auto [b]ash wont get matched because [b]ash regex doesn't match '[b]ash' string

---

### Post by Bachstelze on 2013-10-14
> **dwhitney67 said:**
> The -q option is not portable to all Unix-like systems.  So if you are interested in developing portable scripts, I would recommend using /dev/null to dispose of unwanted output.

-q is mandated by [POSIX](http://pubs.opengroup.org/onlinepubs/009695399/utilities/grep.html).

---


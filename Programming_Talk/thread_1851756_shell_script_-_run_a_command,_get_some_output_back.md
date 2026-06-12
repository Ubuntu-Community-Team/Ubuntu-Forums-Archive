---
title: "shell script - run a command, get some output back."
date: 2011-09-28
forum: Programming Talk
---

### Post by yanom on 2011-09-28
So I'm writing this shell script and i want to run this command within the shell script:
```
/usr/bin/zenity --question --title "Blocked: $*" --text "The file '$exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the <a href=\"https://wiki.ubuntu.com/Security/ExecutableBit\">executable bit</a>. HOWEVER, you can choose to override the security protections and open this potentially unsafe file. Execute manual override?"
```

Then, I want it to do something if that command returns 0, and something else if it returns 1.

What I'm trying to do here is rewrite Ubuntu's infamous cautious-launcher so that it supports manual override. This is because some filesystems (i.e. NTFS) don't support marking things executable. Full code of what I have right now:
```
#!/bin/bash
# For use with .desktop files and MIME handlers so that the Ubuntu Policy
# can be followed: programs cannot be executed when they lack the execute bit.
# https://wiki.ubuntu.com/SecurityTeam/Policies#Execute-Permission%20Bit%20Required
exe="$1"
shift || true
if [ -n "$exe" ] && [ ! -x "$exe" ] && \
   [ "${exe:0:5}" != "/usr/" ] && [ "${exe:0:5}" != "/opt/" ]
then
    if [ -n "$DISPLAY" ] && [ -x /usr/bin/zenity ]; then
	if  
		/usr/bin/zenity --question --title "Blocked: $*" --text "The file '$exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the <a href=\"https://wiki.ubuntu.com/Security/ExecutableBit\">executable bit</a>. HOWEVER, you can choose to override the security protections and open this potentially unsafe file. Execute manual override?"
	then
		echo "aborting"
	else
		exec "$@" "$exe"
	fi
    else
        echo "$*: '$exe' is not executable.  Aborting." >&2
    fi
    exit 1
fi
exec "$@" "$exe"
```

---

### Post by yanom on 2011-09-29
anyone?

---

### Post by sisco311 on 2011-09-29
What's your question?

---

### Post by yanom on 2011-09-29
in bash script, can i run a command from within the script, and then see what the return code of that program is?

---

### Post by sisco311 on 2011-09-29
? expands to the exit status of the most recently executed commmand (well, more precisely, foreground pipeline)

```
[sisco@acme xtmp]$ true
[sisco@acme xtmp]$ echo $?
0
[sisco@acme xtmp]$ false
[sisco@acme xtmp]$ echo $?
1

```

exit status 0 means success
non-0 exist code means failure 

If you press Yes in the zenity question, zenity returns 0 (success). If I understand your code correctly, you want to run a command if the user selects Yes:
```
if zenity ...
then
    run a command
else
    do nothing
fi
```

See:  [http://mywiki.wooledge.org/BashGuide/TestsAndConditionals](http://mywiki.wooledge.org/BashGuide/TestsAndConditionals)

---

### Post by yanom on 2011-09-29
...yes. If they select yes, continue.
sooo, 
```

if $?
   run command
fi

```
?

---

### Post by dave01945 on 2011-09-29
just do 

```
if zenity --question...; then
         run command
fi
```

---

### Post by yanom on 2011-09-29
> **dave01945 said:**
> just do 

```
if zenity --question...; then
         run command
fi
```

include the semicolon? also, the whole command is several words and includes many quotes. should i somehow surround the command with quotes and/or use backslashes on existing quotes?

---

### Post by dave01945 on 2011-09-29
> **yanom said:**
> include the semicolon? also, the whole command is several words and includes many quotes. should i somehow surround the command with quotes and/or use backslashes on existing quotes?

you only need to quote the text strings on the --title and --text options

and the semi colon is only needed if **then** is on the same line as the **if**, you can put **then** on the next line then you don't need the semi colon

---

### Post by yanom on 2011-09-29
Ok, this is what i have now. That should work....

```
#!/bin/bash
# For use with .desktop files and MIME handlers so that the Ubuntu Policy
# can be followed: programs cannot be executed when they lack the execute bit.
# https://wiki.ubuntu.com/SecurityTeam/Policies#Execute-Permission%20Bit%20Required
exe="$1"
shift || true
if [ -n "$exe" ] && [ ! -x "$exe" ] && \
   [ "${exe:0:5}" != "/usr/" ] && [ "${exe:0:5}" != "/opt/" ]
then
    if [ -n "$DISPLAY" ] && [ -x /usr/bin/zenity ]; then
        if /usr/bin/zenity --question --title "Blocked: $*" --text "The file '$exe$
                exec "$@" "$exe"
        fi
        
    else
        echo "$*: '$exe' is not executable.  Aborting." >&2
    fi
    exit 1
fi
exec "$@" "$exe" 
```

---

### Post by dave01945 on 2011-09-29
> **yanom said:**
> Ok, this is what i have now. That should work....

```
#!/bin/bash
# For use with .desktop files and MIME handlers so that the Ubuntu Policy
# can be followed: programs cannot be executed when they lack the execute bit.
# https://wiki.ubuntu.com/SecurityTeam/Policies#Execute-Permission%20Bit%20Required
exe="$1"
shift || true
if [ -n "$exe" ] && [ ! -x "$exe" ] && \
   [ "${exe:0:5}" != "/usr/" ] && [ "${exe:0:5}" != "/opt/" ]
then[
    if [ -n "$DISPLAY" ] && [ -x /usr/bin/zenity ]; then
        if /usr/bin/zenity --question --title "Blocked: $*" --text "The file '$exe$**; then**
                exec "$@" "$exe"
        fi
        
    else
        echo "$*: '$exe' is not executable.  Aborting." >&2
    fi
    exit 1
fi
exec "$@" "$exe" 
```


yeah thats looks about it just one more then in the zenity if statement i've added it in bold for you to see unless that line is incomplete it looks shorter than it was previous

---

### Post by emiller12345 on 2011-09-29
You might consider removing the ...
```
exec "$@" "$exe"
```...
from the end of your script.  If I'm seeing this correctly, that line will execute the command regardless of the result of your zenity command.  Take a look at it.

---


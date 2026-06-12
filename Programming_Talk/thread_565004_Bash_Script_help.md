---
title: "Bash Script help"
date: 2007-10-01
forum: Programming Talk
---

### Post by munwin on 2007-10-01
I am still coming to grips with Bash, so excuse me if this is obvious...
Can anyone tell me why I get False for the script below ?

```
#!/bin/bash

UNKNOWN="[U,u]nknown{*}"
TESTING="Unknown something"

if [ "$TESTING" = "$UNKNOWN" ]
then
 echo "True"
else
 echo "False"
fi
```

---

### Post by Cappy on 2007-10-01
```

#!/bin/bash

UNKNOWN='[Uu]nknown'
TESTING="Unknown something"

if [[ $TESTING =~ $UNKNOWN ]]; then
	echo "True"
else
	echo "False"
fi

```

*or* if you want to do it in #!/bin/sh it would look like this: (actually you can do this in bash too but it is slower)
```

#!/bin/sh

UNKNOWN='[Uu]nknown'
TESTING="Unknown something"

if [ "`echo "$TESTING" | grep "$UNKNOWN"`" ]; then
	echo "True"
else
	echo "False"
fi

```

Edit: A * on the end isn't needed because the regex will match the string "Unknown" out of the string "Unknown something".

---

### Post by munwin on 2007-10-01
Great, got it working. Thank you very much.
One question - why do I need the single quote character when defining UNKNOWN ? ie - why UNKNOWN='[U,u]known' and not UNKNOWN="[U,u]known" - the single quotes definitely make a difference...

---

### Post by Cappy on 2007-10-01
I recommend this page which explains:
[http://www.panix.com/~elflord/unix/bash-tute.html](http://www.panix.com/~elflord/unix/bash-tute.html)

In short, you should use ' ' for anything where you don't have a variable in it. If you need to put in a variable it is possible to do something like ```
'regexhere'"$variablehere"'anotherregexhere'
``` and it will protect the regex from being expanded by the shell while expanding the variable.

Also notice that your regex [U,u]nknown would match
Unknown
unknown
,nknown
because characters in [] are not separated by commas

---

### Post by munwin on 2007-10-01
Thank you very much.
No wonder Ubuntu is so popular. The community is just GREAT !!!

---


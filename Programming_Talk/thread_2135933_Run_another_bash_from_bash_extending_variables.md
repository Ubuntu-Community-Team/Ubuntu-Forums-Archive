---
title: "Run another bash from bash extending variables"
date: 2013-04-15
forum: Programming Talk
---

### Post by pedrommone on 2013-04-15
My scripts are like those:

```

#!/bin/bash

SERVER_ID=1
SERVER_NAME="Test One"

```

```

#!/bin/bash

echo "$SERVER_ID"

```

I want to include the second script inside the first and extend the first script variables. But I dont know how, thanks in advance!

---

### Post by prodigy_ on 2013-04-15
[http://ubuntuforums.org/showthread.php?t=2124843](http://ubuntuforums.org/showthread.php?t=2124843)

---

### Post by tgalati4 on 2013-04-15
```
echo $SERVER_ID
```

Returns:
1

What is the problem?  Don't use quotes around variable names.

The variables will remain defined as long as the script continues to run.

tgalati4@Mint14-Extensa ~ $ echo "Server Number " $SERVER_ID "Server Name " $SERVER_NAME
Server Number  1 Server Name  Test One

I don't see any problems with 

```
#!/bin/bash

SERVER_ID=1
SERVER_NAME="Test One"

echo "Server Number:  " $SERVER_ID "Server Name:  " $SERVER_NAME

exit 0

```

---

### Post by pedrommone on 2013-04-16
> **prodigy_ said:**
> [http://ubuntuforums.org/showthread.php?t=2124843](http://ubuntuforums.org/showthread.php?t=2124843)

Thanks mate, as soon as get home gonna check that!

> **tgalati4 said:**
> ```
echo $SERVER_ID
```

Returns:
1

What is the problem? Don't use quotes around variable names.

The variables will remain defined as long as the script continues to run.

tgalati4@Mint14-Extensa ~ $ echo "Server Number " $SERVER_ID "Server Name " $SERVER_NAME
Server Number 1 Server Name Test One

I don't see any problems with 

```
#!/bin/bash

SERVER_ID=1
SERVER_NAME="Test One"

echo "Server Number:  " $SERVER_ID "Server Name:  " $SERVER_NAME

exit 0

```

I want run the second bash and the second has to read the variables from second.

---

### Post by steeldriver on 2013-04-16
You can *export *the variables from one shell (script) to the other e.g.

```
$ cat script1
#!/bin/bash

[COLOR=#0000ff]export [/COLOR]SERVER_ID=1
[COLOR=#0000cd]export [/COLOR]SERVER_NAME="Test One"

./script2

exit 0
$
$ cat script2
#!/bin/bash

echo "Server Number:  $SERVER_ID"  "Server Name:  $SERVER_NAME"

exit 0

$
$ $ ./script1
Server Number:  1 Server Name:  Test One
```

or you can set the environment explicitly on the line that calls your 2nd script e.g.

```
$ cat script1
#!/bin/bash

SERVER_ID=1
SERVER_NAME="Test One"

[COLOR=#0000ff]SERVER_ID="$SERVER_ID" SERVER_NAME="$SERVER_NAME"[/COLOR] ./script2

exit 0

$
$ ./script1
Server Number:  1 Server Name:  Test One
```

If you're not calling script2 from script1, then you can put all the exports in the first file and *source *it from the second e.g.

```
$ cat script1
#!/bin/bash

export SERVER_ID=1
export SERVER_NAME="Test One"

$
$ cat script2
#!/bin/bash

[COLOR=#0000cd]source ./script1[/COLOR]

echo "Server Number:  $SERVER_ID"  "Server Name:  $SERVER_NAME"

exit 0
$
$ ./script2
Server Number:  1 Server Name:  Test One
$
```

---

### Post by pedrommone on 2013-04-16
Thanks! It is not working for now, I got another idea, if someone can help-me, here's the thread: [http://ubuntuforums.org/showthread.php?t=2135204](http://ubuntuforums.org/showthread.php?t=2135204)

---


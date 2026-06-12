---
title: "[bash cgi] trying to output parts of a file through a loop"
date: 2010-10-15
forum: Programming Talk
---

### Post by tynin on 2010-10-15
I'm attempting to step through a file, and output each line. I'm actually doing much more than that and it works just fine on the command line. But trying to convert it to work in a bash cgi type fashion is giving me problems. I've stripped down this example to make it simple because once I solve this problem I'm sure I'll be fine. Here is my code:

file: index.sh
```

#!/bin/bash

echo "Content-type: text/html"
echo ""

cat <<EOF
<html>
  <head><title>Test</title></head>
<body>
Walk through servers
<br><br>
EOF

walk=1

for x in `cat ./servers`; do
  serverIP=`more +$walk ./servers | head -n 1`

  echo $serverIP 
  echo $walk

  walk=$(( walk+1 ));
done

cat <<EOF
</body>
</html>
EOF

```

file: servers
```

255.255.255.1
255.255.255.2
255.255.255.3

```

When I run it from the command line, it correctly steps through the IP's and displays them:
----
/var/www/cgi-bin# ./index.sh 
Content-type: text/html

<html>
  <head><title>Test</title></head>
<body>
Walk through servers
<br><br>
255.255.255.1
1
255.255.255.2
2
255.255.255.3
3
</body>
</html>
----

When I call it from a browser I get back the following:
-----
Walk through servers 

:::::::::::::: 1 :::::::::::::: 2 :::::::::::::: 3
-----

I'm running bash 4.1.5, and apache 2.2.16. Suggestions? Thanks!

---

### Post by spjackson on 2010-10-15
> ```

  serverIP=`more +$walk ./servers | head -n 1`

```Why are you using "more" in a cgi script? I suspect that's your problem.

---

### Post by DaithiF on 2010-10-15
slow evening here so I had a look through the more source-code.  Theres some logic there which outputs '::::::::::' rather than the contents of a file when a certain condition is met ... i think when its not being run from an interactive terminal.

but as spjackson says, more isn't the tool you want.  Do something like:
```
while read ip
do
   echo $ip
   echo $walk
   walk=$(( walk + 1))
done < ./servers
```

---


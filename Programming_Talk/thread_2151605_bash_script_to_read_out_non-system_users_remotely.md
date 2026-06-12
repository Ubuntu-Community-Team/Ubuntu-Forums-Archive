---
title: "bash script to read out non-system users remotely"
date: 2013-06-05
forum: Programming Talk
---

### Post by rockprincess on 2013-06-05
Hi all,

I would need your help, since I'm not really much of a bash-scripting expert :(
I need to create a script, that writes the output of non-system users of remote machines into a separate file….since I have many many servers where I need to do that, a script would come in quite handy.
I’ve created a txt file named hosts.txt with all the hostnames.

I’ve also created a little bit of code, it used to work until I put in the for loop at the very end….

Could some of you maybe point me into the right direction as to what I’m doing wrong? As said before I’m no expert and the bits I’ve put together were bits I’ve collected from various sites and manpages……

I’m thankful for any kind of advice,

Many thanks in advance,
cheers
theresa


```
#!/bin/bash
# -----------------------------------------------------------------------------------
_l="/etc/login.defs"
_p="/etc/passwd"
 
## get mini UID limit ##
l=$(grep "^UID_MIN" $_l)
 
## get max UID limit ##
l1=$(grep "^UID_MAX" $_l)
 
## use awk to print if UID >= $MIN and UID <= $MAX and shell is not /sbin/nologin   ##
echo "----------[ Normal User Accounts ]---------------"
command=awk -F':' -v "min=${l##UID_MIN}" -v "max=${l1##UID_MAX}" '{ if ( $3 >= min && $3 <= max  && $7 != "/sbin/nologin" ) print $0 }' "$_p" 2>&1 | tee -a users.txt 

for host in $(cat hosts.txt); do ssh "$host" "$command" >"output.$host"; done
```

---

### Post by rockprincess on 2013-06-06
122 views and no one has any idea? :(

---

### Post by steeldriver on 2013-06-06
Are you sure it was working before you added the loop?

1. your command= line looks like it will break on spaces - that needs to be quoted, I think. In order to avoid escaping quotes-within-quotes you can try

```

command="awk -F\: -v a=${l##UID_MIN} -v b=${l1##UID_MAX} '{ if ( $3 >= a && $3 <= b && $7 != /sbin/nologin ) print $0 }' $_p 2>&1 | tee -a users.txt"

```

2. it looks like you need additional measures to pass the $x awk variables unmolested through ssh - for example

```

$ _p=/etc/passwd
$
$ awk -F\: -v a=1000 -v b=5999 '{ if ( $3 >= a && $3 <= b && $7 != /sbin/nologin ) print $0 }' $_p 2>&1 | tee -a users.txt
steeldriver:x:1002:1003:steeldriver:/home/steeldriver:/bin/bash

```

works, but 
```

$ ssh 192.168.1.102 "awk -F\: -v a=1000 -v b=5999 '{ if ( $3 >= a && $3 <= b && $7 != /sbin/nologin ) print $0; }' $_p 2>&1 | tee -a users.txt"
awk: line 1: syntax error at or near >=


```
doesn't; however if I escape the $ characters
```

$ ssh 192.168.1.102 "awk -F\: -v a=1000 -v b=5999 '{ if ( [COLOR=#0000ff]**\**[/COLOR]$3 >= a && [COLOR=#0000ff]**\**[/COLOR]$3 <= b && [COLOR=#0000ff]**\**[/COLOR]$7 != /sbin/nologin ) print [COLOR=#0000ff]**\**[/COLOR]$0; }' $_p 2>&1 | tee -a users.txt"
steeldriver:x:1002:1002:,,,:/home/steeldriver:/bin/bash

```

BTW you may want to have a play with the 'getent' command e.g.

```

$ getent passwd {1000..5999}
steeldriver:x:1002:1003:steeldriver:/home/steeldriver:/bin/bash

```

Also I'd personally use a 'while' loop and avoid $(cat xxx) i.e.

```
while read -r host; do ssh "$host" "$command"; done < hosts.txt
```

Hope this helps

---


---
title: "Link to a script using 'dirname'"
date: 2013-11-15
forum: New to Ubuntu
---

### Post by petrux3 on 2013-11-15
I have a script placed in /opt/MyDir/myscript.sh which calls java, setting its directory as the classpath:


```
scriptdir=`dirname $0`
java -mx3g -cp "$scriptdir/*" MyApp.jar

```

I have created a link to this script in /usr/local/bin/myscript but if I run it, the classpath is messed up. 
Could anyone suggest me a workaround? 
How to deal in such situations? 
Thanks.

---

### Post by steeldriver on 2013-11-15
The $0 builtin will expand to *the name by which the script was invoked* - so when you're invoking it via the symlink, it will expand to /usr/local/bin/myscript.sh and dirname will evaluate as /usr/local/bin, I think

I'm not sure if it's good practice, but you could use readlink to find the canonical name of the file that's being linked to e.g.

```
scriptdir="`dirname $(readlink -f "$0")`"
```

or more consistently

```
scriptdir="$(dirname $(readlink -f "$0"))"
```

or perhaps

```

realname="$(readlink -f "$0")"
scriptdir="${realname%/*}"

```

---


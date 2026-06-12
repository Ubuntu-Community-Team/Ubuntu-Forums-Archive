---
title: "[bash] Allowing for only absolute paths in script"
date: 2008-06-13
forum: Programming Talk
---

### Post by altonbr on 2008-06-13
I just ran into a problem where my script can only accept absolute paths. Since I don't have a blog, I thought I'd post my solution here:

```
if [ "`echo $1 | cut -d '/' -f 1`" != "" ]; then
	echo 'Absolute paths only!
	exit 1
fi
```

Examples:
> $ echo './' | cut -d '/' -f 1 # local directory
.
$ echo '../' | cut -d '/' -f 1 # local directory, back one
..
$ echo 'var/' | cut -d '/' -f 1 # local directory
var
$ echo '/var' | cut -d '/' -f 1 # absolute directory (this is the only type of path that is accepted in the script above)


---

### Post by geirha on 2008-06-13
You can do this with pure bash too.
```
[ "${1:0:1}" != "/" ] && echo "not an absolute path"
```

---

### Post by altonbr on 2008-06-13
> **geirha said:**
> You can do this with pure bash too.
```
[ "${1:0:1}" != "/" ] && echo "not an absolute path"
```

What's "${1:0:1}" specifically do? Looks for variable $1, start at 0 and end after 1 character?

---

### Post by Phenax on 2008-06-13
> **altonbr said:**
> What's "${1:0:1}" specifically do? Looks for variable $1, start at 0 and end after 1 character?

Yep, pretty much makes sure the first character of the string is "/"

---

### Post by geirha on 2008-06-13
> **altonbr said:**
> What's "${1:0:1}" specifically do? Looks for variable $1, start at 0 and end after 1 character?

Exactly that.
[http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_10_03.html#sect_10_03_03_02](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_10_03.html#sect_10_03_03_02)

---

### Post by ghostdog74 on 2008-06-13
use case. 
```

# path="/var"
# case $path in  /* ) echo "yes";; esac
yes

```

---


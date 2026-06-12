---
title: "How to rm a specific type of file.h"
date: 2010-04-27
forum: Programming Talk
---

### Post by youralibaba on 2010-04-27
How to delete only ordinary files in a directory ? e.g file1 is a pipe and file2 is a text file. The linux system should delete only text file ? There is no flag in rm to do that. How to do that ?

---

### Post by dv3500ea on 2010-04-27
```

perl -e '
foreach (glob("*")) { 
	if (-f $_) {
		system("rm $_");
	}
}
'

```

---

### Post by dv3500ea on 2010-04-27
That will work in bash as long as perl is installed (it is by default on most Linux).

A pure bash version is:
```

for i in *
    do echo $i
    if [ -f $i ]; then
        rm $i
    fi
done

```

But I am no expert on bash.

---

### Post by gmargo on 2010-04-27
In a single directory, without recursion:
```

find directoryname -maxdepth 1 -type f -exec rm -f {} \; -print

```

---

### Post by geirha on 2010-04-27
> **dv3500ea said:**
> That will work in bash as long as perl is installed (it is by default on most Linux).

A pure bash version is:
```

for i in *
    do echo $1
    if [ -f $1 ]; then
        rm $1
    fi
done

```

But I am no expert on bash.

$1 != "$i"

```
for file in *; do if [[ -f $file ]]; then rm -iv "$file"; fi done
```

---


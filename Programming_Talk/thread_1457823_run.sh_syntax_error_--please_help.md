---
title: "run.sh syntax error --please help"
date: 2010-04-19
forum: Programming Talk
---

### Post by hoboy on 2010-04-19
I have a sh file that contains the following

DIR=$(dirname $0)

function log() {
    echo 1>&2 `date +"%Y-%m-%d %H:%M:%S"` $0 $*
}
When I run the script I get syntax error on 

at   
function log() {
    echo 1>&2 `date +"%Y-%m-%d %H:%M:%S"` $0 $*
}
saying "(" expected

---

### Post by Bachstelze on 2010-04-19
You want this:

```
DIR=$(dirname $0)

log() {
echo 1>&2 `date +"%Y-%m-%d %H:%M:%S"` $0 $*
}
```

No "function" keyword to introduce functions in Bourne-like shell scripts.

---

### Post by hoboy on 2010-04-19
> **Bachstelze said:**
> You want this:

```
DIR=$(dirname $0)

log() {
echo 1>&2 `date +"%Y-%m-%d %H:%M:%S"` $0 $*
}
```

No "function" keyword to introduce functions in Bourne-like shell scripts.

tks

---


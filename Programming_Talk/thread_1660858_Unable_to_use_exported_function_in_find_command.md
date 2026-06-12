---
title: "Unable to use exported function in find command"
date: 2011-01-05
forum: Programming Talk
---

### Post by jayach on 2011-01-05
I've been working on this way too long, and any help would be greatly appreciated.  I'm trying to execute a bash function from within the find command:

test.sh:
```

#!/bin/bash
set -x

function testFunc {
  echo "$1"
}
export -f testFunc

# what I expected to work:
find /tmp -iname md5sum -exec testFunc '{}' \;

# another test for the heck of it:
find /tmp -iname md5sum -exec $(testFunc) '{}' \;

# function content works here:
find /tmp -iname md5sum -exec echo '{}' \;

# calling the function works:
testFunc 'Hello'

```

results:
```

/usr/local/bin$ sudo ./test.sh
+ export -f testFunc
+ find /tmp -iname md5sum -exec testFunc '{}' ';'
find: `testFunc': No such file or directory
++ testFunc
++ echo ''
+ find /tmp -iname md5sum -exec '{}' ';'
find: `/tmp/MD5SUM': Permission denied
+ find /tmp -iname md5sum -exec echo '{}' ';'
/tmp/MD5SUM
+ testFunc Hello
+ echo Hello
Hello

```

Thanks-

---

### Post by Trumpen on 2011-01-06
Try calling manually bash (if bash is the shell you are using for function declaration):

```
find /tmp -iname md5sum -exec bash -c 'testFunc $1' _ '{}'  \;
```

Alternatively, you could insert that declaration just inside the called shell:

```
find /tmp -iname md5sum -exec bash -c 'function testFunc { echo "$1"; }; testFunc $1' _ '{}'  \;
```

---

### Post by jayach on 2011-01-06
Awesome, thanks so much Trumpen!  That did the trick and gets me moving forward once again.

I had a question about your solution.  Why did you add the $1 and the underscore?  When I remove it, I get the same result, like so:

```
find /tmp -iname md5sum -exec bash -c 'testFunc {}'  \;
```

I found an explanation of the underscore here, but I still don't quite get it in the context used:
[http://www.faqs.org/docs/bashman/bashref_25.html#SEC25]("http://www.faqs.org/docs/bashman/bashref_25.html#SEC25")

---


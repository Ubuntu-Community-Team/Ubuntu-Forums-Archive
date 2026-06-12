---
title: "Recurseive sed"
date: 2007-09-17
forum: Programming Talk
---

### Post by v8YKxgHe on 2007-09-17
Hey,

I'm wanting to use sed to replace some text in my PHP scripts (changing from Router:: to $this->_router) however you can't recurse with sed.

I had a bash script a while ago to do this, but lost it and I can't remember at all how I did it. Another thing is I need it to *not* do the sed replacement on files that are hidden or in a hidden directory.

Regards,

---

### Post by ghostdog74 on 2007-09-17
show a sample of your PHP script you are going to process, and the output you are expecting to see.

---

### Post by Ramses de Norre on 2007-09-17
Something like this maybe:
```
find . -iname '*php' -type f -exec sed -i -e '*sed_command*' '{}';
```
Test it on a test directory first please, I can't test it myself here FTM. I'm not sure how to exclude the hidden files neither, but maybe someone can extend the command to do so.

Maybe better (untested, bugs and typo's are probably there):
```
#!/bin/bash

function doSed()
{
    if [ $(($1:0:1)) != "." ]; then
        sed -i -e '*sed_command*' $1
    fi
}

find . -iname '*php' -type f -exec doSed '{}';

```

---

### Post by ghostdog74 on 2007-09-17
> **Ramses de Norre said:**
> Something like this maybe:
```
find . -iname '*php' -type f -exec sed -i -e '*sed_command*' '{}';
```


it may be simplified to 
```

sed -i -e 'sed_command' *.php

```

---

### Post by Ramses de Norre on 2007-09-17
> **ghostdog74 said:**
> it may be simplified to 
```

sed -i -e 'sed_command' *.php

```

Your command will only parse php files in the current directory and not in subdirectories, mine will go recursive through all subdirectories.

---

### Post by ghostdog74 on 2007-09-17
> **Ramses de Norre said:**
> Your command will only parse php files in the current directory and not in subdirectories, mine will go recursive through all subdirectories.

if that's what the OP meant by recursive sed ie going into subdirectories, then yes, the find command should be sufficient. however i would suggest to use xargs instead of -exec.

---


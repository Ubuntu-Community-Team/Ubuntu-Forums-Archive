---
title: "Using filepath in sed substitutions"
date: 2009-02-18
forum: Programming Talk
---

### Post by Johnny Golden on 2009-02-18
Hi everyone,

I am (a scripting newb) trying to write a bash script to change the following string in /folder/file.xml
```
path="folder/"
```
to
```
path="http://server2.com/folder/"
```

So far I have this working fine:
find /folder -name file.xml -print | xargs sed -i 's|path="folder/"|path="http://server2.com/folder/"|g'

But this won't mirror any nested paths on server2.com.  For example, I would also like the script to change the same string in /folder/**subfolder1**/file.xml to:
```
path="http://server2.com/folder/**subfolder1**/"
```

Is this possible using find piped to sed?  Or am I on the wrong track?

---

### Post by geirha on 2009-02-18
Try with ```
s|path="\([^"]*\)"|path="http://server2.com/\1"|g
```

\1 in the replacement string corresponds to the match inside the first (in this case the only) parenthesis \( \)

---

### Post by Johnny Golden on 2009-02-19
Thanks geihra,

The problem is that the path variable in /folder/subfolder1/file.xml is  relative, i.e. it still reads
```
path="folder/"
```

I am trying to insert part of the filepath of file.xml into the URL.

---

### Post by geirha on 2009-02-19
I see. You can try making a script:
```

#!/bin/bash
for file in "$@"; do
    # file == "/folder/subfolder1/file.xml"
    path="${file%/*}/"    # removes everything from the last /
    # path == "/folder/subfolder1/"
    url="http://server2.com$path"
    # url == http://server2.com/folder/subfolder1/
    sed -i "s|path=\"folder/\"|path=\"$url\"|g" "$file"
done

```

Then pipe find to that script
```
find -name file.xml -print0 | xargs -0 bash thescript.bash
```

I haven't tested it, but I think it should work.

---


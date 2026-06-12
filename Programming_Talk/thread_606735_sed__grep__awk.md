---
title: "sed / grep / awk"
date: 2007-11-08
forum: Programming Talk
---

### Post by pylon42 on 2007-11-08
Hello,

I'm extremely new to linux/bash/programming.

I'm currently in the middle of trying to figure out grep/sed/awk and I'm still pretty foggy about when to use what where. There seems to be a lot of overlap in the functionality.

Here's the item that made me start looking into this:

I have a var: $target=dir2
I have a string: "/dir1/dir2/dir3/dir4/file" 
(The string will always be a path to a file)

I want to scan the string for the var, and if it exists, return the dir in the string that follows the var (in this example, it would be "dir3")

I then want to take the output, scan the string again and return all parts of the string that follow the output (in this example, it would be "/dir4/file")

If someone has some free time and could show me how grep, awk, or sed could be best applied in this situation, I would really appreciate it.

---

### Post by geirha on 2007-11-08
I never learned awk, but you can do that with grep and cut like this at least:
```
#!/bin/bash

string="/dir1/dir2/dir3/dir4/file" 
target="dir2"
target2=$( echo $string | grep -o "$target/[^/]*" | cut -d/ -f2 )
rest=$( echo $string | grep -o "$target2.*" | cut -d/ -f2- )
echo -e "string: $string\ntarget: $target\ntarget2: $target2\nrest: $rest"

```

---

### Post by pylon42 on 2007-11-08
wow... that looks complex, I have so much to learn.

Works like a charm though - thank you kindly!

---


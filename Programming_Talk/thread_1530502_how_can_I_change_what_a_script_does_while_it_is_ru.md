---
title: "how can I change what a script does while it is running, by pressing a key"
date: 2010-07-13
forum: Programming Talk
---

### Post by leahk on 2010-07-13
I am trying to write code which will let the user press a key like 'b' and run an operation, while a script is still running, and have the script continue afterwards. How can I do this??? I am using Linux. working in python

---

### Post by geirha on 2010-07-13
```
#!/bin/bash

while read -p '> ' -r -n1; do
  echo
  case $REPLY in
    b)
      echo "b stuff..."
    ;;
    l)
      ls
    ;;
    q)
      echo "Bye bye"
      break
    ;;
    *)
      echo "Huh?"
    ;;
  esac
done

```
Read this to learn bash scripting: [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

---

### Post by leahk on 2010-07-13
can you please explain the code and how it works. im working in python.

---

### Post by geirha on 2010-07-13
Well, it waits for a char from stdin and runs a set of commands based on what char it was...

Now that you specified you really meant a python script though, I don't see why that matters; a python script to do something similar will look completely different.

---


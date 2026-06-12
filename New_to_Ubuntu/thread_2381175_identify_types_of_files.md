---
title: "identify types of files"
date: 2017-12-27
forum: New to Ubuntu
---

### Post by sed_faster on 2017-12-27
Hello,

I use this script to see how many and which type files I have on directory:
```

find -type f -exec file -ib {} \; | awk '{count[$1]++}END{for(j in count) print j,"("count[j]" occurences)"}' | sort>>$log

```
The result is some like this:
> 
----------------- Initial Script ----------------------
Thu Dec 28 00:48:20 WET 2017
-------------------------------------------------------
application/octet-stream; (1 occurences)
inode/x-empty; (3 occurences)
regular (1 occurences)
text/plain; (22 occurences)
text/x-shellscript; (8 occurences)
-------------------------------------------------------

is there any chance see which extension corresponds to each type? For example:

> 
----------------- Initial Script ----------------------
Thu Dec 28 00:48:20 WET 2017
-------------------------------------------------------
(???) - application/octet-stream; (1 occurences)
(???) - inode/x-empty; (3 occurences)
(???) - regular (1 occurences)
(txt) -text/plain; (22 occurences)
(sh) -text/x-shellscript; (8 occurences)
-------------------------------------------------------

thanks

---

### Post by vasa1 on 2017-12-27
Two links you may like to read completely:
[https://askubuntu.com/questions/803434/do-file-extensions-have-any-purpose-for-the-operating-system](https://askubuntu.com/questions/803434/do-file-extensions-have-any-purpose-for-the-operating-system)
[https://unix.stackexchange.com/questions/266999/why-does-linux-use-file-extension-to-decide-the-default-program-for-opening-a-fi](https://unix.stackexchange.com/questions/266999/why-does-linux-use-file-extension-to-decide-the-default-program-for-opening-a-fi)

---


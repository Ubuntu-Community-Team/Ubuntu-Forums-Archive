---
title: "sh/perl/python help/request"
date: 2007-07-27
forum: Programming Talk
---

### Post by vexorian on 2007-07-27
Hello, I need some help with an script I'd like to make. I want something that would take an argument, the argument is a file path, but then it should convert it to a MSDOS path for wine...

For example

/home/name/alg tur/k.w3x

becomes:

"Z:\home\name\alg tur\k.w3x"

And I then have to concatenate that (including the quotes) to a call to a WINE program.

Please help before the mad side of my brain forces me to compile a C++ program for this...

---

### Post by Mr. C. on 2007-07-28
A simple sed command might work for you:

```
#!/bin/bash

echo "$1"  | sed -e 's-^-Z:-' -e 's-/-\\-g'     
```   

MrC

---

### Post by jyba on 2007-07-28
Or use substring replacement...
```
#!/bin/bash

echo "\"Z:${1////\\}\""
```

---

### Post by slavik on 2007-07-28
might as well do in perl:

```

#!/usr/bin/perl
print "Z:" . join '\\', split /\//, @ARGV[0] . "\n";

```

---

### Post by vexorian on 2007-07-28
thanks

---


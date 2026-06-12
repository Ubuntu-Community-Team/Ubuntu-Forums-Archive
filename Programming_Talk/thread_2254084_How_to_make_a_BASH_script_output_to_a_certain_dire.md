---
title: "How to make a BASH script output to a certain directory"
date: 2014-11-25
forum: Programming Talk
---

### Post by cal1j on 2014-11-25
Hi guys,

I'm still wrapping my head around BASH scripts and have a simple question. I recently wrote a simple script that populates my directory that I write diary entries into with an entire months named files, ot the format xx-xx-2014.odt. Cool little script. So lets assume I save the script somewhere and write a simple alias to run it. It always seems to populate the home directory. What am I doing wrong? This is despite the fact that the script that the alias calls is NOT in /home/, but instead is in the directory that I hope to populate!?! What am I missing?

---

### Post by SeijiSensei on 2014-11-25
If the directory is fixed, you can just cd to it in the script:

```

#!/bin/bash

cd /path/to/the/directory

[stuff]

```

If you want to be able to specify a directory on the command line you can use
```

#!/bin/bash

DIR=/path/to/the/directory

[ "$1" != "" ] && DIR=$1

cd $DIR

[stuff]

```
If you call the script with "script /path/to/some/directory" the directory you specify will be used instead of the default.

---

### Post by cal1j on 2014-11-25
Awesome. This is what I needed. You rock SeijiSensei!!!

---


---
title: "How do I get a list of directories using find?"
date: 2009-05-08
forum: Programming Talk
---

### Post by dwhitney67 on 2009-05-08
I am using 'find' to obtain the list of directories that contain source code (namely, .cpp files).  I have a few directories with .cpp files in it, and in each of these directories, anywhere from 5 to 10 files.

'find' reports all of the directories I ask it to search for using this statement:
```

find . -name '*.cpp' -exec dirname {} \;

```
How can I tell 'find' to stop searching a particular path (directory) after it has found one .cpp file?  I am attempting to avoid having the 'find' statement above report duplicates.  My goal is merely to obtain a list of directories that have source files; not get a list of the files, and then invoke 'dirname' on them.

If you need to experiment, as I often find I have to do, here a little script to setup a test area.
```

#!/bin/bash

mkdir -p FindTest/{A,B,C}

touch FindTest/{A,B,C}/foo{1,2,3}.cpp

```

When running the 'find' command as shown above, my results were:
```

cd FindTest
find . -name '*.cpp' -exec dirname {} \;
./B
./B
./B
./A
./A
./A
./C
./C
./C

```
I desire something like the following (where of course, the order is not relevant):
```

./B
./A
./C

```

---

### Post by ghostdog74 on 2009-05-08
if you desire that output, you can pass your find results to uniq

---

### Post by dwhitney67 on 2009-05-08
Thanks ghostdog74!  That's what I needed.

---


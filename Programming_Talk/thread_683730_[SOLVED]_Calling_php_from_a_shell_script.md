---
title: "[SOLVED] Calling php from a shell script"
date: 2008-01-31
forum: Programming Talk
---

### Post by nimbostratus on 2008-01-31
I'm trying to write a shell script that calls php to run a .php file. Something like this:

#!/bin/sh
php mybuilder.php

It actually does some other useful stuff but this is what it boils down to. builder.php is in the same directory.

So it works fine to type
./mybuild
when in that directory. But I'd like to be able to call it from anywhere (ideally from a softlink in /usr/local/bin, so just type 'mybuild'). However when I do that, the working directory is wrong so php can't find mybuilder.php.

Is it possible to solve this without resorting to using a full path to mybuilder.php ? Especially since it's in the same directory as the script...

Thanks

---

### Post by stroyan on 2008-01-31
If you change the script from using #!/bin/sh to #!/bin/bash then you can get the directory containing the script file (and the mybuilder.php file) using
```
script_dir="$(dirname "$(readlink -f ${BASH_SOURCE[0]})")"
```

The BASH_SOURCE variable is an array of the paths to the source file for each function in the bash function stack.
The "readlink -f" command finds the canonical path to a file, expanding symbolic links.
The "dirname" command removes the file name from the path to get the directory.

---

### Post by nimbostratus on 2008-01-31
Good stuff - that's just what I needed.
Thanks very much :)

---

### Post by nimbostratus on 2008-02-09
If anyone else has come here with a similar problem, please take a look at the post [Shell scripts and the working directory]("http://greythinking.blogspot.com/2008/02/shell-scripts-and-working-directory.html") on my blog at [greythinking.blogspot.com]("http://greythinking.blogspot.com/"). I've explained the problem and the solution more fully there.

---


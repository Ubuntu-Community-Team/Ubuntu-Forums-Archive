---
title: "&quot;sh&quot; and &quot;./&quot;"
date: 2011-01-05
forum: Programming Talk
---

### Post by rahulnair on 2011-01-05
hello again everyone..
actually this morning i was trying to create a script for moving all the unnecessary files on my desktop to a folder called Temp(on my desktop)..

first i tried to run the command on the terminal and it worked fine..the command i used was...
```
mv Desktop/{*.exe,*.pdf} Desktop/Temp
```(just giving an example of exes and pdfs...and my current directory was /home/username/)

and it WORKED FINE....

then i wrote a small script for it as follows..
```
#!/bin/bash
mv Desktop/{*.exe,*.pdf} Desktop/Temp
```BUT strangely it gave me an error..saying..

"mv: cannot stat `Desktop/{*.exe,*.pdf}': No such file or directory"

i tried many times to get it right but in vain..wondering how can the same command which worked in the terminal,not work while included in a script..

finally before shutting down my PC...i tried executing the script using "./" instead of the "sh" command that i normally used...and voila!!... it worked!!!..

what is the difference between the two methods of executing scripts????

---

### Post by MadCow108 on 2011-01-05
sh executes the posix shell (dash on ubuntu) which has less features than bash
{} replacements are not available in sh

*bash yourscript* should work too

---

### Post by Vox754 on 2011-01-05
> **MadCow108 said:**
> sh executes the posix shell (dash on ubuntu) which has less features than bash
{} replacements are not available in sh

*bash yourscript* should work too

This is the same problem the OP was having with his previous thread: [bash problem.](http://ubuntuforums.org/showthread.php?t=1658965)

If you don't have a shebang, you need to call the interpreter explicitly.

```

# This uses the POSIX shell, which in Ubuntu is dash
sh   my_script.sh
dash my_script.sh

# This uses the enhanced bash
bash my_script.sh

```

If you do have a shebang, you don't need to call the interpreter. Just run the script and it will use the interpreter listed in the shebang.
```

# Give the full path
/full/path/my_script.sh

# Give the relative path; in this case, the current working directory
./my_script.sh

```

If you have a shebang that uses "bash", it is dumb to run "sh", because you are overriding the shebang, and actually using a shell with less features. This is the same as running a Python script through Perl, it doesn't work because they are different languages.
```

#!/bin/bash

sh my_script.sh  # WRONG!


#!/usr/bin/python

perl my_script.py # WRONG!

```

---

### Post by rahulnair on 2011-01-05
yeah....you are right..
now i understand.actually the other post(bash problem) also was concerning the same problem..
and thanks for that piece of information bout bash..actually i am new to linux..:p never knew the difference!! thanks again...marking solved..

---


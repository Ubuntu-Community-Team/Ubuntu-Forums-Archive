---
title: "Shell Script"
date: 2009-02-10
forum: Programming Talk
---

### Post by Simplemind169 on 2009-02-10
I am just learning some Ubuntu Shell Scripts and i noticed that they all have to start with `#!/bin/sh`. everywhere that i look i can seem to figure out why this is necessary. I understand that the /bin/sh is a shell but according to the rules of the # symbol the script shouldn't look at that line at all;but without that line the scripts don't work. if anyone has an opinion or an answer i would love to solve this question.

---

### Post by geirha on 2009-02-10
It's the [shebang](http://en.wikipedia.org/wiki/Shebang_(Unix))

If you run the script with ```
bash script-name
``` it will be run as bash, no matter what, but if you make the script executable, and run it with: 
```
chmod +x script-name
./script-name
```
It needs the shebang to know which interpreter to use. How else should it determine if the content is a bash script, python script or perl script or whatever?

---

### Post by lloyd_b on 2009-02-10
> **Simplemind169 said:**
> I am just learning some Ubuntu Shell Scripts and i noticed that they all have to start with `#!/bin/sh`. everywhere that i look i can seem to figure out why this is necessary. I understand that the /bin/sh is a shell but according to the rules of the # symbol the script shouldn't look at that line at all;but without that line the scripts don't work. if anyone has an opinion or an answer i would love to solve this question.

The "#!" evaluates to a [magic number]("http://en.wikipedia.org/wiki/Magic_number_(programming)"), which tells the system how to execute the file.  In the case of "#!", this tells the executable loader routine in the system that it needs to invoke a shell, and that the path to the shell to use immediately follows the "#!".

The actual shell ("bash", "sh", etc) *does* completely ignore this line (because it begins with a "#").

Note that you do *not* have to have the "#!" on the first line of the file.  Most scripts will work just fine without it.  Where it's truly required is when the script uses constructs that only work for a particular shell (some "bash" syntax won't work with "sh" and vice versa), to ensure that the proper shell is invoked to run the script.

BTW: I'd recommend using "#!/bin/bash" instead of "#!/bin/sh" on Linux systems - "bash" has a lot of useful features, and it's universal to all Linux variants (it may not exist by default on other Unix flavors, such as AIX or Solaris).

Lloyd B.

---


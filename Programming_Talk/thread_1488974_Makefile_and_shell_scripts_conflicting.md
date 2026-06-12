---
title: "Makefile and shell scripts conflicting?"
date: 2010-05-20
forum: Programming Talk
---

### Post by Auraomega on 2010-05-20
Hey there,

Attempting to write some shell scripts to aid compiling in Linux however it's being as awkward as possible to get working without issue :p

So far I have is...

makefile:
```

...
package:
	$(shell ./package_kernel.sh $(VAR))
...

```

package_kernel.sh:
```
if [ $# -gt 0 ] ; then
	echo Packaging kernel to $1...
	gzip -9 kernel.bin -c > ../$1
	echo Done!
else
	echo No filename supplied, using default...
	gzip -9 kernel.bin -c > ../Project_Evolution.kgz
	echo Done!
fi

```

[QUOTE=terminal]ubuntu@ubuntu:/media/3A12-10C1/os$ make package VAR=package.kgz
Packaging kernel to package.kgz... Done!
/bin/sh: Packaging: not found
make: *** [package] Error 127
[/QUOTE]

Obviously something is wrong here and I think it's with my echos, running the script via the terminal (./package_kernel.sh package.kgz) works as expected so I'm assuming there is some funky quirk I'm not yet aware of, would anyone mind enlightening me? Obviously I could transfer this little bit of code into my makefile, however with my larger scripts that's not a possibility.

Also is there any good 'tutorials' for makefiles calling scripts and it's little quirks as I'm sure there will be other headaches waiting?

---

### Post by diesch on 2010-05-20
```
$(shell ...)
``` returns the output of the given shell command (like ```
$(...)
``` in the shell). You are trying to run that output, which doesn't work.

Use just 
```
./package_kernel.sh $(VAR)
```

---

### Post by Auraomega on 2010-05-20
D'oh. Thanks for that!

---

### Post by dwhitney67 on 2010-05-20
Also make sure that your scripts are calling out the correct shell to be used when executing.  For example:
```

#!/bin/bash

...

```
Also 'make' uses the shell defined by the environment variable SHELL.  On some Ubuntu systems, this may be set to **/bin/dash**.  If so, then redefine SHELL within your Makefile to use the appropriate shell you wish to use.

P.S.  This is also acceptable for invoking shell script in a Makefile:
```

foo:
        @sh your-script.sh || exit 1

```

---


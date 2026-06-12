---
title: "C pass output to a variable."
date: 2009-06-16
forum: Programming Talk
---

### Post by Woody1987 on 2009-06-16
In my program i want to find out the version of a program i have installed. This program is passed to a function which in turn runs for example:
> system("dpkg -s firefox | grep Version");

This returns
> Version: 3.0.11+build2+nobinonly-0ubuntu0.9.04.1

which is great, but, i want the output to be passed into char. Before i have done something like

> system("dpkg -s firefox | grep Version > version.txt");

This saves the output of the command to version.txt but i would then need another function to read the info into a char, but can i bypass this step and pass the output of the first command straight into a char without having to save it to a file and then read it?

---

### Post by Zugzwang on 2009-06-16
Look up the function "popen" and search for examples for details.

---

### Post by Woody1987 on 2009-06-16
> Look up the function "popen" and search for examples for details.

Thanks, i used an example from [http://www.metalshell.com/source_code/23/Popen.html](http://www.metalshell.com/source_code/23/Popen.html) and it works.

---

### Post by fr4nko on 2009-06-16
> **Zugzwang said:**
> Look up the function "popen" and search for examples for details.
Here an example:
```

#include <stdio.h>
#include <stdlib.h>

FILE *cmdout;
char *line;
size_t llen;

cmdout = popen("dpkg --all-the-options you want", "r");

if (! cmdout) {
  /* treat the error and exit */
}

while (getline (&line, &llen, cmdout) >= 0) {
  /* you can treat you line here */
}

pclose (cmdout);

```As you can see the popen command is very simple, when I use "r" to open a file it starts the subprocess, like system will do, but it returns a file stream that get the output of the subprocess.

To have more informations you can simple type:
> info libc

and search for the 'popen' function.

Note that popen and pclose are high-level functions that gracefully handle all the low-level details needed to use basic pipe commands.

Francesco

---


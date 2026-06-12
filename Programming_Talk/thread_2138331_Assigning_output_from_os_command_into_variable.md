---
title: "Assigning output from os command into variable?"
date: 2013-04-23
forum: Programming Talk
---

### Post by sudo san on 2013-04-23
Hi, I am using python 3.2 in lubuntu 12.04.

I am trying to issue the output of ```
lsb_release -sc
``` into a variable called 'release'.
When run, the interpreter displays the output, but when 'release' is run in the interpreter, it returns 0.

For example:
```
>>> release = (os.system('lsb_release -sc'))
precise
>>> release
0
>>> 
```

What can I add or change to assign the output to the variable?

Thanks in advance.

---

### Post by schragge on 2013-04-23
*/usr/bin/lsb_release* is a python script itself. :) You can import the module instead of trying to execute it through os.system.
```

import lsb_release
release = lsb_release.get_distro_information()['CODENAME']

```
Alternatively, you can use [platform.linux_distribution]("http://docs.python.org/2/library/platform.html#platform.linux_distribution")

---

### Post by sudo san on 2013-04-24
Thanks I will try later!
:)

---

### Post by schragge on 2013-04-24
Sorry, I've noticed you're using Python 3. Then *platform.dist* is the best available option.

As to your code, *os.system()* returns status (0 if command executed successfully). To capture the standard output of a command, you may do something like
```

import subprocess
codename = subprocess.check_output(['lsb_release', '-sc'], universal_newlines=True).rstrip()

```

---

### Post by sudo san on 2013-04-24
Thanks very much!
It now works perfectly!

I appreciate this very much as I have been ripping my hair out not knowing what to do. :)

---


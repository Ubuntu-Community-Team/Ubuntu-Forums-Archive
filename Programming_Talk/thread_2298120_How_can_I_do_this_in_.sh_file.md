---
title: "How can I do this in .sh file ???"
date: 2015-10-09
forum: Programming Talk
---

### Post by hoboy on 2015-10-09
I have installed doxygen on ubuntu 14.04.
I want to write a  test.sh script to run a command from the Terminal.
This is how I run the doxygen test  from the Terminal where test is the file doxygen will run .
test@test:~/Tester$ doxygen test

How can I write a sh script to run  doxygen test ?

---

### Post by Lars Noodén on 2015-10-09
The name of the file is not important as long as it is executable.  For example, if you are making a script called "dtest" then you could start like this:

```

touch dtest
chmod +x dtest
nano dtest

```

The [touch](http://manpages.ubuntu.com/manpages/trusty/en/man1/touch.1.html) and [chmod](http://manpages.ubuntu.com/manpages/trusty/en/man1/chmod.1.html) only need to be done to create the executable file.  Then the first line needs to be which shell interpreter to use, followed by the script itself

```

#!/bin/sh
/usr/bin/doxygen /some/path/to/test

```

There are several shell interpreters to choose from.  [Bash](http://manpages.ubuntu.com/manpages/trusty/en/man1/bash.1.html) is the one you get in the terminal for interactive work, but sh (actually [dash](http://manpages.ubuntu.com/manpages/trusty/en/man1/dash.1.html)) is lighter and more portable so it make more sense to me for scripts.

If you put your script in the directory ~/bin/ then it will be available in your path the next time you log in.  

See also

[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)
[http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)
[http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/)

and many others.

---

### Post by hoboy on 2015-10-09
Tks Lars

---


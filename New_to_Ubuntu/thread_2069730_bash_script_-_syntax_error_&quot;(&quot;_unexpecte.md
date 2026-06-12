---
title: "bash script - syntax error: &quot;(&quot; unexpected"
date: 2012-10-11
forum: New to Ubuntu
---

### Post by wimwam on 2012-10-11
I am trying to write a bash script that calls upon parameters in an array that are stored in a config file, the path of which is stored in /etc/environment and ~/.bash_login as VMS. The config file is sourced using the code below.


if [ -e $VMS ]
           then
                . $VMS
                                readdata
        else
                echo "file not found: "$VMS" "
                exit 0
fi

This all works fine if run in the terminal (which is bash) but not on boot or on login. at boot or login it exits with a "syntax error: "(" unexpected" error.

Me feeling, given my scant knowledge of using bash script, is that at login and boot it is running a sh shell and this is the reason it is not working.

my questions are:

1. is the boot and login shell sh?
2. if 1. is true can i change that or how do i change my code inorder for it to be run as bash in these environments?
3. if the above is not the case; what am i doing wrong and how can i fix it (can i put my config arrays in different places?

I would be very grateful for some input as i am going around in circles and searches have not yielded any obvious solution.

---

### Post by shaktiman1234 on 2012-10-11
if you are a newbie and you want to learn more about shell scripting, I would recommend you to go through the site 
they have awesome tutorial for shell scripting. [Writing shell scripts]("http://linuxcommand.org/lc3_writing_shell_scripts.php")

---

### Post by Lars Noodén on 2012-10-11
I notice that you don't have an explicit shell chosen at the beginning the first line should be either:

```

#!/bin/sh

```

or 

```

#!/bin/bash

```

They are different.  The former will be more portable to other systems and goes to [dash](http://manpages.ubuntu.com/manpages/precise/en/man1/dash.1.html).

---

### Post by wimwam on 2012-10-11
Thanks [shaktiman1234]("http://ubuntuforums.org/member.php?u=1440904") for the info.

The problem is that i have searched extensively and I cannot identify a solution.

I have found that the ~/.bash_login runs in a bash shell by including:

echo $SHELL

in this file, so the answer to point 1. seems to be no

cheers

---

### Post by wimwam on 2012-10-11
Hi [Lars Noodén]("http://ubuntuforums.org/member.php?u=168643"),

Sorry, the piece of code is an extract. the file is #!/bin/bash at the start.

cheers

---


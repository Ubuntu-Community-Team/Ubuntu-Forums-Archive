---
title: "Running Fedora Scripts in Ubuntu"
date: 2009-07-18
forum: Programming Talk
---

### Post by tdrusk on 2009-07-18
I was working on a class assignment in Fedora and thought my scripts would run just fine on Ubuntu as well(as that is what he grades us on). I later found out that there were a lot of errors such as ```
let: command not found
``` and when I did ```
echo -e
``` a singe "e" would show up before every string. This was all using the script I wrote in Fedora and ran in Ubuntu. 

I went back and "fixed" the errors so it would run in Ubuntu, but now the script won't run properly in Fedora #-o

Is there a way I can make my Fedora computer temporarily script like Ubuntu so I don't have to deal with the last minute stress of correcting my programs?

---

### Post by smartbei on 2009-07-18
I think the problem is that in fedora you are running sh and not bash as your shell. Int hat case, either set bash to be your default shell (I don't know how to do this in Fedora) or stick the Shebang in the first line of your script that points to bash.
```

#!/bin/bash

# Your script goes here

```

---

### Post by monraaf on 2009-07-18
Actually, I think it's the other way around. His shell script probably starts with:

```

#!/bin/sh

```

In Fedora /bin/sh is probably a symlink to Bash, in Ubuntu it's a symlink to the dash shell which doesn't understand the bashisms he put in his script. 

If you want your script to be really portable stick to #!/bin/sh and don't use any bashisms otherwise you use #!/bin/bash.

---

### Post by tdrusk on 2009-07-18
> **monraaf said:**
> Actually, I think it's the other way around. His shell script probably starts with:

```

#!/bin/sh

```In Fedora /bin/sh is probably a symlink to Bash, in Ubuntu it's a symlink to the dash shell which doesn't understand the bashisms he put in his script. 

If you want your script to be really portable stick to #!/bin/sh and don't use any bashisms otherwise you use #!/bin/bash.
I tried switching each program to #!/bin/sh and #!/bin/bash . I don't know if either would make a difference if the aliases such as echo being echo -e in Ubuntu.

---

### Post by monraaf on 2009-07-18
```

/bin/sh -c 'echo -e'
-e

```

```

/bin/bash -c 'echo -e'


```

Yes, it makes a difference.

---

### Post by dwhitney67 on 2009-07-18
> **smartbei said:**
> ... either set bash to be your default shell (I don't know how to do this in Fedora)...


It's the same as in Ubuntu; just edit the /etc/passwd file.  If one wants to use a GUI, well then that may differ from one OS to another.

---

### Post by tdrusk on 2009-07-18
Okay I get it!

I was running ```
sh script
``` in fedora. This doesn't work in Ubuntu because Ubuntu actually uses sh when running this, not BASH(as mentioned previously in this thread).

After I did ```
chmod +x script && ./script
``` in Ubuntu I was doing great. 

I am glad I learned something :)

---

### Post by dwhitney67 on 2009-07-19
Under Ubuntu, if you have bash installed (by default, it does not come with it, but instead dash), you could have typed:
```

bash script

```
For portability purposes, the thing to remember, if you want you script using bash, is to define the #!/bin/bash at the beginning of your script.  Next is to ensure that you have bash installed on the system, and not some knockoff (eg dash).

On my Ubuntu system, I also redefine /bin/sh to be a symbolic link to /bin/bash; similar to Fedora.

---


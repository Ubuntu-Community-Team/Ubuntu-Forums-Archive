---
title: "How to display absolute path of a files - from search result?"
date: 2010-09-22
forum: Programming Talk
---

### Post by Rushyang on 2010-09-22
Bonjour Guys!

I'm writing a script in which I need to have a filename from user, and then it will search into particular directory in order to find that specific file. 

and whatever the file is found.. I need to display the ABSOLUTE ( COMPLETE ) path instead of the RELATIVE one. I am not able to figure this out. 

Any suggestions?

---

### Post by r-senior on 2010-09-22
You can sort of use readlink to do this but I don't know whether it's the "proper" way to do it. Readlink is really intended for determining what path a symbolic link points to, but you can also ask it for the path of a regular file (which you must make sure exists). It's a hack, admittedly.

```

$ cd /bin
$ readlink -f ./bash
/bin/bash

```

---

### Post by dwhitney67 on 2010-09-22
Let's see... find a file based on its name, from within a particular directory.

Does the following script meet your needs?

myfind
```

#!/bin/bash

dir=$1
file=$2

find $dir -name $file

```
Sample usage:
```

myfind /usr gedit

```
I'm not sure what is the purpose of having a script like this; it is just as easy to run the 'find' command itself from the command line.

---

### Post by Rushyang on 2010-09-23
> **r-senior said:**
> You can sort of use readlink to do this but I don't know whether it's the "proper" way to do it. Readlink is really intended for determining what path a symbolic link points to, but you can also ask it for the path of a regular file (which you must make sure exists). It's a hack, admittedly.

```

$ cd /bin
$ readlink -f ./bash
/bin/bash

```

Thanks a lot for readlink command... This is exactly what I needed..! Super cool..! :guitar:

---


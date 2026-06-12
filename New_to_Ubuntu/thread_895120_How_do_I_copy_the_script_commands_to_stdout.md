---
title: "How do I copy the script commands to stdout?"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by gordonsowner on 2008-08-19
This is probably really easy, but I'm drawing a blank... I have a script with commands in them and I am directing stdout and stderr to a file.  I would like behavior to be like a windows .bat file, where the commands AND the command output are both directed to the output file.  How do i do this?  This is the form of my call:

```
./my-script > /tmp/my-script.log 2>&1

```

---

### Post by unutbu on 2008-08-19
It's not very pretty, but perhaps just use echos?
```
#!/bin/sh

echo "% ls -l"
ls -l
echo 

echo "% dmesg | grep video"
dmesg | grep video
echo

```

---

### Post by gordonsowner on 2008-08-19
Uff da... I was hoping for a command with a switch, because that solution isn't feasible for me... Thanks, though!

---

### Post by sdennie on 2008-08-20
I think you can just use "cat $0".  For example:

```

#!/bin/bash

cat $0

echo "Hello World"

```

---

### Post by caljohnsmith on 2008-08-20
I think what you want to do can be accomplished with "set -x". Just put it at the beginning of your script:
```
#!/bin/bash
set -x

...script...

```

---

### Post by Thingymebob on 2008-08-20
Why not use the script command? 

```

#!/bin/sh

script my-script.log

.......SCRIPT.....

exit

```

---

### Post by gordonsowner on 2008-08-20
Thanks!

I'll try 'set -x', and I've never heard of the 'script' command, so I'll be looking that up, too... Thanks all!

Matt

---


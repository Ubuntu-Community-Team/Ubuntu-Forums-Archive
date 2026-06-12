---
title: "Shell script - concatenating strings..."
date: 2012-12-04
forum: Programming Talk
---

### Post by dchurch24 on 2012-12-04
Hi all,

I have a shell script that I'm trying to run and a passing a parameter to:

I call it be:

./switch.sh 3

```

#!/bin/bash

sudo -u pi echo -e '\xff\x0$1\x01' > /dev/ttyUSB0;


```

I was hoping it would give me:

```

sudo -u pi echo -e '\xff\x0**3**\x01' > /dev/ttyUSB0;

```

...but I don't get anything out to the screen and the switch is not triggered via the serial port.

If I simply change the $1 to the 3, then it works fine.

I'm guessing it's something to do with the way I'm embedding the parameter, but I've tried a variety of ways and I just can't seem to figure it out.

---

### Post by drmrgd on 2012-12-04
It's because you've used single quotes instead of double quotes.  Single quotes literally interpret the string, while double quotes will allow for variable expansion.  Try with double-quotes and see if that helps.

---

### Post by papibe on 2012-12-04
Hi dchurch24.

drmrgd is right regarding the content of you want to echo on the device.

However, note that that shell construction does not work. The access to the device will be asked before converting to the other user (the sudo part).

Use this syntax instead:
```
sudo -u pi bash -c 'echo -e "\xff\x$1\x01" > /dev/ttyUSB0'
```
Let us know how it goes.
Regards.

---

### Post by Vaphell on 2012-12-04
i'd switch those quotes around

```
$ x=abc
$ bash -c 'echo "=$x="'
==
$ bash -c "echo '=$x='"
=abc=
```

---

### Post by dchurch24 on 2012-12-04
Hi chaps,

thanks for the replies, truly appreciated.  I've tried so many variations that I think I tried the double quote way...but my memory is poor so it's quite likely that I haven't!

I will, however try that in the morning as I'm not back at my house at the moment.

Also, I'm not sure what you mean about the shell construction, but I found that I had to change the permissions on the ttyUSB file before it would work. Could it be that the 'sudo -u' is not actually doing anything and that's why I have to change the permissions?

---

### Post by papibe on 2012-12-04
> **dchurch24 said:**
> I'm not sure what you mean about the shell construction, ...
It is a matter of how bash, the interpreter, works. The redirection of the standard output (using >), will occur before the sudo is ran, thus the access will be either granted or restricted based on your current user.

Try this as an example:
```
sudo echo "Hello, World." > dummy.txt
```
The file 'dummy.txt' is created before running sudo, thus it will be created using your user privileges.

You can double check by doing:
```
ls -l dummy.txt 
-rw-r--r-- 1 **youruser youruser** 14 2012-12-04 16:23 dummy.txt

```
When you use the bash string command, the current bash interpreter don't see any redirection, so it runs sudo. Then the string will be executed completely as root:
```
$ rm dummy.txt 
$ sudo bash -c 'echo "Hello, World." > dummy.txt'
$ ls -l dummy.txt 
-rw-r--r-- 1 root root 14 2012-12-04 16:28 dummy.txt

```
Let us know how it goes.
Regards.

---


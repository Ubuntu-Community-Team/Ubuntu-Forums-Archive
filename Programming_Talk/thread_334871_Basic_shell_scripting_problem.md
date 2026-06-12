---
title: "Basic shell scripting problem"
date: 2007-01-09
forum: Programming Talk
---

### Post by tpg on 2007-01-09
I've recently been experimenting with encrypted loopmounted filesystems to give me a way of storing data on a memory stick securely. In order to automate the mount/unmount process, I am trying to make a simple shell script. The desired behaviour is that running it "usbcrypto mount" will mount the file, and "usbcrypto unmount" will unmount it. However, I am running into problems when trying to test the arguments.

```

#!/bin/sh

sudo -v -p "SUDO Password:"
if [ $1="unmount" ]
then
	sudo umount /media/encrypted
elif [ $1="mount" ]
then
	sudo modprobe cryptoloop
	echo "Now enter encryption password."
	sudo mount /media/usbdisk/encrypted.fs /media/encrypted -o rw,loop,encryption=aes
fi
sudo -k

```

However, whatever arguments I pass, the first block (the unmount command) is always executed. What am I doing wrong? 

Thanks in advance, tpg

---

### Post by 23meg on 2007-01-09
Use "else" instead of "elif" and "then".```

else
	sudo modprobe cryptoloop
	echo "Now enter encryption password."
	sudo mount /media/usbdisk/encrypted.fs /media/encrypted -o rw,loop,encryption=aes
fi
```

---

### Post by tpg on 2007-01-09
> **23meg said:**
> Use "else" instead of "elif" and "then".```

else
	sudo modprobe cryptoloop
	echo "Now enter encryption password."
	sudo mount /media/usbdisk/encrypted.fs /media/encrypted -o rw,loop,encryption=aes
fi
```

This doesn't seem to make any difference; the first block of code is still executed every time.

---

### Post by Arndt on 2007-01-10
> **tpg said:**
> This doesn't seem to make any difference; the first block of code is still executed every time.

I think you need spaces around the = operator:

```
if [ $1 = "unmount" ]
then
```

---

### Post by tpg on 2007-01-10
I tried that, but it gave an error message, but the following seems to work

```

if [ "$1" = "unmount" ]
then

```

Thanks for the help!

---

### Post by Keith Hedger on 2007-01-10
the correct syntax is:

#!/bin/sh

if [ $1 = "option1" ] ;then
	echo "option1"
elif [ $1 = "option2" ] ;then
	echo "option2"
fi

also u might want to download the bash scripting guide its in the repos under abs-guide

---

### Post by kj1h234lkj1234 on 2007-01-10
There's also an online version:

[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

---

### Post by tpg on 2007-01-10
> **Keith Hedger said:**
> the correct syntax is:

#!/bin/sh

if [ $1 = "option1" ] ;then
	echo "option1"
elif [ $1 = "option2" ] ;then
	echo "option2"
fi

Thanks very much, this also works (and seems to make more logical sense than having "$1" in quotation marks).

---

### Post by Arndt on 2007-01-11
> **tpg said:**
> Thanks very much, this also works (and seems to make more logical sense than having "$1" in quotation marks).

The quotation marks help if you happen to give an empty argument; then the version without the quotation marks will give an error message (because the left argument to = is not there).

---

### Post by tpg on 2007-01-13
So using quotation marks doesn't actually effect the comparison when the argument is not empty?

---

### Post by Keith Hedger on 2007-01-16
the quotes stop bash from interprating the string as different commands if the value contains spaces.
if you need to worry about empty variables (NULL NOT "" which is two diferent things) prefix each value with say an "X" this cancelles out and prevents NULL errors ie:

t1=option1;if [ X$t1  = X"option1" ] ;then echo "if";else echo "else";fi
gives if

t1=; if [ $t1  = "option1" ] ;then echo "if";else echo "else";fi
gives else AND an error (bash: [: =: unary operator expected)

t1=; if [ X$t1  = X"option1" ] ;then echo "if";else echo "else";fi
gives else (and no error)

---


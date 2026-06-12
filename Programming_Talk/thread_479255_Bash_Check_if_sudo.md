---
title: "Bash: Check if sudo"
date: 2007-06-20
forum: Programming Talk
---

### Post by ebbe on 2007-06-20
This should be a easy question. I'm new to bash-scripting, but I want to play with it a bit.

I've made a script that can download a big file, and shutdown the computer afterwards, but to make it bulletproof, I want to check if the user wrote sudo in front of it, or else I cant shutdown the computer.

```
#!/bin/bash

if [[ $1 != "" ]]
then
        wget -c "$1";
        sudo shutdown -k 0;
else
        echo "Usage: sudo ./downloadAndShutdown <fileToDownload>";
fi
```

I already check to see if a file has been specified, but still I need to see if the script has the right privileges, and if not only print usage-message.

Ebbe

---

### Post by visik7 on 2007-06-20
```
visi@lappy:~$ whoami 
visi
visi@lappy:~$ sudo whoami 
root

```

 is enought ?

---

### Post by ebbe on 2007-06-20
> **visik7 said:**
> ```
visi@lappy:~$ whoami 
visi
visi@lappy:~$ sudo whoami 
root

```


It's perfect :)
Thanks.

---

### Post by HackingYodel on 2007-06-20
As a sidenote:

You could also use
```
if [ "$(id -u)" != "0" ]; then
	echo "Sorry, you are not root."
	exit 1
fi
```

With **whoami** being the same as **id -un**
```
if [ "$(whoami)" != "root" ]; then
	echo "Sorry, you are not root."
	exit 1
fi
```


Have fun scripting!

---

### Post by Jessehk on 2007-06-20
Even something like this:

```

ROOT_UID=0

if [ $UID != $ROOT_UID ]; then
    echo "You don't have sufficient privileges to run this script."
    exit 1
fi

```

---

### Post by ebbe on 2007-06-21
Thanks for the nice replies. I think I'm going for
```
if [ "$(whoami)" != "root" ]; then
```

It's easier to read.

And yes! My script works as expected :)

---

### Post by hasimir44 on 2007-06-22
just wanted to say that this is a great idea..

---

### Post by ebbe on 2007-06-24
Just want to show you the final script. The only problem now, is that the file will have root as owner..
Maybe a chown should be thrown in there.

```
#!/bin/bash

whoami | grep "root" > /dev/null
if [ $? -eq 1 ] || [ "$1" = "" ]
then
	echo "Usage: sudo $0 <fileToDownload>";
	exit;
fi

wget -c "$1";
shutdown -P +3 "The shutdown can be stopped with: sudo shutdown -c";
```

---

### Post by Mr. C. on 2007-06-24
To use grep and produce no output, use the -q option:

```
$ grep -q root /etc/passwd
$ echo $?
0
```

No need to run whoami.  You can just test the value of the environment variable UID:

```
$ sudo sh -c 'echo $UID'
0
```

Root UID is always 0.  This makes your test:

```
if [ $UID -eq 0 ] ; then
  ...
fi

```

You can also use "id -u" to get the UID.



MrC

---


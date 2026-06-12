---
title: "Help creating a special folder"
date: 2009-04-24
forum: Programming Talk
---

### Post by brandon88tube on 2009-04-24
I want to make a special type of folder that when something is created in it, the folder deletes whatever was created similar to /dev/null. The difference is that I want the file to be able to be quickly read back after being created before being deleted. I have no idea how I would go about doing this and I figured the programming area would be the best place to ask.

---

### Post by Namtabmai on 2009-04-24
Sorry I can't be too much help but I think something like inotify would help you. It's a linux kernel subsystem that provides file system event notification, should do what you want.

---

### Post by sgosnell on 2009-04-24
I don't believe you can have folders with those properties.  You have to do it externally, each time, via a script or something similar.  You could easily make a script that puts a file into a folder, reads it, and then deletes it.

---

### Post by Volt9000 on 2009-04-25
I haven't tested the following too thoroughly but it seems to work well.

First install inotify-tools:

```

sudo apt-get install inotify-tools

```

----------- IMPORTANT NOTE -------------------
Please use this at your own risk. This script contains an rm -rf command which will forcefully remove all files and directories in the specified watch directory as soon as a file is created/moved/copied to it. Use at your own risk and make sure to specify the correct directory to watch.
----------- IMPORTANT NOTE -------------------

Now make the following script:

```

#!/bin/sh

if [ $# -lt 1 ]; then
	echo "You must specify a directory to watch."
	exit
fi

while inotifywait -q -q -e create -e moved_to $1
do
	rm -rf $1/*
done

```

Make the script executable and then just run it, passing to it the directory you want to watch. For example:

```

watchit /path/to/directory &

```

'watchit' being the filename of the above script.

You can specify the ampersand at the end so you don't have to keep the terminal window permanently open for the program to run.
The two -q arguments to inotifywait tell the script to be completely silent except for critical errors.

Note that this script will not work if it's in the directory you're monitoring.

Unfortunately the only thing I could think of to stop this script was to forcefully terminate it (sorry, I'm a bit of a scripting noob myself. ;)

```

killall inotifywait

```

---

### Post by lensman3 on 2009-04-25
You can do it by:

1) create a file
    creat("/tmp/xxxx", O);

2) Open the file.
    file = open("/tmp/xxxx", O_RDRW);

3) then remove the file using.
    unlink( "/tmp/xxx");

4) The remaining file handle is still open and usuable until the last file descriptor referring to the file is closed.  Forked processes will have access.  No other process will have access to the file, as its directory entry in /tmp has been removed with the unlink().

Hope this helps.  (These are the C function calls).

Hope this helps.

---

### Post by brandon88tube on 2009-04-27
> **lensman3 said:**
> You can do it by:

1) create a file
    creat("/tmp/xxxx", O);

2) Open the file.
    file = open("/tmp/xxxx", O_RDRW);

3) then remove the file using.
    unlink( "/tmp/xxx");

4) The remaining file handle is still open and usuable until the last file descriptor referring to the file is closed.  Forked processes will have access.  No other process will have access to the file, as its directory entry in /tmp has been removed with the unlink().

Hope this helps.  (These are the C function calls).

Hope this helps.

I'm not quite sure how this works. Does this get removed when you restart because its in the /tmp directory?

---

### Post by lensman3 on 2009-04-27
The file(s) can be anywhere on the system.   This example was just for /tmp. Essentially, it creates a file by name, but is opened using FILE pointers.  When the last link (in the FILE pointer) is released, the Kernels file system code finally releases the inodes.

---


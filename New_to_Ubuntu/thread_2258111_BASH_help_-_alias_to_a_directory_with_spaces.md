---
title: "BASH help - alias to a directory with spaces"
date: 2014-12-24
forum: New to Ubuntu
---

### Post by Mark_Oesterling on 2014-12-24
So the gist is I have a dual boot system with Windows and I am trying to write a shell for rsync as the final goal to synchronize a Linux directory with a Windows directory.  But the problem is the aggravating "Documents and Settings" in the path.  The spaces.  :-(

When I open the OS with Nautilus and it mounts it, I can find what I have mounted with the following terminal command:

```
ls /media/mylinuxname/OS/"Documents and Settings"/my.windowsname/"My Documents"
```

And if I have the following BASH script to check and see if the directory is there:

```
#!/bin/bash# My first script


MYDEST=/media/mylinuxname/OS/
echo "MYDEST is $MYDEST"


if [ ! -d $MYDEST ] 


then
    echo "It is NOT a directory"
    exit
fi


echo "It is a directory and the contents are..."
ls $MYDEST



```

It works like a charm, in that if I UNMOUNT the OS via Nautilus, it cannot find it and executes my conditional.

The fun begins because the next directory I need is this "Documents and Settings" and I have tried every permutation I can find on the net.  Single quotes.  Double quotes.  Escaping it with a \ character.  It hates this.

My end goal is this:

1) Check and see if the destination directory exists, if it doesn't exit script.
2) Check and see if the source directory exists, if it doesn't exit script.
3) If both directories exist, sync them with "rsync"

So ....  how do I fix?
Is there a better way?
Is it possible to attempt to mount if it cannot see the destination directory?

Thanks.

---

### Post by Impavidus on 2014-12-24
Quote the variable where you call it:```
"$MYDEST"
```
As for where to put the quotes, it doesn't matter, as long as the spaces are quoted. Least chance of errors when you minimise the number of quotes.
```

ls /media/mylinuxname/OS/Documents" "and" "Settings/my.windowsname/My" "Documents
ls /media/mylinuxname/OS/Docum"ents and Se"ttings/my.windowsna"me/My "Documents
ls /media/mylinuxname/OS/"Documents and Settings"/my.windowsname/"My Documents"
ls "/media/mylinuxname/OS/Documents and Settings/my.windowsname/My Documents"

```They all work. Last one is recommended.
> 
Is it possible to attempt to mount if it cannot see the destination directory?

In principle, yes, but you'll have to set things up so that it can be mounted by an ordinary user or run the script with root privileges. That last thing I wouldn't recommend. A simple bug in the script could destroy your system. The file manager has some tricks to run certain things, like mounting partitions, with elevated permissions.

---

### Post by schragge on 2014-12-24
+1 to **Impavidius**. Personally, I find [pmount]("http://manpages.ubuntu.com/manpages/trusty/en/man1/pmount.1.html") easier to deal with in a script than fumbling with [udev rules]("https://help.ubuntu.com/community/UsbDriveDoSomethingHowto") or [/etc/fstab]("https://help.ubuntu.com/community/Fstab") entries.

---

### Post by whitesmith on 2014-12-25
Yet another approach is something like```
My\ Documents
```in which characters with special meanings in the shell are escaped. @Mark_Oesterling : if any of these answers do it for you, please help others by marking the thread as closed.

---


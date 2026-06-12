---
title: "Recursively Deleting Hidden Files and Folders in Ubuntu 14.04.2"
date: 2015-04-24
forum: New to Ubuntu
---

### Post by James_Groves on 2015-04-24
Ok, so I'm migrating a user profile over to a network share, after shifting the entire contents of the <user> home profile into "../lin/" (as both a Windows and Linux system maybe accessing this profile, I thought it'd be a good idea to separate the two profiles into "lin" (Linux) and "win" (Windows) folders. 

So the issue comes up of recursively deleting the hidden files and folders:

After running:
```

root@mg:/home/<user># rm -rf *

```

to remove all normal files and folders, it turns out you can then do rm -rf .* to remove the hidden directories, and despite it's complaint about not being able to remove current directory (.) and the parent directory (..) - it does in fact remove the hidden folders, see below:

```


root@mg:/home/<user># ls -a
.   .cache   .config  .gconf  .gnome2  .mozilla  .ssh
..  .compiz  .dbus    .gnome  .local   .pki      .thunderbird
root@mg:/home/<user># rm -rf .*
rm: cannot remove directory: &#8216;.&#8217;
rm: cannot remove directory: &#8216;..&#8217;
root@mg:/home/<user># ls -a
.  ..



```

---

### Post by steeldriver on 2015-04-24
FYI you could have used the dotglob shell option

```

$ tree -a
.
&#9500;&#9472;&#9472; .otherdir
&#9474;   &#9500;&#9472;&#9472; otherfile
&#9474;   &#9492;&#9472;&#9472; somefile
&#9492;&#9472;&#9472; .somedir
    &#9500;&#9472;&#9472; otherfile
    &#9492;&#9472;&#9472; somefile

$ rm -r *
rm: cannot remove ‘*’: No such file or directory

```
but
```

[B]$ shopt -s dotglob
[/B]$ rm -r *

$ tree -a
.

0 directories, 0 files

```

---


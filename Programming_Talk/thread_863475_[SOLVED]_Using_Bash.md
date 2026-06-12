---
title: "[SOLVED] Using Bash"
date: 2008-07-18
forum: Programming Talk
---

### Post by Jesdisciple on 2008-07-18
I can't seem to get Bash working...

~/www/lib/Bash/hello.sh```
#/bin/bash

echo "Hello world!"
```

terminal output```
chris@Jesdisciple-laptop:~$ cd www/lib/Bash
chris@Jesdisciple-laptop:~/www/lib/Bash$ whereis bash
bash: /bin/bash /etc/bash.bashrc /usr/share/bash /usr/share/man/man1/bash.1.gz
chris@Jesdisciple-laptop:~/www/lib/Bash$ chmod -x hello.sh
chris@Jesdisciple-laptop:~/www/lib/Bash$ hello.sh
bash: hello.sh: command not found
```

Help, please?

---

### Post by Martje_001 on 2008-07-18
**chmod -x hello.sh** has to be [B]chmod +x hello.sh
[/B] and **hello.sh** has to be **./hello.sh**

'.' stand for *this directory*.

---

### Post by WW on 2008-07-18
Try this instead:
```

$ chmod u+x hello.sh
$ ./hello.sh

```

---

### Post by daRealScanMan on 2008-07-18
[QUOTE=Jesdisciple;5412295]```
#/bin/bash
echo "Hello world!"
```I think you're missing an ampersand.
```
#**!**/bin/bash
echo "Hello world!"
```

---

### Post by Jesdisciple on 2008-07-18
Thanks Martje and WW; that works, but I wonder why the dot is only required some places...

@ScanMan: Oh, you mean an exclamation point. Thanks; I must have pasted over that when I corrected my path to Bash.  But interestingly, it doesn't seem to be required...

---

### Post by mssever on 2008-07-18
> **Jesdisciple said:**
> Thanks Martje and WW; that works, but I wonder why the dot is only required some places...
When you type a filename without giving a directory, Bash searches the directories in PATH for a matching file. Since by default . isn't in PATH (and shouldn't be unless you know what you're doing), you have to give a directory. The shortcut for the current directory is . and .. is the shortcut for the parent directory.

You can see this if you do an ls -a.

---

### Post by Jesdisciple on 2008-07-18
I know that part, but not all relative path names require the ./ - and I wonder what+why the distinction is.

---

### Post by mssever on 2008-07-18
> **Jesdisciple said:**
> I know that part, but not all relative path names require the ./ - and I wonder what+why the distinction is.
If the command isn't a shell builtin and isn't in the PATH, it requires the directory to be given. There are no exceptions. Of course, you don't need to specify ./ if you're giving the directory some other way.

---


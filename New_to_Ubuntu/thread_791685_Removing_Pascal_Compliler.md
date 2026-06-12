---
title: "Removing Pascal Compliler"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by ^^viktor^^ on 2008-05-12
I downloaded and installed this compiler. [http://sourceforge.net/project/downloading.php?groupname=freepascal&filename=fpc-2.0.0.x86_64-linux.tar&use_mirror=surfnet](http://sourceforge.net/project/downloading.php?groupname=freepascal&filename=fpc-2.0.0.x86_64-linux.tar&use_mirror=surfnet)
The problem is that I installed it on the desktop by mistake and I can`t remove it. I tried rm but that doesn`t do the job. How can I remove it?

P.S. I was wondering... can anyone explain to me or give se some tutorials on manual installation on software. Tnx,

---

### Post by ConMan318 on 2008-05-12
Well if your only problem is that you installed it in the wrong place you could just move it with the 'mv' command.  Try:

```

mv /home/**username**/Desktop/**filename** /bin/**filename**

```
where username and filename are replaced with your login name and the name of the file on the desktop, respectively.

If you really just want to remove it you could do:

```

sudo rm /home/Desktop/**filename** -rf

```
but **the -rf tag with the rm command is a very dangerous command** and should only be used if you're sure you know what you're doing.

You could also remove everything in that directory and delete its contents  before removing it safely, like:
```

cd /home/**username**/Desktop/**filename**
rm *
cd ..
rmdir **filename**

```
The 'rm *' part is **without** the -rf tag so it doesn't remove directories '.' and '..'; this way it will only remove files, not directories.  If there are directories within the main directory you'll need to navigate into them/clear them/remove them with 'rmdir' or remove them with the -rf tag.

---

### Post by ^^viktor^^ on 2008-05-12
Tnx, the -rf worked. I fixed it.

BTW Can anyone help me with mu P.S.?

---


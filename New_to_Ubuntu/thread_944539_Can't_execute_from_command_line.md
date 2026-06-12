---
title: "Can't execute from command line"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by psyconn on 2008-10-11
I have a very strange problem, I can't execute a file.
```

psycon@psycon-desktop:~/downloads/vmware-server-distrib$ ls
bin  doc  etc  FILES  installer  lib  man  sbin  vmware-install.pl  vmware-vix
psycon@psycon-desktop:~/downloads/vmware-server-distrib$ pwd
/home/psycon/downloads/vmware-server-distrib
psycon@psycon-desktop:~/downloads/vmware-server-distrib$ sudo vmware-install.pl
sudo: vmware-install.pl: command not found
psycon@psycon-desktop:~/downloads/vmware-server-distrib$ ls -la vmware-in*
lrwxrwxrwx 1 psycon psycon 23 2008-10-11 19:44 vmware-install.pl -> bin/vmware-uninstall.pl
psycon@psycon-desktop:~/downloads/vmware-server-distrib$ vmware-inst*
bash: vmware-install.pl: command not found

```

I'm using up to date 8.04 release.

---

### Post by taladan on 2008-10-11
Make sure the file is executable do an 'ls -l' and look for rwx in the first column.  

Then use:

```
./vmware-install.pl
```

Notice the ./

It'll allow you to execute the file.

Tal

---

### Post by psyconn on 2008-10-11
It works now... thanks.

---


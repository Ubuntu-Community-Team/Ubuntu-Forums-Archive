---
title: "[Python] Changing File Permissions During or After Copy"
date: 2010-07-22
forum: Programming Talk
---

### Post by dodle on 2010-07-22
First I will explain what I am doing:  I have a program that builds binary Debian packages.  It first copies files into a temporary directory tree then invokes "**fakeroot dpkg -b**" to build the .deb.  I started using the **lintian** command on the packages I was building and realized there were a lot of errors.  Many of the errors were due to some files that I had transferred from a Windows machine, the file permissions were messed up.  So I got a lot of the following errors:
```
non-standard-file-perm usr/share/myapp/icon.xpm 0666 != 0644
non-standard-executable-perm usr/share/myapp/start.py 0777 != 0755
```

My first question is, is it a good idea to have my program automatically change the permissions for files and executables?  Secondly, does python have a method to do this during the copy process?  Currently I am using **shutil.copy(src, dest)**, which copies the file permissions as they are.  If it is better to do it after the file has been copied, is one of these methods preferred over the other:  **os.system("chmod")**, **commands.getstatusoutput("chmod")**, or **os.chmod(path, mode)**?

---


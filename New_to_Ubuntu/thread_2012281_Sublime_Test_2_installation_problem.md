---
title: "Sublime Test 2 installation problem"
date: 2012-06-28
forum: New to Ubuntu
---

### Post by jjz on 2012-06-28
Never mind, I have a work around that seems to do the job.

I tried to install Sublime Text 2 on Ubuntu 12.04 but when I try to open it I get this error message:

[INDENT]Traceback (most recent call last):
  File "./PackageSetup.py", line 165, in upgrade
    upgradePackage(pkg, pristinedir, datadir, backupdir)
  File "./PackageSetup.py", line 158, in upgradePackage
    os.path.join(backupdir, base), inhibitOverwrite)
  File "./PackageSetup.py", line 90, in upgradeArchive
    writeFile(fname, newar.read(f))
  File "./PackageSetup.py", line 18, in writeFile
    with open(fname, 'wb') as fo:
IOError: [Errno 2] No such file or directory: u'/home/jjz/.config/sublime-text-2/Packages/Package Control/readme.creole'[/INDENT]

Anyone able to help me fix the problem--I'm an absolute beginner.

---

### Post by carlosfaria on 2012-09-18
The problem is that you tried to install the package within Sublime without using sudo. So Sublime has not the permission rights to create files and folders.

The solution is to make a manual install.

First download sublime package control from github:
[https://github.com/wbond/sublime_package_control](https://github.com/wbond/sublime_package_control)
Extract it to a folder (in my case Downloads/Package Control) and move the files to a folder called Package Control inside .config/sublime-text-2/Packages using terminal:

**sudo mv Downloads/Package\ Control/ .config/sublime-text-2/Packages/**

Then another error appears. We need to copy another file provided by the author of the package:

[http://sublime.wbond.net/Package%20Control.sublime-package](http://sublime.wbond.net/Package%20Control.sublime-package)

and then copy it to .config/sublime-text-2/Pristine Packages

**sudo mv Package\ Control.sublime-package .config/sublime-text-2/Pristine\ Packages/**

There you have it. Hope it helps.

---


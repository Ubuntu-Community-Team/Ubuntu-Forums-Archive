---
title: "Change the default installation locations for MySQL, Apache and Php"
date: 2014-02-13
forum: New to Ubuntu
---

### Post by kristian3 on 2014-02-13
How do I change the default installation locations for MySql, Apache, Php either when installing them, or after they are installed?

I'm a little uncomfortable leaving things in their default installation locations, and wanted to change them to something like, say, krisMySql/ and krisServer/ and krisPhp/
 
How can I do something like this. It's easy to do on Windows, but I'm just starting off with Ubuntu Server.

Thanks

---

### Post by ian-weisser on 2014-02-15
The short answer is: Install manually instead of using the package manager.

The package manager expects that you won't move files it installs around. It expects to find them again in that same place when the time comes to update or uninstall. You don't get to choose that location - the packager chose it for you. The packager chose directory names and locations that are expected for the kind of file, and won't conflict with any other package's filenames or locations.

In theory, you can unzip a package and edit the locations before installing...but in practice that's a lot of extra work, and error-prone. The first time an updated package slips past without such editing, it will happily install to the (wrong) location. And some packages update frequently.

Your question implies that you're not comfortable with packages and package management yet. That's common. Play with it a bit, and get comfortable.

---


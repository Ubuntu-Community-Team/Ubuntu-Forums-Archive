---
title: "QT-Designer?"
date: 2006-02-02
forum: Programming Talk
---

### Post by Begatelles on 2006-02-02
I was wondering where i can download the latest version of **QT-Designer and other development tools** for Kubuntu. Can someone give me directions please? 

Will very much appreciate it. Thanks!

---

### Post by Adrian on 2006-02-02
[QUOTE=Begatelles]I was wondering where i can download the latest version of **QT-Designer and other development tools** for Kubuntu. Can someone give me directions please? 

Will very much appreciate it. Thanks![/QUOTE]

I'm on SUSE at the moment, but I think this will work:
(Use the Adept package manager or aptitude/apt-get to install the packages. No manual downloading/unpackaging/installing is necessary)

* Enable the additional repositories (most importantly the universe repository). Instructions of how to do that can be found here:
[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

* For a nice IDE and a lot of tools, install the **build-essential** and the **kdevelop3** package

* For QT Designer 3 + family, install the following packages:
**qt3-dev-tools**
**qt3-apps-dev**
**qt3-designer**
**qt3-doc**
**qt3-examples**

If you miss anything, do a search on this site:
[http://packages.ubuntu.com](http://packages.ubuntu.com)

Here you can search for programs installable through the excellent package management system.

Hope this helps.

---

### Post by asimon on 2006-02-02
The above instructions will only give you Qt 3.3.4, the latest Qt3 version is 3.3.5. Probably you need to compile this yourself again if you want 3.3.5 (rebuilding the qt3 packages from Dapper may work)

And in case "latest version" means the latest version of Qt4, then I recommend to download the Qt4 sources from Trolltech.com and compile them yourself. The qt4 packages from Breezy are quite old (version 4.0.0, you don't want to use that) and I know of no repository which contains a Qt 4.1 for Breezy.

---

### Post by Adrian on 2006-02-02
[QUOTE=asimon]And in case **"latest version"** means the latest version of Qt4...[/quote]

[QUOTE=Begatelles]I was wondering where i can download the **latest** version of QT-Designer and other development tools for Kubuntu.[/quote]

Sorry, I didn't notice the word "latest" in the original post. I guess I have to start reading more carefully.

I think compiling from source is your best option, if you want the **latest** version:
[http://www.trolltech.com/download/qt/x11.html](http://www.trolltech.com/download/qt/x11.html)

---

### Post by Begatelles on 2006-02-02
Thanks so much guys. I'll try seting them up and let you know in case i have trouble. Thanks again, you're awesome!

---


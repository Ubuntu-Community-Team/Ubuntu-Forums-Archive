---
title: "nautilus-admin"
date: 2020-07-25
forum: New to Ubuntu
---

### Post by csmanager on 2020-07-25
i'm using ubuntu and a want to open some folder as administrator to paste some files, but after i installed nautilus-admin ```
[COLOR=#333333][FONT=Monaco]sudo apt install nautilus-admin[/FONT][/COLOR]
``` like it is described here [HTML]http://ubuntuhandbook.org/index.php/2020/04/open-as-administrator-ubuntu-20-04/[/HTML] and the option is not appearing after right click on any folder.

What can i do to make this option appear or to open folders as administrator?

---

### Post by TheFu on 2020-07-25
Often, to see any GUI changes, a logout-login is needed.

**WARNING:**
Running almost all GUI programs using a root account or sudo is a bad idea. There are often undesirable side effects. It is possible, accidentally, to prevent a userid from being able to login just by running a GUI command with sudo even without making any changes, for example.  You've been warned.  GUI programs almost always save settings. In the process of saving those settings, files and directories are created using the current HOME environment variable, which is usually the userid running the GUI session, not root.  That means directories and files are owned by root:root which shouldn't be.  On a new install creating these directories, this can be catastrophic.

There are ways to mitigate some of the possible problems. The easiest would be to use **sudo -H {GUI-program}** for the commands, but some will refuse to run in that way.

Regardless, if you must run GUI programs as root, you'll want a 2nd userid with sudo capabilities or keep a Live Boot environment like a desktop install with the "Try Ubuntu" option, so you can come into the storage after the fact and correct permissions.

Please be careful.

The best answer is to use shell/CLI commands for administration needs, not GUIs.  I realize this will be a hassle for most people new-to-linux or who want to think that GUIs are better.

---

### Post by pbear42 on 2020-07-25
> **TheFu said:**
> Often, to see any GUI changes, a logout-login is needed.
Running almost all GUI programs using a root account or sudo is a bad idea. There are often undesirable side effects. 
FYI, how sudo works with GUI apps changed dramatically with version 19.10, carried forward into 20.04.  See [askubuntu]("https://askubuntu.com/questions/1186999/how-does-sudo-handle-home-differently-since-19-10").

---

### Post by wildmanne39 on 2020-07-25
> **pbear42 said:**
> FYI, how sudo works with GUI apps changed dramatically with version 19.10, carried forward into 20.04.  See [askubuntu]("https://askubuntu.com/questions/1186999/how-does-sudo-handle-home-differently-since-19-10").

Yes this is true, I think we have not mentioned it much here because there are many users still using the older but still supported versions of Ubuntu and I personally believe it will cause more confusion among users if they read sudo does not cause issues any longer with GUI applications because many new users will not pay attention to the fact that it is version specific until the older Ubuntu versions reach EOL.

This is good news especially when all older versions of Ubuntu reach EOL.

---

### Post by monkeybrain20122 on 2020-07-25
> **TheFu said:**
> Often, to see any GUI changes, a logout-login is needed.

**WARNING:**
Running almost all GUI programs using a root account or sudo is a bad idea..

+1. There is already enough abuse of sudo and su even in tutorials and blogs by people who should know better, the new users don't need the convenience to mess up the root system with a click.

---

### Post by TheFu on 2020-07-25
I see.  Much better.

```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 20.04.1 LTS
Release:        20.04
Codename:       focal

$ sudo env|grep HOME
HOME=/root

```
On 16.04```

$ sudo env|grep HOME
HOME=/u/thefu
```

If someone wants the old results (all sorts in the world), I'd bet the sudoers config has a way to control that. Good change, this is.

---


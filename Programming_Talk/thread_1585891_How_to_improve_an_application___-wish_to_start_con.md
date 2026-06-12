---
title: "How to improve an application  ? -wish to start contributing .."
date: 2010-10-01
forum: Programming Talk
---

### Post by Andre-D on 2010-10-01
I have an nice idea on how to improve tsclient application. (in Ubuntu)
To get me started I need to know how to do this properly:
-get sources for tsclient package,
-edit it (where to to editing - right in downloaded files)
-compile it so it replaces mine - for testing.

Thank you.

---

### Post by pbrane on 2010-10-01
you can get the source like this:
```

sudo apt-get source tsclient

```
This command will download the source to the current directory.

or to get the latest source
```

bzr get https://code.launchpad.net/~ubuntu-desktop/tsclient/ubuntu

```

We can't tell you what to edit in the source since we don't know what you what to improve.

Compiling should be
```

./configure --prefix=/usr
make
sudo make install

```
But I haven't got the source so I don't know exactly what the build mechanism is. If you are familiar with programming you will figure it out.

---

### Post by Andre-D on 2010-10-01
Than you.
I wish to make the automatic "reconnect on disconnect" optional.
some code changes, and extra GUI checkbox.

The reason is:
 if you disconnect from a server in a normal, controlled way - it still counts to 30s , then reconnects unless you press cancel.
- So I leave the office, and the office computer is RDP'ing a server.
- I get home, and RDP that server, - now the office computer gets kicked, then counts to 30s and kicks me by reconnecting :)

---

### Post by Zugzwang on 2010-10-01
Ok, then I would suggest you to perform the following steps:
[LIST=1]
[*]Read through the available documentation to find out about the structure of the project. Unfortunately, in many cases, for open source software, there is document explaining the "overall picture".
[*]Find out which parts of the code are relevant to your modification. See which libraries are involved and learn the basics about these libraries to make sure your changes don't break anything.
[*]Develop an idea how the part of the application must be changed in order to fulfill your goal. Think about which other parts might break.
[*]Implement and test
[/LIST]

---

### Post by Andre-D on 2010-10-01
I do have some programming experience from microprocessors , both x86 assembly, and Microchip 16 assembly (RISC). Plus I have been using/playing some high level languages like Basic,PHP,Python and LUA.   :)

Anyway: I saw:
dpkg-source: info: extracting tsclient in tsclient-0.150
dpkg-source: info: unpacking tsclient_0.150.orig.tar.gz
dpkg-source: info: applying tsclient_0.150-4ubuntu1.diff.gz

but I can't find where the sources are, locate does not seem to show anything new..  - I feel dumb :)

---

### Post by Zugzwang on 2010-10-01
> **Andre-D said:**
> but I can't find where the sources are, locate does not seem to show anything new..  - I feel dumb :)

"apt-get source" extracts these into the current directory (you do not need to and should not use the "sudo" for this command). The original compressed files you are writing about can for example be downloaded here: [http://packages.ubuntu.com/lucid/tsclient](http://packages.ubuntu.com/lucid/tsclient)

---

### Post by Andre-D on 2010-10-01
Yep, found them in my home folder.

tsclient_0.150.orig.tar.gz 
is self-explaining,  so is
tsclient_0.150-4ubuntu1.dsc

but how to use/what to do with the big diff file in 
tsclient_0.150-4ubuntu1.diff.gz 

I assume that's the modifications just for Ubuntu ? 
If I just work on tsclient_0.150.orig.tar.gz , then I won't have any of the Ubuntu related stuff - and whatever I compile will be much more different ?

Thank you all.

---

### Post by pbrane on 2010-10-01
I DL'd tsclient 2.0.1 from the sourceforge web site and it looks like the auto-reconnect policy is user configurable. You might try building that version and installing, see if that fixes your issue.

[http://sourceforge.net/projects/tsclient/]("http://sourceforge.net/projects/tsclient/")

And as far as I know the patch file is for ubuntu specific changes/bug fixes that you may or may not want to apply. You can always view the diff and see if the comments help.

---

### Post by Andre-D on 2010-10-04
it seems like it require gnome-desktop-2.0 and other packages I don't have - seems like I should wait..

---


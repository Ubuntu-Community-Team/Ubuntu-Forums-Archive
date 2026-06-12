---
title: "Source Code"
date: 2007-05-16
forum: Programming Talk
---

### Post by fornews on 2007-05-16
Sorry if this question is a bit simplistic but I've searched quite a bit with out great success.

I have Edgy installed on 386

I would like to have the source code for various commands such as top, etc.
Unfortunately searching for words such as 'top' make it extra difficult.

Pointers appreciated.

Jon

---

### Post by Tomosaur on 2007-05-16
This page has links to the source code for top specifically:

[http://directory.fsf.org/top.html](http://directory.fsf.org/top.html)

Many of the 'standard' Linux utilties are available in the 'coreutils' package. To grab the source for the coreutils, use this command:

```

apt-get source coreutils

```

---

### Post by WW on 2007-05-16
You can use the command **dpkg -S** to determine which package provides a file:
```

$ dpkg -S /usr/bin/top
procps: /usr/bin/top
$

```
This says that top is provded by the package **procps**.  To get the source code, you can get the package source with the command
```

$ apt-get source procps

```
This will fetch several files from the Ubuntu repository, with extensions .dsc, .tar.gz and .diff.gz. In dapper, the .dsc file is procps_3.2.6-2ubuntu4.dsc, and then extract the source code into a subdirectory. In this case, the subdirectory is called procps-3.2.6.

Or, now that you know that the package is procps, you can google a bit, or read the short blurb about the procps package in Synaptic, and find the web page [http://procps.sourceforge.net/](http://procps.sourceforge.net/) and download the source code from there.

---

### Post by lloyd_b on 2007-05-16
First, install the package "apt-file".  This allows you to easily find out which package a given command came from:
```
sudo apt-get install apt-file
```

Second, you need to initialize apt-file:
```
sudo apt-file update
```

Third, check the file "/etc/apt/sources.list", and make sure that the various "deb-src" lines are uncommented for each repository that is available.

Then, use apt-file to identify the package a command came from, and then use apt-get to retrieve the source code for that package.

For example, in the case of top.  First, find out where the actual command is:
```
lloyd@laptop:~$ which top
/usr/bin/top
```

Once you know this, use apt-file to identify the package it came from. Note: do NOT include the leading "/" - it's "usr/bin/top", not "/usr/bin/top":
```
lloyd@laptop:~$ apt-file search usr/bin/top
libwww-topica-perl: usr/bin/topica2mail
procps: usr/bin/top
tcpquota: usr/bin/topmasq
tcpquota: usr/bin/topnet
tcpquota: usr/bin/toptcp
topal: usr/bin/topal
```

Pick the one you want - in this case "procps", and use apt-get to retrieve the source:
```
lloyd@laptop:~$ sudo apt-get source procps
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Need to get 320kB of source archives.
Get:1 http://us.archive.ubuntu.com edgy/main procps 1:3.2.7-2ubuntu3 (dsc) [626B]
Get:2 http://us.archive.ubuntu.com edgy/main procps 1:3.2.7-2ubuntu3 (tar) [282kB]
Get:3 http://us.archive.ubuntu.com edgy/main procps 1:3.2.7-2ubuntu3 (diff) [37.2kB]
Fetched 320kB in 3s (83.3kB/s)
gpg: Signature made Fri 08 Sep 2006 06:45:47 AM MST using DSA key ID 5E0577F2
gpg: Can't check signature: public key not found
dpkg-source: extracting procps in procps-3.2.7
dpkg-source: unpacking procps_3.2.7.orig.tar.gz
dpkg-source: applying ./procps_3.2.7-2ubuntu3.diff.gz
```

There is now a subdirectory /usr/bin/procps_3.2.7, with the source code for all of the programs in that package.

(Personally, I wish that I could tell it to install the sources to "/usr/src" instead of "/usr/bin", but I haven't found an option do to this.).

Lloyd B.

---

### Post by trak87 on 2007-05-16
Is the following step necessary or are procps's dependencies automatically installed when the source is installed?

```
apt-get build-dep procps
```

---

### Post by WW on 2007-05-16
**apt-file** looks interesting.  I usually use **dpkg -S**, but that only works for files that are already installed.

By the way, according to my (admittedly very limited) experience, and according to **man apt-get**, the command **apt-get source package** downloads the files to the current directory (not to /usr/bin).   

If you are in your home directory, or in, say, /tmp, you do not need sudo to run the command.

trak87: You don't need that to simply download the source, but if you want to compile it, then yes, you can use **apt-get build-dep** to install the build dependencies.

---

### Post by fornews on 2007-05-16
> **Tomosaur said:**
> This page has links to the source code for top specifically:

[http://directory.fsf.org/top.html](http://directory.fsf.org/top.html)


Thank you.

> **Tomosaur said:**
> 
Many of the 'standard' Linux utilties are available in the 'coreutils' package. To grab the source for the coreutils, use this command:

```

apt-get source coreutils

```

I should have guessed that given this is Open Source... 
Though I probably would not have guessed coreutils.

Much appreciated

---

### Post by FuturePast on 2007-05-16
You do not need to do [COLOR="Red"]sudo[/COLOR] apt-get source

---

### Post by WW on 2007-05-16
> **fornews said:**
> 
Though I probably would not have guessed coreutils.

That's OK, because it is not in coreutils. It is in **procps** (see my first post in this thread).

---

### Post by fornews on 2007-05-16
> **WW said:**
> That's OK, because it is not in coreutils. It is in **procps** (see my first post in this thread).

And you're also correct that it will place the source in PWD.

Thanks all !!

Now let me ask everyone another question...

Included in procpcs (path ~/procps-3.2.7/proc) is sysinfo.c 
and I'd like to invoke a function in sysinfo.c from a separate
c file that is not part of the this procps package. I guess another
way to put it.. I want to use an existing function in sysinfo.c in another
unrelated piece of c code.  I've tried the obvious approach of 
-l/ExplicitPath/procps-3.2.7/proc/libproc-3.2.7.so and
-l/ExplicitPath/procps-3.2.7/proc/sysinfo.o with gcc and it keeps
saying they can't be found but they're there and permissions are
open enough.

TIA.

Jon

---

### Post by FuturePast on 2007-05-16
It should be:
-lproc -L/blah/procps-3.2.7

or
gcc myfile.c /ExplicitPath/procps-3.2.7/proc/sysinfo.o

---

### Post by lloyd_b on 2007-05-16
> **WW said:**
> **apt-file** looks interesting.  I usually use **dpkg -S**, but that only works for files that are already installed.

By the way, according to my (admittedly very limited) experience, and according to **man apt-get**, the command **apt-get source package** downloads the files to the current directory (not to /usr/bin).   

If you are in your home directory, or in, say, /tmp, you do not need sudo to run the command.


My error - I was in the /usr/bin directory when I was testing "apt-get source" - and since it game me an error, I ran it again with "sudo".

So, "apt-get source" will download in the current directory, failing if you don't have the required permissions. 

As for "apt-file" vs "dpkg -S", I believe that "dpkg -S" is somewhat faster, so long as the package is already installed on your machine.  I'm just more used to "apt..." commands than "dpkg" commands.

Lloyd B.

---


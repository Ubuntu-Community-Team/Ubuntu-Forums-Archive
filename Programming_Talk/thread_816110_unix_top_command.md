---
title: "unix top command"
date: 2008-06-02
forum: Programming Talk
---

### Post by GregoryPitts on 2008-06-02
Can anyone give me a detailed description of how the top command is actually implemented? I can't seem to find any documentation on it. A link to the source or a path to the source would be fine. Thanks.

Greg

---

### Post by hermes0710 on 2008-06-02
Hi,
  check these:
[http://linux.about.com/od/commands/l/blcmdl1_top.htm]("http://linux.about.com/od/commands/l/blcmdl1_top.htm")
[http://unixhelp.ed.ac.uk/CGI/man-cgi?top+1]("http://unixhelp.ed.ac.uk/CGI/man-cgi?top+1")

---

### Post by GregoryPitts on 2008-06-02
Thanks. I was looking for something more than the man pages. I found the source here, in case anyone is wondering

[http://procps.sourceforge.net/](http://procps.sourceforge.net/)

---

### Post by geirha on 2008-06-02
If it's gpl, ubuntu has to make the source code available to you, and they do that using apt:

```

$ which top             # Find the absolute path of the file
/usr/bin/top
$ dpkg -S /usr/bin/top  # Find the package the file is installed by
procps: /usr/bin/top
$ apt-get source procps # Download the source 
[...cut...]
dpkg-source: extracting procps in procps-3.2.7
dpkg-source: unpacking procps_3.2.7.orig.tar.gz
dpkg-source: applying ./procps_3.2.7-5ubuntu2.diff.gz

```

I find this procedure a little easier than searching for the source on google. For next time ;)

---


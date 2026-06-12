---
title: "Erlang-package, wx application missing?"
date: 2010-05-08
forum: Programming Talk
---

### Post by Jens_Li on 2010-05-08
Hi,

Ive installed the Erlang package from the repository, it works like a charm. But I dont seem to be able to run the wx gui application.

```

1> wx:demo().
** exception error: undefined function wx:demo/0
2> m(wx).
** exception error: undefined function wx:module_info/0
     in function  c:m/1

```

The erlang source code of wx is pressent in /usr/lib/erlang/lib/wx-0.98.2/src/, but I dont see any beam files, and no c source or binaries. There are sub packages for diffrent erlang applications in the repository which I also have installed, but I dont see one for wx.

Anyone know if there is a problem with wx in the erlang package?

Anyone has got wx to run under Ubuntu? What did you have to do? Download and compile wx manually? Compile the whole of OTP manually?


Thanks,
/Jens

---

### Post by gliptak on 2010-05-16
This is discussed at [https://bugs.launchpad.net/ubuntu/+source/erlang/+bug/438365]("https://bugs.launchpad.net/ubuntu/+source/erlang/+bug/438365")

---

### Post by alep on 2010-05-17
I manually compiled my version of the whole OTP, installed it in /opt/erlang with ./configure --prefix=/opt/erlang. Then added to my .bashrc the following export PATH=/opt/bin/erlang:$PATH. I put /opt/bin/erlang first so when I run "erl" it finds the executable in /opt/ and not the one in /usr/lib/erlang (which is the one that the package manager installs).

If you can figure out a way to only compile wx that would be great, so I don't have to do this which I find very ugly indeed.

---

### Post by cprofitt on 2010-08-01
I wonder if Fedora does a better job of this.

---


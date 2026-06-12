---
title: "Photoprint can't find gutenprint"
date: 2012-07-19
forum: New to Ubuntu
---

### Post by vbonafe on 2012-07-19
Hello everyone! This looks like an old bug (as you can see in [here]("http://ubuntuforums.org/showthread.php?t=1010194")) but I the cause is differente. I found a workarround and I'm writing to share it.

I installed Photoprint in Ubuntu 12.04 but when I run it, it shows this error message:

```
photoprint: error while loading shared libraries: libgutenprint.so.2: cannot open shared object file: No such file or directory
```

I checked that gutenprint is already installed, but it looks like the version changed. When I try the find command, here's what I get:

```
victor@devmobile:~$ sudo find / -name libgutenprint.so.*
/usr/lib/i386-linux-gnu/libgutenprint.so.3.0.0
/usr/lib/i386-linux-gnu/libgutenprint.so.3
```

So I soft linked this file using the expected name:

```
sudo ln -s /usr/lib/i386-linux-gnu/libgutenprint.so.3 /usr/lib/i386-linux-gnu/libgutenprint.so.2
```

It works fine and photoprint is now in action.

My question is: should I register it as a bug in Ubuntu or in Photoprint?

Regards!

---

### Post by richpri on 2012-07-19
According to Synaptic, Photoprint is not supported by Ubuntu.
So I suggest you report the error as a Photoprint bug.

---

### Post by NoOp on 2012-10-02
@vbonafe: Thanks. That workaround works for me. 

Unfortunately the issue is a Photoprint regression & hopefully it will be fixed rather than users having to do workarounds. Please see:
<https://bugs.launchpad.net/ubuntu/+source/photoprint/+bug/260849>

@richpri:
According to all things Ubuntu, Photoprint *is* supported by Ubuntu:
<https://launchpad.net/ubuntu/+source/photoprint>
<http://packages.ubuntu.com/search?searchon=names&keywords=photoprint>

My version of synaptic shows photprint just fine:
$ apt-cache policy synaptic
synaptic:
  Installed: 0.75.9ubuntu1
  Candidate: 0.75.9ubuntu1
  Version table:
 *** 0.75.9ubuntu1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe i386 Packages
        100 /var/lib/dpkg/status
Perhaps you've forgotten to include the universe repository?

---


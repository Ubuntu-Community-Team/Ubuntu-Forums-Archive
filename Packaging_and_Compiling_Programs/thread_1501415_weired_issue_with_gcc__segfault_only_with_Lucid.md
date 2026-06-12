---
title: "weired issue with gcc / segfault only with Lucid"
date: 2010-06-04
forum: Packaging and Compiling Programs
---

### Post by Phocean on 2010-06-04
Hi all,

I am facing a very weired issue.
I spent hours checking my code to finally realize that it was segfaulting only on my laptop with Ubuntu Lucid 64bits.

There it is :
[http://codepad.org/6AONdrtC](http://codepad.org/6AONdrtC)

And the debug session with it :
[http://codepad.org/NlNTacTy](http://codepad.org/NlNTacTy)

As you can see, it is very simple (even though it might look dirty because I cut off useless parts for the issue and made a lot of testing).

It compiles allright (gcc test.c -o test) but when I run it:
```

% ./test example.com 80
toto
phocean.net
resolv: phocean.net
zsh: segmentation fault  ./test phocean.net 80
```

Debug session shows that the resolv function is working as expected, but something on the stack gets crafted and it is unable to return to the main section.

The weired thing is that it compiles and works very well on all others distro I had as virtual machines : Fedora 13 32bits & 64bits, openSUSE 11.2 64bits and Debian 5 32bits.
I also took the binary from one of these VM and ran it on Ubuntu, and it worked.
Does it mean it is an issue with gcc or the libc ?

My programing knowledge is limited so I don't know how to advance on this.


Any idea ? Does it also segfaults on your machine ?
And if it is a bug, how can I dig more to point out the culprit ?

Thanks in advance.

**UPDATE** : added strace :
[http://codepad.org/CIyNCyR6](http://codepad.org/CIyNCyR6)

error in /var/log/messages :
kernel: [81039.332829] test[25870]: segfault at 7fff6d799f39 ip 000000000040077f sp 00007fff7b852b40 error 6 in test[400000+1000]

---

### Post by Phocean on 2010-06-05
If somehow happened to have the same issue, bug reported and confirmed there :
[https://bugs.launchpad.net/ubuntu/+source/gcc-4.4/+bug/589855](https://bugs.launchpad.net/ubuntu/+source/gcc-4.4/+bug/589855)

---


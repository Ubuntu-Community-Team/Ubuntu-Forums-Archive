---
title: "warning: GDB: Failed to set controlling terminal: Operation not permitted"
date: 2012-05-11
forum: Programming Talk
---

### Post by jiangshi on 2012-05-11
Greetings!

Here is the trouble maker:
warning: GDB: Failed to set controlling terminal: Operation not permitted

Here is the issue: I am getting the above error, and it is preventing the marker kdbg that shows what line of code is to be executed next. 

In looking for a solution I found that this error is plastered all over the Internet, yet no one seems to have found a solution. This error occurs no only in Ubuntu, but other distros as well, such as Suse and Fedora. It occurs when using Netbeans and other IDEs. It does not seem to make any difference what programming language is being used.

In my case specifically, I am using Xubuntu 12.04 32bit fully updated on an old Dell Dimension 2400. I am writing in assembly language using the NASM assembler. I am using kdbg as the debugger (frontend).

Here is the kicker - I have received this error while using Fedora, and generally if I reassemble the source and reload the executable, the error goes away and kdbg works fine.

I would very much appreciate some light on this issue.

Thanky you!
~jiangshi

---

### Post by Arndt on 2012-05-11
> **jiangshi said:**
> Greetings!

Here is the trouble maker:
warning: GDB: Failed to set controlling terminal: Operation not permitted

Here is the issue: I am getting the above error, and it is preventing the marker kdbg that shows what line of code is to be executed next. 

In looking for a solution I found that this error is plastered all over the Internet, yet no one seems to have found a solution. This error occurs no only in Ubuntu, but other distros as well, such as Suse and Fedora. It occurs when using Netbeans and other IDEs. It does not seem to make any difference what programming language is being used.

In my case specifically, I am using Xubuntu 12.04 32bit fully updated on an old Dell Dimension 2400. I am writing in assembly language using the NASM assembler. I am using kdbg as the debugger (frontend).

Here is the kicker - I have received this error while using Fedora, and generally if I reassemble the source and reload the executable, the error goes away and kdbg works fine.

I would very much appreciate some light on this issue.

Thanky you!
~jiangshi

How can the problem be reproduced?

---

### Post by zabsv on 2012-07-04
I'm suffering from the same problem. 

There is a bug report with information on how to reproduce it at 
[https://bugs.launchpad.net/ubuntu/+source/netbeans/+bug/469005](https://bugs.launchpad.net/ubuntu/+source/netbeans/+bug/469005)

Any suggestions on how to solve this would be greatly appreciated since it's quite a pain when debugging doesn't work.

---


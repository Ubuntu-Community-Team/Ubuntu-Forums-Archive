---
title: "cvsservice &amp; cervisia"
date: 2006-09-25
forum: Programming Talk
---

### Post by peibol on 2006-09-25
Hi there, I'm having problems making cervisia work, apparently it has some problems with the cvsservice working with dcop, I'm getting this message whenever i try to open a repository:

# cervisia
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
DCOPRef: call 'cvsCommand()' on null reference error
WARNING: DCOPReply<>: cast to 'QString' error

next thing is cervisia just stops working... well.. actually it hasnt yet worked properly.

This are the installed versions of everything: 
cervisia 4:3.5.2-0ubuntu3
cvs: 1:1.12.9-17
cvsservice: libcvsservice0: 4:3.5.2-0ubuntu3

"cvsservice -v" output:
Qt: 3.3.6
KDE: 3.5.2
CVS DCOP service: 0.1

Any help will be greatly appreciated.

Regards.
Pablo Carranza.

---


---
title: "Making a dialup modem kernel module from outdated Redhat source package"
date: 2007-05-22
forum: Packaging and Compiling Programs
---

### Post by soliac on 2007-05-22
I'm trying to make a loadable kernel module for my dialup modem: a BCM V.92 winmodem. Broadcom released a Redhat driver a few years ago, but it was for the 2.4 Linux kernel.
[The (Redhat) source package is here]("http://support.us.dell.com/support/downloads/download.aspx?c=us&cs=04&l=en&s=bsd&releaseid=R47114&formatcnt=1&libid=0&fileid=55543"). Inside it there is, among other things, a file called "BCMSM_lib.o". How do I make a module called BCMSM.ko from that???
Attached is the contents of Broadcom's source package.

---

### Post by magicfab on 2007-05-23
What is Broadcom saying about this ? Let them know you need to use their hardware in Ubuntu, sometimes you may get more / better information about solving your problem with them directly. I know it sound obvious but many times we assume a manufacturer won' t cooperate - although I can't vouch for Broadcom personally.

---


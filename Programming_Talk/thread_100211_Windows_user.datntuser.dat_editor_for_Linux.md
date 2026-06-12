---
title: "Windows user.dat/ntuser.dat editor for Linux"
date: 2005-12-07
forum: Programming Talk
---

### Post by jatos on 2005-12-07
Right I am currently thinking of writing a program that allows people to editor the user.dat and ntuser.dat files, which are used to store the Windows registry settings for individual users of a windows system. On a network with a nt logon server, these files can be put in the users logon home or logon path as appropiate to give the user a "roaming profile". The program would be aimed at people who use Samba as an nt logon server, and the program would allow creation and editing of a user roaming registry data on the Linux server samba server. 

My question is, do people here think a program would be of use, and does anyone here know of any potential legal issues.

---

### Post by hrobky on 2008-09-05
Have you already done it? I really need it for the purpose you were writing about :) It would be great, if it were command line utility.

For syntax inspiration I recommend you SetACL windows utility ([http://setacl.sourceforge.net/](http://setacl.sourceforge.net/))

For now, it would be enough just to edit the content (not ACLs) of registry database hive provided in specific file.

Or does anybody know how to edit hive files (ntuser.dat) under linux? Or maybe a Windows command line utility which run under wine.

---


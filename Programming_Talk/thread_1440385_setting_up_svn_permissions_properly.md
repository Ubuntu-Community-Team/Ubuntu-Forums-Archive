---
title: "setting up svn permissions properly"
date: 2010-03-27
forum: Programming Talk
---

### Post by badperson on 2010-03-27
Hi,
I have a home network, and I want to host an svn server on the machine I'm using as a server. 
I have svn installed, and I have a repo created, and I am able to start the server with: 

> sudo svnserve -d --foreground -r /code/svnrepo


but when trying to import some files into the repo (files are located on client machine, and I'm entering the import command from the client) I get this:

> user@user-desktop:/$ sudo svn import media/files/code/perl svn+ssh://user@<ip addr>/code/svnrepo -m "initial import"
user@<ip>'s password: 
Adding         media/files/code/perl/write-classpath.pl
Adding         media/files/code/perl/get-plural.pl
Adding         media/files/code/perl/lwp-test.pl
Adding         media/files/code/perl/music-backup.pl
Adding         media/files/code/perl/view-classpath.pl
Adding         media/files/code/perl/goal-writer.pl
svn: Can't open file '/code/svnrepo/db/txn-current-lock': Permission denied


when I uncomment the line in the svnserve.conf file:

> password-db = /pswd file


I get this: > svn: Authentication failed


in the psswd file that the *.conf file refers to, what user/pw information should be stored there? 

the client user/pw? 
thanks, 
bp

---

### Post by not_a_phd on 2010-03-28
Not sure about the file permissions issue that you are running into. 

There should be a conf directory within each repository that you set up. In the conf directory, you should find a passwd file. This has a list of usernames and passwords in plaintext that svn will authenticate for that repository.

---

### Post by badperson on 2010-04-13
got it...just had to chown the svn repo and change permissions
bp

---


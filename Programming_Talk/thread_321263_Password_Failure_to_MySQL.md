---
title: "Password Failure to MySQL"
date: 2006-12-18
forum: Programming Talk
---

### Post by theDentist on 2006-12-18
Some help me please, for some reason I cannot access MySQL, my password is being denied, how do I get into it to correct the problem as I'm not allowed access!! Is there anyway to put the installation back to defaults to gain access, I only had one user on it, me!  ](*,)

---

### Post by theDentist on 2006-12-19
More info on my last post,  I was using MySQLCC graphical user interface , something I did must of corrupted my password,  I didn't think passwords could be edited in MySQLCC.  I certainly wasn't obvious to me.      :-?

---

### Post by welshboy on 2006-12-19
Hi there dentist,

Sorry to hear you're having trouble.

This may be a dumb question, but have you tried logging in using the command line 

mysql -u username -p

and then entering your password at the prompt?  Or are you only using the GUI you described.

As it could be the GUI's gone nuts or something like that.

again, sincere apologies if this is a dumb question

---

### Post by theDentist on 2006-12-20
Yes, I did all my configuring at the command prompt, I only launched MySQLCC out of curiousity to see what it was like , big mistake!!.  The Access failure is doing what it supposed to, prevent unauthorised use, shame it's working against me.  I thought logging in as root (not  mysql's root user) on the computer would give me complete control of everything, obviously not, the mysql files are locked to me, even as root.  I tried uninstalling and reinstalling mysql but to my surprise when you reinstall something it unpacks the same package, plus configuration, of the previously uninstalled version, shame as I can't get a fresh install.  I'm going round in circles here.  I did try the --skip-grant-tables command but it informs me that a file is locked and there is someone else  using. this is rubbish as nothing on my computer is using it. it is localhost only, and just one user  - me.  I dread the thought the only way is reformat and a fresh installation of Unbuntu - NO!!!!.    :( .  So I have a database I can never use on this computer.  I didn't think you could change a password without an explicit command to do so.

Oh well, that's life, a learning curve! My advice to all make sure you have more than one user on your databases you can access

---

### Post by welshboy on 2006-12-20
I had that hassle with Tomcat, however isn't there an option that you can completely remove the program and it's configuration files?  I know that's the case in synaptic.

---

### Post by theDentist on 2006-12-20
You can use the --purge option with the remove command that suppose to remove all the configuration files, I tried it, but my computer still remembered me,  All suggestions gratefully received, but I've just had to resign myself to it    :-? 

Peter

---

### Post by theDentist on 2006-12-20
Just to let everyone know, I took welshboy's advice and looked at Synaptic.  I uninstalled everything, mysql client and server, using the total uninstall option i.e. configuration files as well.  I then reinstalled through Synaptic and GUESS WHAT! mysql still remembers me, Oh it is so good to be popular!!    :mad:     I have lost my MySQL forever!

mournfully yours 
Peter

---

### Post by rat1000 on 2006-12-22
I'm having this exact same problem.  I followed the instructions on the mysql dev page, and I also tried removing mysql client and server and reinstalling, but nothing has worked.  I was thinking maybe it remembered my information because I left mysql common files because of dependencies.  Is there a way to force removal of the package without also removing the other programs?

---

### Post by rat1000 on 2006-12-26
This link solved the problem.  My my.conf file was empty so I set it like the one here, followed the steps, and was able to reset my root password.  

[http://help.hardhathosting.com/question.php/200](http://help.hardhathosting.com/question.php/200)

---

### Post by lloyd mcclendon on 2006-12-26
since you've got that restored, you'll probably want to login as root and type

GRANT ALL PRIVILEGES ON *.* to yourUserName@localhost IDENTIFIED BY 'somePassword';

then you can do mysql -p (as yourself), type in the password and you're in

mysql sucks i wish there was a better free alternative that was as widely supported

---

### Post by theDentist on 2007-01-30
Hi all it's been awhile but thanks for all your advice it worked!!!!    :D

---


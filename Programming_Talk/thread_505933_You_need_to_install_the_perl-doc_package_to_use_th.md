---
title: "You need to install the perl-doc package to use this program."
date: 2007-07-20
forum: Programming Talk
---

### Post by superhaus on 2007-07-20
I am trying to learn Perl with the O'Reilly Learning Perl book, and one of the first exercises involves the command 
```
perldoc -u -f atan2
```

I get the response:
```
You need to install the perl-doc package to use this program.
```

I searched the Add/Remove programs app for perl-doc and nothing came up. I tried perldoc and only Pod Browser came up. I installed Pod Browser to see if that would help, but I still get the same error.

Any suggestions?

---

### Post by sisco311 on 2007-07-20
```
sudo aptitude install perl-doc
```

---

### Post by blong on 2009-01-04
I am having the same problem. 

I tried the suggested solution:
>```
sudo aptitude install perl-doc
```

The terminal listed a status report of an install.  It looked like it worked, but the original problem persisted.

I've got two folders of perl, 5.10 and 5.10.0.  I'm pretty sure these came with my Ubuntu 8.10.

Out of curiosity, does the current directory matter when running commands like ```
install
``` from the terminal?

---

### Post by DarkStarHarry on 2009-01-27
it worked for me. Thanks for helping a n00b.

DSH

---

### Post by BradleyAtkins on 2010-08-15
I have two ubuntu machines, 1 is a laptop and this install of perl docs was successful.

The other is a server running an older version of ubuntu, I don't know what version. On this machine the install failed: -

```
poweredge:/home/brad/perl_stuff/sockets>sudo aptitude install perl-doc
[sudo] password for brad: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
The following NEW packages will be installed:
  perl-doc 
0 packages upgraded, 1 newly installed, 0 to remove and 64 not upgraded.
Need to get 8207kB of archives. After unpacking 14.1MB will be used.
Writing extended state information... Done
Err http://gb.archive.ubuntu.com intrepid-updates/main perl-doc 5.10.0-11.1ubuntu2.2
  404 Not Found
Err http://security.ubuntu.com intrepid-security/main perl-doc 5.10.0-11.1ubuntu2.2
  404 Not Found [IP: 91.189.88.37 80]
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/perl/perl-doc_5.10.0-11.1ubuntu2.2_all.deb: 404 Not Found [IP: 91.189.88.37 80]
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
```

Am I right in thinking it could not find a package for my servers version of ubuntu?

If so what can I do to resolve this?

Thanks in advance

---

### Post by shawnhcorey on 2010-08-15
You can install perl-doc using the Synaptic Package Manager.

System -> Administration -> Synaptic Package Manager

Type "perl-doc" in the Quick Search.

Also, you might want to install "build-essential" while you're at it.  This package contains applications to compile C programs.

Once you get it installed, in a terminal type:

```
perldoc perldoc
```

This tells you how to use perldoc.

```
perldoc perl
```

This gives you a table of contents of the perldocs.

```
perldoc perlmodlib
```

This gives you a listing of all the pragmatics and modules install with Perl.

---

### Post by BradleyAtkins on 2010-08-16
Sorry I guess I didn't make myself clear, its the server I cannot get the install to work. 

I don't think I can run a desktop on it. 

If that's possible I don't know how to do it. I usually log in via a terminal emulator.

---

### Post by shawnhcorey on 2010-08-16
Are your software sources valid?  What's in /etc/apt/sources.list ?

---


---
title: "Help with Installing Perl"
date: 2011-09-13
forum: Packaging and Compiling Programs
---

### Post by seabiscuit on 2011-09-13
Hi (I have also asked this in the general help section unfortunately nobody answered so far :( ),

I run ubuntu64 (Description:    Ubuntu 10.04.2 LTS, Release:    10.04,Codename:    lucid)

I need to install an older version of Perl : perl 5.10.0 as my current  perl version (5.10.1) is not compatible with some software I need to  use; 5.10.0 is.

I have never installed perl from the command line: ie using a tar file  such as perl-5.10.0.tar.gz and I would highly appreciate the experts'  help.

I did download from [http://www.cpan.org/src/5.0/](http://www.cpan.org/src/5.0/)  the perl-5.10.0.tar.gz file and I would be very grateful if somebody  can provide me with step-by-sep instructions (commands I need to run) so  that I get that version installed.

Thank you very much!

---

### Post by agillator on 2011-09-13
1. cd to the directory where you wish it to be located (eg /usr/local).
2. sudo tar zxvf /path/to/perl-5.10.0.tar.gz
3. To make it easily executable, sudo ln -s /path/to/perl/executable /usr/local/bin/perl
You might want to check ownerships, modes, etc., but those should be ok without you doing anything. If there is a problem, check those first. If some programs work and some don't, check the 'shebang' at the beginning of the script that runs the problem program (if there is one). For your setup it should read #!/usr/bin/perl. Also be sure you do not have another version of perl named the same. You may use more than  one version but the names must be different and they must be called properly. Note that in my experience PERL is backwards compatible, i.e. later versions run programs/scripts written for earlier versions with no problem. Are you sure that is your problem?

---

### Post by seabiscuit on 2011-10-14
> **agillator said:**
> 1. cd to the directory where you wish it to be located (eg /usr/local).
2. sudo tar zxvf /path/to/perl-5.10.0.tar.gz
3. To make it easily executable, sudo ln -s /path/to/perl/executable /usr/local/bin/perl
You might want to check ownerships, modes, etc., but those should be ok without you doing anything. If there is a problem, check those first. If some programs work and some don't, check the 'shebang' at the beginning of the script that runs the problem program (if there is one). For your setup it should read #!/usr/bin/perl. Also be sure you do not have another version of perl named the same. You may use more than  one version but the names must be different and they must be called properly. Note that in my experience PERL is backwards compatible, i.e. later versions run programs/scripts written for earlier versions with no problem. Are you sure that is your problem?

Thank you for your advice and excuse the latency in replying.

Yes, I am dealing with something that is not backward compatible unfortunately.

I have tried to use the advice above and executed on the steps 1) and 2) above.

I get stuck in step 3: where is the perl/executable? All I got after 2. was a directory perl-5.10.0  with a bunch of files, ansd subdirectories ...should I compile something? If yes, I would appreciate detailed instructions as I have never done this...

---

### Post by seabiscuit on 2011-10-15
> **seabiscuit said:**
> Thank you for your advice and excuse the latency in replying.

Yes, I am dealing with something that is not backward compatible unfortunately.

I have tried to use the advice above and executed on the steps 1) and 2) above.

I get stuck in step 3: where is the perl/executable? All I got after 2. was a directory perl-5.10.0  with a bunch of files, ansd subdirectories ...should I compile something? If yes, I would appreciate detailed instructions as I have never done this...

I have finally got it working after running the following commands in the perl directory that resulted from doing 1. and 2. above

sh Configure -de
    make
    make test
    make install

PS: these are also detailed in the "INSTALL" file that is created after 2. above

I realize that those might be considered trivial for many of this forum's reader, I post this here just in case there exist other "lost" people like me ...

---


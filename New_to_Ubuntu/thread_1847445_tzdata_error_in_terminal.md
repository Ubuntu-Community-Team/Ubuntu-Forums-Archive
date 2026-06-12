---
title: "tzdata error in terminal"
date: 2011-09-20
forum: New to Ubuntu
---

### Post by ajsoulmate on 2011-09-20
Hi,

Ubuntu 10.04 on HP Pavilion dv5. I’m stuck with an error message and I have no idea how to fix it. I have tried several things but obviously nothing helped to fix my problem.
I was searching on [www.googlubuntu.com](www.googlubuntu.com) and found many threads but 95% are OLD threads and UNSOLVED threads.
I haven’t changed anything, all what I was trying to install is:

```
sudo apt-get install pidgin pidgin-data pidgin-lastfm pidgin-guifications msn-pecan pidgin-musictracker pidgin-plugin-pack pidgin-theme

```

This is the output from terminal:


```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libavcodec52 libavformat52 libavutil49 libpostproc51 libswscale0
5 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 2,941kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ lucid-updates/main libavutil49 4:0.5.1-1ubuntu1.2 [66.0kB]
Get:2 http://archive.ubuntu.com/ubuntu/ lucid-updates/main libavcodec52 4:0.5.1-1ubuntu1.2 [2,204kB]
Get:3 http://archive.ubuntu.com/ubuntu/ lucid-updates/main libavformat52 4:0.5.1-1ubuntu1.2 [372kB]
Get:4 http://archive.ubuntu.com/ubuntu/ lucid-updates/main libpostproc51 4:0.5.1-1ubuntu1.2 [124kB]
Get:5 http://archive.ubuntu.com/ubuntu/ lucid-updates/main libswscale0 4:0.5.1-1ubuntu1.2 [175kB]
Fetched 2,941kB in 14s (201kB/s)                                               
debconf: Perl may be unconfigured (Can't locate loadable object for module Fcntl in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/lib/perl/5.10/DynaLoader.pm line 161
BEGIN failed--compilation aborted at /usr/lib/perl/5.10/Fcntl.pm line 161.
Compilation failed in require at /usr/lib/perl/5.10/IO/Seekable.pm line 12.
BEGIN failed--compilation aborted at /usr/lib/perl/5.10/IO/Seekable.pm line 12.
Compilation failed in require at /usr/lib/perl/5.10/IO/File.pm line 11.
BEGIN failed--compilation aborted at /usr/lib/perl/5.10/IO/File.pm line 11.
Compilation failed in require at /usr/share/perl/5.10/FileHandle.pm line 9.
Compilation failed in require at (eval 1) line 3.
BEGIN failed--compilation aborted at (eval 1) line 3.
) -- aborting
Setting up tzdata (2011j-0ubuntu0.10.04) ...
Can't locate loadable object for module Fcntl in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/share/perl/5.10/Carp.pm line 161
BEGIN failed--compilation aborted at /usr/lib/perl/5.10/Fcntl.pm line 161.
Compilation failed in require at /usr/lib/perl/5.10/POSIX.pm line 19.
BEGIN failed--compilation aborted at /usr/lib/perl/5.10/POSIX.pm line 19.
Compilation failed in require at /usr/share/perl5/Debconf/Template.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Template.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Question.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Question.pm line 8.
Compilation failed in require at /usr/share/perl5/Debconf/Config.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Config.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10.
Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7.
Compilation failed in require at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing tzdata (--configure):
 subprocess installed post-installation script returned error exit status 9
Errors were encountered while processing:
 tzdata
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

 I have removed all pidgin PPA from my system using Synaptic but that did not fix the issue. I haved changed the server to "Main" from Synaptic but nothing changed. I have changed my location to another country and rebooted but also that did not fix my issue.

Long story short, HELP ME!

Thank you!

---

### Post by alphacrucis2 on 2011-09-20
The error doesn't appear to be anything to do with tzdata (that is just a side effect). Your problem is that there is something wrong with the perl package.


```
debconf: Perl may be unconfigured
```


Try 

```
sudo dpkg --configure -a
```

---

### Post by ajsoulmate on 2011-09-20
> **alphacrucis2 said:**
> The error doesn't appear to be anything to do with tzdata (that is just a side effect). Your problem is that there is something wrong with the perl package.


```
debconf: Perl may be unconfigured
```


Try 

```
sudo dpkg --configure -a
```


```

Setting up man-db (2.5.7-2ubuntu1) ...
Can't locate loadable object for module Fcntl in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/share/perl/5.10/Carp.pm line 161
BEGIN failed--compilation aborted at /usr/lib/perl/5.10/Fcntl.pm line 161.
Compilation failed in require at /usr/lib/perl/5.10/POSIX.pm line 19.
BEGIN failed--compilation aborted at /usr/lib/perl/5.10/POSIX.pm line 19.
Compilation failed in require at /usr/share/perl5/Debconf/Template.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Template.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Question.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Question.pm line 8.
Compilation failed in require at /usr/share/perl5/Debconf/Config.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Config.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10.
Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7.
Compilation failed in require at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 9
Setting up tzdata (2011j-0ubuntu0.10.04) ...
Can't locate loadable object for module Fcntl in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/share/perl/5.10/Carp.pm line 161
BEGIN failed--compilation aborted at /usr/lib/perl/5.10/Fcntl.pm line 161.
Compilation failed in require at /usr/lib/perl/5.10/POSIX.pm line 19.
BEGIN failed--compilation aborted at /usr/lib/perl/5.10/POSIX.pm line 19.
Compilation failed in require at /usr/share/perl5/Debconf/Template.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Template.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Question.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Question.pm line 8.
Compilation failed in require at /usr/share/perl5/Debconf/Config.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Config.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10.
Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7.
Compilation failed in require at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing tzdata (--configure):
 subprocess installed post-installation script returned error exit status 9
Setting up ufw (0.30pre1-0ubuntu2) ...
Can't locate loadable object for module Fcntl in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/share/perl/5.10/Carp.pm line 161
BEGIN failed--compilation aborted at /usr/lib/perl/5.10/Fcntl.pm line 161.
Compilation failed in require at /usr/lib/perl/5.10/POSIX.pm line 19.
BEGIN failed--compilation aborted at /usr/lib/perl/5.10/POSIX.pm line 19.
Compilation failed in require at /usr/share/perl5/Debconf/Template.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Template.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Question.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Question.pm line 8.
Compilation failed in require at /usr/share/perl5/Debconf/Config.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Config.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10.
Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7.
Compilation failed in require at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing ufw (--configure):
 subprocess installed post-installation script returned error exit status 9
Setting up cups-bsd (1.4.3-1ubuntu1.5) ...
Can't locate loadable object for module Fcntl in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/share/perl/5.10/Carp.pm line 161
BEGIN failed--compilation aborted at /usr/lib/perl/5.10/Fcntl.pm line 161.
Compilation failed in require at /usr/lib/perl/5.10/POSIX.pm line 19.
BEGIN failed--compilation aborted at /usr/lib/perl/5.10/POSIX.pm line 19.
Compilation failed in require at /usr/share/perl5/Debconf/Template.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Template.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Question.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Question.pm line 8.
Compilation failed in require at /usr/share/perl5/Debconf/Config.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Config.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10.
Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7.
Compilation failed in require at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing cups-bsd (--configure):
 subprocess installed post-installation script returned error exit status 9
Setting up cups (1.4.3-1ubuntu1.5) ...
Can't locate loadable object for module Fcntl in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/share/perl/5.10/Carp.pm line 161
BEGIN failed--compilation aborted at /usr/lib/perl/5.10/Fcntl.pm line 161.
Compilation failed in require at /usr/lib/perl/5.10/POSIX.pm line 19.
BEGIN failed--compilation aborted at /usr/lib/perl/5.10/POSIX.pm line 19.
Compilation failed in require at /usr/share/perl5/Debconf/Template.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Template.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Question.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Question.pm line 8.
Compilation failed in require at /usr/share/perl5/Debconf/Config.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Config.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10.
Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7.
Compilation failed in require at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing cups (--configure):
 subprocess installed post-installation script returned error exit status 9
Errors were encountered while processing:
 man-db
 tzdata
 ufw
 cups-bsd
 cups
```

---

### Post by alphacrucis2 on 2011-09-20
Seems something has gone missing on your system


```
Can't locate loadable object for module Fcntl in @INC
```

If it is part of perl you might be able to get it back by downloading the perl package from here (I'm assuming that you are running Lucid according to your avatar - if not download the package for your version and architecture (32 or 64 bit)

[http://packages.ubuntu.com/lucid/perl]("http://packages.ubuntu.com/lucid/perl")

cd to wherever you downloaded the package then install the downloaded package via:

**sudo dpkg -i perl_5.10.1-8ubuntu2.1_amd64.deb** (or whatever the package appropriate for your version was called)

If dpkg requires perl to work to do the install then you may be out of luck. Might require manually restoring the missing file(s).

---

### Post by ajsoulmate on 2011-09-21
> **alphacrucis2 said:**
> Seems something has gone missing on your system


```
Can't locate loadable object for module Fcntl in @INC
```

If it is part of perl you might be able to get it back by downloading the perl package from here (I'm assuming that you are running Lucid according to your avatar - if not download the package for your version and architecture (32 or 64 bit)

[http://packages.ubuntu.com/lucid/perl]("http://packages.ubuntu.com/lucid/perl")

cd to wherever you downloaded the package then install the downloaded package via:

**sudo dpkg -i perl_5.10.1-8ubuntu2.1_amd64.deb** (or whatever the package appropriate for your version was called)

If dpkg requires perl to work to do the install then you may be out of luck. Might require manually restoring the missing file(s).

```

(Reading database ... 144646 files and directories currently installed.)
Preparing to replace perl 5.10.1-8ubuntu2.1 (using perl_5.10.1-8ubuntu2.1_amd64.deb) ...
Unpacking replacement perl ...
Setting up perl (5.10.1-8ubuntu2.1) ...
Can't locate loadable object for module Fcntl in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/share/perl/5.10/Carp.pm line 161
BEGIN failed--compilation aborted at /usr/lib/perl/5.10/Fcntl.pm line 161.
Compilation failed in require at /usr/lib/perl/5.10/POSIX.pm line 19.
BEGIN failed--compilation aborted at /usr/lib/perl/5.10/POSIX.pm line 19.
Compilation failed in require at /usr/sbin/update-alternatives line 25.
BEGIN failed--compilation aborted at /usr/sbin/update-alternatives line 25.
dpkg: error processing perl (--install):
 subprocess installed post-installation script returned error exit status 9
Errors were encountered while processing:
 perl
```

any other suggestion ??

---

### Post by alphacrucis2 on 2011-09-21
Seems like a catch 22 situation. It appears that perl is somehow broken but you cant fix it by reinstalling as dpkg depends on perl being functional. To fix this I think you will need some expert advice. I can think of a few things to try but I am reluctant to suggest as I can see the potential for making things worse. Unless someone can give very specific solution you may need to backup all your data and reinstall from scratch.

---

### Post by jtarin on 2011-09-21
> Can't locate loadable object for module Fcntl

The error says your script is unable to find this module:Fcntl
It's easiest to install using[ cpan]("http://www.cpan.org/misc/cpan-faq.html"), but you can download directly as well.

---

### Post by ajsoulmate on 2011-09-22
> **jtarin said:**
> The error says your script is unable to find this module:Fcntl
It's easiest to install using[ cpan]("http://www.cpan.org/misc/cpan-faq.html"), but you can download directly as well.

I'm so new to this so please could you explain more in details ?

---

### Post by jtarin on 2011-09-22
> **ajsoulmate said:**
> I'm so new to this so please could you explain more in details ?
Your Ubuntu Package manager uses Perl to do it's work. You have something wrong with your Perl configuration which will not allow it to run properly.
You have three choices....reinstall Ubuntu,fix Perl or do nothing.
[To learn more about Perl and find help for your problem.]("http://www.perlmonks.org/?node_id=674621").
I already gave you the link for CPAN. Learn the commands and try to install your module.

---

### Post by ajsoulmate on 2011-09-22
> **jtarin said:**
> Your Ubuntu Package manager uses Perl to do it's work. You have something wrong with your Perl configuration which will not allow it to run properly.
You have three choices....reinstall Ubuntu,fix Perl or do nothing.
[To learn more about Perl and find help for your problem.]("http://www.perlmonks.org/?node_id=674621").
I already gave you the link for CPAN. Learn the commands and try to install your module.

I'm **so new** to this so please could you explain **more in details**? I have read but DID NOT understand ANYTHING :(

I definitely don't want to re-install. Yes, I do have a separate /home partition but again, I don't want to re-install because I have tons of programs I don't want to lose.

Please, if someone else could explain to me how to fix that? I spent my life with Windows and I finally saw the light and don't want to go back to the dark :(

Thanks a lot and I appreciate your help. Ubuntu Forum is a great place and so nice Community.

---

### Post by jtarin on 2011-09-22
Instructing you on the installation of your perl module is beyond the scope of this thread. I would suggest reading [these]("http://perl.about.com/od/packagesmodules/qt/perlcpan.htm") instructions and learn how to do this. I could just copy and paste but that wouldn't accomplish what you need on your own.

---

### Post by amjjawad on 2011-09-22
> **jtarin said:**
> Instructing you on the installation of your perl module is beyond the scope of this thread. I would suggest reading [these]("http://perl.about.com/od/packagesmodules/qt/perlcpan.htm") instructions and learn how to do this. I could just copy and paste but that wouldn't accomplish what you need on your own.

Hello jtarin,

How can I produce that error on my system? I'd like to break it and fix it but not sure how to have the same issue? shall I just delete some files from Perl Folder and that's all? 
I'm trying to learn the hard-way. Don't want to re-install. That of course after I'll break my system :D

Thanks!

---

### Post by jtarin on 2011-09-22
> **amjjawad said:**
> Hello jtarin,

How can I produce that error on my system? I'd like to break it and fix it but not sure how to have the same issue? shall I just delete some files from Perl Folder and that's all? 
I'm trying to learn the hard-way. Don't want to re-install. That of course after I'll break my system :D

Thanks!I would recommend learning how to install a Perl module, rather than breaking your system. There are many useful Perl modules you can learn to install that don't come with the basic distribution of Perl. [Here is a link]("http://www.perlmonks.org/?node=Tutorials") to one of the most informative sites on the subject of Perl.:P

---

### Post by amjjawad on 2011-09-23
> **jtarin said:**
> I would recommend learning how to install a Perl module, rather than breaking your system. There are many useful Perl modules you can learn to install that don't come with the basic distribution of Perl. [Here is a link]("http://www.perlmonks.org/?node=Tutorials") to one of the most informative sites on the subject of Perl.:P

Will look into that link, thanks my friend :)
However, I still insist :D I feel bored and really want some action. I need to learn how to fix things without the need to re-install the whole system. I tried the same thing that the OP installed on a Virtual Box (Ubuntu 11.04) but was too tired last night and couldn't test it. Hopefully today, I'll break either on my test PC or on the Virtual Box installation :)

Glad you still active :)

---

### Post by jtarin on 2011-09-23
> **amjjawad said:**
> Well look into that link, thanks my friend :)
However, I still insist :D I feel bored and really want some action. I need to learn how to fix things without the need to re-install the whole system. I tried the same thing that the OP installed on a Virtual Box (Ubuntu 11.04) but was too tired last night and couldn't test it. Hopefully today, I'll break either on my test PC or on the Virtual Box installation :)

Glad you still active :)Try uninstalling Perl...then reinstall.:P

---

### Post by amjjawad on 2011-09-23
> **jtarin said:**
> Try uninstalling Perl...then reinstall.:P
Nice one jtarin :D
How would I do that if "apt-get" is somehow needs Perl to work?
Anyway, I'll test that soon. Today is Friday and I have lots of Pending Tasks to finish.

I might test that on Lubuntu as a part of my new interest. Did many successful tests on Lubuntu so far.

---

### Post by ajsoulmate on 2011-09-30
Thank you for your help I was able to resolve the problem by re-installing Ubuntu 10.04 ..

---

### Post by amjjawad on 2011-09-30
> **ajsoulmate said:**
> Thank you for your help I was able to resolve the problem by re-installing Ubuntu 10.04 ..

Well done :)

Please mark this thread as SOLVED :)

[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=7263[/IMG]

---

### Post by jtarin on 2011-09-30
> **amjjawad said:**
> Nice one jtarin :D
How would I do that if "apt-get" is somehow needs Perl to work?
You would have to download the source and configure/make/install. Make sure you have all the tools needed to do this though.

---

### Post by amjjawad on 2011-10-01
> **jtarin said:**
> You would have to download the source and configure/make/install. Make sure you have all the tools needed to do this though.
I've been so busy with Testing Lubuntu 11.10 and didn't have time to try that. I have Ubuntu 11.04 installed on VB and planned to mess with it but no time for that now. But thanks anyway :)

---

### Post by ajsoulmate on 2011-10-04
> **amjjawad said:**
> Well done :)

Please mark this thread as SOLVED :)

[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=7263[/IMG]

Done :)

---


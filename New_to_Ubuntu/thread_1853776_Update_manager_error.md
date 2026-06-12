---
title: "Update manager error"
date: 2011-10-03
forum: New to Ubuntu
---

### Post by cksutaria on 2011-10-03
[SIZE=3]Natty Update Manager shows this:
[/SIZE]
installArchives() failed: Traceback (most recent call last):
    [LEFT]  File "/usr/bin/apt-listchanges", line 33, in <module>[/LEFT]
   [SIZE=3]
How do I solve this problem?

Thank You.
[/SIZE]

---

### Post by Rubi1200 on 2011-10-03
Hi and welcome to the forums :)

Open a terminal with Ctrl+Alt+T and run the following command:

```
sudo apt-get update
```

If there are error messages, copy and paste them into a new post so we can try and help you troubleshoot the issue.

Thanks.

---

### Post by cksutaria on 2011-10-03
Hi, Rubi1200

I ran sudo apt-get update as you suggested. Here there are no error.

But when I run Update Manager or Synaptic this message always comes.

(InstallArchives) failed. traceback (most recent call last):
File"usr/bin/apt-listchanges", line 33, in <module>

Thanks for your help and waiting for solution to my problem.

---

### Post by philinux on 2011-10-03
Threads merged.

---

### Post by matt_symes on 2011-10-03
Hi

Well i'm not Rubi but hopefully you both will not mind if i ask a question. What's the output of (from the terminal)

```
apt-config dump | grep apt-listchanges
```I'm interested as  /usr/bin/apt-listchange is not on my Natty install.  

Do you get the same error if you type

```
sudo apt-get install htop
```BTW: You don't need to start a new thread each time you perform some steps someone asks you to. Just reply to the one you started. Otherwise you will find it very difficult to get your questions answered as most people subscribe to one thread when helping someone. If you don't respond in that thread then they will no know that you have responded and it is possible they will not see the new thread you have created.

I will ask a moderator if they can merge your two threads for you.

EDIT: Beaten to it!!!!

Kind regards

---

### Post by cksutaria on 2011-10-03
Hi matt_symes

When I ran this command  these appears;

apt-config dump | grep apt-listchanges

DPkg::Pre-Install-Pkgs:: "/usr/bin/apt-listchanges[/U] --apt || test $? -ne 10";
DPkg::Tools::Options::/usr/bin/apt-listchanges "";
DPkg::Tools::Options::/usr/bin/apt-listchanges::Version "2";
[ In  all the three lines  above apt-listchanges shown in red colour ]


When I ran this command  these appears;

sudo apt-get install htop

dpkg: unrecoverable fatal error, aborting:
syntax error: unknown user 'clamav' in statoverride file
E: Sub-process /usr/bin/dpkg returned an error code (2)

Thanks for your help and waiting for solution to my problem.

---

### Post by matt_symes on 2011-10-03
Hi

> **cksutaria said:**
> Hi matt_symes

When I ran this command  these appears;

apt-config dump | grep apt-listchanges

DPkg::Pre-Install-Pkgs:: "/usr/bin/apt-listchanges[/U] --apt || test $? -ne 10";
DPkg::Tools::Options::/usr/bin/apt-listchanges "";
DPkg::Tools::Options::/usr/bin/apt-listchanges::Version "2";
[ In  all the three lines  above apt-listchanges shown in red colour ]


When I ran this command  these appears;

sudo apt-get install htop

dpkg: unrecoverable fatal error, aborting:
syntax error: unknown user 'clamav' in statoverride file
E: Sub-process /usr/bin/dpkg returned an error code (2)

Thanks for your help and waiting for solution to my problem.

Don't worry aboput the results of grep being red. This is standard to highlight where the text searched for is.

This is from my Lucid install.

```

matthew@matthew-laptop:~/.ssh$ apt-config dump | grep DPkg::
DPkg::Pre-Install-Pkgs "";
DPkg::Pre-Install-Pkgs:: "/usr/sbin/dpkg-preconfigure --apt || true";
DPkg::Post-Invoke "";
DPkg::Post-Invoke:: "if [ -d /var/lib/update-notifier ]; then touch /var/lib/update-notifier/dpkg-run-stamp; fi; if [ -e /var/lib/update-notifier/updates-available ]; then echo > /var/lib/update-notifier/updates-available; fi ";
matthew@matthew-laptop:~/.ssh$ apt-config dump | grep apt-listchange
matthew@matthew-laptop:~/.ssh$ 
```

There is no mention of apt-listchanges. I will boot into Natty and check that install and then post back.

Kind regards

---

### Post by matt_symes on 2011-10-03
Hi

I also could not find your settings in my install of Natty as well. I am wondering if you actually need apt-listchanges. 

What was the last thing you installed/unistalled on your system. Was it an update or a program you installed ?

> 
dpkg: unrecoverable fatal error, aborting:
syntax error: unknown user 'clamav' in statoverride file
E: Sub-process /usr/bin/dpkg returned an error code (2)This is interesting.

Open a terminal and type these two commands.
```

dpkg-statoverride --list
cat /etc/passwd | grep clamav
```Post the results back here.

Did clamAV find any viruses that you removed ? Clam can give a number of false positives. Did you uninstall clam ?

Just trying to get to the bottom of what may have happened to your system before offering any advice.

Kind regards

---

### Post by Krishna Murthy on 2011-10-04
Hi  matt_symes

When I type this appears :

dpkg-statoverride --list
dpkg-statoverride: unrecoverable fatal error, aborting:
 syntax error: unknown user 'clamav' in statoverride file

When I type "cat /etc/passwd | grep clamav"  nothing happens.

I did not install any new applications except the trusted ones like Cairodock, flux, etc and the regular updates.

I have Natty on my other old PC and Laptop as well. This problem is only on my MAIN PC.

Regards.

I am posting this from my friend's PC hence change of name.  Cksutaria.

Thank you.

---

### Post by matt_symes on 2011-10-04
Hi

Let's look at this this first.

> When I type this appears :

dpkg-statoverride --list
dpkg-statoverride: unrecoverable fatal error, aborting:
 syntax error: unknown user 'clamav' in statoverride file

When I type "cat /etc/passwd | grep clamav"  nothing happens.  The problem here is that dpkg is configured to install a package as a particular user but that user does not exit in your passwd file.

Please post the output of (from a terminal)

```
cat /var/lib/dpkg/statoverride
```Kind regards

---

### Post by cksutaria on 2011-10-04
Hi matt

I typed as you have suggested and here is the output.

cat /var/lib/dpkg/statoverride
clamav clamav 755 /var/cache/clamav-unofficial-sigs/add-dbs
root mlocate 2755 /usr/bin/mlocate
clamav clamav 755 /var/cache/clamav-unofficial-sigs/si-dbs
clamav clamav 755 /var/cache/clamav-unofficial-sigs/mbl-dbs
clamav clamav 755 /var/cache/clamav-unofficial-sigs/msrbl-dbs
clamav clamav 700 /var/lib/clamav-unofficial-sigs/gpg-key
hplip root 755 /var/run/hplip
root ssl-cert 710 /etc/ssl/private
clamav clamav 755 /var/cache/clamav-unofficial-sigs/ss-dbs
root Debian-exim 640 /etc/exim4/passwd.client
clamav clamav 755 /var/lib/clamav-unofficial-sigs/configs
root crontab 2755 /usr/bin/crontab


Reinstall may be the easiest route but I do not want to go that way for the simple reason : I will never learn anything about Linux / Natty etc.

Thank you for your persistence in solving my problem. If it is ok with you I am willing to run with you till the problem is solved.

Regards.

---

### Post by matt_symes on 2011-10-04
Hi

> **cksutaria said:**
> Hi matt

I typed as you have suggested and here is the output.

cat /var/lib/dpkg/statoverride
clamav clamav 755 /var/cache/clamav-unofficial-sigs/add-dbs
root mlocate 2755 /usr/bin/mlocate
clamav clamav 755 /var/cache/clamav-unofficial-sigs/si-dbs
clamav clamav 755 /var/cache/clamav-unofficial-sigs/mbl-dbs
clamav clamav 755 /var/cache/clamav-unofficial-sigs/msrbl-dbs
clamav clamav 700 /var/lib/clamav-unofficial-sigs/gpg-key
hplip root 755 /var/run/hplip
root ssl-cert 710 /etc/ssl/private
clamav clamav 755 /var/cache/clamav-unofficial-sigs/ss-dbs
root Debian-exim 640 /etc/exim4/passwd.client
clamav clamav 755 /var/lib/clamav-unofficial-sigs/configs
root crontab 2755 /usr/bin/crontab


There are a number of references to clamav in this file, a user you do not have on your system.

So first things first, let's remove them.

Open a terminal and type (or copy and paste)

```
sudo cp /var/lib/dpkg/statoverride /var/lib/dpkg/statoverride.old
```

This will make a backup copy.

then type

```
sudo bash -c "sed '/clamav/d' < /var/lib/dpkg/statoverride.old > /var/lib/dpkg/statoverride"
```

after that try 

```
dpkg-statoverride --list
```

What are the results of that last command ?

> 
Reinstall may be the easiest route but I do not want to go that way for the simple reason : I will never learn anything about Linux / Natty etc.

You don't need to reinstall. I think this is fixable.

>  If it is ok with you I am willing to run with you till the problem is solved

No worries.

Kind regards

---

### Post by cksutaria on 2011-10-04
Hi Matts

Here is the output :

dpkg-statoverride --list
root mlocate 2755 /usr/bin/mlocate
hplip root 755 /var/run/hplip
root ssl-cert 710 /etc/ssl/private
root Debian-exim 640 /etc/exim4/passwd.client
root crontab 2755 /usr/bin/crontab

Regards.

---

### Post by matt_symes on 2011-10-04
Hi

Well that's one issue fixed by the looks of it. 

What happens if you type...

```
sudo apt-get install htop
```

Post the results back here.

Kind regards

---

### Post by syedyaqubali on 2011-10-04
Hi i am getting this error for update manager and not getting launch also


[B]An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '“deb' is not known on line 61 in source list /etc/apt/sources.list'[/B]

---

### Post by matt_symes on 2011-10-04
Hi

@[syedyaqubali]("http://ubuntuforums.org/member.php?u=1122817")

Open a terminal and type

```
cat /etc/apt/sources.list
```

Copy and paste the results back into your next post.

Kind regards

---

### Post by cksutaria on 2011-10-05
Hi Matt

Here is the output :

 sudo apt-get install htop
[sudo] password for krishna: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  htop
0 upgraded, 1 newly installed, 0 to remove and 80 not upgraded.
Need to get 0 B/58.7 kB of archives.
After this operation, 209 kB of additional disk space will be used.
Selecting previously deselected package htop.
(Reading database ... 208969 files and directories currently installed.)
Unpacking htop (from .../archives/htop_0.9-2_i386.deb) ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_IN.utf8.cache...
Processing triggers for man-db ...
Processing triggers for menu ...
Processing triggers for python-support ...
Setting up htop (0.9-2) ...
Processing triggers for menu ...


Regards

---

### Post by cksutaria on 2011-10-05
Hi Matts

After posting the above I went back and installed a small dock via Ubuntu Software Center : Success

I opened Synaptic and installed  a small dock : Success

Next I opened the Update Manager and ran the already downloaded  but uninstalled packages. It was a Success. All the previously downloaded packages were installed without any problem.

Does this mean my problems are over ?

Regards.

---

### Post by matt_symes on 2011-10-05
Hi
> 
Does this mean my problems are over ?

It looks like it :) Enjoy.

Kind regards

---

### Post by cksutaria on 2011-10-05
Hi Matts

I just installed Firefox 7 from the Update Manager.

Everything went fine.

A BIG THANK YOU FOR YOUR HELP.

Best Wishes.

---


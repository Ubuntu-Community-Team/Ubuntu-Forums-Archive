---
title: "Bash security risk to Linux"
date: 2014-09-25
forum: New to Ubuntu
---

### Post by Michael_McKenney on 2014-09-25
I am in charge of a data center.  Every morning, I check for the latest threats to our network.  I found this article today on the BBC.

[http://www.bbc.com/news/technology-29361794](http://www.bbc.com/news/technology-29361794)

I see it affects Linux.  How do we protect ourselves from it?  Upgrade?  Can Bash be removed and replaced by something else?  Is it installed by default?  How can we check if we have it?  

```

A "deadly serious" bug potentially 
affecting hundreds of millions of computers, servers and devices has been 
discovered.

The flaw has been found in a software component known as Bash, which is a 
part of many Linux systems as well as Apple's Mac operating system.

The bug, dubbed Shellshock, can be used to remotely take control of almost 
any system using Bash, researchers said.

Experts said it was more serious than the[URL="http://www.bbc.co.uk/news/technology-26954540"] Heartbleed bug discovered 
in April[/URL].

"Whereas something like Heartbleed was all about sniffing what was going on, 
this was about giving you direct access to the system," Prof Alan Woodward, a 
security researcher from the University of Surrey, told the BBC.

"The door's wide open."

Some 500,000 machines worldwide were thought to have been vulnerable to 
Heartbleed. But early estimates, which experts said were conservative, suggest 
that Shellshock could hit at least 500 million machines.

The problem is particularly serious given that many web servers are run using 
the Apache system, software which includes the Bash component.
Patch immediately 
Bash - which stands for Bourne-Again SHell - is a command prompt on many Unix 
computers. Unix is an operating system on which many others are built, such as 
Linux and Mac OS.

The US Computer Emergency Readiness Team (US-Cert) issued a warning about the 
bug, [URL="https://www.us-cert.gov/ncas/current-activity/2014/09/24/Bourne-Again-Shell-Bash-Remote-Code-Execution-Vulnerability"]urging 
system administrators to apply patches[/URL].

However, other security researchers warned that the patches were "incomplete" 
and would not fully secure systems.

Of particular concern to security experts is the simplicity of carrying out 
attacks that make use of the bug.

Cybersecurity specialists Rapid7 rated the Bash bug as 10 out of 10 for 
severity, but "low" on complexity - a relatively easy vulnerability for hackers 
to capitalise on.

"Using this vulnerability, attackers can potentially take over the operating 
system, access confidential information, make changes, et cetera," said Tod 
Beardsley, a Rapid7 engineer.

"Anybody with systems using Bash needs to deploy the patch immediately."

For general home users, Prof Woodward suggested simply keeping an eye on 
manufacturer websites for updates - particularly for hardware such as broadband 
routers.

```

---

### Post by Lars Noodén on 2014-09-25
See this thread:

[http://ubuntuforums.org/showthread.php?t=2245682](http://ubuntuforums.org/showthread.php?t=2245682)

But normally, just "apt-get update" should do it.

---

### Post by Lars Noodén on 2014-09-25
> **Michael_McKenney said:**
> Can Bash be removed and replaced by something else?  Is it installed by default?

For scripting, /bin/sh is really a symlink to /bin/dash.  Dash is a different shell, and presumably not vulnerable in that way.  For [CVE-2014-6271](http://people.canonical.com/~ubuntu-security/cve/2014/CVE-2014-6271.html) some kind of outside access to the shell is needed to do the exploit, anyway.  That's not something most machines are set up to do.  The two situations I've seen mentioned would be a CGI script that's a bash script or an SSH key with a forced command.  Both of those would be locked down but for the bug which does provide a way out *for that user* and *maybe* then it can be chained to some other bug into a privilege escallation.

So if your scripts use /bin/sh and you have left that pointing at dash, then the scripts are OK.

---

### Post by whitesmith on 2014-09-25
Not all versions of bash are susceptible. To find out if yours is, run:```
env x='() { :;}; echo vulnerable' bash -c "echo this is a test"

```.

Basically any bash from the Open Software Foundation is susceptible unless and until patched, after which the x function is unimportable and therefore probably harmless. It's important to do as Nooden suggested and "sudo apt-get update." Of course, routers and other network components are still wide open.

---

### Post by Trent T on 2014-09-25
Hi All,

Thanks to all for notifying of the security risk!

My Ubuntu 12.04 32-bit system has not been able to load updates for the past month or so.  apt-get update appears to update, but does not result in resolution of vulnerability to the 'Shellshock' bug.
I may be doing something wrong here-- If so, feel free to enlighten me.  I plan to put in a bug report.  Any/all suggestions welcome. ;)
--Trent T

**1) I have tried without success to update to Ubuntu versions 12.10 thru 14.04;**

```
etc@etc-MS-0123~$ sudo do-release-upgrade
[sudo] password for trent: 
Checking for a new Ubuntu release
Err Upgrade tool signature                                                     
  404  Not Found [IP: 2001:67c:1360:8c01::19 80]                               
Err Upgrade tool                                                               
  404  Not Found [IP: 2001:67c:1360:8c01::19 80]                               
Fetched 0 B in 0s (0 B/s)                                                      
WARNING:root:file 'quantal.tar.gz.gpg' missing
Failed to fetch
Fetching the upgrade failed. There may be a network problem. 
etc@etc-MS-0123:~$

```

**2) My system tests out as 'vulnerable' before and after an apparently successful apt-get update:**

```
~$ env x='() { :;}; echo vulnerable' bash -c "echo this is a test"
vulnerable
this is a test
etc@etc-MS-0123:~$ sudo apt-get update
Hit http://us.archive.ubuntu.com precise Release.gpg
Hit http://us.archive.ubuntu.com precise-updates Release.gpg                   
//..full listing mostly deleted..//
Ign https://private-ppa.launchpad.net trusty/main Translation-en
Reading package lists... Done                                                  
etc@etc-MS-0123:~$ env x='() { :;}; echo vulnerable' bash -c "echo this is a test"
vulnerable
this is a test
```

**3) Update Manager fails to update, with some interesting messages.  Highlights below for the truly compulsive;**

```
installArchives() failed: (Reading database ... 
(Reading database ... 5%%
(Reading database ... 10%%
//....//
Preparing to replace libnss3-1d 3.17-0ubuntu0.12.04.1 (using .../libnss3-1d_3.17.1-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement libnss3-1d ...
Preparing to replace libnss3 3.17-0ubuntu0.12.04.1 (using .../libnss3_3.17.1-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement libnss3 ...
//....//
Unknown parameter encountered: "remote announce"
Ignoring unknown parameter "remote announce"
Unknown parameter encountered: "remote browse sync"
Ignoring unknown parameter "remote browse sync"
//....//
Unknown parameter encountered: "lprm command"
Ignoring unknown parameter "lprm command"
/var/lib/dpkg/info/samba4.postinst: 14: /var/lib/dpkg/info/samba4.postinst: /usr/share/samba/setoption.pl: Permission denied
dpkg: error processing samba4 (--configure):
 subprocess installed post-installation script returned error exit status 126
No apport report written because MaxReports is reached already
Setting up libnss3 (3.17.1-0ubuntu0.12.04.1) ...
Setting up libnss3-1d (3.17.1-0ubuntu0.12.04.1) ...
//...//
Errors were encountered while processing:
 samba4
Error in function: 
Setting up samba4 (4.0.0~alpha18.dfsg1-4ubuntu2) ...
Unknown parameter encountered: "remote announce"
Ignoring unknown parameter "remote announce"
Unknown parameter encountered: "remote browse sync"
Ignoring unknown parameter "remote browse sync"
//....//
Unknown parameter encountered: "valid users"
Ignoring unknown parameter "valid users"
Unknown parameter encountered: "locking"
Ignoring unknown parameter "locking"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "locking"
Ignoring unknown parameter "locking"

```

---

### Post by whitesmith on 2014-09-25
This thread is closed, but since we're still on topic...Try```
sudo apt-get dist-upgrade
sudo apt-get check
```
If there are no errors, then:```
sudo apt-get update
sudo apt-get upgrade
env x='() { :;}; echo vulnerable' bash -c "echo this is a test"
```
If this doesn't work, an answer will have to come from someone more experienced. Odds are your router and modem are affected with no clear way to patch either. Regards.

---

### Post by Impavidus on 2014-09-25
In any case, don't try upgrading to 12.10. It's unsupported. There should be a direct path to 14.04.

---

### Post by Michael_McKenney on 2014-09-25
Many have had issues going from 12.04 to 14.04.   Why would going to 12.10 to 13.04 to 14.04 on DVD upgrades be a issue.  Unsupported just means no patches like XP Pro.

---

### Post by Trent T on 2014-09-26
Thanks Whitesmith!
I _did_ get errors with sudo apt-get dist-upgrade.  

Also received a separate error message on system start that something is wrong with samba.  Will attempt to post details to a new thread, since this one is closed.

Impavidus, no success here in upgrading directly to 14.04.  I agree that it should work, (has worked in the past).

Michael_McKenney -- Not sure why it's an issue.  Win XP Pro!?  brrr!  Never Again... [-(

---


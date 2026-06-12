---
title: "No packages will install - broken package system"
date: 2012-04-19
forum: New to Ubuntu
---

### Post by duncan12 on 2012-04-19
In [this thread]("http://ubuntuforums.org/showthread.php?t=1925735") I installed drivers for my printer.

However now my package system is very broken - cannot install or upgrade packages, and cannot remove the package that causes the problem.

I always got this message since installing *hl1430lpr*, however ignored it because it caused no problems. However now it seems I can't do anything...

I went into Synaptic and the package was marked for removal. I don't want to remove it but the system seems to insist on it - it wouldn't let me unmark it for removal.

I wanted to try removing it and installing again, but trying to **sudo apt-get remove** it doesn't work. I've even tried **sudo dpkg --remove --force-remove-reinstreq hl1430lpr** but get: ```
dpkg: error processing hl1430lpr (--remove):
 subprocess installed post-removal script returned error exit status 1
```


Here is the output of trying to install a package:

```

duncan@Duncan-Linux:~$ sudo apt-get install gimp-resynthesizer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  hl1430lpr
The following NEW packages will be installed:
  gimp-resynthesizer
0 upgraded, 1 newly installed, 1 to remove and 4 not upgraded.
1 not fully installed or removed.
Need to get 0 B/22.9 kB of archives.
After this operation, 111 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 429849 files and directories currently installed.)
Removing hl1430lpr ...
start: Unknown job: lpd
dpkg: error processing hl1430lpr (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 hl1430lpr
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

So instead of trying to install the package I asked it to it just tries to remove hl1430lpr, then aborts.


Any ideas?

Thanks,
Duncan

---

### Post by kurt18947 on 2012-04-19
I'm not sure if Synaptic can fix your problem or not.  If you can install it, it might be worth a try.  I did use Synaptic to solve a similar problem on a 12.04 install.

---

### Post by kc1di on 2012-04-19
If synaptic doesn't fix it try this

In a terminal :

```
dpkg --configure -a
```

If that does not work try this again in terminal one command at a time:

```
sudo rm /var/lib/apt/lists/* -vf 
sudo apt-get update
```

Let us know if it works or not

---

### Post by duncan12 on 2012-04-19
Thanks for the replies.

I forgot to mark the thread as solved last night, but here's what fixed it:

```

$ cd /var/lib/dpkg/info
$ ls hl1430lpr.*
$ sudo vim hl1430lpr.postrm #the instructions for what to do when removing package
(comment out the line that says "/etc/init.d/lpd restart" - the service that it said was not found and aborted)
$ sudo apt-get remove hl1430lpr
$ sudo apt-get install hl1430lpr

```

...fixed!

I didn't work that out BTW, had someone else help :p

But for similar issues try
```

$ cd /var/lib/dpkg/info
$ ls pkg-name.*

```
and take things from there.

---

### Post by tekheretik on 2012-10-30
> **duncan12 said:**
> Thanks for the replies.

I forgot to mark the thread as solved last night, but here's what fixed it:

```

$ cd /var/lib/dpkg/info
$ ls hl1430lpr.*
$ sudo vim hl1430lpr.postrm #the instructions for what to do when removing package
(comment out the line that says "/etc/init.d/lpd restart" - the service that it said was not found and aborted)
$ sudo apt-get remove hl1430lpr
$ sudo apt-get install hl1430lpr

```...fixed!

I didn't work that out BTW, had someone else help :p

But for similar issues try
```

$ cd /var/lib/dpkg/info
$ ls pkg-name.*

```and take things from there.

Thank you ever so much to you and whoever helped you, I had the EXACT same problem! The only diff was, had to replace 'vim' with 'kate', I am a Kubuntu 12.04 LTS user, was getting worried I would have to do a re-install, really hate that! You and your helper are LIFE SAVERS! :-D

Edit: Forgot something, my file name was hl1430lpr:i386, had to change that too.

---


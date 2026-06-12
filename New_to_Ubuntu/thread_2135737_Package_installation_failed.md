---
title: "Package installation failed"
date: 2013-04-15
forum: New to Ubuntu
---

### Post by cheatos on 2013-04-15
Hi,

I have tried installing the Latex package prosper and somehow, the installation failed.
Here is the output of the apt-get upgrade command:

```
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/449 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
dpkg: error processing prosper (--configure):
 package prosper is not ready for configuration
 cannot configure (current status `half-installed')
Errors were encountered while processing:
 prosper
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

What can I do to fix this?
I already tried removing prosper with apt-get purge / remove prosper* but also got the dpkg-error.

Thanks for any help!

---

### Post by ibjsb4 on 2013-04-15
Try

```
sudo dpkg --configure -a

sudo apt-get -f install
```

---

### Post by cheatos on 2013-04-15
thank you for your help but sadly it is still the same problem with the same error code :(

---

### Post by ibjsb4 on 2013-04-15
Some other things to try

```
sudo apt-get install --reinstall prosper

sudo dpkg -r prosper
```

There is also a dpkg --configure option

```
man dpkg
```

Be nice to know what those errors are.  Maybe it will spit out something else to go on.

---

### Post by raja.genupula on 2013-04-15
[http://askubuntu.com/questions/171205/e-sub-process-usr-bin-dpkg-returned-an-error-code-1](http://askubuntu.com/questions/171205/e-sub-process-usr-bin-dpkg-returned-an-error-code-1)

---

### Post by cheatos on 2013-04-16
well I followed the instructions given by the link (replaced the package though ;) ) but still get the same error code :(
dpkg -r says "package is in a very bad state" and i should try installing before removal...

---

### Post by ibjsb4 on 2013-04-16
Ok manually remove it.  Open root nautilus, go to your "FileSystem" (on the left) and do a search for "prosper".  Then remove everything you find.

```
gksudo nautilus
```

---

### Post by cheatos on 2013-04-16
I removed every file that ```
cd / && sudo find -name prosper*
``` gave as output but still I get the following:
```

michael@michaelslaptop:~$ sudo apt-get install prosper
Reading package lists... Done
Building dependency tree       
Reading state information... Done
prosper is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 449 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://de.archive.ubuntu.com/ubuntu/ quantal/main prosper all 1.00.4+cvs.2007.05.01-4 [449 kB]
Fetched 449 kB in 0s (1,677 kB/s)
dpkg: error processing prosper (--configure):
 package prosper is not ready for configuration
 cannot configure (current status `half-installed')
Errors were encountered while processing:
 prosper
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Seems like this pakage just does not want to be installed ;)

---

### Post by cortman on 2013-04-16
Have you tried all these?

```

sudo apt-get clean
sudo rm -r /var/lib/apt/lists/*
sudo touch /var/lib/apt/lists/lock
sudo mkdir /var/lib/apt/lists/partial
sudo apt-get clean
sudo apt-get update
[FONT=verdana]
```

If any return errors, please post back.[/FONT]

---

### Post by cheatos on 2013-04-19
Thank you for your tips, I got no errors.
But when I run ```
sudo apt-get upgrade
``` it still gives the same as above...
All the other commands went thorugh without any problems

---

### Post by cortman on 2013-04-19
Try

```
dpkg --configure -a
```

---

### Post by cheatos on 2013-04-20
Well, that went through without any problems.
But no output either.

---

### Post by cortman on 2013-04-22
So what happens if you run apt-get upgrade again? Is 'prosper' still giving errors?

---

### Post by cheatos on 2013-04-22
Yes, still the exact same error :(

---

### Post by ibjsb4 on 2013-04-22
Hay cortman, what happening :)

Wonder if texlive is holding back corrupted files.

[http://packages.ubuntu.com/precise/prosper](http://packages.ubuntu.com/precise/prosper)

[http://packages.ubuntu.com/precise/texlive](http://packages.ubuntu.com/precise/texlive)

---

### Post by cheatos on 2013-04-22
Well, if this is the case, what do I do?
Will i be able to remove tex-live without srewing up my latex compiler?

---

### Post by ibjsb4 on 2013-04-22
Thats why I was just throwing it out there.  Wanted to see what cortman thinks :)

---

### Post by cortman on 2013-04-22
Not sure, have you tried to purge and reinstall prosper?
I'm afraid I know little about tex/latex.

---

### Post by schragge on 2013-04-22
The only package that depends on prosper is [texlive-full](http://packages.ubuntu.com/quantal/texlive-full). [texlive-latex-recommended](http://packages.ubuntu.com/precise/texlive-latex-recommended) only recommends it. If you don't write transparencies, you can simply remove *prosper*.

---

### Post by cheatos on 2013-04-22
well, the problem here is that prosper won't even get purged away, so I just have this stupid package "half-installed" and can't do anything about it.
Is there some config file of dpkg wher I could remove this package so it doesn't appear half installed anymore and then remove all data by prosper?

---


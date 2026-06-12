---
title: "Ecliplse PDT - Missing perspective"
date: 2007-10-13
forum: Programming Talk
---

### Post by md5hash on 2007-10-13
i downloaded eclipse pdt all-in-one but the php perspective is missing..

---

### Post by md5hash on 2007-10-13
also i noticed that the PDT Feature is disabled. please see the screenshot

---

### Post by dmillimono on 2007-10-16
Same thing for me.

On one computer, Eclipse PDT had been installed several months ago. I upgraded the configuration recently, when they released the version 1.0, and everything remained fine.

However, on another computer, I installed pdt-all-in-one v1.0 from scratch and I only get the Java perspective, but nothing related to PHP...

I'll keep you posted when I'll find a solution (there's always a solution).

MD

---

### Post by Wolter on 2007-11-24
I had the same problem and the solution is very easy. You have to install latest version of Java Environment. Check whether Java 1.4 is installed. Uninstall this version first and then install Java 1.5 or 1.6. Now it should works properly.

---

### Post by ger_macaco on 2008-10-09
I have installed Eclipse 3.4 Ganymede and PDT 2.0 as a plugin. I have tried starting eclipse with '-clean' and checked that I am using Sun's Java 1.6.

However I cannot access PDT perspective.

Any ideas?

---

### Post by filipejps on 2009-04-02
> **ger_macaco said:**
> I have installed Eclipse 3.4 Ganymede and PDT 2.0 as a plugin. I have tried starting eclipse with '-clean' and checked that I am using Sun's Java 1.6.

However I cannot access PDT perspective.

Any ideas?

same problem :(

---

### Post by Kyle Reese on 2009-07-07
I have a solution!


**Background:**
I needed some PHP-support in Eclipse. I began to install Eclipse 3.5, by copying the downloaded 3.5 source to /usr/lib/ with

```
sudo cp -Rf /home/kyle/Desktop/eclipse /usr/lib/
```

Don't remember the page I got that tip on. I have installed and uninstalled both PHPEclipse and PDT several times before I decided which to use, so this solution works for more than PDT.


**Solution, according to my experience**
First, uninstall all plugins that you have installed as ordinary user, because those plugins are installed in your home directory.

Second, start Eclipse as root with:
```
sudo eclipse
```
or
```
sudo eclipse -clean
```
I used the second one, with the clean-flag, just to be sure :)

Third, install the plugin, as instructed on the plugin homepage, but this time as root.

**Some notes**
Sometime, I had to install plugins twice (may be because I messed up  which user I ran as, not sure)

I prefer PDT, because I had major problems with the auto completion in PHPEclipse by giving a list of hundreds of suggestions, where none is a good one. Although, PDT sometimes doubles up the auto completion suggestions (just a small problem).

Off topic recommendation: use Remote System Explorer (RSE) for PHP-files at remote server over sftp, ftp or other protocols. Absolutely godlike, but somewhat network intense. Usage: Add new folder => advanced, check "link folder in the file system" and choose RSE as file system. No more manual file transfer or synchronization buttons to press all the time.

---

### Post by daemonraco on 2012-08-25
hi! I had the same problem and the solution I found was to check and install all packages starting with 'SWT*' from 'Install new software' under 'Help', after that, PHP perspective reappeared.

Sincerely, I don't what it really did, but it worked, I now have the perspective and my codes have colors :D

---

### Post by sandyd on 2012-08-25
[B]Necromancing - Please do not post in threads more than 1 year old

Thread Closed.
[/B]

---


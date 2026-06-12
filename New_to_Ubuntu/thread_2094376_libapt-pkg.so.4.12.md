---
title: "libapt-pkg.so.4.12"
date: 2012-12-13
forum: New to Ubuntu
---

### Post by cmcanulty on 2012-12-13
I am at the library and did a normal update of one laptop and now get this error. Now  I can't open synaptic or software center or do anything. I have googled for an hour and really need this fixed by 5pm!
```
librarian@Darcy40:~$ ud
apt-get: error while loading shared libraries: libapt-pkg.so.4.12: cannot open shared object file: No such file or directory
librarian@Darcy40:~$
```
I tried sudo copying that file from another machine that is identical and works fine but it still says file isn't there . I put it in /usr/lib/x86_64-linux-gnu and set the permissions the way they should be. I can't install anything to fix this!I am running 12.04 classic. I updated 10 identical machines and only one gave this problem.I can sudo nautilus if that helps.I also tried logout and restart.

---

### Post by irv on 2012-12-13
Have you tried running synaptic from the command line to see what the error is if it doesn't start?
```
sudo synaptic
```
I am not sure what to do, but this might tell you something helpful. If it doesn't start, maybe you can reinstall it from the terminal. 
```
sudo apt-get install synaptic
```

---

### Post by cmcanulty on 2012-12-13
same error every time
```
librarian@Darcy40:~$ sudo synaptic
synaptic: error while loading shared libraries: libapt-pkg.so.4.12: cannot open shared object file: No such file or directory
librarian@Darcy40:~$
```

and 
```
librarian@Darcy40:~$ sudo apt-get install synaptic
sudo: apt-get: command not found
librarian@Darcy40:~$ 

```

---

### Post by irv on 2012-12-13
What it is telling you is your apt-get is not installed.
The package "apt" is not installed which includes the apt-get. Without this package I don't see how you can install anything.
At this point I would try one more thing before reinstalling Ubuntu. I would restart and go into recovery mode from grub and try running a repair on installed packages from the repair menu in recovery. This might fix it.

---

### Post by cmcanulty on 2012-12-13
OK thanks can you tell me what I should do after I get in recovery mode?

---

### Post by irv on 2012-12-13
> **cmcanulty said:**
> OK thanks can you tell me what I should do after I get in recovery mode?

To be honest it's been awhile, but I think it has a menu item that lets you run a repair on installed packages. I do remember to just press the shift key as you boot to get to grub and then select recovery mode. From there you have to follow the onscreen instructions.

---

### Post by cmcanulty on 2012-12-13
I guess I have to give up. What a screw to have to reinstall just because of an update!I have tried to figure a way to install apt-get from source using the command line but no luck on researching that. I can boot and even get to sudo but can't install or update a thing.. Can anyone help? It was a pain with a clean install as Ubuntu had to blacklist things ans I'm not sure I could even make it work again.

---

### Post by Zill on 2012-12-13
cmcanulty:  It may be worth trying the following command as it *should* configure all partially installed packages:
```
sudo dpkg --configure -a
```
Then I would try:
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by cmcanulty on 2012-12-14
none of those worked, I ended up reinstalling.Very sad state of affairs.

---

### Post by irv on 2012-12-14
> **cmcanulty said:**
> none of those worked, I ended up reinstalling.Very sad state of affairs.

Yes, that does really sucks. To bad you couldn't just replace the files. I know you said you tried that. Sometimes just reinstalling is the fastest way. I wonder if something happen with the download when doing the update?

---

### Post by cmcanulty on 2012-12-14
well I burned 2 hours trying to fix and 2 hours reinstalling.Having a separate home and my markings saved really helped. Thanks

---

### Post by irv on 2012-12-17
> **cmcanulty said:**
> well I burned 2 hours trying to fix and 2 hours reinstalling.Having a separate home and my markings saved really helped. Thanks

I just got a bug report this morning and I was wondering if this was your problem. Here is the email I go on the bug report.

it seems there is a bug in libicu48-dev package which causes some package config files *.pc to be missing:

I: Installing dependencies on system: libicu wireless-tools
I: Using apt-file to search for providers; this may be slow.  Please wait.
I: No native package found for libicu (/icu-i18n.pc)
I: No native package found for wireless-tools (/usr/include/wireless.h)

In debians version 4.8.1.1-10 this is fixed, since it is a minor patch it should be possible to get this update into ubuntu, would that be possible? Should I file a bug about it?

Here is the bug report on Debian: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=687339]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=687339")

---

### Post by cmcanulty on 2012-12-17
those error messages are different from mine. Mine kept saying libapt. missing and copying it to place didn't help. I could do nothing with apt or even open synaptic.

---


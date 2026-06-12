---
title: "[SOLVED] kindly hlep :- Can't run synaptic anymore"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by AceDip on 2008-10-29
I can not run synaptic anymore.when i try and open it it shows the following error messsage.

E: dpkg was interrupted,you must run 'dpkg --configure -a' to fix the problem.
E:_cache->open() failed,please report.
and that is it..
and when i run
```
:~$ sudo dpkg --configure -a
Setting up msttcorefonts (2.4) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--10:42:18--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=surfnet.dl.sourceforge.net [following]
--10:42:19--  http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=surfnet.dl.sourceforge.net
           => `./andale32.exe?download&failedmirror=surfnet.dl.sourceforge.net'
Resolving prdownloads.sourceforge.net... 216.34.181.60
Connecting to prdownloads.sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://master.dl.sourceforge.net/sourceforge/corefonts/andale32.exe [following]
--10:42:20--  http://master.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving master.dl.sourceforge.net... 216.34.181.56
Connecting to master.dl.sourceforge.net|216.34.181.56|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,98,384 (194K) [application/octet-stream]

20% [========>                                       ] 40,050        --.--K/s    ETA 1:05:24
```

and it never crosses the 20% mark and the ETA keeps on increasing and my synaptic does not work..

---

### Post by jimmy the saint on 2008-10-29
it sounds like a server issue.  apt is clearly trying to download a file, but the download is not completing.  Two instances of apt cannot run at the same time, which is why you cannot run synaptic (which is just a graphical interface for apt).  Try to hit <ctrl>+<C> to stop apt from running or just close the terminal window.  This is not ideal, but if it is stuck, it is stuck.

Good luck

---

### Post by bumanie on 2008-10-29
Try > sudo apt-get install msttcorefontsthey are in the repositories.

---

### Post by macogw on 2008-10-29
> **bumanie said:**
> Try they are in the repositories.

And that won't help anything because that's what they did before to get into this situation.  They download for a server when you install that package.  They just happen to be timing out on the download.

To cancel the package installation, maybe try
```
sudo aptitude purge msttcorefonts
```

---

### Post by AceDip on 2008-10-29
closing the terminal window doesn't stop the process.the error is there when you start the synaptic again.
But wait and watch does solve it.the process ends automatically when tried enough for the server..
thanks jimmy

---


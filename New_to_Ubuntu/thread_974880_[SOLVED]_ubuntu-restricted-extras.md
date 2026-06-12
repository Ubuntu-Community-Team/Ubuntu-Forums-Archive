---
title: "[SOLVED] ubuntu-restricted-extras????"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by bobigeorge on 2008-11-07
Hello everyone 

I just reinstalled ubuntu 8.04 in my laptop and tried ```
sudo apt-get install ubuntu-restricted-extras
``` But it returned with errors

```
Resolving switch.dl.sourceforge.net... 130.59.138.20
Connecting to switch.dl.sourceforge.net|130.59.138.20|:80... failed: Connection timed out.
Giving up.

andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Setting up ubuntu-restricted-extras (15.2) ...
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

And right now crash report is running.
Please post me some help..

Thanks in advance.

---

### Post by bobigeorge on 2008-11-07
I also tried 

```
sudo dpkg --configure -a
```

and 

```
sudo apt-get remove --purge ubuntu-restricted-extras
```

but all returned with errors

---

### Post by Yuki_Nagato on 2008-11-07
Are you plugged into an ethernet connection?  I doubt your wireless is working after a fresh install.

After confirming the presence of a wired internet connection, try updating the package list.

```

sudo apt-get update

```

Then installing the ubuntu-restricted-extras.

---

### Post by bobigeorge on 2008-11-07
yes i am working under a wifi proxy server. But my connection is allright. I can ```
sudo apt-get update
``` without errors.

---

### Post by alzie on 2008-11-08
Have you already double checked that your software sources are all enabled? (restricted and multiverse)

---

### Post by bobigeorge on 2008-11-08
Hello friends 

I have solved my problem. I had configured network proxy via apt.conf alone. Now I changed my System>Preferences>network proxy 

Thank you for your help.

---


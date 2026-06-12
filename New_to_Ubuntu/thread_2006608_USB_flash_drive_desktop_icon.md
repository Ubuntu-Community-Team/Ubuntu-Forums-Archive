---
title: "USB flash drive desktop icon?"
date: 2012-06-19
forum: New to Ubuntu
---

### Post by naragam on 2012-06-19
Another ubuntu newbie question....

How can I list the files on a USB flash drive? Where does it get reported when inserted into an available slot on the PC and what logical file system does it get mapped to? Just want to open and transfer files to/from home directory. Thanks in advance for any quick tips...

Nash

---

### Post by Kakers on 2012-06-19
Well there are two ways, using the GUI, open your home holder ad it should hopefully be listed on the site.
Or you can use the terminal and navigate to the media folder 'cd /media'.

---

### Post by Het Irv on 2012-06-19
If you open up a file browser, your devices should be listed in the top left.  Select it and click the small arrow just to the right.  That will expand the path and show you where the drive is mounted, (which will probably be /media/"name of removable media"

---

### Post by kanikilu on 2012-06-19
> **naragam said:**
> Where does it get reported when inserted into an available slot on the PC Do you mean where does it get logged? If so, when you plug in a removable device, it should show up in dmesg. After plugging in my flash drive and then typing ```
dmesg | tail
``` at the terminal, I see that it's being recognized as sdc1, in my case. Which goes to your next question:

> and what logical file system does it get mapped to? It should just take the next available as /dev/sdX (sda, sdb, sdc, sdd, etc.). As to where it gets mounted (mapped?), it should be in /media and the sub-directory will depend on a couple things.

If the partition has a volume name set, it may take that name. If it doesn't, it should use the UUID (an alphanumeric string of varying length).

For instance, one of my flash drives shows up as /media/IMAKEY, which is what I named my Lacie "key" drive. Another doesn't have a volume name, so it shows up as /media/4980-13E2...

---

### Post by naragam on 2012-06-19
Thanks people! I guess Ubuntu is really for Windows users and for an ancient unix hack (from SunOS days...lol) like me I need to start over if I want to make this a development platform.....sigh. 

Okay, I want to install and start experimenting with some free denovo sequencing s/w from UCSF and I have just loaded the c++ source code into my area. However, my assumption of an available dev environment on this Ubuntu 12.04 LTS is shot! I can't compile anything 'cos I don't have a g++ compiler and/or any complete C++ dev environment??

So, how do I go about making this new Ubuntu PC a c++ dev machine and I will probably just use xterms, tcsh/bash, perl, python, etc. and other command line unix tools. Any quick help is highly appreciated and please point me to available dev tool docs. 

Much thanks in advance,

Nash

---

### Post by Kakers on 2012-06-19
I know nothing about C++ coding, but this link may help you:
[http://www.wikihow.com/Compile-a-C/C%2B%2B-Program-in-Ubuntu](http://www.wikihow.com/Compile-a-C/C%2B%2B-Program-in-Ubuntu)

---

### Post by kanikilu on 2012-06-19
To install the basic development tools, start here:

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

And more information here:

[https://help.ubuntu.com/community/PowerUsersProgramming](https://help.ubuntu.com/community/PowerUsersProgramming)

---


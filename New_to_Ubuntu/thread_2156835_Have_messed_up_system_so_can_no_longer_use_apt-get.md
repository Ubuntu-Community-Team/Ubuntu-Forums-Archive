---
title: "Have messed up system so can no longer use apt-get."
date: 2013-06-23
forum: New to Ubuntu
---

### Post by zozza on 2013-06-23
I have messed up somehow my 10.04 system.

I no longer can use programs that were made with Python.

I get the same errors as shown below which happen whenever I use apt-get install whatever:

Setting up python-gmenu (2.30.0-0ubuntu4) ...
Rebuilding /usr/share/applications/desktop.en_GB.utf8.cache...
  File "/usr/share/gnome-menus/update-gnome-menus-cache", line 48
    except ParsingError, e:
                       ^
SyntaxError: invalid syntax
  File "/usr/sbin/update-python-modules", line 52
    print x
          ^
SyntaxError: invalid syntax
dpkg: error processing python-gmenu (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up python-desktop-agnostic (0.3.90-0ubuntu1) ...
  File "/usr/sbin/update-python-modules", line 52
    print x
          ^
SyntaxError: invalid syntax
dpkg: error processing python-desktop-agnostic (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up ocaml-base-nox (3.11.2-1) ...

Setting up headache (1.03-18) ...
Errors were encountered while processing:
 python-gmenu
 python-desktop-agnostic
E: Sub-process /usr/bin/dpkg returned an error code (1)

Also, there is the red circle in the panel which says "an error occurred when checking for updates."

It looks like there is a problem with Python.  Whereis python shows:

/usr/bin/python3.1 /usr/bin/python /etc/python3.1 /usr/lib/python3.1 /usr/local/lib/python3.1 /usr/include/python3.1 /usr/share/python /usr/share/man/man1/python.1.gz

Can any kind soul please tell me how I can rectify this problem?

---

### Post by grahammechanical on 2013-06-23
This I think has something to do with the problem

> [COLOR=#000000]my 10.04 system[/COLOR]

Is this a server installation? If it is a desktop, then 10.04 is now at End of Life. For a few weeks it has been possible to get updates. Three weeks ago I put in a new install of 10.04.4 and I was able to update it after the first boot. But at some point the repositories are moved into an archive. 

[http://www.ubuntu.com/releaseendoflife](http://www.ubuntu.com/releaseendoflife)

Run

```
ubuntu-support-status
```

you may find it interesting reading.

Regards.

---

### Post by fantab on 2013-06-23
I hope you realize that 10.04 has reached its 'end of life', no more Ubuntu support for the 'eol' versions, especially NO Security Updates. If I were you I would install either 12.04 or 13.04.

Meanwhile try:
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
sudo apt-get upgrade 

I am not really sure if the update/upgrade will work.

---

### Post by zozza on 2013-06-23
bash: /usr/bin/ubuntu-support-status: /usr/bin/python2.6: bad interpreter: No such file or directory

This makes sense - it wants python 2.6 but python 2.6 is no longer in the /usr/bin/ directory.  It's only 3.1 now.

However, my problem is that I cannot install 2.6. 

Can anything be done about this?  Thanks again!

---

### Post by CharlesA on 2013-06-23
I guess you could try installing it from the archived repos, but I don't think that's a good idea as you know (now) that 10.04 is End of Life.

See here: 
[https://help.ubuntu.com/community/PreciseUpgrades](https://help.ubuntu.com/community/PreciseUpgrades)

---

### Post by grahammechanical on 2013-06-23
This might help you

[http://askubuntu.com/questions/101479/are-existing-updates-available-after-end-of-support](http://askubuntu.com/questions/101479/are-existing-updates-available-after-end-of-support)

Regards,

---

### Post by zozza on 2013-06-23
Thanks for the advice - I will install 12.04

---


---
title: "A Problem with Python: Programs Not Running"
date: 2013-01-30
forum: New to Ubuntu
---

### Post by YellowYush on 2013-01-30
Hi! I am very new to Ubuntu and I downloaded Python 3.2 recently. However, I put Python 3 as my (default), and originally it was Python 2.7.3. After this change, I couldn't run programs that relied on Python, such as the Ubuntu Software Center or Bleachbit. Also, I have noticed that there is no file or directory in /usr/bin/python. This appears to be a big problem, as I heard that changing default Python versions could cause system instability. Anyhow, I run on Ubuntu 12.04. Is there any way I can resolve this issue. Do I have to re install Ubuntu, or is there a way to fix this brokenness? Sorry, I am a novice in this field. Any help would be appreciated! Thanks! :p

---

### Post by steeldriver on 2013-02-23
You could try following drmgd's advice using update-alternatives here --> [http://ubuntuforums.org/showpost.php?p=12143825&postcount=6](http://ubuntuforums.org/showpost.php?p=12143825&postcount=6) 

If you originally set python3 to be the default using update-alternatives then you should be able to change to 2.7 that way as well i.e.

```
$ sudo update-alternatives --config python
```

and follow the instructions. If you *didn't* use update-alternatives before, then you may need to configure it manually e.g.

```

$ ls -l $(which python)
lrwxrwxrwx 1 root root 9 Oct 31 15:11 /usr/bin/python -> python2.7
$ 
$ ls -l $(which python3)
lrwxrwxrwx 1 root root 9 Apr 15  2012 /usr/bin/python3 -> python3.2
$ 
$ sudo update-alternatives --install /usr/bin/python python /usr/bin/python3.2 10
[sudo] password for steeldriver: 
update-alternatives: using /usr/bin/python3.2 to provide /usr/bin/python (python) in auto mode.
$ sudo update-alternatives --install /usr/bin/python python /usr/bin/python2.7 20
update-alternatives: using /usr/bin/python2.7 to provide /usr/bin/python (python) in auto mode.
$ 
$ update-alternatives --list python
/usr/bin/python2.7
/usr/bin/python3.2
$ sudo update-alternatives --config python
There are 2 choices for the alternative python (providing /usr/bin/python).

  Selection    Path                Priority   Status
------------------------------------------------------------
* 0            /usr/bin/python2.7   20        auto mode
  1            /usr/bin/python2.7   20        manual mode
  2            /usr/bin/python3.2   10        manual mode

Press enter to keep the current choice
[*], or type selection number: 
$
```

---


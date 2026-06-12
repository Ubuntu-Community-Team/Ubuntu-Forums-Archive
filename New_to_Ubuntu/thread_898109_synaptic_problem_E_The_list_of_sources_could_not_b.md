---
title: "synaptic problem: E: The list of sources could not be read."
date: 2008-08-22
forum: New to Ubuntu
---

### Post by waltclay on 2008-08-22
I can't get past this error report in synaptic

> E: Malformed line 56 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

In /etc/apt/ I find 3 files

1. medibuntu.list
> ## Medibuntu - Ubuntu 7.10 "gutsy gibbon"
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free
# deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free

2. medibuntu.list.distUpgrade
> ## Medibuntu - Ubuntu 7.10 "gutsy gibbon"
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free
#deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free

3. medibuntu.list.save
> ## Medibuntu - Ubuntu 7.10 "gutsy gibbon"
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free
# deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free

I am using Heron.

What is the repository dialog?

Please advise how to proceed.

---

### Post by iaculallad on 2008-08-22
The error did not mention medibuntu.list but instead, it pointed to /etc/apt/sources.list file:

Post the content of your /etc/apt/sources.list:

```
cat /etc/apt/sources.list
```

Or you could manually check line 56 for yourself.

---

### Post by waltclay on 2008-08-23
An 'ls' of /etc/apt/sources.list had 49 lines by my count.
An 'ls' of /etc/apt/sources.list.save appears to be identical.

The listings have 7 totally blank lines. 49+7=56

Here are the last few lines, where I added '[49]'.
> deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse 
[49]deb [http://ppa.launchpad.net/abiword-stable/ubuntu/hardy](http://ppa.launchpad.net/abiword-stable/ubuntu/hardy) main


I have no idea what to do next.

---

### Post by iaculallad on 2008-08-23
> **waltclay said:**
> An 'ls' of /etc/apt/sources.list had 49 lines by my count.
An 'ls' of /etc/apt/sources.list.save appears to be identical.

The listings have 7 totally blank lines. 49+7=56

Here are the last few lines, where I added '[49]'.


I have no idea what to do next.

Try to post your /etc/apt/sources.list file:

```
cat /etc/apt/sources.list
```

---

### Post by nothingspecial on 2008-08-23
I think your problem is that you`re on Hardy but you`ve got Gutsy`s Medibuntu repositories in you sources list.

```
gksudo gedit /etc/apt/sources.list
```

Where it says

```

deb http://packages.medibuntu.org/ gutsy free non-free
deb-src http://packages.medibuntu.org/ gutsy free non-free
```

Change gutsy to hardy in both lines. Save then close.

Then make sure you`ve added the medibuntu key and update -

```

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

That should work.

---

### Post by waltclay on 2008-08-24
Apologies to all who viewed my confused previous posts, especially those who helped.

In applications>accessories>terminal
```
gksudo gedit /etc/apt/sources.list
```

Inserted ## in front of last statement
> deb [http://ppa.launchpad.net/abiword-stable/ubuntu/hardy](http://ppa.launchpad.net/abiword-stable/ubuntu/hardy) main
to make it a comment. I assume that means abi won't be updated, but that will have to wait until it is hardy ready and that url does not give 404 file not found error.

Other references to gutsy were all in comments, so I left them. Synaptic now runs.

I finished by executing in termial 
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O-
sudo apt-key add - 
sudo apt-get update
```

Considering that this absolute beginners forum, I think we should be detailed on use of terminal.

Thanks for helping.

---

### Post by bodhi.zazen on 2008-08-24
> **iaculallad said:**
> The error did not mention medibuntu.list but instead, it pointed to /etc/apt/sources.list file:

Post the content of your /etc/apt/sources.list:

```
cat /etc/apt/sources.list
```Or you could manually check line 56 for yourself.

LOL

```
cat -n /etc/apt/sources.list | grep 56
```

---

### Post by exalt08 on 2008-09-30
hi guys, 
i myself also in the same trouble but this time is in line 1. How to deal with it? Please help.

E:Type '--23:30:25--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to repository dialog to correct the problem.
E: _cache->open()failed,please report.

---

### Post by oldos2er on 2008-09-30
> **exalt08 said:**
> hi guys, 
i myself also in the same trouble but this time is in line 1. How to deal with it? Please help.

E:Type '--23:30:25--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to repository dialog to correct the problem.
E: _cache->open()failed,please report.

 Please post the output of the command "cat /etc/apt/sources.list.d/medibuntu.list"

---

### Post by exalt08 on 2008-10-01
--23:30:25--  [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list)
           => `gutsy.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 223 [text/plain]

    0K                                                       100%   27.19 MB/s

23:30:32 (27.19 MB/s) - `gutsy.list' saved [223/223]

---


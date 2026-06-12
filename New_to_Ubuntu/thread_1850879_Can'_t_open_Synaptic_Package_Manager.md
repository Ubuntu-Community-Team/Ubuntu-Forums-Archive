---
title: "Can' t open Synaptic Package Manager"
date: 2011-09-27
forum: New to Ubuntu
---

### Post by azrri on 2011-09-27
cant open synaptic package manager

E: Malformed line 28 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.

---

### Post by nomko on 2011-09-27
> **azrri said:**
> cant open synaptic package manager
 
E: Malformed line 28 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
 
 
You marked this thread as solved.
 
How did you solved your problem?? i think everybody would like to know this.

---

### Post by CharlesA on 2011-09-27
The problem was more then likely a misedit in the sources.list file.

---

### Post by nomko on 2011-09-27
> **CharlesA said:**
> The problem was more then likely a misedit in the sources.list file.

Then again, was it a misedit? I'm curious....

---

### Post by ikt on 2011-09-27
> **nomko said:**
> Then again, was it a misedit? I'm curious....

There's very little else it can be.

---

### Post by Old_Grey_Wolf on 2011-09-27
The thread is not marked as solved now.

If the OP could post the output of the following command then we can determine what the problem is:
```
cat /etc/apt/sources.list
```

---

### Post by azrri on 2011-09-28
```
cat /etc/apt/sources.list
## Add comments (##) in front of any line to remove it from being checked.
## Use the following sources.list at your own risk.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty universe multiverse main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty universe multiverse main restricted #Added by software-properties
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) natty free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) natty free non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) maverick contrib
deb-src [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) maverick contrib
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) natty contrib
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) natty 
contrib
```
sorry i marked as solve..i am new here...its happen after i start to install medibuntu...

---

### Post by CharlesA on 2011-09-28
dapper repos? That sources.list doesn't look right at all.

---

### Post by nomko on 2011-09-28
> **CharlesA said:**
> dapper repos? That sources.list doesn't look right at all.

He's using dapper, Natty and maverick repos mixed up........ :confused:

The only thing what happened here is that he selected the wrong version when he was adding that specific repo. 

**@Azrri:**
Are you using Ubuntu 6.06 Dapper as operating system? OR some other Ubuntu version? Please provide us whit the correct Ubuntu version.

---

### Post by mörgæs on 2011-09-28
This looks like a computer which has been upgraded **many** times. I would go for a fresh install.

---

### Post by Old_Grey_Wolf on 2011-09-28
To find out what version you are using enter this command and post the output here:
```
cat /etc/*release
```

Once we know, someone can tell you how to generate a new sources.list file.

---

### Post by mörgæs on 2011-09-28
Sources.list can be built using this:
[http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)

However, a fresh install might be faster.

---

### Post by Old_Grey_Wolf on 2011-09-28
> **mörgæs said:**
> Sources.list can be built using this:
[http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)

However, a fresh install might be faster.

If the OP is really using version 6.06 then an fresh install is probably the best answer unless you have a lot of experience.

The OP still needs to determine what version is installed to know if it is supported, determine what to enter in the link you provided, and receive instructions on what to do with the generated file.

Considering the contents of the sources.list file, I thought it would be best to help the OP solve the problem on small step at a time.

 :)

---

### Post by azrri on 2011-10-02
previously im using ubuntu 11.04 natty beta release...but since this problem appear and give me alot of problem to my system, i download again ubuntu 11.04 and reboot. Since everything is new, my system is running smoothly now...thanks guys for your helps..

---

### Post by mörgæs on 2011-10-02
Good, then please mark the thread 'solved' using 'thread tools'.

---


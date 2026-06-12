---
title: "Sybase ASE Express edition"
date: 2007-11-07
forum: Programming Talk
---

### Post by polomint on 2007-11-07
Hello,

Just wondering if anyone has managed to install the free edition of Sybase ASE 15.0.2 for linux? 

I've followed the instructions from here:
[http://www.peppler.org/linux-install.html](http://www.peppler.org/linux-install.html)
and 
[http://www.peppler.org/FAQ/linux.html](http://www.peppler.org/FAQ/linux.html)

but got stuck on the stage where the installer builds the master database. no matter what I try it always segfaults. setting the LD_POINTER_GUARD enviroment variable to 0 or 1 as suggested by some ppl did help either.

any help would be appreciated!

---

### Post by gritsul on 2008-01-14
Bad news: It will not work. Because of the libc.

It seems it will not work on fresh distro's of Suse and Fedora too.

So better forget about it.

Use Postgress instead.

---

### Post by ghostdog74 on 2008-01-14
you can still download the [11.9.2 versoin]("http://www.sybase.com/detail?id=1011127") and have a try on it.

---

### Post by redbull_monsta on 2008-04-03
the error is caused because aswell as libaio you will also need libaio_devel installed

I know as i used to work for Sybase :)

However ASE 15 was compiled on an older version of glibc so your mileage may vary 

I have had it running on 6.10 and 7.04

Regards

Redbull

---

### Post by taihoanh on 2008-05-04
Hello,

does it mean that Sybase will probably NOT work on Ubuntu Hardy Heron ?

Thanks for your answers.

---

### Post by jackos on 2008-06-27
This should work fine now:

[http://blogs.sybase.com/master/master_04290804.asp](http://blogs.sybase.com/master/master_04290804.asp)

Cheers
Jackos

---

### Post by hans.kramer@xs4all.nl on 2009-04-16
[www.happy-hacking.com](www.happy-hacking.com) has the solution for you:

[http://www.happy-hacking.com/index.php/Sybase_ASE_15.0.2_on_Ubuntu](http://www.happy-hacking.com/index.php/Sybase_ASE_15.0.2_on_Ubuntu)

---

### Post by cw19 on 2009-09-19
Hi,
To fix the problem is a very simple matter. 
 ASE requires at least 64 MB of shared memory. To increase, for example, 256 MB, you must add the line: 
 ```
kernel.shmmax = 268435456
``` to /etc/sysctl.conf 
 Then load the setup command: 
 ```
/sbin/sysctl -p 
``` That's all. 
 Regards, Bogdan cw19.

---

### Post by JonEK90 on 2009-12-02
Hi all,

just to let you know that I am using 9.10 (Karmic Koala).
(I am VERY new to Ubuntu - but been around UNIX for a long time.)

I was able to make the current release of Sybase ASE (free) which is 15.0.3 ESD#1 work out of the box.

It requires the package libaio1 to be installed and shmmax to be set (as described above).

The the installer will run without problems.

Have fun with it,
 - jon.

---

### Post by lakshman_ab on 2009-12-11
Hi folks,
I'm new to Ubuntu but familiar with UNIX. 
I'm in the process of installing the developers edition of ASE 15.0.3 on Karmic Koala (9.10) and have a few questions.

kernel.shmmax = 268435456
sudo apt-get install build-essential libaio1 # Fix libaio issue

1) I've created a 'sybase' user via the menus but I'm unable to run xterm under it.  On my main ubuntu account xterm works (DISPLAY=:0.0) fine.  What should be the display variable for the new SYBASE user?
sybase@ubuntu:~$ export DISPLAY=:0.0
sybase@ubuntu:~$ xterm
No protocol specified
xterm Xt error: Can't open display: :0.0

2) Is it OK to use sudo to run the ASE installation as /opt needs root write perms?
    sudo ./setup # ASE installation program

---

### Post by lakshman_ab on 2009-12-12
Here is the solution for the xterm issue:
[LIST=1]
[*]Login as the ubuntu user created during system installation
[*]At the shell prompt enter: xhost + so that clients can connect from any host
[/LIST]

To carry on with the SYBASE installation:
1) su - sybase
2) sudo rm -rf /opt/sybase # Delete ASE installation done as root
3) sudo mkdir /opt/sybase
4) chown sybase /opt/sybase
5) chgrp sybase /opt/sybase
6) ./setup # Run ASE installation without sudo logged in as 'sybase'
7) . /opt/sybase/SYBASE.sh # set the env for ksh
8) export LANG=en_GB # reset LANG so that isql doesn't whinge

isql -U sa -S UBUNTU -P ""
1>select db_name()
go


ASE 15.0.3 on Karmic Koala (9.10) now sorted!

---

### Post by lakshman_ab on 2009-12-12
Duplicate post and hence, deleted

---

### Post by sthaupt on 2010-04-22
> **lakshman_ab said:**
> 
To carry on with the SYBASE installation:
1) su - sybase
2) sudo rm -rf /opt/sybase # Delete ASE installation done as root
3) sudo mkdir /opt/sybase
4) chown sybase /opt/sybase
5) chgrp sybase /opt/sybase
6) ./setup # Run ASE installation without sudo logged in as 'sybase'
!

Hi, as a long-time-with-sybase-dealing guy let me comment these steps:
- you don't need to have an extra user/group ("sybase") for running ASE
- if ase was already installed, leave it on disk; just take steps 4 and 5. They also can be done in one command: chown -R sybase:sybase /opt/sybase

chown -R \                                 # for recursion on subdirectories
<yourUser>:<yourGroup> \        # telling user AND group to the command
<yourInstDir>

Good luck

---

### Post by WitchCraft on 2010-12-19
See here:

[http://ubuntuforums.org/showthread.php?p=10255354#post10255354](http://ubuntuforums.org/showthread.php?p=10255354#post10255354)

---

### Post by gochilla on 2011-10-28
I managed to install sybase on Ubuntu server 11.10... maybe it helps. Install ubuntu server (no extra packages selected).

Setting up ASE 15.7 on Ubuntu Server 11.10 (64it)

Preparing the Linux System

```

    sudo su
    #adjust shared mem space (as documented in install requirements)
    echo "kernel.shmmax=1073741824" >> /etc/sysctl.conf
    sysctl -w kernel.shmmax=1073741824
    cd
    apt-get install libxp-dev
    apt-get install libxt-dev
    apt-get install libxtst-dev
    apt-get install libxmu-dev
    apt-get install libxext-dev
    apt-get install libsm-dev
    apt-get install libice-dev
    apt-get install libx11-dev
    apt-get install libaio-dev
    apt-get install dkms build-essential alien
    apt-get install openjdk-6-jdk
    apt-get install ia32-libs
    #pull openmotif RPM http://www.openmotif.org/files/public_downloads/openmotif/2.3/2.3.0/openmotif-2.3.0-1.rhel4.x86_64.rpm
    alien -d openmotif-2.1.30-1.rhel4.x86_64.rpm
    #this generates openmotif_2.3.0-2_amd64.deb on my system... now install with dpkg -i
    dpkg -i openmotif_2.3.0-2_amd64.deb
    #create sybase install user + directories
    mkdir /opt/sybase
    mkdir /opt/sybasesetup
    useradd -s /bin/bash -M -d /opt/sybase sybase
    chown sybase.sybase /opt/sybase*
    
    su sybase
    cd /opt/sybasesetup
    #pull http://download.sybase.com/eval/157/ase157_linuxx86-64.tgz and copy to sybasesetup
    tar xzf ase157_linuxx86-64.tgz
    ./setup.bin



```

---

### Post by gochilla on 2011-11-04
I struggled to get ASE and PAM auth running on Ubuntu. In hope this might help other users:

1) Prepare PAM. Create a the file [FONT=Courier New]/etc/pam.d/ase[/FONT][FONT=Arial] with the following contents
[/FONT]```

auth required pam_unix.so

```2) Assuming your sybase process user is called *sybase*, **you must add this user to the *shadow* group** in order to get PAM going. Do so by issuing
```

root@sybase# usermod -a -G shadow sybase

```3) Enable PAM authentication in sybase. I assume sybase is installed in [FONT=Courier New]/opt/sybase[/FONT]
```

sybase@sybase:~$ cd /opt/sybase
sybase@sybase:/opt/sybase$ . SYBASE.sh
sybase@sybase:/opt/sybase$ isql -U sa
Password:
1> sp_configure "enable pam user auth",2
2> go
...
1> quit

```This should get PAM up and running... now we can test it.
1) create a system user
```

sybase@sybase:~# useradd -MN sybtest
sybase@sybase:~# passwd sybtest
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
sybase@sybase:~#

```2) create a sybase login (login as *sybase* user)
```

sybase@sybase:~$ cd /opt/sybase
sybase@sybase:/opt/sybase$ . SYBASE.sh
sybase@sybase:/opt/sybase$ isql -U sa
Password:
1>create login sybtest with password anypass
2>go
1>quit

```3) tryout the new login (login as sybase user) **use the unix password for the isql login!**
```

sybase@sybase:~$ cd /opt/sybase
sybase@sybase:/opt/sybase$ . SYBASE.sh
 sybase@sybase:/opt/sybase$ isql -U sybtest
Password:
1>

```AAAAAAAAAAAAaaaaand we are done! have fun!

---


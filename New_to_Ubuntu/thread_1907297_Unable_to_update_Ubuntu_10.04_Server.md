---
title: "Unable to update Ubuntu 10.04 Server"
date: 2012-01-11
forum: New to Ubuntu
---

### Post by &#1052;&#1086;&#1093;&#1085;&#1072;&#1090;&#1099;&#1081; on 2012-01-11
Hello!
I'm trying to update my Ubuntu 10.04 Server.
This is my console log:

```

Preparing to replace sysv-rc 2.87dsf-4ubuntu17 (using .../sysv-rc_2.87dsf-4ubuntu17.4_all.deb) ...
Unpacking replacement sysv-rc ...
dpkg: error processing /var/cache/apt/archives/sysv-rc_2.87dsf-4ubuntu17.4_all.deb (--unpack):
 unable to make backup link of `./etc/init.d/rc' before installing new version: Operation not permitted
Preparing to replace udev 151-12 (using .../udev_151-12.3_amd64.deb) ...
Adding `local diversion of /sbin/udevadm to /sbin/udevadm.upgrade'
Unpacking replacement udev ...
Preparing to replace dmsetup 2:1.02.39-1ubuntu4 (using .../dmsetup_2%3a1.02.39-1ubuntu4.1_amd64.deb) ...
Unpacking replacement dmsetup ...
Preparing to replace plymouth 0.8.2-2ubuntu2 (using .../plymouth_0.8.2-2ubuntu2.2_amd64.deb) ...
Unpacking replacement plymouth ...
Preparing to replace libpng12-dev 1.2.42-1ubuntu2.1 (using .../libpng12-dev_1.2.42-1ubuntu2.2_amd64.deb) ...
Unpacking replacement libpng12-dev ...
Preparing to replace libpng12-0 1.2.42-1ubuntu2.1 (using .../libpng12-0_1.2.42-1ubuntu2.2_amd64.deb) ...
Unpacking replacement libpng12-0 ...
Preparing to replace libplymouth2 0.8.2-2ubuntu2 (using .../libplymouth2_0.8.2-2ubuntu2.2_amd64.deb) ...
Unpacking replacement libplymouth2 ...
Preparing to replace mountall 2.15 (using .../mountall_2.15.3_amd64.deb) ...
Unpacking replacement mountall ...
Preparing to replace upstart 0.6.5-6 (using .../upstart_0.6.5-8_amd64.deb) ...
Unpacking replacement upstart ...
Preparing to replace mysql-server-core-5.1 5.1.41-3ubuntu12.3 (using .../mysql-server-core-5.1_5.1.41-3ubuntu12.10_amd64.deb) ...
Unpacking replacement mysql-server-core-5.1 ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Errors were encountered while processing:
 /var/cache/apt/archives/sysv-rc_2.87dsf-4ubuntu17.4_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

Now i cannot fix it :-(
Thank's

---

### Post by sioxs on 2012-10-18
[http://ubuntuforums.org/showthread.php?t=1221323&highlight=ubuntu+signing+keys](http://ubuntuforums.org/showthread.php?t=1221323&highlight=ubuntu+signing+keys)

---

### Post by Wim Sturkenboom on 2012-10-18
> **sioxs said:**
> [http://ubuntuforums.org/showthread.php?t=1221323&highlight=ubuntu+signing+keys](http://ubuntuforums.org/showthread.php?t=1221323&highlight=ubuntu+signing+keys)
That's about gpg keys; how does that help OP? Did I miss something?

---

### Post by sioxs on 2012-10-18
I had similar error messages today using both the update manager apt-get and dpkg
There were several issues one of a bad sig from the master server and an error about not being able to install a package "with a operation not permitted" error CODE 1
```
Reading package lists... Done
:~# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  login
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/291 kB of archives.
After this operation, 4,096 B disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 286566 files and directories currently installed.)
Preparing to replace login 1:4.1.4.2+svn3283-3ubuntu5 (using .../login_1%3a4.1.4.2+svn3283-3ubuntu5.1_amd64.deb) ...
Unpacking replacement login ...
dpkg: error processing /var/cache/apt/archives/login_1%3a4.1.4.2+svn3283-3ubuntu5.1_amd64.deb (--unpack):
 unable to make backup link of `./bin/login' before installing new version: Operation not permitted
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/login_1%3a4.1.4.2+svn3283-3ubuntu5.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```It's all good now so I thought to pass on what I did hopefully it will solve this issue for you and others.
1st rebuild the Mergelist in apt-get
```
 $ sudo -i
# rm -rf /var/lib/apt/lists/*
# apt-get update

```or you could do
```

$ sudo -i
# apt-get clean
# cd /var/lib/apt
# mv lists lists.old
# mkdir -p lists/partial
# apt-get clean
# apt-get update

```That should take care of the pgp signature issues.

2. Next you want to check what's causing the permission errors for the packages that refuse to install properly in my case is was  the 
"login   1:4.1.4.2+svn3283-3ubuntu5" package so I'll use that as an example.
```

$ # lsattr /bin/login 
----i--------e- /bin/login

```As you can see login has been set to immutable since it changes infrequently and needs to be protected. The "e" attribute is for extent format and need not be changed.
The solution was simply to remove the -i attribute for the install and re-apply the attribute after a successful  installation.
```

$ sudo -i
# chattr -i /bin/login
# apt-get upgrade
[CODE] Preparing to replace login 1:4.1.4.2+svn3283-3ubuntu5 (using .../login_1%3a4.1.4.2+svn3283-3ubuntu5.1_amd64.deb) ...
Unpacking replacement login ...
Processing triggers for man-db ...
Setting up login (1:4.1.4.2+svn3283-3ubuntu5.1) ...
```# chattr +i /bin/login
# lsattr /bin/login
----i--------e- /bin/login
[/CODE]Problem solved

---

### Post by sioxs on 2012-10-18
My bad 
Had the same issue as the thread title and a BADSIG error. I had the page open while I was searching for an answer and must have Ctrl + V in the post instead of the location field 
Got the problem straightened out now and included the fix here.
 
[COLOR=Red]*"if we did all the things we are capable of doing we would literally astound ourselves"   *[/COLOR]

---

### Post by Wim Sturkenboom on 2012-10-19
sioxs, thanks for sharing. I hope it helps the OP

---


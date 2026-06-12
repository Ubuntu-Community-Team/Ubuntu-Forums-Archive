---
title: "trouble the minute i started using terminal"
date: 2012-07-01
forum: New to Ubuntu
---

### Post by godfreezone on 2012-07-01
Suitably embarrassed.

could some kind person decipher the following out put for when I typed 
sudo adduser rachel admin 
at CL,
thanks 
```

```  p, li { white-space: pre-wrap; }  godfree@Greg:/$ sudo adduser rachel admin
 sudo: >>> /etc/sudoers: /etc/sudoers/etc/passwd: Not a directory near line 28 <<<
 sudo: parse error in /etc/sudoers near line 28
 sudo: no valid sudoers sources found, quitting
 sudo: unable to initialise policy plugin
 godfree@Greg:/$ 
 ```

```


I was trying to do a simple job: encrypt my home directory
I got into sudo visudo, followed some directions to edit the /etc/sudoers/temp to etc/sudoers/passwd and must have made an error.


Thks for any assistance,
Godfree

---

### Post by godfreezone on 2012-07-02
I have posted to general with this, some 6 hours ago.
(I hope i can be excused for trying beginners, after waiting 1/4 of a day)

is anyone online able to help me fix it?

---

### Post by NikTh on 2012-07-02
What is the problem exactly ? Can you use sudo or not ?
What did you do and corrupted sudoers file ? 

Can you post the result of this command ? 
```
pkexec cat /etc/sudoers
```

---

### Post by nothingspecial on 2012-07-02
Threads merged.

Please do not multi-post. If you think your thread will get more attention in a different section, use the report button and one of the staff will move it.

Thanks.

---

### Post by godfreezone on 2012-07-02
> **NikTh said:**
> What is the problem exactly ? Can you use sudo or not ?
What did you do and corrupted sudoers file ? 

Can you post the result of this command ? 
```
pkexec cat /etc/sudoers
```

thx for the help, here it is

```
godfree@Greg:/$ pkexec cat /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults    env_reset
Defaults    secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL:ALL) ALL
rachel  ALL=(ALL:ALL) ALL
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo    ALL=(ALL:ALL) ALL

# See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers/etc/passwd
godfree@Greg:/$
```

---

### Post by godfreezone on 2012-07-02
The trouble started when I tried to use terminal to encrypt home directory.
This is what I did
```

godfree@Greg:~$ sudo apt-get install ecryptfs-utils
[sudo] password for godfree: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
godfree@Greg:~$ sudo apt-get install ecryptfs-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  language-pack-zh-hans kde-l10n-de language-pack-kde-de language-pack-kde-en
  language-pack-de-base language-pack-kde-zh-hans language-pack-kde-en-base
  kde-l10n-engb language-pack-kde-de-base kde-l10n-zhcn firefox-locale-de
  language-pack-zh-hans-base firefox-locale-zh-hans language-pack-de
  language-pack-kde-zh-hans-base
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  cryptsetup keyutils libecryptfs0 libnss3-1d
Suggested packages:
  busybox opencryptoki keyescrow-client
The following NEW packages will be installed:
  cryptsetup ecryptfs-utils keyutils libecryptfs0 libnss3-1d
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 273 kB of archives.
After this operation, 1,213 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise/main cryptsetup i386 2:1.4.1-2ubuntu4 [79.1 kB]
Get:2 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise/main libecryptfs0 i386 96-0ubuntu3 [48.0 kB]
Get:3 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise/main keyutils i386 1.5.2-2 [34.1 kB]
Get:4 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise/main libnss3-1d i386 3.13.1.with.ckbi.1.88-1ubuntu6 [13.4 kB]
Get:5 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise/main ecryptfs-utils i386 96-0ubuntu3 [98.0 kB]
Fetched 273 kB in 3s (80.5 kB/s)     
Preconfiguring packages ...
Selecting previously unselected package cryptsetup.
(Reading database ... 187487 files and directories currently installed.)
Unpacking cryptsetup (from .../cryptsetup_2%3a1.4.1-2ubuntu4_i386.deb) ...
Selecting previously unselected package libecryptfs0.
Unpacking libecryptfs0 (from .../libecryptfs0_96-0ubuntu3_i386.deb) ...
Selecting previously unselected package keyutils.
Unpacking keyutils (from .../keyutils_1.5.2-2_i386.deb) ...
Selecting previously unselected package libnss3-1d.
Unpacking libnss3-1d (from .../libnss3-1d_3.13.1.with.ckbi.1.88-1ubuntu6_i386.deb) ...
Selecting previously unselected package ecryptfs-utils.
Unpacking ecryptfs-utils (from .../ecryptfs-utils_96-0ubuntu3_i386.deb) ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Setting up cryptsetup (2:1.4.1-2ubuntu4) ...
update-initramfs: deferring update (trigger activated)
Setting up libecryptfs0 (96-0ubuntu3) ...
Setting up keyutils (1.5.2-2) ...
Setting up libnss3-1d (3.13.1.with.ckbi.1.88-1ubuntu6) ...
Setting up ecryptfs-utils (96-0ubuntu3) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-26-generic-pae
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
```

And that was where I opened another window to try to create a dummy account ie Rachel, as per advice received on a howto page, in order to encrypt the home directory while acting as root under Rachel, not me.

---

### Post by godfreezone on 2012-07-02
With apologies to all: for the last 2 posts I used what I thought was the appropriate symbol to wrap that longish bit of code...
```

```  and ended with ```

```

but it didn't seem to work

(I'm trying here.....
but i'm at my wits' end ... which is discouraging, having only been at it for 2 days or so..)

---

### Post by nothingspecial on 2012-07-02
> **godfreezone said:**
> With apologies to all: for the last 2 posts I used what I thought was the appropriate symbol to wrap that longish bit of code...
```

```  and ended with ```

```

but it didn't seem to work

(I'm trying here.....
but i'm at my wits' end ... which is discouraging, having only been at it for 2 days or so..)


Highlight the text you wish to surround in code tags, then click the # in the formatting options at the top of the posting box.

---

### Post by godfreezone on 2012-07-02
> **nothingspecial said:**
> Highlight the text you wish to surround in code tags, then click the # in the formatting options at the top of the posting box.

```
godfree@Greg:/$ sudo sudoers
sudo: >>> /etc/sudoers: /etc/sudoers/etc/passwd: Not a directory near line 28 <<<
sudo: parse error in /etc/sudoers near line 28
sudo: no valid sudoers sources found, quitting
sudo: unable to initialise policy plugin
godfree@Greg:/$ 
```

Like that? You wouldn't have a suggestion for me too would you?

---

### Post by godfreezone on 2012-07-10
I re-installed.

No  problem, no learning, no gain.

Godfree

---


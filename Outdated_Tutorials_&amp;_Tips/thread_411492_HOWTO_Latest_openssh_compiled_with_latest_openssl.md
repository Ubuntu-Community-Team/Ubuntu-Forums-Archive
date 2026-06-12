---
title: "HOWTO: Latest openssh compiled with latest openssl"
date: 2007-04-16
forum: Outdated Tutorials &amp; Tips
---

### Post by helmet on 2007-04-16
Ubuntu is pretty good about updating software, but sometimes you just want the latest. This howto will show you how to compile and install the latest openssh (4.6p1 at the time of writing) with the latest openssl library (0.9.8e at the time of writing).

**DISCLAIMER**

This worked flawlessly on my setup: Ubuntu server 6.10 x86
Your mileage may vary. It's probably a good idea to do this on a machine you have direct access (keyboard,mouse,monitor) to or at least have webmin installed (with webmin you can run commands to fix things). I can provide some basic "try this" support, but for the most part you're on your own. More than likely everything will be fine. The nice part is at least if you are logged in with ssh, you can still install and restart the server and stay logged in. w00t! :D 

First, install some important tools. I'm not sure about *all* the packages you need to compile this, but usually build-essential does the the trick for most things. (Run things in code blocks on the command line, in a program like *konsole* or *terminal*)

```
sudo aptitude install build-essential libpam-dev
```

If you get any errors at any point about command not found or anything, leave a comment and I'll update the howto with the new information. You can try just 'apt-get'ing the software it claims to be missing.

So anyway, let's get started.

Make a directory to work in:

```
cd && mkdir dev && cd dev
```

Now let's download the latest openssl.

```
wget -c http://www.openssl.org/source/openssl-0.9.8e.tar.gz
```

And while we are in a downloading mood, let's get the latest openssh package.

```
wget -c ftp://ftp.openbsd.org/pub/OpenBSD/OpenSSH/portable/openssh-4.6p1.tar.gz
```

Again, these are the latest at the time of writing, so for newer release head over the the websites and go to the download section to find out what the latest is, and download that.

[OpenSSL]("http://www.openssl.org/")
[OpenSSH]("http://openssh.org/")

Unpack the archives:

```
for i in `ls *.gz`; do tar zxf $i; done
```

Now you should have to directories: openssl-0.9.8e and openssh-4.6p1

Move into the openssl directory:

```
cd openssl-0.9.8e
```

Configure openssl:

```
./config --prefix=/opt/openssl-0.9.8e
```

You can replace *prefix* with something else to install elsewhere or just remove the option to install the default. For this application, I like to install it in /opt to keep it seperate.

Compile openssl:

```
make
```

Make sure openssl compiled properly:

```
make tests
```

If everything compiled and tested okay, install openssl

```
sudo make install
```

Now you should have the directory /opt/openssl-0.9.8e with a bunch of folders and files in it. Sweet.

Lets move on and get openssh going.

The install will not overwrite existing files (like sshd_config or your host key files) if it finds them, so if you want to keep your existing configuration, leave the /etc/ssh directory alone. If you want new everything, backup the original ssh directory.

```
sudo mv /etc/ssh /etc/ssh.bak
```

Move into the openssh directory:

```
cd ../openssh-4.6p1
```

Configure openssh

```
./configure --prefix=/usr --sysconfdir=/etc/ssh --with-pam --with-ssl-dir=/opt/openssl-0.9.8e
```

Replace the --with-ssl-dir option with whatever you configured openssl with as the prefix (again to keep things simple, I just used /opt)

Compile openssh

```
make
```

And install openssh

```
sudo make install
```

Now you have the latest openssh installed with the latest openssl. Check if the install worked and restart the ssh server and check the running version.

```
sshd -v
```

Which should return some info, including *OpenSSH_4.6p1, OpenSSL 0.9.8e 23 Feb 2007*

Restart the server:

```
sudo /etc/init.d/ssh restart
```

And test it:

```
telnet localhost 22
```

Which should return some info, including *SSH-1.99-OpenSSH_4.6*

Now you have the latest and greatest openssh installed. Happy secure remote console access!

Please post comments and questions.

(this howto is also on my blog: [darkhelmetlive]("http://www.darkhelmetlive.com/blog/"))

---

### Post by twochannel on 2007-04-26
What would it take for this to become a package and added to whatever repository it belongs in?

OpenSSH (4.3p2) that comes with Feisty and Edgy does not have a recent patch that was made to 4.4p1 and later. 

From Changelog

<snip>
   - [email]dtucker@cvs.openbsd.org[/email] 2006/03/13 08:33:00
     [packet.c]
     Set TCP_NODELAY for all connections not just "interactive" ones.  Fixes
     poor performance and protocol stalls under some network conditions (mindrot
     bugs #556 and #981). Patch originally from markus@, ok djm@
<snip>

While there are those that think this is not a good idea (I'm one of them re: enabling TCP_NODELAY), its in the code and many that use SSH (sftp/scp) for file transfers may see a significant increase in throughput.

Thanks,

---

### Post by helmet on 2007-04-26
I don't know. I'm not the Ubuntu package maintainer for openssh or openssl. You'd have to take it up with them. What I might be able to do is just build a .deb and make available. I'll look into that.

---

### Post by bleedingpowers on 2007-05-09
If in the repositories, in which one should openssh-server be found? I'm having a hard time trying to find out why ssh is not found with my package manager. Which repository am I missing for feisty, so I can get ssh right from the ubuntu packages? It's weird that in other computers this is not a problem. Please, guide me around....I'll follow your directions for the latest version of openssh and openssl anyway.

Thanks

---

### Post by imagine on 2007-05-09
The package is called "openssh-server"and resides  in the repository "main". However the package in Debian (and therefore also in Ubuntu) is kind of outdated, because the package maintainer says he's "avoiding newer upstream releases until etch is out". Now since Etch is released I hope a new OpenSSH package lands in Debian Unstable soon, hopefully before the 21.06., otherwise we end up with this old version in Gutsy too...

[http://packages.ubuntu.com/feisty/net/openssh-server](http://packages.ubuntu.com/feisty/net/openssh-server)

---

### Post by bleedingpowers on 2007-05-10
Thanks for the previous reply to my question! but even when the the main repository was there, openSSH-server didn't show. In other computers this shows in my package manager, or at least it asks me to insert the Feisty installation disk.

After a few days of trying different things, the simplest thing solved my problem. I just went to synaptics or any other repositories manager, **uncheck** all the repositories, and click to refresh (update) the list. Now that my corrupted repositories were gone, I opened synaptics again and checked Ubuntu's main repository and all the others. After a quick refresh again, I was able to see openssh-server in my list.

---

### Post by Darkriser on 2007-05-18
```
./configure --prefix=/usr --sysconfdir=/etc/ssh --with-pam --with-ssl-dir=/opt/openssl-0.9.8e
```

This gives me following error:
configure: error: *** zlib missing - please install first or check config.log ***

I have a default Feisty installation.
Which package to install? (zlib1g is installed by default, but I couldn't find "zlib" package).

Thanks for help,
Marcel

---

### Post by bleedingpowers on 2007-05-25
I got the same problem, and that's why I decided to install the open-ssh version that comes with Feisty by default. Haven't figure it out yet.

---

### Post by Darkriser on 2007-05-26
> **bleedingpowers said:**
> I got the same problem, and that's why I decided to install the open-ssh version that comes with Feisty by default. Haven't figure it out yet.

this works:
```
sudo apt-get install zlib1g-dev
```

Marcel

---

### Post by lat2005 on 2008-08-16
I have tried this and get the following error when compiling openssh:

In file included from ssh.c:21:
ssh.h:464: warning: conflicting types for built-in function ‘log’
gcc -g -O2 -Wall -I/opt/openssl-0.9.8h//include -DETCDIR=\"/etc/ssh\" -DSSH_PROGRAM=\"/usr/bin/ssh\" -DSSH_ASKPASS_DEFAULT=\"/usr/libexec/ssh/ssh-askpass\" -DHAVE_CONFIG_H   -c -o sshconnect.o sshconnect.c
In file included from sshconnect.c:19:
ssh.h:464: warning: conflicting types for built-in function ‘log’
gcc -g -O2 -Wall -I/opt/openssl-0.9.8h//include -DETCDIR=\"/etc/ssh\" -DSSH_PROGRAM=\"/usr/bin/ssh\" -DSSH_ASKPASS_DEFAULT=\"/usr/libexec/ssh/ssh-askpass\" -DHAVE_CONFIG_H   -c -o sshconnect1.o sshconnect1.c
In file included from sshconnect1.c:21:
ssh.h:464: warning: conflicting types for built-in function ‘log’
sshconnect1.c: In function ‘respond_to_rsa_challenge’:
sshconnect1.c:149: error: ‘MD5_CTX’ undeclared (first use in this function)
sshconnect1.c:149: error: (Each undeclared identifier is reported only once
sshconnect1.c:149: error: for each function it appears in.)
sshconnect1.c:149: error: expected ‘;’ before ‘md’
sshconnect1.c:164: warning: implicit declaration of function ‘MD5_Init’
sshconnect1.c:164: error: ‘md’ undeclared (first use in this function)
sshconnect1.c:165: warning: implicit declaration of function ‘MD5_Update’
sshconnect1.c:167: warning: implicit declaration of function ‘MD5_Final’
make: *** [sshconnect1.o] Error 1

Any help on this?

Thank you

---


---
title: "Distcc, Giving gentoo a helping hand..."
date: 2005-10-28
forum: Outdated Tutorials &amp; Tips
---

### Post by zigford on 2005-10-28
I use Gentoo as my server and Ubuntu as my desktop.
To get distcc working between the two was really quite simple.

I assume you have knowledge of how portage works and how ubuntu works.

**[SIZE="4"]Section 1 - Setting up Distcc on gentoo.[/SIZE]**

**a) Install distcc and distcc-config**

```
emerge distcc
emerge distcc-config
```

*If distcc-config is masked then 

```
echo "sys-devel/distcc-config ~x86" >> /etc/portage/package.keywords

```
**b) Configure distcc**

```
vi /etc/conf.d/distccd

DISTCCD_OPTS="${DISTCCD_OPTS} --allow 192.168.0.0/24"
```

Modify the above line to suite your subnet.  I assume your doing this on a lan.

```
distcc-config --set-hosts "192.168.0.77 192.168.0.36 192.168.0.10"
```

Modify the above line to include the distcc helper ip addresses.

**c) Configure gentoo**

```
vi /etc/make.conf

FEATURES="distcc"
```

**d) Start distcc**

```
/etc/init.d/distccd start
```

**e) Finally, check which version of gcc your gentoo is running.**

```
gcc -v
```

**[SIZE="4"]Section 2 - Configure the helpers[/SIZE]**

**a) Install distcc**

```
sudo apt-get install distcc
```

**b) Configure distcc**

```
vi /etc/defaults/distcc

STARTDISTCC="false"
ALLOWEDNETS="192.168.0.0/24"


```

Change the STARTDISTCC="false"
to
STARTDISTCC="true"

Change the allowednets network id to correspond with your local lan.
[B]
c) Check which version of gcc you are running[/B]

gcc -v

If you have the same version of gcc as your gentoo install, then you can simply run:
```
/etc/init.d/distcc start
```

If you do not, then follow on with the next step
[B]
d) Install required gcc and g++[/B]

Example, to install gcc 3.3
```
sudo apt-get install gcc-3.3 g++-3.3

```
**e) Create a distcc binary directory with links**
From here on in, the version will be refered to $version, please substitute this with your version number of gcc

```
mkdir -p /usr/lib/distcc/$version   <-------Make this ther version
cd /usr/lib/distcc/$version
ln -s /usr/bin/gcc-$version gcc
ln -s /usr/bin/g++-$version g++
ln -s /usr/bin/cc cc
ln -s /usr/bin/c++ c++
```

**d) Set and export your new distcc path**

```
PATH="/usr/lib/distcc/$version:$PATH"
export PATH
```

**e) Crank up distcc**
```

/etc/init.d/distcc start
```

And emerge merily away

---

### Post by gkumar on 2010-06-08
Excellent tutorial! I have a gentoo netbook (Because I can, hehehe) and an Ubuntu server, and this little howto was very helpful in letting KDE compile in less than 3 days. >_>

---

### Post by lilorox on 2010-08-11
Hi, I'm digging up this thread because I'm trying to do the exact same thing.

I followed the instruction and I'm stuck so far on a tiny problem.

When I emerge something, the gentoo client reports this on the stderr :
distcc[2611] (dcc_mkdir) ERROR: mkdir '//.distcc' failed: Permission denied

I searched the logs and found out that this error is not coming from the gentoo machine (the PID doesn't match) but from the Ubuntu distcc server.

I know for a fact that this error comes from the DISTCC_DIR variable that is not set. I also know I don't need it to be set because the default is ~/.distcc.

This is fine until I get to the /etc/passwd file to check what home the distccd user has (that's the user running distccd on ubuntu), and there surprise: it's "/" !

No wonder I get this error message on the gentoo client...

How do I fix this? Do I force a DISTCC_DIR enironnement variable for everyone? Or do set a correct home path for the distccd user?

I'd like to use distccmon too so I guess the environnement variable would be the best solution.

And finally, how come I have such a hard time finding people with the same problem? I did not tweak much beyond the guide above.

Thank you for your answers.

---

### Post by Harpette on 2010-09-28
That's interesting, the install of Distcc creates different *users* on Gentoo and on Ubuntu :

harpette@ubuntu:~$ grep distcc /etc/passwd
distccd:x:105:65534::/:/bin/false

harpette@gentoo:~$ grep distcc /etc/passwd
distcc:x:240:2:added by portage for distcc:/dev/null:/sbin/nologin

Edit : how can i keep a smiley to appear where i wrote a colon followed by a lowercase x ?

Oh, BTW, the Portage elog message of distcc install says :

To use the distccmon program with Gentoo you should use this command:
# DISTCC_DIR="" distccmon-text 5
Or:
# DISTCC_DIR="" distccmon-gnome

...but perhaps you've found out by now.

---

### Post by cipherboy_loc on 2011-01-27
I know this is an old thread, but how do I set up Gentoo to distcc to a different port (other than the default)? I cannot run DISTCC on the default port for some reason (On a heavily modified Ubuntu install that fits in 2GB (Mounting an external hard drive for the DISTCC)), so I have to use port 10000.


Cipherboy

---


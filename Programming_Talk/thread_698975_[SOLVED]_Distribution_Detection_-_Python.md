---
title: "[SOLVED] Distribution Detection - Python"
date: 2008-02-16
forum: Programming Talk
---

### Post by 1337455 10534 on 2008-02-16
I am writing an all-purpose module and part of it is a nice little function that detects the user's distribution. EDIT: Solved
```

def distrofind(discreet):
	DISTROS = {
		"Ubuntu" : "/etc/lsb-release",
		"Debian" : "/etc/debian_version",
		"RedHat" : "/etc/redhat-release",
		"SUSE" : "/etc/SUSE-release",
		"Fedora" : "/etc/fedora-release",
		"Gentoo" : "/etc/gentoo-release",
		"Slackware" : "/etc/slackware-version",
		"Mandriva" : "/etc/mandriva-release",
		"Mandrake" : "/etc/mandrake-release",
		"YellowDog" : "/etc/yellowdog-release",
		"SUN JDS" : "/etc/sun-release",
		"UnitedLinux" : "/etc/UnitedLinux-release"
	}
	for name,location in DISTROS.iteritems():
		try:
			distroFile = open("%s" % location,"r")
			content = distroFile.readlines(); distroFile.close();
			if discreet == 0:
				IDfile = open("%s/DistroID" % cwd,"a")
				IDfile.writelines(content); IDfile.close();
				print "The contents of the identification file has been created at"
				print "%s/DistroID for easy reference. You may use Python to " % cwd
				print "parse it and obtain advanced information about the user's OS."
			else: pass
			return name
		except IOError:
			issueFile = open("/etc/issue","r")
			issue = issueFile.readline(); issueFile.close()
			qname = issue.split(); issue = qname[0];
			return issue

```

---

### Post by LaRoza on 2008-02-16
[http://docs.python.org/lib/module-platform.html](http://docs.python.org/lib/module-platform.html)

plaform.dist()

Returns a tuple: (distname,version,id)

---

### Post by ghostdog74 on 2008-02-16
> **1337455 10534 said:**
> 
1. Any way I can make the code shorter?

```

#!/usr/bin/env python
from sys import argv, exit
from os import getcwd, system
cwd = getcwd()

distros = {
    "Ubuntu" : "/etc/lsb-release",
    "Debian" : "/etc/debian_version",
    "RedHat" : "/etc/redhat-release"
}
def findf(ct):
    IDfile = open("%s/DistroID" % cwd,"a")
    IDfile.writelines(ct).close();
    print """The contents of the identification file has been created at
    %s/DistroID for easy reference. You may use Python to 
    parse it and obtain advanced information about the user's OS.""" % cwd
    
def distrofind():    
    for dis,where in distros.iteritems():        
        try:
            ct = open(where).read()
            findf(ct)
            return dis
        except IOError:
            pass    

```

---

### Post by AusIV4 on 2008-02-16
What about /etc/issue?

I know it's supported by Ubuntu, SuSe, and Redhat. I assume it extends to others as well.

---

### Post by 1337455 10534 on 2008-02-16
I am on Windows now, so I will look into /etc/issue tomorrow, thank-you.

> 
14.12.5 Unix Platforms

dist( 	distname='', version='', id='', supported_dists=('SuSE','debian','redhat','mandrake'))

I'm sure it's good, but it only suports 4 distros, not really enough for my needs.
> 
distros = {
    "Ubuntu" : "/etc/lsb-release",
    "Debian" : "/etc/debian_version",
    "RedHat" : "/etc/redhat-release"
}

Thank-you as well, thats a lot less junk to manage.

---

### Post by ghostdog74 on 2008-02-16
> **1337455 10534 said:**
> 
I'm sure it's good, but it only suports 4 distros, not really enough for my needs.

Thank-you as well, thats a lot less junk to manage.
well you don't expect me to find that out for you how many distros there are right? you have to do your own stuff...  :)

---

### Post by t3hi3x on 2008-02-17
lol, this isn't going to help you any, but I just wanted to know I found your username funny. And if I interpreted the second word correctly, it contradicts itself.

1337455 10534

---

### Post by 1337455 10534 on 2008-02-17
/etc/issue looks promising, now that ive seen the actual file, but ill have to poke around more to see if its universally employed.

-- yeah, I didnt come up with my username and i only recently realized that it was really dumb.

---

### Post by Fbot1 on 2008-02-17
Is this just for the fun of it? Otherwise, It seems like a shabby approach to a problem.

---

### Post by 1337455 10534 on 2008-02-17
I'm trying to get some experience writing random things that may be useful.
The approach may be shabby (OK, it is), but do you have a better suggestion for me?
I can't think of an other way to get the distribution name...

---

### Post by Fbot1 on 2008-02-17
> **1337455 10534 said:**
> I'm trying to get some experience writing random things that may be useful.
The approach may be shabby (OK, it is), but do you have a better suggestion for me?
I can't think of an other way to get the distribution name...

No, I meant using the distro name for portability. Often you should just check the programs installed or in the worst case prompt the user. But since you're just practicing, nvm.

---

### Post by 1337455 10534 on 2008-02-17
Sorry for missing your point.
It might be messier to check installed programs, becasue you then would have to deal with package managers; e.g
```

import os
os.system("nohup sudo aptitude install geany")
cwd = os.getcwd()
file = open("%s/nohup.out" % cwd,"r")
content = file.readlines()
# then search content for whatever aptitude's "already installed package line" is
# if search is positive, then you know that your computer is debain in nature.
# then youd have to guess whether it is Ubuntu, Mint, Debian, PCLinuxOS, Xubuntu or whatever
# worse, you may have to search different packages to test for each type of debian distribution, and parse through all of their file gunk :(
# and thats only apt, moving on to rpm, yum, urpmi, zypper, pacman, portage, swaret, smart, netpkg, and all of those :( :(

```
all to make a guess.

---

### Post by 1337455 10534 on 2008-02-17
yeah, the /etc/issue file is what your computer apparently displays at boot.
Meaning to say, if unhampered, it normally displays the distro name.
Some people like to change it to their name, or to something else, but at least its something that exists in all distros...

---

### Post by Fbot1 on 2008-02-17
> **1337455 10534 said:**
> Sorry for missing your point.
It might be messier to check installed programs, becasue you then would have to deal with package managers; e.g
```

import os
os.system("nohup sudo aptitude install geany")
cwd = os.getcwd()
file = open("%s/nohup.out" % cwd,"r")
content = file.readlines()
# then search content for whatever aptitude's "already installed package line" is
# if search is positive, then you know that your computer is debain in nature.
# then youd have to guess whether it is Ubuntu, Mint, Debian, PCLinuxOS, Xubuntu or whatever
# worse, you may have to search different packages to test for each type of debian distribution, and parse through all of their file gunk :(
# and thats only apt, moving on to rpm, yum, urpmi, zypper, pacman, portage, swaret, smart, netpkg, and all of those :( :(

```
all to make a guess.

I was thinking more along the lines of looking in /bin, usr/bin, etc.

---


---
title: "how to properly install programs like Java Runtime Environment?"
date: 2016-01-23
forum: New to Ubuntu
---

### Post by Jacob_Siehl on 2016-01-23
I was able to install JRE 8u71 today after one hour of searching. then I messed up trying to update to 15.10 from 14.04, so I am reinstalling ubuntu 15.10.

can someone post something like a command list for terminal or something? 

Thanks in advance

---

### Post by Petro Dawg on 2016-01-23
I believe a slightly older version of java, "OpenJDK Java 7 Runtime" and "Icedtea Java Plugin", is already available in the software center.  Were those versions not working for you?

---

### Post by Jacob_Siehl on 2016-01-24
well, I want the latest version of java. even though Linux viruses are rare, security flaws can still be used.

---

### Post by ian-weisser on 2016-01-24
Perhaps you misunderstand how Ubuntu gets it's packages, and how security patches work in Debian/Ubuntu.

When  vuln is announced and patched, you have two choices: You can patch your  own software (and recompile), or you can simply download the latest  version that includes the patch.
Since recompiling yourself is tedious, most individual users choose the latter.
Since  Debian and Ubuntu compile everything from source anyway, the distro  chooses the former. That's a standard piece of a Linux distro's support  for a package.

This leads to version confusion among users:
Foo  3.5 with the patch might be released upstream as Foo 3.6, but the  Debian version with the patch will be Foo 3.5~1, and the Ubuntu version  Foo 3.5~0ubuntu1.
The upstream website shouts "Update to Foo 3.6!",  and some users get confused because their fully-patched Ubuntu version  says "Foo 3.5." They think they are not protected...but they are.
Next time Debian syncs the full source, compiles it, and tests it, *that* package becomes 3.6 for Debian and Ubuntu. Syncing the full source is a regular (non-security) update.

There's another piece of the puzzle - the release schedule:
Security updates occur in already-released editions of Ubuntu. New version updates generally don't.
To get regular, non-security, updated versions of most packages, you must upgrade to the current release of Ubuntu.
For example, most applications in 14.04 are currently about three years old...but each is fully patched for all published vulnerabilities.
Similarly, most applications in 15.10 are about one year old...and fully patched.
Applications in 16.04 will be, on average, about six months newer that their 15.10 versions. Depends upon the upstream releases.

Ubuntu is not a latest-version, bleeding-edge distro. Look to Debian Sid for that.
Ubuntu  is a ease-of-use and safe-and-secure distro, based on Debian Testing.  Ubuntu will always be a version or two behind frequent-release,  fast-moving software *because it's designed to be so*.
As you  have discovered, you can install anything you wish on your Ubuntu system  - it's a garden, but it's not walled. Step outside the garden, and  you're outside - your system lives or dies by your wits.

If you  are interested in Java security, the Ubuntu Security Team always  welcomes volunteers to ensure our versions of Java are fully patched,  regardless of the original version number.

---

### Post by monkeybrain20122 on 2016-01-24
> **Petro Dawg said:**
> I believe a slightly older version of java, "OpenJDK Java 7 Runtime" and "Icedtea Java Plugin", is already available in the software center.  Were those versions not working for you?

There are applications that don't work with java7 any more. I think it is eof upstream.

@OP

openjdk8 is already in vivid and wily's repo and security patches will be updated when necessary. I don't think you miss anything for not having the latest minor versions.

There are also many ppas that backport java 8 to Trusty.[https://launchpad.net/ubuntu/+ppas?name_filter=openjdk-8](https://launchpad.net/ubuntu/+ppas?name_filter=openjdk-8)

A few applications may require Oracle's java (e.g netbeans) and you can get it from [https://launchpad.net/~webupd8team/+archive/ubuntu/java](https://launchpad.net/~webupd8team/+archive/ubuntu/java)

---


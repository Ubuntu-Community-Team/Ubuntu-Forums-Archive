---
title: "What if software center doesn't support a software ?"
date: 2014-02-28
forum: New to Ubuntu
---

### Post by Ardeshir on 2014-02-28
HI everyone !
Today I downloaded CodeBlocks and all of it's dependencies using Synaptic . (almost 161 MB , I think there were some external libraries too)
After the download and installation was complete  , I launched it  and saw the version is 12.11 . (Its the old version , the newest is 13.12)
I checked the software center and it was marked as installed and no upgrade was present and there was this sentence :
        "Canonical does not provide updates for Code::Blocks IDE. Some updates may be provided by the Ubuntu community."
Does it mean I should download the software from the official site or there is a software manager by Ubuntu community which does it for me ?
Thanks !

---

### Post by tgalati4 on 2014-02-28
Open a terminal and post the output of:

```
apt-cache policy codeblocks
```

Try using the installed version first.  Then compare the features between 12.11 and 13.12.  If there is a must-have feature or bug-fix in 13.12, then go through the pain to install it.  You probably have to install a PPA (personal package archive) and install it directly from the developer site.  But try using the current version first.  The focus is to develop code, not break your system.

---

### Post by ian-weisser on 2014-02-28
Ubuntu's snapshots are sometimes not the latest release *right now*, they are the versions that *were* the latest release when that version of Ubuntu was being assembled and tested.

```
$ rmadison -u ubuntu codeblocks
 codeblocks | 8.02-0ubuntu4         | lucid/universe           | source, amd64, armel, i386, ia64, powerpc, sparc
 codeblocks | 10.05-0ubuntu1~lucid1 | lucid-backports/universe | source, amd64, armel, i386, ia64, powerpc, sparc
 codeblocks | 10.05-2               | precise/universe         | source, amd64, armel, armhf, i386, powerpc
 codeblocks | 10.05-2.1             | quantal/universe         | source, amd64, armel, armhf, i386, powerpc
 codeblocks | 12.11-3               | saucy/universe           | source, amd64, armhf, i386, powerpc
 codeblocks | 13.12-3               | trusty/universe          | source, amd64, arm64, armhf, i386, powerpc, ppc64el
```

SOFTWARE CENTER:
It means that in Ubuntu 13.10's Software Center, codeblocks is v. 12.11.
You can get a newer supported version in two months when you upgrade to Ubuntu 14.04 (codeblocks v. 13.12)

MANUAL INSTALL:
Or you can install any version of codeblocks that you like by installing it manually (instead of Software Center).
If you install manually, do remove the Software Center version first.

BACKPORT:
If a community member cares enough about software, they can backport newer versions of the software to older releases of Ubuntu. See [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports) . Backports can show up in Software Center. Backports are supported by the backporter, not by the community or this forum.
Example: You can see that codeblocks 10.05 was backported to Lucid (Ubuntu 10.04)

---

### Post by Ardeshir on 2014-02-28
Thanks @tgalati4
I think I need to downlaod from developer's site .
BTW this is the erro I face when I run CodeBlocks :
[http://ubuntuone.com/6kWDyUsLWjfo5AEwva2Ow8](http://ubuntuone.com/6kWDyUsLWjfo5AEwva2Ow8)
[IMG]http://ubuntuone.com/6kWDyUsLWjfo5AEwva2Ow8[/IMG]
(I'm not sure If I'm sharing this correct)
I'm new to Linux (2 days moving to open source) and I'm not sure if yet I can take that pain .
Thanks !@

---

### Post by tgalati4 on 2014-02-28
There are some bugs that have been filed against this version.  I assume they have been fixed in the newer version.

[https://bugs.launchpad.net/ubuntu/+source/codeblocks/+bug/1173987](https://bugs.launchpad.net/ubuntu/+source/codeblocks/+bug/1173987)

At the bottom of the bug report, a fixed was performed in January and should hit 14.04.  So play with it in the meantime and push the backport effort to get it upgraded.

---

### Post by monkeybrain20122 on 2014-02-28
[https://launchpad.net/~pasgui/+archive/ppa/](https://launchpad.net/~pasgui/+archive/ppa/)

The bug is fixed if you install from the ppa.

Edited: I think it is ridiculous that bug fixes don't get backported and instead expect people to wait for the next OS release (and upgrade at the first moment so get hit by more bugs), meanwhile leaving them broken software. Thanks to ppas ordinary users can get up to date features and bug fixes without having to compile from source or upgrading their whole OS.

---

### Post by ian-weisser on 2014-02-28
It's ridiculous for *every* user to individually backport.
That's why there is a backporters team and a backports repo.

If the PPA owner would merely file the bug and show that their PPA works, then their hard work can be shared by everybody.

---

### Post by monkeybrain20122 on 2014-02-28
One can check easily how many packages are backported. Most users are not not interested in Ubuntu politics and bureaucracies (to be fair often they get packages from Debian upstream so things could get blogged down there) I have read many launchpad bug reports where the Ubuntu package maintainers **know** that 1) there is a bug 2) that the bug is fixed upstream 3) fix is released to Ubuntu next but won't be backported. So can't blame the users or ppa maintainers (often software devs) for not filing bugs and sharing fixes.

---


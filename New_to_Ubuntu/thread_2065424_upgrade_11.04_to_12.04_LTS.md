---
title: "upgrade 11.04 to 12.04 LTS"
date: 2012-10-01
forum: New to Ubuntu
---

### Post by jcka005 on 2012-10-01
hello everyone.
can somebody help me upgrade this pc here with 11.04 to 12.04 LTS??
thankyou.very much.

---

### Post by critin on 2012-10-01
What kind of help do you need?  There are lots of tutorials on line.

Does your upgrade manager tell you there is an upgrade?  Be sure all the updates for 11.04 are installed, then  click upgrade to 12.04.

---

### Post by jcka005 on 2012-10-01
thanks for the reply.
all updates are already installed..
can i upgrade it using terminal?
thanks.

---

### Post by Bashing-om on 2012-10-01
Upgrade from terminal is no big problem.
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```witch brings you up to version 11.10
repeat and brings you to 12.04
[INDENT]just try'n to help <== BDQ

[/INDENT]

---

### Post by jerrrys on 2012-10-02
dist-upgrade ?

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

[http://www.howtoforge.com/how-to-upgrade-ubuntu-11.04-natty-narwhal-to-11.10-oneiric-ocelot-desktop-and-server](http://www.howtoforge.com/how-to-upgrade-ubuntu-11.04-natty-narwhal-to-11.10-oneiric-ocelot-desktop-and-server)

[http://www.google.com/search?q=upgrade+ubuntu+11.04+to+11.10&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=upgrade+ubuntu+11.04+to+11.10&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

---

### Post by jcka005 on 2012-10-02
how about putting this in terminal
update-manager -d


will it be the same with
sudo apt-get update sudo apt-get upgrade sudo apt-get dist-upgradethat you gave me?

thanks a lot!

---

### Post by 3rdalbum on 2012-10-02
If you're going from Ubuntu 11.04 to 12.04, that's a two-version jump.

A lot of people, especially new users, seem to have problems upgrading to the next version (e.g. 11.04 to 11.10) much less jumping over a version entirely. Your new 12.04 system might work well, or it might work badly, or it might not work at all.

My recommendation to you is this:

1. Remove all software that you don't absolutely need; for instance, if you installed some games a while back that you don't play anymore, remove them. Don't remove anything that came preinstalled with the system.

2. Download the Ubuntu 12.04 CD image and burn it to CD or make a USB startup disk with it

3. Boot Ubuntu from the CD/USB and run the Ubuntu installer. When it asks you how you want to install, click the "Upgrade" option. This will do a clean install of the new Ubuntu, but it will keep your existing home folder with your important data, it will update the programs you have installed, and all your program settings will kept.

Before upgrading your operating system, be sure to back up your data. It's a very good idea to back up every six months anyway.

---

### Post by oldos2er on 2012-10-02
> **Bashing-om said:**
> Upgrade from terminal is no big problem.
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```witch brings you up to version 11.10
repeat and brings you to 12.04


'apt-get dist-upgrade' by itself doesn't upgrade to a newer version, it upgrades your current version while removing packages if necessary. This is covered in the man pages: 
"dist-upgrade in addition to performing the function of upgrade, also intelligently handles changing dependencies with new versions of packages...."

Of course if you change your sources.list from natty to oneiric (11.04 to 11.10) and *then* run apt-get dist-upgrade, your version will be upgraded to the next. But I think 'update-manager -d' is the supported way to upgrade versions.

---

### Post by jerrrys on 2012-10-02
"Of course if you change your sources.list from natty to oneiric (11.04 to 11.10) and *then* run apt-get dist-upgrade, your version will be upgraded to the next."

Is that as safe as you make it sound.. :)

Think that would make me nervous.

---

### Post by oldos2er on 2012-10-02
I've never personally tried it, but I've seen it recommended as a way to upgrade versions. As I said, I think the best way is to use 'upgrade-manager -d'.

---

### Post by jcka005 on 2012-10-04
we tried  'upgrade-manager -d'..we haven't get the result..hope it will work well..

---

### Post by jerrrys on 2012-10-04
Its a long process

---

### Post by jcka005 on 2012-10-04
yeah it's a long process..til now it's not yet finished...almost 3hours..whew...

---


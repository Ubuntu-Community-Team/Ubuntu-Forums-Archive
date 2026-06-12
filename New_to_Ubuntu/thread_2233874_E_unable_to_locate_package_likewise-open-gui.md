---
title: "E: unable to locate package likewise-open-gui"
date: 2014-07-11
forum: New to Ubuntu
---

### Post by Rajesh raf on 2014-07-11
Hi to all am Rajesh Recently am install ubuntu 14.04 LTS in my oracle VM virtual box when i try to install likewise package am getting error  am using "sudo apt-get install likewise-open-gui" command but am getting message like "[COLOR=#ff0000]E:unable to locate package likewise-open-gui"[/COLOR] how to solve this issue even  unable to install likewise in GUI mode also getting error messages like [COLOR=#ff0000]"dependency is not satisfiable: likewise-open"[/COLOR] i need likewise for windows Domain integration but unable to install likewise in my virtual box how clear this issue help me and Thanks :confused::confused::confused: :confused::confused::confused:

---

### Post by ian-weisser on 2014-07-11
```
$ rmadison -u ubuntu likewise-open-gui
 likewise-open-gui | 4.1.2982-0ubuntu3      | lucid/universe           | ia64, powerpc, sparc
 likewise-open-gui | 5.4.0.42111-2ubuntu1   | lucid/universe           | amd64, armel, i386
 likewise-open-gui | 5.4.0.42111-2ubuntu1.3 | lucid-security/universe  | amd64, armel, i386
 likewise-open-gui | 5.4.0.42111-2ubuntu1.3 | lucid-updates/universe   | amd64, armel, i386
 likewise-open-gui | 6.1.0.406-0ubuntu5     | precise/universe         | amd64, armel, armhf, i386, powerpc
 likewise-open-gui | 6.1.0.406-0ubuntu5.1   | precise-updates/universe | amd64, armel, armhf, i386, powerpc
 likewise-open-gui | 6.1.0.406-0ubuntu10    | saucy/universe           | amd64, armhf, i386, powerpc
```

The package likewise-open-gui has been removed from the 14.04 Ubuntu repositories.

A quick search of Launchpad shows [the removal request]("https://launchpad.net/ubuntu/trusty/+source/likewise-open/6.1.0.406-0ubuntu10").

Here's [the bug report]("https://bugs.launchpad.net/ubuntu/+source/likewise-open/+bug/1295031"), including some discussion of alternatives. Likewise was unmaintained, apparently abandoned by it's developer. Ubuntu does not include unmaintained software, since it doesn't get bug or security fixes.

Finally, here's the AskUbuntu question (and answers) about [likewise alternatives in Ubuntu]("http://askubuntu.com/questions/452904/likewise-open-14-04-other-easy-way-to-connect-ad/453111#453111").

---

### Post by Rajesh raf on 2014-07-12
Hi ian-weisser thank for your reply i tried "rmadison -u ubuntu likewise-open-gui" command after  [COLOR=#000000] "sudo apt-get install likewise-open-gui" command again [/COLOR] also i getting same error message [COLOR=#000000] "[/COLOR][COLOR=#ff0000]E:unable to locate package likewise-open-gui" help me [/COLOR][COLOR=#000000]what can i do i attached that error message screenshot thanks [/COLOR]:confused::confused::confused:

---

### Post by ubudog on 2014-07-12
From the [bug report]("https://bugs.launchpad.net/ubuntu/+source/likewise-open/+bug/1295031"):
> likewise-open is largely unmaintained, has been renamed upstream and is superceded by other solutions in trusty.

Please remove it from the archive.


From the [wiki page]("https://help.ubuntu.com/community/LikewiseOpen"):
> LikewiseOpen is now Beyond Trust - PowerBroker Identity Services Open Edition The Likewise website is gone, and links to it are broken.
...
Get the new branded version at [http://www.beyondtrust.com/Technical-Support/Downloads/PowerBroker-Identity-Services-Open-Edition/?Pass=True](http://www.beyondtrust.com/Technical-Support/Downloads/PowerBroker-Identity-Services-Open-Edition/?Pass=True)


---

### Post by Rajesh raf on 2014-07-16
Hi [COLOR=#000000]ubudog....thank you for Reply [/COLOR] i tried powerbroker following this steps website  [COLOR=#ff0000]"http://community.spiceworks.com/how_to/show/80336-join-ubuntu-14-04lts-to-a-windows-domain-using-pbis-open"[/COLOR] but finally i got [COLOR=#ff0000]"command not found"[/COLOR] error really i don't know why ubuntu add windows domain integration is this much tough....really its possible to add Ubuntu in windows domain???? because likewise is not working and powerbroker also not working for me please anyone tell me how to add Ubuntu in windows domain in easyway. i hope anyone solve my problem thank you all....:shock::shock::confused:

---

### Post by Vladlenin5000 on 2014-07-16
What command wasn't found? In what step?

Anyway, this has nothing to do with your original issue. That has been thoroughly explained to you. Whatever error you find now with the new software should be better dealt with in a new, separated thread.

---


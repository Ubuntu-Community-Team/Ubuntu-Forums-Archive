---
title: "can't upgrade from 13.04 to 13.10"
date: 2014-04-30
forum: New to Ubuntu
---

### Post by Dergham on 2014-04-30
hi .. 
i can't upgrade my ubuntu to 13.10 ....
error msg : E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages
--
problem image :

[IMG]http://s8.postimg.org/6a8k37578/555.jpg[/IMG]

---

### Post by Bucky Ball on 2014-04-30
How are you trying to upgrade? Did you run these three commands first?

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

### Post by Bashing-om on 2014-04-30
Dergham; Hi ! Welcome to the forum.

As release 13.04 is End-Of-Life, I bet by now the repository has been turned down and redirected.

Maybe this procedure:
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)
Will enable you to move forward.

[INDENT][INDENT]just my thought
[/INDENT][/INDENT]

---

### Post by Dergham on 2014-04-30
thanks for answer Bucky ...

upgrade like usual way .. from softwere updater ...
&
Yes ... Trying this commands bt nothing happens .. the same problem

---

### Post by Dergham on 2014-04-30
Bashing - om ... than you for answer ...
---
Bt the url you send talking about very old ubuntu .. from 2009 !
it maybe not working with mine ...

---

### Post by Bashing-om on 2014-04-30
Dergham; Hello;

Yes the info is dated, but still works. Be sure to follow through to page 2 to know how to change the source.list file.

Once at 13.10, you may as well keep going as 13.10 is soon to be EOL too, and upgrade to release 14.04, then no sweat 'till 2019 .
EDIT: HowTO for trusty:
[https://help.ubuntu.com/community/TrustyUpgrades](https://help.ubuntu.com/community/TrustyUpgrades)


[INDENT]a nudge in the right direction
[/INDENT]

---

### Post by Dergham on 2014-04-30
ok Bashing - om .... I W'll try this ...

thank you very much ..

---

### Post by Warren Hill on 2014-04-30
Another place to look is [this question on AskUbuntu]("http://askubuntu.com/q/91815/107450")

Or you could backup install fresh then restore your personal files from the backup.

---

### Post by monkeybrain20122 on 2014-04-30
Forget it. Just do a fresh install. With all the troubles you go through you are likely to break your system after "upgrade" especially that 13.04 is not even supported any more. A clean install takes 25 minutes (15 for 14.04) and "upgrade" takes hours and very likely to fail if your system has been modified (ppa, proprietary drivers, third party applications, tweaked system config etc)

---


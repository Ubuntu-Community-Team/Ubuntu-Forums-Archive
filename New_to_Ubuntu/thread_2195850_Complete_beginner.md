---
title: "Complete beginner"
date: 2013-12-26
forum: New to Ubuntu
---

### Post by jt358 on 2013-12-26
Hi all,

Really need some help.

I need to download some software that requires Linux and is not usable with windows.

I've downloaded the WUBI UBUNTU from the page [http://download.cnet.com/1770-20_4-0.html?query=wubi&platformSelect=&tag=srch&searchtype=downloads&filterName=platform%3DWindows%2CMac%2CiOS%2CAndroid%2CWebware%2CMobile&filter=platform%3DWindows%2CMac%2CiOS%2CAndroid%2CWebware%2CMobile](http://download.cnet.com/1770-20_4-0.html?query=wubi&platformSelect=&tag=srch&searchtype=downloads&filterName=platform%3DWindows%2CMac%2CiOS%2CAndroid%2CWebware%2CMobile&filter=platform%3DWindows%2CMac%2CiOS%2CAndroid%2CWebware%2CMobile).

Only problem is, once I open ubuntu I can't actually login as it keeps saying that my password is incorrect, despite me knowing full well it is incorrect. It lets in as a guest, but then I can't download software from the internet because it keeps asking me for a superuser root password for authentication. Can Anyone offer any advice.

Many thanks

Jamie

---

### Post by newb85 on 2013-12-26
I'm not a Wubi user (most on these forums aren't), but from what I've read, this problem sometimes occurs if you try installing the original 12.04 instead of [s]12.04.2[/s] *12.04.3* (which is the latest point release of Precise).  The website you linked put that Wubi installer up early enough it has to be 12.04.

First, I would recommend that you do a real-partition install of Ubuntu rather than a Wubi install.  (I'm assuming you're not planning on using Ubuntu only temporarily.)

Barring that, I recommend that you download the Wubi installer from the official Ubuntu website.  [http://www.ubuntu.com/download/desktop/windows-installer](http://www.ubuntu.com/download/desktop/windows-installer)

*Edit: the latest point release is actually 12.04.3. *

---

### Post by Frogs Hair on 2013-12-26
There is a password setup during a Wubi installation that requires password is entered twice as I remember.

---

### Post by hakuna_matata on 2013-12-27
I think that is your problem, too: 

[https://bugs.launchpad.net/wubi/+bug/1005120](https://bugs.launchpad.net/wubi/+bug/1005120)

Take a look at bcbc's comment:

[URL="https://bugs.launchpad.net/wubi/+bug/1005120/comments/3"]https://bugs.launchpad.net/wubi/+bug/1005120/comments/3
[/URL]
There is a difference between name at logon screen and user name in Ubuntu. It is not possible to login as admin (root) in Ubuntu, because by default, the Root account password is locked in Ubuntu!!

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

> because it keeps asking me for a superuser root password for authentication.
Superuser root password is password of your Ubuntu user!!

---

### Post by newb85 on 2013-12-27
Wait... are you trying log in as root, or as the user you created on installation?  As hakuna points out, logging in as root is not possible

---


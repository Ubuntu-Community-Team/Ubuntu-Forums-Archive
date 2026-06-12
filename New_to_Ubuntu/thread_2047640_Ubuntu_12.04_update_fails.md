---
title: "Ubuntu 12.04 update fails"
date: 2012-08-25
forum: New to Ubuntu
---

### Post by canda12 on 2012-08-25
Hi,

I am not using a proxy server to access the internet - however when I try to run the update manager I get the following errors:

W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/precise/partner/source/Sources](http://archive.canonical.com/ubuntu/dists/precise/partner/source/Sources)  407  Proxy Authentication Required
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/precise/main/source/Sources)  407  Proxy Authentication Required
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/precise/partner/binary-i386/Packages](http://archive.canonical.com/ubuntu/dists/precise/partner/binary-i386/Packages)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/source/Sources)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/source/Sources)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise-updates/universe/source/Sources)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/source/Sources)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-i386/Packages)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise-backports/main/source/Sources)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/source/Sources)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise-backports/universe/source/Sources)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/source/Sources)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-i386/Packages)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-i386/Packages)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-i386/Packages)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-i386/Packages)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise-security/main/source/Sources)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise-security/restricted/source/Sources)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise-security/universe/source/Sources)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/source/Sources)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-security/main/binary-i386/Packages)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-i386/Packages)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-security/universe/binary-i386/Packages)  407  Proxy Authentication Required
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-i386/Packages)  407  Proxy Authentication Required
, E:Some index files failed to download. They have been ignored, or old ones used instead.

I can surf the internet as normal, I also am unable to download from the Ubuntu Software Center

Any advice on how to resolve this would be really appreciated

Many thanks

Chris

---

### Post by s1baker on 2012-08-25
Seems people in the last few days are having problems when they update.
I was updating my system yesterday when I received an error message, then the system crashed. I rebooted and used the terminal.

```
sudo apt-get update
sudo dpkg --configure -a
sudo apt-get upgrade
```

---

### Post by jerrrys on 2012-08-25
Have not encountered this problem, but check this out:

[http://ubuntuforums.org/showthread.php?t=1409000](http://ubuntuforums.org/showthread.php?t=1409000)

[http://www.linuxquestions.org/questions/linux-newbie-8/ubuntu-8-04-407-proxy-authorization-error-640793/](http://www.linuxquestions.org/questions/linux-newbie-8/ubuntu-8-04-407-proxy-authorization-error-640793/)

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=407+proxy&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=407+proxy&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by canda12 on 2012-08-28
> **jerrrys said:**
> Have not encountered this problem, but check this out:

[http://ubuntuforums.org/showthread.php?t=1409000](http://ubuntuforums.org/showthread.php?t=1409000)

[http://www.linuxquestions.org/questions/linux-newbie-8/ubuntu-8-04-407-proxy-authorization-error-640793/](http://www.linuxquestions.org/questions/linux-newbie-8/ubuntu-8-04-407-proxy-authorization-error-640793/)

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=407+proxy&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=407+proxy&as_qdr=all&sa=Google+Search&lang=en)

sorry guys none of the above worked

Chris

---


---
title: "[SOLVED] MC displaying weird characters"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by GoofYas007 on 2008-10-23
Hi,

been struggling with mc (midnight commander) and displaying weird characters.
See thread [http://ubuntuforums.org/showthread.php?t=465676](http://ubuntuforums.org/showthread.php?t=465676).
Problem here is that after applying the solution mentioned, mc is fixed but perl is a bit wacko.
->
<me>:~# sudo dpkg-reconfigure locales
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_US"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Generating locales...
  en_AU.UTF-8... up-to-date
  en_BW.UTF-8... up-to-date
  en_CA.UTF-8... up-to-date
  en_DK.UTF-8... up-to-date
  en_GB.UTF-8... up-to-date
  en_HK.UTF-8... up-to-date
  en_IE.UTF-8... up-to-date
  en_IN.UTF-8... up-to-date
  en_NZ.UTF-8... up-to-date
  en_PH.UTF-8... up-to-date
  en_SG.UTF-8... up-to-date
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... up-to-date
  en_ZW.UTF-8... up-to-date
Generation complete.

If anyone can point me in the right direction it would be great.

---

### Post by GoofYas007 on 2008-10-23
fixed it....

thanx to [http://ubuntuforums.org/showpost.php?p=2326951&postcount=6](http://ubuntuforums.org/showpost.php?p=2326951&postcount=6)

only addition is:->in my installation of Hardy there was no file /etc/locale.def, therefore:->

```
sudo pico /etc/locale.def
en_US ISO-8859-1
en_US.ISO-8859-15 ISO-8859-15
en_US.UTF-8 UTF-8
```
Exit with CTRL+X and save. rest is the same as the thread->
[http://ubuntuforums.org/showpost.php?p=2326951&postcount=6](http://ubuntuforums.org/showpost.php?p=2326951&postcount=6)

---


---
title: "file does not exist"
date: 2015-06-01
forum: New to Ubuntu
---

### Post by Thoger on 2015-06-01
I'm new with ubuntu and crouton and I installed trusty and kde the strange is that when I open files containing Swedish letters like å-ö-ä I get this message,  The file or folder /home/thoger/Desktop/OPF S&#56319;&#56933;gmyra AB 8 20141231 ver 1.pdf does not exist. If I change name on the it can be opened.

---

### Post by DuckHook on 2015-06-02
You probably don't have the Swedish language pack installed, or if you do, locale is not set to Swedish. Therefore, Linux cannot understand the accented characters and so does not recognise them as meaningful. Please open a terminal and post back results of:```
locale -a | grep -i sv
```If result is empty (nothing), as I suspect it will be, then do:```
sudo apt-get install language-pack-sv
```Then reboot and check that it is installed by running first command again. You should now see some output along the lines of```
sv_SE.utf8
```This should be enough to get your system to recognize the accented characters. If you want your whole system to be in Swedish, then do```
sudo dpkg-reconfigure locales
```and choose Swedish.

---

### Post by Thoger on 2015-06-02
I got below result bu running  sudo dpkg-reconfigure localesperl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LC_PAPER = "en_SE.UTF-8",
        LC_ADDRESS = "en_SE.UTF-8",
        LC_MONETARY = "en_SE.UTF-8",
        LC_NUMERIC = "en_SE.UTF-8",
        LC_TELEPHONE = "en_SE.UTF-8",
        LC_IDENTIFICATION = "en_SE.UTF-8",
        LC_MEASUREMENT = "en_SE.UTF-8",
        LC_TIME = "en_SE.UTF-8",
        LC_NAME = "en_SE.UTF-8",
        LANG = "en_SE.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Generating locales...
  en_US.UTF-8... up-to-date
  sv_FI.UTF-8... up-to-date
  sv_SE.UTF-8... up-to-date
Generation complete.

---

### Post by DuckHook on 2015-06-02
> **Thoger said:**
> I got below result bu running  sudo dpkg-reconfigure localesperlWhy did you run *localesperl*? Run just locales:```
sudo dpkg-reconfigure locales
```

---


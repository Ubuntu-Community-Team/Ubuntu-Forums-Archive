---
title: "Package Operation failed using Software Centre and Update Manager"
date: 2012-09-20
forum: New to Ubuntu
---

### Post by mathewpadinjath on 2012-09-20
Hi,

I recently deleted Bluetooth config manager and having some tough time to install the same using Ubuntu Software Centre. Every time I try to install Bluetooth software I keep getting an error message 'Package Operation failed' 'The installation/removal of a s/w package is falied.  Following message has been captured from details:

Quote
installArchives() failed: perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
dpkg: error: parsing file '/var/lib/dpkg/available' near line 0: 
 newline in field name `../../../help-langpack/software-center/ca/software-center.xml' 
Error in function:  
Unquote

Similarly I also have problem with the update manager :(  everytime I keep searching for the latest s/w through update manager I keep getting following message:

quote
installArchives() failed: perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
Preconfiguring packages ... 
perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
Preconfiguring packages ... 
perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
Preconfiguring packages ... 
perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
Preconfiguring packages ... 
dpkg: error: parsing file '/var/lib/dpkg/available' near line 0: 
 newline in field name `../../../help-langpack/software-center/ca/software-center.xml' 
unquote


Please help me identifying the issue and also let me know as to how to come out of the same 

Thanks in advance 

Cheers !!!

Mathew

---

### Post by pissedoffdude on 2012-09-20
Is your default language US English?  If it is, try:

```
sudo cp /etc/default/locale /etc/default/locale.bak
sudo rm /etc/default/locale
sudo touch /etc/default/locale
sudo echo LANG="en_US.UTF-8" > /etc/default/locale
sudo echo LANGUAGE="en_US:en" >> /etc/default/locale
sudo locale-gen
```

Otherwise, replace en_US with whatever your default language is and reboot and let us know if this works.

---

### Post by mathewpadinjath on 2012-09-25
Thanks Mate .... here's the outcome of the commands ....

mathew@mathew-laptop:~$ sudo cp /etc/default/locale /etc/default/locale.bak
[sudo] password for mathew: 
mathew@mathew-laptop:~$ sudo cp /etc/default/locale /etc/default/locale.bak
mathew@mathew-laptop:~$ sudo rm /etc/default/locale
mathew@mathew-laptop:~$ sudo touch /etc/defualt/locale
touch: cannot touch `/etc/defualt/locale': No such file or directory
mathew@mathew-laptop:~$ sudo touch /etc/default/locale
mathew@mathew-laptop:~$ sudo echo LANG="en_US.UTF-8" > /etc/default/locale
bash: /etc/default/locale: Permission denied
mathew@mathew-laptop:~$ sudo echo LANG="en_US.UTF-8" > /etc/default/locale
bash: /etc/default/locale: Permission denied
mathew@mathew-laptop:~$ sudo echo LANGUAGE="en_US:en" >> /etc/default/locale
bash: /etc/default/locale: Permission denied
mathew@mathew-laptop:~$ sudo echo LANGUAGE="en_US:en" >> /etc/default/locale
bash: /etc/default/locale: Permission denied
mathew@mathew-laptop:~$ sudo locale-gen
Generating locales...
  en_AG.UTF-8... up-to-date
  en_AU.UTF-8... up-to-date
  en_BW.UTF-8... up-to-date
  en_CA.UTF-8... up-to-date
  en_DK.UTF-8... up-to-date
  en_GB.UTF-8... up-to-date
  en_HK.UTF-8... up-to-date
  en_IE.UTF-8... up-to-date
  en_IN.UTF-8... up-to-date
  en_NG.UTF-8... up-to-date
  en_NZ.UTF-8... up-to-date
  en_PH.UTF-8... up-to-date
  en_SG.UTF-8... up-to-date
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... up-to-date
  en_ZM.UTF-8... up-to-date
  en_ZW.UTF-8... up-to-date
Generation complete.
mathew@mathew-laptop:~$ ^C
mathew@mathew-laptop:~$ 

How do I manually change the Language ??

Mathew

---


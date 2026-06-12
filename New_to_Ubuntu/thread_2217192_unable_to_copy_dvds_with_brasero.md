---
title: "unable to copy dvds with brasero"
date: 2014-04-16
forum: New to Ubuntu
---

### Post by mushroom08 on 2014-04-16
im getting an error that i need libdvdcss2 and when i try to install it in terminal it says

mushoomstamp@Mushroom-Empire:~$ sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libdvdcss2' has no installation candidate
mushoomstamp@Mushroom-Empire:~$ sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libdvdcss2' has no installation candidate

---

### Post by westie457 on 2014-04-16
[COLOR=#000000]libdvdcss2 is bundled in 'linux-restricted-extras'

```
sudo apt-get install linux-restricted-extras
``` should fix things.[/COLOR]

---

### Post by mushroom08 on 2014-04-16
mushoomstamp@Mushroom-Empire:~$ sudo apt-get install linux-restricted-extras
[sudo] password for mushoomstamp: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-restricted-extras

---

### Post by monkeybrain20122 on 2014-04-16
It is 'ubuntu-restricted-extras', libdvdcss2 is not in ubuntu-restricted-extras, but it has libdvdread4,
To install libdvdcss2 you need one extra step after installing restricted-extras, in the terminal run
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by grumblebum2 on 2014-04-16
Too slow ...SEE ABOVE
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Installing_libdvdcss](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Installing_libdvdcss)

---

### Post by mushroom08 on 2014-04-16
thank you [**[COLOR=#000000]monkeybrain20122[/COLOR]**]("http://ubuntuforums.org/member.php?u=1843403") that solved it

---


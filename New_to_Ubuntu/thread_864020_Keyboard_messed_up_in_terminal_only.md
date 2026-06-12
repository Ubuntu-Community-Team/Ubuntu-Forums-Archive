---
title: "Keyboard messed up in terminal only"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by mattkoehn on 2008-07-19
Hi. After a new install on a fake raid my keyboard is messed up only while in terminal. Tab is space, arrow keys display ^[[A and stuff like that. My default character encoding is set to ANSI_X3.4-1968 in terminal. Setting it to UTF-8 or western doesn't change anything. Going to preferences-keyboard my layout is generic 105-key (intl) PC. This is Hardy with all repos and updated. Thanks

---

### Post by pauper on 2008-07-20
```
sudo dpkg-reconfigure console-setup
```

---

### Post by mattkoehn on 2008-07-20
No dice. I still have crazy characters.

---

### Post by pauper on 2008-07-21
```
sudo dpkg-reconfigure locales
locale
```

What's your current locale environment?

---

### Post by mattkoehn on 2008-07-21
Here is my output and thank you for helping.

> 
LANG=C
LC_CTYPE="C"
LC_NUMERIC="C"
LC_TIME="C"
LC_COLLATE="C"
LC_MONETARY="C"
LC_MESSAGES="C"
LC_PAPER="C"
LC_NAME="C"
LC_ADDRESS="C"
LC_TELEPHONE="C"
LC_MEASUREMENT="C"
LC_IDENTIFICATION="C"
LC_ALL=


---

### Post by pauper on 2008-07-21
Find out what is right for you, instead of "C"--"en_US.UTF-8", maybe?

List of all available locale is here:

```
less /usr/share/i18n/SUPPORTED
```

You can swap them until you find what you need (en_US.UTF-8, en_GB.UTF-8,
en_US ISO-8859-1, etc.):

```
export LANG="en_US.UTF-8"
```

Make it permanent:

```
sed -e 's/LANG="*.*"/LANG="en_US.UTF-8"/' /etc/environment > ~/Desktop/environment
sudo mv ~/Desktop/environment /etc/environment
sudo update-locale LANG=en_US.UTF-8
```

Reboot.

---

### Post by mattkoehn on 2008-07-26
So I was trying to mess around with that, while it did change the output of the locales command it didn't change anything in the terminal output. So what I tried was installing onto a fakeraid using the livecd but leaving the boot manager alone. The boot manager is what hangs and spits out errors during the install if you try to just install dmraid and install from the live cd. So doing it this way I was able to install a new, working, ubuntu install without having to roll my own OS like all of the dmraid guides had me doing. Finishing the post just for historical sake and any search engine hits on this.

---


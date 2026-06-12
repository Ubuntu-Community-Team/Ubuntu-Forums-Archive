---
title: "Clean up?"
date: 2012-12-25
forum: New to Ubuntu
---

### Post by Yezinki on 2012-12-25
1. What is the command to run in the terminal to clean up installed packages & junk?

2. If Bleachbit is installed what should not be checked?

Thanks.

---

### Post by Pjotr123 on 2012-12-25
Do not use Bleachbit, Computer Janitor and the like, but do it like this:
[https://sites.google.com/site/easylinuxtipsproject/clean](https://sites.google.com/site/easylinuxtipsproject/clean)

Ubuntu needs much less cleaning than Windows.... :)

---

### Post by Yezinki on 2012-12-25
How do you rate these commands to clean up unused packages, thumbnails, junk/clutter?

```

sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get clean
```

Thanks.

---

### Post by snowpine on 2012-12-25
> **Yezinki said:**
> How do you rate these commands to clean up unused packages, thumbnails, junk/clutter?

```

sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get clean
```

Thanks.

None of these commands are necessary for normal operation of your Ubuntu system.

May I ask, are you running low on hard drive space or something that leads you to ask this question?

```
df -h
```

---

### Post by Yezinki on 2012-12-25
```
vaio@VGC-LS1:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        30G  2.8G   26G  10% /
udev            995M  4.0K  995M   1% /dev
tmpfs           401M  872K  400M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none           1002M  6.7M  996M   1% /run/shm
/dev/sda2       259G  271M  246G   1% /home
/dev/sr1        4.4G  4.4G     0 100% /media/My Movies
vaio@VGC-LS1:~$ 

```

Thanks for your reply.

No I am not running low on disk space. It's a 320 GiB HDD running only Ubuntu 12.04 LTS.

---

### Post by snowpine on 2012-12-25
Looks normal to me, I do not think any further action on your part is necessary to conserve disk space. I see many users on these forums break their system trying to remove stuff they think is unnecessary. :)

---

### Post by Yezinki on 2012-12-25
Thanks again snowpine for your expert advice. :)

---

### Post by oldos2er on 2012-12-26
> **Yezinki said:**
> How do you rate these commands to clean up unused packages, thumbnails, junk/clutter?

```

sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get clean
```

Thanks.

```
man apt-get
``` will give you information on the function of the above commands; it's up to you whether you choose to run them or not.

---

### Post by Yezinki on 2012-12-26
Thanks but what does this mean?

```
APT-GET(8)                            APT                           APT-GET(8)

NAME
       apt-get - APT package handling utility -- command-line interface

SYNOPSIS
       apt-get [-sqdyfmubV] [-o= config_string ] [-c= config_file ]
               [-t= target_release] [-a= default_architecture] {update |
               upgrade | dselect-upgrade | dist-upgrade |
               install pkg [ { =pkg_version_number | /target_release } ] ...
               | remove pkg...  | purge pkg...  |
               source pkg [ { =pkg_version_number | /target_release } ] ...  |
               build-dep pkg...  | check | clean | autoclean | autoremove |
               {-v | --version} | {-h | --help}}

DESCRIPTION
       apt-get is the command-line tool for handling packages, and may be
       considered the user's "back-end" to other tools using the APT library.
       Several "front-end" interfaces exist, such as dselect(1), aptitude(8),
       synaptic(8) and wajig(1).

       Unless the -h, or --help option is given, one of the commands below
       must be present.
 Manual page apt-get(8) line 1 (press h for help or q to quit)

```

---

### Post by snowpine on 2012-12-26
If you aren't interested in learning and understanding the documentation then simply skip these completely optional and unnecessary commands. You do not need to understand this material to have a pleasant and enjoyable Ubuntu experience. :)

---

### Post by CharlesA on 2012-12-26
It's a man page, you can scroll down to see a list of what a program does.

Otherwise you can look at something like this:

[http://linux.die.net/man/8/apt-get](http://linux.die.net/man/8/apt-get)

---

### Post by oldos2er on 2012-12-26
> **Yezinki said:**
> Thanks but what does this mean?


Use Page Up and Page Down to move around in man pages. "q" (without the quote marks) exits back to your command prompt.

More info on using man pages: [http://linuxcommand.org/reading_man_pages.php](http://linuxcommand.org/reading_man_pages.php)

---


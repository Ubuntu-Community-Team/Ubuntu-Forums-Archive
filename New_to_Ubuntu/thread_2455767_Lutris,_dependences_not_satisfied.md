---
title: "Lutris, dependences not satisfied"
date: 2020-12-27
forum: New to Ubuntu
---

### Post by dunivixs on 2020-12-27
Hello !
Few days ago, I tried to install Lutris, but it failed.
A dependence is not satisfied : Depend: python3-magic

I searched on internet how to solve the problem but I do not really understand what they did
I also saw that there were packages named "python-magic" or "python3-magic++" available. But I don't think that will help me.

In fact I got the error : "E: Impossible de corriger les problèmes, des paquets défectueux sont en mode « garder en l'état »." (sorry it is in french)

Could you help me to solve this ?
Thanks

---

### Post by SeijiSensei on 2020-12-27
Did you try installing python3-magic?

```
sudo apt install python3-magic
```

---

### Post by dunivixs on 2020-12-28
Yes I did
But at first when I did the command   "sudo apt search python3-magic"
The terminal found nothing
And the command   "sudo apt install python3-magic"
responds that : 

"Aucune version du paquet python3-magic n'est disponible, mais il existe dans la base
de données. Cela signifie en général que le paquet est manquant, qu'il est devenu obsolète
ou qu'il n'est disponible que sur une autre source

E: Le paquet « python3-magic » n'a pas de version susceptible d'être installée"

---

### Post by Impavidus on 2020-12-28
You can switch output to english by prefixing the commands with LANG=C:```
LANG=C sudo apt update
```That disables translations for most commands.

You haven't told us the version of Ubuntu you're running. And when you give the output of some commands, it's easiest for us if you just post all of it. We know where to find the interesting bits. And what's the source of your lutris? I can only find it in the official repos of the current development version of Ubuntu, not in any of the released versions.

---

### Post by SeijiSensei on 2020-12-28
I just installed Lutris on 20.04 ("Focal Fossa") using the instructions here: [https://linuxconfig.org/install-lutris-on-ubuntu-20-04-focal-fossa-linux](https://linuxconfig.org/install-lutris-on-ubuntu-20-04-focal-fossa-linux)

python3-magic was installed automatically as a dependency.

---

### Post by dunivixs on 2020-12-29
I want to install Lutris on 20.04.1 LTS

Wine is also installed on my computer by the command "sudo apt install wine"

I tried to install Lutris from thi sppa :
ppa:lutris-team/lutris

[FONT=arial]And when I launch the command : "sudo apt install lutris"
I get this : 

"Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 lutris : Depends: python3-magic but it is not installable
          Recommends: python3-evdev but it is not going to be installed
          Recommends: libwine-development but it is not going to be installed
E: Unable to correct problems, you have held broken packages."
[/FONT]

---

### Post by Impavidus on 2020-12-29
python3-magic is in the repositories for 20.04. What does it say when you try to install it?```
sudo apt install python3-magic
```

---

### Post by ActionParsnip on 2020-12-29
Have you contacted the PPA maintainer to report the issue?

I found this 
[https://linuxconfig.org/install-lutris-on-ubuntu-20-04-focal-fossa-linux](https://linuxconfig.org/install-lutris-on-ubuntu-20-04-focal-fossa-linux)
Does it help?

---

### Post by dunivixs on 2020-12-29
> **Impavidus said:**
> python3-magic is in the repositories for 20.04. What does it say when you try to install it?```
sudo apt install python3-magic
```


The result is : 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package python3-magic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
```

---

### Post by dunivixs on 2020-12-29
> **ActionParsnip said:**
> Have you contacted the PPA maintainer to report the issue?

I found this 
[https://linuxconfig.org/install-lutris-on-ubuntu-20-04-focal-fossa-linux](https://linuxconfig.org/install-lutris-on-ubuntu-20-04-focal-fossa-linux)
Does it help?

I launched all the commands that the site gave to me, at the end, the command :
```
sudo apt install --install-recommends winehq-stable
```

responds : 
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package winehq-stable

```

But there is also a problem, the command "sudo apt update" responds a lot of errors:

```
Hit:1 http://fr.archive.ubuntu.com/ubuntu focal InRelease
Hit:2 http://fr.archive.ubuntu.com/ubuntu focal-updates InRelease              
Hit:3 http://ppa.launchpad.net/gezakovacs/ppa/ubuntu focal InRelease           
Hit:4 http://fr.archive.ubuntu.com/ubuntu focal-backports InRelease            
Hit:5 http://download.opensuse.org/repositories/hardware:/razer/xUbuntu_20.04  InRelease
Hit:6 http://fr.archive.ubuntu.com/ubuntu focal-security InRelease             
Hit:7 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu focal InRelease     
Hit:8 https://repo.steampowered.com/steam stable InRelease                     
Get:10 http://download.opensuse.org/repositories/home:/strycore/Debian_10 ./ InRelease [1497 B]
Get:11 https://dl.winehq.org/wine-builds/ubuntu focal InRelease [6257 B]       
Hit:12 http://ppa.launchpad.net/lutris-team/lutris/ubuntu focal InRelease      
Get:13 https://linux.teamviewer.com/deb stable InRelease [11.0 kB]
Hit:14 http://ppa.launchpad.net/mkusb/ppa/ubuntu focal InRelease
Hit:15 http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu focal InRelease
Hit:16 http://ppa.launchpad.net/obsproject/obs-studio/ubuntu focal InRelease
Ign:9 https://dl.bintray.com/etcher/debian stable InRelease           
Hit:18 http://ppa.launchpad.net/ondrej/php/ubuntu focal InRelease
Get:17 https://dl.bintray.com/etcher/debian stable Release [3674 B]
Hit:19 http://ppa.launchpad.net/openrazer/stable/ubuntu focal InRelease
Hit:20 http://ppa.launchpad.net/webupd8team/haguichi/ubuntu focal InRelease
Err:10 http://download.opensuse.org/repositories/home:/strycore/Debian_10 ./ InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2F7F0DA5FD5B64B9
Err:11 https://dl.winehq.org/wine-builds/ubuntu focal InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 76F1A20FF987672F
Err:13 https://linux.teamviewer.com/deb stable InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C5E224500C1289C0
Reading package lists... Done
W: GPG error: http://download.opensuse.org/repositories/home:/strycore/Debian_10 ./ InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2F7F0DA5FD5B64B9
E: The repository 'http://download.opensuse.org/repositories/home:/strycore/Debian_10 ./ InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: https://dl.winehq.org/wine-builds/ubuntu focal InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 76F1A20FF987672F
E: The repository 'https://dl.winehq.org/wine-builds/ubuntu focal InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: https://linux.teamviewer.com/deb stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C5E224500C1289C0
E: The repository 'https://linux.teamviewer.com/deb stable InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.


```

---

### Post by ActionParsnip on 2020-12-29
```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2F7F0DA5FD5B64B9
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 76F1A20FF987672F
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys C5E224500C1289C0

```

You haven't added the keys to say they are "OK". It's just a warning but cleaning up takes seconds.

---

### Post by mastablasta on 2020-12-29
add PPA then:

sudo apt update
sudo apt upgrade
sudo apt install lutris

---

### Post by Impavidus on 2020-12-30
> **dunivixs said:**
> The result is : 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package python3-magic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
```
That shouldn't happen. python3-magic is available from the main focal repository. On my system:```
$ apt-cache policy python3-magic
python3-magic:
  Installed: (none)
  Candidate: 2:0.4.15-3
  Version table:
     2:0.4.15-3 500
        500 http://nl.archive.ubuntu.com/ubuntu focal/main amd64 Packages
        500 http://nl.archive.ubuntu.com/ubuntu focal/main i386 Packages

```
Check your /etc/apt/sources.list. It must mention focal main. Maybe refreshing software lists helps. sudo apt update should do that, but it can fail if some timestamps are wrong. First deleting the lists will force apt update to download them again. The lists are in /var/lib/apt/lists/.
Your output from sudo apt update shows the main focal repository on the first line as "Hit". This means that no changes were reported compared to the version cached on your system, so it didn't redownload.

The only other possibility I see is a server problem. In that case, switch to a different mirror.

---

### Post by dunivixs on 2021-02-17
I have solved the problem :
I just went to this site : [https://ubuntuplace.info/questions/389/comment-resoudre-les-dependances-non-satisfaites-apres-avoir](https://ubuntuplace.info/questions/389/comment-resoudre-les-dependances-non-satisfaites-apres-avoir)

I ticked this : "Conical-supported free and open-source software (main)

I did this commands : ```
sudo apt-get clean
sudo apt-get autoclean
sudo apt -f install
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get -u dist-upgrade
```

Then I unticked some ppa unused

And I tried to install lutris and this works !!

Thanks for everyone

---

### Post by ActionParsnip on 2021-02-17
Looks like you didn't import the key as per the guide linked earlier ([https://linuxconfig.org/install-lutris-on-ubuntu-20-04-focal-fossa-linux](https://linuxconfig.org/install-lutris-on-ubuntu-20-04-focal-fossa-linux))

```

wget -nc https://dl.winehq.org/wine-builds/winehq.key
sudo apt-key add winehq.key

```

---


---
title: "can not upgrade.."
date: 2005-02-09
forum: Repositories &amp; Backports
---

### Post by emamarro on 2005-02-09
Hi,I get this warning trying to install upgrades..what should I do? thanksss

E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Impossibile bloccare la cartella di download

------------------------------------------------------------------
Here my sources.list:
------------------------------------------------------------------

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Alpha i386 Binary-1 (20050204)]/ unstable main restricted


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

---

### Post by lao_V on 2005-02-09
[emamarro]("member.php?u=406"), how are you trying to install the upgrage? if through a terminal, do you have the synaptic window open at the same time?

---

### Post by emamarro on 2005-02-09
i was doing by synaptic , but also when i tried by terminal i get a list of many "can't open etc.." is something wrong with my repository?

---

### Post by emamarro on 2005-02-09
i did install many apps,it's just upgrades not working..

---

### Post by lao_V on 2005-02-09
>  ## Uncomment the following two lines to fetch major bug fix updates produced
 ## after the final release of the distribution.
 deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") hoary-updates main restricted
 deb-src [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") hoary-updates main restricted
 
 you may have to comment the above two lines as it says its only available after the final realease?

---

### Post by frijolito on 2005-02-09
Hrm... maybe a permissions problem? Are you running it as root?

Try running the following line in a command terminal (gnome-terminal, for example), and show us the output:

```
sudo apt-get upgrade
```

---

### Post by emamarro on 2005-02-09
thanks,i did by terminal ok,the simpliest thing is often the best..
do you know is repository list  needs to be added with others UrL or the one standard is just ok for manteinance of system?
ciao

---

### Post by frijolito on 2005-02-09
[QUOTE=emamarro]thanks,i did by terminal ok,the simpliest thing is often the best..
do you know is repository list  needs to be added with others UrL or the one standard is just ok for manteinance of system?
ciao[/QUOTE]
 Like you said, the original sources.list file will definitely be enough for adequate maintenance and security. Now, if you want bleeding-edge stuff, or packages that can't be found in the default repositories, you could try adding more sources if you're feeling a little feisty.

Check out this ubuntuguide post for more info: [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---


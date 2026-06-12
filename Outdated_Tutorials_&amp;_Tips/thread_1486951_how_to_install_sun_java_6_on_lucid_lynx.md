---
title: "how to install sun java 6 on lucid lynx"
date: 2010-05-18
forum: Outdated Tutorials &amp; Tips
---

### Post by terry_gardener on 2010-05-18
In the newly released Ubuntu 10.04 LTS, the sun-java6-jre packages have been removed from the Multiverse section of the Ubuntu archive. So you cannot install it using the command sudo apt-get install sun-java6-jre directly!!!

To install sun-java6-jre on Ubuntu 10.04 LTS, type the commands below in Terminal:

```
sudo add-apt-repository "deb http://archive.canonical.com/ lucid partner"
```

```
sudo apt-get update
```

```
sudo apt-get install sun-java6-jre
```

this can i be used for the JDK java packages just replace the jre with JDK

this tutorial was from 
[http://linuxidiotnote.blogspot.com/2010/05/install-sun-java6-jdksun-java6-jre-on.html]("http://linuxidiotnote.blogspot.com/2010/05/install-sun-java6-jdksun-java6-jre-on.html")

---

### Post by Andrew Golightly on 2010-05-26
anyone know why the Sun version of Java was removed?

Thanks for the instructions on how to install it :)

---

### Post by ontwowheels on 2010-06-09
> **Andrew Golightly said:**
> anyone know why the Sun version of Java was removed?

Thanks for the instructions on how to install it :)

Maybe it is no longer open source because Oracle has purchased it.

Thanks for the install instructions.

---

### Post by scouser73 on 2010-06-10
Sun Java is back in the Ubuntu repositories, it's the latest version.

---

### Post by nu2this on 2010-06-11
Thanks for this!):P

---

### Post by mmilliss on 2010-08-26
I'm doing unattended installs using a combination of preseeding and kickstart and would like to know if any one has any idea how to automate the license agreement that you have to manually accept when installing the sun jdk.

Cheers
Matt

---

### Post by Linuxforall on 2010-08-26
Sun Java and Adobe Flash are in partner repo, need to enable it in synaptic or kpackagemanager.

---

### Post by satish_j on 2010-08-28
> **terry_gardener said:**
> In the newly released Ubuntu 10.04 LTS, the sun-java6-jre packages have been removed from the Multiverse section of the Ubuntu archive. So you cannot install it using the command sudo apt-get install sun-java6-jre directly!!!

To install sun-java6-jre on Ubuntu 10.04 LTS, type the commands below in Terminal:

```
sudo add-apt-repository "deb http://archive.canonical.com/ lucid partner"
```

```
sudo apt-get update
```

```
sudo apt-get install sun-java6-jre
```

this can i be used for the JDK java packages just replace the jre with JDK

this tutorial was from 
[http://linuxidiotnote.blogspot.com/2010/05/install-sun-java6-jdksun-java6-jre-on.html]("http://linuxidiotnote.blogspot.com/2010/05/install-sun-java6-jdksun-java6-jre-on.html")

Thanks for this info..:D
i use JDownloader which requires jre.Although it should work with openJDK,but i have previously used sun java and was searching the same in Lucid..

---

### Post by Linuxforall on 2010-08-28
Update to latest Sun Java via dedicated Java PPA.

sudo add-apt-repository ppa:ferramroberto/java && sudo apt-get update

sudo apt-get upgrade

---

### Post by inaho on 2010-09-04
I would like to know... if do the upgrade to ubuntu 10.04, does it install automatically sun-java6 or doest it go for the open source version?

---

### Post by insanity54 on 2010-10-23
> **inaho said:**
> I would like to know... if do the upgrade to ubuntu 10.04, does it install automatically sun-java6 or doest it go for the open source version?

@inaho: No. If you upgrade to Ubuntu 10.04, you won't have the option of installing sun-java6 unless you allow Ubuntu to get packages from the partner repository. All you will see in synaptic is openjdk.

---


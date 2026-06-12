---
title: "need all required repositories...!!!"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by maxy69 on 2008-06-26
hey ppl another newbie question 
1. plz give the address of all the basic repositories community.unofficial and for good extra softwares.

2. if ubuntu 8 hardy is available in kde.....:)

---

### Post by webofunni on 2008-06-26
Hello,

Let me answer your questions one by one. 

1. You can enable repositories using Synaptic Package manager. 

1.a Go to System >> Administration >> Synaptic Package Manager
1.b In Synaptic Go to Settings >> Repositories 
1.c In the "Ubuntu Software" tab select the repositories 
1.d In the "Third party Software" Tab you can add additional repositories. 

2. You can use Kubuntu [www.kubuntu.org](www.kubuntu.org) for KDE. Also you can install KDE in Ubuntu using : 

```
 apt-get install kde
```

Let me know if you have further queries.

---

### Post by maxy69 on 2008-06-26
> **webofunni said:**
> Hello,

Let me answer your questions one by one. 

1. You can enable repositories using Synaptic Package manager. 

1.a Go to System >> Administration >> Synaptic Package Manager
1.b In Synaptic Go to Settings >> Repositories 
1.c In the "Ubuntu Software" tab select the repositories 
1.d In the "Third party Software" Tab you can add additional repositories. 

2. You can use Kubuntu [www.kubuntu.org](www.kubuntu.org) for KDE. Also you can install KDE in Ubuntu using : 

```
 apt-get install kde
```

Let me know if you have further queries.
but ubuntu is gnome how can two enviornment run together or it will replace gnome and install kde.

also  i was  asking some new repositories ftp or http address which are not give by default.
thanx

---

### Post by Martje_001 on 2008-06-26
[http://archive.ubuntu.com/ubuntu/dists/hardy/](http://archive.ubuntu.com/ubuntu/dists/hardy/)

---

### Post by billgoldberg on 2008-06-26
Just enable the repositories in synaptic "settings -> repositories".

Also, add the medibuntu repo.

Click the "Install all codecs in ubuntu" link in my sig.

---

### Post by t0p on 2008-06-26
> **maxy69 said:**
> but ubuntu is gnome how can two enviornment run together or it will replace gnome and install kde.


If you install kde alongside gnome, you'll be offered a choice of GUI every time you log in.

---

### Post by maxy69 on 2008-06-26
and one more thing, which one [www.kubuntu.org](www.kubuntu.org) is the latest with kde4 (what is remix) is that the only one or all.

---

### Post by Martje_001 on 2008-06-26
The Remix version is KDE 4. This is called remix because the official 'LTS' realease includes KDE 3.

---

### Post by billgoldberg on 2008-06-26
Oh I forgot to mention what the medibuntu repo actually does.

If you add it, you will be able to download things like:

non-free-codecs (divx, windows codecs, ...)
adobe reader
newest skype version
amarok with mp3 support
google earth
dvd support
...

All package listed here:

[http://www.medibuntu.org/packages.php](http://www.medibuntu.org/packages.php)

---

### Post by maxy69 on 2008-06-26
ok to make it simple tell me  how to add universe repository i heard it has got all the required tools. give either graphical or terminal step wise guide.
thanx

---

### Post by webofunni on 2008-06-26
> but ubuntu is gnome how can two enviornment run together or it will replace gnome and install kde.

  You can use the session option in the login screen to switch the GUI after installing KDE. 

> also i was asking some new repositories ftp or http address which are not give by default.

  You will get most of the packages from the Ubuntu universe/multiverse/restricted repositories. Which package you are searching for ?

---

### Post by billgoldberg on 2008-06-26
> **maxy69 said:**
> ok to make it simple tell me  how to add universe repository i heard it has got all the required tools. give either graphical or terminal step wise guide.
thanx

Go to system -> administration -> synaptic package" manager.

Enter you password when prompted.

Go to "settings -> repositories".

Make sure everything is tagged in the tabs "ubuntu software" and "third party software".

(you won't need the source code repositories, so you don't need to enable them)

Also make sure to add the medibuntu repo as I said.

---

### Post by maxy69 on 2008-06-26
cool added it .......now wat......lolz.....thanx

---

### Post by maxy69 on 2008-06-26
very well guys everything is ok now only 1 thing to ask.....(
apt-get install kde ) will this command install latest kde4 or kde3.

---

### Post by Nepherte on 2008-06-26
Just install the kde4 package.

---

### Post by maxy69 on 2008-06-26
> **Nepherte said:**
> Just install the kde4 package.

jst install or it will install kde4.......there is a lot of diff in both the statements....be clear.

---

### Post by Martje_001 on 2008-06-26
> **maxy69 said:**
> very well guys everything is ok now only 1 thing to ask.....(
apt-get install kde ) will this command install latest kde4 or kde3.
If you open up Synaptic and search for kde, you'll see a package named 'kde'. Click on it and you'll see a description:
```
the K Desktop Environment official modules
KDE (the K Desktop Environment) is a powerful Open Source graphical
desktop environment for Unix workstations. It combines ease of use,
contemporary functionality, and outstanding graphical design with the
technological superiority of the Unix operating system.

This metapackage includes all the official modules released with KDE that
are not specific to development. In addition to the core KDE modules, this
includes multimedia, networking, personal information manager (PIM),
graphics, education, games, web development, system administration tools,
and other artwork and utilities.

Homepage: http://www.kde.org
```

if you click on kde4:
```
the K Desktop Environment version 4 official modules
KDE (the K Desktop Environment) is a powerful Open Source graphical
desktop environment for Unix workstations. It combines ease of use,
contemporary functionality, and outstanding graphical design with the
technological superiority of the Unix operating system.

This metapackage includes all the official modules released with KDE4 that
are not specific to development. In addition to the core KDE modules, this
includes multimedia, networking, graphics, education, games, web
development, system administration tools, and other artwork and utilities.
```
So, you'll need kde4 ;)

---

### Post by maxy69 on 2008-06-26
> **Martje_001 said:**
> If you open up Synaptic and search for kde, you'll see a package named 'kde'. Click on it and you'll see a description:
```
the K Desktop Environment official modules
KDE (the K Desktop Environment) is a powerful Open Source graphical
desktop environment for Unix workstations. It combines ease of use,
contemporary functionality, and outstanding graphical design with the
technological superiority of the Unix operating system.

This metapackage includes all the official modules released with KDE that
are not specific to development. In addition to the core KDE modules, this
includes multimedia, networking, personal information manager (PIM),
graphics, education, games, web development, system administration tools,
and other artwork and utilities.

Homepage: http://www.kde.org
```

if you click on kde4:
```
the K Desktop Environment version 4 official modules
KDE (the K Desktop Environment) is a powerful Open Source graphical
desktop environment for Unix workstations. It combines ease of use,
contemporary functionality, and outstanding graphical design with the
technological superiority of the Unix operating system.

This metapackage includes all the official modules released with KDE4 that
are not specific to development. In addition to the core KDE modules, this
includes multimedia, networking, graphics, education, games, web
development, system administration tools, and other artwork and utilities.
```
So, you'll need kde4 ;)

ya sort of.....thanx bro...!!!

---


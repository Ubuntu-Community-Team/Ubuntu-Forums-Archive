---
title: "gfortran dependency hell"
date: 2013-02-21
forum: Packaging and Compiling Programs
---

### Post by tmfs on 2013-02-21
I was trying to install an R package which said it couldn't find -lgortran. So I uninstalled gfortran. However, when I tried to install it again, I got the following error

```

gfortran : Depends: gfortran-4.7 (>= 4.7.2-1~) but it is not going to be installed

```

When I tried installing gfortran-4.7

```
gfortran-4.7 : Depends: gcc-4.7-base (= 4.7.2-2ubuntu1) but 4.7.2-11precise2 is to be installed

             Depends: gcc-4.7 (= 4.7.2-2ubuntu1) but 4.7.2-11precise2 is to be installed
```

When I try installing gcc-4.7-base or gcc-4.7, it tells me they're already installed.

What's happening here and how can I fix this?

I'm running 12.10

Thanks

---

### Post by Malsasa on 2013-02-21
It could be happen if you try to instal a package from source. This *hell of dependency* always solved on my machine by installing from repo, with using Synaptic Package Manager.

---

### Post by iMac71 on 2013-02-22
you might proceed as follows: open a Terminal window and type in sequence:```
gpg --keyserver keyserver.ubuntu.com --recv-key E084DAB9
gpg -a --export E084DAB9 | sudo apt-key add -
gksudo gedit /etc/apt/sources.list
```[SIZE=2][COLOR=#000000][FONT=Verdana][SIZE=2]
then paste in the opened file the following line (or a similar one: see the link below):[/SIZE]
[/FONT][/COLOR][/SIZE][HTML]deb http://cran.mirror.garr.it/mirrors/CRAN/bin/linux/ubuntu precise/[/HTML][SIZE=2][COLOR=#000000][FONT=Verdana]
[SIZE=2]BTW: [/SIZE][/FONT][/COLOR][/SIZE][SIZE=2][COLOR=#000000][FONT=Verdana][SIZE=2]regarding to the R mirrors, you find their complete list here:
[http://cran.r-project.org/mirrors.html](http://cran.r-project.org/mirrors.html)[/SIZE]
[SIZE=2]and fin[SIZE=2]ally type in a new Terminal window:[/SIZE][/SIZE]
[/FONT][/COLOR][/SIZE] ```
sudo  apt-get update -y && sudo apt-get upgrade -y && sudo  apt-get dist-upgrade -y && sudo apt-get dselect-upgrade -y
sudo apt-get install -y r-base
```[]("http://cran.r-project.org/mirrors.html")

---


---
title: "eeebuntu on 701 eeepc cannot install packages"
date: 2014-07-09
forum: New to Ubuntu
---

### Post by R_Huson on 2014-07-09
Cannot use sudo apt-get install any packages (in particular tangogps). Error message cannot find package. Have run sudo apt-get update  no go (and apt-get update) same thing. Tried sudo apt-get upgrade and it tries to load 73 update gets to 53 the error messsage. Have been into synapse package manager and changed it to main. Tried to reload and it does the same as upgrade shows 73 changes gets to 53 and fails. Downloaded package tar  ball onto desktop and extracted package to desktop. In package  folder ran ./configure which goes through a load of checks okay. Then at the end message pages not found gtkt-2.0, gdk-2.0, gconf-2.0, libxml2-0. Which I presume are prerequisites. There seems, (in my total ignorance) to be 2 issues installing from terminal and loading prerequisites. Have looked at various online ideas about this but no change. How can I do these things. Any help would be appreciated.

---

### Post by sudodus on 2014-07-09
Welcome to the Ubuntu Forums :-)

I think eeebuntu is old and has passed end of life (at least versions based on Ubuntu). This was the impression after visiting some web pages of eeebuntu and aurora. Which version of eeebuntu are you trying to use?

Please try a supported version (a version with updated repositories for the program packages). See this link
[URL="http://ubuntuforums.org/showthread.php?t=2229730"]
Forums Staff recommendations on EOL Ubuntu releases, in particular 10.04 desktop.[/URL]

---

### Post by R_Huson on 2014-07-09
HI dont mind starting afresh, after messing around its any ones guest what has happenedregardsroger

---

### Post by sudodus on 2014-07-09
Is the internal drive only 4 GB? In that case there will be problems to install a full size linux system, but there are several small distros and flavours, that will work with 4 GB. An alternative is to get a fast USB 3 pendrive (yes I know the port is only USB 2, but it is a question about fast flash hardware too). See this link

[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

The lightest flavour of Ubuntu is Lubuntu, but you can also build lighter flavours from the Ubuntu mini.iso or with the One Button Installer using the tarball

***Lubuntu_14.04oem-npae5.tar.xz***

according to this link

[https://help.ubuntu.com/community/OBI](https://help.ubuntu.com/community/OBI)

A simple LXDE desktop environment or Lubuntu Core are lighter than standard Lubuntu. And you can install only the packages you really need.

There are also some ultra-light distros (lighter than Lubuntu)

***DSL***, ***Wary Puppy***, ***Tiny Core***

---


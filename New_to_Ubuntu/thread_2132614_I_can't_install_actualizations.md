---
title: "I can't install actualizations"
date: 2013-04-05
forum: New to Ubuntu
---

### Post by Jonatan Formentera on 2013-04-05
I have a problem. At the top rihgt of the screen appears the traffic signal: prohibit direction and I can't install actualizacions. It saids to my to check if I'm using repositories of a third and to desactivate them. Then I have to install the packets. How can I check the repositories? I don't know how to make this comprobations
Thanks

---

### Post by grahammechanical on 2013-04-05
What version of Ubuntu are you using? I cannot give clear directions because I do not know the version of Ubuntu that you are using. You need to open Software Sources in System Settings and go to the Other Software tab and uncheck any PPAs that are there and then try to run Update Manager again.

Regards.

---

### Post by Jonatan Formentera on 2013-04-06
I'm using ubuntu 14.2. I've gone to Other Software but there is no APT. I've got information like that: 


Following packets have unfulled dependencies:

libreoffice-base-core: Depends: libreoffice-core (= 1:3.5.7-0ubuntu4) but it's not installed 1:3.5.4-0ubuntu1.1 is installed
                       Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is installed
libreoffice-calc: Depends: libreoffice-core (= 1:3.5.7-0ubuntu4) but 1:3.5.4-0ubuntu1.1 is installed
                  Depends: libreoffice-base-core (= 1:3.5.7-0ubuntu4) but 1:3.5.7-0ubuntu4 is installed
                  Depends: libgcc1 (>= 1:4.1.1) pero 1:4.6.3-1ubuntu5 está instalado
libreoffice-draw: Depends: libreoffice-core (= 1:3.5.7-0ubuntu4) pero 1:3.5.4-0ubuntu1.1 está instalado
                  Depends: libgcc1 (>= 1:4.1.1) pero 1:4.6.3-1ubuntu5 está instalado
libreoffice-gnome: Depends: libreoffice-core (= 1:3.5.7-0ubuntu4) pero 1:3.5.4-0ubuntu1.1 está instalado
                   Depends: libgcc1 (>= 1:4.1.1) pero 1:4.6.3-1ubuntu5 está instalado
libreoffice-gtk: Depends: libreoffice-core (= 1:3.5.7-0ubuntu4) pero 1:3.5.4-0ubuntu1.1 está instalado
                 Depends: libgcc1 (>= 1:4.1.1) pero 1:4.6.3-1ubuntu5 está instalado
libreoffice-impress: Depends: libreoffice-core (= 1:3.5.7-0ubuntu4) pero 1:3.5.4-0ubuntu1.1 está instalado
                     Depends: libreoffice-draw (= 1:3.5.7-0ubuntu4) pero 1:3.5.7-0ubuntu4 está instalado
                     Depends: libgcc1 (>= 1:4.1.1) pero 1:4.6.3-1ubuntu5 está instalado
libreoffice-math: Depends: libreoffice-core (= 1:3.5.7-0ubuntu4) pero 1:3.5.4-0ubuntu1.1 está instalado
                  Depends: libgcc1 (>= 1:4.1.1) pero 1:4.6.3-1ubuntu5 está instalado
libreoffice-writer: Depends: libreoffice-core (= 1:3.5.7-0ubuntu4) pero 1:3.5.4-0ubuntu1.1 está instalado
                    Depends: libreoffice-base-core (= 1:3.5.7-0ubuntu4) pero 1:3.5.7-0ubuntu4 está instalado
                    Depends: libgcc1 (>= 1:4.1.1) pero 1:4.6.3-1ubuntu5 está instalado
python-uno: Depends: libreoffice-core (= 1:3.5.7-0ubuntu4) pero 1:3.5.4-0ubuntu1.1 está instalado
            Depends: python (< 2.8) pero 2.7.3-0ubuntu2 está instalado
            Depends: libgcc1 (>= 1:4.1.1) pero 1:4.6.3-1ubuntu5 está instalado

---

### Post by Jonatan Formentera on 2013-04-06
Sorry: I mean, ubuntu 12.4

---


---
title: "please help me with atheros 5007 and ubuntu 8.10"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by spaik on 2008-11-02
hi

i have just installed the new ver. of unbuntu but iam still beginner and i need to make the wireless card work to be able to learn more as i use it and i don't have any other way to connect to the internet. please i need a step by step how to and even online help if it is possible as soon as possible ..

thank u very much !

---

### Post by melojo on 2008-11-02
look here

[http://ubuntuforums.org/showthread.php?t=964836&page=3](http://ubuntuforums.org/showthread.php?t=964836&page=3)

---

### Post by spaik on 2008-11-02
they are using the wget code how could this work when i dont have an internet ?????

---

### Post by ugm6hr on 2008-11-02
[http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default](http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default)

The file should be on your installation CD - just double-click.

If not:
[http://packages.ubuntu.com/intrepid/linux-backports-modules-2.6.27-7-generic](http://packages.ubuntu.com/intrepid/linux-backports-modules-2.6.27-7-generic)
[http://packages.ubuntu.com/intrepid/linux-backports-modules-intrepid-generic](http://packages.ubuntu.com/intrepid/linux-backports-modules-intrepid-generic)

Download them (links for i386 or AMD64 - depending on your Ubuntu version - near bottom in table) - and double-click in that order.

Hope that works for you (apparently does for that chipset).  If not - it's easy to uninstall (from Synaptic).

---

### Post by spaik on 2008-11-03
thank you very very much 

i have used this way [http://ubuntuforums.org/showthread.php?t=964836&page=3](http://ubuntuforums.org/showthread.php?t=964836&page=3)

and it did work and iam so so happy to be able to use the internet from ubuntu for the first time and i actually learning so much about the terminal and wow its great .

the only problen is that the internet is very slow very very slow, is there any solve for this problem ????

---

### Post by drs305 on 2008-11-03
For others with Atheros 5XXX, there is a section of the 8.10 Release Notes which discusses the original issue and how to resolve it:
[release/notes]("http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default")

---


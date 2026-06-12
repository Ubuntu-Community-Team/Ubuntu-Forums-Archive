---
title: "Can't get sun-java8-plugin to work in ubuntu 11.04 natty."
date: 2011-12-16
forum: New to Ubuntu
---

### Post by ooseven on 2011-12-16
Can't get sun-java6-plugin to show up on firefox:
zorin5-32-bit@homesky:~$ sudo apt-get install sun-java6-plugin
[sudo] password for zorin5-32-bit: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-plugin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
zorin5-32-bit@homesky:~$ 

But it is not showing up>
I have ubuntu 11.04 natty installed.
If it matters I have zorin 5 32 bit installed?

Thank You
ooseven

---

### Post by ooseven on 2011-12-16
> **ooseven said:**
> Can't get sun-java6-plugin to show up on firefox:
zorin5-32-bit@homesky:~$ sudo apt-get install sun-java6-plugin
[sudo] password for zorin5-32-bit: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-plugin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
zorin5-32-bit@homesky:~$ 

But it is not showing up>
I have ubuntu 11.04 natty installed.
If it matters I have zorin 5 32 bit installed?

Thank You
ooseven
That java6 I ment my bad

---

### Post by gandaran on 2011-12-16
> **ooseven said:**
> Can't get sun-java6-plugin to show up on firefox:
zorin5-32-bit@homesky:~$ sudo apt-get install sun-java6-plugin
[sudo] password for zorin5-32-bit: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-plugin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
zorin5-32-bit@homesky:~$ 

But it is not showing up>
I have ubuntu 11.04 natty installed.
If it matters I have zorin 5 32 bit installed?

Thank You
ooseven
type this code in firefox url bar
```
about:plugins
```
do you see the sun-java-plugin or icedtea web plugin?
if you have the icedtea plugin installed remove it from software center as there's no need for two java plugins installed.

---

### Post by ooseven on 2011-12-16
> **gandaran said:**
> type this code in firefox url bar
```
about:plugins
```do you see the sun-java-plugin or icedtea web plugin?
if you have the icedtea plugin installed remove it from software center as there's no need for two java plugins installed.

No Icedtea. Learned that long time ago:-) 

PLUS

I heard the official Java was removed from the Ubuntu repository.
You can install it with one of this way:
 1. Install Java 6:
-
1. Open a terminal by hitting CTRL + ALT + T
2. Insert and run this command:
sudo add-apt-repository ppa:ferramroberto/java
sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
 Read this:
[https://answers.launchpad.net/ubuntu/+source/sun-java6/+question/176843](https://answers.launchpad.net/ubuntu/+source/sun-java6/+question/176843)


And it did work ones. But it is not working now...


Thank You


ooseven[URL="https://answers.launchpad.net/ubuntu/+source/sun-java6/+question/176843"]
[/URL]

---


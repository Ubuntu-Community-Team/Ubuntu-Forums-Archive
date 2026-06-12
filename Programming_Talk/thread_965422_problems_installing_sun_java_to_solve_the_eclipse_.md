---
title: "problems installing sun java to solve the eclipse running slow problem."
date: 2008-10-31
forum: Programming Talk
---

### Post by ajlinzey on 2008-10-31
I tried installing Sun java (to seed up eclipse) using Hod139's instructions ([http://ubuntuforums.org/showthread.php?t=201378](http://ubuntuforums.org/showthread.php?t=201378))  and ran into a few problem's that I'm hoping somebody can help me with. After entering the command
sudo apt-get install eclipse sun-java6-jdk 
I got an initial estimate of 12 hours for the download so I left to run some errands, I checked after a few hours and there was a sun license agreement in the terminal window so I concluded that it had installed.
Trying the next step:
sudo update-java-alternatives -s java-6-sun 
produced
update-java-alternatives: directory does not exist: /usr/lib/jvm/java-6-sun 
so I figured that the first step didn't install correctly so I retried it and got 
 sudo apt-get install eclipse sun-java6-jdk 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
eclipse is already the newest version. 
You might want to run `apt-get -f install' to correct these: 
The following packages have unmet dependencies: 
  sun-java6-jdk: Depends: sun-java6-bin (= 6-07-3ubuntu2) but it is not going to be installed 
  sun-java6-jre: Depends: sun-java6-bin (= 6-07-3ubuntu2) but it is not going to be installed or 
                          ia32-sun-java6-bin (= 6-07-3ubuntu2) but it is not installable 
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution). 
user@user-desktop:~$ sudo update-jave-alternatives -s java-6-sun 
sudo: update-jave-alternatives: command not found 

Something seems to be messed up somewhere but I'm not sure where Any suggestions?

---

### Post by cl333r on 2008-10-31
Are you sure you _accepted_ the java license agreement?

---

### Post by drubin on 2008-10-31
> **ajlinzey said:**
> I tried installing Sun java (to seed up eclipse) using Hod139's instructions ([http://ubuntuforums.org/showthread.php?t=201378](http://ubuntuforums.org/showthread.php?t=201378))  and ran into a few problem's that I'm hoping somebody can help me with. After entering the command
sudo apt-get install eclipse sun-java6-jdk 
I got an initial estimate of 12 hours for the download so I left to run some errands, I checked after a few hours and there was a sun license agreement in the terminal window so I concluded that it had installed.
Trying the next step:
sudo update-java-alternatives -s java-6-sun 
produced
update-java-alternatives: directory does not exist: /usr/lib/jvm/java-6-sun 
so I figured that the first step didn't install correctly so I retried it and got 
 sudo apt-get install eclipse sun-java6-jdk 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
eclipse is already the newest version. 
You might want to run `apt-get -f install' to correct these: 
The following packages have unmet dependencies: 
  sun-java6-jdk: Depends: sun-java6-bin (= 6-07-3ubuntu2) but it is not going to be installed 
  sun-java6-jre: Depends: sun-java6-bin (= 6-07-3ubuntu2) but it is not going to be installed or 
                          ia32-sun-java6-bin (= 6-07-3ubuntu2) but it is not installable 
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution). 
user@user-desktop:~$ sudo update-jave-alternatives -s java-6-sun 
sudo: update-jave-alternatives: command not found 

Something seems to be messed up somewhere but I'm not sure where Any suggestions?

It is sudo update-jav**a**-alternatives -s java-6-sun
If there are any other issues take a look at my sig for installing java.

---

### Post by ajlinzey on 2008-11-02
cl333r- I didn't but I just ran updates and sun-java6 reinstalled and I did accept the agreement.
drubin thanks that seems to have worked
Thanks all

---

### Post by cl333r on 2008-11-03
> **ajlinzey said:**
> cl333r- I didn't but I just ran updates and sun-java6 reinstalled and I did accept the agreement.
drubin thanks that seems to have worked
Thanks all
Java from Sun won't install if the user doesn't accept the license.

---

### Post by pancher on 2009-01-28
How did you solve this problem? 

I encountered the same problem. :( 

How did you update and reinstall jdk6? Thanks very much.

---

### Post by drubin on 2009-01-30
> **pancher said:**
> How did you solve this problem? 

I encountered the same problem. :( 

How did you update and reinstall jdk6? Thanks very much.

Hi firstly welcome to the forums.

Did you read the whole thread... look at post [number 3]("http://ubuntuforums.org/showpost.php?p=6075877&postcount=3") and post number 4 says that solved his issue :)

Hope this helps you.

---


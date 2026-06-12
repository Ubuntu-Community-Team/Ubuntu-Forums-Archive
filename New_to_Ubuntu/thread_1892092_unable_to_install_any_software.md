---
title: "unable to install any software"
date: 2011-12-07
forum: New to Ubuntu
---

### Post by sharatsn123 on 2011-12-07
I AM UNABLE TO INSTALL ANY SOFTWARE IN UBUNTU 11.04[IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]
WHILE USING TERMINAL TO INSTALL SOFTWARES, I GET THE MESSAGE   
.
 "E: The package google-chrome-stable needs to be reinstalled, but I can't find an archive for it."
.
I AM NOT ABLE TO USE EVEN UBUNTU SOFTWARE CENTRE....
PLEASE HELP

---

### Post by josephmills on 2011-12-07
Hi there you can get chrome from 
[https://www.google.com/chrome/index.html](https://www.google.com/chrome/index.html)

after downloading open terminal and go to the dir that you downloaded it to. and run 
```
sudo dpkg -i chrom*
```

this will install chrome browser is there errors still ?

---

### Post by Paqman on 2011-12-07
> **josephmills said:**
> 
after downloading open terminal and go to the dir that you downloaded it to. and run 
```
sudo dpkg -i chrom*
```


You can also just double-click the .deb file. It will open Ubuntu Software Centre and you can hit "install".

---

### Post by BC59 on 2011-12-07
> **sharatsn123 said:**
> I AM UNABLE TO INSTALL ANY SOFTWARE IN UBUNTU 11.04[IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]
WHILE USING TERMINAL TO INSTALL SOFTWARES, I GET THE MESSAGE   
.
 "E: The package google-chrome-stable needs to be reinstalled, but I can't find an archive for it."
.
I AM NOT ABLE TO USE EVEN UBUNTU SOFTWARE CENTRE....
PLEASE HELP

Run on a terminal opened with CTRL+ALT+T:

```
sudo apt-get install --reinstall google-chrome-stable
```

then to check the integrity of the packages run:

```
sudo dpkg --configure -a
sudo apt-get -f install
```

---

### Post by sharatsn123 on 2011-12-08
Thanks guys for trying to help me but i am still getting the same error message.. The problem is not only for installing google chrome.. i am unable to install ANY software.:(

---

### Post by Paddy Landau on 2011-12-08
Please follow the [post=11519739]instructions that BC59 gave[/post].

Post here the *exact* error messages that each command gives.

---

### Post by oldsoundguy on 2011-12-08
Hate to ask a silly question, but, are you ON LINE with the computer?  In order to install ANYTHING from the repositories, you have to be on line.

---

### Post by BC59 on 2011-12-08
Run on a terminal:

```
sudo dpkg --configure -a
```

and then

```
sudo apt-get -f install
```

and post the results

---

### Post by sharatsn123 on 2011-12-09
> **BC59 said:**
> Run on a terminal:

```
sudo dpkg --configure -a
```and then

```
sudo apt-get -f install
```and post the results


sharat@ubuntu:~$ sudo dpkg --configure -a
[sudo] password for sharat: 
  
sharat@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package google-chrome-stable needs to be reinstalled, but I can't find an archive for it.
sharat@ubuntu:~$ 


*also i'm not able to reinstall google chrome as you suggested earlier *

---

### Post by BC59 on 2011-12-10
How started this? Do you have enabled the Google-Chrome repositories?

Try to enable the repository:

```
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add - 
```

setup

```
sudo sh -c 'echo "deb http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list'
```

and then

```
sudo apt-get update 
sudo apt-get install google-chrome-stable
```

---

### Post by sharatsn123 on 2011-12-10
> **BC59 said:**
> How started this? Do you have enabled the Google-Chrome repositories?

Try to enable the repository:

```
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add - 
```setup

```
sudo sh -c 'echo "deb http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list'
```and then

```
sudo apt-get update 
sudo apt-get install google-chrome-stable
```

many thanks... success!!!:D

---

### Post by BC59 on 2011-12-10
Please mark the thread as closed, from the thread tools close to the top.

---


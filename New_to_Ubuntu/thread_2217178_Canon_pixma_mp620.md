---
title: "Canon pixma mp620"
date: 2014-04-15
forum: New to Ubuntu
---

### Post by Trekafied on 2014-04-15
I'm having trouble with one particular step in a process to install my Canon pixma mp620 printer.

Let me go through the steps that I've done so that it makes a bit more sense.
[B]To get this script and install files you will need to install git.  Git is available in Ubuntu, Debian, and Mint from the base repositories.
[/B]
[B]sudo apt-get update
sudo apt-get install git-core
[/B]
[B]Once you have git installed, you will get the files using git.
[/B]
[B]git clone git://github.com/cloudnull/MP620-630-Linux-Printer.git


[/B]
These were the steps that I used to create a "script" which I think is what allows me to install
the printer driver? Ok, so those steps I have done. This is the one that confuses me:

[B]Now enter the installation directory
[/B]
**cd MP620-630-Linux-Printer/**


When I enter this command, I only get:

**~/mp620-630-linux-printers$**

The only thing that changes is that the slash and the cash sign change places, if that helps. It seems 
to be asking me for something else to enter in but I just don't know what to tell it to do.
This could be this case, it might not. I'm super new to Ubuntu 12.04 , and I know that many other people have
gotten this printer to work. Any help would be appreciated!

Here is the website with the instructions fyi:
[http://cloudnull.io/2011/05/mp-620-630-debian-based-univeral-installer/](http://cloudnull.io/2011/05/mp-620-630-debian-based-univeral-installer/)

---

### Post by jaspreet on 2014-04-16
Looking at the link that you have shared, what you are trying is a 2 step process:
1. Getting the script
2. Installing the printer

You have successfully completed step 1. Now, you need to move on to step 2, 
Once you have entered the installation directory using command: cd MP620-630-Linux-Printer/, perform below steps:
> 1. sudo su
2. sudo chmod +x install.sh
3. ./install.sh

Or
just fire below command
sudo bash install.sh

This will start the installation process. Once it completes without any errors, your printer is successfully installed!

---

### Post by Trekafied on 2014-04-17
Ok, so as i understand it, I've entered the installation directory in my above post already by using that exact command, the first part of your part 2, giving me:

**~/mp620-630-linux-printers$**

Which is me entering the installation directory from my terminal, which is what confused me at first. Then, I add onto that information by adding

[B]sudo bash install.sh
[/B]
So that it will look something like this when entered in:

**~/mp620-630-linux-printers$****sudo bash install.sh**

Feel free to steer me right if I've got something wrong.

---

### Post by mörgæs on 2014-04-17
[http://ubuntuforums.org/showthread.php?t=361236&page=88&p=12909495&viewfull=1#post12909495](http://ubuntuforums.org/showthread.php?t=361236&page=88&p=12909495&viewfull=1#post12909495)

---

### Post by Trekafied on 2014-04-17
Thanks much for the thread morgaes, but it is talking about an older printer.

jaspreet, I tried your method and it work for me! I can now print and scan from my computer! Thank you so much!

---


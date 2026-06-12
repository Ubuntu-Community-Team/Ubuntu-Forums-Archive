---
title: "I need to install QTstalker  I am using Ubuntu 12.04 LTS"
date: 2012-05-31
forum: New to Ubuntu
---

### Post by jose53 on 2012-05-31
I would like to download and install QTSTalker on Unbuntu 12.4 LTS
I need to know the commands ,
I tried to download it from the Ubuntu software center and fails to finish the installation.
I change the permission setting on my Etc\Apt\sources.list and added the owner HTTP:/ address and it returned a failed four digit number.
I need help!!! thank you for your help

---

### Post by ubudog on 2012-05-31
Could you post the output of:
```
sudo apt-get update
```

---

### Post by jose53 on 2012-05-31
W: GPG error: [http://www.zwets.com](http://www.zwets.com) unstable/ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY AFC0079DA217C012

---

### Post by Curtis6767 on 2012-05-31
I have spent countless hours trying to figure out Qtstalker and it just isn't worth the effort. You can't change indicators once you've selected them. It's an absolute waste of time.

 Hasn't been updated in years. No clear installation of users guide. I think that Qtstalker is part of the reason I had to do a fresh install two weeks after 12.04LTS came out.

I wouldn't touch it. 

If you are looking for stock market stuff, you can find several flash-based sites that offer good charts.

---

### Post by Curtis6767 on 2012-06-03
Here is a link on how to install QTstalker.

 No guarantees it's going to work and this could easily bork your system requiring a fresh install. 

Just a suggestion, but you might want to set up a virtual OS using Virtual Box and see if you can get it to work that way.
 
Be sure to scroll down below the image of Synaptic Package Manager and look at all the other stuff you need to do*** before*** you install QTstalker. You may already have some of those packages installed and some are in the Software Center. 



[http://www.marketcalls.in/softwares/qtstalker-open-source-trading-software-for-ubuntu-11-10.html](http://www.marketcalls.in/softwares/qtstalker-open-source-trading-software-for-ubuntu-11-10.html)

Good luck and if you get it working, please inform.

---

### Post by Old_Grey_Wolf on 2012-06-03
> **jose53 said:**
> W: GPG error: [http://www.zwets.com](http://www.zwets.com) unstable/ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY AFC0079DA217C012

To get the PUBKEY enter these commands:
```
gpg --keyserver keyserver.ubuntu.com --recv AFC0079DA217C012

gpg --export --armor AFC0079DA217C012 | sudo apt-key add -
```

QTstalker is a good program after you figure out how to use it.

---

### Post by jose53 on 2012-06-03
Qtstalker is an excellent program ,  I have been using Puppy Linux and Qtstalker works really good. Qtstalker = excellent  +++.  Thank you for your help.  to Mr Old_Gray_Wolf the code that you gave me worked like a charm. thank you. I went back to the ubuntu's software center and I tried to download Qtstalker again and it gave me the following message:

The following packages have unmet dependencies:

qtstalker: Depends: libc6 (>= 2.7-1) but 2.15-0ubuntu10 is to be installed
           Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed
           Depends: libqt3-mt (>= 3:3.3.8b) but 3:3.3.8-b-8ubuntu3 is to be installed
           Depends: libstdc++6 (>= 4.1.1) but 4.6.3-1ubuntu5 is to be installed
 
thank you .

---

### Post by Old_Grey_Wolf on 2012-06-04
I assume that QTstalker is not working because of the unmet dependencies. Is that correct?

---

### Post by bluswall on 2012-06-05
Try using the ppa found on this site. Had the same problem as you and after updating the sourses.list SENAPTIC had no problem :smile:
[https://launchpad.net/~mario-mariomedina/+archive/qtstalker-stable]("https://launchpad.net/%7Emario-mariomedina/+archive/qtstalker-stable")

let us know if it works for you

bluswall

---

### Post by jose53 on 2012-06-08
Your are correct.  Unmet dependencies

---

### Post by Old_Grey_Wolf on 2012-06-08
> **bluswall said:**
> Try using the ppa found on this site. Had the same problem as you and after updating the sourses.list SENAPTIC had no problem :smile:
[https://launchpad.net/~mario-mariomedina/+archive/qtstalker-stable]("https://launchpad.net/%7Emario-mariomedina/+archive/qtstalker-stable")

let us know if it works for you

bluswall

That PPA does not contain a package for 12.04 (Precise).

---

### Post by Old_Grey_Wolf on 2012-06-08
Try entering this command to install the unmet dependencies ```
sudo apt-get -f install
```

---

### Post by jose53 on 2012-06-08
ubuntu@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ubuntu@ubuntu:~$

---

### Post by Old_Grey_Wolf on 2012-06-08
Enter this command and post results ```
sudo apt-get update
```

Then enter this command and post output ```
sudo apt-get dist-upgrade
```

---

### Post by jose53 on 2012-06-08
I was trying to install the dependencies , I am getting the following error. Items can not be installed or remove until the Catalog is fix. Broken It can not be repaired

---

### Post by Old_Grey_Wolf on 2012-06-08
You are not giving me the information I have asked for. I need it in order to help you.

Therefore, I will let someone else help you for now. I will be off-line for the next 12 to 24 hours anyway.

---

### Post by Old_Grey_Wolf on 2012-06-09
Try these commands to fix the catalog

```
sudo dpkg --configure -a

sudo apt-get -f install

sudo apt-get --fix-missing install

sudo apt-get update

sudo apt-get dist-upgrade
```

---

### Post by jose53 on 2012-06-11
Thank you ... thank you .! every - one Qtstalker is working on my machine.(my new computer I  got rid of windows)  Mr Gray Old Wolf you sir!! are the best . I would love to shake your hand !! in this case a humble thank you !! Your instructions helped me solve my Qtstalker installation problem . 
Sudo apt--get dist-upgrade . It can be done!  I am very  happy and in Fuego!!  it is time to start trading and make some money!!

---

### Post by Old_Grey_Wolf on 2012-06-11
I am glad it is working.

I am sorry if some of my responses seemed terse.

I got a little frustrated. Not with you necessarily. Some of the other posts frustrated me. 

I apologize.

Qtstalker is one tool to analyse investments. It is only one tool to use in your arsenal. Use common since, an exit strategy for investments, and some fundamental knowledge about the sectors your invest in.

---


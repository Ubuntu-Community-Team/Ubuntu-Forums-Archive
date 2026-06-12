---
title: "problem Installing Skype"
date: 2011-02-16
forum: Philippine Team
---

### Post by eeeris on 2011-02-16
Kamusta!

Im having a problem installing skype, According sa error message. please see attached screeshot. Patulong naman kung pano ko masolve. Your reply will be highly appreciated. Thanx! :)

---

### Post by lfforman on 2011-02-16
did you try to download from skype website? thats how i normally install it.

---

### Post by jepong on 2011-02-16
looks like old Qt toolkits. Maybe you should add ppa:kubuntu-ppa/ppa on your repository

```

sudo add-apt-repository ppa:kubuntu-ppa/ppa
sudo apt-get update
sudo apt-get install skype

```

yes... you're correct... its a Kubuntu PPA and this one has Qt 4.5. If you want the latest Qt 4.6, add ppa:kubuntu-ppa/backports instead.

---

### Post by jepong on 2011-02-16
oh wait... teka... have you tried using aptitude instead of apt-get? can you try it first. weird because apt-get should also install missing dependecies when a package needs it.

maybe you can manually install the dependecies so you won't add additional repository as I first suggested. :D

---

### Post by zeroseven0183 on 2011-02-16
Download mo na lang yung para sa Ubuntu sa [Skype download page]("http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/").

---

### Post by ITC on 2011-02-16
Since Ubuntu 10.04 (Lucid Lynx), Skype is part of the Canonical partner repository. To install Skype add the [Canonical Partner Repository](https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Canonical%20Partner%20Repositories) and install Skype via the [Software-Center](https://help.ubuntu.com/community/SoftwareCenterFAQ) or via the Terminal. 
[Skype - Community Ubuntu Documentation](https://help.ubuntu.com/community/Skype)

You can add the Apt source like this 
```
echo "deb http://download.skype.com/linux/repos/debian/ stable non-free #Skype" | sudo tee -a /etc/apt/sources.list > /dev/null
```
Import the Apt key, even it is not used, but may be useful in future: 
```
sudo apt-key adv --keyserver pgp.mit.edu --recv-keys 0xd66b746e
```
Install Skype: 
```
sudo apt-get update && sudo apt-get install skype
```

---

### Post by jepong on 2011-02-16
> **zeroseven0183 said:**
> Download mo na lang yung para sa Ubuntu sa [Skype download page]("http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/").

deb file from skype will also install necessary dependency like Qt which is (i think) not part of the skype deb package. :-D you can try this by installing the deb while not connected to the internet that is if you don't have any Qt stuff installed. :D

---

### Post by tech-hero on 2011-02-16
> **ITC said:**
> Since Ubuntu 10.04 (Lucid Lynx), Skype is part of the Canonical partner repository. To install Skype add the [Canonical Partner Repository]("https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Canonical%20Partner%20Repositories") and install Skype via the [Software-Center]("https://help.ubuntu.com/community/SoftwareCenterFAQ") 
 
 
This worked for me . :) Using UBUNTU 10.04 LTS.

---

### Post by jepong on 2011-02-16
some find installing using the terminal dramatic... that includes me. I love the way you see installation progress in text. I find apt-get and aptitude very messy on terminal. The most neat package manager I saw is Yum.

---

### Post by Script Warlock on 2011-02-16
why complicate things when this can be done thru synaptics or ubuntu software?.

---

### Post by jepong on 2011-02-17
i don't think typing thru terminal is a complicated thing, it makes you aware of necessary and more often unnecessary stuff being installed... unless one is lazy. :)

---


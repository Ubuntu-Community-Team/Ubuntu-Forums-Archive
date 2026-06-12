---
title: "Skype"
date: 2014-04-30
forum: New to Ubuntu
---

### Post by daniel146 on 2014-04-30
Hi, name is Dan, Daniel just joined. We know each other now? Okay? Okay. Anyway, I tried to download Skype on this computer, and I couldn't find the Lubuntu version , so I downloaded the 10.4 32 bit version and after attempting to install Skype it gave me an error and now, the install Window appears and tells me: "Broken dependencies".
Any suggestions on what to do?

---

### Post by monkeybrain20122 on 2014-04-30
Instead of downloading from skype you can install from the repo. I don't know if there is any difference but I have never had any trouble with skype installed this way though I have read numerous threads where people are having problems with skype downloaded from its website (but honestly I have never had problems with skype from its website on other distros either)

In lubuntu synaptic is already installed. Open synaptic, go to Settings > Repositories and go to the tab "Other Software" and check the box "Canonical's Partners" then close the dialogue and reload synaptic. Now search for skype then just click and install.

---

### Post by daniel146 on 2014-04-30
> **monkeybrain20122 said:**
> Instead of downloading from skype you can install from the repo. I don't know if there is any difference but I have never had any trouble with skype installed this way though I have read numerous threads where people are having problems with skype downloaded from its website (but honestly I have never had problems with skype from its website on other distros either)

In lubuntu synaptic is already installed. Open synaptic, go to Settings > Repositories and go to the tab "Other Software" and check the box "Canonical's Partners" then close the dialogue and reload synaptic. Now search for skype then just click and install.

Okay, I went to Synaptic and it gave me two Canonical Partner options:
1. Canonical Partners Source Code
2. Canonical Partners standard
Do I just use the standard? Also, what about the broken Dependencies it stated from trying to download it? Also, upon opening Synaptic it informed me there were broken packages- I'm not really sure how to fix those. This is my first time having Lubuntu as an OS

---

### Post by monkeybrain20122 on 2014-04-30
Don't worry the source codes, they are not available for the Partners' repo anyway (closed source stuffs like skype) 

To fix broken dependencies, in synaptic click Edit > Fix Broken Packages then relaunch synaptic
What are the broken dependencies? Have you tried to install the downloaded package from skype? In that case it should be installed after fixing broken packages and if it works you don't need to install from Partners'

---

### Post by Don_Tai on 2014-05-01
I just installed Skype today for Lubuntu 14.04. Though I tried to download directly using Synaptic, Skype is not available. Skype has 11 dependencies before it can run. You need to ensure you install all these dependencies first. I used Synaptic, typed the dependency names in (they are listed when you try to run the skype install package), and installed them all in one go.

The downloaded Skype package is a .deb file and I did not know how to install it. I used the GDebi Package Installer:
<code>
cd /Downloads
sudo su -c &#8220;gdebi skype-ubuntu*4*.deb&#8221;
</code>

I found the method here: [http://tutorialforlinux.com/2014/04/24/how-to-install-latest-skype-on-lubuntu-14-04-trusty-tahr-lts-32-64bit-step-by-step-easy-guide/](http://tutorialforlinux.com/2014/04/24/how-to-install-latest-skype-on-lubuntu-14-04-trusty-tahr-lts-32-64bit-step-by-step-easy-guide/)

Cheers!

---

### Post by monkeybrain20122 on 2014-05-01
It is in synaptic if you activate the Partner's repo. 

Not sure who wrote that tutorial but it doesn't make a lot of sense. The sudo su is not necessary, you don't need to become root. Also the whole point of gdebi is that you can install .deb by right clicking, to run it in the terminal defeats the purpose. Normally if you install .deb with gdebi you don't need to install dependencies separately as it will download and install them. In 14.04 gdebi has a bug and doesn't do that. You can still install by right clicking and run "sudo apt-get -f install" after to fix the dependencies, therefore there is still no need to install all the dependencies by hand. There was a gdebi update either yesterday or this morning so that bug may have been fixed.

But as I said before the preferable way is to install it from synaptic.

---


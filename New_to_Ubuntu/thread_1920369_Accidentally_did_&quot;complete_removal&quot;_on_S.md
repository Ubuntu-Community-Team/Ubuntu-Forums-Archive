---
title: "Accidentally did &quot;complete removal&quot; on Synaptic, how to restore?"
date: 2012-02-04
forum: New to Ubuntu
---

### Post by flushentitypacket on 2012-02-04
I'm on Ubuntu 11.10 and accidentally did a "complete removal" of Skype on Synaptic when I meant to do a normal removal. How do I restore the configuration files so that I can reinstall Skype on Synaptic?

Thanks, all! :)

---

### Post by Cowboybebop79 on 2012-02-04
You should be able to install it again it just wont have any of your preferances or password saved. You will need to set those up again

---

### Post by flushentitypacket on 2012-02-04
> **Cowboybebop79 said:**
> You should be able to install it again it just wont have any of your preferances or password saved. You will need to set those up again
How? Because I did a "complete removal," it no longer shows up as a package on Synaptic.

---

### Post by Cowboybebop79 on 2012-02-04
Which version of ubuntu are you using?

Did you download skype and install it from a deb file?

Completely removing from synaptic only Uninstalls the program **and** removes the config files for the program it doesn't remove it from synaptic as synaptic just shows a list of the packages that can be installed from the server you are connected to "you" cannot remove skype from the server

---

### Post by durand on 2012-02-04
If it isn't showing up in synaptic, you probably just got Skype off their website rather than installing it directly from the Software center. It should work if you just get it from here: [http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/](http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/)

---

### Post by jerrrys on 2012-02-04
Its in synaptic

sudo apt-get install skype

---

### Post by yetiman64 on 2012-02-04
> **jerrrys said:**
> Its in synaptic

sudo apt-get install skype
OP, you will find skype is in the repositories, BUT, you have to ensure you have the "Canonical Partners" repository enabled in software sources first. 

Once the repo is enabled you can search for and find it by entering "skype" in the search box. The package I installed here from synaptic is the "skype:i386" package (note I'm on 64 bit machine and 64 bit 11.10 install). This setup of skype is working fine here.

---

### Post by flushentitypacket on 2012-02-05
> **Cowboybebop79 said:**
> Which version of ubuntu are you using?

Did you download skype and install it from a deb file?

Completely removing from synaptic only Uninstalls the program **and** removes the config files for the program it doesn't remove it from synaptic as synaptic just shows a list of the packages that can be installed from the server you are connected to "you" cannot remove skype from the server
You are all correct. Sorry for my fail understanding of how it works. :)

Thanks, everyone!

---


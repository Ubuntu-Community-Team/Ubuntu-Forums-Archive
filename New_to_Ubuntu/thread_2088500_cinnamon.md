---
title: "cinnamon"
date: 2012-11-26
forum: New to Ubuntu
---

### Post by oldtechynot on 2012-11-26
not sure if I did this right or not but here go's

trying to install cinnamon on ubuntu 12.10

$sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-stable
$sudo apt-get update
$sudo apt-get install cinnamon

when I hit enter it asks for password but nothing happens when I type it in. the white cursor just keeps flashing
what should I do to fix my delema?

---

### Post by Frogs Hair on 2012-11-26
Hello and Welcome

Did you enter the commands one at a time? You should get a password prompt when adding the repository and you shouldn't see it for the two remaining commands. When the repository is found you will be asked to continue adding it. Once added run the other two commands in order.

---

### Post by DoABarrelRoll on 2012-11-26
The password doesn't show up as you type it. I was curious about the same thing when trying to install Android Debugging Bridge and Fastboot to play around with my droid. 

Simply type your password that you set when you installed ubuntu and hit enter. It should read it just fine and continue with the installation. Same deal installing ADB and fastboot. 

:)

If that doesn't work, I leave you with a more experienced Linux user. I just had the same question and said the heck with it, I'll just type it in hit enter and see what happens and it worked.

---

### Post by ibjsb4 on 2012-11-26
You may find this helpful.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=how+to+enter+password+in+terminal&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=how+to+enter+password+in+terminal&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

---

### Post by oldtechynot on 2012-11-27
no matter how I do it, it dose not work at all. I would like to know how this is any different than windows except in windows you can install or add programs without problems like this!

---

### Post by Frogs Hair on 2012-11-27
I know the source command is valid because this is what I see when it is run and I enter the password ```
 sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-stable
[sudo] password for david: 
You are about to add the following PPA to your system:
 This PPA contains the stable releases of cinnamon for Oneiric and Precise. Oneiric will not get any new updates.

Cinnamon website : http://cinnamon.linuxmint.com/
 More info: https://launchpad.net/~gwendal-lebihan-dev/+archive/cinnamon-stable
Press [ENTER] to continue or ctrl-c to cancel adding it

```

---

### Post by Frogs Hair on 2012-11-27
This may be a problem though because Quantal 12.10 is not included in the description.   


>  This PPA contains the stable releases of cinnamon for Oneiric and Precise

Edit: According to the linked article the PPA works with 12.10 and I see the Quantal  pkg on the Lauchpad page.    [http://handytutorial.com/cinnamon-1-6-released-install-ubuntu-12-04-12-10/](http://handytutorial.com/cinnamon-1-6-released-install-ubuntu-12-04-12-10/)

PPA: [https://launchpad.net/~gwendal-lebihan-dev/+archive/cinnamon-stable](https://launchpad.net/~gwendal-lebihan-dev/+archive/cinnamon-stable)

---


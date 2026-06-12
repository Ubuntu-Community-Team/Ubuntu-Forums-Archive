---
title: "can't install wine"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by irish66 on 2008-11-08
getting message
E: /var/cache/apt/archives/wine_1.1.8~winehq0~ubuntu~8.10-0ubuntu1_i386.deb: unable to stat `./usr/share/applications/wine-browsedrive.desktop' (which I was about to install)

---

### Post by mr nintendo on 2008-11-08
open up terminal and type:

```
sudo apt-get install wine
```

---

### Post by irish66 on 2008-11-08
did that-thank you
[sudo] password for irish: 
irish@ubuntu:~$ 
irish@ubuntu:~$ 
irish@ubuntu:~$ 
irish@ubuntu:~$

---

### Post by Mickeyj4j on 2008-11-08
I am using Ubuntu 8.04.1 Lts Desktop Edition installed within windows xp. I cant connect to the net(I only have a dialup modem which will not work). I tried installing the Wine package # Wine 1.1.7 i386, -dev manually from [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html) (onto my flash Drive from xp) When i tried to install it I got this error message. 

Error Dependency is not Satisfiable: binfmt-support 

In advance, Thanks for taking the time to reply.

---

### Post by gandaran on 2008-11-08
> **Mickeyj4j said:**
> I am using Ubuntu 8.04.1 Lts Desktop Edition installed within windows xp. I cant connect to the net(I only have a dialup modem which will not work). I tried installing the Wine package # Wine 1.1.7 i386, -dev manually from [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html) (onto my flash Drive from xp) When i tried to install it I got this error message. 

Error Dependency is not Satisfiable: binfmt-support 

In advance, Thanks for taking the time to reply.

forget this package and get wine from the ubuntu hardy 8.04 repos [http://packages.ubuntu.com/hardy/](http://packages.ubuntu.com/hardy/)
you'll have to download the wine dependencies here too

---

### Post by alwayshere on 2008-11-08
add below into your Repository

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) hardy main #WineHQ - Ubuntu 8.04 "Hardy Heron"

then open terminal put

sudo apt-get update

right click on below address and save to desktop 
[http://wine.budgetdedicated.com/apt/Scott%20Ritchie.gpg](http://wine.budgetdedicated.com/apt/Scott%20Ritchie.gpg)

now go to system then admiistration then  software sources
then authentication then import key file and navagate to the 
file you downloaded to desktop and import it .
once file is imported you can delete it from your desktop .
while you in software sources. Put main server in the download from box .

then open terminal put

sudo apt-get update

now try 

sudo apt-get install wine

---

### Post by irish66 on 2008-11-08
WEll looking at my first message
E: /var/cache/apt/archives/wine_1.1.8~winehq0~ubuntu~8.10-0ubuntu1_i386.deb: unable to stat `./usr/share/applications/wine-browsedrive.desktop' (which I was about to install)

i presume E"/ refers to my E windows drive.
This is a drive on my hd which is partioned into 3 drives.
initially it did show in ubuntu, but not anymore
although it does show in windows.
Well I'll give it another go
M

---

### Post by gandaran on 2008-11-08
> **irish66 said:**
> WEll looking at my first message
E: /var/cache/apt/archives/wine_1.1.8~winehq0~ubuntu~8.10-0ubuntu1_i386.deb: unable to stat `./usr/share/applications/wine-browsedrive.desktop' (which I was about to install)

i presume E"/ refers to my E windows drive.
This is a drive on my hd which is partioned into 3 drives.
initially it did show in ubuntu, but not anymore
although it does show in windows.
Well I'll give it another go
M
E: has nothing to do with windows drive, it's for ERROR
open synaptic package manager, scroll down to wine, if its installed (green box) mark it for complete removal and click the apply button.
now run these commands one at a time in the terminal
**sudo apt-get clean**
**sudo apt-get autoclean**
**sudo apt-get update**
now find the wine options again and mark for install, click the apply button, should work.

type your password in the terminal when it asks for it, you won't see it just hit enter next

---

### Post by irish66 on 2008-11-08
thank you, but unfortunately that didn't work/
i probably should post the link i'm using 
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
hmm, maybe it's because they are beta pacages.
I'll see if i can install one of the stable versions

---

### Post by gandaran on 2008-11-08
look, if you want help, you should describe what did not work or post any errors here

---

### Post by irish66 on 2008-11-08
here;swhat i did
1.went to
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
did as instructed ie
Open the Software Sources menu by going to System->Administration->Software Sources. Then select the Third Party Software tab and click Add.
then
Then, copy and paste one of the lines below depending on which version you are running.
ie For Ubuntu Intrepid (8.10):
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex" 
then
After adding the repository, you also need to add the key for the repository to your system's list of trusted keys.

Download and save Scott Ritchie's key to your desktop. Then open the Authentication tab, click import key file, and select the key file you just saved (Scott Ritchie.gpg). It is safe to delete this file after doing this step.

i then looked for wine in applications-add remove, and put a tick in the box.
I CLICK APPLY CHANGES, then apply
it goes to preparing pacages-preparing wine-error in pacage
E: /var/cache/apt/archives/wine_1.1.8~winehq0~ubuntu~8.04-0ubuntu1_i386.deb: unable to stat `./usr/share/applications/wine-browsedrive.desktop' (which I was about to install)

so i decided to have a go with synaptic pacaging manager.
i searched for wine and found three instances of it
wine
wine-dev
wine-gecko
the first has an arrow within the box and the text is highlighted in green, The other two have green boxes
i managed to mark them all for removal, but they still show up in pacage manager albeit with white boxes.
i then did a reinstall, but still getting
the same error message as above.

---

### Post by gandaran on 2008-11-08
you get this error message when installing any application because you have a broken package in cache
now you must try to remove this broken package from you system first, run these commands in the terminal, if any error messages post them back here
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get update
after running these commands try installing wine again

---

### Post by gandaran on 2008-11-08
also I think you should remove the wineHQ repo you added to the sources list and just try installing wine from the official ubuntu repos.

---

### Post by irish66 on 2008-11-08
okay
did as instructed
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_IE
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid Release
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release                
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates Release
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/main Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/restricted Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/main Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/universe Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/universe Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/multiverse Sources
Reading package lists... Done
irish@ubuntu:~$ 

except now I'm getting
"Failed to check for installed and available applications
This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'."
okay time for a reboot
time to get out
M

---

### Post by gandaran on 2008-11-08
> so i decided to have a go with synaptic pacaging manager.
i searched for wine and found three instances of it
wine
wine-dev
wine-gecko
the first has an arrow within the box and the text is highlighted in green, The other two have green boxes
i managed to mark them all for removal, but they still show up in pacage manager albeit with white boxes.
i then did a reinstall, but still getting
the same error message as above.

wine-gecko is a dependency or wine, you just mark for install wine wine-gecko just gets pulled for install too, don't mark for install wine-dev

---

### Post by gandaran on 2008-11-08
> "Failed to check for installed and available applications
This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information

theres something wrong with the /etc/apt/sources.list, maybe it is the wineHQ repo you added, try removing it and try again or post the sources list here

---

### Post by irish66 on 2008-11-08
Well after reading another wine thread. I decided not to bother with it, as the windows programs i want to run on it are probably quite complex
Thanks for all the help.
M

---

### Post by Mickeyj4j on 2008-11-13
Wow thanks but I am having trouble finding Wine and the dependences as i do not know which section to find everthing. I am very New to Linux what can you suggest

---

### Post by Mickeyj4j on 2008-11-13
> **gandaran said:**
> forget this package and get wine from the ubuntu hardy 8.04 repos [http://packages.ubuntu.com/hardy/](http://packages.ubuntu.com/hardy/)
you'll have to download the wine dependencies here too

> **Mickeyj4j said:**
> Wow thanks but I am having trouble finding Wine and the dependences as i do not know which section to find everthing. I am very New to Linux what can you suggest

:confused: :confused: :confused: :confused: :confused: :confused:

---

### Post by Mickeyj4j on 2008-11-13
> **gandaran said:**
> forget this package and get wine from the ubuntu hardy 8.04 repos [http://packages.ubuntu.com/hardy/](http://packages.ubuntu.com/hardy/)
you'll have to download the wine dependencies here too

> **Mickeyj4j said:**
> Wow thanks but I am having trouble finding Wine and the dependencies as i do not know which section to find everthing. I am very New to Linux what can you suggest

well I found the right section now got the wine install. what are the dependencies do i need all of the other wine related files suggested here

[http://packages.ubuntu.com/hardy/otherosfs/wine](http://packages.ubuntu.com/hardy/otherosfs/wine)

---

### Post by gandaran on 2008-11-13
> **Mickeyj4j said:**
> well I found the right section now got the wine install. what are the dependencies do i need all of the other wine related files suggested here

[http://packages.ubuntu.com/hardy/otherosfs/wine](http://packages.ubuntu.com/hardy/otherosfs/wine)
try installing the the wine package, it'll tell you what dependencies are missing and you have to install first, wine is the last package to install

---

### Post by irish66 on 2008-11-15
Yipee. got wine to run. Maybe it was one of the pacage updating 
I did.
M

---


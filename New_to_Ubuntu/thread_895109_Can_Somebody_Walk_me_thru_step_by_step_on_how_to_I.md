---
title: "Can Somebody Walk me thru step by step on how to Install Stuff"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by mattcadu on 2008-08-19
I cant figure it out for the life of me

---

### Post by halitech on 2008-08-19
easiest way is by going to Applications - Add/remove programs and searching for what you want to install

---

### Post by Crafty Kisses on 2008-08-19
This link may help you > [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by tuxulin on 2008-08-19
by looking through some of this will give you a fair idea how to install pretty much all that you need.
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28ATI.%2029](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28ATI.%2029)

or for a wider approach you could digest this 
one stage at a time

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

and lastly you could try this
[http://polishlinux.org/first-steps/installing-software/](http://polishlinux.org/first-steps/installing-software/)

its not real difficult once you spend a day or two 
looking at and trying out some installation examples in the above links.

once you get you head around that then it will become all clear in an instant

Tuxulin

---

### Post by mattcadu on 2008-08-19
Thing is when i download something... lets say its on the desktop, i cant find it in Add/remove

---

### Post by R.Bucky on 2008-08-19
The applications that you download have to be installed using your terminal/konsole, similar to command line in Windos. Stick with the Add/Remove Programs for now. Do you have a particular program that is not in the Program list?

---

### Post by OutOfReach on 2008-08-19
See
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
It explains how to install anything...

---

### Post by mattcadu on 2008-08-19
Well First thing is First I cant run frostwire Cause i cant install Java , ... thats for starters 
and i cant play video cause i need codecs

jre-6u7-linux-i586.bin   


this files is downlaoded to my desktop

---

### Post by halitech on 2008-08-19
check here for a complete multimedia, streaming instruction

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by tuxulin on 2008-08-19
what did you try to download ?
how did you download it ?

not every software you download will show up, however all installed
software can be run from the CLI .

sometimes certain software may not show in the menu
you could try "system >> preference >> main menu" then look for the app
and click check.

if not then try whereis from CLI eg. >whereis name-of-software<

---

### Post by oldos2er on 2008-08-19
[https://help.ubuntu.com/8.04/add-applications/C/index.html](https://help.ubuntu.com/8.04/add-applications/C/index.html) and [https://help.ubuntu.com/8.04/musicvideophotos/C/index.html](https://help.ubuntu.com/8.04/musicvideophotos/C/index.html)

---

### Post by aysiu on 2008-08-19
Here's yet another guide for you:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

For Frostwire, you should be able to just double-click [this file](http://main2.frostwire.com/frostwire/4.17.0/frostwire-4.17.0.i586.deb) and follow the prompts.

---

### Post by Gregmond on 2008-08-20
There are also various other options such as Ultamatix (replaces Automatix I believe) and is aimed at adding Linux/Open Source type software, or wine and then wine-doors will give you various other web browser options for video content but this is more about getting Windos software running on a Linux PC. Google them for the install.

If you are running a 64-bit OS, it can be an advantage to install a 32-bit web browser to get codecs/java etc etc to work better.

---

### Post by oldos2er on 2008-08-20
> **mattcadu said:**
> Well First thing is First I cant run frostwire Cause i cant install Java , ... thats for starters 
and i cant play video cause i need codecs

jre-6u7-linux-i586.bin   


this files is downlaoded to my desktop

 It's best (and easiest for someone new to Linux) to install software from the repositories. Open up a terminal and type "sudo aptitude update && sudo aptitude install ubuntu-restricted-extras". This will install java, Flash, and some other goodies.

---

### Post by todaymueller on 2008-08-20
Yes I have not worked out how to install things I have downloaded either . For instance adobe flash player , it was sat on my desktop but I could not get it to install .  Eventually I gave up , then had a look in the synaptic package manager , Where I found a flash player and installed it no problem .
Where was I going wrong ?

---

### Post by aysiu on 2008-08-20
> **todaymueller said:**
> 
Where was I going wrong ? Downloading things separately instead of having Synaptic Package Manager handle the downloading and installation for you.

---

### Post by appi2012 on 2008-08-20
Ubuntu is not like windows, where you download files and double click them to install. In ubuntu, there are repositories of software. The default ubuntu repository has pretty much everything you will need. To install programs from the repository, you go to Applications -> Add Remove, and search for what you want to install. If it has a check by it, it is installed. If not, it in uninstalled. You can check it to install it. For video codecs, installing the "ubuntu restricted extras" package may fix the problem. Try searching for it in Add-Remove. Also, search for "gstreamer" and check the packages that say "Gstreamer Codecs..."

---

### Post by anotherdisciple on 2008-08-20
Let's take care of all your codec needs and java needs at once!

Open up the terminal... 

Applications > Accessories > Terminal

... and type this

```
sudo aptitude install ubuntu-restricted-extras
```

Now... I would personally go with frostwire... which is a limewire clone... it works well and their website should have a .deb file of it. And yes, you can double click it just like a .exe in windows.

edit: whoops... typo

---

### Post by todaymueller on 2008-08-21
Thanks for that . all working fine .:guitar:

---


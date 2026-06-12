---
title: "Trouble Installing Wine"
date: 2011-12-20
forum: New to Ubuntu
---

### Post by Momof9Blessings on 2011-12-20
When I was installing Ubuntu - I was having a hard time with the disc - would work on live, then the next time I tried it (to install) - the disc would quit working.... I did eventually try a different brand and was able to install....

But, when I first tried to install it.... I ended up doing a partial install of the server 11.10 32 bit instead of desktop....  I stopped this when I realized the problem....

When I was trying to install wine earlier everything was working fine, until I got to "You can now install Wine by typing 'sudo apt-get install wine1.3'."  I was getting the message that I need to insert the "server" cd.....  and it would never work just keeps asking for me to insert disc....

any ideas???

---

### Post by Lisiano on 2011-12-20
I don't exactly get why it is asking for a CD but, try copy pasting these commands into a terminal, the first one turns on the Wine-PPA, 2nd one updates the local index, 3rd actually installs wine.
```
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine1.3
```
Also, are you following some sort of tutorial? Could you please post a link to it just in case?

---

### Post by Momof9Blessings on 2011-12-20
I have done the above several times....  

It happens when I get to the 3rd line.... 

I even have tried it from within Ubuntu Software Center - it is asking for a disc....

Right now, I am burning the "server" disc.... someone elsewhere suggested I might want to "start over" and get the server info off.  But I thought when I installed the desktop version and it "partitioned" my HD it was reformatting it then....

---

### Post by garyhibdon on 2011-12-20
i hate to say it man, but it sounds like you only have a prtial install. make sure the computer is connected to the internet and type:

```
sudo apt-get install wine
sudo apt-get upgrade
sudo apt-get update
```

that should make sure that all the proper drivers are installed. if this doesnt work, id re-install with the same disc, but make sure to delete the previous partition, just to make sure that you dont have any proprietary files hanging around.

good luck man

---

### Post by Lisiano on 2011-12-20
I don't know what else you could do except try this. Type this in a terminal ```
gksudo gedit /etc/apt/sources.list
``` A window will popup and ask you for a password, give it. Now another window will popup with text in it, find any line that starts with ```
deb cdrom:
``` For example ```
deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20070419.1)]/ natty main restricted
``` Now prepend a # (Hash) to them like so ```
#deb cdrom:
``` So for our example it would look like this ```
#deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20070419.1)]/ natty main restricted
``` Save the file, close the editor and enter this command in a terminal again ```
sudo apt-get update
``` then try to install Wine again.

---

### Post by Momof9Blessings on 2011-12-20
Thank you Lisiano - that actually worked....

I guess sometime tomorrow I will have to try to install CS3!!!  YEA!!!

---


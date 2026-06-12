---
title: "cli dialog interface help"
date: 2013-02-20
forum: Programming Talk
---

### Post by iceman30ad on 2013-02-20
I will admit it i am fully expecting to be told to go back to the sand box and play with the script kiddies.

my issue is this i pieced( cant say wrote kanged from multiple sites and a few friends)  together a script to help me with reinstalling my system when i break it to bad to recover. a few friends want a copy of my script but would like it to have a gui interface. Request is either teach me how to do it or do  a few lines of it for me so i can see the context and how to do it for my self  for when i change it up. already know about dialog but i need to see examples of how to use it before i can implement it my self .

here is the script so you know what your getting in to any help is appreated
```

#!/bin/bash

echo "this is an install script for my favored apps 
xbmc calibre medibuntu"


echo '#!/bin/bash
#
#
#
###
 
#backup org. 
read -p "Is this a fresh install? (y/n)?" CONT;
if [ "$CONT" = "n" ]; then
  cp /etc/apt/sources.list.orig /etc/apt/sources.list;
else
  cp /etc/apt/sources.list /etc/apt/sources.list.orig;
fi

#enable repo scripts
apt-get install python-software-properties
  

wget -q -O - http://archive.getdeb.net/getdeb-archive.key | apt-key add -
echo "deb http://archive.getdeb.net/ubuntu precise-getdeb games" >> /etc/apt/sources.list.d/getdeb.list

wget -q -O - http://archive.getdeb.net/getdeb-archive.key | apt-key add -
echo "deb http://archive.getdeb.net/ubuntu precise-getdeb apps" >> /etc/apt/sources.list.d/getdeb.list

add-apt-repository ppa:tualatrix/ppa

wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && apt-get --quiet update && apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && apt-get --quiet update

sudo add-apt-repository ppa:me-davidsansome/clementine' >> ./ReposProgs.sh

sudo bash ./ReposProgs.sh
rm ./ReposProgs.sh
sudo apt-get --quiet update
sudo apt-get --yes --quiet install app-install-data-medibuntu apport-hooks-medibuntu ubuntu-tweak xbmc synaptic clementine ubuntu-restricted-extras libdvdcss2

read -p "install calibre (y/n)?" CONT;
if [ "$CONT" = "y" ]; then
  sudo python -c "import sys; py3 = sys.version_info[0] >= 3; u = __import__('urllib.request' if py3 else 'urllib', fromlist=1); exec(u.urlopen('http://status.calibre-ebook.com/linux_installer').read()); main()"
  
fi
echo  "this is synaptic close the program to cont"
sudo synaptic

echo "and this is ubuntu-tweak close the program to cont"
sudo ubuntu-tweak

read -p "do you want to see websites for games and problem solving (y/n)?" CONT;
if [ "$CONT" = "y" ]; then
echo "sites for you to bookmark"
firefox http://ubuntuforums.org/ http://www.getdeb.net/welcome/
else
 exit
fi

```

---

### Post by sudodus on 2013-02-20
You can try *_**zenity**_* or ***kdialog*** to make a simple GUI front-end to your script. There are good tutorials about those programs in the internet.

---

### Post by iceman30ad on 2013-02-20
ok ill try that thanks

i see an issue with part of my script  i use the calibre installer instead of the one in the repos it brings up questions in the cli like where do i want to install and if i am sure i want to install how would i go about handling that ?   and if it can not be done it looks like this is sol.

---

### Post by iceman30ad on 2013-02-20
ok i just noticed that my script is kinda broken how do i query the code name of the disto for it to be entered in to my listing and how do i get it in to the listing 
i want this to last Im now on Quantal  but my script is still  Precise i would like it to be self configuring if at all posible and before any one says rtfm i have and it confuses me more than i was before i read it.

---

### Post by sudodus on 2013-02-20
> **iceman30ad said:**
> ok ill try that thanks

i see an issue with part of my script  i use the calibre installer instead of the one in the repos it brings up questions in the cli like where do i want to install and if i am sure i want to install how would i go about handling that ?   and if it can not be done it looks like this is sol.
I guess you could catch that output and feed it to zenity or kdialog.

Finally I want to give you a general piece of advice: Often it takes more time to create a GUI than to create the back-end program itself. I think a good text-based dialogue is often good enough (but I'm an old-timer). So you should consider how much you want to refine your text-based program and where to put the priority (to the program or to its GUI interface) or if you have time for both.

---


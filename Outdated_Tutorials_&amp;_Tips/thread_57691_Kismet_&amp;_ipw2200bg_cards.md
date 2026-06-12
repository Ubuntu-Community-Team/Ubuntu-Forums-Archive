---
title: "Kismet &amp; ipw2200b/g cards"
date: 2005-08-17
forum: Outdated Tutorials &amp; Tips
---

### Post by somuchfortheafter on 2005-08-17
Well this is a tutorial to get kismet working with the ipw2200 card found in most centrino notebooks. 

First off you will need the latest ipw2200 driver which the tutorial on how to get it can be found here:
[http://www.ubuntuforums.org/showthread.php?t=26623&highlight=ipw2200+wpa](http://www.ubuntuforums.org/showthread.php?t=26623&highlight=ipw2200+wpa)
You can stop at the install of wpa supplicant as you dont really need wpa support.

Next you need to install subversion and the libncurses5-dev package so:
```

sudo apt-get install subversion libncurses5-dev

```

Next you will need to get the kismet source from svn so 
```

svn co http://svn.kismetwireless.net/code/trunk kismet-devel

```
After this cd into the kismet directory and run
```

./configure --sysconfdir=/etc/kismet
make dep
make
sudo make install

```
Finally the kismet.conf file must be edited to use the ipw2200 card so 
```

sudo gedit /etc/kismet/kismet.conf

```
Then add the following lines in the source section and comment out the other ones using the # key
```

source=ipw2200,eth0,ATHEROS

```

To test and ensure that the program is working
```

sudo iwconfig eth0 mode monitor && sudo kismet

```

hope this helps everyone :)

---


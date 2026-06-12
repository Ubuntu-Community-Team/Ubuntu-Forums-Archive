---
title: "amarok is breaking my system every time i try to install it"
date: 2012-07-07
forum: New to Ubuntu
---

### Post by totiescone on 2012-07-07
I installed ubuntu 12.04 a few days ago and everything works fine ,except for amarok. Every time i try to install it, it get to about 75% then crashes saying " items cannot be installed or removed until the package catalog is repaired. Do you want to repair it now?" and gives me the option to repair it. So if i select repair it just does nothing and the same message comes up over and over again. i have went into the console and done sudo apt-get -f install , and it tries to remove it but fails, if i change the source it does it ok and removes amarok but not the logo from the desktop sidebar, and everything works fine. But if i try to install amarok again the exact same thing happens. anyone know if this can be fixed or shall i just give up with amarok?

---

### Post by totiescone on 2012-07-07
turns out i can only play mp3 or any other media files using vlc.
if i try the rhythmbox app it says i need additional plugins, gives me the option to install then says they are not available in python (or something). What is going on? can it not just work? why is this being so annoying yet my bro who lives across the road from me installed  ubuntu 12.04 last night on his crappy little laptop and everything works great..... but not for me!!

---

### Post by totiescone on 2012-07-07
now says ubuntu has an internal error. about ready for giving up :( maybe vista aint that bad, at least things work. no answers here anyway

---

### Post by cottfcfan on 2012-07-07
Have you installed the Restricted extras?
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by totiescone on 2012-07-07
yep heres what it says
totiescone@ubuntu:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for totiescone: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ubuntu-restricted-extras

---

### Post by oldsoundguy on 2012-07-07
totiescone, patience!  This forum is about and full of USERS .. not "on line help"  When you post something requesting help, you have to wait until someone clicks on your posting that knows how to fix the problem, or can, at least, offer a suggestion.

As cottfcfan pointed out, installing the restricted extras is the first step towards getting the needed codex files.

---

### Post by totiescone on 2012-07-07
thanks very much sorry for seeming impatient. have done restricted download now, will there be anything else i'll need to do?

---

### Post by cottfcfan on 2012-07-07
OK..
It sounds like you haven't got all the repos enabled.
Go into software sources, and make sure all your ubuntu software sources are ticked.
Then in "other software" make sure canonical partners & independant repos are ticked.
Update everything.
```
sudo apt-get update && sudo apt-get upgrade
```
Then try again.

---

### Post by cottfcfan on 2012-07-07
Just another point Totiescone.
Amarok is a massive app. developed for the KDE environment, and will drag in with it a lot of extras.
IMO Clementine would be a better Media player to use on the Gnome environment.

---

### Post by totiescone on 2012-07-07
no same again as soon as i try to install amarok it says its failed at about 75%.:(
thanks cottfc will try clementine instead after ive done sudo apt-get -f install to get rid of amarok as the software centre breaks and wont remove it.

---

### Post by oldsoundguy on 2012-07-07
I like VLC for the media player.  Even use it in an old Windows box that is my "photo dark room".

---

### Post by totiescone on 2012-07-07
great clementine works! can now play mp3s etc. but still cant get rid of the amarok logo from my desktop sidebar. otherwise thanks very much guys!:p

---

### Post by cottfcfan on 2012-07-07
To get rid of the Icon from the side bar, just Right click the icon & remove.
To remove Amarok completely:
```
sudo apt-get purge --remove amarok
```
then:
```
sudo apt-get autoremove
```

---


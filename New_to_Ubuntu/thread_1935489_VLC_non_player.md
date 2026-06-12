---
title: "VLC non player"
date: 2012-03-04
forum: New to Ubuntu
---

### Post by drivejohn on 2012-03-04
Hi I am an absolute beginner so wont feel an idiot when I ask questions.Have just installed ubuntu 11.10 on an old pc all went well, but will want to play films and have downloaded VLC media player.  Put film in pc puts it on the screen I click on vlc dvd buttons come up click play, vlc regognises the film and goes off, buttons stay on screen but will not play film. any help appreciated

---

### Post by TeoBigusGeekus on 2012-03-04
Start vlc from command line
```
vlc
```
and post us any error messages you get.

---

### Post by winh8r on 2012-03-04
If you press 

control + alt + T 

and open a terminal then copy and paste this command into it and hit enter:


```
sudo apt-get install ubuntu-restricted-extras
```

it will ask for your password then install the package.

you may also need to install this:

```
sudo apt-get install libdvdread4
```

Give these a go and see how it goes.

hope this helps

---

### Post by drivejohn on 2012-03-05
entered 1st link and Stopped at "Configuring ttf-mscorefonts-installer" for 3.5 hrs anything else I need to do

---

### Post by howefield on 2012-03-05
> **drivejohn said:**
> entered 1st link and Stopped at "Configuring ttf-mscorefonts-installer" for 3.5 hrs anything else I need to do

Are you stuck at the licence screen ?

Press tab to highlight the OK button and press enter.

---

### Post by Harry.k on 2012-03-05
Try again. If it still doesnt work, google for restricted extras offline installer. Ps: i would reccomend totem media player. I have a prehistoric pc, and totem works better than vlc                                                         edit: of course, the license agreement.

---

### Post by drivejohn on 2012-03-08
Hi guys.  I have entered the code from win8hr got stuck, then followed help from howefield, but still would not run , followed advise from harry.k and trawled google to find code for css and hey presto it worked. Sorry teobigusgreekus I could not follow your advise as I didn't know where the terminal was, as I said total novice.  Thank you for your help

---


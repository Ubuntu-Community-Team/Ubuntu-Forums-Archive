---
title: "Removing a app installed using checkinstall"
date: 2019-01-24
forum: New to Ubuntu
---

### Post by Lou Reed on 2019-01-24
Is it possible when you have installed a app by compiling from source to use checkinstall to remove it completely?

I know that if you install it using checkinstall instead of make install that this can be done. 

Consider the situation where initially the app is installed by compiling from source.

Now you want to remove it. It is a difficult task. 

But if you go ahead and make a deb file using checkinstall and not install something like this.

sudo checkinstall  --install=no

Then you will have the deb file with with you can use to uninstall the initial  app that you compiled from source in the first place.

Thsos of course assumes that make install and checkinstall --install=no when compiling the app from source both install
the program the same way. If that is not true then this is a wasted exercise. 

Everything keys on that last statement. 

Any help appreciated.


Respectfully,

ErnestTBass

---

### Post by oldrocker99 on 2019-01-24
I compile Aqualung, which disappeared from the repos, and is a gapless music player. I wanted to recompile it for .m4a files, and found the executable and removed it. It worked.

---

### Post by Lou Reed on 2019-01-24
Yes, but my apps files have so much more than just an executable. Take python 3.7.2 for instance.

Respectfully,

ErnestTBass

---

### Post by monkeybrain20122 on 2019-01-24
Checkinstall creates a .deb so you just remove it like you would with other apps installed with a .deb, i.e sudo apt remove packagename. I really recommend getting synaptic to manage your solftware, it is a gui package manager with a lot of features and very easy to use., much better than the Software Centre. You can install it via the SC or sudo apt install synaptic

P.S btw if you are querying about the python3.6.3 that you installed from source sudo apt remove or using synaptic will remove cleanly python3.6.3 but it probably won't remove the modules you installed with pip3 (and pip3 itself) ,--though I am not 100% sure about that so check the folders. For that you have to delete the folders manually, look at /usr/local/lib for the python3.6.3 subfolder and /usr/local/bin for .py that you might have installed this way (or use pip3 to remove the modules first, then remove python3.6.3 with synaptic or apt)

---

### Post by ajgreeny on 2019-01-24
^^^ +1 ^^^

Definitely worth installing synaptic, though I admit, not absolutely necessary, as apt in terminal works very well for packages installed using checkinstall.

Synaptic however, gives you a superb GUI version of everything that the terminal does, and once you have got used to it, is many times better than any of the software store GUI applications; it is the first package I add to any of my *buntu OSs.

---

### Post by oldrocker99 on 2019-01-25
Synaptic does categorize apps, and can really narrow things down with the Quick Filter:
[https://askubuntu.com/questions/763857/how-to-get-quick-filter-back-in-synaptic-ubuntu-16-04-and-later](https://askubuntu.com/questions/763857/how-to-get-quick-filter-back-in-synaptic-ubuntu-16-04-and-later)

---


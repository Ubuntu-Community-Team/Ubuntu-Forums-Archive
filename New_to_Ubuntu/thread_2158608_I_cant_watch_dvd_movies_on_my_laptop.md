---
title: "I cant watch dvd movies on my laptop"
date: 2013-06-29
forum: New to Ubuntu
---

### Post by openation1 on 2013-06-29
Hello everyone..... I installed ubuntu on my laptop and I cant watch movies...... I dont know if theres a software for it or what? please advice me how to do it please I'm a beginner ...... dont know too much about it thank you so much......

---

### Post by squakie on 2013-06-29
You first need to install the package libdvdread4 (I think that's the current).  Once that finishes, there is another step involved in installing a package to get around the encryption of commercial DVD's.  That is not legal in all countries, so I don't know if we're allowed to post publically what it is.  You can Private Message me for more information if you'd like.  I should respond by Sunday night (it's a busy weekend here).

---

### Post by oldos2er on 2013-06-29
```
sudo apt-get update && sudo apt-get install libdvdread4

sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by squakie on 2013-06-29
I guess it's ok to post the install script ;)

---

### Post by newb85 on 2013-06-30
The first command installs the libraries for reading DVDs, which are included in the repositories.

The second command runs a script that downloads (from a source outside the repositories) and installs software for descrambling commercial DVDs (i.e., movie DVDs). The descrambling software can't be included in the repos because it's deemed illegal to distribute without proper license in some countries.  (This is why squakie wasn't sure we could post the script.)  In fact, Windows doesn't even come with the descrambling software, but computer manufactures that pre-install Windows obtain the license and install it for the users' convenience.  (This info comes from Windows' own support site.)

---

### Post by oldos2er on 2013-06-30
It's been posted hundreds if not thousands of times before, so yes.

Edit: In Software Center you can purchase a license (if you need to) for Fluendo DVD Player, which contains full commercial DVD playback capability: [https://apps.ubuntu.com/cat/applications/fluendo-dvd/](https://apps.ubuntu.com/cat/applications/fluendo-dvd/)

---


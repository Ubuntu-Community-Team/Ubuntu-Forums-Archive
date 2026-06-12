---
title: "How Do I Shut Down Linux with a Command Line"
date: 2013-08-04
forum: New to Ubuntu
---

### Post by GUZZLR on 2013-08-04
Hello All,
What is a command line that I can shut down Linux/computer, with out having to get to the top right and shut down normally?
Thanks

---

### Post by ibjsb4 on 2013-08-04
Looks like the first link has the answer.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=How+Do+I+Shut+Down+Linux+with+a+Command+&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=How+Do+I+Shut+Down+Linux+with+a+Command+&sa=Search&cof=FORID:9)

---

### Post by oldos2er on 2013-08-04
```
sudo shutdown -h now
``` ```
man shutdown
``` for more info.

---

### Post by GUZZLR on 2013-08-06
Thank you everybody...dont know why 13.04 just decides to hang-up on me and stop working, with no apparent reason

---

### Post by wealthy2 on 2013-08-06
> **GUZZLR said:**
> Hello All,
What is a command line that I can shut down Linux/computer, with out having to get to the top right and shut down normally?
Thanks
```
init 0
```
And to reboot:
```
init 6
```

---

### Post by kevdog on 2013-08-07
init 0 and init 6 (which have to be run with sudo) are a hold over for sysV init scripts correct? I believe they still work in Ubuntu, however I don't think they are going to work on other distro's that use Systemd like arch and Fedora or android for that matter.  Yes I know this is probably more information than you wanted to know, however there are other methods out there -- here's a reference for a broad overview: [https://www.linux.com/learn/tutorials/524577-here-we-go-again-another-linux-init-intro-to-systemd](https://www.linux.com/learn/tutorials/524577-here-we-go-again-another-linux-init-intro-to-systemd).   Really what you need to know is that successor to system V init scripts are either upstart (which was written solely by Ubuntu developers) and systemd which was written by Leonard Poettering (Fedora).  I don't remember the story, but there was a falling out between Poettering and the Ubuntu developers -- some say it was do to copyright policies that Ubuntu imposes on its developers when contributing to upstart, some say it involves other things as well.  Poettering and others wrote systemd as an advancement "as he would call it" or alternative to upstart.  Needless to say Ubuntu remains with upstart, whereas many other distributions have moved onto systemd.  Ubuntu at the present time looks like it will never move to systemd, however who knows what the future will bring.

---

### Post by nerdtron on 2013-08-07
Shutdown ubuntu using command line?

sudo poweroff   --> poweroff
sudo reboot      --> reboot

Simple enough. :)

---


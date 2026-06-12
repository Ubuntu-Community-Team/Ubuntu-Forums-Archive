---
title: "Matlab"
date: 2007-05-11
forum: Programming Talk
---

### Post by Zacharias on 2007-05-11
Hi guys,

is there any chance to install matlab to my fiesty?

---

### Post by kebes on 2007-05-11
According to the Wine application database, many versions of Matlab run quite well using wine:
[http://appdb.winehq.org/appview.php?iAppId=49](http://appdb.winehq.org/appview.php?iAppId=49)

(If you don't know what WINE is, it is a windows-compatibility layer for Linux. You can find instructions for adding it to Ubuntu [here]("http://www.winehq.org/site/download-deb").)


Another option, depending on your needs, is to install [Octave]("http://www.gnu.org/software/octave/"), which is a free and open-source Matlab-like environment. Many (but not all) Matlab programs will run in Octave without modification.



Hope that helps.

---

### Post by Zacharias on 2007-05-11
how can i install the octave to my fiesty ?

---

### Post by cyberslayer on 2007-05-11
You can install Matlab on linux.  There is a thread somewhere on the forums on how to do it that I used when I installed Matlab.

Type
```
sudo apt-get install octave
```
 to install octave

---

### Post by kebes on 2007-05-11
If you like using the commandline, you can go:
```

sudo aptitude install octave

```

(You may also want to install the "koctave" program, which provides a graphic interface to Octave.)


If you want to install it the GUI way, you can go Applications > Add/Remove, then do a search for the Octave package. (Or use the Synaptic package manager, which is under System > Administration > Synaptic Package Manager.)

---

### Post by xtacocorex on 2007-05-11
Matlab does have a Linux version, well at least it used to.  Scilab is also another program quite similar to Matlab and has a Simulink clone which runs pretty much the same.

---

### Post by Hairy_Palms on 2007-05-11
matlab still has a linux version
[http://www.mathworks.com/support/sysreq/current_release/linux.html](http://www.mathworks.com/support/sysreq/current_release/linux.html)

---

### Post by tjansson on 2007-05-11
I am running matlab on Linux with the native Linux installer - which is quite easy to use.

---

### Post by Krokido on 2007-11-04
To find installation help for matlab under ubuntu, I typed 'install matlab ubuntu' in google and got the following link [https://help.ubuntu.com/community/MATLAB](https://help.ubuntu.com/community/MATLAB).

Tells you anything you need to know

---


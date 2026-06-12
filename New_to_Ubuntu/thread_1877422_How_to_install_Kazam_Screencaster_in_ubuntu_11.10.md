---
title: "How to install Kazam Screencaster in ubuntu 11.10"
date: 2011-11-08
forum: New to Ubuntu
---

### Post by anandharaja on 2011-11-08
hi,
i try to install kazam screen caster but i got the following error.
how can i resolve that error?


> 
The following packages have unmet dependencies:

kazam: Depends: python-central (>= 0.6.11) but 0.6.17 is to be installed
       Depends: libx264-106 but it is not going to be installed
       Depends: libmatroska3 but it is not going to be installed
       Depends: libavdevice-extra-52 but it is not going to be installed
       Depends: libavcodec-extra-52 but it is not going to be installed

---

### Post by satanselbow on 2011-11-08
How are you installing in? From the ppa?

There seem to be a few deps that have been updated in the repos but not in the kazam install script - but you can still get it up and running ;)

This is how I got it up on 11.10 on Gnome-Shell

```
sudo apt-get install bzr python-rsvg python-keybinder python-xlib

bzr branch lp:kazam/stable

cd stable/bin
sudo ./kazam

```

---

### Post by beew on 2011-11-08
Don't understand the python requirement. 0.6.17 is >= 0.6.11, no?
For the second and third requirements see this
[http://thewebit.com/install-kazam-ubuntu-11-04/](http://thewebit.com/install-kazam-ubuntu-11-04/)
for the last 2 you need to activate the medibuntu ppa
[http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1656-how-to-add-medibuntu-repository-in-ubuntu-via-terminal-and-gui](http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1656-how-to-add-medibuntu-repository-in-ubuntu-via-terminal-and-gui)

---

### Post by anandharaja on 2011-12-28
hi, 
just now installed Kazam from this ppa "ppa:bigwhale/kazam-oneric" but capturing the selected region is not available. Unstable release have that feature?

---

### Post by anandharaja on 2012-01-02
hi,
Today i installed kazam 0.13 from this ppa "ppa:kazam-team/unstable-series" after that kazam not opening.what is the problem?

---


---
title: "mplayer will not install trying to run a-desk"
date: 2011-12-15
forum: New to Ubuntu
---

### Post by fattyz on 2011-12-15
Here I am again not being able to remember how I did this, Im glad I got off THAT stuff damn!

Anyway I want to run a-desk which is a script that animates the wallpaper and I have it installed but it won't load, (even though it seems like it is)  I remember this kind of but last time I resolved it by installing xwinwrapper.  It seems this is not the case this time so google searches got me to thinking I needed to install mplayer (even though I have VLC installed and it works)

Do I really have to do this?  Is this a multiverse issue?  I can't see anything wrong with my repositories.

The following packages have unmet dependencies:
  devede: Depends: mencoder but it is not going to be installed
          Depends: mplayer but it is not going to be installed
          Depends: libavcodec-extra-52 but it is not going to be installed
          Depends: libavformat-extra-52 but it is not going to be installed
  mandvd: Depends: dvd-slideshow but it is not going to be installed
          Depends: mencoder but it is not going to be installed
          Depends: mplayer but it is not going to be installed or
                   mplayer-nogui but it is not going to be installed
E: Broken packages
mark@mark-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mark@mark-laptop:~$ sudo apt-get install mplayer
[sudo] password for mark: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer: Depends: libavcodec52 (>= 4:0.6-1~) but it is not going to be installed or
                    libavcodec-extra-52 (>= 4:0.6-1~) but it is not going to be installed
           Depends: libavformat52 (>= 4:0.6-1~) but it is not going to be installed or
                    libavformat-extra-52 (>= 4:0.6-1~) but it is not going to be installed
           Depends: libcaca0 (>= 0.99.beta17-1) but 0.99.beta16-3 is to be installed
           Depends: libdirectfb-1.2-9 but it is not installable
           Depends: libjack-jackd2-0 (>= 1.9.5~dfsg-14) but it is not installable or
                    libjack-0.116 but it is not installable
           Depends: libncurses5 (>= 5.7+20100313) but 5.7+20090803-2ubuntu3 is to be installed
           Depends: libx264-98 but it is not installable
E: Broken packages

Anyone who has this beat I'd appreciate a hand.

Thanks

---


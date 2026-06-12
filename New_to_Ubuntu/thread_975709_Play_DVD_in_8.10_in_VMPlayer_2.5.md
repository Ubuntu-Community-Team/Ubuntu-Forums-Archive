---
title: "Play DVD in 8.10 in VMPlayer 2.5"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by davidr63 on 2008-11-08
Not able to play DVD.  I can hear the audio but no video.

System:
* VMware Player 2.5 build-118166
* Host system is Windows XP SP 3
* Ubuntu 8.10 (got it as a virtual appliance from [http://chrysaor.info/?page=ubuntu](http://chrysaor.info/?page=ubuntu)) Desktop VMware image

I have gone through many forums and websites listing libdvd this and that.  I have tried mplayer, vlc, totem (with all the plugins I could select), and gxine.  I am pretty sure I have the medibuntu packages installed, though I may be wrong on that.  The root issue I believe is that Ubuntu always mounts the DVD in /cdrom and /media/cdrom whereas I have seen that it should be /media/dvd.  Is this the problem? And if so how do I resolve it besides linking /media/dvd to /media/cdrom?  I have also tried to see if there was a setting I could change in the VMX file to say my drive is a DVD drive rather then using ´atapi-cdrom´ or ´cdrom-raw´ for that ide device.

Thank you for your patience while this long time Windows user tries to adjust to the linux way of things.

David

---

### Post by pgorillaman on 2008-11-08
First make sure the decryption libraries are installed.
```
sudo apt-get install libdvdnav4 libdvdplay0 libdvdread3 libdvdcss2
```

---

### Post by pgorillaman on 2008-11-08
Also, what player are you using?

---

### Post by cariboo on 2008-11-08
If you can't play a dvd in linux, you are not going to be able to play dvds in a vm. Windows XP won't play dvd's natively and legally, with out adding a for pay codec from Microsoft or buying dvd player software.

Linux will play dvds, but  depending on where you live you may not be able to play them legally. The only thing I ever have to do is download unbunut-restricted-extras and enable the Medibuntu repositories and install libdvdcss2. I've never had a dvd that wouldn't play after doing the above. Sometimes you may have to tell vlc where you dvd drive is, usually /dev/scd0

Jim

---

### Post by davidr63 on 2008-11-10
pgorillaman,

Players I have tried:

GNOME MPlayer
gxine
Movie Player (totem)
VLC
Ogle

None of them work right, if anything I only get the audio.  The DVD works just fine in Windows.  Could fact that when I put the DVD in it always shows up mounted to /media/cdrom instead of /media/dvd be causing the issue?  

Also, I tried to install that list of packages you said.  I did them each individually.  I already had all of them (xxxx is already the newest version) except for libdvdplay0, which gave me the following:

user@ubuntu810desktop:~$ sudo apt-get install libdvdplay0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libdvdplay0

I ran apt-get against all of them and libdvdplay0 is the only one that gave me issues, maybe I need to enable a different repo? Thank you very much for your assistance pgorillaman.

---

### Post by sambita on 2008-12-06
I dont know if you still have this problem, but just in case...
I was having the same issues and stumbled upon your thread, i found libdvdplay0

[http://packages.ubuntu.com/dapper/libs/libdvdplay0]("http://packages.ubuntu.com/dapper/libs/libdvdplay0")

Its for dapper but i guess it doesnt matter, i had no problem installing it. 

Im still unable to play dvd menus on totem, but installed vlc from the repos and that did the trick. 

good luck!

---


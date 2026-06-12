---
title: "30 seconds into using ubuntu and it's already broken!"
date: 2021-10-01
forum: New to Ubuntu
---

### Post by thunderchild2 on 2021-10-01
why can't I post a THREAD?

---

### Post by ActionParsnip on 2021-10-01
You did and have. What is the issue?

---

### Post by T6&amp;sfpER35% on 2021-10-01
what does it say when you try to?

---

### Post by T6&amp;sfpER35% on 2021-10-01
> [COLOR=#000000]You did and have. What is the issue?[/COLOR]
just realized that ...
:lolflag:

---

### Post by thunderchild2 on 2021-10-01
As soon as i installed ubuntu it asked if I wanted to check for updates.  I said yes, it went wrong and now every time I try to install something  I get told something is broken and I should run: 'sudo apt --fix-broken  install'

I do and get:

```

simon@simon-ubuntu:~$ sudo apt --fix-broken install
[sudo] password for simon: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  chromium-codecs-ffmpeg-extra gstreamer1.0-vaapi libgstreamer-plugins-bad1.0-0 libva-wayland2
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  samba-libs
The following packages will be upgraded:
  samba-libs
1 to upgrade, 0 to newly install, 0 to remove and 9 not to upgrade.
2 not fully installed or removed.
Need to get 0 B/5,264 kB of archives.
After this operation, 4,096 B disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 186906 files and directories currently installed.)
Preparing to unpack .../samba-libs_2%3a4.11.6+dfsg-0ubuntu1.10_amd64.deb ...
Unpacking samba-libs:amd64 (2:4.11.6+dfsg-0ubuntu1.10) over (2:4.11.6+dfsg-0ubuntu1.9) ...
dpkg-deb (subprocess): decompressing archive member: lzma error: compressed data is corrupt
dpkg-deb: error: <decompress> subprocess returned error exit status 2
dpkg: error processing archive /var/cache/apt/archives/samba-libs_2%3a4.11.6+dfsg-0ubuntu1.10_amd64.deb (--unpack):
 cannot  copy extracted data for  './usr/lib/x86_64-linux-gnu/samba/libndr-samba4.so.0' to  '/usr/lib/x86_64-linux-gnu/samba/libndr-samba4.so.0.dpkg-new':  unexpected end of file or stream
Errors were encountered while processing:
 /var/cache/apt/archives/samba-libs_2%3a4.11.6+dfsg-0ubuntu1.10_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


so  I'm buggered. Why can't this problem just be taken care of, the net is  full of this but nothing suggested works. I can't edit system files.  Does Ubuntu work?

---

### Post by thunderchild2 on 2021-10-01
> **ActionParsnip said:**
> You did and have. What is the issue?

i wrote it all out and got an error telling me I did not have permission, so I just dumped that filler text in having lost what I wrote. I have now rewritten it.

---

### Post by thunderchild2 on 2021-10-01
I tried to edit my first message but apparently I had not entered a message of at least one character,??????

---

### Post by Impavidus on 2021-10-01
> dpkg-deb (subprocess): decompressing archive member: lzma error: compressed data is corruptSomehow, the archive containing the upgrade was corrupted. Try deleting it and redownloading:```
sudo apt clean
sudo apt update
sudo apt install -f
```
> I can't edit system filesThat's normal security. See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
> Does Ubuntu work?I have been a happy Ubuntu user for 15 years. It's the only system I use. It broke maybe 3 times.

---

### Post by thunderchild2 on 2021-10-01
I'll give it a go, thing is I just want an operating system, I don't want to have to keep fixing things. You know, like I drive a car but I am not a mechanic, so:

```

simon@simon-ubuntu:~$ sudo apt clean
[sudo] password for simon: 
simon@simon-ubuntu:~$ sudo apt clean
simon@simon-ubuntu:~$ sudo apt update
Hit:1 [http://ppa.launchpad.net/kicad/kicad-5.1-releases/ubuntu](http://ppa.launchpad.net/kicad/kicad-5.1-releases/ubuntu) focal InRelease
Hit:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal InRelease                      
Get:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal-updates InRelease [114 kB]     
Hit:4 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal InRelease                      
Get:5 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal-backports InRelease [101 kB]   
Get:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease [114 kB]      
Fetched 328 kB in 1s (407 kB/s)    
Reading package lists... Done
Building dependency tree       
Reading state information... Done
10 packages can be upgraded. Run 'apt list --upgradable' to see them.
simon@simon-ubuntu:~$ sudo apt install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  chromium-codecs-ffmpeg-extra gstreamer1.0-vaapi
  libgstreamer-plugins-bad1.0-0 libva-wayland2
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  samba-libs
The following packages will be upgraded:
  samba-libs
1 to upgrade, 0 to newly install, 0 to remove and 9 not to upgrade.
28 not fully installed or removed.
Need to get 5,264 kB of archives.
After this operation, 4,096 B disk space will be freed.
Do you want to continue? [Y/n] y
Get:1 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal-updates/main amd64 samba-libs amd64 2:4.11.6+dfsg-0ubuntu1.10 [5,264 kB]
Fetched 5,264 kB in 2s (2,456 kB/s)     
(Reading database ... 214089 files and directories currently installed.)
Preparing to unpack .../samba-libs_2%3a4.11.6+dfsg-0ubuntu1.10_amd64.deb ...
Unpacking samba-libs:amd64 (2:4.11.6+dfsg-0ubuntu1.10) over (2:4.11.6+dfsg-0ubun
tu1.9) ...
Setting up kicad-footprints (5.1.10-202104251634+302ac78ba~10~ubuntu20.04.1) ...
Setting up libjxr0:amd64 (1.1-6build1) ...
Setting up kicad-packages3d (5.1.10-202104261003+7abe02f3~7~ubuntu20.04.1) ...
Setting up xsltproc (1.1.34-4) ...
Setting up libtbb2:amd64 (2020.1-2) ...
Setting up samba-libs:amd64 (2:4.11.6+dfsg-0ubuntu1.10) ...
Setting up kicad-demos (5.1.10-202107120859+88a1d61d58~90~ubuntu20.04.1) ...
Setting up libngspice0:amd64 (31.3-2) ...
Setting up libilmbase24:amd64 (2.3.0-6build1) ...
Setting up libopenexr24:amd64 (2.3.0-6ubuntu0.5) ...
Setting up kicad-templates (5.1.10-202104251636+1ccbaf3~8~ubuntu20.04.1) ...
Setting up kicad-symbols (5.1.10-202104251637+6dec5004~6~ubuntu20.04.1) ...
Setting up kicad-doc-en (5.1.10-202104281228+1688~28~ubuntu20.04.1) ...
Setting up libsmbclient:amd64 (2:4.11.6+dfsg-0ubuntu1.10) ...
Setting up kicad-libraries (5.1.10-202104251635+7~ubuntu20.04.1) ...
Setting up libglew2.1:amd64 (2.1.0-4) ...
Setting up libwxbase3.0-0v5:amd64 (3.0.4+dfsg-15build1) ...
Setting up python3-sip (4.19.21+dfsg-1build1) ...
Setting up libfreeimage3:amd64 (3.18.0+ds2-1ubuntu3) ...
Setting up gnome-control-center (1:3.36.5-0ubuntu3) ...
Setting up libocct-foundation-7.3:amd64 (7.3.3+dfsg1-1build1) ...
Setting up libwxgtk3.0-gtk3-0v5:amd64 (3.0.4+dfsg-15build1) ...
Setting up libocct-modeling-data-7.3:amd64 (7.3.3+dfsg1-1build1) ...
Setting up python3-wxgtk4.0 (4.0.7+dfsg-2build1) ...
Setting up libocct-modeling-algorithms-7.3:amd64 (7.3.3+dfsg1-1build1) ...
Setting up libocct-visualization-7.3:amd64 (7.3.3+dfsg1-1build1) ...
Setting up libocct-ocaf-7.3:amd64 (7.3.3+dfsg1-1build1) ...
Setting up libocct-data-exchange-7.3:amd64 (7.3.3+dfsg1-1build1) ...
Setting up kicad (5.1.10-202107120859+88a1d61d58~90~ubuntu20.04.1) ...
Processing triggers for mime-support (3.64ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu1) ...
Processing triggers for libc-bin (2.31-0ubuntu9.2) ...
Processing triggers for man-db (2.9.1-1) ...
Processing triggers for shared-mime-info (1.15-1) ...
Processing triggers for desktop-file-utils (0.24-1ubuntu3) ...
simon@simon-ubuntu:~$
```

---

### Post by thunderchild2 on 2021-10-01
So, next problem: I select "power off" and the system restarts instead.

---

### Post by QIII on 2021-10-01
> 
Does Ubuntu work?


No.  We are all actually Windows users putting on a hoax.

Please ask for support with only one issue per thread.  Start a new on for your power off issue.  Things get confusing quickly if everyone tries to help with a laundry list of issues.

---

### Post by Skaperen on 2021-10-01
it looks like you have much of the file space shared from some Windows server and many are getting corrupted while writing them there or while reading them back.  which is happening doesn't really matter.  i'm not sure how best to resolve the issue and so i suggest installing all over, again, and this time put all system file space on the local hard drive.

it is possible to run Ubuntu hosted from a Windows server, even network booted from it.  but there are a couple programs to install and run (as system programs with Administrator access) there and i don't know anything about it.  were you trying to do this with a no-disk machine?

---

### Post by yancek on 2021-10-02
> Does Ubuntu work? 

You should be embarrassed to even be asking a question like that.  There are tens of millions of Ubuntu users in many different countries and have been for over a decade..

Did you run all the commands suggested in your attempt to install?  The output shows you have a number of ppa's already installed, none of which are there on a default install.  Your problem seems to be with trying to install samba to interact over a network with windows which indicates that the title to your thread is 'a gross exaggeration.  Have you resolved your Samba install problem?  If so, as suggested above, post another thread about the start/restart problem.

Another suggestion so you understand, the members here are not making millions from Ubuntu but are all volunteers trying to help other people so coming here and posting a whining, complaining thread isn't going to interest people in trying to help you or anyone else with a similare attitude.

Good luck.

---

### Post by grahammechanical on 2021-10-02
> posting a whining, complaining thread isn't going to interest people in  trying to help you or anyone else with a similar attitude.

That is the exact reason why I decided not to suggest any kind of help solutions in this thread.

In the past I received First Aid training. I remember one training session. We were told to imagine coming upon the scene of a vehicle accident. In the front seat of the vehicle one person is sitting there, silent and still. Another person has got out the vehicle and is walking up and down shouting & interfering with first responders. Which of the two people is about to die? The noisy person is not hurt badly. Otherwise they would not be so noisy and agitated. The silent one could be quietly bleeding to death. The lesson? Ignore the noisy people and help the still and silent ones for they are the ones most in need of help.

Regards

---

### Post by T6&amp;sfpER35% on 2021-10-04
i'm always trying to be as silent as a turkey the day before thanksgiving
:P

---


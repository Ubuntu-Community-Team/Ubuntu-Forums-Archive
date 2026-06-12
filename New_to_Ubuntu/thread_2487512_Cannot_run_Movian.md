---
title: "Cannot run Movian"
date: 2023-06-07
forum: New to Ubuntu
---

### Post by loguey on 2023-06-07
Hi all,

I am trying to run Movian, but when I click on the Movian icon, nothing happens. So I have tried to run it from the command line and get the following error message:

> user@mypc:~$ movian
/snap/movian/2/bin/movian: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.34' not found (required by /var/lib/snapd/lib/gl/libGLdispatch.so.0)
/snap/movian/2/bin/movian: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.34' not found (required by /var/lib/snapd/lib/gl/libGLX.so.0)

I know I have GLIBC_2.35 installed. I did try the Movian support page but cannot create an account there.

Best regards

Richard

---

### Post by aikoo7 on 2023-06-11
Hi, loguey, I hope I can help you with you problem.

Can you try install the moviam with the snapd store?

Here the commands:

sudo apt update
sudo apt install snapd
sudo snap install movian --edge

If you don't want or it dont work you can try installing GLIBC_2.34 with the following commands:

# Build GLIBC_2.34 from sources
sudo apt-get install gawk bison -y
wget -c [https://ftp.gnu.org/gnu/glibc/glibc-2.34.tar.gz](https://ftp.gnu.org/gnu/glibc/glibc-2.34.tar.gz)
tar -zxvf glibc-2.34.tar.gz && cd glibc-2.34
mkdir glibc-build && cd glibc-build
../configure --prefix=/opt/glibc-2.34
make 
sudo make install

If you done the snapd installation you can remove the snapd store when finished using the following commands:

sudo apt remove snapd

--------------------------------------------------------

Keep me updated in your situation, welcome to the Ubuntu/the forum if you are new to any and be free to ask me anything.

Regards,
Aiko.

---

### Post by loguey on 2023-06-12
Thanks so much for your help. I successfully installed glibc-2.34 however despite reinstalling Movian from Snap afterwards I still get the same error message!

---

### Post by Holger_Gehrke on 2023-06-12
snaps are constrained through app-armor and therefore can't access anything not in the snap itself, other snaps connected through the slot and plug mechanism, or things in the $HOME of the user running the snap. So installing the library won't help since the snap can't see it. Since the snap doesn't contain the library and it isn't in the core-* snaps, you're going to have a hard time getting this to run.

The snap is in the 'edge'-channel. That usually means it's an experimental build not meant for general use. It's been that way for five years. No changes on the github ([https://github.com/andoma/movian](https://github.com/andoma/movian)) for just as long. There have been no new postings on movian.tv for even longer. So unless I'm missing something, this is probably a dead project.

Holger

---

### Post by aikoo7 on 2023-06-12
Hi Holger_Gehrke, my bad for the misunderstood and thanks for your clarification, please be aware this is my first time here.

--------------------------------------------------------

Keep me updated in your situation, welcome to the Ubuntu/the forum if you are new to any and be free to ask me anything.

Hope I helped you.

Regards, Aiko.

---

### Post by loguey on 2023-06-12
Thanks guys. It's clear that Movian is a dead duck, I have been playing with MPV and I find the picture quality is excellent for my tvheadend server. The user interface...not so! But I am now experimenting with Kodi and trying to integrate the MPV player into it.

---

### Post by tea for one on 2023-06-13
Are you looking for media centre software to use independently of Ubuntu?
e.g. [https://libreelec.tv/](https://libreelec.tv/)

Or to add media centre software to Ubuntu?
e.g. you can create a TV channel Playlist from tvheadend and use in VLC.
VLC is available in the Universe repository.

Alternatively, Kaffeine (also in the Universe repository) can be used for DVB TV and other media.

Just offering suggestions if you want to try a different route.

---


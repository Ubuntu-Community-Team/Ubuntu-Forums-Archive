---
title: "Cannot watch dvd's/movies from the library."
date: 2013-08-29
forum: New to Ubuntu
---

### Post by tom_barnes on 2013-08-29
I am a noobie.  I have been using Windows for most of my computing life, but recently jumped into Linux with both feet.

I checked out some cool  dvd's from the library that I have not been able to watch. The dvd's won't play. Error message states:

"Could not read dvd. This may be because the dvd is encrypted and a dvd decryption library is not installed."

I searched for my issue in the search box and tried some solutions that were mentioned.

So far nothing has worked.

I am using ubuntu 12.04 LTS which I downloaded as an ISO, burned to a disc, and then installed. It is the only OS on my computer.

Computer is dell laptop inspiron 1585. 320  gb hdd, 4gb ram.

Search Instructions have said to go to Dash>enter into the terminal: 
"sudo /usr/share/doc/libdvdread4/install-css.sh"

I do this and hit "enter."

Nothing seems to happen, or I don't know what to look for.

[Is the dash terminal the same as the command-line????]

Other instructions have said to open the software center>type "ubuntu restricted extras" into search box, and then hit "enter." I started downloading the "restricted areas" addition. During the installation process a dialogue box opened up that stated, "to install ubuntu restricted extras, these items must be removed, 
--libav codec library, libav codec 53
--libav utility library, libavutil 51."

I clicked the area that stated "install anyway."

After restarting the computer a couple of times, I still wasn't able to watch these dvd's.

So here I am  asking for help. Any help that can be offered will be appreciated.

Thanks.

---

### Post by Dennis N on 2013-08-29
> **tom_barnes said:**
> 
Search Instructions have said to go to Dash>enter into the terminal: 
"sudo /usr/share/doc/libdvdread4/install-css.sh"

I do this and hit "enter."

Nothing seems to happen, or I don't know what to look for.

[Is the dash terminal the same as the command-line????]

If you type "terminal" into the Dash search box, it should come up in the Dash. Start the terminal by left click on the icon. After entering the command in the terminal window, hit enter, you should be asked for your user password (the one you log in with), type it in (you won't see what you type!) hit enter again, and the installation should proceed.

---

### Post by squakie on 2013-08-30
+1.  I *think* libdvdread4 is installed by default now, but if not you'll need to install it before you can do the above to install the css decoding.

---

### Post by tom_barnes on 2013-08-30
Thank You dennis n for your help.:D
The problem is solved.:D

Thank You for taking the time to help me.:D
Thank You Squakie.:D

---

### Post by xdecalmanx on 2013-10-10
new to ubuntu.  i've been searching for a way to play dvds and nothing seems to work.  running ubuntu 12.04 lts.

---

### Post by 3rdalbum on 2013-10-11
> **xdecalmanx said:**
> new to ubuntu.  i've been searching for a way to play dvds and nothing seems to work.  running ubuntu 12.04 lts.

You didn't say what you had actually tried, so we might be going over old ground here.

Press Control-Alt-T (it opens the terminal). Type or copy-paste the following:

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

Press Enter. Type your password (it won't be displayed) and hit Enter.

While that command is running, or after it finishes, install VLC from the Ubuntu Software Center and you will be able to play DVDs in VLC. I find I can't use the built-in Totem Movie Player for DVDs so I use VLC instead, which always works.

If this doesn't work, let us know and tell us what error messages or symptoms you get, and what things you've tried, and someone might be able to help.

---

### Post by xdecalmanx on 2013-10-11
thanks for the quick reply.  this is what a i got

--2013-10-11 16:14:23--  [http://packages.medibuntu.org/dists/precise/free/binary-i386/Packages](http://packages.medibuntu.org/dists/precise/free/binary-i386/Packages)
Resolving packages.medibuntu.org (packages.medibuntu.org)... failed: Name or service not known.
wget: unable to resolve host address `packages.medibuntu.org'
Dynamic fetch failed; Falling back to static fetch
--2013-10-11 16:14:24--  [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_i386.deb)
Resolving packages.medibuntu.org (packages.medibuntu.org)... failed: Name or service not known.
wget: unable to resolve host address `packages.medibuntu.org'

---

### Post by Otto-C on 2013-10-13
Medibuntu has ceased.
Check below link for installing libdvdcss to play your dvd's.
Also doing a regular update libdvdcss may be installed.
[https://blogs.kde.org/2013/09/11/medibuntu-disappear-libdvdcss-now-direct-videolan](https://blogs.kde.org/2013/09/11/medibuntu-disappear-libdvdcss-now-direct-videolan)

---

### Post by xdecalmanx on 2013-10-13
> **Otto-C said:**
> Medibuntu has ceased.
Check below link for installing libdvdcss to play your dvd's.
Also doing a regular update libdvdcss may be installed.
[https://blogs.kde.org/2013/09/11/medibuntu-disappear-libdvdcss-now-direct-videolan](https://blogs.kde.org/2013/09/11/medibuntu-disappear-libdvdcss-now-direct-videolan)

did 

```
   [INDENT]sudo gksu gedit /etc/apt/sources.list
[/INDENT]
```

added at the end

```
   deb http://download.videolan.org/pub/debian/stable/ /
 deb-src http://download.videolan.org/pub/debian/stable/ /
 
```

still didnt work in VLC media player

thanks in advance

---


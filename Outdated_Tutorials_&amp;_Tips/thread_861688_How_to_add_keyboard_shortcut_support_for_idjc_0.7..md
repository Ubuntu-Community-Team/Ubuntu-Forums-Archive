---
title: "How to: add keyboard shortcut support for idjc 0.7.8a"
date: 2008-07-16
forum: Outdated Tutorials &amp; Tips
---

### Post by dionisis on 2008-07-16
If you have used [Internet DJ Console]("http://www.onlymeok.nildram.co.uk/") you might have found out that the keyboard shortcut support is minimal and not global/widespread. I like using idjc, but I have having to press all those buttons using my mouse, so I created a new python module to make idjc to handle keyboard shortcuts globally. In this guide I will explain step by step how to get the latest idjc code, add the keyboard handling code, compile them and have idjc understanding keyboard shortcuts.

Here are the steps you need to follow in detail:

Step 1) Open a terminal window. It's under Applications->Accessories in the top left corner of the screen.

Step 2) Install necessary dependencies (copy and paste the following into the console window):
```

sudo apt-get install libc6-dev libjack-dev jackd libvorbis-dev libsamplerate0-dev libsndfile1-dev python-gtk2-dev libshout3-dev libmad0-dev libavcodec-dev libavformat-dev liblame-dev libfaad-dev libmp4v2-dev flac vorbis-tools python-eyed3
```
If you are using a 64 bit Ubuntu add **libc6-dev-i386** to the list.

Step 3) Grab a copy of IDJC:
```

wget http://web.bethere.co.uk/idjc/download/idjc-0.7.8a.tar.gz

```

Step 4) Extract it:
```

tar xzvf idjc-0.7.6.tar.gz

```

Step 5) Compile and install:
```

cd idjc-0.7.8a
./configure
make
sudo make install

```

Step 6) Download a copy of the keyboard shortcuts module:
```

wget http://dionisis.freehostia.com/zips/idjcKeyboardShortcuts_v0.1.tar.gz

```

Step 7) Extract it:
```

tar xzvf idjcKeyboardShortcuts_v0.1.tar.gz

```

Step 8) Run the script to add keyboard handling to idjc
```

chmod +x patchidjc
./patchidjc

```

Step 9) Post configuration:
```

echo "/usr/bin/jackd -d alsa -r 44100 -p 2048" > ~/.jackdrc

```

Notes:
The keyboard handling is in a very early stage. The shortcuts used are read from a file that exists in the .idjc folder of the user. If you need to change the shortcuts you have to do it by editing the file directly. In the near future I will create a small GUI tool that will help you do that.
IDJC 0.7.8a has some keyboard shortcuts already. Some of the shortcuts set up by default in the keysAssigned file clash with the shortcuts already in place, e.g. m key is used to turn the mic on/off. If the focus of the application is on any of the two lists of the players, then the microphone turns momentarely on and then off. This is because keypress m is handled twice, once from the existing idjc code and one from the new keyhandling routine. I hope to fix these problems in future versions.

[SIZE="1"]Parts of this post were taken from the post of StephenF at [http://ubuntuforums.org/showpost.php?p=5200135&postcount=5](http://ubuntuforums.org/showpost.php?p=5200135&postcount=5) and my blog at [http://dionisis.blogspot.com/2008/07/keyboard-shortcuts-for-idjc.html](http://dionisis.blogspot.com/2008/07/keyboard-shortcuts-for-idjc.html)[/SIZE]

---


---
title: "can i install a newer version of mplayer"
date: 2012-04-27
forum: New to Ubuntu
---

### Post by klqd on 2012-04-27
than through sudo apt-get mplayer?


i am using a flashcard program called anki and the sound's not working perfectly -sometimes it doesn't play when it should. it says

> **Anki repeats audio from previous cards!**

 Ubuntu’s mplayer package has a buggy implementation of slave mode. Install the latest version of mplayer by following these instructions: [http://ubuntuforums.org/showthread.php?t=1081070](http://ubuntuforums.org/showthread.php?t=1081070)

 
  **The last part of my audio files are not being played!**

 Anki uses mplayer to play audio files. The default mp3 player uses libmad, which has troubles with some audio files. To use a different encoder, edit ~/.mplayer/config and add a line:

 ac=mp3,

 If you’re on Windows, you’ll probably find the file in the \Program Files\Anki directory.

 If you still have problems, consider installing a different version of mplayer. You can get it here: [http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)

 
  **Anki is not playing my audio!**

 If you’re on Linux, make sure you have installed mplayer. On a Mac, audio requires OSX10.4+ or a special plugin.


in its documentation, which made me think of this. 

can you help at all?

---

### Post by SeijiSensei on 2012-04-28
You can install today's daily build of mplayer from  [this PPA](https://launchpad.net/~motumedia/+archive/mplayer-daily).  Run these commands

```

sudo add-apt-repository ppa:motumedia/mplayer-daily
sudo apt-get update
sudo apt-get install mplayer

```

to replace the version of mplayer on your machine with the one from that repository.

Since this build uses the daily snapshots of mplayer, there's a chance it will be unstable and not function properly.  If you want to revert to the standard version, run these commands

```

sudo add-apt-repository -r ppa:motumedia/mplayer-daily
sudo apt-get update
sudo apt-get purge mplayer
sudo apt-get install mplayer

```

If you're not afraid of building from source, you can download the source tarball from [here](http://www.mplayerhq.hu/MPlayer/releases/mplayer-export-snapshot.tar.bz2) then unpack it and run "./configure; make; sudo make install" as usual.  Before doing so, you need to make sure you have the compiler and all required headers and libraries by running

```

sudo apt-get install build-essential
sudo apt-get build-dep mplayer

```

This version will be installed as /usr/local/bin/mplayer and leave the Ubuntu version untouched.  Because the default PATH places /usr/local/bin ahead of /usr/bin,  typing "mplayer /path/to/file" will use the one you built from source.  To revert to the standard version, just delete the file with "sudo rm /usr/local/bin/mplayer".

---

### Post by andrew.46 on 2012-04-28
That old Jaunty MPlayer guide has a newer Precise Pangolin version just out yesterday:

Howto: Build the svn MPlayer under the latest release version of Ubuntu
[http://www.andrews-corner.org/mplayer.html](http://www.andrews-corner.org/mplayer.html)

that has risen Phoenix-like from the upcoming ashes of Tutorials and Tips :).

---


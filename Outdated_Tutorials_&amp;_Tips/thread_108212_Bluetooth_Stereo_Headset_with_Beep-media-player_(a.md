---
title: "Bluetooth Stereo Headset with Beep-media-player (a2dp,a2play)"
date: 2005-12-25
forum: Outdated Tutorials &amp; Tips
---

### Post by redman5087 on 2005-12-25
This is a little howto for getting a2play to work with beep-media-player.
You need Breezy Badger, it will not work Hoary.
a2play is a package from bluetooth-alsa ([http://bluetooth-alsa.sourceforge.net/](http://bluetooth-alsa.sourceforge.net/))
I'm sorry for my bad english but I will do my best.

First of all, make sure you have a bluetooth STEREO headset that supports the
advanced audio distribution profile (bluetooth:a2dp)

For installing bluetooth-alsa, use this tutorial FIRST.
[http://ubuntuforums.org/showthread.php?t=52296&highlight=bluetooth-alsa]("http://ubuntuforums.org/showthread.php?t=52296&highlight=bluetooth-alsa")
It will not work without.

After this is done , install this:
sudo apt-get install mpg123

You should now have the following syntax working:
    mpg123 --au - file.mp3 | ./a2play 00:0D:3C:30:32:AD
You should remember from the tutorial above that you can find your mac address
of your headset by "hcitool scan".

I suppose you all have beep-media-player installed
If not do so.

Now you have to install sox like this:
 sudo apt-get install sox

You should make a "asoundrc" file. It may not exist.
Create it in your home directory like this:
gedit .asoundrc

     put the following text in it:

                   pcm.stdout {
                                 type file
                                 slave.pcm null
                                 file /dev/stdout
                  }

It 's best to reboot the system now. I don't know if that is exacly nessesary.

Now start beep-media-player and select within preferences the alsa sound driver.
Chose plugin and the output tab.
Choose preferences again of the alsa-driver and with selected audio device, type
the following:

           pcm.stdout

If you start now your beep-media-player from the command-line it should throug
stdout.

Make sure you have a2play installed in the /usr/bin

Now you can use beep-media-player like this:

beep-media-player | sox -c 2 -t raw -r 44100 -w -s - -t au - | a2play -p 00:08:E0:09:75:6F

This should work. You should now hear sound through your bluetooth headset from
beep-media-player

Now make a liitle script and call it like this "play.sh"
put the following inside the script

#!/bin/sh
beep-media-player -p "$1$2$3$4$5$6$7" | sox -c 2 -t raw -r 44100 -w -s -   -t au - | a2play -p 00:08:E0:09:75:6F
done

Make the file executable "chmod a+x".
And put it in your home directory

Now from nautilus, right click an mp3 file, choose properties, 
choose "open with" tab, choose "add" and locate play.sh
Select it as favorite to open mp3

now if you click an mp3 it should work.

Good luck

Redman

---

### Post by gcain on 2006-01-01
Nice howto Redman!

I have been trying to get stereo sound to work for a little while now but very time I run:

mpg123 --au - file.mp3 | ./a2play 00:0D:3C:30:32:AD

I get:

bash: ./a2play: cannot execute binary file

Any ideas what the go could be?

EDIT:
Here's another error I'm getting now...

MPEG 1.0 layer III, 256 kbit/s, 44100 Hz joint-stereo
out of sync (0x2e)
couldn't read header on -

---

### Post by wesper on 2006-01-02
Don't use "./a2play", since then bash tries to find "a2play" in the current directory.

---

### Post by gcain on 2006-01-02
Hi Wesper,

a2play is in the current directory. I haven't done a make install yet.

---


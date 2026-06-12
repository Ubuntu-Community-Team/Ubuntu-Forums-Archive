---
title: "Extending Muine music player"
date: 2006-06-18
forum: Outdated Tutorials &amp; Tips
---

### Post by dontodd on 2006-06-18
[Muine]("http://muine-player.org/wiki/Main_Page") is a basic music player for Gnome that plays ogg, flac, mp3, and aac. I like Muine because I don't always need the features of, say, Rhythmbox or Amarok.

**Installing Muine**

```
sudo apt-get install muine muine-plugin-inotify muine-plugin-trayicon muine-shell
```

(I can't remember if muine-shell is in the repositories or not, but you can download a deb at [http://desrt.mcmaster.ca/code/muine-shell/]("http://desrt.mcmaster.ca/code/muine-shell/").)

Start Muine and File > Import your music directory. Enjoy Muine as it finds songs and albums as you type.

**Add Scrobbler Support**

I recently became addicted to [last.fm]("http://last.fm"), so I needed audioscrobbler support. Luckily, Muine has a plugin for this, available [here]("http://home.gna.org/muinescrobbler/"). To build it I had to install mono-mcs: ```
sudo apt-get install mono-mcs
``` Then I got errors on build, but after browsing the Muine mailing list, I found a patch to fix it [here]("http://mail.gnome.org/archives/muine-list/2006-March/msg00018.html").

**Dynamic Playlists with Ruffle**

Another plugin, [Ruffle]("http://www.informatics.sussex.ac.uk/users/mrm21/ruffle/index.html"), allows you to create dynamic playlists based on your listening history. It tracks all sorts of info about your listening habits and generates a history, charts, playlists, and lets you browse your collection by artist, genre, etc. For playlist generation, play some songs and decide how random you want the list to be, whether to fetch similar artists from audioscrobbler, and whether to stick the the same genre and/or artist.

**Integrating Muine with Gnome (Nautilus)**

Sometimes I like to listen to songs that are "outside" of my collection, so I wrote a Nautilus script that will let me do this. The script lets me right-click music files and send them to Muine. If Muine isn't running, it starts Muine and plays the songs. If Muine is running and playing, it adds the songs to the queue. If Muine is running but not playing, it starts playing the songs right away.

To install, put the script in ~/.gnome2/nautilus-scripts, and make it executable: ```
chmod +x script_name
```

```

#!/bin/bash
#
# send2muine Nautilus script
#
# 17 June 2006
# Todd Slater <dontodd at gmail dot com>
#
# sends selected songs to Muine and either adds them to the queue (Muine
# is playing) or starts playing them right away (Muine is not playing)
#
# requires muine-shell: http://desrt.mcmaster.ca/code/muine-shell/
#
num=1

# test if muine is running

muine-shell -v 2>&1|grep running
runningTest=$?
if [ "$runningTest" -eq 0 ] ; then      # not running, start muine
for tune
do
        if [ "$num" -lt "2" ] ; then
                muine "$tune"&
                num=$(($num+1))
                sleep 2                 # wait for muine to start
        else
                muine-shell -q "$tune"
                num=$(($num+1))
        fi
done
else  # muine is running, let's see if it's playing or not
        # if it's playing, add tracks to queue
        # if not, play the first, add the rest to queue

        if [ `muine-shell -k|sed s/"\.[0-9][0-9]"//` -lt 100 ] ; then
                # muine is playing, add tracks to queue
                for tune
                do
                        muine-shell -q "$tune"
                done
        else    # not playing
                num=1
                for tune
                do
                        if [ $num -lt 2 ] ; then
                                muine-shell -f "$tune"
                                num=$(($num+1))
                        else
                                muine-shell -q "$tune"
                                num=$(($num+1))
                        fi
                done
        fi
fi

```

Enjoy!

---

### Post by oskvaz on 2006-07-02
Hello, I installed Muine without disadvantages but when trying to reproduce the archives gives the following message:

"Backend error
There were no decoders found to handle the stream, you might need to install the corresponding plugins"

I have all the codecs and I use Rhythmbox, VLC player, Realplayer and Gxine without any problem.

What can be happening?

---

### Post by longinus on 2006-07-07
Same thing here! =(

Perhaps because (I think) Muine uses GStreamer 8?

---

### Post by xfile087 on 2007-03-02
Installed and works beautifully for me, a great little player!!! Thanks a lot.

---


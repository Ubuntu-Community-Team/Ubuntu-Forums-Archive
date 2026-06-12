---
title: "Playlist auto-update script"
date: 2013-06-02
forum: Programming Talk
---

### Post by Hekabe on 2013-06-02
I'm trying to write a script to auto-update several large playlists in Audacious which each pull from a single static location. Basically, what I want the script to do is clear each playlist, rescan its respective folder, and then add all the files in those folders to the playlist. I played around with xmms2 for a bit, but it isn't compatible with audacious' proprietary file format. I need it to be a seamless solution, without having to re-import. Basically, I'm asking for a program with an interactive command line interface which can edit playlists and is compatible with Audacious's .audpl format. Any ideas?

---

### Post by gordintoronto on 2013-06-02
Are you asking for help so you can write this program?

---

### Post by Hekabe on 2013-06-03
All I really need is to know of a CLI that could do it, I could write the program with expect. Unless there's another way to do it I'm not thinking of?

---

### Post by Vaphell on 2013-06-04
very very ugly script utilizing xdotool on audacious window
i suggest backing up contents of $HOME/.config/audacious before testing because the script wipes the config so it doesn't have to worry about the current state.

```
#!/bin/bash

acfg=$HOME/.config/audacious

# associative array of ["playlist name"]="path"
declare -A playlists
playlists=(
            ["playlist 1"]="$HOME/Music/Dir1"
            ["playlist 2"]="$HOME/Music/Dir2"  
          )

rm -r "$acfg"  # delete audacious config

for p in "${!playlists[@]}"
do
  # name current playlist
  audacious &      # run audacious
  sleep 1
  xdotool search --onlyvisible --class audacious windowactivate    # activate player window
  sleep 0.1 && xdotool key F2  && sleep 0.1    # rename current playlist   (F2)
  xdotool type "$p" && sleep 0.1 && xdotool key Return && sleep 0.1    # type playlist name
  xdotool key ctrl+q && sleep 2    # quit (CTRL+Q) and give some time to save state

  # add to current playlist from cmdline
  audacious -e "${playlists[$p]}" &     # run audacious, add files to active playlist
  sleep 2
  xdotool search --onlyvisible --class audacious windowactivate
  sleep 0.1 && xdotool key ctrl+t && sleep 0.1 # add new playlist
  xdotool key ctrl+q && sleep 2  # quit
done
```

while the audpl is human readable it would be painful to create by hand because it stores a lot of very specific data that is not trivial to obtain, so i chose to emulate clicks on audacious window to create and name playlists - this way it's the player itself that manages the playlists so everything should be fine.
Script works fine on my test setup, but i don't know if for example sleep intervals will be enough to manage heavier/numerous playlists.

---


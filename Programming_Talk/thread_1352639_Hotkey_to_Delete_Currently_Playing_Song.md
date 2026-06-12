---
title: "Hotkey to Delete Currently Playing Song"
date: 2009-12-11
forum: Programming Talk
---

### Post by mockdeep on 2009-12-11
Hi, I have a massive music collection which I am constantly weeding out and I would love to have a quick and easy way to delete the currently playing track.  Right now I right click on the track in Rhythmbox and click 'Move to Trash'.  I was thinking it would be cool if I could map a delete operation to the Stop media key, which I never use anyway.  At any rate, the tricky part seems to be getting the path to the file, at which point it would be simple to write a shell script and map it to a key.  Are there any media players that can be made to give the path of the currently playing song at the command line?

Thanks!

---

### Post by falconindy on 2009-12-11
MPD with a front end such as MPC can do this.

---

### Post by mockdeep on 2009-12-12
Thanks, this looks like it'll work.  After much trial and error ([and sound bugs]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/410948")) I've got mpd/mpc up and running in a rudimentary way.  Here's the delete script I came up with:

```
#!/bin/bash

# a short script to move the currently playing song
# in mpd to the Trash

deadFile=`mpc --format %file% | head -n 1`
fullDead=$HOME/Music/$deadFile
gvfs-trash "$fullDead"
mpc next
```

Happy to hear comments.

Now for the media keys.  I've got the stop button mapped, but is there any way to map the play/>>/<< keys so that they won't take away from the other media players on my system?

Then there's conky...

---


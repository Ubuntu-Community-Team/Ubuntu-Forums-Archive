---
title: "DVD playback worked ... now it doesn't"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by Samurai Penguin on 2008-06-04
I downloaded a bunch of files for media and DVD was playing great until ...
I got to reading on a HowTo media page and decided to try firefox streaming
and ran:

sudo apt-get remove totem-mozilla mozilla-plugin-vlc xine-plugin kaffeine-mozilla helix-player mozilla-helix-player

then:

sudo apt-get install mplayer mozilla-mplayer

but it failed to install, and no wonder, it's for Hardy Heron only.
Now, when I load a DVD movie Totem opens and runs but the screen is
blacked out and stays that way. How do I undo whatever I did when I
ran:

sudo apt-get remove totem-mozilla mozilla-plugin-vlc xine-plugin kaffeine-mozilla helix-player mozilla-helix-player

thanks

---

### Post by lisati on 2008-06-04
Even if you don't use totem to play DVDs, removing its components can sometimes mess with your ability to play DVDs.

Try from the terminal:
```
sudo aptitude install totem
```

---

### Post by lswest on 2008-06-04
take the commands you ran and run them in reverse order and inversely.

so:
```
sudo apt-get remove mplayer mozilla-player
```
and
```
sudo apt-get install totem-mozilla mozilla-plugin-vlc xine-plugin kaffeine-mozilla helix-player mozilla-helix-player
```

This may install components that were not installed last time, but it will install any files you may have uninstalled when you ran the remove version of that command.

---

### Post by peakshysteria on 2008-06-04
Not sure. But how about:
```
sudo apt-get install totem-mozilla mozilla-plugin-vlc xine-plugin kaffeine-mozilla helix-player mozilla-helix-player
```

---

### Post by sayakb on 2008-06-04
I guess those are VOB files? If so, open them in VLC media player. Should play pretty well I guess..

EDIT: Sorry, I didn't read the post carefully enough..

---

### Post by Samurai Penguin on 2008-06-04
none of the above worked

---


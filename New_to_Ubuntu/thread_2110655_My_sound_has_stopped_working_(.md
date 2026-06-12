---
title: "My sound has stopped working :("
date: 2013-01-30
forum: New to Ubuntu
---

### Post by lemmingrebel on 2013-01-30
I lost power during one of the ubuntu upgrades, and my sound hasn't worked since.

Are there any diagnostics I can run to figure out what is wrong?

---

### Post by mattyasaurus on 2013-01-30
> **lemmingrebel said:**
> I lost power during one of the ubuntu upgrades, and my sound hasn't worked since.

Are there any diagnostics I can run to figure out what is wrong?

Which version of Ubuntu are you running?

---

### Post by mattyasaurus on 2013-01-30
Hey. You could try checking 'Alsa Mixer' To do this follow instructions below:

Open a terminal. (The quickest way is the **Ctrl-Alt-T** shortcut.)
Enter** “alsamixer”** and press the Enter key.
You will now see a user interface. In this user interface, you can do the following:
1- Select your correct sound card using **F6 and select F5** to see recording controls as well
2- Move around with left and right arrow keys.
3- Increase and decrease volume with up and down arrow keys.
4- Mute/Unmute with the **“M”** key. An “MM” means muted, and “OO” means unmuted.
5- Exit from alsamixer with the Esc key.

You could also install the Ubuntu Development Team Driver.  Complete this by entering the following into Terminal:
```

**sudo add-apt-repository ppa:ubuntu-audio-dev** [B]
sudo apt-get update[/B] [B] 
sudo apt-get dist-upgrade[/B]
```

---

### Post by DuckHook on 2013-01-31
Sometimes, the Ubuntu sound server, PulseAudio, gets confused or corrupted and can be corrected by renaming its database directory and letting Ubuntu build a new one. Open a terminal and try the following:

```
mv ~/.pulse .pulse-old
```This will rename your PulseAudio database to .pulse-old. The dots are important. The pulse database is a hidden file in your home directory and all hidden files begin with a dot. Another way to do this is to open Nautilus and press <Ctrl>+<h>. This will unhide all of your hidden files/directories and you can rename .pulse the graphical way.

Now, to rebuild .pulse, logout/login.

If you now have sound, you can safely delete .pulse-old.

---

### Post by tokyo08 on 2013-01-31
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) this link has all kinds of scenarios, from having it on mute to complex things :)

---


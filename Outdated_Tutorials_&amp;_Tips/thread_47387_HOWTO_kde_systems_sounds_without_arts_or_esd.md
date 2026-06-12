---
title: "HOWTO: kde systems sounds without arts or esd"
date: 2005-07-08
forum: Outdated Tutorials &amp; Tips
---

### Post by McQuaid on 2005-07-08
I've switched recently from gnome to kde and had to deal with the dreaded arts sound system again. I really like kde but arts is just plain evil and I didn't want to deal with this again.

Ok, what you'll need:

1) You need to have dmix set up via your .asoundrc file in your home or the system wide file.  I'm not going to go into that here as there are other how to's on that.
2) You'll need to install alsa-oss package.  This will give you the wrapper program aoss to wrap non alsa sound programs and pipe it through alsa as if it's a native alsa app. sudo apt-get install alsa-oss or install via synaptic.

Once you have those we can set this up.
Luckily, kde gives an option to use a command line program to launch system sounds thus bypassing arts/esd altogether.  I noticed the majority of kde system sounds are ogg files.  So first I tried ogg123 and which seemed to work, but ogg123 has a problem in that if there are too many system sounds it ends up with runaway instances of it left running and will end up holding your soundcard and nothing else will be able to access it.  Next I tried aplay, a native alsa cmd line player, but it doesn't support ogg, you'll just get nasty screeching sounds which almost blew my eardrums as I had my headset too loud  :-x   So were going to use play which does support ogg but isn't a native alsa app and that's why we need the wrapper.  This can be used like so aoss play foo.ogg and will play a sound via dmix and not take your soundcard hostage.  But one more catch, kde wouldn't let me specifiy a wrapper followed by the actual program to play the sounds so were going to need to put this in a little script.

1) Launch your favourite editor and put this in:
```

#!/bin/bash
aoss play $1

``` 
2) We're going to need to save this in somewhere like /usr/bin so it's in your path and accessible to any program.  Save it in your home first and call it something like kdesounds.  We need to use a unique name to ensure some other binary is not called the same thing.
3) Now from your home we need to make this executable.  Either do it from konqueror or from the cmd line:  chmod +x kdesounds.
4) Finally copy it to /usr/bin.  From your home dir:  sudo cp kdesounds /usr/bin

Now we are ready to instruct kde to use this.
 
1) Launch kde control center (kde menu --> control center)
2) Expand Sound & Multimedia and select System notifications
3) Turn on all the sounds you want and then near the bottom right you'll see 'Player Settings'.  Select it and choose 'Use an external player'.  Simply place kdesounds in there and we are finally done.

This will allow you to have all this system sounds you want and not hog your soundcard.   Since we are not using arts or esd the only thing left to do is make sure all your apps (xmms,beep, amarok etc) are using alsa and not arts, esd or oss.  This has the added bonus of if you ever use a light window manager like icewm and don't have a sound daemon running, you won't need to muck with your favourite apps sound settings again.

Finally, once this is all working turn off all the system sounds as they are damn annoying.  :grin:

---

### Post by sal on 2005-07-14
would it be posable to do something like this in gnome? if so could you do a write up on it. this way i could set the system sounds and still play audio then everything would be complete for me.
TIA

---


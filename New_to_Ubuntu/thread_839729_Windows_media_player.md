---
title: "Windows media player?"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by Whatrymes on 2008-06-24
I'm trying to view a video from Si.com but I need a plug in. I guess these are usually played via windows media player.

---

### Post by JoshuaRL on 2008-06-24
Does it ask you to install a codec or plugin?

---

### Post by t0p on 2008-06-24
What is it you're asking for? You haven't phrased your question very clearly I'm afraid.

It'd be a good idea to also tell us: what app are you using to try to watch this video?  What exactly is the error message you're getting?

---

### Post by Bright Hammer on 2008-06-24
You need to install the mplayer plugin. Have look at medibuntu [http://www.medibuntu.org/](http://www.medibuntu.org/) .

---

### Post by Whatrymes on 2008-06-24
Sorry I'm new, I can't seem to figure this out. I went to that page was not sure what to download, tried a couple, doesn't seem to work.

---

### Post by JoshuaRL on 2008-06-24
> **Whatrymes said:**
> Sorry I'm new, I can't seem to figure this out. I went to that page was not sure what to download, tried a couple, doesn't seem to work.

That's okay, we all start somewhere.  Let's first add the Medibuntu repository to your computer, then we'll go after some stuff to help you out.
```

sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```
Those are two commands, so just copy and paste them into the terminal.
Then, let's get a couple of packages:
```

sudo apt-get install ubuntu-restricted-extras
sudo apt-get install sudo apt-get install libdvdcss2
sudo apt-get install w32codecs

```
That last command is for a 32bit system.  If you installed the AMD64 version of Hardy, change that last command to:
```

sudo apt-get install w64codecs

```
Then you need mplayer plugin, like Bright Hammer said.  Put this in:
```

sudo apt-get install mozilla-mplayer

```
Does that work?

---

### Post by Xerp on 2008-06-24
Si.com uses Adobe Flash. You just need the Adobe Flash Player plugin for Mozilla Firefox.

---

### Post by JoshuaRL on 2008-06-24
> **Xerp said:**
> Si.com uses Adobe Flash. You just need the Adobe Flash Player plugin for Mozilla Firefox.

And you would do that by putting this into the terminal:
```

sudo apt-get install flashplugin-nonfree

```

---

### Post by Whatrymes on 2008-06-25
Flash player doesn't do anything, tried that before. I followed the instructions of JoshuaRL everything ran fine but still the vids aren't displaying. Now I just get random text scrolling around faster than I can read, in the frame where the video should be playing. ???

---

### Post by JoshuaRL on 2008-06-25
> **Whatrymes said:**
> Flash player doesn't do anything, tried that before. I followed the instructions of JoshuaRL everything ran fine but still the vids aren't displaying. Now I just get random text scrolling around faster than I can read, in the frame where the video should be playing. ???

So you installed the plugin then?  If you get that installed it should work.

---

### Post by Whatrymes on 2008-06-25
When I first opened SI.com, Ubuntu informed me a plugin was required, flash player 9. I installed it. I also installed again with the code you supplied, not working ???

---

### Post by drs305 on 2008-06-25
To see what plugins are actually now installed, type "about : plugins" in the address window. You can then report whether the desired plugins are installed or not.

Note: there are no spaces in "about : plugins" but I had to insert a space to prevent a :p

**Added:** I was just reading a SOLVED thread about FF3 and the flash plugin. If it's still not working or you don't see it installed, reference the following post. If you still have problems, repost here as not as many people view a SOLVED post. If the other post does solve your issues, please return here and mark this post SOLVED as well.

[http://ubuntuforums.org/showthread.php?t=835786]("http://ubuntuforums.org/showthread.php?t=835786")

---

### Post by bhadotia on 2008-06-25
You said that you installed the flash plugin before joshuaRL told you how to.
But, flash is in the medibuntu repo, did you have it enabled before he told you how-to?

Well, whatever the case you first need to completely remove the plugin and then do a fresh install.



```
  sudo apt-get remove --purge flashplugin-nonfree
 sudo apt-get install flashplugin-nonfree
```

Restart the firefox and then try again.

---

### Post by Whatrymes on 2008-06-25
Did that, no go. I also checked to see if it is installed, it is. So is Mplayer plug-in. After mplayer plug-in was installed, instead of just a blank screen now there is text scrambling around the screen and a logo that says "Mplayer Plug-in."

---

### Post by bhadotia on 2008-06-25
Did you restart ff.

---

### Post by bhadotia on 2008-06-25
I've had troubles with flash many a time. Restart of the computer might do the trick.

Before restarting follow the steps I gave above.

---

### Post by Whatrymes on 2008-06-25
SI's web site does require flash player but I do believe the videos are using Windows Media Player. When on my laptop, if I right click the video, it says it is using WMP. I tried some "YouTube" clips which use adobe flash, they work fine. 

I noticed that there are about 4 varieties of MPlayer plug ins listed with Fire Fox, is this okay? Should I uninstall/install them? But I don't know how.

---

### Post by moore.bryan on 2008-06-25
ff's [media player connectivity]("https://addons.mozilla.org/firefox/addon/446") might be what you're looking for.

---

### Post by bhadotia on 2008-06-25
Try the new gecko media player plugin. The mplayer plugin requires to be configured first. But this plugin works without the need of any manual configuration.

Do this:
```
**sudo apt-get remove kaffeine-mozilla mozilla-helix-player mozilla-mplayer mozilla-plugin-vlc totem-mozilla xine-plugin**

**sudo apt-get install gnome-mplayer gecko-mediaplayer** 
 
```

Don't forget to restart firefox after your are done installing.

---

### Post by Whatrymes on 2008-06-25
moore.bryan got it! 

Thank you,
Ed

---

### Post by moore.bryan on 2008-06-26
glad to hear you got it working!

---


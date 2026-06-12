---
title: "Default plug-in vs. Adobe Flash plug-in problem"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by elint66 on 2008-04-27
As a preface, I am absolutely ABSOLUTELY new to linux and ubuntu, so thanks in advance for the things I will soon learn.

My ethernet worked right out of the box (the wireless one, I'll be posting another thread), and so I decided to go to youtube. Of course, I need a flash player.

Firefox recognized this, and so I clicked on "install missing plug-ins." I installed the first one without looking at it, and now youtube videos appear, (the sound works perfectly), but the video is very jittery. 

Later, I went over to Adobe's official Flashplayer webpage and installed that flash player. I believed I did this perfectly and properly.

Now, however, the original one is taking precedence and I still get lag. I know this is due to the original one because flash appears as a gray box with a central "play" symbol.

How do I fix this? Thanks in advance!

---

### Post by NilsE on 2008-04-27
> **elint66 said:**
> How do I fix this? Thanks in advance!

Go into Synaptic and remove flashplugin-nonfree which will remove the flash that was installed from the repos.  You will then have to reinstall the Adobe one.

I am not sure if it will solve your problem since Ubuntu actually installs the Adobe plugin but sometimes reinstalling helps.

---

### Post by twright on 2008-04-28
you might have installed gnash, not the adobe flash player

---

### Post by Sirron on 2008-04-28
Yes, you definitely installed Gnash.

Open Synaptic, and remove "gnash", then install "flashplugin-nonfree"

That will solve your problem.

---

### Post by elint66 on 2008-04-29
Thanks for all the help guys but no dice :(

I never installed gnash (I checked synaptic and it confirms this). In Firefox add-ons, I painstakingly disabled each add-on, one by one, and I have isolated the problem to Shockwave Flash 9.0 r100 and r124.

Whenever I load a youtube video, for example, I get a big gray box with a central "Play" symbol. When I click on this "Play," the video begins to load. The sound plays fine, but the video is AWFULLY choppy.

Thanks!

---

### Post by aheckler on 2008-04-29
Try this:

[LIST=1]
[*]Close Firefox.
[*]Go into Synaptic Package Manager.
[*]Search for "gnash".
[*]If anything in the results is installed, remove it.
[*]Search for "swfdec".
[*]If anything in the results is installed, remove it.
[*]Restart Firefox and see if Flash works now.
[*]If not, you may need to install the official plugin again (flashplugin-nonfree), NOT Gnash or Swfdec.
[/LIST]

---

### Post by vishzilla on 2008-04-29
```
sudo apt-get remove gnash swfdec
sudo apt-get install flashplugin-nonfree
```

---

### Post by aheckler on 2008-04-29
> **vishzilla said:**
> ```
sudo apt-get remove gnash swfdec
sudo apt-get install flashplugin-nonfree
```

Or that.... ;)

---

### Post by Sukarn on 2008-04-29
despite what everyone here has been saying, I too have been experiencing slow playback in youtube and other websites. I didn't really notice it at first, but I noticed that it was really slow when I watched the same videos on a windows machine, and the same videos on Ubuntu but in a different player (VLC) instead of the flash player from adobe.

I've heard that r124 gives this problem because of high cpu usage from that plugin, and that r49 did not have this problem, so downgrading might help, although I have not personally tried this.

---

### Post by elint66 on 2008-05-03
Okay, so it's been fixed. I followed some of the directions here, but I think a nice restart is what was needed, apparently.

I have Shockwave r124 installed, but I uninstalled r100. Maybe that was it?

---


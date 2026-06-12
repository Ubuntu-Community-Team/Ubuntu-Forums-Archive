---
title: "[SOLVED] Music players?"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by slughappy1 on 2008-08-01
I was wondering if there is a music player out that will read the cd art that is integrated into mp3s? For example, most of my cd's have the cd art added to them using itunes. So the music player doesn't need to go online and get them, like rhythmbox does.

---

### Post by ConMan318 on 2008-08-01
> 
Where does Banshee get its cover art?
    Banshee looks first in the audio file itself for embedded artwork, then in the folder the file is in, then from Rhapsody, then Amazon, then finally Last.fm.


That is from the Banshee 1.2 FAQ.  I'm not sure if the Banshee that's in the repos (1.0) does that or not, but 1.2 is very easy to install.

[https://edge.launchpad.net/~banshee-team/+archive](https://edge.launchpad.net/~banshee-team/+archive) has instructions for installing in Hardy and Gutsy.

---

### Post by wolfen69 on 2008-08-01
amarok will do that also, once you set it up.

---

### Post by slughappy1 on 2008-08-01
Well then I should also ask, will the programs that you mention be in the repositories? Or will I have to get the newest version from their respective sites?

---

### Post by adobrakic on 2008-08-01
They're all in the repos

---

### Post by ConMan318 on 2008-08-01
> **adobrakic said:**
> They're all in the repos

No, the newest version of Banshee is not in the default repos.

It only takes about 15 seconds to add the repository needed, so I wouldn't factor it so heavily that it's not in the default repos.  Give it (and Amarok, might as well try some options) a try, and if you don't like it, uninstall it.

---

### Post by vikramaditya on 2008-08-01
> **adobrakic said:**
> They're all in the repos
Life of a repo man is always intense. :)

---

### Post by slughappy1 on 2008-08-01
Does Amarok work well in Gnome? I think I remember trying to use it once, but it kept freezing and closing for some unknown reason.

---

### Post by ConMan318 on 2008-08-01
It depends on the computer.  Try it and see if it works on yours; don't assume that others' experiences will mirror your own.  Install it, try it, and if it's no good, it can be removed with 4 words:
```

sudo apt-get purge amarok

```

---

### Post by slughappy1 on 2008-08-01
Ok maybe I should have been more detailed in my question. I meant, is it fully compatible with Gnome. Or does it just work most of the time?

---

### Post by SunnyRabbiera on 2008-08-01
> **slughappy1 said:**
> Ok maybe I should have been more detailed in my question. I meant, is it fully compatible with Gnome. Or does it just work most of the time?

well me i never had any issues what i used with amarok, as it worked all the time for me.

---

### Post by gjoellee on 2008-08-01
AMAROK ALPHA 2 is beautiful and s easy to use with a great layout, use Ultamatix to get it: [http://linux.softpedia.com/get/System/Software-Distribution/Ultamatix-24551.shtml](http://linux.softpedia.com/get/System/Software-Distribution/Ultamatix-24551.shtml)

---

### Post by slughappy1 on 2008-08-01
And what is the difference between ultamatix and synaptic?

---

### Post by skipknyc on 2008-08-01
> **gjoellee said:**
> AMAROK ALPHA 2 is beautiful and s easy to use with a great layout, use Ultamatix to get it: [http://linux.softpedia.com/get/System/Software-Distribution/Ultamatix-24551.shtml](http://linux.softpedia.com/get/System/Software-Distribution/Ultamatix-24551.shtml)

[FONT="Comic Sans MS"]Man ... I'm running Amarok 1.4.9.1. right now (just installed it yesterday), and it sounds *incredibly*good! Never heard anything better coming out of my speakers![/FONT]

---

### Post by Raine on 2008-08-01
> **slughappy1 said:**
> Ok maybe I should have been more detailed in my question. I meant, is it fully compatible with Gnome. Or does it just work most of the time?

It is fully compatible with gnome from what I have seen. The only problem that I have had was that I had to switch the audio device to alsa so that it would be able to play sound in other aps. Other than that it is an amazing media player. I have also been getting into banshee which works very well.

---


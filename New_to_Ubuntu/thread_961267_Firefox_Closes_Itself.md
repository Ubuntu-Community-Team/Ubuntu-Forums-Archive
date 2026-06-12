---
title: "Firefox Closes Itself"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by Pioneer5000 on 2008-10-28
Having a bit of trouble with Firefox and i have been having this problem for a while now. Whenever i watch videos etc. or even in some cases play audio files Firefox just closes itself down. Like eg. watching a Youtube video i can watch a couple then the next video will just shut down it seems to be kinda random. Anyone know how to fix this? as its getting very annoying now. Thanks.

---

### Post by Ganonspike on 2008-10-28
Yeah that is a common problem with ubuntu's firefox. What i did was just keep trying different java plugins until you get one that does actually work all the time. Just remeber to remove the old plugiins when doenloading the new ones. Also does your firefox close with or without audio breakdown?

---

### Post by Thelasko on 2008-10-28
A) This doesn't sound like a Java problem, it sounds like a Flash problem.
B) What version of Ubuntu are you using?

---

### Post by Pioneer5000 on 2008-10-29
Audio/Video works fine then out of no where Firefox window will just close.



I'm using Ubuntu 8.04.

---

### Post by macogw on 2008-10-29
Adobe makes a broken Flash that likes to crash whatever browser you use, because they don't really care about Linux too much.  I use swfdec-mozilla instead of Adobe Flash, but it's pretty much only good for YouTube.  The alternative is to upgrade to 8.10 when it's released on Thursday, because that has Adobe Flash 10, which is more stable.

Or, you can install Adobe Flash in nspluginwrapper so that only Flash crashes without taking down Firefox as well.

---

### Post by kansasnoob on 2008-10-29
I don't altogether disagree with this being a flash problem, but since you also say:

> or even in some cases play audio files Firefox just closes itself down

My bet is it also involves pulse audio. The following tutorial straightened out all of my pulse audio problems in Hardy:

[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

That PPA will also get you Flash 10.

Something you could try first is just installing the Flash 10 .deb from here:

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

Read the next post if you choose to just install Flash 10!

---

### Post by macogw on 2008-10-29
> **kansasnoob said:**
> I don't altogether disagree with this being a flash problem, but since you also say:



My bet is it also involves pulse audio. The following tutorial straightened out all of my pulse audio problems in Hardy:

See, I'm betting they're using a Flash-based music player though, because that's how most sites handle it nowadays to keep people from leeching their songs.

---

### Post by kansasnoob on 2008-10-29
I had additional thoughts if you decide not to do the Pulse Audio fix thing and just go for installing the Flash 10 .deb.

First remove the old flash:

```
sudo apt-get remove --purge flashplugin-nonfree
```

Then install the new Flash, then restart Firefox by going to File > Quit. Then restart Firefox and the changes should take a hold.

---

### Post by kansasnoob on 2008-10-29
> **macogw said:**
> See, I'm betting they're using a Flash-based music player though, because that's how most sites handle it nowadays to keep people from leeching their songs.

Quite possible. I have gotten by quite well with my last two fresh installs of Hardy just installing the Flash 10 Final Release.

Prior to that I used the Pulse Audio fix on several installs and it worked very well also.

---


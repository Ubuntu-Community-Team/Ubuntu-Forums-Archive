---
title: "you tube video playing problems"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by scientist1971 on 2008-04-28
have seen that several other users have had this problem
using gutsy
youtube videos freeze the browser I am using (and the whole OS) and the only solution is a restart
I have looked at other peoples solutions and tried the following already:
installed java, flash non free etc from multiverse
tried firefox, epiphany and opera
medibuntu could not be found by terminal
and gnash
still will not work and I fear I may have 'clogged' up my system with a load of non functioning packages
and help appreciated (as usual :))

---

### Post by spiderbatdad on 2008-04-28
can you remove the programs you don't want and flash using synaptic...then run sudo apt-get update...then reinstall flashplugin-nonfree?

---

### Post by gunbladeiv on 2008-04-28
Firefox 3 beta 5 is known with the flash problems which will freeze the browser randomly.  As far as i'm using epiphany, there is no problem at all viewing youtube.com or any streaming flash player.  

FYI, i'm not using flash plugin from the repo, try to install the flash plugin manually, hope that will fix that.  By the way, stick with epiphany browser until Firefox release a stable version of Firefox 3.

---

### Post by scientist1971 on 2008-04-30
seem to be having the youtube prob a lot of other people have i.e. freezes firefox and the whole os
I have downloaded
Adobe Flash Player version 9.0.124.0
.tar.gz for Linux (x86) | 3MB
but when I get to archive manager I get stuck
I definately feel I am over looking something really simple
do I extract or open?
why is there no simple install button?

---

### Post by pedro_orange on 2008-04-30
Simple "install button" for dvd codecs/mp3codecs / flashplayer / jre ==

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Google Spider on 2008-04-30
It must be having installation instructions in a txt inside, or on the website where you downloaded. There is also an easy way to install flash in case you're not aware of it:
```
sudo apt-get install flashplugin-nonfree
```

edit: oops! Beaten. pedro_orange's code will install many more goodies :)

---

### Post by scientist1971 on 2008-04-30
i tried that and installed it but you tube is still asking me to get the latest flash player....

---

### Post by pedro_orange on 2008-04-30
> **scientist1971 said:**
> i tried that and installed it but you tube is still asking me to get the latest flash player....

Remove the old software. (Using add/remove or synaptic for example) and then re-install it using either methods described above.

---

### Post by timcredible on 2008-04-30
for anyone reading this that has this problem - DO NOT GO THROUGH THE EFFORT OF INSTALLING FLASH FROM ADOBE.COM!!!!  use synaptic (system->administration->synaptic) to install flashplugin-nonfree.  if this is the first time using synaptic, click on 'reload' first, then do a 'search' for flashplugin-nonfree, mark it to be installed, then click 'apply'.  all software you install should be done like this.  the above instructions are the same as the previous poster's instructions, only that this one uses a gui.

---

### Post by scientist1971 on 2008-04-30
i tried that and it still ask me to download the flash player

---

### Post by scientist1971 on 2008-04-30
i know I should not double thread but not really getting anywhere
problem is when I download a package rather than use synpatic
I open install manager and I can either open or extract (thats the first problem..)
it extracts to temp files and then I am offered extract or open again
going round in circles
Am I overlooking something really easy or what?
where is install??
this is doing my head in it should be easier than this....

---

### Post by oedha on 2008-04-30
what about installing gstreamers ?

---

### Post by mivo on 2008-04-30
Where are you downloading the packages from and what is their file extension? Also, why not use Synaptic?

---

### Post by scientist1971 on 2008-04-30
.tar.gz

when I search in syntaptic they are not found

BTW uni/multiverse are enabled so V confused

---

### Post by scientist1971 on 2008-04-30
sorry
the adobe flash download page
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

---

### Post by mivo on 2008-04-30
Ah, well, those are just archives, not Debian/Ubuntu packages (their extension is .deb, and they are installed by double-clicking). Flash was installed on my system when I went to a web site that required flash (i.e. youtube.com) and Firefox asked if I wanted to install the plugin. Have you tried this?

---

### Post by scientist1971 on 2008-04-30
you tube asks me:
get latest flash player
I click on the link
offered following downloads:
YUM for linux - does not work
.rpm for linux does not work
.tar.gz for linux cannot install
and flash not free does not work so really banging my head against a wall here
XP calls....unfortunately:(

---

### Post by mivo on 2008-04-30
Firefox should give you a "missing plugin" message the first time you encounter flash on a web site, and then offer the download (not from a web site). If you type:

```
about:plugins
```

... in the URL box of the browser (just like that), does it say anything about shockwave?

Which browser are you using? 32- or 64-bit?

---

### Post by aysiu on 2008-04-30
Please follow one of these screenshot-laden tutorials. If you get stuck on one part, just ask:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)
[http://www.psychocats.net/ubuntu/flashmanual](http://www.psychocats.net/ubuntu/flashmanual)

---


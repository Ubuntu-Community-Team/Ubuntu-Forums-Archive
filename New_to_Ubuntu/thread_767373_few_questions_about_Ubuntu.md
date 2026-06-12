---
title: "few questions about Ubuntu"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by MUNDO5555 on 2008-04-25
Hello all.  i am taking a introductory class in redhat at school so i thought i'd download Ubuntu at home and try it out.  It just happened to be yesterday (release day) :) .  anyway i have a few questions.

1.  Because this is version 8.04 and was just released do i need to wait for programs to be updated to be compatible with my version?

2.  Id like to get some more screensavers and maybe a few more small games.  Are there some websites i could go for these?

3.  I went and downloaded a bitchx (Internet Relay Chat client) tarball off of the web, i looked around in the forums here before i attempted to install and i found a thread that said it was safer to use the apt-cached method then a tarball.  The search did not return anything about bitchx.  sources.list in /etc/apt has universe and multiverse uncommented so i don't think theres a version out that works with mine?

4.  I've seen some really sweet screen shots of peoples desktop themes (not sure if this is the right terminology) are these hard to do? or are there packages i can get to help me out.  I'd like to get a real slick lookin setup and impress my friends.

well thats it for now!  I'm off to school so ill give my thanks in advance!

---

### Post by Joeb454 on 2008-04-25
1) No not all :)

2) I'm not sure on that one, try searching Google for gnome-look :)

3) There should be, enable all repositories then load up synaptic and search for it. My preferred IRC Client however, is XChat, you may want to look into it :)

4) It depends what you want to do :p

And keep in mind Ubuntu is a Debian based system, so it will be quite different from what you are studying about Red Hat :) Just thought I would pre-warn you

---

### Post by MUNDO5555 on 2008-04-25
thanks for the response!

synaptic did not return any results for either bitchx or chatx, I will go and uncomment all the things in /etc/apt/sources.list when i get home and see if i get anymore luck.  

Im not really sure what they did for there desktops.  they seemed to have customized everything from a neat see through terminal to firefox matching up with there background.  I dont think it would be that hard to do i'm just not sure what to search for to begin.  Poking around on the forums is a help.  And yes redhat is different.  i found that out when i tried to ll and got a bash error :).

---

### Post by Joeb454 on 2008-04-25
:lolflag: Yeah, but learning about Red Hat & Debian systems will likely help a lot, especially if you are interested in Server systems etc :)

And it wasn't chatx, it was XChat - it's in the Ubuntu repositories. And instead of editing your sources.list, you can open up System > Administration > Software Sources :)

Hope this helps

---

### Post by hellonull on 2008-04-29
BitchX is not in Hardy's repos. Apparently there are some [security issues]("http://ubuntuforums.org/showthread.php?t=735341").

However, you can still install it using the .deb package from Gutsy. It is available at [Linux App Finder's bitchx page]("http://linuxappfinder.com/package/bitchx"). Just download it and install using the GDebi Package Installer. After installation, it will show up in Synaptic as an installed package (green box).

---

### Post by Helios38 on 2008-04-29
> **MUNDO5555 said:**
> Hello all.  i am taking a introductory class in redhat at school so i thought i'd download Ubuntu at home and try it out.  It just happened to be yesterday (release day) :) .  anyway i have a few questions.

1.  Because this is version 8.04 and was just released do i need to wait for programs to be updated to be compatible with my version?

2.  Id like to get some more screensavers and maybe a few more small games.  Are there some websites i could go for these?

3.  I went and downloaded a bitchx (Internet Relay Chat client) tarball off of the web, i looked around in the forums here before i attempted to install and i found a thread that said it was safer to use the apt-cached method then a tarball.  The search did not return anything about bitchx.  sources.list in /etc/apt has universe and multiverse uncommented so i don't think theres a version out that works with mine?

4.  I've seen some really sweet screen shots of peoples desktop themes (not sure if this is the right terminology) are these hard to do? or are there packages i can get to help me out.  I'd like to get a real slick lookin setup and impress my friends.

well thats it for now!  I'm off to school so ill give my thanks in advance!



1. No

2. depends on your hardware :)

3. try XChat

```
sudo apt-get install xchat
```

4. if your hardware can support it, try compiz fusion

---

### Post by hyper_ch on 2008-04-29
Konversation is also a very nice irc client... or go with the command-line based irssi

---


---
title: "From warty to hoary"
date: 2005-03-11
forum: Repositories &amp; Backports
---

### Post by Miguel on 2005-03-11
Hello everybody,

I'm a warty user willing to upgrade to hoary when it goes gold. My question is: will an apt-get dist-upgrade (after changing warty with hoary on my sources.list) give me all the new benefits, like faster booting and improved laptop support? (both very important, as I run a Dell Inspiron 8600). Or should I burn a Hoary CD and install it?

Please note that the second option wouldn't be much of a trouble, as I have a /home partition (as well as /boot and /var, that will be promptly deleted).

I'm sorry if this question doesn't proceed here, but just asked because found lots of topics on upgrading.

Thanks in advance,

Miguel

---

### Post by telmo on 2005-03-11
És Português?

---

### Post by kahping on 2005-03-11
yep... just the way you said it. plus, read the wiki here: [http://www.ubuntulinux.org/wiki/HoaryUpgradeNotes](http://www.ubuntulinux.org/wiki/HoaryUpgradeNotes)

for additional info...

another way is to replace warty with hoary in sources.list, run synaptic, then click reload followed by mark all upgrades and finally apply. same thing there.  ;) 

kahping

edit: o yeah... don't forget to reboot after the upgrade so that the changes get applied.

---

### Post by Miguel on 2005-03-11
Thanks a lot, foks!!!

I should recompile the few programs I built from sources, shouldn't I?

BTW: Telmo, I'm spanish.

---

### Post by jsgotangco on 2005-03-11
I didnt recompile anything again when I upgraded to Hoary. But after doing the apt-get dist-upgrade, you might want to keep your existing configurations (it will give options) and remove the apps that were basically backports and install the hoary ones. Just dist-upgrade when Hoary gets released as stable.

---

### Post by jdong on 2005-03-11
This really doesn't have much to do with this forum.

A rumor/freakout that Backports is catastrophic to the upgrade is why we have so many updating questions in here. 99% of the times, that's absolutely FALSE and can be ignored.

---

### Post by LongTooth on 2005-03-11
Maybe this is a dumb question but here goes. I've upgraded to Hoary and am very pleased with it. Obviously I did the 'dist-upgrade' when I did. Now for my question: I'm thinking I shouldn't 'dist-upgrade' (or using Synaptic) Smartupgrade any more. I'm thinking there is no need for it since I've already upgrade to Hoary and as anyone knows, especialy me, if used too easily dist-upgrade can bork you system. Comments anyone? 

PS I do update, upgrade every two day or so. 

Thanks.

---

### Post by jdong on 2005-03-11
It never hurts to do dist-upgrade, **as long as** you use a bit of common sense. If APT says "The Following Packages Will Be REMOVED", then lists 50 packages, it doesn't take Einstein to figure out that you'll break your system!

Hoary is still much in development, so you should do "dist-upgrade" to get a complete update -- I personally always use dist-upgrade.

---

### Post by LongTooth on 2005-03-11
Jdong, thanks. In the past I've messed up more systems then I can remember, so I'm a little gun shy with the 'dist-upgrade'. But I wil try to be more conscious in the future of what Apt tells me. Thanks.

---


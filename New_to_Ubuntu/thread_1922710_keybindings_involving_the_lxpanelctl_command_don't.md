---
title: "keybindings involving the lxpanelctl command don't work"
date: 2012-02-09
forum: New to Ubuntu
---

### Post by erisdiscordia on 2012-02-09
Hello all,

I am a *very* fresh Linxus, Ubuntu, and Lubuntu user, having only spent a few weeks each twelve, then four, years ago experimenting with Linux and then giving up over hardware issues. Also, I previously didn't have any hardware that my wife didn't make "I WANNA RUN WORD AND NOT HAVE TO THINK ABOUT BOOTING" demands on. :-) This run is MOSTLY going better, but every desktop I have tried has issues. I'm close to deciding on Lubuntu but I'm blocked by the titular issue.

Context: I'm on a Toshiba NB305 netbook with 1GB RAM, 2GB ordered but no shipment date provided yet. I installed as dual-boot using the Big Orange Button installer on the Ubuntu website. Unity 3D is... well. Unity 2D is borderline bearable, and I actually may revisit it once I have 2GB, but I wanted something less painful than Unity-on-a-netbook NOW. So I followed the instructions here:

[http://askubuntu.com/questions/44062/how-do-i-install-lxde-lubuntu](http://askubuntu.com/questions/44062/how-do-i-install-lxde-lubuntu)

Lubuntu is... surprisingly pretty! And beautifully responsive. (To out the desktop list: I tried Openbox/Gnome after first hitting my keybinding difficulties, and at first it was all "LOL TRY GUESS WAT DO" and after some googling it was all "LOL U NO HAVE MIDDLE MOUSE BUTTON.")

However, I quickly got the urge, among other now-solved wizardry like key-minimizing windows, to make. the bloody. start. menu. appear. with. a key.

I'm stuck. And worse yet, I seem to be alone. I can't find any reports of someone else having the exact same problem as me.

After hours of research and experimentation, I've narrowed it down to being apparently this: any keybinding that uses the command "<command>lxpanelctl foo</command>" isn't working. I.e. out of the defaults, any keybinding using lxpanelctl run or lxpanelctl menu isn't working. I must confess that I haven't tried yet creating a custom keybinding involving lxpanelctl. The friskiest I've gotten is setting Toggle Desktop to Win-M.

A perhaps-useful data point: trying "lxpanelctl run" from the term (I was too scared that calling "lxpanelctl menu" from the term would make my computer "divide by zero") caused absolutely nothing to happen.

A second perhaps-useful data point: the keybinding for bringing up the file manager brings it up unfocused. This isn't a showstopper deal to me per se, but I wonder if it has a tie-in to the problem that actually bothers me. I read a discussion mentioning this type of problem and a fix (isn't at hand but I can probably dig it up on request) but the way the suggested XML was formed didn't quite match the conventions I saw in my config file so it scared me off.

May I ask for some advice on what might be the problem?

---

### Post by erisdiscordia on 2012-02-09
I finally found a discussion of this problem! It is a bug, and it is here:

[https://bugs.launchpad.net/ubuntu/+source/lxpanel/+bug/769644](https://bugs.launchpad.net/ubuntu/+source/lxpanel/+bug/769644)

A passable workaround is mentioned at that address.

---


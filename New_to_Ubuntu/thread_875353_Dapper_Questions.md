---
title: "Dapper Questions"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by houseisland on 2008-07-30
Having installed the Gnome Network Manager applet, how do I run it so that I can try to configure WPA encryption with a wireless card?  The the native network config tool only allows for WEP.

In the Synaptic package manager there is a button which can be clicked to upgrade to a current version of Ubuntu, 8.x something.  What are the risks of doing an upgrade?

Thanks.

---

### Post by phidia on 2008-07-30
Last question 1st-I'm not sure if you can go directly from 6.06 to 8.10 unless the LTS status of dapper somehow makes that possible? Anyway I think the common wisdom here is clean installs are less trouble prone-do a search on full back ups.

The Ubuntu Community Docs do contain guides on WPA [here]("https://help.ubuntu.com/community/WifiDocs/WPAHowTo").

---

### Post by kansasnoob on 2008-07-30
I've never done a Dapper to Hardy upgrade in Ubuntu. I did one in Kubuntu and it went OK other than some screen resolution problems but that Kubuntu had NOT been used or modified much. (I was then just starting out -7 months ago- and had read a lot of good things about Kubuntu Dapper)

My luck with upgrades from Gutsy to Hardy have been about 50% successful and the other 50% require a full install. So, backup, backup, backup!

Personally before upgrading I'd BACKUP (oops overkill), then run a sudo apt-get autoclean followed by a sudo apt-get clean.

Honestly, if you have at least 10GB free space (and you're under the 4 primary partition limit) I'd just install Hardy on a separate partition and see how it works, then you'll have a chance to work out the (personal) bugs.

Dapper is still supported until June 2009!

---

### Post by bodhi.zazen on 2008-07-30
You can try upgrading directly, it is supported to do this, but as will all upgrades there is always a chance that the upgrade will fail.

Once you have upgraded (or failing that re-installed), if you want wpa, I found network manager was problematic.

I advise you install wicd : [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by houseisland on 2008-07-31
Thanks all.

Last question first:

> **phidia said:**
> Anyway I think the common wisdom here is clean installs are less trouble prone-do a search on full back ups.

> **kansasnoob said:**
> My luck with upgrades from Gutsy to Hardy have been about 50% successful and the other 50% require a full install. So, backup, backup, backup!

Personally before upgrading I'd BACKUP (oops overkill), then run a sudo apt-get autoclean followed by a sudo apt-get clean.

):P






> **bodhi.zazen said:**
> You can try upgrading directly, it is supported to do this, but as will all upgrades there is always a chance that the upgrade will fail.

Thanks.  This is about what I expected.  I am a big fan of clean installs.

First question last:

> **phidia said:**
> The Ubuntu Community Docs do contain guides on WPA [here]("https://help.ubuntu.com/community/WifiDocs/WPAHowTo").

> **bodhi.zazen said:**
> Once you have upgraded (or failing that re-installed), if you want wpa, I found network manager was problematic.

I advise you install wicd : [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

My daughter has moved out.  She has been running Dapper almost since it was first released, and she loves it.  She is renting a suite in a house, and the house owners have no problem letting her piggy-back on their wireless, which is WPA.  I dragged a windoze box over and tried it with a couple of different NICs, and it seems that the router is too far away to get a reliable signal anyway so there is not much point in investing time in getting WPA setup in Dapper (seemingly a painful task, unusual in comparison to the relative ease of doing other things in Dapper).  So she has signed up for ADSL service, and I will give an old wired router.   

After 2009, I may rebuild the machine for her (proc and hard drive upgarde) and install Hardy.  At present she is extremely happy with Dapper and does not wish to change.

---


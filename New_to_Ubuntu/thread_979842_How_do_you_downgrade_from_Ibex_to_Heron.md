---
title: "How do you downgrade from Ibex to Heron?"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by hapkidoman on 2008-11-12
Hey guys,

I'm a huge fan of the ubuntu 8.10, but there are some things in it that do not work quite right like they did in Hardy Heron (cairo-dock, audacity, etc.) is there a safe way to downgrade from Ibex to Heron without screwing anything up?

Thanks in advance

---

### Post by Steve1961 on 2008-11-12
Safest way is to back up your data and then do a clean install of Hardy

---

### Post by tuxxy on 2008-11-12
WHy not try AWN its better than Cairo imo

---

### Post by iponeverything on 2008-11-12
Steve1961 is right.

It's pretty much a one way street.

---

### Post by mjwhitfield on 2008-11-12
> **steve1961 said:**
> safest way is to back up your data and then do a clean install of hardy+1

---

### Post by Duck2006 on 2008-11-12
+1 on back-up your data and do a install.

---

### Post by hapkidoman on 2008-11-12
If it's pretty much a one way street, then I'll just wait until developers fix the problems in cairo and in audacity (way too technical for me to help).  Also, AWN was too glitchy for me.  Are there any like AWN and Cairo that work well in Ibex?

---

### Post by DGortze380 on 2008-11-12
> **hapkidoman said:**
> If it's pretty much a one way street, then I'll just wait until developers fix the problems in cairo and in audacity (way too technical for me to help).  Also, AWN was too glitchy for me.  Are there any like AWN and Cairo that work well in Ibex?

could try kiba

---

### Post by Kaspersky_ on 2008-11-12
Don't update to 8.10?

---

### Post by phidia on 2008-11-12
> **hapkidoman said:**
> Hey guys,

I'm a huge fan of the ubuntu 8.10, but there are some things in it that do not work quite right like they did in Hardy Heron (cairo-dock, audacity, etc.) is there a safe way to downgrade from Ibex to Heron without screwing anything up?

Thanks in advance

There actually is a method for downgrading debian based distros-it's been an often discussed topic. There is a Ubuntu wiki entry on that [here]("https://help.ubuntu.com/community/DowngradeHowto")-be sure to read the intro.

For anyone else who is feeling experimental or wanting a little OS adventure a debian based write up on pinning to accomplish downgrading is [here]("http://ryandaigle.com/articles/2005/10/31/listing-downgrading-unstable-testing-debian-packages").

---

### Post by hapkidoman on 2008-11-12
Thanks all, I'll try Kiba and just forget about downgrading.  I don't want to screw anything up :)

---

### Post by bodhi.zazen on 2008-11-12
> **phidia said:**
> There actually is a method for downgrading debian based distros-it's been an often discussed topic. There is a Ubuntu wiki entry on that [here]("https://help.ubuntu.com/community/DowngradeHowto")-be sure to read the intro.

LOL, that is not for the feint of heart and is more complicated the re-installing.

> I have *YET TO TEST THE PROCEDURE*. Please pursue at your own risk until this documentation is completed!And

> we'll use the example of downgrading Ubuntu Breezy to Ubuntu Hoary

Also notice the last line of that wiki page :

> The last step probably will end up a **catastrophic mess of incompletely installed packages**. We need to fix that now.bolded emphasis added by me :)

I think that last sentence sums up the reason this is not advised very often.

Breezy = 5.10 (3 years old and the wiki page is not yet "completed")

Hoary = 5.04.

So take that advice with a large grain of salt.

With all of that said, if you know how to actually do this please consider updating the wiki :twisted:

---

### Post by starcannon on 2008-11-12
If you decide to go back to 8.04, then after you have backed up your data; during the install process, take time to manually partition the drive.
Ext3 10~20gb for /
Swap 2gb
Ext3 rest of drive for /home

This way /home is on its own partition, then if you ever regret an upgrade a clean install is as simple as not formatting that partition during the install process. Any clean install of course means reinstalling software, but thats all neatly available through synaptic.

GL have fun, and always backup before you move forward.

---

### Post by directcharitycontribution on 2008-11-12
> **bodhi.zazen said:**
> 

Breezy = 5.10 (3 years old and the wiki page is not yet "completed")

Hoary = 5.04.

So take that advice with a large grain of salt.

With all of that said, if you know how to actually do this please consider updating the wiki :twisted:

and correlate adopters

---

### Post by phidia on 2008-11-12
I have done this with debian. I added a link to my orginal post that shows most of what's required. 
My reason for adding to this thread was to point out that it's possible to make the attempt if one wants to-whether or not it's practical I leave to those who want to try it. 
One doesn't learn by staying in the parameters of tradition or what's accepted practice.

---

### Post by phidia on 2008-11-12
> **bodhi.zazen said:**
> LOL, that is not for the feint of heart and is more complicated the re-installing.

And



Also notice the last line of that wiki page :

bolded emphasis added by me :)

I think that last sentence sums up the reason this is not advised very often.

Breezy = 5.10 (3 years old and the wiki page is not yet "completed")

Hoary = 5.04.

So take that advice with a large grain of salt.

With all of that said, if you know how to actually do this please consider updating the wiki :twisted:

The notation here says

"DowngradeHowto (last edited 2008-11-02 19:50:21 by j-kurella"

It appears someone has reviewed the wiki then.

---

### Post by ibuclaw on 2008-11-12
I agree with phildia, all you need is a strict pin to downgrade.

[EDIT]
OK, I ran this in a VM... and I have reviewed the steps I previously posted and have made judgmental decisions on what to do when things seem to go pear shaped...

First, change your sources back to Hardy. Usually sed is the move efficient way of doing this.
```
sudo sed -i 's/intrepid/hardy/g' /etc/apt/sources.list
```

And create your preferences files.
```
sudo touch /etc/apt/preferences
sudo ln -s /etc/apt/preferences /var/lib/synaptic/preferences

```

And we can start the magic :D
```
sudo gedit /etc/apt/preferences
```
and input the following:
```

Package: *
Pin: release a=hardy
Pin-Priority: 1011

Package: *
Pin: release a=hardy-security
Pin-Priority: 1101

Package: *
Pin: release a=hardy-updates
Pin-Priority: 1001

```
Save and quit.

Then run:
```
sudo apt-get update
sudo apt-get upgrade
```
[EDIT]
OK, I have gotten through this procedure, and I have documented what happens and fixes.
1) **language-pack-en-base** fails upon configuring... this is OK, run
```
sudo apt-get install -f
```
To fix this and run upgrade again.
```
sudo apt-get upgrade
```
And wait for about 20-30 minutes for it to complete.

Once everything is finished, reopen the preferences file, and remove what you everything you put in.
```
sudo gedit /etc/apt/preferences
```

Now reboot and pray :)
[SIZE="3"]
**BE SURE TO BACK EVERYTHING UP FIRST BEFORE ATTEMPTING THIS SENSITIVE PROCEDURE**[/SIZE]

If it works, you will probably find yourself with a few extra unneeded packages from intrepid still, such as the 2.6.27 kernel. You can choose to **purge** these packages if you prefer the 2.6.24 instead.

Regards
Iain

---

### Post by bodhi.zazen on 2008-11-15
Thank you tinivole.

I tried this on a test system, using Virtualbox 32 bit guest.

The pinning and down grade went fine, but the downgrade was not complete, and the resulting system was not "normal". By that I mean if you open synaptic and update ("Mark all upgrades" -> apply) the system will remove critical parts of the system.

So I would caution that while initially pinning and downgrading "works", the downgrade is not perfect and the resulting  system is a bit touchy, to say the least.

---

### Post by speeddemon8803 on 2008-11-15
thank you for the information tinivole and the warning bodhi.zazen.

---

### Post by Steve1961 on 2008-11-15
> **speeddemon8803 said:**
> thank you for the information tinivole and the warning bodhi.zazen.

yes, i was aware of this method but tried it myself several years ago on a Debian system.  It took so long to repair the resulting mess that unless you really know what you're doing it takes much longer than a simple backup and reinstall.

---

### Post by AlanInVancouverBC on 2008-11-21
If I use WUBI to dual-boot with XP, and I've installed Ibex, would there be a difference if I reinstalled Heron? How would I reinstall Heron?

---

### Post by bodhi.zazen on 2008-11-21
> **AlanInVancouverBC said:**
> If I use WUBI to dual-boot with XP, and I've installed Ibex, would there be a difference if I reinstalled Heron? How would I reinstall Heron?

I would remove ibex and install over the top.

---

### Post by AlanInVancouverBC on 2008-11-23
In the end, I just searched which WUBI to use for 64-bit 8.04.1 Ubuntu and downloaded it and installed it. Of course, unlike 8.10, internet worked right away, graphics worked right away (my 2 main problems). I'll wait for others to experiment with later releases, like 9.04 (Jackalope?) rather than download install and freak on the first day, prior to learning that a distro is so buggy!

---


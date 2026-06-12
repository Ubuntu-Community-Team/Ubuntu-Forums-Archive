---
title: "dumb question cannot find synaptic"
date: 2018-06-05
forum: New to Ubuntu
---

### Post by bodhin2 on 2018-06-05
trying live 18.4 before i install to check stuff out.  i looked all over the place but do not see any synaptic app tool to add or remove apps?  i just saw the updater.  what am i missing please.

---

### Post by Dennis N on 2018-06-05
You can search for 'synaptic' by typing into search box on the activities overview screen. But, since it is not included in the default installation of Ubuntu 18.04, it is probably not on the live media either.

---

### Post by Frogs Hair on 2018-06-05
Search for the software application where you can install synaptic and other applications.

---

### Post by bodhin2 on 2018-06-05
ok thank you.  how come it is not part of it?  it seems like a crucial piece of software - endemic to most of the deb/ubuntu distro's i have used.

---

### Post by Frogs Hair on 2018-06-05
Synaptic hasn't been a default application for quite a while.

---

### Post by bodhin2 on 2018-06-05
hmmmmm....???? i have not been around ubuntu since it first came out.

---

### Post by Frogs Hair on 2018-06-05
> **bodhin2 said:**
> hmmmmm....???? i have not been around ubuntu since it first came out.

This is the case with many other Linux distributions as well. The software store model seems to be the trend.

---

### Post by bodhin2 on 2018-06-05
:-))))

---

### Post by ajgreeny on 2018-06-06
As a long time user of the *ubuntu family of OSs synaptic is the first package I now add if it's not already installed, as it is, I believe, in Lubuntu.

I'm not sure it is now being developed much further which I find disappointing, but probably inevitable in this age of software stores.  Software stores, however, can not in my limited experience do all that synaptic can.

---

### Post by bodhin2 on 2018-06-06
thanks.  i use it for adding and removal of unwanted stuff.

---

### Post by Morbius1 on 2018-06-06
So let's say I've been using only Windows since forever and I want to share some folders in my new Ubuntu desktop with other machines in my home network. I learned from my grandmother's hairdresser that I need to install someting called samba. So I go to Ubuntu Software and search for "samba". I get two results:

**smb4k**
That is a KDE application and is used to connect to a folder on another box not share one of my own folders and since I'm not a KDE user the offering is useless.

**Samba**
That looks promising but it is not the samba server package it is a GUI for administering it ( system-config-samba ). Oh, and by the way it was written for Version 3 of samba not the current version 4 of samba and ... um ... after you install it it doesn't run.

Search for samba in synaptic and you will get a mess of option but one of them is ... well ... samba and it's description looks like this:
> Samba is an implementation of the SMB/CIFS protocol for Unix systems,
providing support for cross-platform file and printer sharing with
Microsoft Windows, OS X, and other Unix systems.

Yep, that's it.

---

### Post by bodhin2 on 2018-06-06
ok appears that VLC is not available in search running live and also no synaptic.  so maybe it is available when i install.  sorry for all of the dumb questions - just trying to scope out some stuff before i install.  it is a big deal for me when you count on your computers and also when you know enough to be dangerous and also as an old fart too.

---

### Post by #&amp;thj^% on 2018-06-06
Even when using the Live medium before you install>> you will still need to run "**sudo apt update**" to populate the software available to you. :)
And from there you can perform search's from the Terminal with "**apt search vlc**" or "**apt search synaptic**" long story short "**apt search <your package here>**"

---

### Post by bodhin2 on 2018-06-06
ok thanks.  hoping to find time to install the next few days and tweak to get it all happening.  just have so much outside work to get done here. small homestead but a lot of work.

---

### Post by rsteinmetz70112 on 2018-06-06
You man need to add some repositories to find those applications as well.

---

### Post by bodhin2 on 2018-06-06
ok so how do i do all of this please!i need to get synaptic.  badly

---

### Post by #&amp;thj^% on 2018-06-06
Do you now have a installed system, or is this for the future when you get around to installing one.
Lets not put the cart in front of the horse for now if the later is the case. :)

---

### Post by bodhin2 on 2018-06-06
installed and updating and transfered files already

ok did a search and synaptic package manager came up so i am installing - seems to be ok will try it in a moment

seems to work fine so far. deleted firefox.  downloaded gimp just now to so not sure about these repos.  seems to be straghtforward

---

### Post by #&amp;thj^% on 2018-06-06
I do admire your enthusiasm! 
Just bear in mind we are all just volunteers here, and come from timezones all across this big world of ours. So sometimes patience is required when asking for for support.
Enjoy your time spent here.

---

### Post by bodhin2 on 2018-06-06
thanks - sorry have limited time to redo 3 laptops....  2 have to be exact duplicates for myself.

so far i am most impressed.

---

### Post by danthonyd on 2018-06-08
Do you mean Synaptic Package Installer?

---

### Post by bodhin2 on 2018-06-08
yes and found it days ago.  thanks.  new to this new ubuntu dynamic.

---

### Post by oldos2er on 2018-06-10
Would you please mark this thread 'Solved'? It both helps others who may have a similar problem, and helps prevent others wasting time answering. Thanks.

---

### Post by deadflowr on 2018-06-10
FYI,
Live sessions do not normally have all repositories enabled.
So packages not in the default Canonical [Main] repository might not be listed.
To enable other repository sources open the software sources in the Software center (inside the Edit menu) and enable those which are not already enabled.
(You can also open software sources directly through the Software and Updates program)
(You can usually enable the community [universe] and software restricted [multiverse]; ignore the restricted repository, as anything you want to install on a live session here would get wipe out before you ever had a chance to use it.)
then when you close software sources, let it do a reload. (it should ask if you want to do that)
After that most packages should show.

I expect if it asks for a password just leave it blank press enter.
The live session default user should have sudo rights and the ability to run sudo without a password.
(At least you can run sudo in a terminal in a live session without a password, so I would assume the same is true of a gui, 
the last time I tried it did or I'm delusional and I was doing something else)

If I'm wrong about the password ability in a gui, then you can enable extra sources in a terminal like so
```
sudo add-apt-repository universe && sudo add-apt-repository multiverse
sudo apt update
```

Sorry if this is a day late and a dollar short.

Hope it makes sense

---

### Post by bodhin2 on 2018-06-10
yes it does and thanks - also sorry about marking stuff solved - thought i did.


p.s. so far all is working rather sweetly!

---

### Post by oldos2er on 2018-06-10
Sorry if my last post appeared rude, it wasn't intended that way.

> sorry about marking stuff solved - thought i did.

No problem, thanks!

---

### Post by Topsiho on 2018-06-10
Except for installing all updates first, synaptic is the first program that I install after a new installation:
sudo apt install synaptic.
It is far more easy and fast to use than using the software store.
Topsiho

---

### Post by bodhin2 on 2018-06-10
oldos2er - we're good.

---

### Post by deadflowr on 2018-06-10
> It is far more easy and fast to use than using the software store.
Not sure about easier.
Better and faster, sure. But easier?

---

### Post by Topsiho on 2018-06-10
Yes, easier :) I'm dead sure of that. For one, one can search by name in synaptic.
In the store, that is true, one can browse and see what one likes to install.
And so things always have two sides.
But still: easier, for me. I almost never use the store.
Topsiho

---

### Post by deadflowr on 2018-06-10
I'm looking at easier in terms of steps it takes to install a basic package
the software store, for all it's warts, only takes 3 steps.
Find package
click install
enter password

---

### Post by bodhin2 on 2018-06-10
as ad hoc moderator - let's play nice!!!!!


(sorry could not pass that one up!)   just kidding.  proceed!

---


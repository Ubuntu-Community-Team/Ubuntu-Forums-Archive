---
title: "How to actually get the latest stable proprietary Nvidia drivers?"
date: 2015-02-23
forum: New to Ubuntu
---

### Post by garycheng12 on 2015-02-23
I did some brief googling and there seems to be so many ways to get and update Nvidia drivers--I see people adding one of the options: "nvidia-current/nvidia-current-updates", "x-swat", "xorg-edgers", etc. but I don't know the differences. I know that there's Nouveau drivers, unified, drivers, etc. but  I read that proprietary tends to be better if you want to take advantage of the graphics card (which for my purposes I need to). I also don't want experimental versions--I just want the latest stable one that you would get from Nvidia.
 
1. Is there an official PPA from Nvidia such that I can always ensure that my graphics driver is up-to-date without me having to download directly from Nvidia page and install manually? Or anything that would allow me to automatically update to the latest stable driver via apt-get update and apt-get dist-upgrade? Step-by-step instructions for 9300 M GS (GeForce) graphics card would be ideal.

2. Any tips/recommendations I need to know when I update the entire distro (or anything regarding maintaining the system)? I read that you have to purge and then do something.

Thanks.

---

### Post by dino99 on 2015-02-24
The diver is 340.76 for the 9300M chipset. Depending on the ubuntu release used, you can install it from archive via synaptic for example, or get it via xorg-edgers ppa (then deactivate that ppa as you does not need the other provided packages)

---

### Post by garycheng12 on 2015-02-24
Yea, I know I need the 340.76 driver, just not sure if xorg-edgers is the right ppa for me since I think it contains experimental (not stable) drivers too. Also, do I have to specify which package to install (like a package for 340.76)? If so, then this process isn't really automated since I would have to look at Nvidia's page to see if a newer driver is released. Not sure if what I'm looking for is possible--does xorg-edgers release stable Nvidia drivers as soon as it's available from the Nvidia page? Is the driver from xorg-edgers 100% identical to the one downloaded from the Nvidia page?

---

### Post by dino99 on 2015-02-24
340.76 is not an "experimental" one; so why all your questions ? but i agree with you, its not automated, you have to understand what you are doing  :lolflag:

---

### Post by deadflowr on 2015-02-24
> Is the driver from xorg-edgers 100% identical to the one downloaded from the Nvidia page?
More or less, it's closed-source driver so they are not allowed to tweak it.
How well the two match up between xorg-edgers and the nvidia site's probably depends upon time of release.
I would expect some lag between when nivida makes it available and when it comes to the ppa.
Other than that, they should be the same. Or at least right now they are.

The only real difference between them is the installation packaging mechanicism.
Ubuntu repackages it to install through Ubuntu's standard debian packaging way.
Where as nividia releases them typically as simple run-install scripts.
(Or at least they did the last time I downloaded from nvidia)

But the end result driver is the same.

---

### Post by grahammechanical on 2015-02-24
System Settings>Software and Updates has a box labelled "proprietary drivers for devices (restricted)." If we tick that box we will get updates to proprietary video drivers as and when the Ubuntu developers consider them stable enough to be pushed out to Ubuntu users.

I consider the word "stable" to be an illusion. What Nvidia considers stable others would consider untested at best and experimental at worst. The Ubuntu developers can do nothing to fix what is wrong with proprietary drivers. The best the Ubuntu developers can do is to push any bug reports up to the owner of the driver. This is why Additional Drivers does not offer us the so-called latest and greatest from a manufacturer.

There is an easy way and a hard way. Ubuntu gives us the easy way. Linux lets us do it the hard way if that is our choice. I do not think that apt-get would update a proprietary driver if we have not ticked the box "Proprietary drivers for devices (restricted)." It most likely will update a proprietary driver if we installed it from a PPA and the PPA was still enabled. But then we would become an experimenter.

Regards.

---

### Post by garycheng12 on 2015-03-09
Newbie question: what is actually my process when accomplishing this? For example, do I:

1. Add ppa: xorg-edgers
2. Go to Nvidia website to find out the latest "stable" driver available from the website? <- is there no better way to do this?
3. Go to xorg-edgers page and search if a package for that version exists and its package name
4. apt-get install <packagename determine from step 3>?

Do I need to do anything thing else such as disable the PPA? I read that you shouldn't do a full update from the PPA (how do you do a full update from a PPA and am I doing it when I do steps 1-4) because it will pull in other irrelevant updates that could mess with your trackpad, etc. However, on the xorg-edger's page, they warn users not to install individual packages as it could mess up with dependencies, etc. They also highly recommend that ppa-purge be used if upgrading Ubuntu--why is this necessary?

---

### Post by JeQhdMD on 2015-03-09
Why not just go with Graham's suggestion?  Use the USC (Ubuntu Software Center OR Synaptic) to update your video drivers for Nvidia or AMD/ATI.   There should be no need to get the latest versions of MOST software anyway, just as Corporations will go with standard drivers, modules and programs for years (my company only updated from Office 97 in about 2007 for example).   ONLY if your hardware is not working properly is there a need for a PPA.   95% of he software in the USC will remain at the set original versions for 5 years (having only security or bug updates - - which Canonical will push down to you).

---

### Post by monkeybrain20122 on 2015-03-09
> **garycheng12 said:**
> Newbie question: what is actually my process when accomplishing this? For example, do I:

1. Add ppa: xorg-edgers
2. Go to Nvidia website to find out the latest "stable" driver available from the website? <- is there no better way to do this?
3. Go to xorg-edgers page and search if a package for that version exists and its package name
4. apt-get install <packagename determine from step 3>?

Do I need to do anything thing else such as disable the PPA? I read that you shouldn't do a full update from the PPA (how do you do a full update from a PPA and am I doing it when I do steps 1-4) because it will pull in other irrelevant updates that could mess with your trackpad, etc. However, on the xorg-edger's page, they warn users not to install individual packages as it could mess up with dependencies, etc. They also highly recommend that ppa-purge be used if upgrading Ubuntu--why is this necessary?


Use the ppa. it has the latest (with perhaps a only few days lag after Nvidia new releases) Install the driver and whatever update it pulls in (doesn't have to be all the updates, just those you need for the driver) then disable the ppa. When the next Nvidia driver is released, enable the ppa, then update the driver(along with the dependencies), then disable it again. xorg-edgers update very often, you probably don't want to keep updating. This can be done very easily using synaptic instead of the Software Centre to manage your software (install it with the software centre of 'sudo apt-get install synaptic')

Install ppa-purge in case the ppa gives you problem and you need to reverse your action by downgrading packages you have installed from ppa.

DON'T Install the .run file from Nvidia unless you know what you are doing or looking for troubles. Use xorg-edgers.

Finally I disagree with always sticking to Ubuntu provides. New driver usually brings improvements or bug fixes. "stability" just means predictable, which may mean predictably broken. Anyway with ppa-purge you can try out different drivers (or clone your root partition before proceeding if you have  separate / and /home partitions)

---


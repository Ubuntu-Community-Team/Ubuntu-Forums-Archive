---
title: "Using xorg-edgers (and PPAs in general) vs. .run installation: apt-pinning?"
date: 2015-03-16
forum: New to Ubuntu
---

### Post by garycheng12 on 2015-03-16
I learned that there are 2 methods to getting* latest stable* Nvidia proprietary drivers and have questions regarding both methods:

**1. via PPA:**

```
sudo add-apt-repoistory ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-343

```
Questions:

Apparently there's more you have to do after running these commands--otherwise you get additional updates that could screw up touchpad, etc. Why does this happen and what is causing that to happen? I was under the impression that after adding a PPA and doing sudo apt-get install nvidia-343, if I were to do a normal sudo apt-get update/upgrade to upgrade my system in general, it would not do anything to nvidia-343 or the xorg-edgers PPA, since *the only package I installed from xorg-edgers was nvidia-343 and nvidia-343 is a package of its own *(meaning nvidia-343 won't upgrade to nvidia-344 since nvidia-344 is itself a different package).

Why is it necessary to disable the PPA? 

 xorg-edgers specifically warns against installing individual packages, but isn't that what many xorg-edgers users doing when they do the above method?

See: [http://askubuntu.com/questions/302930/install-all-xorg-edgers-updates](http://askubuntu.com/questions/302930/install-all-xorg-edgers-updates), relevant to all the questions I've asked above.

**2. via .run installation file from Nvidia website**

Questions: 

Readme file say to simply run file with ./<name_of_file>.run, yet when I did some googling, others state .run files can cause dependency problems and a whole range of other problems. What are these potential problems and why do they occur? 

Try to be as specific as possible--I want to be aware of potential problems and things I can do about it. This isn't really about installing graphics drivers but more about installing applications on Ubuntu in general. Thanks.

---

### Post by dino99 on 2015-03-16
Ubuntu packaging follow some rules, like having sometimes strict versioned dependencies for some packages. If a 'non' ubuntu package(s) is installed , it can have some different versioned dependencies, and so can conflict / break the already installed ubuntu packages. (that's what the 'askubuntu' link posted above explain)

---

### Post by grahammechanical on 2015-03-16
> [COLOR=#000000]to getting[/COLOR]* latest stable Nvidia proprietary drivers *

I would not describe the latest video drivers from the manufacturers web site or from a PPA like xorg-edgers as "stable." Certainly not in the New to Ubuntu section of this forum. It could mislead new users. The Additional Drivers utility gives Ubuntu users the latest stable drivers as decided by the Ubuntu developers. When we install by another method we are moving to the edge. That is what the name xorg-edgers means - xorg to the edge.

I took the xorg-edgers advice not to install packages individually to mean that I should use the PPA as that will provide all necessary components of the drivers. Whereas, I may not get satisfactory results if I install each of those components individually rather than as a driver package.

Some developers provide up-dates through their PPAs. Most do not and if we do not disable the PPA then we will get error messages from Update Manager about something being wrong with our internet connection. Not only that when it comes to upgrading Ubuntu to the next release we need to downgrade from what the xorg-edgers PPA installed to what is default in Ubuntu otherwise = broken OS.

> [COLOR=#111111][FONT=Verdana]*IMPORTANT NOTICE* - If you are upgrading from one release to another and are using this PPA, be sure to install ppa-purge and use it to downgrade all of this PPA's packages before the upgrade or you will have a broken system.[/FONT][/COLOR]

[http://www.ubuntuupdates.org/ppa/xorg-edgers](http://www.ubuntuupdates.org/ppa/xorg-edgers)

Personally, I think it is safer to upgrade using the open source video driver than using a proprietary video driver. Many come on this forum to say that they upgraded and on the re-start could not get to a working desktop. I suspect proprietary video driver problems.

Who knows what is in a .run file? Only the person who created it. Is that not a problem in itself?

> [COLOR=#333333][FONT=Ubuntu]Careful consideration must be put into place whenever installing anything outside of the official repositories. Run files install software into the system via a script rather than a package manager. Verify that the run file you obtained came from a source that you trust before executing it.[/FONT][/COLOR]

[https://help.ubuntu.com/community/InstallingRunPackage](https://help.ubuntu.com/community/InstallingRunPackage)

It was to avoid problems that packaging protocols were written and package managers were created. But as Ubuntu is Linux we can choose to live on the edge if we want.

Regards

---

### Post by buzzingrobot on 2015-03-16
OK, my specific advice is avoid using video drivers from PPA's on machines you expect to be reliable.

If you don't need proprietary drivers, I recommend not installing them. If you do want to install them, stay with the drivers provided by Canonical, which will be shown in Additional Drivers.  Those drivers may not always be at Nvidia's or AMD's very latest version bump.  But, the very latest version may or may not include anything useful to you. (Specifics about what's changed in each version bump are available at each vendor's site.)

(Failed proprietary driver installs need to be removed and backed out cleanly and completely before trying another driver. That's tedious and problematic.  'Additional Drivers' handles it quite well, and that's another reason to use it.)

*All* packages in all PPA's are unoffical and unsupported.  At a minimum, one should read any warning and advise provided at the PPA's page. xorg-edgers says this:

> This PPA is currently meant to be used as a whole. Please do _not_  individually install packages from it, add it to your sources and let  your package manager pull in every update.  

Anytime you use a PPA to install untested unoffical software, you're taking on a potential risk.  If the package you're installing also installs other unofficial, untested dependencies, your risk increases. It's not that difficult to blithely overwrite core components. Sometimes nothing happens.  Sometime something breaks.  Often, in my experience, an update down the road breaks due to unresolvable dependencies.

Breakage often occurs when a machine using a proprietary driver, from any source, gets a kernel update.  Historically, it's common to reboot into a black screen.  Specific reasons vary, but Nvidia and AMD develop their Linux drivers apart from the mainstream of Linux development and release their work as simply binary files.  Bugs introduced, or revealed, in the drivers due to kernel changes need to be fixed after-the-fact. Ditto new drivers running on current kernels.

---

### Post by garycheng12 on 2015-03-16
Yea, I already understand the risks--trading some instability for some potential performance increases. If ubuntuforums cannot provide the help I need because PPA is too dangerous for a newbie, where can I find the answers to the ones I asked? I already tried AskUbuntu and got no answers. Maybe reddit?

---

### Post by dino99 on 2015-03-16
> **garycheng12 said:**
> Yea, I already understand the risks--trading some instability for some potential performance increases. If ubuntuforums cannot provide the help I need because PPA is too dangerous for a newbie, where can I find the answers to the ones I asked? I already tried AskUbuntu and got no answers. Maybe reddit?

well , everything is already explained
then it is up to you to take time to understand that

---

### Post by garycheng12 on 2015-03-16
I already glanced over the Ubuntu documentation and I see nothing about xorg-edgers, which people on UbuntuForums recommend for* those who want latest stable proprietary drivers (I already understand the risks) *over manually running .run files from Nvidia. I stated my problem with xorg-edgers, the first method, which is:

Why would the PPA continue to pull updates or do anything that would add additional, potentially uneccessary packages that could mess up touchpad, etc. if all I needed is "nvidia-343" and the implications of only adding the PPA and installing "nvidia-343" *without disabling the PPA*. As well as other questions listed in my original post.

As for the second method, via .run installation from Nvidia website, most people say just to run the .run file and you're set. On the Ubuntu documentation, much more needs to be done and it* recommends to not use this method, but says nothing about xorg-edgers, the alternative*. What I want to know for this method is *why* it is not recommended, which buzzingrobot says is because of untested dependencies that could mess up the system. I want to know why the xorg-edgers PPA (or PPAs in general) wouldn't have this same problem, since many people use PPAs that are trusted (such as Firefox beta PPA and other popular applications with official PPAs).

I understand that people on this forum tend to be automatically hostile toward any method that requires more work and is less stable than the default repositories offered by Ubuntu, but the Ubuntu documentation itself states that: "Sometimes using the drivers in the Ubuntu repositories is not the best option" and I am having some performance issues which I want to see if it can be fixed through xorg-edgers method.

---

### Post by buzzingrobot on 2015-03-16
If you ignore the guidance and advice given by the people who maintain the PPA and build and install their packages on their hardware, and choose to follow the ad hoc, anecdotal advice of random forum posters who may or may not have systems similar to your system... I think you're making a mistake.

People recommend doing 'X' because it worked for them in their specific circumstances. But, the basic point is that PPA packages are not supported.  Whatever happens, you're on your own.

If a system update delivers a kernel or any other package that breaks a package from any PPA, then you're on your own until the PPA maintainer(s) decide to fix their packages.  That may or may not happen.

 Packages from the officials repos will pull in the dependencies they need from the official repos, and some effort has been taken to ensure nothing breaks.  Packages installed from PPA's pull in the dependencies they need from that PPA, from other PPA's, from the official repos, or from any other source listed in the files in /etc/apt. The only place they've been tested to see if they work is on the PPA maintainers' systems. (And its presence on the PPA is no guarantee a package works on any system.) If a PPA package needs a dependent package that breaks a package from an official repo, or breaks a system update at some point due to unresolvable dependencies,  the fix is down to the PPA maintainers or you. *You*, not Canonical and not the PPA maintainers, get to fix things when they break.

Running applications from PPA's is likely to be less problematic because they don't supply core functionality to a system. Note, too, that just because someone slaps "official' on their PPA that doesn't make it an official and supported source of Ubuntu packages.

---

### Post by garycheng12 on 2015-03-16
> **buzzingrobot said:**
> If you ignore the guidance and advice given by the people who maintain the PPA and build and install their packages on their hardware, and choose to follow the ad hoc, anecdotal advice of random forum posters who may or may not have systems similar to your system... I think you're making a mistake.

People recommend doing 'X' because it worked for them in their specific circumstances. But, the basic point is that PPA packages are not supported.  Whatever happens, you're on your own.

If a system update delivers a kernel or any other package that breaks a package from any PPA, then you're on your own until the PPA maintainer(s) decide to fix their packages.  That may or may not happen.

 Packages from the officials repos will pull in the dependencies they need from the official repos, and some effort has been taken to ensure nothing breaks.  Packages installed from PPA's pull in the dependencies they need from that PPA, from other PPA's, from the official repos, or from any other source listed in the files in /etc/apt. The only place they've been tested to see if they work is on the PPA maintainers' systems. (And its presence on the PPA is no guarantee a package works on any system.) If a PPA package needs a dependent package that breaks a package from an official repo, or breaks a system update at some point due to unresolvable dependencies,  the fix is down to the PPA maintainers or you. *You*, not Canonical and not the PPA maintainers, get to fix things when they break.

Running applications from PPA's is likely to be less problematic because they don't supply core functionality to a system. Note, too, that just because someone slaps "official' on their PPA that doesn't make it an official and supported source of Ubuntu packages.

Thank you.

---

### Post by monkeybrain20122 on 2015-03-16
> **garycheng12 said:**
> 
Why would the PPA continue to pull updates or do anything that would add additional, potentially uneccessary packages that could mess up touchpad, etc. if all I needed is "nvidia-343" and the implications of only adding the PPA and installing "nvidia-343" *without disabling the PPA*. As well as other questions listed in my original post.


Because by adding a ppa you add all its packages to your sources and apt-get upgrade would pull in the highest version available. Therefor even if x is not related to the package you need (e.g Nvidia-343) but it is in the ppa and has version higher than the version Cannocial provides apt-get upgrade would pull in the the version from the ppa.

As for xorg-edgers' warning my understanding is that you should **install all the updates related to the package needed,** - as opppose to downloading the .deb from its archive and install it separately,--not that you should necessary update all available packages whenever they are pushed out. Hence disabling the ppa afterward.

As buzzingrobot said if you install with the .run file, chances are you may not have the dependencies from the official repo because their versions are not high enough, but with the ppa you fetch those dependencies from the ppa instead of the official repo and the maintainers are supposed to make sure that they are of the correct versions.

ppa that a lot of people use tend to be very safe and more people will be filing bugs to the maintainers if something doesn't work. If the problem is due to packaging they tend to get fixed and updated very fast, much faster than the official channel which typically would be available only for the next Ubuntu release, if  you don't want to upgrade the whole OS you can only pray that the fix would be backported.

---

### Post by oldos2er on 2015-03-16
If you're looking for stable I'd try the x-swat PPA instead of xorg-edgers: [https://launchpad.net/~ubuntu-x-swat/+archive/ubuntu/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/ubuntu/x-updates)

---

### Post by garycheng12 on 2015-03-16
Happy to see someone that directly addresses my questions.

> **monkeybrain20122 said:**
>  Therefor even if **x** is not related to the package you need (e.g Nvidia-343) but it is in the ppa and has version higher than the version Cannocial provides apt-get upgrade would pull in the the version from the ppa.


Assuming that **x **was installed on the system, right? For example, you would *only* get additional, unnecessary packages that are unrelated to the PPA *if * these unnecessary packages are installed as a newer version of packages *already installed on the system.* Meaning you *would not *get additional, unnecessary packages if your system did not have these packages installed in the first place.

> **monkeybrain20122 said:**
> 
As for xorg-edgers' warning my understanding is that you should **install all the updates related to the package needed,** - as opppose to downloading the .deb from its archive and install it separately,-**-not that you should necessary update all available packages whenever they are pushed out. *Hence disabling the ppa afterward.***


So (to clarify) not disabling the PPA and doing sudo apt-get update && sudo apt-get ugprade would update all packages pushed out that are *newer versions of packages already installed on the system* which could result in a problem I mentioned earlier about messing up the touchpad. And it would only make sense to disable the PPA *before* I do sudo apt-get upgrade. Is there not a whitelist I can do (or something to that effect) for a package (in this case, nvidia-343) of a PPA that would ensure that the rest of my system would not be affected in an unpredictable way where having a random additional update because the PPA's version of a package is newer than the system's installed version would cause problems like messing up the touchpad? 

Thanks your for patience.

> **oldos2er said:**
> If you're looking for stable I'd try the x-swat PPA instead of xorg-edgers: [https://launchpad.net/~ubuntu-x-swat/+archive/ubuntu/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/ubuntu/x-updates")

Yea, I saw x-swat PPA but I'm not sure if it would matter which PPA I use for my specific purpose, since I'm assuming nvidia-XXX is available on both x-swat and xorg-edgers. If someone can tell me why I would prefer x-swat over xorg-edgers *even for my specific* *purpose*, then I can understand more about PPAs. This would help me understand the questions I posed within this post.

---

### Post by mc4man on 2015-03-16
> **garycheng12 said:**
> 


I'm still not entirely sure why the PPA should be disabled if I only need nvidia-343. If I do sudo apt-get update && sudo apt-get upgrade, why would I be updating all available packages whenever they are pushed out? Wouldn't I only be upgrading the packages I installed from the PPA, which in this case is nvidia-343 and which wouldn't be receiving any updates since a potential nvidia-34**4** is a new package itself that nvidia-343 would not upgrade to?

Thanks your for patience.
Personally if I was to use that ppa I'd leave it  enabled & upgrade all, probably with a dist-upgrade.
But putting that aside when you do an upgrade or dist-upgrade with that ppa enabled then you'll get all your currently installed packages that are also in the ppa as higher versions  upgraded. That includes libdrm & mesa source packages which aren't "additional, unnecessary packages " , quite the opposite. Any issues from that ppa  generally are related to those 2 sources. 

So here if a full upgrade from that ppa broke something like touchpad support I'd file a bug on it, then use ppa-purge on the ppa until it was fixed. 

If you just want the newer nvidia drivers then install them & dump the ppa.

---

### Post by garycheng12 on 2015-03-16
> **mc4man said:**
> 
When you do an upgrade or dist-upgrade with that ppa enabled then you'll get all your currently installed packages that are also in the ppa as higher versions  upgraded. That includes libdrm & mesa source packages which aren't "additional, unnecessary packages " , quite the opposite. Any issues from that ppa  generally are related to those 2 sources. 

So here if a full upgrade from that ppa broke something like touchpad support I'd file a bug on it, then use ppa-purge on the ppa until it was fixed. 

If you just want the newer nvidia drivers then install them & dump the ppa.

Thanks for the clarification.

It would only make sense for me to disable the PPA *before*  I do sudo apt-get upgrade at any time in my case, right?

 Is there not a whitelist I can do (or  something to that effect) for a package (in this case, nvidia-343) of a  PPA that would ensure that the rest of my system would not be affected  in an unpredictable way where having a random additional update because  the PPA's version of a package is newer than the system's installed  version would cause problems like messing up the touchpad?

---

### Post by mc4man on 2015-03-16
In this specific ppa's case I'd totally trust the ability of ppa-purge to restore back to a pre ppa state. (they wrote the ppa-purge app.
So from that perspective there is nothing to lose trying it..
I'd enable the ppa, install ppa-purge,  update sources & go sudo apt-get -s dist-upgrade 
If the sim looked good then redo apt-get  without the -s , reboot & check out. If not liking the result then simply - 
sudo ppa-purge xorg-edgers

---

### Post by garycheng12 on 2015-03-17
Thanks, all.

---

### Post by pappo2 on 2016-02-03
I tried using the ubuntu-x-swat repository.  It installed fine using apt-add-repository, but when I ran apt-get update on my wily release, I get 404 not found.
If I use my browser, I can got to the launchpad.net site and see it just fine, but it doesn't like the 15.10 wily

Any ideas ?

---

### Post by oldfred on 2016-02-03
Changes are why it is best to use newest instructions or start a new thread if issues. This should be the preferred PPA now.

 Ubuntu Launches Its "Fresh" Proprietary Driver PPA - August 2015
[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
See notes on current suggestions:
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

# purge any other ppa's first.

 # Shows standard repository versions
ubuntu-drivers devices
sudo apt-add-repository ppa:graphics-drivers/ppa
# should show newest versions available in addition
ubuntu-drivers devices
sudo apt-get update && sudo apt-get install nvidia-3xx

[URL="https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa"]
[/URL]

---

### Post by monkeybrain20122 on 2016-02-04
> **pappo2 said:**
> I tried using the ubuntu-x-swat repository.  It installed fine using apt-add-repository, but when I ran apt-get update on my wily release, I get 404 not found.
If I use my browser, I can got to the launchpad.net site and see it just fine, but it doesn't like the 15.10 wily

Any ideas ?

I think x-swat has been abandoned. If you look at the page the last update was 113 weeks ago. Either stick to xorg-edgers or use the new ppa from above (I think it only has the driver so there will be less stuffs to install and update) 

To clarify  mc4man has a point for keeping xprg-edgers ppa enabled because some potential dependency problems may arise. But still I would recommend disabling the ppa after installing the driver.

Scenario where disabling the ppa may be problematic (probably what mc4man has in mind): you try to install package y but y is not installable when the ppa is disabled, that is because y depends on z, but not just any z, it has to be the right version to match with the version of y in the repo. However you have higher version of z installed from the ppa so it is out of sync with y in the repo. In that case the maintainer of the ppa should provide a version of y that matches its version of z. So to install y you need to re-enable the ppa.

 That sometimes happens especially if you compile your own software but otherwise is rare. So IMO I would rather disable the ppa to avoid frequent updates of key parts of the graphic system and just re-enable it if needed.

---


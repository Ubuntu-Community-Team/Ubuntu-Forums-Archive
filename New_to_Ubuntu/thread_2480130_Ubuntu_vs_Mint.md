---
title: "Ubuntu vs Mint"
date: 2022-10-20
forum: New to Ubuntu
---

### Post by tmgfigueiredo on 2022-10-20
A few years ago (more than 5 years) I used Ubuntu, and I confess that I  liked it. Later stopped using it, due to the compatibility of the  software I use regularly. So I became a regular Windows user.

Today I want to go back to Linux with dual boot windows. Obviously I'm  very tempted to go back to Ubuntu, but I've seen that Mint has been in  pretty good shape. So I come here to the forum, asking users to convince  me "in a minute"  [IMG]https://forums.linuxmint.com/images/smilies/icon_lol.gif[/IMG] that Ubuntu is a better choice than Mint, and why!

Thanks

---

### Post by guiverc on 2022-10-20
**For Linux Mint**

Visually I do like Linux Mint. They have some great wallpapers, and some of their configs I've found useful. Out of the box I find Linux Mint very impressive.

On my primary box (*a refurbished box where I always use it for awhile before I clean & install the OS I intend using*), I installed Linux Mint to use it for the weeks where I *evaluate** and test* the box before I use & trust it for my own purposes. I liked the configs that much that I actually didn't *clean* install (ie. no format), but just manually erased the *runtime adjustments, package history *and other things I didn't want to survive into my used system, then *unclean* install (ie. installed over where existing files were left untouched, *manually installed *packages get auto-reinstalled back (*I'd prevented this with my deletes though!*).

If you don't like *snap* packages and don't want to use them; a Ubuntu install mandates you disable those post-install; where installing Linux Mint has this already done. They have a number of these like *tweaks* that can save time.

Linux Mint uses many packages unchanged from Ubuntu, and thus can rely on Security checks performed by the Ubuntu Security Team directly; Linux Mint having no equivalent security team.

**Against Linux Mint**

Linux Mint isn't a full distribution, they rely on Ubuntu packages to make their system works. This has consequences.

Linux Mint *devs* don't have upload privileges to Ubuntu repositories they rely on, giving them the choice of building all packages themselves (*costly resource wise to build, host etc*) and they've chosen to rely on packages Ubuntu provides, and add an extra layer of software on their system - **runtime *adjustments***.  The consequence of this is adding extra security holes to their system, extra resources required by the extra layer of software, and problems can occur whenever upstream (ie. *Ubuntu is upstream of Linux Mint*) make changes as Ubuntu doesn't consider the runtime *adjustments* in their testing, thus also a reliability issue can occur. Linux Mint opted to improve reliability by using a lower security model in the past. To deal with this reliability issue, Linux Mint have a balancing act of reducing-security/increasing-reliability as a consequence of their reliance on upstream packages.  Thus there is added risk, is it a big risk; in my my opinion NO, but it's still a risk, problems can occur, and I've chosen to avoid that risk & those problems. (Note: *this paragraph is skipping a few details; ie. Linux Mint have varied their focus over time; & you didn't mention a specific release or time period*) 

(*I've used Linux Mint before; and not just for testing, and kept running into  reliability issues... the system works well if you use it a certain why, but personally I've found Debian & Ubuntu, neither of which rely on hacks/runtime-adjustments to be far more stable, and I know security is higher on Debian & Ubuntu. I'm likely not a typical user, and my systems tend to be very bloated (with many DEs; something Linux Mint doesn't deal with as well as Ubuntu, Debian though does better than Ubuntu!**)*

Far more packages in Ubuntu get security checks by [Ubuntu Security Team]("https://wiki.ubuntu.com/SecurityTeam") alas not all packages; ie. does not extend to community sourced packages (*but on the plus side it's super easy knowing which do & which don't*).

Ubuntu has more support sites; eg. sites like [askubuntu ]("https://askubuntu.com/help/on-topic")allow questions about *supported* releases of Ubuntu and *flavors*, but not systems like Linux Mint. There is a far larger community of Ubuntu users meaning far faster support should you need it.

[B]Other items

[/B]Even if you don't like *snap* packages & will disable them, *tweaks* such as disabling them are easily done (*search online and pick one of the 100+ pages telling you how to do it; you'll even find some listed on Planet Ubuntu!*) thus I don't see it as a big issue. Besides, having *snap* packages just allows your box to use a different package format giving you more options, more choices - to me that's a benefit !

I'm using a 2008 dell desktop right now; ie. hardly a high-powered box, but it runs all Ubuntu releases well out of the box. Sure I prefer the *lighter flavor* desktops, firstly as they're *lighter*, *faster*, but also its just my tastes. [Ubuntu offers a number of *flavors*]("https://ubuntu.com/desktop/flavours").

Linux Mint have had their web site hacked, have had their ISOs *tainted/replaced* and served for a short while before the problem was detected & stopped. This has **not**happened with Ubuntu where security is dealt with better (*Ubuntu has a company [Canonical] plus the community, and thus far more resources behind it!* *thus hardly a surprise*).

---

### Post by Dennis N on 2022-10-20
Unless things have changed, Linux Mint does not offer the Gnome desktop (which Ubuntu uses).

---

### Post by ActionParsnip on 2022-10-20
Try it. See what you think.

---

### Post by tmgfigueiredo on 2022-10-20
I already did! both to be honest. I did like the workflow of both. Of course not as an heavy user, because the learning curve is slow, for a guy who have worked with Windows for years! But I would like to "invest" in something for using a long time. What I'm trying to understand, is the pros and cons of both!

---

### Post by tmgfigueiredo on 2022-10-20
By the way, how much space do you think i should reserve to Mint, and don't have problems with space or performance issues.

---

### Post by tmgfigueiredo on 2022-10-20
Should 50Gb be enough for Ubuntu? our should I increment to 100GB?

---

### Post by yancek on 2022-10-20
20-30GB should be enough for Mint or Ubuntu if you have a separate /home or /data partition for personal files unless you intend to install a lot of software.

---

### Post by guiverc on 2022-10-20
The recommended minimum for Ubuntu Desktop is 25GB; though I am for 32GB for my / as I tend to have space problems with less than that. We all use our systems differently though, using different software etc.

It'll depend on what packages you intend adding to your system, what types of packages etc.. Only the owner/operator of the machine will know what they'll use it for, what software they'll need, or if the software that comes included is all they'll need.

 If you don't upgrade regularly; you'll need space to download the accumulated upgrades; then they'll get installed one by one, with the cleanup & return of free disk space occurring only at the end; ie. the more regular the maintenance the less disk space required to be kept free. Are you going to *upgrade via re-install* or do a *in-place release-upgrade*, as the in-place system upgrades requires disk space to download the newer release packages, then space to install then, before older packages are removed & space can be reclaimed. If you *nuke & install* none of that required free space is required.

Consider what you'll use the machine for, how you'll use it, now and into the future. We all have different requirements, as we use our systems differently.

[SIZE=1]*FYI:  I need more disk space than most as I worry mostly about what's in RAM, not really the disk, and like that I can login to a different desktop for a change, or because I'll use specific apps one session which perform best (most efficiently) when they can share resources with a desktop/toolkit. I still use devices with only 1GB of RAM so that's what I consider most critically. If you have more RAM  than the 8GB I usually use, disk space may matter more than RAM.*[/SIZE]

---


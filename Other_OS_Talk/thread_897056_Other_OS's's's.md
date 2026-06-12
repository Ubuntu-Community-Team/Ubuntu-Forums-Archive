---
title: "Other OS's's's"
date: 2008-08-21
forum: Other OS Talk
---

### Post by adobrakic on 2008-08-21
Is there another OS you guys would recommended? I'm sick of dealing with bugs on ubuntu every time I log in. Okay, well not EVERY time, but it's still a nuisance.

Perhaps downloading the previous version of Ubuntu may be better, since it's been out for a long time.

Any ideas?

---

### Post by Mhurst1 on 2008-08-21
Debian Stable is virtual bug free, but you might have to configure some things to work properly.

---

### Post by dmizer on 2008-08-21
Moved to "Other OS talk".

---

### Post by cardinals_fan on 2008-08-21
I enjoy Slackware.

---

### Post by y6FgBn)~v on 2008-08-21
Quite a few people here on the forums seem to like Arch. It might be something you would like.

---

### Post by adobrakic on 2008-08-21
I'll google those two and see how they look. Thanks guys.
And sorry for posting in incorrect forum, i have absolute beginners bookmarked. :x

---

### Post by PegMonster on 2008-08-21
It depends on your interests and capabilities.

Gnome, KDE, XFCE?

Are you comfortable with building it yourself or do you want to install it and log in to all the bells and whistles.

Package management preferences?

I would go to the top 10 major distro list at Distrowatch.com and start there.
[http://distrowatch.com/dwres.php?resource=major]("http://distrowatch.com/dwres.php?resource=major")

You are likely to get good support and information on all of those listed.


PegMonster

---

### Post by adobrakic on 2008-08-21
To be honest with you, I really have no idea what a good part of that means. :X

I like Ubuntu, it's just it has a lot of little bugs that piss me off. I like the repository, gui, memory usage, etc. Just the little things really bother me.

--edit--

Slackware looks good imo. based on my system specs, what would be best for me?

735MB RAM
1.7ghz processor
32mb video

---

### Post by PegMonster on 2008-08-21
As far as I am aware, just about anything Slack based is pretty light on the resources.

But Slackware itself is quite a bit more hands on than Ubuntu. So configuring your system is more of a challenge if you are not used to it.

But Slack does have many good derivatives, may be you should try those first.

They will be a bit more user friendly if you aren't up for the challenge.

e.g

Slax
Wolvix
GoblinX
Zenwalk
Vector

And there are plenty more


PegMonster

---

### Post by adobrakic on 2008-08-21
I'll google those when I'm done reading for my history classes, and see which one i like.

thanks for the advice.

---

### Post by PegMonster on 2008-08-21
You're welcome :)


Just keep in mind that they are not Ubuntu, so you will have to learn how to do things differently.

PegMonster

---

### Post by zmjjmz on 2008-08-21
I've tried GoblinX and Wolvix, both were pretty awesome.

---

### Post by cardinals_fan on 2008-08-21
SLAX is total win.  Install it and slapt-get, then sync with the 12.1 repos.

Wolvix looked nice, but never booted for me.  Vector is solid.  Zenwalk has had a few rough spots lately, but is still a great distro.

---

### Post by adobrakic on 2008-08-21
> **cardinals_fan said:**
> SLAX is total win.  Install it and slapt-get, then sync with the 12.1 repos.

Wolvix looked nice, but never booted for me.  Vector is solid.  Zenwalk has had a few rough spots lately, but is still a great distro.

I'm downloading it now, and burning the iso image to a CD for installation.

Before I do that though, how do i synch with the 12.1 repos?

---

### Post by PegMonster on 2008-08-21
I can't help you with that one, but I would install slapt-get (and gslapt if you want a gui front end, similar to synaptic) and read the manuals.

Gslapt should have some drop down menus with help files, I would think.

It may even give you a selction of mirrors to chose from, like synaptic does.
I'm only guessing though.

You might as well have a crack at it, I don't think you will break your system, as long as you follow the instructions.


PegMonster

---

### Post by wolfen69 on 2008-08-21
> **Mhurst1 said:**
> Debian Stable is virtual bug free, but you might have to configure some things to work properly.

amen. stable as a rock, but not the latest and greatest. and more configuring involved. a second mention goes to mandriva one. great kde based distro.

---

### Post by cardinals_fan on 2008-08-21
> **adobrakic said:**
> I'm downloading it now, and burning the iso image to a CD for installation.

Before I do that though, how do i synch with the 12.1 repos?
Install the slapt-get and gnupg packages manually.  Then type "slapt-get -u" and, when it's done, "slapt-get -i *package*" and "slapt-get --upgrade" to upgrade packages.

As far as installing SLAX, follow the instructions quoted below (from the SLAX forums):

> Hmmm my fault, the Slax installer isn't in Slax6, I put it back into mine version. I've uploaded it here :

[http://backtrack.serveftp.com/backtrack/misctools/slax6-install.kmdr](http://backtrack.serveftp.com/backtrack/misctools/slax6-install.kmdr)

Its a kmdr script, so download it to where you want, say /usr/share/slax/, then run it using the following :

```
/usr/bin/kmdr-executor /usr/share/slax/slax6-install.kmdr
```

Ignore the portion on the "live" version install, use the "real" version install.
NOTE: Make absolutely certain that you wipe and create a new partition for SLAX, because the installer won't do that for you (it'll happily install inside another distro, mixing the two and making a mess).  Cfdisk is included on the CD.

Technically, Slackware is better for installation (it's actually made to install, while SLAX is designed as a live CD).  However, going the SLAX route requires far less downloading and jump-starts you with a fully functional system right off the bat.  It provides a genuine Slackware system with a bit less work.  Just remember that it was designed as a live CD first, installed OS second.

---

### Post by init1 on 2008-08-22
> **adobrakic said:**
> Is there another OS you guys would recommended? I'm sick of dealing with bugs on ubuntu every time I log in. Okay, well not EVERY time, but it's still a nuisance.

Perhaps downloading the previous version of Ubuntu may be better, since it's been out for a long time.

Any ideas?
Yeah I have the same problem. Debian Etch is extremely stable and reliable though. However, Lenny should be coming out in a few weeks so maybe you should wait for that

---

### Post by philinux on 2008-08-22
> **adobrakic said:**
> I like Ubuntu, it's just it has a lot of little bugs that piss me off. I like the repository, gui, memory usage, etc. Just the little things really bother me.


In the meantime before you switch, what exactly are the little bugs?

---

### Post by adobrakic on 2008-08-23
- My firefox randomly closes on pages with flash on it 
- streaming videos is extremely slow / lags in full-screen 
- keyboard doesn't always get recognized and i have to restart the computer so i can even use it 
- can't get surround sound to work (although i doubt i'm going to get it to work with any other distro)
- firefox also sometimes closes when i try to make streaming videos full-screen

and basically i get a bug that i have to workout like once a week. i mean, i get it fixed and everything, but it's just annoying. also, i'm sure there's some that I forgot that will come up sooner or later

for example yesterday i couldn't download/install/uninstall anything because of some file that messed something up while i was uninstalling kde, there was a bug report on it and a fix available, luckily. and then last week everytime I tried playing something in XMMS, it said that the device was already being used and that i should choose a different output plugin or something. i was annoyed so i just clicked a bunch of stuff and fixed it, even though i dont really want it to be like that.. but i'm not as savvy with linux as i am with windows so i can't tell what the problem was.

---

### Post by Twitch6000 on 2008-08-23
> **adobrakic said:**
> To be honest with you, I really have no idea what a good part of that means. :X

I like Ubuntu, it's just it has a lot of little bugs that piss me off. I like the repository, gui, memory usage, etc. Just the little things really bother me.

--edit--

Slackware looks good imo. based on my system specs, what would be best for me?

735MB RAM
1.7ghz processor
32mb video
You might Like Linux Mint Version XFCE.

Linux Mint usually can fix anything that Ubuntu has not.
It also is in some ways like Ubuntu yet in many others different.

---

### Post by adobrakic on 2008-08-23
I'll do some research on slax & linux mint. actually, i saw linux mint recently and was thinking of switching to it.

also, to add to my list of bugs (which just happened now):
- i can't delete some file from my trash. says i don't have permissions or something.
good thing its like a 5kb file and not a 500mb file.

---

### Post by PegMonster on 2008-08-23
>  i can't delete some file from my trash. says i don't have permissions or something.

File needs to be deleted as root, or it's permissions changed so 'user' can delete it.

See this post-

[http://ubuntuforums.org/showthread.php?p=5647680#post5647680]("http://ubuntuforums.org/showthread.php?p=5647680#post5647680")


PegMonster

---

### Post by Seventh Reign on 2008-08-23
I wouldnt mind hearing what some of your favorite "lesser" known distros are.  The kind that might not even be in Distrowatches top 100.  Or atleast outside of the top 50.

Myself .. I've fallen in love with Workbench and OpenGEU 8.04.1.  Even tho they're both Betas.

---

### Post by cardinals_fan on 2008-08-23
> **Seventh Reign said:**
> I wouldnt mind hearing what some of your favorite "lesser" known distros are.  The kind that might not even be in Distrowatches top 100.  Or atleast outside of the top 50.

Myself .. I've fallen in love with Workbench and OpenGEU 8.04.1.  Even tho they're both Betas.
SliTaz is awesome.  I couldn't get it working with my printer/NVIDIA card, but it's a nice distro.

---

### Post by Seventh Reign on 2008-08-23
SliTaz is tucked away with my other 79 CD/DVD's.  The Interface and color scheme took some getting used too, but for a 25mb CD you cant beat it.

---

### Post by sub2007 on 2008-08-23
> **pcybill said:**
> Quite a few people here on the forums seem to like Arch. It might be something you would like.

Arch is excellent but not for a bug free system. It doesn't have a lot of bugs, but inherently will have some as it is rolling release and new versions of packages are rolled out constantly. It's not like using a testing repository - they are only released when stable but occasionally there could be some bugs and so for anyone looking for an ultra stable, bug free system it's not a good choice. It's great if you want a stable (because it's certainly not unstable) and constantly up to date system.

---

### Post by adobrakic on 2008-08-23
Damnit, there are so many distros, i dont know which to choose. :/

---

### Post by LateNiteTV on 2008-08-23
freebsd.org

---

### Post by adobrakic on 2008-08-23
I just went to walgreens and got some CDRs so i can put a new OS on my computer. is it possible to just put this OS over ubuntu, instead of formatting the whole harddrive? Because I got windows on here also, and i dont wanna have to re-install that.

Also, it's either Linux Mint or Freebsd. What do you guys think?

---

### Post by Shippou on 2008-08-23
Linux Mint Elyssa. Works fine for me.

Don't worry. It is Hardy Heron based.

---

### Post by adobrakic on 2008-08-23
Yeah, I'm burning Elyssa onto a cd-r now. i noticed it's a rc, hopefully it doesnt have too many bugs.

--edit--

I'm burning it at 1x speed, so i have a little time to ask some questions. :p

is there anyway i can save my firefox profile and transfer it, once I'm on linux mint?
I have a bunch of saved passwords, bookmarks, extensions, etc. that i REALLY don't wanna get again.

---

### Post by wolfen69 on 2008-08-23
if you're downloading an RC, you're not downloading the main edition. xfce and kde are rc. the main gnome edition is final.

---

### Post by adobrakic on 2008-08-23
oh damnit, i already burned the rc one. :(!(!(

XFCE Community Edition RC1 (BETA 025)  	XFCE

that's the one i downloaded. should i get:

Main Edition (revision 1)  	Gnome  	CD  	691MB

?


--edit--

wait, no i'm confused.

i went to here: [http://linuxmint.secsup.org/5/](http://linuxmint.secsup.org/5/)
and downloaded "LinuxMint-5-r1.iso". Is this right?

---

### Post by adobrakic on 2008-08-24
im typing this from linx mint. :D

if i have questions, could i ask here, or should i go to the linux mint forums?

---

### Post by eeezzzeee on 2008-08-24
You could definitely ask for help here in the Ubuntu forums, but if you are using Mint you may as well go to the Mint forums too. It's a small but very friendly community.

---

### Post by adobrakic on 2008-08-24
Alright, sounds good. Liking this already. :D

---

### Post by zmjjmz on 2008-08-24
Not sure if it's too late, but if you get the .firefox (or is it .mozilla) folder from ~, you can copy it over and that will transfer your settings.

---

### Post by adobrakic on 2008-08-24
Yeah, it's too late haha. I couldn't wait to switch over to this last night. :X
But thanks for the advice anyway. :D

---

### Post by doorknob60 on 2008-08-25
Debian, it's easy if you're comfortable with Ubuntu because you still can use apt-get to install stuff etc. IMO Testing is even more stable than Ubuntu, and Stable's packages are too old TBH (FF3 doesn't even run with its GTK version) but that'll change when Lenny goes to stable (happens pretty soon, forgot exact date), but I recommend Debian for sure, particularly testing, and try out KDE, it's a lot better and faster and more stable than Kubuntu :). EDIT: Dangit too late.

---

### Post by Seventh Reign on 2008-08-25
My Dyslexic 94 year old Grandmother could build an Operating System more stable than Kubuntu.

---

### Post by Seventh Reign on 2008-08-25
Ok here's one.

if Kubuntu = Ubuntu/KDE, and Xubuntu = Ubuntu/Xfce.
Which of the Enlightenment/Ubuntu systems would be #1?

So Far I've tried OpenGEU 8.04.1 Beta (currently installed)
OzOS (Liked it)
and gOS

---


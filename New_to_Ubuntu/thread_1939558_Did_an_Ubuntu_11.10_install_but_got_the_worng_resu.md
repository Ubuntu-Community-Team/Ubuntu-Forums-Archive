---
title: "Did an Ubuntu 11.10 install but got the worng result"
date: 2012-03-11
forum: New to Ubuntu
---

### Post by ClientAlive on 2012-03-11
Hi,

I just did an Ubuntu 11.10 install from an alternate install cd - thinking i was going to end up with a cli only system. What I actually have is the full blown system with Unity and everything. I'm really dreading this, but...

What is the easist way to strip everything down to cli only and not miss a single extra 'bit' ? Not a single orphan file laying around on the system. Is there some tool or something that can do this?

Doing a diff between what I have and an actual cli only 11.10 system crossed my mind but if I had a cli only system to do the diff agains I wouldn't have the problem in the first place.

What do I do?

---

### Post by alphacrucis2 on 2012-03-11
You probably wanted the server version rather than alternate CD.

---

### Post by wlraider70 on 2012-03-11
I would just re-install with the server version it has no gui. 

You should consider 12.04 it will be an LTS.

---

### Post by ClientAlive on 2012-03-11
> **alphacrucis2 said:**
> You probably wanted the server version rather than alternate CD.

err... Well I checked out the server version and wasn't too keen on some of the the way it's set up. I may have just missed some check box in this install or something... idk.

At any rate, I'm wondering if there is a way to generate a clear cut list of all things non - cli on the system. If there's a way to do that then maybe that same list can be used as the list of stuff to uninstall. Maybe even just pipe it into dpkg or something?

---

### Post by wlraider70 on 2012-03-11
What about the set up did you not like?

---

### Post by ClientAlive on 2012-03-11
> **wlraider70 said:**
> I would just re-install with the server version it has no gui. 

You should consider 12.04 it will be an LTS.

Thank you. Your advice is much appreciated but this is a route I just don't wish to go.

---

### Post by ClientAlive on 2012-03-11
> **wlraider70 said:**
> What about the set up did you not like?

Well, I really don't mean to get into a debate. This is just my humble opinion based on what I've seen and heard...

The sever version is optimized for server functions not regular user type functions. The...

You know, to tell you the truth, I'm really not sure whether it or the what I have would be better suited for my application. What I do know is I would be judging, first, by a performance standard, then a close second would be functionality. I know they set the timer interrupt lower on the server edition. One thing I know for sure is that getting an efi bootable system installed is absolute, torturous hell! I wouldn't wish that experience on my worst enemy and would certainly not like to go throught it again the 3 weeks.

What I need in this base system is really just s single purpose system. A stripped down, almost appliance like, host system to run quemu - kvm. I will need a couple front end tools for vm management so I'll probably have to have some kind of window manager. It may not need to big ol' bloatski x server though. I want to have as much of my system resources as possible going to the guests. I also need the host system to be as optimized as possible for this type of a job (I'm talking about i/o and network througput/ perforamance).

I'm not sure how much debate there is going on about what the 'best' timings and type of system is for something like this, but I could certainly stand to make a more informed decision. Glad you asked.  :)
--------------

Well, sure, here's some of what it says about the server edition...

> Kernel Differences:


 The Server Edition uses the Deadline I/O scheduler instead of the CFQ scheduler used by the Desktop Edition. 


Preemption is turned off in the Server Edition. 


 The timer interrupt is 100 Hz in the Server Edition and 250 Hz in the Desktop Edition.

[https://help.ubuntu.com/10.04/serverguide/C/preparing-to-install.html#intro-server-differences](https://help.ubuntu.com/10.04/serverguide/C/preparing-to-install.html#intro-server-differences)

For some reason that all strikes me as a system that would make running vm guests very unresponsive and sluggish.

---

### Post by Kirboosy on 2012-03-11
> **ClientAlive said:**
> Hi,

I just did an Ubuntu 11.10 install from an alternate install cd - thinking i was going to end up with a cli only system. What I actually have is the full blown system with Unity and everything. I'm really dreading this, but...

What is the easist way to strip everything down to cli only and not miss a single extra 'bit' ? Not a single orphan file laying around on the system. Is there some tool or something that can do this?

Doing a diff between what I have and an actual cli only 11.10 system crossed my mind but if I had a cli only system to do the diff agains I wouldn't have the problem in the first place.

What do I do?

Why not try a [Minimal Install]("https://help.ubuntu.com/community/Installation/MinimalCD") of Ubuntu? IT allows you to manually choose what packages you would like to use. I recommend having a fast internet connection though otherwise it might take a while to install as it grabs all the packages off the internet.

---

### Post by ClientAlive on 2012-03-12
> **Caboose885 said:**
> Why not try a [Minimal Install]("https://help.ubuntu.com/community/Installation/MinimalCD") of Ubuntu? IT allows you to manually choose what packages you would like to use. I recommend having a fast internet connection though otherwise it might take a while to install as it grabs all the packages off the internet.

I'm really very concerned about this uefi install thing. Perhaps my experience with it was not typical but what I went through to get what I have was really really extreme. I just don't want to chance not getting a clean install again.

I've been reading the dpkg man page and I see it is a very powerful tool. I'm not sure if it is able to calculate dependencies and make clean removals; but, if it can, I think my best option is to figure out the right commands to run with it to determine what needs stripped off and then use it to strip those things off.

If anyone knows the right way to go about this I would certainly appreciate the help.

Thanks
--------------

Edit:

What I'd like to do is see if there's a way to make dpkg differentiate between userspace apps, the window manager and de, and that sort of stuff - in a single command. I'd then like to take those results and see if I can use it to remove those packages including all their dependancies. I've been experimenting with "dpkg -l PackageName*" I also recall there being a way to use dpkg to clean up unused dependancies. What I envision is probably a 3 command process. (1) retreive a list of all installed packages that are non-base system (2) have it remove those packages along with their dependancies (but it could not remove dependancies for which other remaining packages would need), and (3) Either (a) use it to clean up all unused dependencies of (b) find and install any required dependencies that are no longer there (making sure it didn't take something away that's needed by another remaining package).

---

### Post by Kirboosy on 2012-03-12
The Ubuntu Minimal install CD is the cleanest and purist install of Ubuntu. The ISO is a whole whopping 23 Mb to download. I believe the only way to remove packages with DPKG is to manually specify the packages.

Another route would be to use [UCK]("http://uck.sourceforge.net/") to remove all the packages you do not wish to use and build a custom ISO of Ubuntu. The only hitch is you would need an existing Ubuntu install with a GUI (I believe) in order to use it.

---

### Post by ClientAlive on 2012-03-12
> **Caboose885 said:**
> The Ubuntu Minimal install CD is the cleanest and purist install of Ubuntu. The ISO is a whole whopping 23 Mb to download. I believe the only way to remove packages with DPKG is to manually specify the packages.

Another route would be to use [UCK]("http://uck.sourceforge.net/") to remove all the packages you do not wish to use and build a custom ISO of Ubuntu. The only hitch is you would need an existing Ubuntu install with a GUI (I believe) in order to use it.


Well I guess dpkg is not an option. From the dpkg man page...

> 
Warning:  At  present  dpkg  does  not  do any dependency
          checking on downgrades and therefore will not warn you if
          the  downgrade  breaks the dependency of some other pack&#8208;
          age. This can  have  serious  side  effects,  downgrading
          essential system components can even make your whole sys&#8208;
          tem unusable. Use with care.


I sure thought I'd seen a thread in the past where it was being used for something just like this. The person had accidentally gottan an unwanted upgrade on their server and it borked the server. he was asking how to revert it back to what it was before the upgrade and someone pulled some dpkg commands out of their hat. That was a long time ago I saw that thread. I must be mistaken in the way I remember it bc the man page doesn't lie.
------------------------

Edit:

You know, I would do the whole minimal install cd thing. Before I did though I would need to be certain of three things:

(1) I have a pretty complicated raid/ lvm setup on that machine. I would need to be sure it's going to handle those properly (including the fact that / is in a logical volume).

(2) That it uses the exact same insaller (with the catalog that allows it to boot in either UEFI or BIOS)

and (3) that the base system it does install isn't anything less than what's in the base system of the biggest baddest ubuntu out. In other words, not stipped down versions of packages but the real deal.

I could easily check (2) by simply burning the cd and looking in my firmware boot menu. If there is an entry for my optical drive with the prefix "uefi" then it will uefi boot. But (1) and (3) I"m not so sure of.

---

### Post by Kirboosy on 2012-03-12
> **ClientAlive said:**
> Well I guess dpkg is not an option. From the dpkg man page...



I sure thought I'd seen a thread in the past where it was being used for something just like this. The person had accidentally gottan an unwanted upgrade on their server and it borked the server. he was asking how to revert it back to what it was before the upgrade and someone pulled some dpkg commands out of their hat. That was a long time ago I saw that thread. I must be mistaken in the way I remember it bc the man page doesn't lie.
------------------------

Edit:

You know, I would do the whole minimal install cd thing. Before I did though I would need to be certain of three things:

(1) I have a pretty complicated raid/ lvm setup on that machine. I would need to be sure it's going to handle those properly (including the fact that / is in a logical volume).

(2) That it uses the exact same insaller (with the catalog that allows it to boot in either uefi or bios

and (3) that the base system it does install isn't anything less than what's in the base system of the biggest baddest ubuntu out. In other words, not stipped down versions of packages but the real deal.

I could easily check (2) by simply burning the cd and looking in my firmware boot menu. If there is an entry for my optical drive with the prefix "uefi" then it will uefi boot. But (1) and (3) I"m not so sure of.

The mini CD is simply core Ubuntu. It is the newest release available but the difference is it doesn't have any packages included on the CD. **However** any package normally available in Ubuntu via Synaptic or Software Center (in the repos) are readily available.

I do not know about the UEFI deal but I'm assuming it would use the same installer method as the Alternative CD.

---

### Post by ClientAlive on 2012-03-12
> **Caboose885 said:**
> The mini CD is simply core Ubuntu. It is the newest release available but the difference is it doesn't have any packages included on the CD. **However** any package normally available in Ubuntu via Synaptic or Software Center (in the repos) are readily available.

I do not know about the UEFI deal but I'm assuming it would use the same installer method as the Alternative CD.


Well the entry in my boot menu did show up (with the "uefi" prefix) so it's apparently capable of a uefi install. When I fire it up though I get the grub command line. What on earth am I supposed to do with that?

---

### Post by Kirboosy on 2012-03-12
> **ClientAlive said:**
> Well the entry in my boot menu did show up (with the "uefi" prefix) so it's apparently capable of a uefi install. When I fire it up though I get the grub command line. What on earth am I supposed to do with that?

If you hit Enter will it start booting?

Did you verify the CD  is valid using MD5?

---

### Post by ClientAlive on 2012-03-12
> **Caboose885 said:**
> If you hit Enter will it start booting?

Did you verify the CD  is valid using MD5?

I don't know but when I went looking for documentation on how to install that way I found the following:

> 
To install a base system, boot from any Alternate CD and choose "Install a command-line system."

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)


This led me to belive that the alternate install cd that I used is capable of a base system only install. That perhaps I just missed making the right selection before.

Thing is, when I boot that cd again (the alternate install cd) there is no main menu entry that anything like "Install a command-line system" like it says in the documention. Note that the quotation mars in the quoted (above) are in the original document.

There are only two sane chioces from the main many of the alternate install cd "Install Ubuntu" or Expert Installation (something very close to that - from memory). So I tried both selections thinking maybe the selection for "Install a command-line system" is in a later step. It doesn't appear to be and I can't go beyond the point where it would write anything to the drive (including any partition changes) until I'm sure about how this goes.

I should note that the reason I felt attracted to looking at the alternate install cd again is because of that raid/ lvm setup. I know for sure the alternate install cd will handle those things but I don't know whether the minmal install cd does. I have to be very carful about this. I'm not willing to lose a 4.4 and 1.5 TB raid arrays and their associate lvm stuff - the raid just takes too long to build (like all day).

---

### Post by Kirboosy on 2012-03-12
I understand. I have a server sitting in my house that has a 6 TB RAID 10 Array. If anything ever happened to that I would lose my mind. I haven't had a change to play with the shiny new UEFI motherboards. I am out of suggestions but I wish the best of luck to you. Hopefully you can figure it out 

[UEFIBooting Docs]("https://help.ubuntu.com/community/UEFIBooting")
[LVM Installation Guides]("https://help.ubuntu.com/community/Installation#LVM_Installation_Guides")

---

### Post by ClientAlive on 2012-03-12
> **Caboose885 said:**
> I understand. I have a server sitting in my house that has a 6 TB RAID 10 Array. If anything ever happened to that I would lose my mind. I haven't had a change to play with the shiny new UEFI motherboards. I am out of suggestions but I wish the best of luck to you. Hopefully you can figure it out 

[UEFIBooting Docs]("https://help.ubuntu.com/community/UEFIBooting")
[LVM Installation Guides]("https://help.ubuntu.com/community/Installation#LVM_Installation_Guides")

Thanks.

For the record... reinstalling with the alternate cd gave a me a trashed system that won't boot. Now there's a new boot entry in my firmware boot menu that I can't get rid of and suspect it may be playing a part in the carnage.

The mini.iso gives me a "grub>" command line, not a grub boot menu. That's just what it does and then I'm at a dead end with it.

I'm gonna try to get a full install back on there and do what I knew I should have done in the first place - remove the packages (one by one if I have to) until I'm down to just the cli base system.

No offense, I know you meant well, and it was I who made the choice.

Peace out man.

---


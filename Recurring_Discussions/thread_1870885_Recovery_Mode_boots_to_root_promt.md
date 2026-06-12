---
title: "Recovery Mode boots to root promt"
date: 2011-10-28
forum: Recurring Discussions
---

### Post by ranch hand on 2011-10-28
I want to file a bug on this as it is a security risk.

What is the package.  We used to be able to file against the package "ubuntu" as a generic but not anymore.

The old recovery menu was always a major security hole with the option of a root terminal.  Debian did away with that some time ago in favor of a test log in after the recovery boot up process.

Ubuntu has finally integrated this and removed that flaky menu too.  This is good.

They do not have a login at all though.  You just end up and a root prompt (#).  This is not good

So, what package am I filing this against.

---

### Post by cariboo on 2011-10-28
ranch hand, in Ubuntu this is considered a feature, instead of a bug. The often quoted reason, is that physical access is root access, which I tend to agree with. This is mainly because of the lack of the ability to set up a root account during installation, and even then with a live cd/usb, you still have access to everything, unless you encrypt the home directory.

---

### Post by effenberg0x0 on 2011-10-28
Logic says that once someone is at physical console, he is root anyway. Hell, one could crack the PC open and take the HDD away, plug a USB / CD with a OS and mount chroot, etc. 

But, when you consider implementations like schools, libraries, coffee shops, game / Lan houses, airport and bus grand stations, thin-clients, etc, the PC cases are generally locked inside metal boxes/racks that sometimes are even embedded in walls, etc. Only Monitor, mouse and keyboard are accessible. Giving away root access in this cases is not redundant, because there's no physical access to HDD or I/O ports. 

And in these cases, it would be nice for IT guys to not have just about anyone booting as root and formatting the machine every now and then... What I see in implementations, is that IT guys remove recovery from grub menu, try to hide grub as default, etc. But, anyway, one can access grub, edit the grub boot line and get root anyway, without much skills needed. I'm unaware of a bulletproof solution.

I'm not sure about the package. This is a security issue IMHO (no one wants to have a user getting root, even thou its local root, in a lan). But the boot process and grub should have options to avoid root access if configured to do that.

---

### Post by cariboo on 2011-10-28
On a public access system, you'd want to remove the option to boot into recovery mode from grub, or set the grub delay to zero.

---

### Post by MacUntu on 2011-10-28
I'd just make sure they can't reboot. :P

---

### Post by effenberg0x0 on 2011-10-28
> **cariboo907 said:**
> On a public access system, you'd want to remove the option to boot into recovery mode from grub, or set the grub delay to zero.

> **MacUntu said:**
> I'd just make sure they can't reboot. :P

There's a thing about users: They find a way.  

:)

---

### Post by ronacc on 2011-10-28
alt>sysreq>b

---

### Post by MacUntu on 2011-10-28
> **ronacc said:**
> alt>sysreq>b
```
# echo 0 > /proc/sys/kernel/sysrq
```
;)

---

### Post by ronacc on 2011-10-28
thanks I'll remember that .

---

### Post by tekstr1der on 2011-10-28
> **ranch hand said:**
> I want to file a bug on this as it is a security risk...

As stated by others this has long been accepted as the default behavior. It's very difficult to protect against physical access.

The first thing I do to mitigate the issue is to set a root password:

```
<snip>
```

I also make sure that my partitions are encrypted with cryptsetup/LUKS, so that even with root access to the system, my data would be secure were someone to remove the HDD and use another system to access it. They'd be SOL.

On top of that I also use a BIOS password and make sure the boot options do not include any USB, optical, or other external devices. On laptops, this typically is a very secure way to ensure that the system can't be booted to another OS such as a Live CD. Also, since there's typically no jumper to clear the CMOS on laptops, it requires an EEPROM reader to hack the BIOS password. This is well beyond the means of a typical laptop thief, I'd imagine. Encrypted data would still be safe anyhow, they'd just gain use of the system. Keep in mind this tactic is useless on a typical desktop computer where a jumper is normally available to clear the CMOS (and password along with it).

I remember you had been very studious with grub 2 and posted a lot of helpful information about it a few releases ago. You probably know that you can set a grub password as well. A good how-to is posted here:
[http://ubuntuforums.org/newreply.php?do=newreply&p=11401848](http://ubuntuforums.org/newreply.php?do=newreply&p=11401848)

I typically skip the grub password step, as the other 3 measures I've mentioned protect my laptop and data in the event of theft/loss. Without an EEPROM reader (and serious skills) or outright replacing the motherboard, the system is 100% useless to anyone who finds/steals it.

---

### Post by effenberg0x0 on 2011-10-28
Magic Sysrq is well know too within hax0rs.
**R**aising **S**kinny **E**lephants is **U**tterly **B**oring

A guy showed me one of this days he could use Windows debug.com to corrupt the BIOS. Then when you boot, you get a warning saying that settings are invalid, press something to enter setup. And you go in without a password... Probably easily doable too in Linux.

---

### Post by effenberg0x0 on 2011-10-28
> **tekstr1der said:**
>  it requires an EEPROM reader to hack the BIOS password. 

Depends... cmospwd cracks some of them beautifully. You can also use it to simply load bad cmos code and make the thing boot asking you to enter BIOS and setup defaults (no passwd)...

On Windows:
debug.com
o 70 10
o 71 20
quit
exit
Works for most award bios, some phoenix.

dmidecode dump + hexedit works too.

And there are a lot of other ways. One common way is to use a paperclip to short serial ports pins. Do that 3 or 4 times and the bios is corrupted.

---

### Post by tekstr1der on 2011-10-28
> **effenberg0x0 said:**
> Depends... cmospwd cracks some of them beautifully. You can also use it to simply load bad cmos code and make the thing boot asking you to enter BIOS and setup defaults (no passwd)...

On Windows:
debug.com
o 70 10
o 71 20
quit
exit
Works for most award bios, some phoenix.

dmidecode dump + hexedit works too.

And there are a lot of other ways. One common way is to use a paperclip to short serial ports pins. Do that 3 or 4 times and the bios is corrupted.

The windows/hex method are irrelevant if you can't boot an operating environment.

The paperclip method sounds handy if you really want to brick the thing for good!

---

### Post by tekstr1der on 2011-10-28
> **effenberg0x0 said:**
> Depends... cmospwd cracks some of them beautifully. You can also use it to simply load bad cmos code and make the thing boot asking you to enter BIOS and setup defaults (no passwd)...

On Windows:
debug.com
o 70 10
o 71 20
quit
exit
Works for most award bios, some phoenix.

dmidecode dump + hexedit works too.

And there are a lot of other ways. One common way is to use a paperclip to short serial ports pins. Do that 3 or 4 times and the bios is corrupted.

Hmm...seemed to have double-posted.

Anyway, I think that you (effenberg0x0) are missing the point of my post. I was letting the OP know the simplest way to alleviate his concern and also what further steps I take to ensure the safety of my data. This just boils down to encryption. The rest of the methods are done more out of spite to render the system useless if it falls into the wrong hands. If those wrong hands somehow have the skill to thwart my efforts, then they get to use the machine as their reward!

---

### Post by effenberg0x0 on 2011-10-28
> **tekstr1der said:**
> The windows/hex methods are irrelevant if can't boot an operating environment.

The paperclip method sounds handy if you really want to brick the thing for good!

Not at all. If you can corrupt the BIOS and get inside it, you can allow for USB/CD-ROM boot, run a tiny Linux Distro in any of these media, chroot to the main HDD and have fun.

There are tango diagrams online on how to short serial ports correctly. Some people make "keys", with resistors. Most simply short the thing a couple times until the BIOS pops on screen. 

On public PCs users couldn't care less about destroying the hardware or not.... Been there myself many, many years ago when life was still fun. 15 years old "I just read Alt2600-FAQ and I rock" vs Touchscreen machine that displays location of stores in Shopping Malls = hack it or break it.

---

### Post by effenberg0x0 on 2011-10-28
> **tekstr1der said:**
> Hmm...seemed to have double-posted.

Anyway, I think that you (effenberg0x0) are missing the point of my post. I was letting the OP know the simplest way to alleviate his concern and also what further steps I take to ensure the safety of my data. This just boils down to encryption. The rest of the methods are done more out of spite to render the system useless if it falls into the wrong hands. If those wrong hands somehow have the skill to thwart my efforts, then they get to use the machine as their reward!

Yes, I missed the point, you're right. 
@Ranch Hand Sorry man, didn't wanted to screw your thread :) Go with tekstr1der info.

---

### Post by ranch hand on 2011-10-29
> **tekstr1der said:**
> As stated by others this has long been accepted as the default behavior. It's very difficult to protect against physical access.

The first thing I do to mitigate the issue is to set a root password:

```
sudo passwd root
```I also make sure that my partitions are encrypted with cryptsetup/LUKS, so that even with root access to the system, my data would be secure were someone to remove the HDD and use another system to access it. They'd be SOL.

On top of that I also use a BIOS password and make sure the boot options do not include any USB, optical, or other external devices. On laptops, this typically is a very secure way to ensure that the system can't be booted to another OS such as a Live CD. Also, since there's typically no jumper to clear the CMOS on laptops, it requires an EEPROM reader to hack the BIOS password. This is well beyond the means of a typical laptop thief, I'd imagine. Encrypted data would still be safe anyhow, they'd just gain use of the system. Keep in mind this tactic is useless on a typical desktop computer where a jumper is normally available to clear the CMOS (and password along with it).

I remember you had been very studious with grub 2 and posted a lot of helpful information about it a few releases ago. You probably know that you can set a grub password as well. A good how-to is posted here:
[http://ubuntuforums.org/newreply.php?do=newreply&p=11401848](http://ubuntuforums.org/newreply.php?do=newreply&p=11401848)

I typically skip the grub password step, as the other 3 measures I've mentioned protect my laptop and data in the event of theft/loss. Without an EEPROM reader (and serious skills) or outright replacing the motherboard, the system is 100% useless to anyone who finds/steals it.
Yes, I agree completely.

My bios are password protected.

I use a custom menu entry with no recovery entry.

Grub is password protected to prevent editing of entries so that you con boot to recovery.

I do not have to disable sudo and set up a root password, I use Debian.

My next box will have physical security so that something like the removal of a drive will involve some mechanical adventure, perhaps even exciting adventure.  Why?  Because I think I can, even in a safe manner, while improving the cooling system quite a bit.

The installs that this crap is on are 4 Xubuntu 12.04-testing installs.  That are isolated from anything else on here.

This is not my point.  The point is just how much do you want to rebuild your system so that it is secure, particularly as a precious noob.

Just because these folks are new does not mean they are idiots.  Quite the contrary.  Many have switched because of security concerns.  Just how much of a build it your self OS are we trying to sell to this noob anyway?  There really are easier ways to to get a Linux OS that is noob friendly and does not, dispose of security measures no matter how "trivial" they may seem.

Let's see how far we can go to attracting the lowest literacy level of computer users.  It may be hard to believe, but a lot of folks actually research things before doing them.  This kind of stupidity is not the way to attract those folks.

I started this thread because I KNEW this was a bug.  There is no possible doubt that it is, no matter what Ubuntu and Canonical decide to label it.

The defense of this foolishness looks like another proof the man is a rationalizing animal.

---

### Post by cariboo on 2011-10-29
@ ranch hand, root access in recovery mode has been available in Ubuntu since I started using it in 2006, Now that you want to call us all dummies for using Unity, you've just noticed this?

---

### Post by MacUntu on 2011-10-29
> **ranch hand said:**
> I started this thread because I KNEW this was a bug.

The current state is intended, therefore by definition not a bug.

If you want real security, encrypt your system.

---

### Post by ranch hand on 2011-10-29
> **cariboo907 said:**
> @ ranch hand, root access in recovery mode has been available in Ubuntu since I started using it in 2006, Now that you want to call us all dummies for using Unity, you've just noticed this?
Yes it has.  It has also been talked about, in a more serious manner, in testing forums in the past.  Also in numerous other places.

The entire recovery menu and the option of having a root terminal came straight from Debian.

Now, at last, Debian has done something about it.  Not a terrible lot, but an improvement.

I am not talking about peoples choice of using Unity at all.  I am sure some actually like it.   I don't like KDE either.  This has nothing at all to do with that.

It does have a lot to do with Ubuntu and Canonical thinking that because there are always ways to get around a block to root permissions that there should be no blocks.  That is dumb.

Brute force attacks on ssh works too.  Let's just set the defaults for "open passwords yes" and "allow root login yes" as default.  Disabling all that silly key stuff would be a great idea too.

If there are any silly paranoid users they can always reset that too if it makes them feel any better for some ridiculous reason.

---

### Post by ranch hand on 2011-10-29
> **MacUntu said:**
> The current state is intended, therefore by definition not a bug.

If you want real security, encrypt your system.
I already encrypt what I need encrypted.

This is not the point.

Before I am, again, accused of being a "elitist guru", I would really like to know EXACTLY what the objection to some rudimentary security for noobs really is.

Is it too hard for them to type their user name and then a password?  It is assumed, I take it, that they can type "startx".

Is it then too hard, if they want a root prompt, to learn that "sudo su" is the command they want and then have to give the password again.

Just who is it here that figures that they are dumb.

I really like the concept that if someone has a reasonable concern that they need attacked.  I see that it is very popular and effective.

Yes I can, and you can, set up a system that is as secure as we feel like making it.  There really is no use in it, though, because someone could get your box, remove the HDD, and probably with time, break your encryption.  The idea of encryption is that by the time it is broken the information is useless.

All I am trying to say is DECREASING security improvements, no matter how small, that comes from upstream is not the brightest thing to be doing.

---

### Post by Thewhistlingwind on 2011-10-29
No offense, but physical access = root access.

Not even very hard either.

---

### Post by cariboo on 2011-10-30
Actually if the majority of new users had their way, there wouldn't need to be any passwords to be entered ever, could you imagine the uprorar if they had to set a root password and a regular user password?

If you look, you'll see a number of people have gone to the trouble of encrypting their home directory, then enabling auto login.

We can't spend all our time protecting people from doing stupid things, people have to take some responsibility themselves when administering their systems.

---

### Post by MacUntu on 2011-10-30
> **ranch hand said:**
> Is it too hard for them to type their user name and then a password?
What if their user is broken? It's called recovery mode for a reason.

> **ranch hand said:**
> Is it then too hard, if they want a root prompt, to learn that "sudo su" is the command they want and then have to give the password again.
Same as above, or: what if they've accidentally removed the package 'sudo'?

---

### Post by Elfy on 2011-10-30
Thread moved to Recurring Discussions.

---

### Post by ranch hand on 2011-11-02
I have let this go for a few days to cool off to the point that I could reply in cooled off manner.

Most of the responses here are from a very unrealistic view point.  They assume that the box in question is not only in a public place but a public place involving people of malicious intent that have more knowledge of Linux than the person using it.

This on the face of it is preposterous.  The odds, on which all security is based are against that environment.

Linux users are not a significant percentage of computer users no matter what we would like to believe.  Therefore the argument that physical access equals root access is simply wishful thinking.  I would go so far as to say that physical access does not equal root access in the case of a majority of posters on this forum if they are not carrying a cheat sheet with them.

A fairly significant number of posters here, perhaps as many as 10% do not know how to get the grub menu to show when they first post, let alone what the recovery mode is for.  I am sure that getting root access on my box is beyond their wildest dreams.

Now to the current state of recovery mode in Pretty ***** (12.04-testing).  The recovery script runs fine, does all its little extras very well.  Many times this is enough to get you to your desktop.

That means that all you need to do is type "startx" and you will, the way things are set up, be on a desktop as root.  This is not a good thing.

If you came to a user text login you would get to a user prompt ($) instead of the current root prompt (#).  If you then typed "startx" and got to a desktop you would be in as user, not root.  This would be a good thing.

If you did not end up on a desktop you would end up back at a user prompt.  If you did not know how to get a root prompt then you probably should not get one at all.

This is part of the minimal security that I am saying is needed on an OS that you want people new to Linux to be using.  They are, in fact, the biggest threat to their OS.

I do not think, from reading on this forum and helping folks straighten things out, that my experience as a noob in unique.  I KNOW that I was the biggest threat to my box.  I was very good at breaking things in my enthusiasm for the freedom I had to do so.  I still am, for that matter, but have gotten much better at doing it in a repairable way.

It is not "intuitive" (as if anything on a computer truly is, rather than just what we are used to) about "Ctrl + d" to get to the user prompt from a root prompt that comes up automatically and probably not recognized as such by may new users.  Nor is there anything, for those users that is "intuitive" about using "Alt + SysRq + b" to reboot the computer.

Actually at a root prompt that last should not be needed at all, simply typing "reboot" should do the trick.  Another thing that is not "intuitive".

If this is a feature instead of a bug it is a very badly thought out feature and a major security risk.  It is more dangerous than the old recovery menu that this fix, supplied by upstream (Debian), is supposed to improve on.

As implemented by Debian, it is an improvement.  You get a user text login.

Ubuntu has, it appears, spent time and effort to make an improvement into a regression.  Not a good thing.  Sounds, no matter what you call it, like a bug to me.

The knee jerk response to any criticism of "features" from Ubuntu, in these forums, I submit, has a lot more to do with the dropping forum usage (and loss of experienced testers), than the lack of a new theme or spam on here.

It could be that a little thought on this may be a good idea.

I can, much to the relief of the fanatic evangelists (fanboys) that appear to be in charge of policy here, assure you that I will never bring this, or any other, thought provoking subject up here again.

---

### Post by afrodeity on 2011-11-23
Recovery mode boots straight into root prompt, I have to telinit 3 to get back.

Since latest kernel update, I can't telinit anywhere.

---

### Post by Dangertux on 2011-11-23
> **Thewhistlingwind said:**
> No offense, but physical access = root access.

Not even very hard either.

This really just this.


Hexediting libs to break into bios is cool. Paperclips are cool. Recovery shells are cool. You know what they all have in common? You have to be sitting in front of the machine to do them.

If someone has physical access to a machine it's game over, period. Unless you are willing to use physical action to stop them from doing what they are planning on doing there is nothing you can do about it. Hence physical security. Locks, keys, logs and rosters, guards, cameras, and booby traps if need be.

This is one of those things that truly is a feature. Every single operating system I've ever seen has some sort of recovery mode, that allows you to easily bypass whatever authentication credentials are on the operating system. This is to secure against something like the disgruntled employee who decides to lock you out of a database. Anyone remember MS Access? How many scripts did you have to write to unlock an access database because someone got fired? 

I don't think the OP is going to get much attention to this "bug" because ultimately it's working as intended.

> **ranch hand said:**
> 
The knee jerk response to any criticism of "features" from Ubuntu, in  these forums, I submit, has a lot more to do with the dropping forum  usage (and loss of experienced testers), than the lack of a new theme or  spam on here.

It could be that a little thought on this may be a good idea.

I can, much to the relief of the fanatic evangelists (fanboys) that  appear to be in charge of policy here, assure you that I will never  bring this, or any other, thought provoking subject up here  again.

Also... Experienced testers don't really worry so much about a feature (despite what you call it) that has been around in multi-user operating systems since the 70's.

---

### Post by haqking on 2011-11-23
+1 To DT above.

Physical access is root access.

It is a feature not a bug.

The End.

---

### Post by gradinaruvasile on 2011-11-23
Hmm. What about temporary access to said computer?

The guy comes, pushes the button/removes cable (if the computer is running), logs in the recovery mode, copies/does whatever he needs/wants and thats all folks.

No physical opening-of-the-case, exploiting or cli-fu magic required, the back door is actually an unlocked front door, usable by anyone with minimal knowledge and minimal time. And the consensus here is that this is not a security issue.
Am i missing something?

---

### Post by haqking on 2011-11-23
> **gradinaruvasile said:**
> Hmm. What about temporary access to said computer?

The guy comes, pushes the button/removes cable (if the computer is running), logs in the recovery mode, copies/does whatever he needs/wants and thats all folks.

No physical opening-of-the-case, exploiting or cli-fu magic required, the back door is actually an unlocked front door, usable by anyone with minimal knowledge and minimal time. And the consensus here is that this is not a security issue.
Am i missing something?

your missing the fact that it is a feature and not a bug.

Physical access is root access, anyone malicious enough to do what you mention is likely to know or find out the multitude of other ways to also access things physically given the chance.

It is a dead end discussion to be honest, physical is root and always has been.

If you want to enable a root password then do so, it is your system and you are responsible for its security.

Linux/Windows/Mac all have an equal footing thereabouts when it comes to security certification so the rest is upto the user/admin.

Secure it the best way you see fit within the confines of your own need for ease of use and functionality.

Cheers

---

### Post by gradinaruvasile on 2011-11-24
So, if anyone asks about Ubuntu i should say - Ubuntu  it a very secure OS only that anyone can log in with the systems administrator account without a password. The maliciously inclined people must love Ubuntu for its security - they dont have to learn a damned thing about chrooting/other exploitation techniques, just use the unlocked back (ahem, front) door.

This should be on Ubuntu's feature list: "Admin access without providing password"

---

### Post by haqking on 2011-11-24
> **gradinaruvasile said:**
> So, if anyone asks about Ubuntu i should say - Ubuntu  it a very secure OS only that anyone can log in with the systems administrator account without a password. The maliciously inclined people must love Ubuntu for its security - they dont have to learn a damned thing about chrooting/other exploitation techniques, just use the unlocked back (ahem, front) door.

This should be on Ubuntu's feature list: "Admin access without providing password"

Most malicious people dont have physical access to the machine. So its not about not knowing anything about security.

And it is your job to secure it, if it bothers you so much enable a password if there are malicious people in your household.

If it is corporate it **should** already be secured anyways ? ;-)

---

### Post by Dangertux on 2011-11-24
> **gradinaruvasile said:**
> So, if anyone asks about Ubuntu i should say - Ubuntu  it a very secure OS only that anyone can log in with the systems administrator account without a password. The maliciously inclined people must love Ubuntu for its security - they dont have to learn a damned thing about chrooting/other exploitation techniques, just use the unlocked back (ahem, front) door.

This should be on Ubuntu's feature list: "Admin access without providing password"

Have you ever used runas to bypass UAC in Windows? It works quite nicely, also let's not forget the Windows recovery console. Also Mac OSX has the same thing as do most other Unix like Operating Systems. It's called single user mode.

Also -- chrooting is child root, it is designed as a security mechanism not a bypass for security mechanisms.

> **haqking said:**
> 

If it is corporate it should already be secured anyways

LOL -- you know better my friend :-P

---

### Post by haqking on 2011-11-24
> **Dangertux said:**
> 



LOL -- you know better my friend :-P

HA HA i did say should, i will go back and format that as bold ;-)

---


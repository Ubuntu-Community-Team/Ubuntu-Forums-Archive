---
title: "Physical access is root access"
date: 2007-04-20
forum: Recurring Discussions
---

### Post by NIKOSHIBA on 2007-04-20
hi everyone
fresh install 704 last night. starting up from GRUB in "recovery mode" brings me to root shell without even asking for a username and password!!!!!!!

---

### Post by MJN on 2007-04-20
That's because by default there isn't one...
 
Check the archives as this is becoming FAQ #1!
 
The bottom line is that whilst this may initially sound alarming think about it - if someone has got physical access to your machine to boot into recovery mode then they've got access to everything anyway (unless your disks are encrypted). Even with a root password they can easily boot with a LiveCD, change the password files, restart and they're in.
 
Mathew

---

### Post by NIKOSHIBA on 2007-04-20
> **MJN said:**
>  
The bottom line is that whilst this may initially sound alarming think about it - if someone has got physical access to your machine to boot into recovery mode then they've got access to everything anyway (unless your disks are encrypted). Even with a root password they can easily boot with a LiveCD, change the password files, restart and they're in.
 
Mathew
you got a point. but then again, why ask password and username at normal startup then? i think this is an a serious issue.
linux is all about security and stability. i think at install everything must be, as you have sad, encrypted. otherwise nothing much makes a sense.

---

### Post by jtc on 2007-04-20
Actually, security is a lot about prioritizes. To a lot of people the possibly to rescue a system with a LiveCD is more important then the extra locale security an encrypted drive gives you. In some environments, and especially on laptops, it might be a good idea to encrypt your harddrive. That doesn't make it so in every case.

Still, if someone has physical access to your computer there are always risks involved. By the way, if someone plugged in a small recording device between your computer and your keyboard, are you sure you would notice?

---

### Post by Cybergod on 2007-09-25
Below is a link that explains how to boot to a root shell without a password.  I was very surprised when I read this.  How could a Network/System Admin prevent users from doing this on their Workstation?

[http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html]("http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html")

---

### Post by /etc/init.d/ on 2007-09-25
Linux is primarily used on servers.  Imagine a server running Linux in a modern colo facility.  It's a high security building, you typically need swipe cards to get in, rooms are kept locked and the machine itself is in a locked cupboard.

Physical access is a low priority compared to say, securing running services that are facing the Internet.  If you install telnet and leave your system wide open, somebody can root you from a thousand miles away, but they can't get physical access.

That's why sysadmins and Linux distros in general typically think about remote security first.

---

### Post by Cybergod on 2007-09-25
> **/etc/init.d/ said:**
> Linux is primarily used on servers.  Imagine a server running Linux in a modern colo facility.  It's a high security building, you typically need swipe cards to get in, rooms are kept locked and the machine itself is in a locked cupboard.

Physical access is a low priority compared to say, securing running services that are facing the Internet.  If you install telnet and leave your system wide open, somebody can root you from a thousand miles away, but they can't get physical access.

That's why sysadmins and Linux distros in general typically think about remote security first.

Isn't the whole purpose of Ubuntu to bring Linux to the Desktop?  I understand what you are saying about servers, but I'm referring directly to the Desktop.

---

### Post by Brazen on 2007-09-25
This is the same as on Windows.  If you have physical access to a Windows PC, it is trivial getting admin access without a password.  You could add a root password on there, or Ubuntu could do it by default, but it would really be the illusion of additional security more than anything.

Just lock your doors and worry about remote threats.

---

### Post by koenn on 2007-09-25
> **Cybergod said:**
> Below is a link that explains how to boot to a root shell without a password.  I was very surprised when I read this.  How could a Network/System Admin prevent users from doing this on their Workstation?

you set a password on the root account with
```

sudo -i
passwd root
exit

```
that automatically protects the recovery mode by asking for a root password - if i remember well

It's useless unless you also
- password protect the grub menu, and lock the recovery menu item in it
- set the boot order in the BIOS to alwas boot Hard disk first or hard disk only (to prevent CD boots that circumvent your password protection
- password-protect the BIOS setup to prevent users from modyfing the boot order again. 

additional measures may include
- lock up the PC to prevent it from being stolen or its disks from being removed (or from someone inserting an alternative hard disk to boot from), or to prevent someone from hard-resetting the bios password

---

### Post by UbuWu on 2007-09-25
You can easily remove the recovery mode from the grub menu.

---

### Post by /etc/init.d/ on 2007-09-26
Here are some other tips though:

[LIST]
[*]Set a BIOS password.
[*]Disable booting from anything other than the HDD.
[*]Enable a HDD password if your BIOS supports it, this offers marginally better security than the BIOS password.
[*]Set a root password that is different from your other passwords using sudo passwd.
[*]Set a GRUB password.
[*]Hope that someone doesn't come up to the machine with a screwdriver, because you're hosed if they do.
[/LIST]

---

### Post by frodemt on 2008-03-20
Why am I able to start Recovery mode and logging in as root without even getting prompted for password? I feel this is insanly unsafe to have on a computer, but why?

---

### Post by munkyeetr on 2008-03-20
> **frodemt said:**
> Why am I able to start Recovery mode and logging in as root without even getting prompted for password? I feel this is insanly unsafe to have on a computer, but why?

I don;t know why, but follow the link in my signature to close that hole.

---

### Post by frodemt on 2008-03-20
Good guide you have there munkyeetr. I hope that this issue is adressed and taken seriously by Ubuntu developers. Right now I use BIOS password on my desktop and my laptop, but no password on my server. I wont have direct access to that server before june, so it will be open to attack until then.

---

### Post by mcduck on 2008-03-20
It doesn't really make any difference security-wise, but makes fixing some possible problem situations a lot easier.

The recovery mode requires physical access to the computer, and when somebody has that your security is already completely gone (unless you use encrypted file system or something).

When somebody has physical access to the machine he can access all your files by just popping in some live-CD and booting the machine with that and then mounting your disks from there.

BIOS passwords are pretty much useless as clearing them takes less than 30 seconds to do. Actually most new motherboards have a button or jumper for clearing CMOS settings, but if there is none simply removing the CMOS battery and cutting power from the machine for 15 minutes will do the trick.

Grub password is a bit better, but the live-CD way still works just as easily as with no password.

And last, if everything else fails, it's still possible to just open the case and take the hard disk out & move it to another machine and access your files that way.

If you want to secure your machine, the first rule is to keep everybody you can't trust away from the computer. If you can't do that, then disable booting from CD's and external drives in BIOS (or, even better, remove the drive completely), set BIOS password and GRUB password, lock the case and make sure nobody has enough time alone with the machine to break the lock.

---

### Post by hackertarget on 2008-03-21
Good post mcduck.

If you are a paranoid type - you could always go for full disk encryption.  Complicates matters if you lose your keys but at least it is safe. :)

---

### Post by p_quarles on 2008-03-21
Just to reiterate what mcduck said:

A password-locked single-user mode isn't going to make the tiniest bit of difference to any serious attacker.

---

### Post by aysiu on 2008-03-21
> **p_quarles said:**
> Just to reiterate what mcduck said:

A password-locked single-user mode isn't going to make the tiniest bit of difference to any serious attacker. Especially one who has physical access to your computer.

---

### Post by munkyeetr on 2008-03-21
It's still a hole that doesn't need to be there.

---

### Post by aysiu on 2008-03-21
> **munkyeetr said:**
> It's still a hole that doesn't need to be there.
No, it's not.

It's a way to rescue your system--that's why it's called *recovery mode.*

Perhaps it bears repeating--giving someone with a bit of technological knowledge physical access to your system **is** giving that person root access, whether *recovery mode* is a boot menu option or not, or passworded or not.

Mac OS X has this, too. If you press Cmd-S during boot-up, you boot into single-user mode, which is basically recovery mode.

If you want your data secure, don't give people physical access to your computer, and do encrypt your data. Otherwise, all you're getting is the illusion of security, like when my dad thought his fingerprint authentication on his IBM Thinkpad was so clever, and all I did was boot a Knoppix live CD on it and could see all his files--he was outraged that the "security" could be so easily bypassed. I had physical access to his laptop and thus had root access.

---

### Post by munkyeetr on 2008-03-21
Granted, someone with physical access and enough time can get by any security, or they could just remove the hard drive as has been stated, but...

At least with it password protected you are *requiring* someone to use a LiveCD (or similar boot method, which you can *slow down* by using a BIOS password)

At least with it password protected you are requiring more work and more time as opposed to less than 2 minutes it would take to reboot into recovery mode and run** rm -rf / ** I would be more worried about someone who wanted to quickly come in a wreck something, than someone who has hours to work at it. They are more likely to do damage just for damage sake. Someone who has hours, has time to dismantle your security and there isn't much you can do about that. With this **hole** there is something you can do about it.

And I don't know how you can say that providing root access without authentication of any kind isn't a hole? No matter how remote the chance, it is an opening, thus a hole in an otherwise secure system.

Suppose you had an internet cafe style setup with a dozen machines. You'd want to secure this up then wouldn't you?

You guys seem to really be taking offense to someone talking about this, or even questioning it. :confused:

---

### Post by aysiu on 2008-03-21
It's a simple difference of opinion as to what should be the default.

Ubuntu is not requiring that you not slow people down. It's just not defaulting to slowing down. If you have an internet cafe, you probably have the machines locked down behind a door in the desk, anyway, but you always have the option to add a root password, set a password in the BIOS, or implement other slow-down mechanisms. Ubuntu certainly cannot do anything about your BIOS.

In all honesty, I prefer the Apple approach to it. Don't have it simply be a menu item you can accidentally select, but make it some key combination you have to hold down to get into. This isn't for security reasons but usability ones. If a new user not familiar with the command-line happens to accidentally select recovery mode, she'll just be stuck at a root-privileged command-line with no idea what to type.

---

### Post by munkyeetr on 2008-03-21
And I personally think it should be secured by default, but like you say it a difference in opinion.

We can agree to disagree...for now! LOL :).

---

### Post by bhavi on 2008-03-22
> **aysiu said:**
> No, it's not.

It's a way to rescue your system--that's why it's called *recovery mode.*

Perhaps it bears repeating--giving someone with a bit of technological knowledge physical access to your system **is** giving that person root access, whether *recovery mode* is a boot menu option or not, or passworded or not.

Mac OS X has this, too. If you press Cmd-S during boot-up, you boot into single-user mode, which is basically recovery mode.

If you want your data secure, don't give people physical access to your computer, and do encrypt your data. Otherwise, all you're getting is the illusion of security, like when my dad thought his fingerprint authentication on his IBM Thinkpad was so clever, and all I did was boot a Knoppix live CD on it and could see all his files--he was outraged that the "security" could be so easily bypassed. I had physical access to his laptop and thus had root access.

I too agree with this.. Nice post and a detailed explanation.. 

Only if one has physical access to the system then its possible.. But Grub can always be protected with a password...

---

### Post by p_quarles on 2008-03-22
> **bhavi said:**
> Only if one has physical access to the system then its possible.. But Grub can always be protected with a password...
That is no more effective than a fingerprint reader. Booting from a removable disk will skip the hard disk's bootloader completely.

---

### Post by bhavi on 2008-03-22
> **p_quarles said:**
> That is no more effective than a fingerprint reader. Booting from a removable disk will skip the hard disk's bootloader completely.
Yes... I know... but there is no way to stop social engineering and one gaining physical access to a system.. Only user awareness is the way out I think...

---

### Post by nutz on 2008-03-23
This is why physical security is so important. Even a bios password is easy to get around. The lesson here is to prevent physical access to the computer by unauthorized users.

If you want to safe guard it in the case it gets lost or stolen then you could encrypt the drive. This is why companies are now enforcing whole disk encryption on all devices that leave the building and lose their physical security layer. Hard drive encryption is just a good idea anyway and should have been a standard on end user computing devices a long time ago.

---

### Post by BatsotO on 2008-03-23
The way I see it is that security is based on need. The Internet cafe people like me, lock the pc in the drawer for security reason, It prevent kleptomaniac from stealing the pc or any part of it. But when it come to the system, there's no secret in it, and if anyone managed to do some damage, it can always be restored.
Not everyone need to lock up their pc on a room with armed personel guarding it 24/7, or encypt their disks, it just too unpractical.
I keep recovery mode coz it very handy when i need it mostly for fsck, I dont have cdrom or floppy installed on every computers. And I do forget passwords. Recovery mode is a hole that available when we can't enter from the other hole. But I consider removing it from menu.list when i have linux bootable usb flashdrive, some day. 
Leaving a laptop unattended is as risky as having your door home open while you're away, you can only hope that your system is still running ok, or better yet, you can pray that your laptop is still there.

Measure your security level and be happy with it. Remember that in your hands lies the safety of the world, or the safety of your family photos.

BTW, I can't imagine someone would waste his time booting my pc, press esc, wait a while and type sudo rm -rf.

---

### Post by mateamargo on 2008-04-13
If I choose to start in terminal with safe mode (in the Grub menu) I have root access without asking me for a password.

How can I change this?

PS: Using Ubuntu 7.10

---

### Post by kwacka on 2008-04-13
I haven't tried, but I assume that if you set a root password you'll be prompted for the password.

If you're root - "passwd root" otherwise "sudo passwd root"

---

### Post by The Cog on 2008-04-13
That's true. But the idea of Ubuntu's security system is that there is no root password, meaning that it is not possible to log in as root The recovery mode had to be modified to allow recovery in this case. And setting a root password doesn't make the machine safer. Anyonoe who is there to choose recovery mode on boot up is also able to use a live cd to gain access. The idea that setting a root password makes the machine safer is just self delusion.

---

### Post by kwacka on 2008-04-13
There remains the problem of "sudo su".

---

### Post by mrsteveman1 on 2008-04-13
If you mean single user mode (recovery mode in ubuntu), there shouldn't really be a password. Single user mode is supposed to be able to bypass the normal boot authentication and startup sequence, a password doesn't really help much there, you are better off protecting the system itself to keep someone from booting single user / recovery mode in the first place.

The best you can do is lock the case, set a password on the bios and set a password on grub. This moves your security down to the case level, someone would have to get into the case and reset the bios in order to circumvent the boot process to get into single user mode or boot a livecd.

As for sudo su, by default any user with sudo access can run anything. If they can run something with sudo as the super user already, there isn't anything MORE they can accomplish by changing the shell to run as root with sudo su, they are already running processes as UID 0. Hence sudo su isn't a security hole unless you specifically restrict the programs that user can run with sudo.

---

### Post by netlogic on 2008-04-13
I think everyone explained this very clear why this process is needed. Just remember how operating system functions. Security isn't active when the machine is inactive. That is why disk encryptions are used. This applies to every operating system in this planet. It wouldn't be hard to change or blank the LMHASH with a live cd for Windows. If the disk encryption isn't used, there is no physical security for any operating system.

---

### Post by netlogic on 2008-04-14
> **Chiko2008 said:**
> still think it's not possible.
What isn't possible?
Root access in  a single user mode or 100s of security apps out that will blank out local lmhash passwords?

---

### Post by matemargo on 2008-04-14
If I disable the boot from a CD and put a password to the BIOS, someone can still choose the recovery mode and gain root access without any password prompt.

That's my point.

Setting a password for the root user should avoid this?

---

### Post by netlogic on 2008-04-14
1. search online about adding a grub password.
2. put password on your bios from booting from cd-rom
(however, someone can change the jumper and reset your bios password)
3. encrypt /home, /etc, /tmp, /var

If you do all three, you are fully protected and more secure than any other OS.

---

### Post by edm1 on 2008-04-14
you can set a grub password by tinkering in /boot/grub/menu.lst but the idea is that if someone has physical access to your computer there's nothing you can really do to stop them accessing private info, only slow them down (apart from encrypting your HD).

---

### Post by jrothwell97 on 2008-05-04
> **aysiu said:**
> Mac OS X has this, too. If you press Cmd-S during boot-up, you boot into single-user mode, which is basically recovery mode.
Indeed it does, but there is an easy way to lock this option off: as OS X ties in more closely with the firmware, the BIOS (or its equivalent) handles both CD booting and booting from the kernel image and starting init. This means that running the Open Firmware password utility (there is an Intel Mac equivalent) will disable CD booting, network booting, Firewire and USB booting, single user mode and booting into target disk mode (which is, unchecked, a *horrendous* security risk).

---

### Post by aysiu on 2008-05-04
> **jrothwell97 said:**
> Indeed it does, but there is an easy way to lock this option off: as OS X ties in more closely with the firmware, the BIOS (or its equivalent) handles both CD booting and booting from the kernel image and starting init. This means that running the Open Firmware password utility (there is an Intel Mac equivalent) will disable CD booting, network booting, Firewire and USB booting, single user mode and booting into target disk mode (which is, unchecked, a *horrendous* security risk).
You can also, in Ubuntu, set a Grub password or a password in the BIOS.

These measures slow down attempts to breach security, but they do not prevent someone who has physical access to your computer from essentially having root access.

---

### Post by Random5 on 2008-05-16
If someone has stolen my computer it's gone, they have the time to get what they want. Well ok your typical thief would just flail around hopelessly trying to login without the password let alone using linux, probably just giving up and leaving your personal photos and so on secure but I digress... If I'm away for 5 minutes I don't want someone to be able to copy anything or nuke my root filesystem in that amount of time! If this is unsecured why can I lock my screen? What's the point of putting an application in to lock my screen so a password is required to use the computer again if instead a reboot is all that is needed to gain full access to the system.

It's like locking your front door but leaving the window open in case you forget your keys and need to get into the house.

---

### Post by aysiu on 2008-05-16
> **Random5 said:**
> If someone has stolen my computer it's gone. If I'm away for 5 minutes I don't want someone to be able to nuke my root filesystem in that amount of time! If this is unsecured why can I lock my screen? What's the point of putting an application in to lock my screen so a password is required to use the computer again if instead a reboot is all that is needed to gain full access to the system.

It's like locking your front door but leaving the window open in case you forget your keys and need to get into the house.
If you lock your screen, people can't make a change without you knowing it.

And just because you have access to the keyboard and screen doesn't mean you have the ability to reboot, especially if the computer itself is locked away somewhere.

Regardless, anyone who comes to an unlocked session can point and click their way into messing things up, but most people who reboot into root@ubuntu:~$ have no idea what to do from there, even if they wanted to mess things up. Someone knowledgeable enough to nuke your installation from a command prompt wouldn't be deterred by a locked screen anyway, if they had the ability to reboot the computer.

---

### Post by lswest on 2008-05-16
if you're interested in security check out this how-to: [http://ubuntuforums.org/showthread.php?t=715630](http://ubuntuforums.org/showthread.php?t=715630) it shows you how to add a password to certain GRUB entries (such as the recovery console) so that others cannot access it without a password.

---

### Post by Rmantingh on 2008-06-15
Add my vote to the "No" camp.

I've read all the pro's and con's but am still not convinced that such easy access to an Ubuntu system is the way to go. If we ever want to compete with Windows on a professional level then it should be harder to gain access to your system, not easier. I also see tightening up GRUB security as part of that.
I know that a determined mind will get access whatever the security measures but that does not mean that we have to make it easier for a person taking a 'casual' interest in our files.
I agree that the best way to secure any data is to prevent physical access to the storage devices (e.g. network storage with hardware locked away) or else to encrypt the data itself.

---

### Post by eragon100 on 2008-07-28
I have been using it for 10 months, and I lofe it, but this is terrible:

1: reboot pc

2: use grub menu to start "ubuntu recovery mode"

3: in the menu, select "drop to root terminal" and press enter

4: You are now in a root terminal, and can do anything you like, like typing in rm --rf / or something just as bad. No password required.

So, ubuntu gives you full root acces to the computer without asking password or even username. GREAT!!

I might just have to report this as a bug :(

---

### Post by sharks on 2008-07-28
Not like what your title says. just change that to  Ubuntu: the most secure OS ever.

---

### Post by Der Alte on 2008-07-28
Nothing is secure if the intruder has local access, it's just a matter of time. There's no way to achieve this without local access, so it's irrelevant.

---

### Post by popch on 2008-07-28
Once you have ***physical ***access to a computer, no OS is secure. Consider: how does making the computer proof against intruders make your computer secure when you can just take any live CD and boot the computer from that?

---

### Post by eragon100 on 2008-07-28
> **popch said:**
> Once you have ***physical ***access to a computer, no OS is secure. Consider: how does making the computer proof against intruders make your computer secure when you can just take any live CD and boot the computer from that?

Ever heard of encrypting a harddisk?

That doesn't work if the Os then easily, very easily, gives you full acces to all the encrypted data, lets you read it, delete it, etcetera.

Furthermore, offcourse no OS is secure with local access. Problem is, only advanced technical people can normally hack a OS. This problem makes it easy for joe the average user, which is bad.

---

### Post by Bachstelze on 2008-07-28
> **popch said:**
> Consider: how does making the computer proof against intruders make your computer secure when you can just take any live CD and boot the computer from that?

Boot from CD disabled in the BIOS, BIOS password and case lock. It won't block anyone who is *really* wanting to lurk into your machine, but will be good enough to avoid pranksters in a mildly sensible environment (work, school, etc.).

But this thread is pointless anyway. If your system is in such an environment, you really should do some securing yourself anyway, and not just leave the default install as is, whatever the OS is.

---

### Post by lisati on 2008-07-28
Just a thought: Finding security problems (both real and imagined) isn't everybody's idea of a good time.

---

### Post by Archmage on 2008-07-28
I'm sorry, but you know that you can easily turn of the recovery mode if it is bugging you?

---

### Post by Bachstelze on 2008-07-28
> **lisati said:**
> Just a thought: Finding security problems (both real and imagined) isn't everybody's idea of a good time.

Just a thought: neither is making personally hostile innuendos.

---

### Post by LaRoza on 2008-07-28
> **HymnToLife said:**
> Boot from CD disabled in the BIOS, BIOS password and case lock. It won't block anyone who is *really* wanting to lurk into your machine, but will be good enough to avoid pranksters in a mildly sensible environment (work, school, etc.).


Give me three minutes and a screwdriver and I will get in. (Even if you disable booting, taking the harddrive out is easy. Drive encryption is the only way to go.)

> **eragon100 said:**
> 
2: use grub menu to start "ubuntu recovery mode"

Password protect grub and remove that entry.

> 
So, ubuntu gives you full root acces to the computer without asking password or even username. GREAT!!

I'd think they'd have noticed this if it were unintentional.

---

### Post by lisati on 2008-07-28
> **HymnToLife said:**
> Just a thought: neither is making personally hostile innuendos.
Huh? :confused:

---

### Post by Bachstelze on 2008-07-28
> **LaRoza said:**
> Give me three minutes and a screwdriver and I will get in. (Even if you disable booting, taking the harddrive out is easy. Drive encryption is the only way to go.)

Read my message entirely, please. Also, how do you break a lock with a screwdriver?

---

### Post by LaRoza on 2008-07-28
> **HymnToLife said:**
> Read my message entirely, please. Also, how do you break a lock with a screwdriver?

I've broken into cases that were "locked". Cases aren't meant to be secure. The screw driver is for resetting the BIOS. (although if I were trying to steal data, I'd just take the hard disk and peruse it as my leisure)

---

### Post by powerpleb on 2008-07-28
> **LaRoza said:**
> I've broken into cases that were "locked". Cases aren't meant to be secure. The screw driver is for resetting the BIOS. (although if I were trying to steal data, I'd just take the hard disk and peruse it as my leisure)

Or you could just find the person who knows the information you are trying to get and threaten to use the screwdriver on them. :twisted:

---

### Post by lisati on 2008-07-28
As much as I'd like to hang around to monitor this discussion, I think I'll sign off for the night.....

Happy security discussions, everyone!

---

### Post by Bachstelze on 2008-07-28
> **LaRoza said:**
> I've broken into cases that were "locked". Cases aren't meant to be secure.

P'raps we're not talking about the same kind of "locks".

[http://en.wiktionary.org/wiki/lock#Noun](http://en.wiktionary.org/wiki/lock#Noun)

It would take more than a screwdriver to get in, and you'd probably be noticed quite easily.

---

### Post by aaaantoine on 2008-07-28
1.```
sudo apt-get install startupmanager
```
2. System -> Administration -> Startup Manager
3. **Security** tab.
4. Check the box next to "Password protect rescue mode"
5. Enter a new password in the **Change password** area.
6. Click **Update Password**.

Problem solved.

---

### Post by Elfy on 2008-07-28
You don't need startupmanager to do that the option is in the menu list anyway.

---

### Post by pmlxuser on 2008-07-28
> **eragon100 said:**
> I have been using it for 10 months, and I lofe it, but this is terrible:

1: reboot pc

2: use grub menu to start "ubuntu recovery mode"

3: in the menu, select "drop to root terminal" and press enter

4: You are now in a root terminal, and can do anything you like, like typing in rm --rf / or something just as bad. No password required.

So, ubuntu gives you full root acces to the computer without asking password or even username. GREAT!!

I might just have to report this as a bug :(

1. it's nice that u assume that the person nows the commands
2. You deliberately gives his access to your machine
3. you just want to do it anyway as stated in 4

for security purposes i did the follwing
```

$sudo apt-get install lock #for my bedroom door
$sudo apt-get install password # for bios

```

---

### Post by Archmage on 2008-07-28
I fund another **BIG SECURITY BUG** in Ubuntu.

Someone can take the whole PC with you! That means that everbody can steal your data and hardware!!! :shock:

I mean, instead of the person taking the recovery mode, it can take the whole PC! Where is the security?

---

### Post by powerpleb on 2008-07-28
> **Archmage said:**
> I fund another **BIG SECURITY BUG** in Ubuntu.

Someone can take the whole PC with you! That means that everbody can steal your data and hardware!!! :shock:

I mean, instead of the person taking the recovery mode, it can take the whole PC! Where is the security?

They're fixing that. The next Ubuntu is going to come preinstalled with tenticles which fly out of the computer case when a theif tries to take it and flails them with razor sharp barbs.

---

### Post by popch on 2008-07-28
> **powerpleb said:**
> They're fixing that. The next Ubuntu is going to come preinstalled with tenticles which fly out of the computer case when a theif tries to take it and flails them with razor sharp barbs.

Use python, rather. It installs with a sixteen ton weight.

---

### Post by Joeb454 on 2008-07-28
If you don't want somebody getting access to your PC, unscrew the hard drive and take it with you everywhere. They can't really do much then...

Thread finished??

---

### Post by SupaSonic on 2008-07-28
I use truecrypt for sensitive data. Intruders, take your time, you are never going to get in without the knowledge of my 23-character password.

Or maybe I'm just paranoid.

---

### Post by Luffield on 2008-07-28
I thought it was possible to configure Ubuntu so that rebooting will require a password - is this true?

---

### Post by K.Mandla on 2008-07-28
I'm sorry, I'm sure it was intended to be serious, but this thread made me lol. :lolflag:

---

### Post by powerpleb on 2008-07-28
> **Joeb454 said:**
> If you don't want somebody getting access to your PC, unscrew the hard drive and take it with you everywhere. They can't really do much then...
Except mug you.
> **Joeb454 said:**
> 
Thread finished???
Sorry.

---

### Post by Dragonbite on 2008-07-28
Y'know, I'll have to try this out now that I found out my Library is using Ubuntu for their card catalog.

This *is* an issue unless the people deploying these Ubuntu Machines in public locations know about this issue and make the recommended modifications to protect it.

For home use it may be nice to have this option just in case, but on a laptop that may be a different story.

It should be closed by default, and then made known how to turn it on if one so chooses to it (lock down by default).

---

### Post by Joeb454 on 2008-07-28
> **powerpleb said:**
> Except mug you

Well there's not much you can do about that except try and stamp on the drive to break it.

Either way this thread is getting increasingly off topic...</hint>

---

### Post by billgoldberg on 2008-07-28
> **eragon100 said:**
> I have been using it for 10 months, and I lofe it, but this is terrible:

1: reboot pc

2: use grub menu to start "ubuntu recovery mode"

3: in the menu, select "drop to root terminal" and press enter

4: You are now in a root terminal, and can do anything you like, like typing in rm --rf / or something just as bad. No password required.

So, ubuntu gives you full root acces to the computer without asking password or even username. GREAT!!

I might just have to report this as a bug :(

Set a root password.

--

If someone get physical access to your pc, you are vulnerable.

Do you really think people care about your info  that much they would brake in and use those steps to access your data?

--

The only was to secure it is to encrypt your data/hdd/

---

### Post by tom66 on 2008-07-28
Give me 12 minutes and the ophcrack CD and I'll be in Vista in no time.

---

### Post by billgoldberg on 2008-07-28
> **Dragonbite said:**
> Y'know, I'll have to try this out now that I found out my Library is using Ubuntu for their card catalog.

This *is* an issue unless the people deploying these Ubuntu Machines in public locations know about this issue and make the recommended modifications to protect it.

For home use it may be nice to have this option just in case, but on a laptop that may be a different story.

It should be closed by default, and then made known how to turn it on if one so chooses to it (lock down by default).

If you are deploying Ubuntu computers and you don't know how to set a root password and/or disable the recovery mode in the grub, than you shouldn't be deploying them.

---

### Post by eragon100 on 2008-07-28
> **Dragonbite said:**
> Y'know, I'll have to try this out now that I found out my Library is using Ubuntu for their card catalog.

This *is* an issue unless the people deploying these Ubuntu Machines in public locations know about this issue and make the recommended modifications to protect it.

For home use it may be nice to have this option just in case, but on a laptop that may be a different story.

It should be closed by default, and then made known how to turn it on if one so chooses to it (lock down by default).

Exactly.

And encrypting data doesn't work, becasue you also have full acess to that via steps mentioned in first post :( (the root user doesn't need to enter the encryption key, becasue root can do anything he likes. A normal user can't)

And it is a bit stupid that you have to disable recovery mode to secure your data, because recovery mode isn't called that for no reason.
It can come in quite handy, I actually rescued a broken system with it once :wink:

---

### Post by tom66 on 2008-07-28
For library computers just remove the entry on GRUB. It's not imperative; you can just reinstall. If you're paranoid, epoxy the USB and CD-rom.

---

### Post by billgoldberg on 2008-07-28
A real unsecure OS (mac osx, windows, ...) is one where stuff is running where you don't know what it's doing (or can't find out).

---

### Post by Trail on 2008-07-28
> **popch said:**
> Use python, rather. It installs with a sixteen ton weight.

rofl

---

### Post by Archmage on 2008-07-28
> **SupaSonic said:**
> I use truecrypt for sensitive data. Intruders, take your time, you are never going to get in without the knowledge of my 23-character password.

Or maybe I'm just paranoid.

If you are asking yourself this question, than you are not paranoid enough. ;)


> **Luffield said:**
> I thought it was possible to configure Ubuntu so that rebooting will require a password - is this true?

Yes, this is true. But someone still could just unplug the cable. And keep in mind that they even can STEAL YOUR PC!


> **Dragonbite said:**
> This *is* an issue unless the people deploying these Ubuntu Machines in public locations know about this issue and make the recommended modifications to protect it.

If you put a PC in a public location you should know such things.

> **Dragonbite said:**
> It should be closed by default, and then made known how to turn it on if one so chooses to it (lock down by default).

Bad idea. If something goes wrong you couldn't go into the recover mode.

---

### Post by SupaSonic on 2008-07-28
> **eragon100 said:**
> Exactly.

And encrypting data doesn't work, becasue you also have full acess to that via steps mentioned in first post :( (the root user doesn't need to enter the encryption key, becasue root can do anything he likes. A normal user can't)

And that is why it's best to use 3rd party encryption. Even though it's only partial, it still offers some level of protection for your data, if not your OS.

---

### Post by billgoldberg on 2008-07-28
> **eragon100 said:**
> Exactly.

And encrypting data doesn't work, becasue you also have full acess to that via steps mentioned in first post :( (the root user doesn't need to enter the encryption key, becasue root can do anything he likes. A normal user can't)

And it is a bit stupid that you have to disable recovery mode to secure your data, because recovery mode isn't called that for no reason.
It can come in quite handy, I actually rescued a broken system with it once :wink:

Once again, set a root password.

This is an ubuntu feature, not a bug.

Or do you think you are to first one to "discover" this?

---

### Post by Archmage on 2008-07-28
> **eragon100 said:**
> And encrypting data doesn't work, becasue you also have full acess to that via steps mentioned in first post :( (the root user doesn't need to enter the encryption key, becasue root can do anything he likes. A normal user can't)

Sorry, without the key you can't read the encryption. No matter what user you are. You can be root, King of England or God. Without key there is no data you can look at, it it is encrypted.

---

### Post by LaRoza on 2008-07-28
> **HymnToLife said:**
> P'raps we're not talking about the same kind of "locks".

[http://en.wiktionary.org/wiki/lock#Noun](http://en.wiktionary.org/wiki/lock#Noun)

It would take more than a screwdriver to get in, and you'd probably be noticed quite easily.

Yes, we are.

The locks are strong, and where they are attached is also strong, but the best place to break into is the weakest part, not the strongest.

---

### Post by Archmage on 2008-07-28
> **LaRoza said:**
> Yes, we are.

The locks are strong, and where they are attached is also strong, but the best place to break into is the weakest part, not the strongest.

If you are an evil intruder, you can smash the PC a few times on the floor. The case will be broken and you can take out the hard drive. It might be broken, but what is the fun in beeing an evil intruder.

---

### Post by tom66 on 2008-07-28
Why don't we just short out some component like they do in the movies? Watch for flying sparks (they're signs it's acknowledging your request) and strange billows of blue smoke along with an eerily beeping. 

If you're paranoid a couple of 5 inch bolts through the motherboard, CPU, and HDD ought to keep it in place. (Don't laugh, someone actually did that. Worried about theives stealing his computer but confused why it wasn't working after his 'security program')

---

### Post by Dragonbite on 2008-07-28
> **Archmage said:**
> If you put a PC in a public location you should know such things.
The optimal word is "should" but with the proliferation of Linux among PC-guys-going-to-Linux there is a significant chance that this is overlooked unless there is some way to educate these people.

Is it included in the $99 Ubuntu class? Is it included in the certification learning?

Then some kid finds out you can do it and *blam!* Linux is insecure piece of #$%^ and they go back to Windows.

Where else, other than this thread, is this information available?

---

### Post by eragon100 on 2008-07-28
> **Archmage said:**
> If you are an evil intruder, you can smash the PC a few times on the floor. The case will be broken and you can take out the hard drive. It might be broken, but what is the fun in beeing an evil intruder.

Smashing the owner on the floor? :twisted:

---

### Post by jimv on 2008-07-28
> **eragon100 said:**
> Ever heard of encrypting a harddisk?

That doesn't work if the Os then easily, very easily, gives you full acces to all the encrypted data, lets you read it, delete it, etcetera.

Furthermore, offcourse no OS is secure with local access. Problem is, only advanced technical people can normally hack a OS. This problem makes it easy for joe the average user, which is bad.

FAIL.  Logging in as root will not give you access to a user's encrypted data.  You still have to know the password.  Also, a default install of Windows has a blank administrator password.

All the average Joe needs to do to get admin rights on a Windows box is put a live CD in.  All the sudden all those NTFS permissions don't mean anything anymore.

---

### Post by Archmage on 2008-07-28
> **Dragonbite said:**
> The optimal word is "should" but with the proliferation of Linux among PC-guys-going-to-Linux there is a significant chance that this is overlooked unless there is some way to educate these people.

Is it included in the $99 Ubuntu class? Is it included in the certification learning?

Then some kid finds out you can do it and *blam!* Linux is insecure piece of #$%^ and they go back to Windows.

Where else, other than this thread, is this information available?

Please check out the recovery option in Windows...

---

### Post by Mr. Picklesworth on 2008-07-28
Just removing the entry from GRUB solves nothing, by the way, since recovery mode is just a particular known boot option. Best solution is to skip GRUB entirely, set a password for recovery mode or set a password for GRUB.

---

### Post by lukjad on 2008-07-28
> **eragon100 said:**
> I have been using it for 10 months, and I lofe it, but this is terrible:

1: reboot pc

2: use grub menu to start "ubuntu recovery mode"

3: in the menu, select "drop to root terminal" and press enter

4: You are now in a root terminal, and can do anything you like, like typing in rm --rf / or something just as bad. No password required.

So, ubuntu gives you full root acces to the computer without asking password or even username. GREAT!!

I might just have to report this as a bug :(

You're acting like this is Mission Impossible. :D Unless you have a super secret NOC list that thousands of spies are going to want to get, this is not a problem. Also, if you have a nosy relative, just make a boot password and shut off your computer every time you leave the room. You can also encrypt your HD, but make sure not to forget your password.

---

### Post by mordak13 on 2008-07-28
> **K.Mandla said:**
> I'm sorry, I'm sure it was intended to be serious, but this thread made me lol. :lolflag:

It's all just for the LOLs anyway right? :mrgreen:

---

### Post by MasterJS on 2008-07-28
One good thing came out of this thread: Information that some people might not know will now be easily found. I actually learned a couple things, so thanks to all.

---

### Post by reyfer on 2008-07-28
Just for those claiming that the only real solution is full disk encryption:

[http://www.youtube.com/watch?v=JDaicPIgn9U](http://www.youtube.com/watch?v=JDaicPIgn9U)

---

### Post by sydbat on 2008-07-28
> **reyfer said:**
> Just for those claiming that the only real solution is full disk encryption:

[http://www.youtube.com/watch?v=JDaicPIgn9U](http://www.youtube.com/watch?v=JDaicPIgn9U)Oh those smart people and their university educations!!!

---

### Post by aaaantoine on 2008-07-28
> **tom66 said:**
> Give me 12 minutes and the ophcrack CD and I'll be in Vista in **12 minutes**.

Fixed that for you. ;)

---

### Post by original_jamingrit on 2008-07-28
> **reyfer said:**
> Just for those claiming that the only real solution is full disk encryption:

[http://www.youtube.com/watch?v=JDaicPIgn9U](http://www.youtube.com/watch?v=JDaicPIgn9U)

It still provides some level of security, especially against a thief who finds your computer turned off (except for that one version of vista mentioned in the video).

But I agree, security can never have just one solution.  It requires many solutions, and even then it cannot be 100% perfect.

I think Truecrypt provides the ability for multiple layers of encryption, so that some parts are encrypted more than once and require extra keys.  Several others may also provide this ability.

---

### Post by cardinals_fan on 2008-07-28
> **lisati said:**
> Just a thought: Finding security problems (both real and imagined) isn't everybody's idea of a good time.
I enjoy it :)

I realize that you could encrypt your hard drive, but if you take the time to do that, you could easily disable the root option.  Otherwise, an intruder with local access has everything they need anyway.

---

### Post by Archmage on 2008-07-29
> **cardinals_fan said:**
> I realize that you could encrypt your hard drive, but if you take the time to do that, you could easily disable the root option.  Otherwise, an intruder with local access has everything they need anyway.

If you don't encrypt your harddrive, than anybody can acces your data. There are just so many possiblities: Live-CD, taking harddrive and reading from a different PC and so on.

---

### Post by cardinals_fan on 2008-07-29
> **Archmage said:**
> If you don't encrypt your harddrive, than anybody can acces your data. There are just so many possiblities: Live-CD, taking harddrive and reading from a different PC and so on.
My point exactly.

---

### Post by klange on 2008-07-29
Let's just end this with the following:

Security and encryption are meaningless if someone really wants to get to your data. Their only purpose is to impede the progress of thieves, but no method should ever be looked as a way to prevent break in. We protect things with encryption keys and passwords to keep people who really don't care from getting to them. You put a password on your account because you don't want your mother/brother/roommate to just go and use it - not because it's going to prevent Joe Random Cracker from getting on. You encrypted data on a hard disk so that it takes longer for Mr. Smith to get to it, not to stop him in his tracks.

The company I work for has a program that comes with quite a few AES-encrypted files, yet the key is available just by opening the application in a hex editor. Decompile it to intermediate language and it's labeled for you with a nice pretty variable name. We encrypt the files to keep our users from accidentally screwing them up. While sure, we wouldn't really like them to open them, it's not there to completely prevent it and there is no truly sensitive data in the files - just stuff we'd rather not have the our clients looking whenever they want.

---

### Post by Archmage on 2008-07-30
> **WindowsSucks said:**
> Let's just end this with the following:

Security and encryption are meaningless if someone really wants to get to your data. Their only purpose is to impede the progress of thieves, but no method should ever be looked as a way to prevent break in. We protect things with encryption keys and passwords to keep people who really don't care from getting to them. You put a password on your account because you don't want your mother/brother/roommate to just go and use it - not because it's going to prevent Joe Random Cracker from getting on. You encrypted data on a hard disk so that it takes longer for Mr. Smith to get to it, not to stop him in his tracks.

I'm sorry, but I beg to differ. Encryption is the only way if you have sensitive data.

---

### Post by jimv on 2008-07-30
Is it just me, or are a lot of Linux users overly paranoid when it comes to security?  I mean, what the heck are you guys keeping on your computers that all these supposed hackers and infiltrators are going to want so badly that they're going to steal your computers and decrypt your hard drives?

---

### Post by klange on 2008-07-30
> **Archmage said:**
> I'm sorry, but I beg to differ. Encryption is the only way if you have sensitive data.

And what exactly don't you agree with? I never said "don't do it, it's pointless", I said you should never expect any method to keep anyone out if they really want your data. I fully agree that if you have sensitive data you should take as many precautions as necessary to protect that data. I just said that nothing is going to prevent someone from getting to it if they really want to.

---

### Post by cardinals_fan on 2008-07-30
> **jimv said:**
> Is it just me, or are a lot of Linux users overly paranoid when it comes to security?  I mean, what the heck are you guys keeping on your computers that all these supposed hackers and infiltrators are going to want so badly that they're going to steal your computers and decrypt your hard drives?
I enjoy being paranoid :)

---

### Post by Oldsoldier2003 on 2008-07-30
> **cardinals_fan said:**
> I enjoy being paranoid :)

Just because you're paranoid doesn't mean they aren't out to get you!

---

### Post by Wiebelhaus on 2008-07-30
remove that line in the grub.lst , simple.

---

### Post by Oldsoldier2003 on 2008-07-30
> **sx66gns said:**
> remove that line in the grub.lst , simple.

actually that is easily bypassed...

---

### Post by jimv on 2008-07-30
> **Oldsoldier2003 said:**
> Just because you're paranoid doesn't mean they aren't out to get you!

Beat me to it.

---

### Post by cardinals_fan on 2008-07-30
> **Oldsoldier2003 said:**
> Just because you're paranoid doesn't mean they aren't out to get you!
*makes sure that tinfoil hat is secured*

---

### Post by Dragonbite on 2008-07-30
You aren't paranoid if they ARE out to get you.

---

### Post by cardinals_fan on 2008-07-30
> **Dragonbite said:**
> You aren't paranoid if they ARE out to get you.
We wouldn't want anything to happen to you, but unfortunate accidents are always possible...

---

### Post by munkyeetr on 2008-07-30
I've had this argument a few times now, and am not looking to have it again. For those who are concerned and want to secure their boot menu, use the link in my signature. Also disable booting from CD in your BIOS, and set a BIOS password. While not unstoppable, it definitely slows someone down if they want to perform the attack without stealing the machine.

There are those who continually argue that it is pointless if someone has physical access to your system, but as far as I am concerned, the biggest no-no as far as linux security goes is giving up root access, and any system that provides root access without requiring a password is insecure, regardless of whether that access is provided through physical access or over a network. It is a hole that doesn't need to be there at all, yet people defend it tooth and nail as a "feature". It's so bizarre to me.

Also, when people use the fact that Windows has Admin access without a password, that's a non-argument. No one, outside of Microsoft, claims Windows is secure. Linux is another story.

Anyway, as I said, the link in my sig can help those who are concerned.

---

### Post by JT9161 on 2008-08-01
Protecting your data is very simple: Juist have a boot password set in BIOS any if someone enters the wrong password your HDD covered in Thermite is ignited, Thieves wont get anything out of it.

---

### Post by Dragonbite on 2008-08-03
> **JT9161 said:**
> Protecting your data is very simple: Juist have a boot password set in BIOS any if someone enters the wrong password your HDD covered in Thermite is ignited, Thieves wont get anything out of it.

Reminds me of the James Bond car that when they tried breaking in by breaking the window, it blew up and took them out too!

---

### Post by fuzzyk.k on 2008-08-05
you can set a root password on the users and groups to prevent this

---

### Post by Dragonbite on 2008-08-05
So, is another, absolute way to counter doing this something as simple as setting a root password yourself?  Would that require somebody to put in the password to continue?

---

### Post by munkyeetr on 2008-08-05
> **Dragonbite said:**
> So, is another, absolute way to counter doing this something as simple as setting a root password yourself?  Would that require somebody to put in the password to continue?

No, that wouldn't change the situation at all.

---

### Post by munkyeetr on 2008-08-05
> **fuzzyk.k said:**
> you can set a root password on the users and groups to prevent this
?

Please explain what you mean.

---

### Post by saulgoode on 2008-08-05
> **Dragonbite said:**
> So, is another, absolute way to counter doing this something as simple as setting a root password yourself?

No. Having a root password would not be sufficient (but it is probably a necessary first step). The startup scripts would need to be modified to add an 'sulogin' at some point in the init process -- most GNU/Linux distros seem to do this (Slackware, Debian, Mandriva), but not all (CentOS, Ubuntu). 

Even having an 'sulogin' required by init does not prevent unauthorized access, since Linux allows you to override running 'init' on startup. For example, the user could boot with the kernel command "linux init=/bin/bash" and instead of the normal boot process, the kernel would load and run the BASH shell -- **this BASH shell would be running as root**.

In order to protect your system, you should add password protection to your bootloader. In LILO this is done by including the "restricted" command in its config file (along with a password). GRUB probably has something similar but I am unfamiliar with GRUB. 

> **Dragonbite said:**
> Would that require somebody to put in the password to continue?

Password protecting your your bootloader (GRUB or LILO) does not mean the user has to always enter a password; a password is necessary only if he wishes to boot with a method other than those available in the bootloader menu (the menu should be constructed so as to eliminate "unsafe" boot configurations).

It would also be necessary, if a secure system is desired, to disable booting from CDs, floppies, or pendrives in your BIOS and password protecting your BIOS. Again, password protecting your BIOS does not mean that a password needs to be entered every time you boot; it is only needed if changes are to be made to the BIOS.

None of this is very difficult, however, to my knowledge it does require that you enable root logins (unless you wish to completely forgo ever booting into single user mode, which is probably not a good idea).  Perhaps someone more familiar with Ubuntu's bootup process could provide the answer.

---

### Post by munkyeetr on 2008-08-05
> **saulgoode said:**
> 
None of this is very difficult, however, to my knowledge it does require that you enable root logins (unless you wish to completely forgo ever booting into single user mode, which is probably not a good idea).  Perhaps someone more familiar with Ubuntu's bootup process could provide the answer.

You don't need to enable root to secure this. Follow the link in my signature.

---

### Post by saulgoode on 2008-08-05
> **munkyeetr said:**
> You don't need to enable root to secure this. Follow the link in my signature.
I stand corrected. Thanks.

Following your tutorial, how does your technique password protect the 'e' and 'c' GRUB commands? Is that inferred by GRUB if you add a password to a particular image? Or did I overlook something in your tutorial? (mind, I know little about GRUB)

---

### Post by munkyeetr on 2008-08-05
When you add
```
password --md5 <password>
```
to the password section of /boot/grub/menu.lst you are now required to enter the specified password before you can add any boot parameters to the kernel. You must press 'p' and enter a password before any of the other commands ('e' and 'c' for instance) are available.

---

### Post by mp035 on 2008-08-27
Hello all,

I have been playing around with my own custom a super-light version of ubuntu for my eeepc.  It's made from a JEOS install with fluxbox and X installed.

I am running without a display manager, fluxbox starts from rc.local, starting as my user (mark) with the su command.

This means that I need to modify sudoers to access the shutdown command from the fluxbox menu.

I found that if I grant access to /sbin/shutdown anyone can simply run "sudo shutdown now" and they will be logged in to a console as root without entering a password.

Q1)Is this normal?

Q2) I have tried to close the hole by only allowing access to /sbin/poweroff and /sbin/reboot, instead of shutdown.  Is this a good solution?

Thanks.

---

### Post by Dr Small on 2008-08-27
Apparently, you do not understand how the sudoer's file operates. By adding an entry in the /etc/sudoers file to allow /sbin/shutdown, it does not allow it for everyone, unless you set a group, or ALL.

The proper syntax should be:
```
mark    ALL=(ALL) NOPASSWD: /sbin/shutdown
```

Regards,
Dr Small

---

### Post by mp035 on 2008-08-27
Hi, thanks for the quick reply,

I understand how the sudoers file works, that's why I included th background info,

if fluxbox and x are started from rc. local, this means everyone has normal user access to the system under my user name.

This is a small personal netbook, so this is a risk I am willing to take, however i am not prepared to have root access available without a password. 

the entry you showed is exactly what i had, but i have changed it to:
```

mark ALL=NOPASSWD: /sbin/poweroff
mark ALL=NOPASSWD: /sbin/reboot

```

Will this close the hole?

Thanks.

---

### Post by Dr Small on 2008-08-27
It should, but why not /sbin/shutdown ?
Also, if you want to keep X and Fluxbox from starting at bootup, install XDM for a login manager. A user would then have to login in order to get to your desktop.

Dr Small

---

### Post by mp035 on 2008-08-27
I want fluxbox to auto-login without the overhead of a display manager. 

As stated in post #1 if i allow access to /sbin/shutdown, running "sudo shutdown now" drops the system into a runlevel 1 tty **already logged in as root.**

This allows full root access without entering a password.

I didn't think this was normal behavior, but perhaps it is.

---

### Post by Dr Small on 2008-08-27
No. That is not normal behavior. Running:
```
sudo shutdown -h now
```

Should begin the shutdown proccess, and end with the system powered off. I don't know why it would be dropping to runlevel 1 and logging you in as root. That is absurd.

Dr Small

---

### Post by cdenley on 2008-08-27
As "Dr Small" said, you need the "-h" option. If you're not sure how a command works, check the man page.
```

man shutdown

```
> 
When invoked it generates a runlevel event, with an argument containing the new runlevel.


---

### Post by rogeriopvl on 2008-08-27
The thread's title is a little exaggerated.

Your system is dropping to init 1 on shutdown? that's not a normal behavior. init 1 is single user mode. Shutdown is init 0. So probably your not using the command correctly, or have changed it's normal behavior.

btw, have you set a password on grub? because in grub is also very easy for anyone to boot in single user mode.

---

### Post by mp035 on 2008-08-27
Yeah, I know that you need the -h option to halt the system, and the -r option to reboot.  I think I have not made myself clear.

My concern is that anyone who has access to the shutdown command, can log themselves in as root.

Sure you need the -r or -h option to do what I want (shutdown or reboot), but I thought it was extremely unsafe to have the ability to log in as root without a password given to anyone who can run shutdown.

There are numerous threads on the net suggesting that sudoers access to shutdown is a simple answer to shutting down without a password, but it seems like a major security flaw to me.

I will try running the shutdown command on my AMD64 box, and see if it responds the same way................

---

### Post by aysiu on 2008-08-27
> **mp035 said:**
> 
My concern is that anyone who has access to the shutdown command, can log themselves in as root. Your concern is unfounded. If you define it so that everyone can shutdown without a password, it doesn't mean anyone can log in as root. It means anyone can shutdown without a password.

---

### Post by mp035 on 2008-08-27
Ok, I just tried it on my stock Ubuntu 8.04 AMD 64 system.  Same issue, but with the stock box, you actually get a recovery menu with the option "Drop to root shell prompt."

Please can the next person who is thinking about telling me that you can't log in as root if you have access to /sbin/shutdown please do the following:

- Save any open files so you don't loose them. Close any open apps.
- In gnome, open a terminal
- type this exactly: ```
sudo shutdown now
```
- if you have not allowed standard user access to shutdown you will need to type the password.

Check the results!

If you did allow standard user access to shutdown ...... Access to a root console without a password!!!!

---

### Post by aysiu on 2008-08-27
It's not a root console. It's access to *one* root-privileged command.

That's the whole point of the /etc/sudoers file. It allows you fine-grained control. You can allow one kind of root access while denying all others.

---

### Post by mp035 on 2008-08-27
Thanks for the reply aysiu, but Please read this carefully:

Access to /sbin/shutdown DOES allow a user to access a console as root without a password.

This is not a question, I just did it twice to confirm it! Try it for yourself, follow the instructions in post #11

---

### Post by aysiu on 2008-08-27
I just tried it with unprivileged user who is allowed to shut down as specified in /etc/sudoers, and I just get the recovery menu.

One of the recovery menu options is *Drop to root shell prompt*, but you can always select that if you're able to reboot the computer.

I thought you meant that the user immediately dropped to a root shell without rebooting into recovery mode.

---

### Post by mp035 on 2008-08-27
Thanks for trying this aysiu.  So this is normal behavior? I should not be concerned?

Also, you say that a root prompt can be accessed if you're able to reboot the computer.  Does that mean that anyone can access an Ubuntu system as root without a password?  Just by selecting the recovery mode option in the Grub menu?

Thanks again.

---

### Post by mp035 on 2008-08-27
BTW on my eeepc I used JEOS as the base, so it drops straight to the root shell prompt without displaying the menu.

---

### Post by saulgoode on 2008-08-27
> **mp035 said:**
> Thanks for trying this aysiu.  So this is normal behavior? I should not be concerned?

Also, you say that a root prompt can be accessed if you're able to reboot the computer.  Does that mean that anyone can access an Ubuntu system as root without a password?  Just by selecting the recovery mode option in the Grub menu?

Yes, it is the "normal" behavior. However, you can modify your boot configuration so that dropping to a recovery console requires a password if you wish -- and should do so if you find the default behavior undesirable.

---

### Post by mp035 on 2008-08-27
Cool, thanks all, that answers my questions.

---

### Post by Vivaldi Gloria on 2008-08-28
Note that in the sudoers file you can use the exact form of the commands (i.e. with options):

```
# Cmnd alias specification
Cmnd_Alias SHUTDOWN_CMDS = /sbin/shutdown -h now, /sbin/reboot, /sbin/halt
```

Now the users that you let to give SHUTDOWN_CMDS without a pswd cannot use shutdown without the -h now option.

---

### Post by doorknob60 on 2008-08-29
Also, if you set a root password then you have to type it in in order to access it. Confirmed with Debian (where root is enabled by default, you can enable it in Ubuntu easy enough, just type 'sudo passwd' IIRC)

---

### Post by saulgoode on 2008-08-29
> **doorknob60 said:**
> Also, if you set a root password then you have to type it in in order to access it. Confirmed with Debian (where root is enabled by default, you can enable it in Ubuntu easy enough, just type 'sudo passwd' IIRC)
Actually, there is a way to circumvent that if your bootloader is configured to permit passing arguments to the kernel at startup. While creating a root password will provide some additional protection against someone booting into a root-enabled console, it is only protection in the sense that the user needs to learn the steps necessary to circumvent it.

---

### Post by bro on 2008-11-21
is this true? [http://www.paulspoerry.com/2008/09/06/replace-linux-root-password/](http://www.paulspoerry.com/2008/09/06/replace-linux-root-password/)

---

### Post by bodhi.zazen on 2008-11-21
Yes, if someone has physical access they pretty much own the machine. If not via the recovery mode, then via a live CD.

Your only protection (for data) would be encryption, even then they could install a new OS.

Everything else (bios passwords, grub passwords, etc) are easily defeated.

---

### Post by gpsmikey on 2008-11-21
Be careful playing with encryption - while this is the Linux forum, many here also use XP Pro.  One BIG trap door you can drop through with XP Pro is to enable the encrypting file system (EFS) and not have a safe copy of the key exported to disk somewhere.  XP Pro does not require you to have a DRA (Designated Recovery Agent) set up and if you do, as a number of poor souls have, re-install windows without exporting that key, all your encrypted data is now very safe ... even from you !! :(
It is virtually unrecoverable.

Just wanted to mention that for those thinking of using EFS in a mixed mode type environment etc.

mikey

---

### Post by Dr Small on 2008-11-21
> **gpsmikey said:**
> Be careful playing with encryption - while this is the Linux forum, many here also use XP Pro.  One BIG trap door you can drop through with XP Pro is to enable the encrypting file system (EFS) and not have a safe copy of the key exported to disk somewhere.  XP Pro does not require you to have a DRA (Designated Recovery Agent) set up and if you do, as a number of poor souls have, re-install windows without exporting that key, all your encrypted data is now very safe ... even from you !! :(
It is virtually unrecoverable.

Just wanted to mention that for those thinking of using EFS in a mixed mode type environment etc.

mikey
We are more or less discussing encrypting the linux partition, not the Windows one.

@OP:
Yes, this is possible (if you do not take such precautions to secure your system) and there are multiple other ways. Physical access is a security weakness in itself. So literally, if someone has physical access, there is nothing stopping them from taking the system to their lab and running tests there.

As bodhi.zazen mentioned, encryption is your greatest asset. Of course, encryption has it's flaws too, like if you use a weak password, have the keyfile within reach, or it could just inevitably be cracked (least likely).

A BIOS password can be circumvented,
A root password can be changed,
A user password can be altered,
A case lock can be broken,
etc.

You should get the point. With encryption, they can't edit the root/user password via a liveCD, nor can they access the system files. But anyhow, we have really went off base from the OP's question, I guess :D

---

### Post by bodhi.zazen on 2008-11-21
> **gpsmikey said:**
> Be careful playing with encryption - while this is the Linux forum, many here also use XP Pro.  One BIG trap door you can drop through with XP Pro is to enable the encrypting file system (EFS) and not have a safe copy of the key exported to disk somewhere.  XP Pro does not require you to have a DRA (Designated Recovery Agent) set up and if you do, as a number of poor souls have, re-install windows without exporting that key, all your encrypted data is now very safe ... even from you !! :(
It is virtually unrecoverable.

Just wanted to mention that for those thinking of using EFS in a mixed mode type environment etc.

mikey

It is similar to Linux. If you lose the key or forget the password our data will essentially be lost (until (if) someone develops the cracking tools ...).

---

### Post by Therion on 2008-11-21
> **bro said:**
> is this true? [http://www.paulspoerry.com/2008/09/06/replace-linux-root-password/](http://www.paulspoerry.com/2008/09/06/replace-linux-root-password/)
Related question...  Let's assume I wanted someone's data badly enough to rip off their entire PC and bring it back to my evil PC laboratory. 

Wouldn't it be simpler to strip out the primary hard drive from the stolen PC and then connect it to another PC as a slave-drive?  Would that work?  Would I then be able to navigate the stolen hard drive without even booting the operating system it contains?  Would I cackle with vile laughter as I made illicit copies of little Johnnie's fifth birthday party and and .mp3's of bands I've never heard of?

Frankly, I don't think most PC's are stolen for the data, I think they're stolen for the hardware (I'm told I have a keen eye for the obvious) but either way I'm playing this through in my head and can't decide if it would work or not.

---

### Post by Dr Small on 2008-11-21
> **Therion said:**
> Related question...  Let's assume I wanted someone's data badly enough to rip off their entire PC and bring it back to my evil PC laboratory. 

Wouldn't it be simpler to strip out the primary hard drive from the stolen PC and then connect it to another PC as a slave-drive?  Would that work?  Would I then be able to navigate the stolen hard drive without even booting the operating system it contains?  Would I cackle with vile laughter as I made illicit copies of little Johnnie's fifth birthday party and and .mp3's of bands I've never heard of?

Frankly, I don't think most PC's are stolen for the data, I think they're stolen for the hardware (I'm told I have a keen eye for the obvious) but either way I'm playing this through in my head and can't decide if it would work or not.
It all depends on if you work for the CIA, or are just simply Johnnie's mom.

---

### Post by Therion on 2008-11-21
> **Dr Small said:**
> It all depends on if you work for the CIA, or are just simply Johnnie's mom.
What if I'm Johnnie's mom AND work for the CIA AND have a license to kill (e.g. 008)?

---

### Post by bodhi.zazen on 2008-11-21
> **Therion said:**
> Related question...  Let's assume I wanted someone's data badly enough to rip off their entire PC and bring it back to my evil PC laboratory. 

Wouldn't it be simpler to strip out the primary hard drive from the stolen PC and then connect it to another PC as a slave-drive?  Would that work?  Would I then be able to navigate the stolen hard drive without even booting the operating system it contains?  Would I cackle with vile laughter as I made illicit copies of little Johnnie's fifth birthday party and and .mp3's of bands I've never heard of?

Frankly, I don't think most PC's are stolen for the data, I think they're stolen for the hardware (I'm told I have a keen eye for the obvious) but either way I'm playing this through in my head and can't decide if it would work or not.

Yes that would work as well, but that falls under the umbrella of "Physical Access".

The only protection one has in this scenario is encryption :twisted:

And do not assume that "private data" has no value, identity theft is a big problem. As has been pointed out on similar threads it depends on the private data.

---

### Post by Therion on 2008-11-21
> **bodhi.zazen said:**
> Yes that would work as well, but that falls under the umbrella of "Physical Access".
Right, that's what I meant... Once the PC in question is in my evil laboratory (I'm SO going to convert my garage!) and I have that total access, I was just thinking it really WOULD be easier to simply remove the stolen drive and "hot swap" it into my existing system.  It would by-pass all that icky root/admin password stuff and let me get down to my evil business post-haste.  The world's not going to dominate itself now is it??

---

### Post by bodhi.zazen on 2008-11-21
naw, a live CD will do just fine. You can crack the bios (if a password is set) faster then you can move the hard drive.

---

### Post by bro on 2008-11-22
Nice to see people pick up on the discussion. I figured that somebody could study my harddisk and more by taking it out. But if my laptop is stolen, yes that would be for the hardware. 

However, the easier it gets to 'just log in and see' the more chance that the thief might just try and see. 

What will he find besides naked pictures of my girlfriend? 
He will go to my mail account and see my mail. He will see my browser remembered my password and login and change it. Then I will be excluded from a lot of data (that I can recover elsewhere). 
But I have there data on how to log in to many websites that I own, master of use. He might change all of that. There are scanned copies of my passport, I even mailed a scanned copy of a fax-form with creditcard data once - it might still be in 'sent items' and it might take him a thousand mails to digg through... but still. 

So this encryption of /home? Is it a big strain on performance? 
Come to think about it, I'm going to tell firefox to forget my passwords right now.

---

### Post by digicidal on 2008-11-22
I use 'old school security' for this type of scenario... I have ubuntu set up as my 'financial OS' for doing bill payment, online orders, etc.. nothing else (at least on that machine) is done in Linux - only on XP.  Firefox is set to not remember anything and not to cache anything - after all browser caching made sense in the dial-up days... but I have a 6Mbit connection now... why bother.

Now the secure part... each account has a hyper-secure password that would be impossible to crack (and unfortunately, impossible to remember as well) which I generate via a script I wrote... so each password looks something like : 'Dj3$5ioL2@9y7MPs105' - and it's different for each account.  I write in a ledger book (or 'crashless archive' if you prefer) the account type (bank, CC, retailer, etc..) and the date it (the password) was set.  Every 90 days or so I regerate a new password and cross out the old entry after writing the new one in the ledger.  This ledger then gets locked in the safe with my other important papers.

Any digital media (PDF receipts, scans, important emails, etc..) are then individually encrypted and password protected in separate archives and stored on a thumb drive which is also locked in the safe.

Now I can have the computer stolen, or my house can burn down and I lose the computer itself... but unless the fire gets ridiculously hot - I can still recover the passwords and the thumbdrive data (safe is fireproof).  Naturally someone could steal the safe and my computer, however it would take some very serious hardware and a jackhammer to get the safe out and open it - during which time I would hope that my nosy neighbors would have called the cops multiple times.

Although (for the most part) Linux makes things more difficult for hackers... there is not a computer on the planet that is 'un-hackable' unless it is disconnected from all networks and sits in a vault under the pentagon... and even then it's just safe from 99.9999% of intruders.

The main idea I use for determining security requirements (both professionally - I'm in IT - and personally) is the 'rule of value'... i.e. if it costs more to get something than that thing is worth... then it is safe.  If you are a multi-millionaire, then you'd better have some top-shelf security on your home, business, and financial records... if you're me (a 'thousandaire' at best) ... then you can do it with a $500 safe and some common sense.

---

### Post by gpsmikey on 2008-11-22
Actually, you could go one more level to make sure that there is no chance of anything on the computer being found - run Ubuntu from a "live CD" on a diskless machine with only the usb thumb drive for storage.  Now there is no chance of them getting anything cached anywhere on the disk because there is NO disk to check !!

mikey

---

### Post by bro on 2008-11-22
@digicidal. If I would live in a country where they have things like patriot acts I might do it your way (and beyond that...). However, I like to have life too. Everytime you check your mail you get the password out the safe and type in stuff like LSO£%)SLDKK"**( ? (the last question mark is a question mark) 

That is too much work. 

@gpsmikey And doing everything from a live cd (handmade live-dvd with al the software and codecs I want ...). That is too much work and too slow. And if I safe everything externally, I might as well run a passwordless ubuntu from HD.

---

### Post by bodhi.zazen on 2008-11-22
> **bro said:**
> So this encryption of /home? Is it a big strain on performance? 
Come to think about it, I'm going to tell firefox to forget my passwords right now.


IMO, the easiest is to install with the alternate CD, and no an encrypted / or /home is not a huge performance hit.

It is important, however, to understand the limitations of encryption, namely that when you boot or mount an encrypted partition the information is decrypted, so encryption only helps you when someone tries to boot or access your data with the partition un mounted.

8.10 now comes with an encrypted directory in your home directory by default.

---

### Post by bro on 2008-11-22
> **bodhi.zazen said:**
> encryption only helps you when someone tries to boot or access your data with the partition un mounted.

My /home is on a seperate partition. If I would, say, reinstall and tell it to mount the same encrypted partition as /home without formatting. That would work? I mean it needs a password right? Otherwise when does encryption work? 

Scenario: I have an encrypted /home. Somebody steels my laptop and changes my passwords as per method that started this topic. That encrypted /home would NOT help me? Then why encrypt?

---

### Post by bodhi.zazen on 2008-11-22
> **bro said:**
> My /home is on a seperate partition. If I would, say, reinstall and tell it to mount the same encrypted partition as /home without formatting. That would work? I mean it needs a password right? Otherwise when does encryption work? 

Scenario: I have an encrypted /home. Somebody steels my laptop and changes my passwords as per method that started this topic. That encrypted /home would NOT help me? Then why encrypt?

Take a look at LUKS. 

The point of encryption is that you can not access the data without the password. The password can not be changed easily and not without the original  password. In addition you can use a key.

[http://www.debuntu.org/how-to-encrypted-partitions-over-lvm-with-luks](http://www.debuntu.org/how-to-encrypted-partitions-over-lvm-with-luks)

[http://luks.endorphin.org/dm-crypt](http://luks.endorphin.org/dm-crypt)

My point is that once you enter the password, the data is decrypted and potentially accessible, so you need to unmount the crypt or turn off your computer when not in use.

---

### Post by iKonaK on 2008-11-22
I read all the post's but i feel i must be mentioned encfs, encfs encrypts your sensitive files and is pretty fast compared with other encryption tool i had deal with; you can install it by installing "cryptkeeper" (a GUI for the encfs)

---

### Post by bro on 2008-11-22
So it would help me to encrypt my /home. That somebody might enter when my computer is on... yes, but that's another problem, I'm not to scared that will happen. I'm just an average laptop user behind his firewall and all. The chance of the laptop being stolen is much higher. 

Nevertheless, not all the data is decrypted magically at once is it? Somehow it must be decrypting it on the fly when I access data, so the one hacking into it while my computer is on, should also be 'me' as a user?

---

### Post by billgoldberg on 2008-11-22
You have physical access to any system, you're in.

And it should be that way.

I don't see why this is a big deal.

If someone breaks into your house, I doubt they will care about hacking into you computer.

And if they steel it, it will be to either use for themselfs or sell, either way they will erase everything, unless you think they care about your text documents or something.

---

### Post by digicidal on 2008-11-23
@bro:
It's funny you should bring up the Patriot Act - it is that reason that I don't do anything via email other than chat with my family and friend about casual subjects.  Unfortuately, I have the 'privilege' of living in a country where ISP's and corporations are not just allowed to archive every single email that crosses their networks... in most cases they are compelled to do so.

I work in IT for a government agency here, and I will be held liable if I am not able to surrender copies of email correspondence for any users at my company that are requested via subpoena.:shock:

For that reason (and others) I have set up all of my online banking accounts over the phone or in person, and have done so without providing an email account.  It would make it a real pain if I lost my password (but again, something that I could take care of in person).

In my experience, the most likely cause for theft/fraud/etc.. is not the guy that broke into your home, or is sitting next to you in a coffee shop - but the disgruntled tech at your ISP or your employee/co-worker. (Although if you use your computer on a public wifi connection you might as well just tape your account info to your forehead!) [-X

---

### Post by jimi_hendrix on 2008-11-23
very disturbing...good thing there are 2 people in my town that know how to use linux

---

### Post by michaelzap on 2008-11-23
I just recommend a few "reasonable" methods for people with laptops who are worried about the security of their data:
[LIST]
[*]Use full-disk encryption (LUKS or TrueCrypt)
[*]Store all account info and other sensitive data in KeePassX
[*]Use GPG for encrypted email if you need that
[*]Set a master password in Firefox if you store personal info there
[*]Never send passwords or other sensitive data in the clear over an insecure network (cybercafes, conferences, etc.) - at a minimum always use SSL connections, and if needed use Tor
[*]If you save sensitive data to a USB drive or other removable media, encrypt it with GPG
[*]Make sure that you have a secure, reliable, offsite backup system and that the data there is current (I use JungleDisk/Amazon S3)
[*]Don't use passwords that are easy to break. Have a guest account with a different password if you need to allow others to use your system. Change your main passwords at least once a year. Never use the same passwords for systems that you do not control (online banking, email, etc.) as you do for your own data.
[*]If you are truly concerned about the safety of your data, you probably shouldn't use Windows as your main operating system and definitely shouldn't have that data accessible to a Windows system that is used for downloading files
[/LIST]
I find that implementing these methods is actually pretty painless and doesn't adversely affect my system performance or general workflow.

---

### Post by jase21 on 2008-11-29
Hi,

Using: Ubuntu 7.10- Gusty Gibbon
There is an option during booting:

ubuntu ... kerner 2.xxxx...(recovery mode)

which directly gives the user with root privilage.
Giving a startx gets the desktop as a root,

Instead of directly logging in as root it would better to ask the user of the root password.

I posted this in launchpad. Actually confusion where to post.

Thank You.

---

### Post by blakjesus on 2008-12-18
If there is a way to either figure out or change the user's password, wouldn't that be a major security concern?

---

### Post by iponeverything on 2008-12-18
> **blakjesus said:**
> If there is a way to either figure out or change the user's password, wouldn't that be a major security concern?

If a bad guy has physical access to your machine, being able to log into the box in recovery mode and reset the password would be the least of your problems.

;)

---

### Post by blakjesus on 2008-12-18
> **iponeverything said:**
> If a bad guy has physical access to your machine, being able to log into the box in recovery mode and reset the password would be the least of your problems.

;)

Hmmm... Well, its a good thing that no one i personally know has only moderate windows computer knowledge. Although, as an extreme measure, what if i set my bios to not boot to a cd at all, set up a bios password, and then edited my grub to not even give a choice for alternate boot options. Would that lock my computer down enough? (I'm not actually going to do it, i just want to learn)

That way everything is locked by passwords and you can't boot into a live cd to change stuff.

(Also forget the fact that they could pull my hard-drive and other stuff out of my computer to get to my stuff) :p

---

### Post by taurus on 2008-12-18
> **blakjesus said:**
> Hmmm... Well, its a good thing that no one i personally know has only moderate windows computer knowledge. Although, as an extreme measure, what if i set my bios to not boot to a cd at all, set up a bios password, and then edited my grub to not even give a choice for alternate boot options. Would that lock my computer down enough? (I'm not actually going to do it, i just want to learn)

That way everything is locked by passwords and you can't boot into a live cd to change stuff.

(Also forget the fact that they could pull my hard-drive and other stuff out of my computer to get to my stuff) :p

Nope.  I can remove the battery on the mobo for 30 minutes and your machine will reset it back to default so setting a password to get into the BIOS is useless if somebody has a physical access to your machine.

That's why large corporations lock their machines in a secure room with password on the lock and only give limited access to a certain people.

---

### Post by jerome1232 on 2008-12-18
> **blakjesus said:**
> Hmmm... Well, its a good thing that no one i personally know has only moderate windows computer knowledge. Although, as an extreme measure, what if i set my bios to not boot to a cd at all, set up a bios password, and then edited my grub to not even give a choice for alternate boot options. Would that lock my computer down enough? (I'm not actually going to do it, i just want to learn)

That way everything is locked by passwords and you can't boot into a live cd to change stuff.

(Also forget the fact that they could pull my hard-drive and other stuff out of my computer to get to my stuff) :p

If you wanted to protect your computer from physical access use full disk encryption, maybe for more annoyance slap a good lock on the case to make it difficult to open.

With full disk encryption no one can get into recovery mode (or anything on your hard disk for that matter) without knowing your long and difficult to guess passphrase that unlocks the encryption.

edit: As an aside you don't even have to pull the battery out for 30 minutes, you can short the cmos jumper for 3 seconds and get the same affect.

---

### Post by albinootje on 2008-12-18
> **blakjesus said:**
> Hmmm... Well, its a good thing that no one i personally know has only moderate windows computer knowledge. Although, as an extreme measure, what if i set my bios to not boot to a cd at all, set up a bios password, and then edited my grub to not even give a choice for alternate boot options. Would that lock my computer down enough? (I'm not actually going to do it, i just want to learn)

That way everything is locked by passwords and you can't boot into a live cd to change stuff.

(Also forget the fact that they could pull my hard-drive and other stuff out of my computer to get to my stuff) :p

That would not be enough because you can "live" edit the grub boot menu entries and make it boot into "recovery mode".
If you are surrounding by bad people and/or if you are paranoid about this, then set a difficult to guess root password, and then the "recovery mode" will ask you for that password instead of letting you enter that mode without any password.

(And apart from disabling booting from cd, there's probably the BIOS boot menu where people can boot from usb, isn't it ? Or will setting a BIOS password also disable the BIOS provided boot-menu ?)

---

### Post by blakjesus on 2008-12-18
Ok thanks for the info. I really don't have any reason to be that paranoid, i just wanted to learn a little bit about that.

---

### Post by jerome1232 on 2008-12-18
> **albinootje said:**
> That would not be enough because you can "live" edit the grub boot menu entries and make it boot into "recovery mode".
If you are surrounding by bad people and/or if you are paranoid about this, then set a difficult to guess root password, and then the "recovery mode" will ask you for that password instead of letting you enter that mode without any password.

(And apart from disabling booting from cd, there's probably the BIOS boot menu where people can boot from usb, isn't it ? Or will setting a BIOS password also disable the BIOS provided boot-menu ?)

The problem with that method is if I take out the hard disk and slip it into another computer or a usb enclosure I can gain full access to the data/files on it regardless. Or just boot into a live cd and hand edit some files.

Which is why I say full disk encryption and physical security (locked case, locked room etc...) are the only answers for securing the computer locally.

---

### Post by albinootje on 2008-12-18
> **jerome1232 said:**
> The problem with that method is if I take out the hard disk and slip it into another computer or a usb enclosure I can gain full access to the data/files on it regardless. Or just boot into a live cd and hand edit some files.

Which is why I say full disk encryption and physical security (locked case, locked room etc...) are the only answers for securing the computer locally.

The remark from the poster i've responded to was : "(Also forget the fact that they could pull my hard-drive and other stuff out of my computer to get to my stuff)". Hence my answer.

And concerning disk-encryption, a while back some new method was found to "freeze" the state of the RAM memory, and being able to get the passphrase (or keyfile content) from that.

Of course disk-encryption adds a good extra layer (Provided that you don't forget the passphrase or the keyfile), but it doesn't give you a theoretical 100% security.

(And i would not recommend disk-encryption to people who forget passwords easily.) :)

---

### Post by jerome1232 on 2008-12-18
I definitly see your point about not recomending full disk encryption on a "I forgot my password thread"!!!!

Ah I didn't catch that in the original post my bad; and yes I know about being able to retrieve the key from ram. While I agree the encryption isn't 100%, it's certainly the method that is most difficult to bypass, and requires situational circumstance to happen (the computer being on with the disks unlocked and the key stored in ram in this case)



I actually (forgot which brand) know there's a laptop that has a unique password placed on bios out of the factory, and so you can't simply reset bios as it'll have this unique password on it still. In that case I consider it's bios level security very good.

---

### Post by Dragonbite on 2008-12-18
Run everything  through LTSP (thin clients) and make sure the actual server is physically locked in a room.

That way they can take the whole darn client and it isn't going to get them any of my information unless they can get to the server.

---

### Post by sintacto on 2008-12-24
I'm not sure what other releases has this same feature but it's kinda sketchy

1) walk up to pc and restart or turn on

2) press escape button at start up

3) choose recovery mode

4) a menu pops up with boot to root terminal as a option and with networking to.

No password at all

---

### Post by Naddiseo on 2008-12-25
Ubuntu doesn't have a root password by default. If you set one yourself, then that trick doesn't work.

---

### Post by sintacto on 2008-12-25
it could ask for a user password?
who is a sudoer
my friend and I always change each others settings (fonts,wallpaper,homepage,themes) when there not looking, this makes it so easy.
they can't touch my debian install heehee
o I'm planing evil now.(unicorns rainbows,window managers, pink theme.)hee hee

---

### Post by sintacto on 2008-12-25
Im making a theme bomb on usb stick now

---

### Post by HotShotDJ on 2008-12-25
> **sintacto said:**
> I'm not sure what other releases has this same feature but it's kinda sketchyPhysical access to the hardware is a security risk no matter what you do.  Of course it is possible to protect against only the most casual intruder by setting a root password, but all they have to do is pop in a CD-ROM to gain full access no matter what you do with the software, including password protecting GRUB.  One COULD password protect the BIOS and disable booting from a CD/DVD, USB, etc., but if one has access to the machine, it is a simple matter to for the determined intruder to reset the BIOS.

In other words, once an individual has their hands on your hardware, it is generally GAME OVER.

---

### Post by MacUntu on 2008-12-25
That's why you encrypt sensitive data.

---

### Post by sintacto on 2008-12-25
I was only suggesting a prank

"In other words, once an individual has their hands on your hardware, it is generally GAME OVER."

I agree. but more thieves than hackers around here. (not my friends) I think they would install window$ and sell for drug money.

but would it be hard for ubuntu to ad a user password there and not an extra one for root? 
Is there a possability for some one to boot a  computer from a network (boot from lan) with another os or os on hard drive remotely?  I mean the computer is off and connected to Ethernet to internet?   

get to root that way, remotely? (probably not but just asking )

---

### Post by albinootje on 2008-12-25
> **sintacto said:**
> 
4) a menu pops up with boot to root terminal as a option and with networking to.

No password at all
This has been possible in Ubuntu since quite a few releases.
If you're worried that others might "benefit" from this, set a root password.
See :
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by RAOF on 2008-12-25
This has been raised a couple of times over the years on various lists.  The consensus is that the convenience of the recovery mode well outweighs its (small) security implications.  Even without the recovery mode entry, you can edit the boot entry from grub to do the same thing.

---

### Post by chris062689 on 2008-12-25
Is there any way you can think of them being able to "re-add" the recovery option without sudo privileges?  I normally just comment it out on a fresh Ubuntu install.

Also; if your /home partition is encrypted, a Live CD wouldn't be able to read it without the key, right?

---

### Post by RAOF on 2008-12-25
> **chris062689 said:**
> Is there any way you can think of them being able to "re-add" the recovery option without sudo privileges?  I normally just comment it out on a fresh Ubuntu install.

By editing the kernel line from the grub prompt.  Alternatively, by booting from a live CD.

> **chris062689 said:**
> 
Also; if your /home partition is encrypted, a Live CD wouldn't be able to read it without the key, right?

Right.  Encryption is easily the most secure option.  Although, if you really, really care, only encrypting /home will potentially leave the keys or sensitive data lying around unencrypted in swap.

---

### Post by sarang on 2008-12-25
> **hotshotdj said:**
> physical access to the hardware is a security risk no matter what you do.  Of course it is possible to protect against only the most casual intruder by setting a root password, but all they have to do is pop in a cd-rom to gain full access no matter what you do with the software, including password protecting grub.  One could password protect the bios and disable booting from a cd/dvd, usb, etc., but if one has access to the machine, it is a simple matter to for the determined intruder to reset the bios.

In other words, once an individual has their hands on your hardware, it is generally game over.

+1, though considering the rate at which performance of encrypted volumes is becoming better, this might change soon.

---

### Post by lswb on 2008-12-25
You can add a password to grub in various ways, such as requiring a pw to edit the boot lines or to select a certain boot option, or to block booting entirely until a password is entered.

---

### Post by sintacto on 2008-12-26
thank you naddiseo
thank you HotShotDJ
thank you MacUntu
thank you albinootje
thank you RAOF
thank you Sarang
thank you lswb

one question if i was to encrypt say my /home folder could I still share it on my home network?
or would I need a key on each pc?

---

### Post by SikEnCide on 2009-03-31
I do not know if I am the only one to really notice this but, Ubuntu poses an inherent threat when installed.

If someone were to attempt to login to you computer the could in fact change your password or even create their own as long as they have physical access to your computer.

How is this possible?

Simple when you install Ubuntu it never askers for a root password. THIS IS BAD BAD BAD BAD BAD. Ubuntu is the ONLY distro I have tried (and I have tried a lot) that does not make you create a root password.

You can simply reboot a computer and on grub select the recovery boot option. Tell it to drop to root. It askes for a root password so just hit enter and you in as root.

You now have free rein over the computer you can create or remove users, change or remove passwords, or you could do worse if your really malicious.



So the question I have ot the Ubuntu developers and the community.

Is this done on purpose? If so why? and If this was not known how could you not. I hope there is an upcoming fix. I know a user could simply set a root password but if you ask on install you eliminate a threat that a normal user may not know about.

---

### Post by srt4play on 2009-03-31
This subject has been beaten to death and back. Physical access to a computer effectively negates the security features of any operating system.

---

### Post by hyper_ch on 2009-03-31
and if someone gains physical access to your windows computer they can also get all data they want... encryption is the only option here.

---

### Post by sisco311 on 2009-03-31
in other distros(by default) you can add init=/bin/bash 
to the kernel line in grub to boot into a root shell. 

is that safer?

> **hyper_ch said:**
> and if someone gains physical access to your windows computer they can also get all data they want... encryption is the only option here.

+1

---

### Post by bodhi.zazen on 2009-03-31
> **srt4play said:**
> This subject has been beaten to death and back. Physical access to a computer effectively negates the security features of any operating system.

+1 , what a breath of fresh air to these discussions as well.

Moved to recurring discussions.

---

### Post by bodhi.zazen on 2009-03-31
> **sisco311 said:**
> +1

in other distros(by default) you can add init=/bin/bash to the kernel line in grub to boot into a root shell. how is this safer?

You can not do that if grub is password protected (not that I am advocating BIOS or gurb passwords, I do not feel they add all that much because ....)

You can ALWAYS boot a live CD and access the hard drive or pull the hard drive and access it from another box.

---

### Post by sisco311 on 2009-03-31
> **bodhi.zazen said:**
> You can not do that if grub is password protected (not that I am advocating BIOS or gurb passwords, I do not feel they add all that much because ....)

You can ALWAYS boot a live CD and access the hard drive or pull the hard drive and access it from another box.

Yes, i know. I was talking about "default" settings.

---

### Post by saulgoode on 2009-03-31
> **bodhi.zazen said:**
> You can not do that if grub is password protected (not that I am advocating BIOS or gurb passwords, I do not feel they add all that much because ....)

You can ALWAYS boot a live CD and access the hard drive or pull the hard drive and access it from another box.
If you password protect your BIOS and it has been configured to only boot from the hard drive, there is no way to boot from a live CD. 

Taking apart a computer and removing a hard drive might make co-workers or family members just a little bit more suspicious than someone typing at a keyboard. And even at that, having someone steal your data at a certain point in time is not as potentially compromising as them having continual access to your system without your knowledge.

Nonetheless, what Cisco311 stated is very much true for many distros: if your bootloader is not password-protected then users can obtain root access.

---

### Post by Dragonbite on 2009-03-31
> **SikEnCide said:**
> Simple when you install Ubuntu it never askers for a root password. THIS IS BAD BAD BAD BAD BAD. Ubuntu is the ONLY distro I have tried (and I have tried a lot) that does not make you create a root password.

Actually when I recently did an openSUSE installation it didn't ask for a root password and whenever root access is needed I just use my login password (same as Ubuntu).  Haven't tried hacking into it from the login screen yet though.

---

### Post by cariboo on 2009-03-31
@saulgoode

If you have physical access to a computer, it takes less than 5 minutes to clear a bios password. You don't have to remove the hard drive.

Jim

---

### Post by ashmew2 on 2009-05-11
We've come 21 pages and the debate still goes on.

Bottom Line : There is no password required for accessing root shell.
Advice : There SHOULD be a password..I mean come on , people who use Ubuntu regularly , why cant they enter a friggin password of say 12 characters once when they screw up their PC ?

---

### Post by ashmew2 on 2009-05-11
> **cariboo907 said:**
> @saulgoode

If you have physical access to a computer, it takes less than 5 minutes to clear a bios password. You don't have to remove the hard drive.

Jim

Also , if you have physical access to a computer say a friend's whose PC doesnt require you to enter a password to become root , your friend's fried in say under 1 minute ?

Even for physical access , a password wont hurt much..would it ? To anyone who says that physical access is root access and the system can be controlled like root in 5 minutes...then why not put a password so that the vandal needs at least 7 minutes in place of 5 ?

---

### Post by starcannon on 2009-05-11
As has been mentioned before, physical access means just that, a determined individual will get into your machine using one of the various methods already described.

Since there is no way to stop a determined individual from accessing your data when/if they have physical access to you computer, then all your left with is the old "Keeping Honest People Honest" routine.

To do this AND keep the computer useful, I would recommend a bios administration password, again only to keep honest users honest, I would set the grub timer to 0 so that the menu does not even appear at boot time, the admin will know how to get a menu its a non issue. This pretty much solves the problem, and there is nothing, zip, zero, zilch, nada that your going to do to stop a determined person with physical access to the computer; so all the complex password schemes won't work. I suppose perhaps a hidden and encrypted partition would slow them down a bit, but determination would win the day for them.

Just thought I'd beat on the carcass for a moment as well :)

GL and have fun :KS

---

### Post by cdenley on 2009-05-11
> **ashmew2 said:**
> Also , if you have physical access to a computer say a friend's whose PC doesnt require you to enter a password to become root , your friend's fried in say under 1 minute ?

Even for physical access , a password wont hurt much..would it ? To anyone who says that physical access is root access and the system can be controlled like root in 5 minutes...then why not put a password so that the vandal needs at least 7 minutes in place of 5 ?

It doesn't take much time at all to boot to a cd, usb drive, or floppy, mount the disk, then edit /etc/shadow. Just about as long as it would take to use recovery mode.

Are you suggesting that the user be prompted for the password of an admin user? Certainly you're not suggesting that a root password be set? Recovery mode is usually used when the user forgot their password or removed themselves from the admin group. If they needed an admin password in order to use recovery mode, then it would be useless in that situation.

---

### Post by ashmew2 on 2009-05-12
> **cdenley said:**
> It doesn't take much time at all to boot to a cd, usb drive, or floppy, mount the disk, then edit /etc/shadow. Just about as long as it would take to use recovery mode.

Are you suggesting that the user be prompted for the password of an admin user? Certainly you're not suggesting that a root password be set? Recovery mode is usually used when the user forgot their password or removed themselves from the admin group. If they needed an admin password in order to use recovery mode, then it would be useless in that situation.

I agree with the forgot password thingy and that you cannot password protect it since you've already forgotten your password. But , someone else can of course screw up your system pretty bad because that person too doesnt need a password. So there's no stopping him. IF there was a password , it would take at least some time to bypass/crack the password..?

---

### Post by bashphoenux on 2009-05-12
> **koenn said:**
> you set a password on the root account with
```

sudo -i
passwd root
exit

```
thanks i needed this .. just now received my ubuntu shipment and installed it .. wanted to know how to set su password and your post helped 

thanks

---

### Post by cdenley on 2009-05-12
> **ashmew2 said:**
> IF there was a password , it would take at least some time to bypass/crack the password..?

It doesn't take long to boot to a CD, mount the disk, and edit the root password. It is easy for someone who knows what they're doing, but difficult for some new user that forgot their password. No matter what, a user that forgot their password will be in the same position as a malicious person with physical access. Since physical users can get access anyway, there isn't much additional risk, but it saves a lot of people a lot of trouble when they forget their password or remove themselves from the admin group.

> 
thanks i needed this .. just now received my ubuntu shipment and installed it .. wanted to know how to set su password and your post helped

Posting those commands aren't allowed here for a reason, and I hope you understand what you are doing.

---

### Post by albinootje on 2009-05-12
> **cdenley said:**
>  Posting those commands aren't allowed here for a reason, and I hope you understand what you are doing.

Indeed. The person who asked that, should read this carefully :
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

And to disable the root password, do this : 
```

sudo usermod -L root

```

---

### Post by meeples on 2009-07-23
sorry if this has already been mentioned because i dont have he patience to read all the posts on this thread but.

what i find unnerving is all anyone has to do to access my files on ubuntu is use an ubuntu live disk. full access to everything. even system files by gaining the live disk's own root privelages.

there has to be a way to make the os more secure.

---

### Post by Smartin on 2009-07-23
> **meeples said:**
> sorry if this has already been mentioned because i dont have he patience to read all the posts on this thread but.

what i find unnerving is all anyone has to do to access my files on ubuntu is use an ubuntu live disk. full access to everything. even system files by gaining the live disk's own root privelages.

there has to be a way to make the os more secure.

There *are* ways of making your box more secure.

BIOS passwords, encryption etc.

Take the CD drive out when your back is turned... :D

S

---

### Post by meeples on 2009-07-23
> **Smartin said:**
> There *are* ways of making your box more secure.

BIOS passwords, encryption etc.

Take the CD drive out when your back is turned... :D

S

too much work for noobs like me;)


i'll rephrase,

Ubuntu should make my computer more secure!

---

### Post by Mornedhel on 2009-07-23
> **meeples said:**
> too much work for noobs like me;)


i'll rephrase,

Ubuntu should make my computer more secure!

The first rule of secure computing is simple.

If a malicious user has physical access to the computer, it's over for you. Especially if he also carries a screwdriver.

The second rule of secure computing is also simple.

If a malicious user has physical access to you, he doesn't even need the first rule.

---

### Post by bodhi.zazen on 2009-07-23
> **meeples said:**
> sorry if this has already been mentioned because i dont have he patience to read all the posts on this thread but.

what i find unnerving is all anyone has to do to access my files on ubuntu is use an ubuntu live disk. full access to everything. even system files by gaining the live disk's own root privelages.

there has to be a way to make the os more secure.

It is unnerving when you learn this.

Why do you think they keep servers in locked rooms ?

The only viable option , IMO, is encryption. Grub and bios passwords are easily defeated.

And of course if someone has physical access nothing prevents pulling the hard drive, wiping the drive, poring coffee into the intake fan, for simply smashing the box with a sldege hammer.

Physical access = pure pwnage , game over, !epic fail.

---

### Post by aysiu on 2009-07-23
> **meeples said:**
> 
what i find unnerving is all anyone has to do to access my files on ubuntu is use an ubuntu live disk. full access to everything. even system files by gaining the live disk's own root privelages.

there has to be a way to make the os more secure. It has nothing to do with the OS.

Using a Ubuntu live disk, you can access everything on a Windows computer as well, or on a Mac.

Physical access is root access *for any operating system*.

You can try to slow down the compromise by passwording Grub, passwording the BIOS. But unless you have encrypted your files and folders, anyone with physical access, a little time, and a little know-how has access to everything.

---

### Post by meeples on 2009-07-23
> **aysiu said:**
> It has nothing to do with the OS.

Using a Ubuntu live disk, you can access everything on a Windows computer as well, or on a Mac.

Physical access is root access *for any operating system*.

You can try to slow down the compromise by passwording Grub, passwording the BIOS. But unless you have encrypted your files and folders, anyone with physical access, a little time, and a little know-how has access to everything.

i dont see how the OS cant do anything about it,

why cant a users files only be accessed by that user? whether the OS is on a live disk or on your hard drive only if you have the password should you be able to access the files.

and FYI just because Apple and Microsoft haven't done anything about it, doesn't mean Canonical/Ubuntu should follow suite.

stop comparing Ubuntu to other operating systems, whether what im saying is possible or not, Ubuntu shouldnt do things just because OS X or Windows does, it can do its own thing.

---

### Post by heyyy on 2009-07-23
> **MJN said:**
> That's because by default there isn't one...
 
Check the archives as this is becoming FAQ #1!
 
The bottom line is that whilst this may initially sound alarming think about it - if someone has got physical access to your machine to boot into recovery mode then they've got access to everything anyway (unless your disks are encrypted). Even with a root password they can easily boot with a LiveCD, change the password files, restart and they're in.
 
Mathew

could you give a link or two on how to encrypt?

---

### Post by jerome1232 on 2009-07-23
Hasn't this horse been beat dead enough?

An OS can't protect your files when the OS isn't running.

The answer is, if you want this level of security, Fully Encrypt Your Disks. There now no one can access your files without first unlocking the encryption.

---

### Post by aysiu on 2009-07-23
> **meeples said:**
> whether what im saying is possible or not, Ubuntu shouldnt do things just because OS X or Windows does, it can do its own thing. If something is impossible, how can Ubuntu do it?

By definition, the impossible is what can't be done.

I've already explained to you that if you want to protect your files from a live CD, you have to encrypt the files. My point about bringing up OS X and Windows is not to say that we need to be like other operating systems. My point was that it doesn't matter what operating system you use.

The operating system and how it's built has *nothing* to do with whether a live CD can compromise files or not.

---

### Post by bodhi.zazen on 2009-07-23
he he he ....

be nice , meeples is in "shell shock" , lol.

Nothing like this kind of information to make one more aware of security, too many people ignore security.

meeples , why do you think they call them "recovery disks" or "recovery tools", lol. They are tools and, like all tools, can be mis used.

The primary focus of teh Ubuntu live CD is to test drive and install Ubuntu, but the tools to mount, read, and modify files on your hard drive are but an apt-get away.

Take a deep breath and take a look at encryption if this bothers you. If encryption is "too hard" well I guess that tells us how much you value your data (many encryption tools are a snap, truecrypt for one).

---

### Post by meeples on 2009-07-23
> **bodhi.zazen said:**
> he he he ....

be nice , meeples is in "shell shock" , lol.

Nothing like this kind of information to make one more aware of security, too many people ignore security.

meeples , why do you think they call them "recovery disks" or "recovery tools", lol. They are tools and, like all tools, can be mis used.

The primary focus of teh Ubuntu live CD is to test drive and install Ubuntu, but the tools to mount, read, and modify files on your hard drive are but an apt-get away.

Take a deep breath and take a look at encryption if this bothers you. If encryption is "too hard" well I guess that tells us how much you value your data (many encryption tools are a snap, truecrypt for one).

> **aysiu said:**
> If something is impossible, how can Ubuntu do it?

By definition, the impossible is what can't be done.

I've already explained to you that if you want to protect your files from a live CD, you have to encrypt the files. My point about bringing up OS X and Windows is not to say that we need to be like other operating systems. My point was that it doesn't matter what operating system you use.

The operating system and how it's built has *nothing* to do with whether a live CD can compromise files or not.

lol. ok.


why cant ubuntu encrypt our files then?

---

### Post by jerome1232 on 2009-07-23
It can, if you use the alternate install cd there is the option of setting up lvm and encryption using dm-crypt. Alternatively you can use Truecrypt.

This would be horrible to have setup as default for a number of reasons.

Encrypted partitions are more susceptible to data loss, if you lose certain sections of the partition that have to do with the encryption, you will forever lose everything on the disk.

edit: You can make backups of these important sections if I remember right.

If you forget your passphrase, you forever lose everything on the disk

There is a performance penalty, every time something is read/written to disk it must be de/encrypted on the fly. If you are doing a lot of file transfers this can be a heavy performance penalty.

---

### Post by meeples on 2009-07-23
> **jerome1232 said:**
> It can, if you use the alternate install cd there is the option of setting up lvm and encryption using dm-crypt. Alternatively you can use Truecrypt.

This would be horrible to have setup as default for a number of reasons.

Encrypted partitions are more susceptible to data loss, if your lose certain sections of the partition that have to do with the encryption, you will forever lose everything on the disk.

If you forget your passphrase, you forever lose everything on the disk

There is a performance penalty, every time something is read/written to disk it must be de/encrypted on the fly. If you are doing a lot of file transfers this can be a heavy performance penalty.

that sucks.

---

### Post by aysiu on 2009-07-23
> **meeples said:**
> that sucks.
Well, that's why live CDs are great. You don't lose everything forever, even if the operating system won't boot up, even if you've forgotten your password.

---

### Post by Dragonbite on 2009-07-24
> **jerome1232 said:**
> Hasn't this horse been beat dead enough?

An OS can't protect your files when the OS isn't running.

The answer is, if you want this level of security, Fully Encrypt Your Disks. There now no one can access your files without first unlocking the encryption.

On the plus side, the same principal works with Viruses (at least in Windows). So using a LiveCD you can run a virus scan which doesn't "tip off" the virus and allows it to enact a self-replication scheme.

---

### Post by sashag on 2009-07-25
> **Cybergod said:**
> Below is a link that explains how to boot to a root shell without a password.  I was very surprised when I read this.  How could a Network/System Admin prevent users from doing this on their Workstation?

[http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html]("http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html")

Hi!

I'm a newbie when it comes to Linux 9.04, and my biggest problem is that although I DID set the username and password when I first
installed Linux, when I get to the login screen and put in the
correct username and password, I keep getting told that I DID NOT
put in the correct username or password. Is there a 'general'
username and password that I can use without having to 'reset' 
the password and username? I like the new version of Linux, however, I can't even get into the program without having the right username and password! Thanks!

---

### Post by aysiu on 2009-07-25
> **sashag said:**
> Hi!

I'm a newbie when it comes to Linux 9.04, and my biggest problem is that although I DID set the username and password when I first
installed Linux, when I get to the login screen and put in the
correct username and password, I keep getting told that I DID NOT
put in the correct username or password. Is there a 'general'
username and password that I can use without having to 'reset' 
the password and username? I like the new version of Linux, however, I can't even get into the program without having the right username and password! Thanks!
What's wrong with resetting the password? It's not that difficult:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

And, no, there is no general username and password you can use. Just reset it.

---

### Post by heyyy on 2009-08-01
one question which has been probably answered if someone has physhical access to an encrypted hdd the only protection is a good password....?
am i right or is there something else too?

---

### Post by juancarlospaco on 2009-08-01
For example, if i got a Rocket Launcher that means Physical access is root access :)

---

### Post by JT9161 on 2009-08-01
> **heyyy said:**
> one question which has been probably answered if someone has physhical access to an encrypted hdd the only protection is a good password....?
am i right or is there something else too?

True, Its why one should also have a strong password

---

### Post by running_rabbit07 on 2009-08-04
> **NIKOSHIBA said:**
> you got a point. but then again, why ask password and username at normal startup then? i think this is an a serious issue.
linux is all about security and stability. i think at install everything must be, as you have sad, encrypted. otherwise nothing much makes a sense.

To easily fix this lttle problem go into BIOS and set a boot password. Then the perp will have to find the reset on your motherboard.

---

### Post by yabbadabbadont on 2009-08-04
> **running_rabbit07 said:**
> To easily fix this lttle problem go into BIOS and set a boot password. Then the perp will have to find the reset on your motherboard.

As long as the case is open, they could just pull out your hard drive(s) and peruse them at their leisure...

---

### Post by running_rabbit07 on 2009-08-05
> **yabbadabbadont said:**
> As long as the case is open, they could just pull out your hard drive(s) and peruse them at their leisure...

That's where an encrypted hard drive pays off. You can only do so much. You could pay a couple grand to get a German Shepard trained to protect your house, but then the burglar shoots the dog, now you've lost even more.

---

### Post by Mornedhel on 2009-08-05
It's simple.

Physical access is root access, full stop. The only defense you may have is disk encryption, and that is only as strong as your passphrase is. Not to mention that it has adverse effects on IO performance and that other attack vectors exist, see [http://it.slashdot.org/article.pl?sid=09/08/01/2247225](http://it.slashdot.org/article.pl?sid=09/08/01/2247225)

Also social engineering attacks are the easiest and often the most efficient.

---

### Post by Dragonbite on 2009-08-05
If somebody wants to rob your house enough, they are going to rob it regardless of what you do. The key is to make it so difficult that only the most capable, fanatical or obsessive person would even TRY to!

---

### Post by running_rabbit07 on 2009-08-05
> **Mornedhel said:**
> Also social engineering attacks are the easiest and often the most efficient.

That is why I get aggravated every time someone sends me one of those chain mails asking what your fav color or song or whatever, because they phish enough info out of you to figure out your passwords, or at least that is the objective. Of, course I always get the response that I am too paranoid.

---

### Post by The Real Dave on 2009-08-05
If someone can boot another OS from your computer, thats it, they've got ya. BIOS and GRUB passwords, and even full harddrive encryption wont stop a really persistant attacker (though the latter will definately slow them right down ;))

Its why servers are kept in locked rooms, often with locked cases. 

In fact, the IT guy at my school went one further. In the server-room, there was 3 optical drives. I went in with my BackTrack disk to the drive on the main server, the other ones I knew were just web, print, and a server for the school office. Turns out that our IT guy (utter legend of a man all the same), had rigged the main server, so that the optical drive in the office server was actually the one connected to it (dont ask me how :lolflag:) The server's optical drive was booby trapped, upon opening, it triggered a 120Db alarm above it. That was one prank that turned out quite wrong, though, it did make me good friends with our IT teacher, who had definately earned my respect! :D

---

### Post by aysiu on 2009-08-05
> **The Real Dave said:**
> even full harddrive encryption wont stop a really persistant attacker (though the latter will definately slow them right down ;)) How does full disk encryption *not* stop a persistent attacker? Can you explain some more details? Are you assuming the password is easy to guess? Or are you assuming the attacker has a few thousand years to try guessing different passwords?

---

### Post by jerome1232 on 2009-08-05
My understanding is that unless the attacker has a few clustered modern super computers he is not cracking good encryption within this lifetime.

---

### Post by The Real Dave on 2009-08-05
What I mean is, if someone seriously seriously wants to get to your data, they will. Eventually. Might take time, but they will. Also, many passwords are quite easy to guess, hackers bruteforcing passwords often use dictionaries, then randomise the words, add numbers, change case etc. High power computers can guess several hundred passwords a second, or more. 

I realise though, that with a strong password, getting access to an encrypted drive is hard, and time consuming. It is not, however, impossible, if someone wants to badly enough, they will.

---

### Post by running_rabbit07 on 2009-08-05
I'd love to see the look on their face when they have done all that work for a few family photo albums and an out of date music collection. I mean how much would someone with those skills be paid? About 50 to 100 an hour for someone with the skills and equipment? They would definitely be happier getting a real job.

---

### Post by running_rabbit07 on 2009-08-05
> **The Real Dave said:**
> What I mean is, if someone seriously seriously wants to get to your data, they will. Eventually. Might take time, but they will. Also, many passwords are quite easy to guess, hackers bruteforcing passwords often use dictionaries, then randomise the words, add numbers, change case etc. High power computers can guess several hundred passwords a second, or more. 

I realise though, that with a strong password, getting access to an encrypted drive is hard, and time consuming. It is not, however, impossible, if someone wants to badly enough, they will.

Settings that allow only three tries per 15 minutes would really give them heartburn! Make the password be a line from an old crappy song like Karma Chameleon and they would never think of it.

---

### Post by The Real Dave on 2009-08-05
> **running_rabbit07 said:**
> Settings that allow only three tries per 15 minutes would really give them heartburn! 

Sure would =] TBH, I wouldn't bother encrypting my drives, nothing on them particularly that anyone would want :) Or at least, thats what they think ;)

---

### Post by Yes on 2009-08-05
> **aysiu said:**
> How does full disk encryption *not* stop a persistent attacker? Can you explain some more details? Are you assuming the password is easy to guess? Or are you assuming the attacker has a few thousand years to try guessing different passwords?

I saw a post awhile ago that showed how you could retrieve the password of an encrypted hard drive from the RAM, if you could get access to the RAM within about 10 minutes or so after turning the computer off.  Obviously not useful all the time, but it goes to show no matter how secure your password is under the right circumstances someone could always get to your data.

---

### Post by JT9161 on 2009-08-06
> **Yes said:**
> I saw a post awhile ago that showed how you could retrieve the password of an encrypted hard drive from the RAM, if you could get access to the RAM within about 10 minutes or so after turning the computer off.  Obviously not useful all the time, but it goes to show no matter how secure your password is under the right circumstances someone could always get to your data.

Called a Cold Boot Attack, and I think some seatings can be tweaked to be sure that encryption keys are flushed from RAM.

---

### Post by rocket16 on 2009-09-10
Hello to everybody here. Recently, I came to know that Ubuntu can be easily hacked, using the Grub bootloader. The Proceedure is as follows:
1. While loading Grub, hit "e" to edit the Ubuntu menu.
2. Now, press e to edit the Kernel.
3. Replace the last words "ro single" with "rw=/init/bash"
4. Press Enter to save
5. Press b to boot the kernel
6. Next, a command shell will open, while we are root
Now, using passwd and users command, from root-shell we can easily create a new account (temporarily), or change the root or user password. Thus Ubuntu is hacked. I tried the procedure too, and it works really. Some of my friends, who are Windows fans, heavily cornered us in our Linux Club in our locality, by telling that Ubuntu is insecure from hackers. I am sorry to say, that even Windows XP requires a CD or software such as Windows Installation CD or DreamPackPL to get hacked, and that takes time. I want to know, that how can we secure our Grub bootloader such that no one can make changes to it, making Ubuntu very secure? (I know of securing BIOS, but still that is inconvenient, since if the BIOS pass is forgotten, then it is nearly impossible fo a genereal user to acces the Computer, since then even Linux CDs won't work).

---

### Post by Grenage on 2009-09-10
Local access = owned on **all** systems.

---

### Post by rocket16 on 2009-09-10
Sorry, but I did'nt understand. Can you please tell me how to secure Grub?

---

### Post by scottuss on 2009-09-10
> **rocket16 said:**
> Sorry, but I did'nt understand. Can you please tell me how to secure Grub?

Grenage is stating that if someone gets local access to any machine, it has been compromised. At University we had locked down XP machines, didn't stop anyone rebooting them and booting from a USB stick loaded with Ubuntu.

Right there, that machine no longer had any restrictions. We had root access.

It's not a hack.

---

### Post by P4man on 2009-09-10
what he means, is that when you have physical access to a machine, no OS is secure. You can always boot in to some recovery mode, boot from a cd/stick, remove the harddrive... this is not exactly news.

If you want, you can set a password on your bios and/or in grub. Both will make it a bit harder, but neither are fail proof. You can circumvent a bios password by resetting the bios (requires opening the machine) and you can always rewrite grub from a livecd.  And you can still remove the drive and read whats on it on a different machine.

If you're concerned about the privacy of your documents, encrypt your home folder, and let "hackers" hack all they want. But you can not prevent anyone them using your computer when they have access to it.

---

### Post by binbash on 2009-09-10
Dude with local access you can hack every system easily. You can set a password to GRUB, or your HDD from bios.

---

### Post by Soul-Sing on 2009-09-10
: [http://ubuntuforums.org/showthread.php?t=715630](http://ubuntuforums.org/showthread.php?t=715630)

(fysical/local access means every system can be hacked)

---

### Post by rocket16 on 2009-09-10
Thanks to all, but still, Ubuntu is the best OS in the entire planet. So, it should defy all challenges.

---

### Post by barnex on 2009-09-10
You could use the "encrypted home folder" option when you install ubuntu. Even root can not read that.

By the way, there's usually some jumper on the motherboard to reset the BIOS. Local acces == owned system ;), no matter what.

---

### Post by rocket16 on 2009-09-10
Well, I think I may try that.

---

### Post by XCan on 2009-09-10
You surely can encrypt your home partition, or even our whole system partition (-boot), but that only prevents them from reading your information, it doesn't prevent them from sabotaging you. Lock the computer away, that's the safest.

---

### Post by Grenage on 2009-09-10
Sorry, I should have elaborated but was running out the door.  The other posters answered you much more completely.

---

### Post by earthpigg on 2009-09-10
> **rocket16 said:**
> Thanks to all, but still, Ubuntu is the best OS in the entire planet. So, it should defy all challenges.

a computer operating system is no replacement for locking the front door to your home....

---

### Post by overdrank on 2009-09-10
Moved to Recurring Discussions

---

### Post by SunnyRabbiera on 2009-09-10
No OS is 100% safe, really the only way to make sure nothing bad happens to your computer is to never turn it on.

---

### Post by scottuss on 2009-09-10
> **SunnyRabbiera said:**
> No OS is 100% safe, really the only way to make sure nothing bad happens to your computer is to never turn it on.

Yep. Even better, drop it into a vat of acid. That should ensure that no one can hack it.

---

### Post by sydbat on 2009-09-10
> **SunnyRabbiera said:**
> No OS is 100% safe, really the only way to make sure nothing bad happens to your computer is to never turn it on.

> **scottuss said:**
> Yep. Even better, drop it into a vat of acid. That should ensure that no one can hack it.Better yet, never buy one.

---

### Post by P4man on 2009-09-10
> **rocket16 said:**
> Thanks to all, but still, Ubuntu is the best OS in the entire planet. So, it should defy all challenges.

Think about this for a while. Imagine you would have some hardened computer you couldn't use or access without some key or password.. what would you do if it needed reinstalling? What if you forgot the password? You'd have to throw the computer away and lose your stuff.

An OS is just a piece of software. It doesn't even attempt to prevent you using the computer for other things (imagine it would or could, windows somehow  making it impossible to install or boot ubuntu!). Depending how you configure it, it can however prevent you from reading certain data, that is where encryption comes in. Use that if you are worried about ppl with physical access to the machine. Anything else, if you think about, you definitely wouldn't want.

---

### Post by Lampi on 2009-09-10
like already mentioned above: encrypt your fs using LUKS, encfs, ecryptfs, truecrypt or whatever you like most. - problem: solved!

---

### Post by zolookas on 2009-09-10
> **Lampi said:**
> like already mentioned above: encrypt your fs using LUKS, encfs, ecryptfs, truecrypt or whatever you like most. - problem: solved!

Exactly

---

### Post by Chronon on 2009-09-10
> **Lampi said:**
> like already mentioned above: encrypt your fs using LUKS, encfs, ecryptfs, truecrypt or whatever you like most. - problem: solved!

You don't specify what problem you're solving.  Someone could still repartition, reformat your drive and install a new system on top of it.

Also, if the information on it is sensitive now and will remain so for the foreseeable future, encryption isn't a guarantee of security.  They could just take the drive, wait for the computational ability of computers to increase exponentially and then have a much better chance to crack it in the future with a much more powerful computer.  Encryption is a temporary security measure because it relies on a task that's hard for the technology of today.  There's no guarantee that this task will remain computationally out of reach (on a reasonable time scale) in the future.

Bottom line: if you are worried about the integrity of your machine/data, then ensure that nobody has access to the machine except you.

---

### Post by joelgsf on 2009-09-10
I have stumbled upon what seems to me a security concern regarding Ubuntu, at leat 9.04 Jaunty Jakalope, which is the current version I am using. I do not want to offend current policy for publishing ways of getting root rights without using sudo, so, I am not expliciting the way here, but there is a way for anyone get to a terminal as root without ever authenticating to the system and not even beeing a registered user. That is a real concern for me.
I would like to discuss this, or hear about a fix in a near udate. If there is another channel where I can post the method I will use it, or, if allowed, I will post it here. But I assure, it is trivial.
Regards,

---

### Post by lovinglinux on 2009-09-10
I guess you are talking about having total access running a terminal from LiveCD, I'm right?

---

### Post by ad_267 on 2009-09-10
Or choosing recovery mode from the grub menu.

But if someone has physical access to your computer then they're always going to be able to get root access. They can open up the box and steal your harddrive if they like, or run a LiveCD/USB and get access to anything they want.

---

### Post by cariboo on 2009-09-10
> **joelgsf said:**
> I have stumbled upon what seems to me a security concern regarding Ubuntu, at leat 9.04 Jaunty Jakalope, which is the current version I am using. I do not want to offend current policy for publishing ways of getting root rights without using sudo, so, I am not expliciting the way here, but there is a way for anyone get to a terminal as root without ever authenticating to the system and not even beeing a registered user. That is a real concern for me.
I would like to discuss this, or hear about a fix in a near udate. If there is another channel where I can post the method I will use it, or, if allowed, I will post it here. But I assure, it is trivial.
Regards,

Go ahead and post it here. I want to see how you do it.

---

### Post by joelgsf on 2009-09-10
Yes, I was astonished of finding that I could do it through the standard Grub menu, choosing recovery mode and after "Drop to root shell prompt".
Of course anyone with physical access to my computer can try to boot from a Live CD, PenDrive, or else, but any of these means I can block in the Bios Setup and allow booting only from the system Drive (which I can even physically lock). Why leave this door ope as default? I can certainly remove this option from "menu.lst", but I think that the opposite should be implemented - the default installation should not show this option, leaving it at the discretion of the user to enable it or not. Isn't this a security concern for you? For me it is.
I supose that one of the main reasonings behind Linux is exactly to be secure by default (isn't this the reasoning behind "sudo"?). If I were to accept leaving this door open because anyone with pysical acces to my machine can steal my HD then why any security at all? IMHO it is because you should close as much doors as you can to make it harder for someone else, not authorized, to get access to you system. Not impossible, but harder.

---

### Post by cariboo on 2009-09-10
I suggest you read this thread from the begining, the way to guard your preciuos data is to encrypt your home directory.

---

### Post by joelgsf on 2009-09-10
I'm sorry, but this you are not going to teach me. I teach it to my students. But I agree with you, encryption is a solution for protecting my data, but security isn't just protecting my data, but protecting my system. If someone can disrupt my system at will in any way, this is a security problem. Even though I may reconstruct it from a security backup.

---

### Post by aysiu on 2009-09-11
> **joelgsf said:**
> If I were to accept leaving this door open because anyone with pysical acces to my machine can steal my HD then why any security at all? Because the greatest threats to your computer's security are online ones. Computers are compromised millions of times more often remotely than locally.

---

### Post by earthpigg on 2009-09-11
i use a BIOS password to protect casual access to my system.

never bothered encrypting /home.

---

### Post by bodhi.zazen on 2009-09-11
> **joelgsf said:**
> Yes, I was astonished of finding that I could do it through the standard Grub menu, choosing recovery mode and after "Drop to root shell prompt".
Of course anyone with physical access to my computer can try to boot from a Live CD, PenDrive, or else, but any of these means I can block in the Bios Setup and allow booting only from the system Drive (which I can even physically lock). Why leave this door ope as default? I can certainly remove this option from "menu.lst", but I think that the opposite should be implemented - the default installation should not show this option, leaving it at the discretion of the user to enable it or not. Isn't this a security concern for you? For me it is.
I supose that one of the main reasonings behind Linux is exactly to be secure by default (isn't this the reasoning behind "sudo"?). If I were to accept leaving this door open because anyone with pysical acces to my machine can steal my HD then why any security at all? IMHO it is because you should close as much doors as you can to make it harder for someone else, not authorized, to get access to you system. Not impossible, but harder.

It is amazing to watch people understand how vulnerable they are to physical access. Why do you think they keep servers in locked rooms ?

> **earthpigg said:**
> i use a BIOS password to protect casual access to my system.

never bothered encrypting /home.

That is fine so long as you do not have sensitive data on your computer you need to protect and you understand the limits of things such as BIOS and Grub passwords. BIOS and grub passwords will deter only the most casual of potential crackers (which may be all you feel you need).

---

### Post by Mornedhel on 2009-09-11
These threads seem to come up every week or so. Really, everything is said with "Physical access is root access".

---

### Post by Dragonbite on 2009-09-11
> **Mornedhel said:**
> These threads seem to come up every week or so. Really, everything is said with "Physical access is root access".

And scary is the physical access opportunities when considering a laptop or netbook. Inside a house is one thing but out in public that can be gone in the blink of an eye.

I have read that Karmic is including disk encryption option during installation?

---

### Post by yabbadabbadont on 2009-09-11
> **Dragonbite said:**
> And scary is the physical access opportunities when considering a laptop or netbook. Inside a house is one thing but out in public that can be gone in the blink of an eye.

I have read that Karmic is including disk encryption option during installation?

Jaunty already provides the option to have an encrypted /home.  At least it does on that alternate installation CD.

---

### Post by Bachstelze on 2009-09-11
> **yabbadabbadont said:**
> Jaunty already provides the option to have an encrypted /home.  At least it does on that alternate installation CD.

... or to use an encrypted LVM for the whole system (except /boot) sice (IIRC) Dapper.

---

### Post by Soul-Sing on 2009-09-11
> Physical access is a low priority compared to say, securing running services that are facing the Internet.

Physical access= access to the system. Only full encryption protects your system/data.

---

### Post by Frak on 2009-09-11
Apple + S on boot
mount -uw /
rm /var/db/.AppleSetupDone
shutdown -h now

You have now tricked a Mac into thinking it has never been set-up before. Of course, the first account's password will be the sudoers password.

Physical Access = Instant Compromise, why do you think they keep servers behind lock and key?

---

### Post by RabbitWho on 2009-09-11
that's why i write sensitive information on little scraps of paper

---

### Post by lisati on 2009-09-11
> **Frak said:**
> 
Physical Access = Instant Compromise, why do you think they keep servers behind lock and key?

At one of the companies I used to work for, due in part to a limitation of the OS, storing stuff on tape was instant compromise, making the data available to anyone within the company who knew which tape the data was on. A couple of simple overrides (which I won't specify here) were sufficient to bypass the usually very stringent security precautions that had been set up. Chances are, however, you wouldn't be able to get away with it for long, due to logging arrangements.

---

### Post by fela on 2009-09-11
Physical access IS root access. You can boot it up with a livecd and pull all of the data off the harddisk as long as it isn't encrypted.

If you're gonna bother with encryption then you're also gonna make damn sure that there's a root password, and you probably won't be using Ubuntu.

---

### Post by Frak on 2009-09-11
> **fela said:**
> Physical access IS root access. You can boot it up with a livecd and pull all of the data off the harddisk as long as it isn't encrypted.

If you're gonna bother with encryption then you're also gonna make damn sure that there's a root password, and you probably won't be using Ubuntu.
Root users can't access encrypted tables.

---

### Post by bodhi.zazen on 2009-09-11
> **fela said:**
> If you're gonna bother with encryption then you're also gonna make damn sure that there's a root password, and you probably won't be using Ubuntu.

Well I too have to disagree with that statement.

"Encryption" is a broad topic and there are many tools one can use. These tools all work on Ubuntu without the need to set a root password.

---

### Post by Bachstelze on 2009-09-11
> **fela said:**
> 
If you're gonna bother with encryption then you're also gonna make damn sure that there's a root password, and you probably won't be using Ubuntu.

Could you please quit it with the "Ubuntu is for dumb people" garbage? I use encrypted LVM *and* I don't have a root password, *and* I'm running Ubuntu.

---

### Post by Mornedhel on 2009-09-11
> **fela said:**
> If you're gonna bother with encryption then you're also gonna make damn sure that there's a root password, and you probably won't be using Ubuntu.

Uh.

A root password is less secure than a sudoer's password : in the case of a root password, you already know 1 out of 2 pieces of information necessary to log in, i.e. the username, 'root'.

This is one of the main reasons enabling a root account is not recommended.

---

### Post by fela on 2009-09-11
> **Bachstelze said:**
> Could you please quit it with the "Ubuntu is for dumb people" garbage? I use encrypted LVM *and* I don't have a root password, *and* I'm running Ubuntu.

Could you please quit it with the obnoxious behaviour?

I never said Ubuntu was for dumb people, I just implied that the fact that Ubuntu doesn't by default give you a root password, if you want a root password you probably won't be using Ubuntu (the UF COC doesn't even allow giving instructions to create a root password on ubuntu).

---

### Post by bodhi.zazen on 2009-09-11
> **fela said:**
> (the UF COC doesn't even allow giving instructions to create a root password on ubuntu).

That also is not true.

We ask you to educate users how to use sudo.

We support setting a root password when necessary.

When you do advise setting a root password please advise users of the risks as well as how to reverse these changes. If you do not know the risks and how to lock the root account agin, perhaps you should learn them.

If you need a root shell please use:

```
sudo -i
```

---

### Post by Chronon on 2009-09-11
> **leoquant said:**
> Physical access= access to the system. Only full encryption protects your system/data.

And even then it's only considered "safe for now" because the odds of finding the right key in a given time frame are very small.  There's no real way to know whether someone will stumble upon an algorithm next week that allows for fast prime number factorization.  At that point, the current set of public key encryption methods becomes instantly insecure.  (Or if somebody builds a functional quantum computer, etc.) 

Encryption provides a practical protection for data, but it should be considered temporary.  Consider that someone can steal the encrypted data and sit on it for a few decades while computers get exponentially faster (presuming that we find ways to stick to Moore's Law).  They can then attempt to crack the cipher with an exponentially faster computer and all of the bits that put the calculation out of practical reach on the technology of today may only take a few years or months on exponentially more powerful computers.  Obviously, this is sufficient protection for any average home user and most businesses and parties with really sensitive data should know all of this already.  I just wanted to counter the idea that encryption represents some kind of absolute security for your data.

---

### Post by heyyy on 2009-09-11
speaking of encryption if i use luks with the alternative cd will it make any difference?

---

### Post by samjh on 2009-09-12
> **joelgsf said:**
> Of course anyone with physical access to my computer can try to boot from a Live CD, PenDrive, or else, but any of these means I can block in the Bios Setup and allow booting only from the system Drive (which I can even physically lock).No, your system still won't be secure when using BIOS settings, because BIOS can be reset by removing the system battery.

> **joelgsf said:**
> Why leave this door ope as default? ...
I supose that one of the main reasonings behind Linux is exactly to be secure by default (isn't this the reasoning behind "sudo"?).No, Linux isn't supposed to be "secure by default".  There is no such "default" intentions as far as security is concerned.  Implementation of security features in Linux is entirely dependent on the goals of the developers of a particular distribution.

The use of "sudo" is also not for making Linux "secure by default".  What sudo does from a security administration point of view is provide a record of which user performed actions on a system using root access, and finer control over which user is able to obtain root access.  It is little more than a tool of convenience.  On Ubuntu, sudo is used to make root access simpler, so that the average user doesn't need to bother with having a separate root account.

> **joelgsf said:**
> If I were to accept leaving this door open because anyone with pysical acces to my machine can steal my HD then why any security at all? IMHO it is because you should close as much doors as you can to make it harder for someone else, not authorized, to get access to you system. Not impossible, but harder.The thing is, a person who has physical access to your system won't find it harder to compromise it merely because there is a password-protected root account.  As mentioned before, a LiveCD can be used, the HDD can be physically taken, etc.  And if an attacker was not interested in the contents of your HDD, but only in making it unusable, they can destroy it physically.

Ubuntu is a distro which aims to be user-friendly.  As you are probably aware, security often comes at the expense of convenience.  The developers obviously thought that the slight decrease in security by having a password-less recovery mode is acceptable in exchange for the added convenience.  Personally, I think this is fine for 99% of home users; for commercial users, the system administration staff should be able to tailor the security access policies appropriately; for security-sensitive environments, one should not use an ordinary Linux distribution.

Obviously, you can change this behaviour by modifying the grub settings, and setting up a root account and password, if you so desire.

---

### Post by fela on 2009-09-12
@bodhizazen

When I gave someone instructions on how to set a root password, a forum admin gave me a warning and said that I shouldn't do that, it's against the UF COC.

---

### Post by bodhi.zazen on 2009-09-13
> **fela said:**
> @bodhizazen

When I gave someone instructions on how to set a root password, a forum admin gave me a warning and said that I shouldn't do that, it's against the UF COC.

I am not trying to give you mixed messages, merely clarifying what my expectations are.

I obviously have not reviewed the incident you are referring to. but my guess is you probably advised setting a root password unnecessarily with out giving proper information / warnings.

---

### Post by adalal on 2009-09-15
> **JT9161 said:**
> Protecting your data is very simple: Juist have a boot password set in BIOS any if someone enters the wrong password your HDD covered in Thermite is ignited, Thieves wont get anything out of it.

But can't you just as easily reset the bios password by reinserting the CMOS battery?

---

### Post by Mornedhel on 2009-09-15
> **JT9161 said:**
> Protecting your data is very simple: Juist have a boot password set in BIOS any if someone enters the wrong password your HDD covered in Thermite is ignited, Thieves wont get anything out of it.

You'd also need a mirror somewhere if you can't afford to lose the data (which is likely, if you're going to such ends to protect it). That mirror needs to be protected. Etc.

Plus it makes it extra easy to destroy your data (and your machine) if the goal is just to harass you.

---

### Post by bodhi.zazen on 2009-09-15
> **adalal said:**
> But can't you just as easily reset the bios password by reinserting the CMOS battery?

You are correct, both BIOS and grub passwords are trivial in terms of protection and will deter only the most casual of crackers.

---

### Post by Dragonbite on 2009-09-15
Alright, so I am trying to set up a "new" laptop (Thinkpad T40 in case you're interested).  What is, after all this back-and-forth, going to be the best option for security since it will be carried out into the "wylde"?

Encrypt the hard disk (thinking of using LVM too) but the /boot partition cannot be encrypted?

---

### Post by bodhi.zazen on 2009-09-15
> **Dragonbite said:**
> Alright, so I am trying to set up a "new" laptop (Thinkpad T40 in case you're interested).  What is, after all this back-and-forth, going to be the best option for security since it will be carried out into the "wylde"?

Encrypt the hard disk (thinking of using LVM too) but the /boot partition cannot be encrypted?

Only you can answer that question. Why do you think /boot needs to be encrypted, do you thing somebody is going to access your laptop , boot some kind of live CD, and install some kind of custom kernel or other malware into /boot ?

As of now /boot can not be encrypted as grub can not decrypt the kernel or initrd.

If this is a problem for you the best you can do is put /boot on a removable flash drive.

You do not need LVM for encryption. Be sure to encrypt /swap and /.

---

### Post by Dragonbite on 2009-09-15
> **bodhi.zazen said:**
> Only you can answer that question. Why do you think /boot needs to be encrypted, do you thing somebody is going to access your laptop , boot some kind of live CD, and install some kind of custom kernel or other malware into /boot ?

As of now /boot can not be encrypted as grub can not decrypt the kernel or initrd.

If this is a problem for you the best you can do is put /boot on a removable flash drive.

You do not need LVM for encryption. Be sure to encrypt /swap and /.

Ah.. the /swap!  Glad to bring that to my attention!

The LVM isn't for encryption purposes, I just like the flexibility.

I'm not going to go crazy with putting the /boot on a USB or anything (though that is a pretty good method), I just want to give it some protection.

Right now my work laptop is whole-disk encrypted and comes up with a pass phrase request before Windows starts to boot up.  

Since /boot cannot, I assume that Grub will show up and then when it is time to boot the system it will ask for a pass phrase to continue?  Therefore, if somebody drops from Grub into a shell they will still need the pass phrase to do anything that will modify the / partition when it is encrypted?

Just verifying my understanding.

---

### Post by bodhi.zazen on 2009-09-15
Well, IMO, neither a BIOS or GRUB password add any substantial security.

If your / and /swap are encrypted that means the can not be accessed by any means without entering a password and decrypting.

If you wish, boot a live CD and try to mount your encrypted partitions.

/boot can not be "protected" in any way , files in boot can be accessed and replaced (your grub password can be changed or deactivated) with a live CD. As of now the only option you have would be to put /boot on a removable device.

---

### Post by Dragonbite on 2009-09-15
> **bodhi.zazen said:**
> If you wish, boot a live CD and try to mount your encrypted partitions.

I had to do that when a laptop installation went sour the morning I was doing a presentation and the hard drive was encrypted.  Took a while to find out how to get the data off of the hard drive (it was Fedora who uses LUKS).

Then I found out accessing an LVM setup was an additional hurdle to jump!

---

### Post by Mornedhel on 2009-09-15
I see many users on the forums who go the encryption route after finding out about that sort of things. Actually, all users I ever heard of that do any kind of encryption on their personal data are people from around here. My frikkin' *crypto teacher* from college (the kind that writes papers on the stuff) does not do full disk encryption.

My honest questions are : a. are you really in the sort of environment where this poses a problem (ie. do you know for sure that people are after your data), and b. is your data really that sensitive ?

Right now I have to assume that half the population of this forum is some kind of diplomat or secret service agent.

If it's just a matter of not getting your system owned, you should mostly be worried about remote exploits and brute forcing passwords. Botnets are not built by some guy wandering around internet cafés and removing random people's CMOS batteries.

---

### Post by Dragonbite on 2009-09-15
> **Mornedhel said:**
> My honest questions are : a. are you really in the sort of environment where this poses a problem (ie. do you know for sure that people are after your data), and b. is your data really that sensitive ?

Right now I have to assume that half the population of this forum is some kind of diplomat or secret service agent.

Naw.. just overly protective of my UbuntuForums account password! :lolflag:

---

### Post by koenn on 2009-09-16
> **Mornedhel said:**
> 
My honest questions are : a. are you really in the sort of environment where this poses a problem (ie. do you know for sure that people are after your data), and b. is your data really that sensitive ?

Right now I have to assume that half the population of this forum is some kind of diplomat or secret service agent.
It's a "magic bullet" kinda thing. People are insecure about security, because they don't know much about it, so they reach for the wonder oil : "encrypt your hard disk and you'll never have to worry about security again". 

That, and a tendency to want "the best" - the fastest PC, the best operating system, the widest monitor, the highest screen resolution, the ultimate security, ... "anti-virus ? firewall ? passwords ? mere toys - I do nothing less than *full disk encryption*"


Outside the geek universe, there's something similar going on with big/fast cars compensating for undersized body parts in the reproductive system. 


Just kidding .... sort of.

---

### Post by Dragonbite on 2009-09-16
> **koenn said:**
> It's a "magic bullet" kinda thing. People are insecure about security, because they don't know much about it, so they reach for the wonder oil : "encrypt your hard disk and you'll never have to worry about security again". 

That, and a tendency to want "the best" - the fastest PC, the best operating system, the widest monitor, the highest screen resolution, the ultimate security, ... "anti-virus ? firewall ? passwords ? mere toys - I do nothing less than *full disk encryption*"


Outside the geek universe, there's something similar going on with big/fast cars compensating for undersized body parts in the reproductive system. 


Just kidding .... sort of.

Hey... my car isn't THAT fast ... *mutter*

---

### Post by koenn on 2009-09-16
> **Dragonbite said:**
> Hey... my car isn't THAT fast ... *mutter*

I bet it's faster than mine

:)

---

### Post by matemargo on 2009-09-16
Why leaving the door open when you can lock it?
Without a default password, anyone can access with root privileges without having a CD, opening your case to remove the BIOS password or any other kind of stuff. It just boot and there is it.

That's just my 2 cents.

---


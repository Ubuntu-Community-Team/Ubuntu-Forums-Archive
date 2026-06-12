---
title: "restore points"
date: 2010-02-17
forum: Recurring Discussions
---

### Post by degarb on 2010-02-17
I am thinking, it might be unwise to do any tweak in Ubutu, of the os or something like a flash tweak, because I don't know how to roll back the system.

Doing anything on the system is risky, things aren't ideal (flash is good ex. ), but have junk is you stay with what one has, or risk making things worse.  This is a risk not present in windows because of the roll back ability.

---

### Post by bruno9779 on 2010-02-17
Roll back ability?? has that ever worked?

I am not too sure what it is that you want to do, but you can quite easily remove any package you install.

When I was on XP I have never managed to restore anything with the infamous app you are quoting

---

### Post by mikewhatever on 2010-02-17
You should only tweak the system if you understand what you are doing, and preferably understand how to undo. It is fairly easy to image the whole system with Clonezilla or Partimage (no ext4), but once again, I wouldn't recommend messing with it, if you don't understand how it works.
The Windows System Restore utility is a neat, but far from bullet proof tool. Often exploited by malware or simply malfunctioning, time and again, it failed to work for me.

---

### Post by degarb on 2010-02-17
> **mikewhatever said:**
> You should only tweak the system if you understand what you are doing, and preferably understand how to undo. It is fairly easy to image the whole system with Clonezilla or Partimage (no ext4), but once again, I wouldn't recommend messing with it, if you don't understand how it works.
The Windows System Restore utility is a neat, but far from bullet proof tool. Often exploited by malware or simply malfunctioning, time and again, it failed to work for me.

It keep track on any ini, reg, and exe changes.  Yes, it works, even to point of removing viruses.   What is not to work?  Besides, whether it works is not the issue; the concept is a very good one.   The concept, that don't tweak unless you know what you are doing is pure crap, oth.  Since, no one really fully knows what they are doing since they didn't write every program on their system. 

Imaging the drive is total bs, since I would need to image every hour to really get any benefit of daily tweaks.  Certainly, not a practical solution for anything other than catastrophic recovery, which sets you back a week, at best.    

Goback was a program that worked before xp sp2, was better done than the windows restore, with easier file retrieval from vault after rollback.   Goback saved my local computer repair days of headaches, and me (especially when I had a bad memory stick (didn't know it) and my xp sp1 was blowing up every 2 month because of bad disk writes. ) So, sure windows restore could be improved upon.

---

### Post by mikewhatever on 2010-02-17
The recurring theme in all of your recent posts is something like "Oh, this and that was so easy in windows and so hard in Ubuntu". I'd like to point out that Ubuntu is not a free version of Windows. If you find it impossible to live without the Windows ways of doing things, perhaps you made a wrong choice with Ubuntu.

---

### Post by tom.swartz07 on 2010-02-17
> **mikewhatever said:**
> The recurring theme in all of your recent posts is something like "Oh, this and that was so easy in windows and so hard in Ubuntu". I'd like to point out that Ubuntu is not a free version of Windows. If you find it impossible to live without the Windows ways of doing things, perhaps you made a wrong choice with Ubuntu.

+1


Although I understand where you are coming from, you need to realize that Ubuntu will not hold your hand. Windows does that, and you could see some of the problems it creates. 

As far as 'fire-proofing' your computer from a major meltdown, you could simply buy an external drive and back up your entire /home folder to it every night or so. Additionally, you could get a list of programs installed from synaptic- just click file>save markings. This should be first on your list before you ever do anything to your system.


The only rock solid advice here is to only do things you fully understand and know how to reverse. sudo apt-get install can be countered with sudo apt-get purge, for example. 
Just take your time, know whats going on and you should be fine.

---

### Post by degarb on 2010-02-17
> **mikewhatever said:**
> The recurring theme in all of your recent posts is something like "Oh, this and that was so easy in windows and so hard in Ubuntu". I'd like to point out that Ubuntu is not a free version of Windows. If you find it impossible to live without the Windows ways of doing things, perhaps you made a wrong choice with Ubuntu.

Yeah, the last post was a request for a one line of code, to include a context menu shortcut that exists--for good reason--in windows.

It is attitude like this that has held Linux down for last two decades.  Screw the average user, we are better and smarter.  It is a miracle any gui is used with attitudes like this.  It is no accident Ubuntu is twice as successful as next linux distro.  They fixed most things, because they have about best core philosphy.  Not totally there yet, but a short list from being there. 

Yes, my tone is fix things!   I philosophically have always wanted Linux to take over windows.   But this will never happed without Ubuntu's core philosophy + increase backward compatibility + shedding rest of 1980's computer engineer's warped mindsets forgetting the goal and the desired outcome.  

The lack of a Roll back is A HUUUUUUGE hole!  Probably, enough to negate any sane consideration for using Ubuntu for any main computer.
 

This is not to say there is no current fix: this may not be needed as a Ubuntu fix.  Take the defunct Goback which was never a MS product, until it was bought and stripped down by them, I believe.

---

### Post by tom.swartz07 on 2010-02-17
> **degarb said:**
> Yeah, the last post was a request for a one line of code, to include a context menu shortcut that exists--for good reason--in windows.

It is attitude like this that has held Linux down for last two decades.  Screw the average user, we are better and smarter.  It is a miracle any gui is used with attitudes like this.  It is no accident Ubuntu is twice as successful as next linux distro.  They fixed most things, because they have about best core philosphy.  Not totally there yet, but a short list from being there. 

Yes, my tone is fix things!   I philosophically have always wanted Linux to take over windows.   But this will never happed without Ubuntu's core philosophy + increase backward compatibility + shedding rest of 1980's computer engineer's warped mindsets forgetting the goal and the desired outcome.  

The lack of a Roll back is A HUUUUUUGE hole!  Probably, enough to negate any sane consideration for using Ubuntu for any main computer.
 

This is not to say there is no current fix: this may not be needed as a Ubuntu fix.  Take the defunct Goback which was never a MS product, until it was bought and stripped down by them, I believe.

The fact of the matter is, most users dont regularly use 'roll back', out of my 10 years experience with Windows users, the better part of 60% didnt even know it existed. Because you are aware of the fact that exists puts you ahead of the crowd. 

Like i mentioned in my previous post, you could essentially replicate the 'rollback' by backing up your /home folder and your installed applications. Should something come up, you just overwrite your /home folder with the backup one and restore the saved program markings.

---

### Post by mcduck on 2010-02-17
Just make proper backips and you don't need to worry about such things.

No automatic backup solution or restore point system can replace actual backups, and as long as you have backups you'd only need restore points to fix system stuff you have broken yourseld, not to save your important files. And the system stuff can always be repaired or reinstalled.. :)

(restore points are not proper backups, as you need to make the backups to some external media that *isn't always connected to your computer*, Any hardware failure on your computer that might destroy the drive that contains your original files can easily break any external drives connected to the machine as well. Not to mention that restore points and such backups actually stored on the *same* hard drive where the original files are will automatically be destroyed should the drive fail.)

---

### Post by tom.swartz07 on 2010-02-17
> **mcduck said:**
> Just make proper backips and you don't need to worry about such things.

No automatic backup solution or restore point system can replace actual backups, and as long as you have backups you'd only need restore points to fix system stuff you have broken yourseld, not to save your important files. And the system stuff can always be repaired or reinstalled.. :)

(restore points are not proper backups, as you need to make the backups to some external media that *isn't always connected to your computer*, Any hardware failure on your computer that might destroy the drive that contains your original files can easily break any external drives connected to the machine as well. Not to mention that restore points and such backups actually stored on the *same* hard drive where the original files are will automatically be destroyed should the drive fail.)

My thoughts exactly.

Windows backup restore points basically did nothing but gobble up space on the drive, as practically all of them were saved. If you do a backup proper, you use the same size, its safe from cataclysmic drive failure, and you could even easily move it to another computer, should the need arise. 

To the OP- the answer to your question is, in short; yes. Its not as point-and-click, so easy a drooling imbecile could do it; but it is much safer. 

I could reference you to SimpleBackup from the software center, and its counterpart SimpleRestore. 

Other than that, you NEED to make a habit of regularly backing up your home folder. Thats all.

---

### Post by bodhi.zazen on 2010-02-17
I am moving this thread to recurring discussions as it appears to by yawvu (Yet Another Windows Vs Ubuntu) thread.

> **degarb said:**
> I am thinking, it might be unwise to do any tweak in Ubutu, of the os or something like a flash tweak, because I don't know how to roll back the system.

Linux is not Windows and we do not "rool back" the system. We restore from back up.

This process is called learning. Almost everything in Ubuntu can be undone. Back up system files before you edit them, when you edit them, make comments, etc, etc.

Install packages with apt-get, remove them with apt-get.

The hardest thing would be if you manually compiled something and the developers did not include a make uninstall ... In that case you would need to manually find and remove the files.

> Doing anything on the system is risky, things aren't ideal (flash is good ex. ),This is true of any OS, there is no more or less risk on Ubuntu then any other OS.

>  but have junk is you stay with what one has, or risk making things worse.  This is a risk not present in windows because of the roll back ability.Well, personally, I found it is not so easy on Windows. The "roll back" feature leaves a lot to be desired. Then there is the registry. If roll back is so easy and reliable, why is it not advised to remove viruses or other malware by using the roll back feature ? I think you will find the roll back feature is neither easy to use or as reliable as you claim.

The other factor is familiarity of the OS. I can fix the vast majority of problems I encounter on Ubuntu / Linux but I am not as familiar with Windows, so I would claim ubuntu is easier to fix then windows.

So, as you can see, your claims are not really much more then an opinion.

Just because you do not know how to back up and restore yous system does not mean it is difficult to do ;)

A simple google search will lead you to many many how-to's and tutorials on the subject.

Just because Windows has  "roll back" or restore point feature does not mean it works, a simple google search will turn up many third party commercial products.

You are entitled to your opinion and if you prefer you are more then welcome to use Windows. You are also welcome to learn Linux, and if you take the time you may find it is indeed easier.

If you want to "play" with you system, Windows or Ubuntu, or any OS really, by far the best thing is to dual boot or use Virtualization (KVM / QEMU / VirtualBox / VMWare). Keep a stable desktop and tweak a test system.

---

### Post by degarb on 2010-02-17
> 
As far as 'fire-proofing' your computer from a major meltdown, you could simply buy an external drive and back up your entire /home folder to it every night or so. Additionally, you could get a list of programs installed from synaptic- just click file>save markings. This should be first on your list before you ever do anything to your system.


The only rock solid advice here is to only do things you fully understand and know how to reverse. sudo apt-get install can be countered with sudo apt-get purge, for example. 
Just take your time, know whats going on and you should be fine.

Thanks, I appreciate the synaptic file>save advice and will try it later, since never have.

I must point out to all you linux gurus that a system isn't just the OS.  The OS is about 1% of a my XP system.  I have about 100 programs I adopted as my own since  the 80s. Take flash that may be used for several tv stations by others, for example, it might run like crap but watchable,  you find a out dated website with a ton of commandline fixes, you run, and now it is working worse.  I could roll back an entire day of work, or the last half hour.  Nothing is more practical than the system restore for allowing safe tweaking.  I never saw the restore/rollbacks as backup; it simply is not the same thing.

---

### Post by HPD2 on 2010-02-17
I agree with what most people say about the windows restore never working. I had issues in windows before and tried to "roll back" only to find that it didn't work and if it did the system wasn't exactly stable after.

Taking a backup of the /home as well as getting a list of installed appliations is one way to go, you could also use remastersys. Useing that program you can make a snapshot live cd of your system. I'm not sure if it saves all your documents and every thing but it is some thing to look into.

---

### Post by bodhi.zazen on 2010-02-17
> **tom.swartz07 said:**
> Other than that, you NEED to make a habit of regularly backing up your [s]home folder[/s] data. Thats all.

I fixed that for you ;)

Personally I use a separate data partition and IMO there are many many (configuration or "dot") files in $HOME that do not require back up.

Anything I consider of any value I keep a copy on my /data partition, and of course back up off the Hard drive.

---

### Post by degarb on 2010-02-17
> >>Well, personally, I found it is not so easy on Windows. The "roll back" feature leaves a lot to be desired. Then there is the registry. If roll back is so easy and reliable, why is it not advised to remove viruses or other malware by using the roll back feature ? I think you will find the roll back feature is neither easy to use or as reliable as you claim.

The other factor is familiarity of the OS. I can fix the vast majority of problems I encounter on Ubuntu / Linux but I am not as familiar with Windows, so I would claim ubuntu is easier to fix then windows.>>.

I totally agree with this.  The roll back isn't first line protection against viruses, nor is it backup.  It is mainly tweak protection. But, how poorly MS does things, because they are rushing deadlines, is not relevant.  

Again, I ask, maybe there is a roll back repository, or some third party program that can be used to do this?



-------------

My meanderings: 

 I hated XP until SP2 came around. There is a lot to loathe about MS: their licensing, aim at getting people to constantly buy new hardware every two years, the past frustrations we had with crashes/registry nightmares/security issues and backdoors made for Uncle Sam.  But, they do test things very well to get a design to cause the least number of support requests--an expense larger than coding costs, I suppose.  This, they do well and should be admired for it.  As a result, they have changed the world (along with others, of course.)

---

### Post by mikewhatever on 2010-02-17
> **degarb said:**
> ................ Take flash that may be used for several tv stations by others, for example, it might run like crap but watchable,  you find a out dated website with a ton of commandline fixes, you run, and now it is working worse.  I could roll back an entire day of work, or the last half hour.  Nothing is more practical than the system restore for allowing safe tweaking.  I never saw the restore/rollbacks as backup; it simply is not the same thing.

It is point blank against common sense to enter commands presented as fixes that you don't understand or have trouble undoing, regardless of whether you have or have not the restore utility. I strongly advise doing anything of the sort, ever.

---

### Post by degarb on 2010-02-17
> **mikewhatever said:**
> It is point blank against common sense to enter commands presented as fixes that you don't understand or have trouble undoing, regardless of whether you have or have not the restore utility. I strongly advise doing anything of the sort, ever.


While your advice is sound, Think about it.   There are a ton of tweak utilities,  some may lack a reversal procedure.  Should we never try to improve our system when using Linux?

---

### Post by MasterNetra on 2010-02-17
> **degarb said:**
> It keep track on any ini, reg, and exe changes.  Yes, it works, even to point of removing viruses.   What is not to work?  Besides, whether it works is not the issue; the concept is a very good one.   The concept, that don't tweak unless you know what you are doing is pure crap, oth.  Since, no one really fully knows what they are doing since they didn't write every program on their system. 

Imaging the drive is total bs, since I would need to image every hour to really get any benefit of daily tweaks.  Certainly, not a practical solution for anything other than catastrophic recovery, which sets you back a week, at best.    

Goback was a program that worked before xp sp2, was better done than the windows restore, with easier file retrieval from vault after rollback.   Goback saved my local computer repair days of headaches, and me (especially when I had a bad memory stick (didn't know it) and my xp sp1 was blowing up every 2 month because of bad disk writes. ) So, sure windows restore could be improved upon.

I've used it a number of times, often had issues still. And note there are viruses that attack and/or hides in system restore and will continue to infect the system even after a roll back. Its not a sure system. In fact all but once I end up having to do a fresh install after rolling back. Needless to say my experiences with it have been less then pleasing.

Edit: And not all virus infected files are .exe's .ini's or reg.

---

### Post by HPD2 on 2010-02-17
No one is saying not to improve, tweak, play, break, fix, ect.. 

hell the first time I installed ubuntu I managed to break it a day later, reinstalled and broke it a few days later, it took me a month or so till I was finaly able to do what I wanted with out worrying that i would break it. Granted that I was also just playing around in the terminal for a while. 

When switching to any operating system, play with it at first read wiki's, manuals, comunity documents, forums, what ever you can to get you self a general knowlage of what to do and what not to do. 

The big thing to rember is what you do you can undo if you understand what it is you are doing in the first place. Although a reinstall is some times easer than hunting down every little thing you did if you cant rember.

In all honesty Ubuntu doesnt need a whole lot of tweaking, a little here a little there, I my self mostly tweak the boot up processes and the themes.

---

### Post by degarb on 2010-02-17
> **HPD2 said:**
> 
In all honesty Ubuntu doesnt need a whole lot of tweaking, a little here a little there, I my self mostly tweak the boot up processes and the themes.

You had to say it!  There is a way to cut bootup time with a tweak?!?!   How do I do this?

---

### Post by mikewhatever on 2010-02-17
> **degarb said:**
> While your advice is sound, Think about it.   There are a ton of tweak utilities,  some may lack a reversal procedure.  Should we never try to improve our system when using Linux?

I am not telling you what to do or not to do, just expressing my personal opinion. Having tried some of the tweak programs (not sure what you are referring to exactly), I don't think they are necessary at all, yet, if you think you can improve your system without knowing what happens, well, good luck to that.

---

### Post by mcduck on 2010-02-17
> **HPD2 said:**
> The big thing to rember is what you do you can undo if you understand what it is you are doing in the first place.
Well said. :)

I might add that if you *don't* understand what you are doing you probably shouldn't be doing it. At least not on a system you are using for anyhting else than testing.

---

### Post by HPD2 on 2010-02-17
> **degarb said:**
> You had to say it!  There is a way to cut bootup time with a tweak?!?!   How do I do this?

Well I stop programs from starting up at boot, like "Find New Hardware Drivers," "Visual Assistance." Stopping those likely doesn't do much but I don't need them so why have them start up at boot?

There is also a program called "bum" I would suggest caution though you can break you system using that, or so I have heard.

---

### Post by degarb on 2010-02-17
> **HPD2 said:**
> Well I stop programs from starting up at boot, like "Find New Hardware Drivers," "Visual Assistance." Stopping those likely doesn't do much but I don't need them so why have them start up at boot?

Now, need to lookup what a visual assistant is.  

I read that next ubu will load faster because of hal not being included.   I need to look that one up too.

Remember, this started as a know nothing new user group.  I will count myself, though I have read 125 pages of the HB, mastered far less.  The read hat manual of 2000 was 1100 pages, I recall, and my dos 1.0 manual 6000 pages.    So, I will need to revist which folders other than home to backup.   I assume I would not backup program files or the OS, since too many dependencies I don't understand.  Also backup would be over network to external large drive.  So, I need a repository for a backup, or scheduler + script (which may or may not be above my user level to compose that script} .   Any suggestions appreciated.

---

### Post by HPD2 on 2010-02-17
System > Preferences > Startup Applications

---

### Post by Gallahhad on 2010-02-17
> **degarb said:**
> I am thinking, it might be unwise to do any tweak in Ubutu, of the os or something like a flash tweak, because I don't know how to roll back the system.

Doing anything on the system is risky, things aren't ideal (flash is good ex. ), but have junk is you stay with what one has, or risk making things worse.  This is a risk not present in windows because of the roll back ability.

It appears that someone or some group of individuals have been busy working on just this sort of thing for Ubuntu:
[https://wiki.ubuntu.com/SystemRestore](https://wiki.ubuntu.com/SystemRestore)

The project appears to still have active involvement at least it appears so from the dates at the sourceforge page.

That's the good news.

The bad news is, it is not done yet; so if you want it right now, clonezilla or something like that would probably be something to consider.

---

### Post by degarb on 2010-02-17
Thanks!

---

### Post by degarb on 2010-02-17
i wonder if they track config changes in programs too.


They are looking for a better name. I am thinking:

michief recovery
the Jump Back Jack utility
UbiBack / Rebuntu tool
the "morning after" tool    or just ub586
the Noregrets tool
the Untweak tool

short back machine (the not so way back machine)
Restore configs.  
last prefs
preference recovery

---

### Post by degarb on 2010-02-17
How about:  system rewind
           or time rewinder

---

### Post by dartdog on 2010-04-20
well FWIW I am looking for similar solutions.. I am new and am repruposing an older laptop and using 10.04 beta 2 and before you tell me to go back to stable 9.1 I already did and due to my config it is a non starter.. has to do with bios and grub I gather which is handled quite differently in 10.04 so I finally get it going.. then the massive set of updates come down and brick the machine.. after about 10-15 reformats and reinstalls followed by selective updates I'm down to 22 open gl suspect packages,, I need a good system restore so I'm not spending Hrs each time.. the bad pckg prevents rebooting in any form and the disk must be reformatted completely,, the "normal install" does not fix the mbr/grub.... so I'm investigating clonzilla and remastersys both look promising partimage would have been great but no ext 4 support.. and I have a ntfs external drive that would be handy once I get a handle on just how all these startup files and directory structures work and can be backed up and restored.. And.. I sort of know how to approach the problem.. a real newbie would have given up days ago... Not bitching just chiming in!

---


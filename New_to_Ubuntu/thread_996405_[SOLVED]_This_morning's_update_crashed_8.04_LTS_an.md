---
title: "[SOLVED] This morning's update crashed 8.04 LTS and I could not reinstall it"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by socref on 2008-11-28
Good evening everyone. I had the strangest thing happen when I tried to update 8.04 LTS using Update Manager. I have no idea what happened, but I've spent the entire day restoring my pooter as a result. Sorry for the length of this post, but I want to include all the details.

I upgraded from 7.10 to 8.04 LTS on my desktop two days ago using the Update Manager. All seemed well until about 9 a.m. eastern time today (November 28) when I logged on and noticed that Update Manager showed 9 recommended items to download. So I clicked "OK" and let it run.

At the end a message popped up saying I needed to restart the pooter for the changes to take effect, so I clicked "restart."

The pooter restarted and after a bit the Dell splashscreen came up, remained on screen for a few seconds, and then as expected the Ubuntu splashscreen appeared (the black screen with the orange progress bar that goes back and forth). After awhile more the computer went back to the Dell splashscreen rather than completing the boot-up process and giving me a desktop. And then the Ubuntu splashscreen came up again.

This went on -- back and forth between the two splashscreens maybe five or six cycles. I was not getting error messages -- rather the pooter just kept cycling between the two splashscreens.

Well this was crazy, so I powered down the pooter and then powered back up. The same thing happened -- back and forth endlessly between the two splashscreens. So I decided that something must have been amiss in the update (maybe the kernel got screwed up??) and I decided to reinstall the O/S. I hate doing that but I was at a loss. Fortunately I had backed up all my files two days ago in preparation for the upgrade to 8.04 LTS.

I do not have an original 8.04 disk -- only one for 7.10. But I do have an 8.04 disk that came from Linux magazine, so I put that in the drive and restarted the computer since it is supposed to allow installs. But the pooter refused to recognize the disk. No matter what I did I could not boot to the "live" version (to "sample" Ubuntu) or install to the hard drive.

So I took out that disk and inserted my original 7.10 disk. That one was recognized, and it installed no problem. So once 7.10 was installed (without getting any updates via the Update Manager) I then went to the Update Manager and tried to upgrade again to 8.04 LTS (following the same procedure which had resulted in a successful upgrade two days ago).

Unfortunately this time the upgrade to 8.04 LTS must have included those 9 items that screwed me this morning, for the same thing happened! Back and forth between the two splashscreens, no error messages, and no way that I knew to halt the loop. As you can imagine, I was really upset (to put it mildly). A couple of hours wasted at this point.

So I gave up on upgrading to 8.04 LTS and reinstalled 7.10. I spent the entire afternoon and early evening restoring all of my files and getting the system reconfigured as I wanted it. And the pooter is running great on 7.10.

So....  Does anyone know if this morning's updates for 8.04 LTS included something that "borked" the kernel or otherwise has screwed up others? Or am I the only one who's been so affected? I did a brief search in these forums but did not see anything similar.

Frankly I don't see that I erred during the update early this morning given that all I did was accept the recommendation of Update Manager and click "restart" when the download was completed. After that it was gremlins!!

Any ideas how I can get back to 8.04 without going through this splashscreen hell again?

Thx
socref

---

### Post by psycosmyth on 2008-11-28
Here are the stupid questions, sorry.
What pooter you got?
are you dual-booting?
have other partitions?
should I hold off on that kernel update?
Hang on. This will be fixed ok?

---

### Post by louieb on 2008-11-28
Sounds like you did most things right. The only thing that I saw is after you installed 7.10 you did not bring it up to date before upgrading to 8.04. Try applying all the 7.10 updates before upgrading to 8.04.

Kind of sounds like the 8.04 disk is defective. Guess you have to get another disk if you want to go that route. 

Haven't had any trouble with updates. I have 2 PCs running 8.04 and 1 PC running 8.10.

---

### Post by socref on 2008-11-29
> **psycosmyth said:**
> Here are the stupid questions, sorry.
What pooter you got?
are you dual-booting?
have other partitions?
should I hold off on that kernel update?
Hang on. This will be fixed ok?

Dell desktop. Do you need specifics as to processor, memory, etc?

No, only Ubuntu on this pooter

Three partitions: /, /home, and swap

Thx
socref

---

### Post by socref on 2008-11-29
> **louieb said:**
> Sounds like you did most things right. The only thing that I saw is after you installed 7.10 you did not bring it up to date before upgrading to 8.04. Try applying all the 7.10 updates before upgrading to 8.04.

Kind of sounds like the 8.04 disk is defective. Guess you have to get another disk if you want to go that route. 

Haven't had any trouble with updates. I have 2 PCs running 8.04 and 1 PC running 8.10.

When I did the original upgrade to 8.04 my 7.10 install was current with all updates. When I did the update yesterday of 8.04 it was current except for the 9 suggested "fixes" offered by the updater.

Are you suggesting now that 7.10 is updated once again I try to get 8.04 once more and hope that this time it doesn't get "borked?"

socref

---

### Post by ugm6hr on 2008-11-29
> **socref said:**
> Are you suggesting now that 7.10 is updated once again I try to get 8.04 once more and hope that this time it doesn't get "borked?"

I would always go with a fresh install.

Try downloading a fresh 8.04 CD (or use a USB stick with unetbootin to save on CD-Rs) and try again.

I don't think there was a problem with the kernel update yesterday, but then bugs can be hardware specific.

Remember, if it was a kernel issue, you can go into the GRUB menu and pick an old version (obviously it's too late now that you;ve reinstalled).

---

### Post by clhsharky on 2008-11-29
I don't want to steal your thread, but your not alone. That update through a scare at me. But not as bad as yours. I've never had a problem with 8.04 LTS before.

---

### Post by socref on 2008-11-29
Arrrgh!!  This is really p*ssing me off.

I tried again to upgrade to 8.04 LTS using Update Manager and based on a clean install of 7.10 (remember, I don't have an 8.04 original disk so I have to do this through Update Manager). Same thing happened as described in yesterday's long e-mail. Once again I am back to that endless loop of Dell and Ubuntu splashscreens.  :confused:

This is more than I can deal with and I will have to stay with 7.10 much as I would like to upgrade. But I'm not going to deal with this insanity for a third time.

Guess I'll have to find an original 8.04 disk and try that.

Sheesh. :mad::(

---

### Post by ugm6hr on 2008-11-29
On reboot, go into the GRUB menu.

Do you have any other options?  I presume not, since the update probably only pulls the latest.  But it's worth looking.

A fresh install is sensible.  If you don't want to burn another CD, use a 1GB USB stick.

---

### Post by Scarlath on 2008-11-29
Are you applying all updates before upgrading...?

Fresh install seems like it'd be the most easy now though.

---

### Post by socref on 2008-11-29
> **Scarlath said:**
> Are you applying all updates before upgrading...?

Fresh install seems like it'd be the most easy now though.

Yes, all updates for 7.10 were applied before upgrading the first time to 8.04 LTS. That update was successful (a few days ago). Then yesterday morning the problem started when I allowed Update Manager to install the 9 items it recommended for 8.04. After the endless looping would not stop I reinstalled 7.10 but did not update it before trying to upgrade again to 8.04. That then also failed with the same endless looping. And then I tried a third time after reinstalling 7.10 with all updates before trying to upgrade to 8.04.

I'm reinstalling 7.10 yet again as I type this on my SuSE laptop.

socref

---

### Post by ugm6hr on 2008-11-29
> **socref said:**
> I'm reinstalling 7.10 yet again as I type this on my SuSE laptop.

You obviously have a large download limit, if you've upgraded twice already.

Why not just download a new 8.04.1 CD (on your Suse laptop, or using the 7.10 LiveCD), and then install that?

---

### Post by socref on 2008-11-29
> **ugm6hr said:**
> You obviously have a large download limit, if you've upgraded twice already.

Why not just download a new 8.04.1 CD (on your Suse laptop, or using the 7.10 LiveCD), and then install that?





As soon as this reinstall is done I'll download an 8.10 disk (faster on desktop DSL than on wireless lappy). I have also requested an original disk from Ubuntu just in case. I'll post an update to the list in a few weeks when I get up the courage to try again to upgrade from 7.10.  :lolflag:

socref

---

### Post by ugm6hr on 2008-11-29
> **socref said:**
> I'll post an update to the list in a few weeks when I get up the courage to try again to upgrade from 7.10.  :lolflag:

Another upgrade?  I'd just wait for the 8.10 CD now (if that's what you want to upgrade to).

---

### Post by socref on 2008-11-29
[QUOTE=ugm6hr;6276611 Another upgrade?  I'd just wait for the 8.10 CD now (if that's what you want to upgrade to).[/QUOTE]



Questions:

1) I'm running 7.10. If I get an original disk of 8.10 and also download a copy of 8.04 should I go directly to 8.10 and bypass 8.04, or should I first install a clean version of 8.04 and wait for awhile to see if there are problems with 8.10? At the moment I am rather gun shy about yet another go-round with 8.04 but also wonder about the wisdom of jumping a version.  :confused:

2) My drive is partitioned into /, /home, and swap. If I decide to upgrade to either 8.04 or 8.10 can I successfully upgrade just the O/S without affecting my files in /home? Or is it best to backup all my files, do a clean install of 8.04 or 8.10, and then restore my /home? I know the standard answer is that a clean install is always best, but I'm hoping that others might have had success without a full blown reinstall of everything on the hard drive.  

Thx!
socref

---

### Post by jorj82 on 2008-11-29
If the problem keeps happening after upgrading, your best bet would be to just do a clean install.  Back up your important files though!

---

### Post by sdowney717 on 2008-11-29
I would just backup /home
install Ibex 8.10
restore /home/username

You will restore menu items and all will be well. 
[http://ubuntuforums.org/showthread.php?t=964988](http://ubuntuforums.org/showthread.php?t=964988)
for example, 'test' as user name. This worked for me.

Login as another user to make sure my home files are not in use for copying
run gksudo Nautilus
select the home folder to backup
select hidden files options
copy the files and folders somewhere

To restore

create a login user 'test'
copy the backed up home files and folders into /home/test
run the command
sudo chown -R test:test /home/test

and everything is back like it was. (test is just a test name)

---

### Post by ugm6hr on 2008-11-30
> **sdowney717 said:**
> I would just backup /home
install Ibex 8.10
restore /home/username
...

I believe socref has a separate /home partition.

Hence a backup is just good common sense, but the rest is unnecessary.  You can just install whatever Ubuntu version you want using Manual install, select the appropriate partitions as mount points and **make sure /home partition is NOT marked to format**.  All /home files will be preserved, and permissions etc as they should be (inc all users desktop prefs etc).

As for the 8.04.1 vs 8.10 debate - have a look around here.  There is no right answer.  I'm still on 8.04.1 for now because I'm happy with it, and I have not had a single problem (unlike you).

If the latest kernel update is the problem, a fresh install will not cause problems.  Each kernel update leaves an old kernel in Grub for use.  Hence, you should be able to install 2.6.24-21 after a fresh install, and then lock that kernel version before updating.  If that leaves your system functional, you could try unlocking the kernel and trying -22 again.  You should then be able to get back to -21 from Grub if it borks again.

---

### Post by gabba on 2008-11-30
**Socref**:
- First, I doubt your 8.04 cd is bad. This version of Ubuntu probably introduced an incompatibility with your hardware. Hopefully it is fixed in 8.10.

- Still, you should check your iso file after download. If you know how to download torrents the best is to download from the official Ubuntu torrent at [http://www.ubuntu.com/getubuntu/downloadmirrors#bt](http://www.ubuntu.com/getubuntu/downloadmirrors#bt)
A torrent download is automatically checked for integrity, so you're 100% sure its not corrupted.
Otherwise get some info on the Ubuntu wiki on how to compute an md5sum of your iso and compare it with the official one.
(To compute it under Windows: just install [HashTab]("http://beeblebrox.org/hashtab/").)

Also, when you burn the iso and your cd burning software has a "Verify Data" checkbox, enable it. It will verify your CD burned ok and therefore contains the same thing as the iso.

- You can't upgrade directly from 7.10 to 8.10, you have to get a working 8.04 installation first. Which seems impossible in your case without a lot of hassle. So **backup your documents and do a fresh install of 8.10**. I personally advise you to **format your home partition** (unlike what ugm6hr is telling you above) once you're sure that all your important data is safe: reusing the configurations contained in the dot-files of an old version can mess up new applications, in my experience. Nothing guarantees you that config files don't change format between application versions, and that apps properly convert those to the new version 100% of the time.

- If you still have problems with 8.10 and you verified your CD using the steps above, better file a bug report on launchpad than try the same install 3 times in a row: your time will be better spent.
To file a bug, you need:
- Lots of patience, nerves and free time
- To read up a bit on what info you need to provide when filing a Ubuntu bug (look on the ubuntu website and wiki, including the following page: [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs))
- To search existing bugs before filing a new one. Who knows, maybe your bug is being fixed as we speak, or someone posted a workaround in the bug discussion that you can use as a temporary fix.
- To ignore idiots who might tell you to learn programming and fix the problem yourself: it might take a long time, but eventually someone more intelligent like an ubuntu developer will take a look at your bug. If you provided the right info.

---

### Post by socref on 2008-11-30
> **gabba said:**
> **Socref**:
- First, I doubt your 8.04 cd is bad. This version of Ubuntu probably introduced an incompatibility with your hardware. Hopefully it is fixed in 8.10.

- Still, you should check your iso file after download. If you know how to download torrents the best is to download from the official Ubuntu torrent at [http://www.ubuntu.com/getubuntu/downloadmirrors#bt](http://www.ubuntu.com/getubuntu/downloadmirrors#bt)
A torrent download is automatically checked for integrity, so you're 100% sure its not corrupted.
Otherwise get some info on the Ubuntu wiki on how to compute an md5sum of your iso and compare it with the official one.
(To compute it under Windows: just install [HashTab]("http://beeblebrox.org/hashtab/").)

Also, when you burn the iso and your cd burning software has a "Verify Data" checkbox, enable it. It will verify your CD burned ok and therefore contains the same thing as the iso.

- You can't upgrade directly from 7.10 to 8.10, you have to get a working 8.04 installation first. Which seems impossible in your case without a lot of hassle. So **backup your documents and do a fresh install of 8.10**. I personally advise you to **format your home partition** (unlike what ugm6hr is telling you above) once you're sure that all your important data is safe: reusing the configurations contained in the dot-files of an old version can mess up new applications, in my experience. Nothing guarantees you that config files don't change format between application versions, and that apps properly convert those to the new version 100% of the time.

- If you still have problems with 8.10 and you verified your CD using the steps above, better file a bug report on launchpad than try the same install 3 times in a row: your time will be better spent.
To file a bug, you need:
- Lots of patience, nerves and free time
- To read up a bit on what info you need to provide when filing a Ubuntu bug (look on the ubuntu website and wiki, including the following page: [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs))
- To search existing bugs before filing a new one. Who knows, maybe your bug is being fixed as we speak, or someone posted a workaround in the bug discussion that you can use as a temporary fix.
- To ignore idiots who might tell you to learn programming and fix the problem yourself: it might take a long time, but eventually someone more intelligent like an ubuntu developer will take a look at your bug. If you provided the right info.


First off let me thank all who have replied on my strange circumstance. I really appreciate your help.

That said, I've discovered some things this morning that make the situation even more bizarre. Here's the latest. (I have completely restored the 7.10 installation.)

1) I followed instructions and burned an 8.04.1 iso. I verified its integrity with the md5sum number on the iso and on the Ubuntu Hashes page.

2) I then put the iso into my drive and rebooted the machine, but my pooter would NOT recognize the iso! Just as yesterday with the 8.04 disk I got from Linux Magazine, when I clicked on "Try Ubuntu without installing" I got a series of error messages as follows (copied as best I could during multiple reboots):

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash) 
Enter 'help' for a list of built-in commands.
(initramfs) [    95.397298] ata1.00: revalidation failed (errorno=-5)

[    another number appeared here] ata2.00: Emask 0x0 exception Sact 0x0 Serr 0x0 Action 0x2 frozen 

and then some more numbers in and out of brackets. (By this time I had watched at least 20 reboots trying to capture the info above and was worn out!)


Then the pooter self-rebooted and returned to the Dell splashscreen, and the process started all over again. When I clicked "Try ubuntu without installing" I got another series of messages as above, each time with the numbers in [brackets] changing.

3) So I took the iso and put it in my wife's pooter (a custom build running SuSE 11.0) and it was recognized perfectly, and I could test Ubuntu 8.04 on her pooter.

4) I then took the iso and the Linux Magazine 8.04 disks that failed in my desktop and put them into my lappy (running SuSE 10.0) and both were recognized and both worked perfectly.

So....

Nothing works on my pooter other than an original Ubuntu 7.10 disk. I do not have an original 8.04 or 8.10 disk to check. But it's clear that my desktop does not like non-Ubuntu originals (or even a confirmed iso).

If the non-Ubuntu original disks work perfectly on two other pooters but not on mine does that indicate that the problem is more likely hardware-related than software-related? Can we discount the fact that both of those other pooters were running SuSE rather than Ubuntu?

Is this a bug that needs to be filed with Ubuntu or is it more likely a problem I need to take up with Dell? Note that the pooter came with Ubuntu 7.10 loaded (NO Windows), so you'd think Dell would have pre-determined that the hardware they used was Ubuntu/Linux compatible.

Until I have an original 8.04 or 8.10 disk to check I won't know the full story, but it just makes no sense to me that ONLY an original disk seems to be recognized by this pooter, and it rejects anything else, even a verified iso.

Sheesh.  :confused:

socref

---

### Post by gabba on 2008-11-30
The CD you download, if it passed the md5 check, is *exactly* the same as the "official" one you get in the mail. Except for the pretty picture printed on the latter. It definitely sounds like an incompatibility with your hardware introduced by 8.04 Hardy (and not fixed in 8.04.1, either). The easiest thing for you would probably to try installing 8.10 Intrepid, in the hope they fixed the problem. (Do you have any reason to stick to Hardy?)

If that fails you have quite a few options:

- Take it up with Dell: why not, if they support the computer under Ubuntu. I don't know if they support upgrades to newer versions. Please note that while Dell might know the solution, its clearly Ubuntu which is behaving badly.

- Try installing with the 8.10 Alternate CD : it's possible that somehow the liveCD has the wrong configuration for your computer, but that the alternate installer will set it up correctly.

- Search google, the ubuntu bugs and this forum for problems between 8.10 Intrepid and your specific computer model ("Dell XXYZ"). As I said, someone will have come up with a workaround. Please also post here your exact "Dell XXYZ" computer model, so I can help you search if I have some free time.

- File a bug.

---

### Post by socref on 2008-11-30
> **gabba said:**
> The CD you download, if it passed the md5 check, is *exactly* the same as the "official" one you get in the mail. Except for the pretty picture printed on the latter. It definitely sounds like an incompatibility with your hardware introduced by 8.04 Hardy (and not fixed in 8.04.1, either). The easiest thing for you would probably to try installing 8.10 Intrepid, in the hope they fixed the problem. (Do you have any reason to stick to Hardy?)

If that fails you have quite a few options:

- Take it up with Dell: why not, if they support the computer under Ubuntu. I don't know if they support upgrades to newer versions. Please note that while Dell might know the solution, its clearly Ubuntu which is behaving badly.

- Try installing with the 8.10 Alternate CD : it's possible that somehow the liveCD has the wrong configuration for your computer, but that the alternate installer will set it up correctly.

- Search google, the ubuntu bugs and this forum for problems between 8.10 Intrepid and your specific computer model ("Dell XXYZ"). As I said, someone will have come up with a workaround. Please also post here your exact "Dell XXYZ" computer model, so I can help you search if I have some free time.

- File a bug.

1) I have no reason to stick with Hardy. In fact I had it installed and working for only one day -- until the infamous download of 9 "fixes" that caused this whole mess.

2) I will take it up with Dell this week and let you know what they say.

3) What is the 8.10 "alternate" CD? I see a link for it as a torrent, but I do not know how to download a torrent. I have "Bit Torrent" on my computer, but when I click on that all I get is the list of files in my home directory. Not much help, and it's definitely not what I expected (I thought I'd get some sort of GUI program that would download as a torrent.)

4) I am confused as to why you suggest I search for problems between 8.10 and my computer. I have not yet gotten to 8.10 -- I'm still trying to get 8.04 to work. Did you mean 8.04?

5) Would greatly appreciate anything you can find re: my Dell. :)
Here is the basic info on my pooter. Please let me know if you need more.

Dell Inspiron 530, Intel Pentium Dual Core processor E2160 (1.80 Ghz, 800FSB),

2 Gb DDR2 RAM @ 667 MHz

socref

---

### Post by gabba on 2008-11-30
> **socref said:**
> 

3) What is the 8.10 "alternate" CD? I see a link for it as a torrent, but I do not know how to download a torrent. I have "Bit Torrent" on my computer, but when I click on that all I get is the list of files in my home directory. Not much help, and it's definitely not what I expected (I thought I'd get some sort of GUI program that would download as a torrent.)


The alternate CD has a text-based installation "for experts". Well, it's not that hard, and you can find many guides on the 'net. If you never downloaded torrents I'd avoid it, you have to configure your router and other stuff. You can find a regular .iso download of the alternate CD on the Ubuntu download page.

> **socref said:**
> 
4) I am confused as to why you suggest I search for problems between 8.10 and my computer. I have not yet gotten to 8.10 -- I'm still trying to get 8.04 to work. Did you mean 8.04?


No. If you try 8.10 and it fails as well, then search for incompatibilities between 8.10 and your computer.

> **socref said:**
> 
5) Would greatly appreciate anything you can find re: my Dell. :)
Here is the basic info on my pooter. Please let me know if you need more.

Dell Inspiron 530, Intel Pentium Dual Core processor E2160 (1.80 Ghz, 800FSB),

2 Gb DDR2 RAM @ 667 MHz

socref

Well, [googling this]("http://www.google.com/search?ie=UTF-8&oe=UTF-8&sourceid=navclient&gfns=1&q=Dell+Inspiron+530+hardy+boot+problem") already gives interesting results.
Dell has some interesting info:
[http://linux.dell.com/wiki/index.php/Ubuntu_8.04](http://linux.dell.com/wiki/index.php/Ubuntu_8.04)
Apparently Dell has a custom cd image you can use to wipe the hard drive and get their customized 8.04.1. (Warning: it will destroy all your data and partitions on that hard drive)

And I think this might be your bug, they have two workarounds:
[http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/Desktop_Wont_Boot](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/Desktop_Wont_Boot)
The workarounds will probably also work with 8.10 if you decide to install that and the problem persists.

---

### Post by socref on 2008-12-02
> **gabba said:**
> 

(snip)

Well, [googling this]("http://www.google.com/search?ie=UTF-8&oe=UTF-8&sourceid=navclient&gfns=1&q=Dell+Inspiron+530+hardy+boot+problem") already gives interesting results.

(snip)

And I think this might be your bug, they have two workarounds:
[http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/Desktop_Wont_Boot](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/Desktop_Wont_Boot)
The workarounds will probably also work with 8.10 if you decide to install that and the problem persists.

Gabba and all others... SOLVED!!  :p  Thank you! 

The links Gabba provided were amazing and led me to literally dozens and dozens of other folks on multiple websites who had the same problem and were similarly frustrated by the illogic of the entire situation. I found several suggestions -- some simple and some involving command line wizardry.

The fix I tried was amazingly simple, if bizarre: Go into the BIOS > Integrated Peripherals > Sata Mode, and then change Sata Mode from IDE to RAID.

Now, what seems illogical and yet it works is that I only have one drive. I don't have a RAID setup, yet with the Sata Mode on the default setting (IDE) Ubuntu 8.04 won't boot, the pooter goes into an endless loop between the Dell and Ubuntu splashscreens, and it displays error messages as I described previously. But when the Sata mode is changed to RAID, 8.04 installs without any problem and then boots and reboots without any problem. 

Fortunately I only have Ubuntu on this Dell, for the discussions I followed in getting to this solution said that it won't work if you have a dual-boot (Linux/Windoze) hard drive. (I don't understand why -- it's well beyond my understanding of pooters.)

By the way, Ubuntu tech support at Dell insisted that this fix could not possibly work without a true RAID set-up of multiple hard drives. One tech support person even told me that I should stick with 7.10 and forget about upgrading the O/S. When I told him that was absurd he said there was nothing they could do for me. After many, many more calls I finally got to a supervisor who was willing to walk me through the process just in case the system did crash and I needed to be "rescued." When the Sata settings switch did not immediately crash the pooter on reboot I installed 8.04.01, rebooted at the end of the install, and verified that the pooter was working properly. What a relief. :lolflag: 

So I hope that this saga is finally over. It will be interesting to see what happens when I upgrade to 8.10. Will I have to change the Sata setting back to IDE, or will 8.10 install only in RAID mode? I'll let you folks know when I make the move.

Thanks again for hanging in with me through many long messages. ):P
socref

---

### Post by gabba on 2008-12-02
Hey, glad I could help! ;)

---


---
title: "Ubuntu makes me cry, should I give up on Linux?"
date: 2007-10-15
forum: Recurring Discussions
---

### Post by killertofu on 2007-10-15
Mistake No. 1:  I decided to install Gutsy Gibbon, even though it's not complete.

Mistake No. 2: I didn't give Windows very much space, because I assumed I'd be able to magically share space between Ubuntu's /home partition and Windows itself.

Now, I am up a damn creek! I can't even browse the web in Gutsy, it gives me the white frozen screen of doom. (Everytime I have to unplug my computer to reboot, I die a little inside.) 

Should I install another distro? (Please don't be offended by my suggesting this, boys and girls...I love Ubuntu's community), or should I install Feisty?

If not either of the above, how on earth can I get my computer back into a somewhat usable configuration for windows again?

My HDD had some serious nip and tuck, here's the juicy details:

Windows XP NTSF Partition, only 15GB (Was supposed to be 20, but I made a mistake due to lack of sleep)
/root EXT3 15GB
swap 2GB
a whopping 147GB /home  EXT3 partition.

If I decide to go with another distro, will I need to delete the Ubuntu partitions? It's all Linux, but damn! I'm confused!

Any help will be appreciated, a lot!

---

### Post by kamitsukai on 2007-10-15
well i can offer moral surpport (if thats any help) ive given up on linux many times but! i have always had the curiosity to come back...

---

### Post by dakuran on 2007-10-15
w0w you've been through a lot buddy, well seeing as Gutsy's big debut is only in a few days, you can either wait and just repartition everything and install Gutsy, or (if ur like me and can't wait) I'd say Download Feisty, just make sure you repartition everything and Start Fresh~!, take ur time and don't give up, believe me I've wrecked my box PLENTY of times, but I'm still here =] and that much smarter XD

GoodLuck!!

---

### Post by angryfirelord on 2007-10-15
> Mistake No. 1: I decided to install Gutsy Gibbon, even though it's not complete.
Release date is on Oct. 18, so try downloading it again when it comes out.

However, try again with this partitioning scheme:

-Windows NTFS (don't change that anymore)
- swap 512MB
- / takes remaining space

Note that it's / & not /root. If you do it as above, you should be able to boot into your system.

---

### Post by wpshooter on 2007-10-15
I would get rid of everything and then if you need "Windows", install that and then install Feisty and let Gutsy age a while before you attempt that again.

---

### Post by killertofu on 2007-10-15
> **kamitsukai said:**
> well i can offer moral surpport (if thats any help)

Thanks, it's a big help. :)

> **dakuran said:**
> w0w you've been through a lot buddy, well seeing as Gutsy's big debut is only in a few days, you can either wait and just repartition everything and install Gutsy, or (if ur like me and can't wait) I'd say Download Feisty, just make sure you repartition everything and Start Fresh~!, take ur time and don't give up, believe me I've wrecked my box PLENTY of times, but I'm still here =] and that much smarter XD

GoodLuck!!

How should I go about installing Feisty? Can I just use the LiveCD and mess around with the partitions there?
If I were to try a distro like Mandriva, would I need to repartition everything first? :confused:

---

### Post by dwhitney67 on 2007-10-15
I would install Ubuntu over windows.  You don't need windows.  You weren't born with it, and you can surely live and die someday without it too.

I just did a reinstall of Fedora 7 yesterday evening.  What a breeze!  I can't imagine Ubuntu requiring a degree in rocket science to install either.  Never use a beta release (e.g. Gutzy) unless you want to be a tester.  Even on the official release date I wouldn't touch it with a 10-foot pole.

---

### Post by jpyanowski on 2007-10-15
OK, let me try. I've reinstalled Ubuntu on my box many times over the past two years (has it been that long??? 8-[ You can use the live CD and delete the ubuntu partition as part of the installation. Use the example given and also think about a /home partition. That way your stuff is safe in a reinstallation (I think).:)

---

### Post by killertofu on 2007-10-15
> **angryfirelord said:**
> Release date is on Oct. 18, so try downloading it again when it comes out.

However, try again with this partitioning scheme:

-Windows NTFS (don't change that anymore)
- swap 512MB
- / takes remaining space

Note that it's / & not /root. If you do it as above, you should be able to boot into your system.

Yeah, it's just /.

> **wpshooter said:**
> I would get rid of everything and then if you need "Windows", install that and then install Feisty and let Gutsy age a while before you attempt that again.

Agreed, it'll be a while before I get up the guts for gutsy again.

---

### Post by killertofu on 2007-10-15
> **jpyanowski said:**
> OK, let me try. I've reinstalled Ubuntu on my box many times over the past two years (has it been that long??? 8-[ You can use the live CD and delete the ubuntu partition as part of the installation. Use the example given and also think about a /home partition. That way your stuff is safe in a reinstallation (I think).:)

Thank you very much.

> **dwhitney67 said:**
> I would install Ubuntu over windows.  You don't need windows.  You weren't born with it, and you can surely live and die someday without it too.

I just did a reinstall of Fedora 7 yesterday evening.  What a breeze!  I can't imagine Ubuntu requiring a degree in rocket science to install either.  Never use a beta release (e.g. Gutzy) unless you want to be a tester.  Even on the official release date I wouldn't touch it with a 10-foot pole.

You are probably right about windows, but I'm not where you're at yet in my knowledge, if that makes sense.
I am on Windows right now, that's how I am asking you guys for help.
Until I am confident about Linux, sadly, windows will be my crutch.

NO more betas! 100% agreed!

---

### Post by por100pre1 on 2007-10-15
Backup your files to removable media or external hdd. Give 50GB disk space to Windows, 20GB to /, 2GB to swap, the rest to /home. Use Fiesty or wait till Gutsy final.

---

### Post by -grubby on 2007-10-15
you should probably stay with stable,proven software, such as Fiesty Fawn.

---

### Post by Harpoon on 2007-10-15
Sorry about the trouble you've run into.  As I haven't yet yielded to the temptation to install Gutsy,I can't help with those particulars.  However, I can offer you some advice on making the situation less painful.

First, if you want to "magically share your home partition with windows" then go here:  [http://www.fs-driver.org/extendeddl.html](http://www.fs-driver.org/extendeddl.html) and download the driver (in windows).  Run it and make sure you assign a drive letter to the linux partition.  I've been using it for a "long" time, and the only glitch is that sometimes the windows install does not want to see all the files.  In that case, just run it again. The file you are looking for, BTW, is ext2ifs.

Second, if Gutsy is going to be a problem, Feisty is not a bad choice.  I'm running that on my core2duo (x64) laptop with (mostly) no problems.

I'd wait a week or two after Gutsy is released, and keep checking the forum to see what others are experiencing, and then decide if you want to try it again.

Good luck.

---

### Post by Tjarn on 2007-10-15
If I had a dollar fore each time I've messed up Linux, I'd be able to treat you all to a beer or 5.  I'm afraid that i didn't see exactly what the partitions were that you set up.  You had 15 gig for windows, that should be OK.  As long as you don't mess with that you should still be able to boot into it and run OK.  Figure that any Linux is a guess.  And I don't see much benifit for going into Feisty over Gutsy -- just go ahead and re-install Gutsy.  If it messes up, just reinstall again.  I assume that the live CD works OK?  Oh, if you can tell me what size the whole disk is, I'll give you my recommendations for partitioning.

The whole thing is don't expect to know everything first time you set it up.  Let yourself make mistakes and it's less painful.  If it doesn't work, re-install.  it's not that long a process and the second time through you know better what you're doing.

---

### Post by SnTholiday on 2007-10-15
If you want to store files on a partition that is read/write accessible by both Windows and Ubuntu, create an additional NTFS partition if you reinstall XP. I keep all my important documents, music, and photos on an NTFS partition that will never be touched. You can then allocate whatever space you want for Windows/Ubuntu. I believe you can also format a partition as FAT32 if you want, but I have never tried it.

---

### Post by por100pre1 on 2007-10-15
> **Tjarn said:**
> If I had a dollar fore each time I've messed up Linux, I'd be able to treat you all to a beer or 5.  I'm afraid that i didn't see exactly what the partitions were that you set up.  You had 15 gig for windows, that should be OK.  As long as you don't mess with that you should still be able to boot into it and run OK.  Figure that any Linux is a guess.  And I don't see much benifit for going into Feisty over Gutsy -- just go ahead and re-install Gutsy.  If it messes up, just reinstall again.  I assume that the live CD works OK?  Oh, if you can tell me what size the whole disk is, I'll give you my recommendations for partitioning.

The whole thing is don't expect to know everything first time you set it up.  Let yourself make mistakes and it's less painful.  If it doesn't work, re-install.  it's not that long a process and the second time through you know better what you're doing.

Sorry to differ, but it seems the OP doesn't like the idea of reinstalling over and over again. IMHO, the OP will do better installing Feisty, there's no need to install Gutsy at this time. Feisty will continue to be supported for a long time.

---

### Post by darkworld on 2007-10-15
The more problems you encounter the more you learn. yeah its tough but once you are there it worth it. Its like windows was just a stepping stone to another world. 

A guy at work said to me, hey I tried Linux again the other day, its getting better but loading programs is still a pain in the butt...... windows you just click ok install. Well my inside reaction to his comments was, go cook a microwave meal....I use real ingredients! 

Hang in there!

My only advice is run 2 drives! Fiesty and Gutsy.

---

### Post by vrangforestillinger on 2007-10-15
> **killertofu said:**
> 
How should I go about installing Feisty? Can I just use the LiveCD and mess around with the partitions there?


Just be sure you mess around in the installation dialog. And don't do the same mistake as I did earlier and resize a partition outside the installation dialog with the liveCD:

I started gparted from the system menu, unmounted the partition, and then told gparted to resize it. Then suddenly, the partition was remounted for some reason while the operation was still running! The result: A corrupted and useless partition. At that point, I started all over and repartitioned the whole drive.

Betas and partitioning can make you cry regardless of OS-flavour. Always backup!

---

### Post by bodhi.zazen on 2007-10-15
Somehow this did not feel like a support thread...

---

### Post by killertofu on 2007-10-15
Thank you all so much for the replies!
I am going to try to reinstall Ubuntu, this time Feisty.
If that fails, I'll cross that bridge when I come to it I guess.

Wish me luck! And I'll post the results after the install.

God bless you guys.

---

### Post by Tjarn on 2007-10-15
> **por100pre1 said:**
> Sorry to differ, but it seems the OP doesn't like the idea of reinstalling over and over again. IMHO, the OP will do better installing Feisty, there's no need to install Gutsy at this time. Feisty will continue to be supported for a long time.

Well, differences are what make horseracing fun!  No offense taken or meant.  IMO the problem isn't which distro he's using it's in the idea of how partitions work and how they can be shared.  With that in mind (and I really don't see whether using Feisty or Gutsy or another distro entirely makes any difference to his problem), my suggestion is to install as follows: (assuming you're using disk sda)
sda1 - 15 to 100 G  for Windows.  I'd go for lower, but some might want more.
sda2 - 10 G  ext3  For Linux /  (root directory)  I usually use 5 
sda3 - leave blank right now
sda4 -- logical partition for the additional two directories -- not used directly
sda5 -- two G swap space (2x actual memory is the rule of thumb)
sda6  -- 1/2 the memory left on the disk.  ext3  as /home
sda3 revisited -- the final amount of disk space left.  Format FAT32.  Mount as an additional disk on Windows, and as a shared file system on Linux.

As I say, the actual distribution isn't going to matter that much.  And I'm making a lot of assumptions about what someone might want  to do. 

My main point is that when you learn something new, don't always expect to get it right first time.  Allow yourself the luxury of a failure or two and you can sleep nights without a care.  If someone walks you through in person, you might get it right the first time, but digging out what you want is pretty tricky even when you've done it before.  I've ended up repartitioning two or three times when it was almost right.  And OK I get a little carried away.  I boot into Gutsy Feisty, Xbuntu, Kbuntu, PCLinuxOS, Foresight, and Debian.  My home directory in each is a symbolic link into another partition.  But I enjoy complications.  (I find 5 G is plenty for any / on todays distributions.)

---

### Post by happysmileman on 2007-10-17
> **Tjarn said:**
> 
My main point is that when you learn something new, don't always expect to get it right first time.  Allow yourself the luxury of a failure or two and you can sleep nights without a care.  If someone walks you through in person, you might get it right the first time, but digging out what you want is pretty tricky even when you've done it before.

AGreed, I think i learned more about computers by forgetting to defragment Windows before partitioning for Linux than I did following the instructions to built Linux from scratch (or indeed following the instructions to do anything), I found out why it broke, and I knew exactly what needed to be done in future, but more importantly, I understood the technical reasons WHY I have to do it in the future because of the reading I did

---

### Post by argie on 2007-10-17
A blank white screen on login? That happened to me when I didn't have direct rendering enabled but managed to enable Desktop Effects. Try to turn it off somehow. Maybe the settings are in gconf.

---

### Post by Extreme Coder on 2007-10-20
May I suggest using a different distro?(Please no body flame me :/ )
Some distros work with certain HW combinations better than others.
I'd suggest Mandriva, or OpenSUSE :)

---

### Post by here.david on 2009-05-13
While I was very impress with the easy of installing, easy of printers, scanner, updates...the SOUND and Movies not working makes me stay with XP x64 vs. Ubuntu 9.04 amd64....

I got all the "other issues worked out by looking at the abundant help" on the Forum...the sound and not getting the DVD movies, yes if I 'rip' them to Hard disk they almost run fine (sound is so-so) yet issues from the dvd directly...

The SUN VM does not allow xpro x64 amd64 to load nor the vista....was trying to work around these issues by using vm...

SO I must jump between Ubuntu and XpPro x64 - to much trouble...Maybe next year...as the previous try a few years ago could not get the printer/scanner to work..... and was SO VERY HAPPY with the easy of Ubuntu until the movies/sound...

HP a6110n 8GB ram with an ATI x1650 card

root@a6110n:~# sudo hdparm -Tt /dev/scd1

/dev/scd1:
 Timing cached reads:   874 MB in  2.00 seconds = 436.61 MB/sec
 Timing buffered disk reads:   16 MB in  3.14 seconds =   5.10 MB/sec

root@a6110n:~# sudo hdparm -Tt /dev/sda

/dev/sda:
 Timing cached reads:   1514 MB in  2.00 seconds = 757.12 MB/sec
 Timing buffered disk reads:  220 MB in  3.01 seconds =  73.13 MB/sec

root@a6110n:~# sudo hdparm -Tt /dev/sdb

/dev/sdb:
 Timing cached reads:   1382 MB in  2.00 seconds = 691.16 MB/sec
 Timing buffered disk reads:  230 MB in  3.01 seconds =  76.34 MB/sec

---

### Post by lvleph on 2009-05-13
What is the deal with necromancy?

---

### Post by overdrank on 2009-05-13
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]

---


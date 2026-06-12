---
title: "Newbie here looking for partition help"
date: 2018-09-29
forum: New to Ubuntu
---

### Post by hottunacartel on 2018-09-29
Hey all, newbie here.  
Looking to install ubuntu 14 on an older desktop. 
I'm running off of ubuntu live but I believe the desktop is a hp 6310f which from what I'm reading allows only 4 partitions.   I've been reading about making an extended partition but I'm a little confused.   Here is a screen shot currently of my partitions [https://imgur.com/a/zeK8ykO](https://imgur.com/a/zeK8ykO).   From a bit of research I feel like I need to remove one more partition and create an ext4 then create a extended partition.   Am I correct in this or incorrect?  
Thanks

---

### Post by yancek on 2018-09-29
The screenshot you posted of GParted shows 3 partitions with 255GB unallocated between sda2 and sda3.  Create an Extended partition on the 255GB unallocated and create logical partitions within it.  1 for the filesystem ( / ), one from swap and one for /home or /data if you want.  You can get all the details you need to do this by doing an online search for 'gparted manual', the entire manual with every possible option is available online.

---

### Post by TheFu on 2018-09-29
Most versions of Ubuntu 14.04 lost support in 2017.  A few like Ubuntu Server have support until April.
What this means is that installing 14.04 is not the best choice today.  At this point, everyone is moving their last remaining systems off 14.04. [https://www.ubuntu.com/about/release-cycle](https://www.ubuntu.com/about/release-cycle)  While running a live-boot Ubuntu, you can run **ubuntu-support-status** command to see which packages aren't supported any longer. On my 16.04 system, 470 packages are no longer supported. With a 14.04 system, it will be much worse.  Almost 1800 packages are still supported, however. Just trying to provide some knowledge.

To get help partitioning, please run** sudo parted -l** and post the exact command and output text **as text** here. Please use "code tags", so things are readable and line up correctly.  Adv Reply (#) does the code tags.  It would be best if you used 16.04 desktop that was still supported.  Some of the flavors get 3 yrs of support, others 5 yrs.

---

### Post by Bashing-om on 2018-09-29
hottunacartel; Hello - Welcome to the forum .

You presently have 3 partitions devoted to windows . and yes you are correct in that in the legacy partitioning scheme there is that 4 primary partition limit, and the way around this limitation is the 'extended' partition. Ubuntu will happily install to 'logical' partitions inside that 'extended' partition.

Now I ask you how much control do you want to exercise on what is allocated to ubuntu ?

The easy - simple - thing here is to choose "install along side" in the installer and allow the installer to do it's thing. While you can certainly set up the ubuntu partitions to your exact requirements, it does take a bit of knowing what to expect and what you are doing.
> 
sysop@x1804mini:/$ sudo blkid
[sudo] password for sysop: 
/dev/sda1: LABEL="x1604" UUID="d9c2a8e6-d014-42a6-846f-7e7892f4aef5" TYPE="ext4" PARTUUID="b6a9f0ca-01"
/dev/sda5: UUID="8d4743bc-8e47-4650-b5fd-1ea904d4ecda" TYPE="swap" PARTUUID="b6a9f0ca-05"
/dev/sda6: LABEL="x1810" UUID="49de038e-9807-469b-9009-540f2989f913" TYPE="ext4" PARTUUID="b6a9f0ca-06"
/dev/sdb1: LABEL="x1804root" UUID="1460de17-30e4-4566-b181-18c17b62887a" TYPE="ext4" PARTUUID="c6c4079f-01"
/dev/sdb2: LABEL="x1804home" UUID="5cd50446-1330-4130-a521-1ea936c9fc2a" TYPE="ext4" PARTUUID="c6c4079f-02"
/dev/sdb3: LABEL="x1804var" UUID="69b1f02a-5e00-415e-ab75-78fdd63f72a3" TYPE="ext4" PARTUUID="c6c4079f-03"
/dev/sdb5: LABEL="u1804" UUID="0b89d785-9ba8-4bd5-a41a-43462459c230" TYPE="ext4" PARTUUID="c6c4079f-05"
/dev/sdb6: LABEL="bups" UUID="a0c6dc1f-51d3-4824-b770-ce42d777277a" TYPE="ext4" PARTUUID="c6c4079f-06"
/dev/sdb7: LABEL="data" UUID="fe9cee2e-6812-46e1-b0a0-b03d5094763a" TYPE="ext4" PARTUUID="c6c4079f-07"
sysop@x1804mini:/$


Partitioning can be an art - there is a learning curve as custom partitioning is particular to each use case. You tell us what you want to do, and we are here to help.

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by hottunacartel on 2018-09-29
Hey thanks for the reply.   I was able to make the extended before but only saw the file system for the swap and not ```
/
``` 
will be looking at the manual, thanks. 
> **yancek said:**
> The screenshot you posted of GParted shows 3 partitions with 255GB unallocated between sda2 and sda3.  Create an Extended partition on the 255GB unallocated and create logical partitions within it.  1 for the filesystem ( / ), one from swap and one for /home or /data if you want.  You can get all the details you need to do this by doing an online search for 'gparted manual', the entire manual with every possible option is available online.

---

### Post by hottunacartel on 2018-09-29
Thanks as well for the reply. 
Fist off, I was trying to run mint 19 mate the other day.  Everything was fine until I installed it and there were all sorts of issues with the video driver.  I looked on ubuntu and saw that 14 seems to be the best for my specs.  I figured maybe my video card was outdated that I'd have to run an older version of linux.   
I've been messing around with partitions the last week so I'm not too "bad" at it.  I was able to move the ext4 to take use of the unallocated.  I just need to have a small portion of windows so I can run 3 programs.  At some point in the near future I want to wipe everythign and just run linux from now on.  I have mint on two much newer laptops downstairs but this pc has been sitting for at least 5 years unused.  I like the idea of opensource which is why I'm trying this.  
As above, not sure if i need to manually imput / and /home as I don't see it in the dropdown menu when adding a partition to the extended. 
Thanks so much 
> **Bashing-om said:**
> hottunacartel; Hello - Welcome to the forum .

You presently have 3 partitions devoted to windows . and yes you are correct in that in the legacy partitioning scheme there is that 4 primary partition limit, and the way around this limitation is the 'extended' partition. Ubuntu will happily install to 'logical' partitions inside that 'extended' partition.

Now I ask you how much control do you want to exercise on what is allocated to ubuntu ?

The easy - simple - thing here is to choose "install along side" in the installer and allow the installer to do it's thing. While you can certainly set up the ubuntu partitions to your exact requirements, it does take a bit of knowing what to expect and what you are doing.


Partitioning can be an art - there is a learning curve as custom partitioning is particular to each use case. You tell us what you want to do, and we are here to help.
[INDENT][INDENT]we can do that
[/INDENT]
[/INDENT]


---

### Post by hottunacartel on 2018-09-29
little update as I'm trying stuff 
Here is the extended with the swap and I think would be /home
I think I still need to put in a / which would be the 40 gig unallocated.  
[https://imgur.com/a/4zehsoE](https://imgur.com/a/4zehsoE)

---

### Post by Bashing-om on 2018-09-29
hottunacartel; Yepper :)


You are doing well :)
Ya still need to create that "root" (/) partition ... 40 Gigs will be just fine even a bit of overkill, but you have the space . 
> 
sysop@x1804mini:/$ sudo fdisk -lu
[sudo] password for sysop: 
Disk /dev/sda: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xb6a9f0ca

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048 290818047 290816000 138.7G 83 Linux
/dev/sda2       290820094 488396799 197576706  94.2G  5 Extended
/dev/sda5       290820096 300036095   9216000   4.4G 82 Linux swap / S
/dev/sda6       300038144 488396799 188358656  89.8G 83 Linux


Disk /dev/sdb: 111.8 GiB, 120034123776 bytes, 234441648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xc6c4079f

Device     Boot     Start       End   Sectors  Size Id Type
/dev/sdb1  *         2048  16386047  16384000  7.8G 83 Linux
/dev/sdb2        16386048  36866047  20480000  9.8G 83 Linux
/dev/sdb3        36866048  49154047  12288000  5.9G 83 Linux
/dev/sdb4        49154048 172034047 122880000 58.6G  5 Extended
/dev/sdb5        49156096 110596095  61440000 29.3G 83 Linux
/dev/sdb6       110598144 131078143  20480000  9.8G 83 Linux
/dev/sdb7       131080192 151560191  20480000  9.8G 83 Linux
sysop@x1804mini:/$ 

where sdb1 is my / for my "work" install of 18.04 (core).


[INDENT][INDENT]A bit of will goes a long way
[/INDENT][/INDENT]

---

### Post by hottunacartel on 2018-09-29
awesome!  So I can just type in ```
/
``` into the text part?  Never did it this way, in mint it has the drop down to select that when installing.     > **Bashing-om said:**
> hottunacartel; Yepper :)


You are doing well :)
Ya still need to create that "root" (/) partition ... 40 Gigs will be just fine even a bit of overkill, but you have the space . 

where sdb1 is my / for my "work" install of 18.04 (core).

[INDENT][INDENT]A bit of will goes a long way
[/INDENT]
[/INDENT]


---

### Post by TheFu on 2018-09-29
On older hardware, using a lighter DE like Lubuntu or Xubuntu or Ubuntu-Mate will usually work fine.  Just avoid the main Ubuntu Desktop with the heavy Gnome3 DE.

The others seem to be helping with partitioning nicely.  Don't want too many cooks ruining the soup. ;)   BTW, my desktop has less than 25G total storage, so 40G is overkill.   Don't forget that WinXP ran on less than 10G of storage and Win98 ran on less than 1G.

---

### Post by hottunacartel on 2018-09-29
lol I've noticed this is much easier than on the mint forums.  
Do you think the computer is too old to run a never version?  it stinks cause I have a ton of space but from what I was reading the nvidia 900 was a "mid to lower" line and had a ton of issues with mint install.  I'm sure I'll be back after this to figure out what was going wrong. 
> **TheFu said:**
> On older hardware, using a lighter DE like Lubuntu or Xubuntu or Ubuntu-Mate will usually work fine.  Just avoid the main Ubuntu Desktop with the heavy Gnome3 DE.

The others seem to be helping with partitioning nicely.  Don't want too many cooks ruining the soup. ;)   BTW, my desktop has less than 25G total storage, so 40G is overkill.   Don't forget that WinXP ran on less than 10G of storage and Win98 ran on less than 1G.

---

### Post by TheFu on 2018-09-29
I looked up the specs for that HP system.  Passmark of 3000+ and 6G of RAM should be fine for any version of Ubuntu.  The GPU will matter more for fancy desktops.  If you load Ubuntu-Mate, I think you'll be happy.  I'm running 16.04 Mate on a laptop with about the same passmark capabilities, but less RAM here.  Of course, the on-board GPU is probably better than the one in that HP unless you've upgraded it since it was shipped.

---

### Post by Bashing-om on 2018-09-29
hottunacartel; Welp 

> 
Do you think the computer is too old to run a never version? 

it is not a question of the version, rather how heavy of a (D)esktop (E)nvironment your hardware will support.

18.04 is the current (L)ong (T)erm (S)upport 'buntu release; for older hardware you might consider a flavor with a lighter desktop - say xubuntu or lubuntu .. ( or fastest is a minimal install. roll your own ) . 

[INDENT][INDENT]decisions decisions decisions
[INDENT][INDENT]open source, it is all about choice
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by hottunacartel on 2018-09-29
your awesome for doing that.  When do you select the flavor, on ubuntu website looking at the older versions [http://old-releases.ubuntu.com/releases/xenial/](http://old-releases.ubuntu.com/releases/xenial/) but not seeing how to select mate.  Using mat on my mint machine downstairs and like the slightly less fancy feel to it.  and nope no upgrades.  Just put a bigger monitor on but switched it out the other day when I was having issues with the video card driver, was trying easiest to hardest first lol. > **TheFu said:**
> I looked up the specs for that HP system.  Passmark of 3000+ and 6G of RAM should be fine for any version of Ubuntu.  The GPU will matter more for fancy desktops.  If you load Ubuntu-Mate, I think you'll be happy.  I'm running 16.04 Mate on a laptop with about the same passmark capabilities, but less RAM here.  Of course, the on-board GPU is probably better than the one in that HP unless you've upgraded it since it was shipped.

---

### Post by hottunacartel on 2018-09-29
lol honestly the few months I've been using linux its much nicer to have choices over windows. > **Bashing-om said:**
> hottunacartel; Welp 


it is not a question of the version, rather how heavy of a (D)esktop (E)nvironment your hardware will support.

18.04 is the current (L)ong (T)erm (S)upport 'buntu release; for older hardware you might consider a flavor with a lighter desktop - say xubuntu or lubuntu .. ( or fastest is a minimal install. roll your own ) . 
[INDENT][INDENT]decisions decisions decisions[INDENT][INDENT]open source, it is all about choice
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2018-09-29
hottunacartel -

[https://ubuntu-mate.org/download/](https://ubuntu-mate.org/download/)

[INDENT][INDENT]peace of cake :)
[/INDENT][/INDENT]

---

### Post by TheFu on 2018-09-29
I googled "ubuntu mate 16.04" and this was the top result: [https://ubuntu-mate.org/download/](https://ubuntu-mate.org/download/)  It is an official Ubuntu.  That's important to me.

I normally get my Linux releases from mirror at a local university, that makes the downloads FAST.  

BTW, we tend to bottom post here, not top post. Also, we only leave the important, relevant parts of the prior posts.  Some people here pay by the byte to download.

---

### Post by hottunacartel on 2018-09-29
lol see how new I still am!   googled "ubuntu mate" and that came up lol.  Though you downloaded them all from the ubuntu website.  New things I'm learning :) 
one more thing and not sure who to ask it to.  
I read the swap is supposed to be equal to the ram.  > **Bashing-om said:**
> hottunacartel -

[https://ubuntu-mate.org/download/](https://ubuntu-mate.org/download/)
[INDENT][INDENT]peace of cake :)
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2018-09-29
hottunacartel

Again, the amount of swap depends on the use case .. 4 Gigs should be plenty .
That old adage of "swap == ram" applied to the times of limited ram and code not optimized to the extent it is today. If you have 4 Gigs of ram, in normal use swap will not even be touched.

[INDENT][INDENT]them little details
[/INDENT][/INDENT]

---

### Post by hottunacartel on 2018-09-29
Bashing-om  
  Okay so then I can just move the rest, its not a lot to the home partition.  
I'm still confused kinda that I can just manually put in / or /home instead of selecting it from the drop down (or at least I hope I can manually put it in and have it work) 

Going to download mate 18 and install it tonight maybe.... livepd is on!

---

### Post by TheFu on 2018-09-29
> **hottunacartel said:**
>  
I read the swap is supposed to be equal to the ram.

Did you search these forums before asking the question?

The answer is "it depends."
If you hibernate, then that rule is fine.  I don't hibernate and only use standby mode when I'm not travelling for security reasons. Both standby and hibernation are security considerations.

IMHO, desktops need 4G of swap.  
Low RAM desktops need that amount so the monster browsers have enough virtual memory to be abused.
Desktops with 4G or more RAM, probably have enough, but the more RAM people have, the more browser tabs they feel entitled to leave open.

The purpose of virtual memory (swap), is to provide some feedback to the end-user when RAM use is beyond the physical amount available.  That feedback should have the machine getting slower and slower, which swap on a spinning disk will accomplish.  With SSDs, the swap slowdown isn't a clear and we often miss it, until the system totally runs out of both RAM and virtual memory. The result is either a stalled computer or a locked up system.  Often, if you wait 5-10 minutes, the system will come out of that state and you can close down the monster RAM-using programs.  Then everything will be fine again.   But if the system doesn't come back after 30min and you can't remote in over ssh from another machine to kill firefox or chrome, then there isn't much choice besides the BSR - Big Red Switch.

---

### Post by hottunacartel on 2018-09-29
@The Fu 
 I have searched for weeks, between this forum and many more.  For me though, it helps quite a bit having back and forth with someone instead or reading posts from beginning to end and still not understanding.  
I see that you are quite knowledgeable about linux, which is great.  I am not, and me asking questions pertaining to my question is the easiest way for me to understand.  
I have researched what ram does as well as what the swap does.  I'm simply asking because I'm not sure if there is any kind of difference between how I have done it in the past and how I am about to do it.

---

### Post by TheFu on 2018-09-29
> **hottunacartel said:**
> @The Fu 
 I have searched for weeks, between this forum and many more.  For me though, it helps quite a bit having back and forth with someone instead or reading posts from beginning to end and still not understanding.  
I see that you are quite knowledgeable about linux, which is great.  I am not, and me asking questions pertaining to my question is the easiest way for me to understand.  
I have researched what ram does as well as what the swap does.  I'm simply asking because I'm not sure if there is any kind of difference between how I have done it in the past and how I am about to do it.

Nobody knows this stuff and we all learn in slightly different ways.  The rules of thumb around swap have drastically changed since the early 1990s when having 4MB of RAM was fantastic. Back then, 2-3x RAM was the answer for swap.

And THIS is exactly the reason these forums rock. You did the searching and it wasn't clear based on the results found.   I hope the other paragraphs were helpful with the "why", not just the "use 4G" as the answer. "Why" matters for a deeper level of understanding.

Really short questions with little background often get really short answers without the "why."  Sometimes that is exactly what is needed.  I tend to avoid those questions. Call it a personality issue. I have many.

And I asked because google found this [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) which is an extensive answer.  I do disagree concerning how to edit systems files.  **gksudo gedit** should be **sudoedit** instead, but there are different opinions about that.

---

### Post by hottunacartel on 2018-09-29
@TheFu 
I totally understand, I didn't want just, do this and do that.  I wanted to and want to learn how to do things including why I'm doing them.  I see on a lot of forums when new people ask and they just do what they say and not ask.   That is why I ask so much.  
So it was funny... When I was messing around with the partitions on gparted, I totally forgot to hit the check mark.  So after I downloaded mate 18, I came back upstairs and booted from the usb, went through all the steps and got to the partition part and said "****" all stuff I did was gone, back to normal.   So I did it again and it was easier because there was the drop down with / and /home and linux swap.  Much much easier.  Kinda of proud I almost did this myself lol. 
[https://imgur.com/a/TsLU5oQ](https://imgur.com/a/TsLU5oQ)
For whatever else reason I don't know, the 3rd party software is working fine this time.  No idea why but I'm not going to complain.  

Thanks all for your help and I'm sure I'll see you around.

---

### Post by yancek on 2018-09-29
You should have the same drop down menu option for Mount point when you are creating a partition in Ubuntu as you saw with Mint.  Mint uses the same installer (Ubiquity) as Ubuntu.

---

### Post by hottunacartel on 2018-09-29
Yea to totally forgot about the installer.  Was trying to make the partitions prior in gparted, just so I got a feel of making the extended parts.

---


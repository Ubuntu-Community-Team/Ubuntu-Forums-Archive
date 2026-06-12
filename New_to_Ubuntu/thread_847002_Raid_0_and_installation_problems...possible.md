---
title: "Raid 0 and installation problems...possible?"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by jim256 on 2008-07-02
Hey all,
Ok, so I had Ubuntu on my previous box about a year or so back, and was playing around with 7.04/7.10 and really liked it.

My problem was that I then upgraded to a slightly higher performance pc, one that I configured as Raid0. I read back then, and have done some reading now, but must say that I feel more than slightly overwhelmed/lost.

My question that I just want to get is...With my current setup, A WinXP Pro SP3 PC, with two 80gb HDD's configured as Raid0 using the Promise Fasttrack TX2 controller and partitioned as a few different sizes/drives...Can I install Ubuntu with Raid 0 or no?

If not, can I install it at all, such as using the method of a live cd (did this a few times before).

Thanks a lot!,
Jim.

p.s. im sorry if this answer is obvious. I am pretty used to the forum system and am a very active member of a couple boards, but just haven't been able to find the straight answer im looking for just yet.

---

### Post by jim256 on 2008-07-02
alright well i loaded up the live cd, installed dmraid, and that definitely helped. my ubuntu [livecd] system can now recognize the raid partitions but...when attempting to install, after hitting all the "ok"'s and "forward"'s, I get this error...

"The ext3 file system creation in partition #4 of Serial ATA RAID pdc_jgabeiii (stripe) failed."

any ideas anyone? would be much appreciated.

Thanks!...sorry for my noobishness...

EDIT: ok well i thought i may as well give ext2 a shot and...it got farther, but still got this error not too long after :S
"The attempt to mount a file system with type ext2 in Serial ATA RAID pdc_jgabeiii (stripe) at / failed.

You may resume partitioning from the partitioning menu."

thanks!

i would love most to just go ahead and use ntfs but...my only mount options there are \dos and \windows?...?
thx.

EDIT2: reiserfs gave me this: "The attempt to mount a file system with type reiserfs in Serial ATA RAID pdc_jgabeiii (stripe) at / failed.

You may resume partitioning from the partitioning menu"

and xfs and jfs gave me the same error that i got very first. im not sure if any of this is really relavant/matters/helps but..thought i might as well throw it out there.

---

### Post by cariboo on 2008-07-02
To be really truthful I would dump the raid0 and install windows on one drive and ubuntu on the other. Otherwise if you don't want to do that, maybe consider a wubi install. That way you still keep your raid array and you can run ubuntu from inside windows.

Jim

---

### Post by jim256 on 2008-07-02
> **cariboo907 said:**
> To be really truthful I would dump the raid0 and install windows on one drive and ubuntu on the other. Otherwise if you don't want to do that, maybe consider a wubi install. That way you still keep your raid array and you can run ubuntu from inside windows.

Jim

thx for the response/help.  i would really love to do a wubi install, you bet.  the only problem is that it wont work with my configuration (or at least thats what i have read/heard other times)...do you know of anything different?

i will try wubi again right now.

EDIT: quoted from [http://wubi-installer.org/faq.php:](http://wubi-installer.org/faq.php:) 
"...Most computers purchased within the last 3 years should be able to run Ubuntu fine, and Xubuntu is suitable for older computers. Software raids (aka fakeraid) are not supported..."  

i have discussed this with a friend, who is more than a little computer/tech savvy, and they confirmed multiple times that my raid was not software/fakeraid...but it seems that it is somehow, because wubi has not worked in the past. here goes nothin...

---

### Post by phidia on 2008-07-02
I don't know if you have already checked the community docs on RAIDS [here]("https://help.ubuntu.com/community/Installation#Installing%20on%20external%20or%20RAID%20hard%20disks") but there it is for what it's worth.

---

### Post by jim256 on 2008-07-03
> **phidia said:**
> I don't know if you have already checked the community docs on RAIDS [here]("https://help.ubuntu.com/community/Installation#Installing%20on%20external%20or%20RAID%20hard%20disks") but there it is for what it's worth.

well i had read that.  and i have tried booting up the livecd, then installing dmraid and doing it that way, but it still refuses to install.

for the record, i tried wubi, and when booting for the first time i got this error:

[xxx.xxxxxx] Buffer I/O error on device sda3, logical block 0
[xxx.xxxxxx] Buffer I/O error on device sda3, logical block 0
[xxx.xxxxxx] Buffer I/O error on device sda3, logical block 1
[xxx.xxxxxx] Buffer I/O error on device sda3, logical block 2
[xxx.xxxxxx] Buffer I/O error on device sda3, logical block 3
[xxx.xxxxxx] Buffer I/O error on device sda3, logical block 0
[xxx.xxxxxx] Buffer I/O error on device sda3, logical block 0
....

anything anybody!?

---


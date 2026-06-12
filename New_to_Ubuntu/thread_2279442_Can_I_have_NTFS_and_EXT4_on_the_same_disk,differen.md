---
title: "Can I have NTFS and EXT4 on the same disk,different partitions?"
date: 2015-05-23
forum: New to Ubuntu
---

### Post by azoreus on 2015-05-23
Hello,I have 2 hard disks,one of 500 GB with windows 7 and another one of 160 GB that I want to use for Ubuntu and I need to format it to EXT4 for Ubuntu.BUT I have a small partition of 5 GB on the second hdd that I use right now for pagefile for the 1st hdd with Windows.My question is can I still keep this small partition for pagefile in NTFS and format the rest in EXT4 for the partitions of Ubuntu? Can it create any problems for the disk in the long run,reduce its lifespan?

---

### Post by Bashing-om on 2015-05-23
azoreus; Hi ! Welcome to the forum .

Short answer is yes , NTFS and ext4 partitions can and do co-exist on the same hard drive.
Now what might be tricky as you desire to keep the present NTFS partition intact means manually partitioning the drive for the ubuntu allocation.
Initially done from Windows,
Windows' tools for Windows' file systems
ubuntu tools for ext4 file systems.

When you are ready to proceed, and desire a bit of guidance;
Boot the liveDVD and provide screenshots from gparted of both hard drives and we can better advise.
> 
Can it create any problems for the disk in the long run,reduce its lifespan?
 Well, if you use it you are going to wear it out. Installing ubuntu however will not have an adverse effect.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by azoreus on 2015-05-23
Well thank you for the answer and help,I had to ask because I remember reading something about NTFS and EXT4 on the same hdd means more heavy work for that HDD,booting one time into NTFS and then again booting into EXT4
 I m gonna install this in a couple of days cause I miss Ubuntu and Linux and I don t wanna keep this hdd just for windows pagefile.It is not the first time I install Ubuntu or manual partition a hdd for Ubuntu so I just wanna ask if doesn t just mean that I will have to leave the 5gb partition alone and format the rest into: /,/home,swap? cause if I remember correctly  Ubuntu recognizes NTFS partitions so I just leave alone the small partition which I think will be labeled as NTFS from the ubuntu installer or if not just as a 5gb partition and move on with the rest?

---

### Post by Bashing-om on 2015-05-23
azoreus; Yep;

You have the right of it .
Just partition as you desire for ubuntu - leaving the NTFS partition alone.
All that is required for ubuntu's minimum is a partition for large enough '/' and a swap partition . From this minimum partitioning scheme your use case will dictate alternative schemes ( many advocate a separate /home partition, I do ) .

[INDENT][INDENT]no luck wished ->
[INDENT][INDENT][INDENT]all in the Prior Prudent Planning
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-05-23
azoreus; Yep;

You have the right of it .
Just partition as you desire for ubuntu - leaving the NTFS partition alone.
All that is required for ubuntu's minimum is a partition for large enough '/' and a swap partition . From this minimum partitioning scheme your use case will dictate alternative schemes ( many advocate a separate /home partition, I do ) .
You do the ubuntu partitioning in ubuntu partition editor GParted.

[INDENT][INDENT]no luck wished ->
[INDENT][INDENT][INDENT]all in the Prior Prudent Planning
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by azoreus on 2015-05-23
Ok thank you very much for all the help and have a brilliant nice day

---

### Post by Bashing-om on 2015-05-23
azoreus; Hey;

> 
 for all the help and have a brilliant nice day


Thanks, I will as my Lord is my guide .
As this discussion seems concluded;
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]see ya on the other side
[/INDENT][/INDENT]

---


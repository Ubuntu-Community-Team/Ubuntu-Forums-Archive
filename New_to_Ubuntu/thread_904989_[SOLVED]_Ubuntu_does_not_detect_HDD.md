---
title: "[SOLVED] Ubuntu does not detect HDD?"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by JSeb on 2008-08-29
Hi! Trying to install Ubuntu on a new machine.

I wanted to partition my blank HDD with Ubuntu LiveCD, but it didn't seem to detect my drive. So I downloaded GParted LiveCD, and it worked. 

My partition ([FONT="Courier New"]sudo fdisk -lu[/FONT]):
...Oops, lost it. If you need it, I'll try again...

Basically, my primary partition is NTFS, for XP.
Then I have an extended partition with two ext3 sub-partitions, for sharing XP/Ubuntu.
Then I have a ext3 partition for Ubuntu, and a Swap partition.

(yes, ext3 for shared stuff... I want to try [FS-Drive]("www.fs-driver.org"))

I then installed XP Pro on my primary partition.

Finally, I'm trying to install Ubuntu from the LiveCD.
After the keyboard question, I get to the partitionner. It SKIPS the "prepare disk space" dialog, and goes straight to the "prepare partition" dialog, which is empty. Exactly like [this]("http://ubuntuforums.org/showpost.php?p=5652138&postcount=11").

I did
[LIST]
[*]check my Ubuntu CD for defects (none)
[*]Use testdisk, but I'm not sure I did it ok
[*]reformat all my ext3 partitions.
[/LIST]

By the way, I didn't leave any space between my partitions, if that matters.

I have a **SATA** drive, LG GSA-H55L.

Please, help?

---

### Post by Bachstelze on 2008-08-29
Maybe try the Alternate CD?

---

### Post by old-codger on 2008-08-29
Don't know if this will help, but I had the same problem. Was not trying a duel boot, just trying to install hardy. I changed the jumper on the hard drive from master to cable slect. Even gparted on the live disc could not find it. I down loaded and burned gparted live and it could see the hard drive.Just not Ubuntu. After I changed the jumper all went well. Don't understand it as I had Dapper on it and reinstalled it several times.Might be worth a try.
        old-codger

---

### Post by JSeb on 2008-08-29
> **HymnToLife said:**
> Maybe try the Alternate CD?
What's that?

> **old-codger said:**
> I changed the jumper on the hard drive from master to cable slect.
I thought about the jumpers, but there's a sticker on my drive that says that they are not necessary for SATA drives (didn't know that). There are indeed no jumpers on the drive. Maybe I should investigate more on that?

---

### Post by Bachstelze on 2008-08-29
> **JSeb said:**
> What's that?

CD with a standard, text-based installer. Less pretty, but also far less likely to fail on you.

---

### Post by JSeb on 2008-08-30
Okay, downloading alternate CD now... will try it later today.

Thanks!

---

### Post by JSeb on 2008-08-30
Damn! Alternate CD doesn't detect my drive ](*,)

You know what? The drive I mentionned in my first post was my DVD burner. My HDD is Western Digital Caviar SE16 500GB SATA-2. I'll check into that: maybe a driver is missing?

What I don't get: GParted LiveCD loads into some flavor of linux, and recognizes my drive without any problem. Why not Ubuntu?

Any clue is appreciated.

---

### Post by JSeb on 2008-08-30
Hey, it's me again! I know I'm pretty much talking to myself here on this n00b forum, but maybe this could help somebody else.

Searching the forum, I found [this]("http://ubuntuforums.org/showpost.php?p=5675236&postcount=2") concise, straightforward advice.

I first tweaked my BIOS so my SATA controller would be set to AHCI, and Ubuntu LiveCD was able to recognize my HDD \\:D/

But not windows anymore :cry:

But the second advice, the one with the "all_generic_ide", seems so far to be solution!

Thanks!

---


---
title: "Can anyone explain to me the differences between filing systems?"
date: 2010-06-03
forum: Recurring Discussions
---

### Post by Legendary_Bibo on 2010-06-03
I used to only know about Fat 32, Fat 16, and NTSF, but now there's ext3, ext4, and BTRF. I don't understand how it makes a difference. How does it work exactly?

---

### Post by philinux on 2010-06-03
[http://www.linux.org/lessons/advanced/x1254.html](http://www.linux.org/lessons/advanced/x1254.html)
[https://help.ubuntu.com/community/LinuxFilesystemsExplained](https://help.ubuntu.com/community/LinuxFilesystemsExplained)
Moved to recurring discussions.

---

### Post by kamaboko on 2010-06-03
As one of my college profs would say, "that sounds like a great research project.  have a paper for me in four weeks".

---

### Post by SunnyRabbiera on 2010-06-03
File systems are simple to understand, I will quote myself on the matter:

A lot of people when they first use linux seem to always ask about defragmentation, understandable as they are used to Windows and defragging.
A lot of people have tried to explain why Linux filesystems typically dont need defragging.
I have seen some interesting explanations, the most interesting way I have seen someone explain the difference between EXT3/4 and NTFS is that EXT is like pigeonholes while NTFS is like a string of beads.
A good analysis indeed, the way I see the difference is like this:

EXT3/4 and most other Linux filesystems is like a book, or if one must be literal its like a journal (as most linux filesystems are journalized though not all)
This said journal is a composition book, for me its a 75 page composition book.
Currently I use 31 pages in this book, one entry consistent with the next.
On day 1 I ate, drank and slept, same as most other days though on some days I do more then others.
On day 6 I had to go into work at 6:00AM, on Day 12 I had to go to the supermarket.
But most of my entries are organized and the flow of my entries are similar.

NTFS and FAT is more like a series of Post it notes on my refrigerator.
Note 1 says get milk
Note 2 says get eggs
Note 3 says pick up the kids from soccer practice
Note 4 says what I will make for dinner tonight
While my journal explains what I did that day, my post it notes tell me what I have to do today...
It still gives me the same info, my journal says I went to to the store to pick up the eggs while my post it note tells me that I need eggs.
But once I got those eggs that post it note becomes unneeded, but what if I forget to take that post it note down and the following day I go out to the store to buy eggs again forgetting I picked up eggs the other day.
My journal says I already got those eggs, but my post it note says otherwise.
The confusing gets worse when I start running out of room on my refrigerator and I dont take down all those other post it notes that I made and when I make a new post it note telling me to do the laundry today and put it on the refrigerator and all my other post it notes fall down.
This is a big issue, not only do I have all these post it notes on the floor but I cannot tell what day they are from as I never put any dates on my post it notes, just things I had to do on that day...
I didnt think of the long term when I made those post it notes.

My journal keeps my records of what I did that day better then my post it notes, because I have the date and time numbered in my journal but these post it notes I have are so tiny I dont have room to put a date on them and I have big bold handwriting.
When I drop my journal on the floor its very easy to find where I left off at if I lost my place but my post it notes are in chaos.

---

### Post by Legendary_Bibo on 2010-06-03
> **SunnyRabbiera said:**
> File systems are simple to understand, I will quote myself on the matter:

A lot of people when they first use linux seem to always ask about defragmentation, understandable as they are used to Windows and defragging.
A lot of people have tried to explain why Linux filesystems typically dont need defragging.
I have seen some interesting explanations, the most interesting way I have seen someone explain the difference between EXT3/4 and NTFS is that EXT is like pigeonholes while NTFS is like a string of beads.
A good analysis indeed, the way I see the difference is like this:

EXT3/4 and most other Linux filesystems is like a book, or if one must be literal its like a journal (as most linux filesystems are journalized though not all)
This said journal is a composition book, for me its a 75 page composition book.
Currently I use 31 pages in this book, one entry consistent with the next.
On day 1 I ate, drank and slept, same as most other days though on some days I do more then others.
On day 6 I had to go into work at 6:00AM, on Day 12 I had to go to the supermarket.
But most of my entries are organized and the flow of my entries are similar.

NTFS and FAT is more like a series of Post it notes on my refrigerator.
Note 1 says get milk
Note 2 says get eggs
Note 3 says pick up the kids from soccer practice
Note 4 says what I will make for dinner tonight
While my journal explains what I did that day, my post it notes tell me what I have to do today...
It still gives me the same info, my journal says I went to to the store to pick up the eggs while my post it note tells me that I need eggs.
But once I got those eggs that post it note becomes unneeded, but what if I forget to take that post it note down and the following day I go out to the store to buy eggs again forgetting I picked up eggs the other day.
My journal says I already got those eggs, but my post it note says otherwise.
The confusing gets worse when I start running out of room on my refrigerator and I dont take down all those other post it notes that I made and when I make a new post it note telling me to do the laundry today and put it on the refrigerator and all my other post it notes fall down.
This is a big issue, not only do I have all these post it notes on the floor but I cannot tell what day they are from as I never put any dates on my post it notes, just things I had to do on that day...
I didnt think of the long term when I made those post it notes.

My journal keeps my records of what I did that day better then my post it notes, because I have the date and time numbered in my journal but these post it notes I have are so tiny I dont have room to put a date on them and I have big bold handwriting.
When I drop my journal on the floor its very easy to find where I left off at if I lost my place but my post it notes are in chaos.

Thanks for the analogy...I think :P

---

### Post by SunnyRabbiera on 2010-06-03
I tried my best there you know :D
Now BTRFS is a B tree file system, that works like well... a tree.
Each folder is a branch and each file a leaf, thats how I understand it.
Now NTFS on windows is a B tree, it does not encourage me one bit on why B tree file systems are better then journalized ones.

---

### Post by tom66 on 2010-06-03
That journal analogy is wrong, because most Linux filesystems and NTFS have journals. A journal only helps if a disk crash occurs or if power is lost when writing data. If anything, it slows down write time. 

I think you're thinking of how each filesystem organises its files. B-trees and journals are different.

---

### Post by SunnyRabbiera on 2010-06-03
> **tom66 said:**
> That journal analogy is wrong, because most Linux filesystems and NTFS have journals. A journal only helps if a disk crash occurs or if power is lost when writing data. If anything, it slows down write time. 

I think you're thinking of how each filesystem organises its files.

Well yes, but NTFS's journals is more like a coloring book in the hands of a 2 year old

---

### Post by tom66 on 2010-06-03
NTFS isn't that bad. It's actually a reasonably good product. But I guess it is what you would call a "general purpose" filesystem. Not really specialised in anything. 

The ext series and ReiserFS are also general purpose filesystems. But a filesystem like XFS is more useful for handling large files. This is a good thing on Linux, allowing you to pick the particular file system for your uses.

---

### Post by SunnyRabbiera on 2010-06-03
> **tom66 said:**
> NTFS isn't that bad. It's actually a reasonably good product. But I guess it is what you would call a "general purpose" filesystem. Not really specialised in anything. 

The ext series and ReiserFS are also general purpose filesystems. But a filesystem like XFS is more useful for handling large files. This is a good thing on Linux, allowing you to pick the particular file system for your uses.

Yeh but for the sake that the filesystem fragments every time you edit something makes NTFS very shaky

---

### Post by tom66 on 2010-06-03
I'm not so sure on that. I've rarely defragged NTFS Windows systems. FAT32  on the other hand... NTFS isn't the best filesystem. But it works fairly well for its job, which is run desktop operating systems. Now, I disagree with running servers on Windows because NTFS is just not fast or reliable enough. And because Windows is subject to many attacks.

---


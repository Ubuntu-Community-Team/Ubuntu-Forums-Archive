---
title: "Can't get my setup to work."
date: 2011-09-14
forum: New to Ubuntu
---

### Post by Kracer on 2011-09-14
I have a TB HDD for Windows which I need to keep so my family can use the computer.
So I bought a 500gb drive to install ubuntu on.
Many issues came up.
They all point that I haven't formatted or setup my hard drive corretly.
How should I go about that?
And when I'm done how do I make it easy to choose which OS to boot on startup?
Thanks in advance

---

### Post by Basher101 on 2011-09-14
1. Pop in your ubuntu live CD
2. Boot from the live CD
3. Select "Install ubuntu" once it loaded
4. i will attach screenshots for further guidence.

---

### Post by Basher101 on 2011-09-14
alright looks like i have not taken the thought of a second **_internal_** hdd..so you will need to set up the partitions manually in order to *_ensure_* you get it only on your second internal hdd not the primary one. i will make screens on how to use the partition tool.

---

### Post by Basher101 on 2011-09-14
To give you an exact step by step explaination, could you give me a picture on how you want your partitions? If you did not know Ubuntu uses the ext4 filesytem. Windows cannot read it, but Ubuntu can read the Windows NTFS filesystem. So i suggest a setup like mine: a smaller, approx 30 GB partition for the Ubuntu OS itself and a Shared NTFS partition for shared storage. There you should store large files, music, pictures, documents...the only thing you should keep on your 30 GB ubuntu partitionn should be the programs. This should not be all too difficult since the Ubuntu software centre always installs into your root partition (Ubuntu). Would you like it this way, or do you want the entrire HDD to be used by the ext4 filesystem? keep in mind that you cant access it through windows then.

---

### Post by Kracer on 2011-09-15
For my files I planned using the D: because the TB drive is split in half(C: for windows and prgramms, D: for all of our files)
All I want is a 500GB partition to install ubuntu(I know it's WAY overkill but there wasn't any smaller drives.
I assume Ubuntu can read NTFS(That's the filesystem of D:)
From where do I format the drive?
And how do I make the BIOS see it beacause somehow it's not coming up.

---


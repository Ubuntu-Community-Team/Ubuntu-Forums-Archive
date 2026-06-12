---
title: "Partitioning a Big HD that already has Windows and Ubuntu on it?"
date: 2013-10-22
forum: New to Ubuntu
---

### Post by conconbay on 2013-10-22
**Background:**
ABSOLUTE Beginner here. This community seems very friendly to people trying to become more "tech/linux savvy" so I figure you guys can help me out. I have a Samsung Series 7 Chronos with a 750gb HDD and a 256gb SSD. I have a few folders with school essays and stuff that I want to save but I don't care about saving anything else. 

[B]Problem:
[/B]My laptop came with windows 7 installed and in my green user attempt to become a linux Ubuntu user I managed to somehow use Wubi to download ubuntu and install it. I chose Ubuntu 12.04 because it had "support" til 2017. Idk what that means but I figure by 2017 I won't need the "support" anymore and can upgrade then. Anyways I think wubi partioned my HD for me so I think I now have windows 7 and ubuntu on my HD. I worked with Ubuntu some and then booted up windows again and it restored my computer to a previous state. I guess it was mad at me for using ubuntu. I need help figuring out the right kind of dual boot I need to do. I've been reading a lot of stuff about partitioning and resizing so that I have a partition for each OS and then a Big chunk of memory to use as storage between them. I would like to go ahead and just clean boot Ubuntu and force myself to convert but I need windows 7 to finish a few of my mandatory iTech classes at school. Also I figure it would be safe to keep windows in case I take a while to get used to ubuntu so I can stay productive in school. Anyways I figure my laptop is capable of a dual boot but I need guidance in what kind I should do or how I should resize my partitions and any advice, helpful links, or help you guys could offer to my situation. 

P.S. I think I might change my name to greenie weenie since I am such a stone age computer using newb

---

### Post by conconbay on 2013-10-22
Just tried to insert a screen shot of my disk management screen and noticed that my Microsoft Word, Excel, and Powerpoint are not working anymore. It says they are 32bit versions and can't be intalled with my 64bit installer? Things are going wrong fast! Help Please

---

### Post by oldfred on 2013-10-22
Wubi is not a partitioned install, but just a file folder inside Windows NTFS partition. It is for a short term trial over just using liveDVD for a while as you can update. New gpt partitioned drives which all new Windows 8 systems with UEFI have, do not work with wubi, so wubi is being discontinued.

With two drives you have lots of room for partitioned install. I have two Ubuntu / (root) installs in my 60GB SSD with all data on my hard drive.

Post this either from wubi or liveDVD or flash drive desktop installer:

       sudo parted /dev/sda unit s print
            sudo parted /dev/sdb unit s print
df -h

---


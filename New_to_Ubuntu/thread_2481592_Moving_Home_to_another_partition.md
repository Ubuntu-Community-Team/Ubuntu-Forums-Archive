---
title: "Moving Home to another partition"
date: 2022-12-03
forum: New to Ubuntu
---

### Post by nowyoumadememad on 2022-12-03
Hello everyone o/
Ubuntu 20.04.01. Having a small SSD with Ubuntu one half shared with Win10 (for gaming purposes). Have recently purchased an extra 1tB SSD which again is split into two, one half NTFS, one Ext4 (Formatted with Gparted) and I want to move my Home folder over to that partition. I have found many a description how to but decided on this at Ubuntu.com: [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)  But fell into trouble getting past the Fstab setup. I suspect I misunderstand some of the abbreviations, particularly the dates. I follow description, do mostly cut 'n paste but fail miserably when I come to writing the dates (I believe) as nothing happens when i hit enter after writing the command, I cannot see any duplicate nor can I compare any. I stopped there before I did any more wrong,  seeking advice here. Someone out there who can lead me on the right path?

---

### Post by oldfred on 2022-12-04
The only date related command is for the backup and that is just so you have the date you made the backup in the file name.
You do not even have to have the date, but should have backup. I often copy it into /home so part of my normal backup as I do not backup /etc as some suggest. I only edit a few files in /etc & save copies or have script that auto edits what I want to change.

And alternate to moving /home is moving data.
I keep /home but really only the hidden (.dot) user configuration files. All the folders with data like Music, Documents, Downloads, etc & a few more I create are in a separate data partition. I then mount that data partition and link all those folders back into /home, so it looks like normal, but data is actually not in / but in another partition. You can just move some data or have some linked from your NTFS data partition. Back when I still had XP, I had both a shared Windows partition and a Linux data partition.

[https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909](https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909)
[http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198) &
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)

---

### Post by nowyoumadememad on 2022-12-15
Hello everyone o/
So:
I have to mark this one as solved even if it never was. I found a solution to how move the home folder, had a copy on the new SSD and were on the final when everything froze; I mean Everything except I could move the mouse arrow around, nothing else responded, keyboard , nothing! Could not stop, reverse or kill any process just frozen screen. Waited for 30 minutes, nothing. Waited 30 minutes more and switched everything off. The SSD with the OS's on had crashed: When i tried to start the computer again nothing happened until I disconnected the cables to the drive and I could see the UEFI screen again. Now six days later, four days into the process I have everything up and running again. Now with a 1TB drive shared 500GB each OS and all sorrows (almost) forgotten. Enough space now not to worry about size of the home folder and spent some savings on an external back-up. 

Seasons greetings
and
Brgds

---


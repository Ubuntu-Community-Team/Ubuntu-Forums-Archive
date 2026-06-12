---
title: "Format USBs, exFat or something else?"
date: 2019-04-14
forum: New to Ubuntu
---

### Post by billy3xs on 2019-04-14
[COLOR=#000000][FONT=Arial]I'm trying to format a few USB drives that can handle movies in Windows, Ubuntu, and Nvidia Shield (Andriod).[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I'm confused about File Sytem Formats; NTFS, FAT, and Fuse. From right-clk on a USB Drive in Ubuntu 18.04, the options for formatting are NTFS and FAT, which Windows says is Fat32, which doesn't work for movies larger than 4 GB.  I see someone recommeded exFat, but I don't see it listed in the format options.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]So it's NTFS, but there's a warning that if the drive has any error in NTFS, Ubuntu will not touch it.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I could try entering via the terminal, but I have little experience. I'm trying to learn and have had some success following explicit instructions. [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I have three USB drives which were formatted exFat.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]So I loaded “exFat to Fuse” in the terminal from itsFOSS and it worked for a small drive, but not for my 1TB USB drive. 
Maybe there's an error with that drive. I could try NTFS on it...or redo exFat.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]again:[/FONT][/COLOR]

[LIST=1]
[*][COLOR=#000000][FONT=Arial]NTFS has a warning [/FONT][/COLOR] 
[*][COLOR=#000000][FONT=Arial]Fat32 can't handle large files [/FONT][/COLOR] 
[*][COLOR=#000000][FONT=Arial]exFat to Fuse didn't work on the 1 TB USB drive[/FONT][/COLOR] 
[*][COLOR=#000000][FONT=Arial]And I want them compatible with Ubuntu, Windows, Nvidia Shield[/FONT][/COLOR] 
[/LIST]

[COLOR=#000000][FONT=Arial]Can you recommend something here? [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Thanks for your time![/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Ubuntu Bionic Beaver 18.04 since 2019![/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]To completely replace Win 7, 64 bit, someday![/FONT][/COLOR]

---

### Post by TheFu on 2019-04-14
I know nothing about a Shield device. I would start with the list of supported file systems on that device and work backwards.  Sometimes there isn't a good answer.

NTFS uses journals which are brutal on Flash storage. Even with load-leveling, expect it to wear out with lots of write cycles. I destroyed a 64G flash drive from a highly reputable vendor/maker in less than a year by recording video on it about 300 days a year. It was FAT32, but NTFS would have been much worse.

You can split video files into parts, BTW.

FUSE is a user-land file system interface. It is used by all non-kernel file systems.  That includes NTFS, vFAT and xFAT - plus probably 50 other file systems.

Er ... you should use a repo or PPA to get the exFAT FUSE tools installed on Ubuntu.  I avoid exFAT for anti-microsoft reasons, but if that works for you, 
```
sudo apt-get install exfat-utils exfat-fuse

``` is how access is available.  I know little about using any specific GUI to re-format storage, sorry. Well, I use gParted sometimes, but most of the time I'd use **mkfs -t ext4** to format a partition/LV into a specific file system.

[https://www.reddit.com/r/DataHoarder/comments/7wcgv0/filesystem_for_drives_connected_to_nvidia_shield/](https://www.reddit.com/r/DataHoarder/comments/7wcgv0/filesystem_for_drives_connected_to_nvidia_shield/) says only NTFS and exFAT are supported. Of those choices, exFAT is less abusive towards flash storage.  There's the answer, such as it is.

[https://en.wikipedia.org/wiki/Comparison_of_file_systems](https://en.wikipedia.org/wiki/Comparison_of_file_systems) might be worth skimming to understand just how many choices there are in the wider world.

---

### Post by billy3xs on 2019-04-15
Thank you Fu! Looks like it's exFat for meeee! 
I loaded exfat-utils exfat-fuse again, pretty cool, the terminal suggested deleting unused files.
:popcorn:

---


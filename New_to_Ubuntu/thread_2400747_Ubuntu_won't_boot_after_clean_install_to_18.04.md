---
title: "Ubuntu won't boot after clean install to 18.04"
date: 2018-09-09
forum: New to Ubuntu
---

### Post by trent65 on 2018-09-09
So, I think I may have messed up here. Here is the story from the beginning. I upgraded to 18.04 and was immediately saddled with a login loop issue. I couldn't log in at all, after I successfully entered in my credentials it would just loop right back to the login page. Someone suggested that it could be BIOS related. So, I backed up my home directory as is described in this thread: [https://ubuntuforums.org/showthread.php?t=35087](https://ubuntuforums.org/showthread.php?t=35087), then I updated my BIOS to the most recent version. Then I did a clean install of Ubuntu 18.04. Everything was hunky dory. I was able to log in and everything. Then it came time to recover the data that I had backed up. I ran
 [COLOR=#000000][FONT=&quot]tar xvpfz backup.tgz -C /
[/FONT][/COLOR]As was described in the same link. I did get an error at this point. Something like: exited with errors due to previous errors. Or something like that, I don't remember for sure. Even with that error, I was feeling pretty good. All of my data had been returned and it was looking great.

So I restarted. Now I get a menu for GNU GRUB version 2.02. The menu has the following options: Ubuntu, Advanced options for Ubuntu, Memory test (memtest86+) Memory test (memtest86+, serial console 115200). 

If I select "Ubuntu". I get error: no such device:a95047ed-ea39-43ff-b5b2-2ed86f3e496a (I'm pretty sure this is the name it assigned to my external drive while I was recovering after the successful install of Ubuntu)  and it redirects to a black screen for a while. Then I get.
```

Gave up waiting for root file system device. Common problems:
-Boot args (cat /proc/cmdline)
  - Check rootdelay= (did the system wait long enough?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! UUID=a95047ed-ea39-43ff-b5b2-2ed86f3e496a does not exist. Dropping to a shell!

BusyBox v1.27.2 (Ubuntu 1:1.27.2-2ubuntu3) built-in shell (ash)
Enter 'help for a list of built-in commands.

```

And then I am at a command prompt (intitramfs)

Where did I go wrong here? When I was restoring the backup, I seem to have somehow made it dependent on my external drive. But even if I plug it back in, I get the same errors. Any ideas?

Hardware, if relevant:
[COLOR=#1C1C1C][FONT=&quot]AMD Ryzen 5 1600 3.2 ghz processor[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&quot]Radeon RX 570 4GB Video Card[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&quot]ASRock AB350 Pro4 ATX Motherboard[/FONT][/COLOR]

---

### Post by DuckHook on 2018-09-09
According to your description, this is what you did:

[LIST=1]
[*]You made a full backup of your old install: everything from / on down
[*]You then replaced everything in your old problematic install with a new pristine install. This was why you could now log in.
[*]You then overwrote your new working install with your old backup, complete with whatever it was that had caused you your problems.
[/LIST]
I think you can see where this is going. There's no point in installing a pristine OS only to overwrite it with your old problematic one.

The instructions that you link to are for people who want to make a backup of their whole system when it is still working properly so that this *working* image can be used as a restore point after something bad happens. In your case, you created an image of a system that was no longer working. It's too late to do a full system backup at that point. What you may have wanted to do was to back up only your data and then only bring the data back into your new working install.

Here's what I recommend:

[LIST=1]
[*]If you are unused to the command line, don't use *tar*. Instead, fire up a LiveUSB and use the graphical file manager to copy all of your important data to another HDD/SSD.
[*]Install a new pristine OS.
[*]Then, copy *only the data* into the new OS.
[/LIST]
The typical Linux file system keeps all of your data under */home*. Unless you are a more experienced user that has changed the system's default settings or fiddled with its configuration files, then */home* the only directory that you would need to copy. However, double check to make sure that you have, in fact, copied everything and that it is readable. Your "backup" is only as good as your ability to restore it.

If you wish to see another way to make good backups, try the link in my sig: !!BACKUP FIRST!!

Let us know how it goes.

---

### Post by trent65 on 2018-09-09
Well, that certainly makes a lot of sense. Thank you for the thorough reply. I fully admit that I was playing it high and loose with the backup and I waited until I had a problem before I ever got around to backing it up. I'll be more diligent about it in the future. I'll come back here and post an update when I get to it.

---


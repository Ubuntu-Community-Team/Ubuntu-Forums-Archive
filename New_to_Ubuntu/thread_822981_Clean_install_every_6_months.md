---
title: "Clean install every 6 months?"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by Bimbambum on 2008-06-08
Hello,

I was wondering how easy can be a clean install twice a year. I'd like to ask you how do you do it, if you do so. 

I've seen that I can easily change the Home directory even from the GUI. If I change it to be on a different partition than where Ubuntu is, can it be enough at the time of an Ubuntu reinstall? I'm coming from Windows, of course, and I'm used to keeping my every personal data on a D: drive, even Firefox configuration files, for example, so that when I reinstall Windows I don't have to think for a second if there's something important on C:. And after the reinstall, I simply redirect installed programs to use the old config files stored on my D:. What's up with this procedure in Ubuntu? What do I need to keep on an isolated partition, how can I do it, etc.? I wanna know everything on this topic.

The only purpose is not to have any work with the system partition before a clean install.

Plus, with the mentioned method in Windows, the only problem was that every program had to be installed again each time I had a clean install. In Ubuntu, is there a way to skip this, too, and have a working new OS in minutes with the old stuff? Of course not including the installation time. :P

Thanks in advance.

---

### Post by Joeb454 on 2008-06-08
Easy - you don't even have to back-up your home directory if you don't mind reconfiguring a few things :)

If you're just going to be using Ubuntu, having a separate /home wouldn't be an issue :)

---

### Post by Bimbambum on 2008-06-08
Thanks. :) Can you add some details, please? How does a new installation work, what should I do, why don't I have to make backups, etc. :)

EDIT: BTW, is the Home directory the only directory where Ubuntu stores my personal data and config files? So if I have it separately, is everything solved?

---

### Post by Grishka on 2008-06-08
> **Bimbambum said:**
> Hello,

I was wondering how easy can be a clean install twice a year. I'd like to ask you how do you do it, if you do so. 

I've seen that I can easily change the Home directory even from the GUI. If I change it to be on a different partition than where Ubuntu is, can it be enough at the time of an Ubuntu reinstall? I'm coming from Windows, of course, and I'm used to keeping my every personal data on a D: drive, even Firefox configuration files, for example, so that when I reinstall Windows I don't have to think for a second if there's something important on C:. And after the reinstall, I simply redirect installed programs to use the old config files stored on my D:. What's up with this procedure in Ubuntu? What do I need to keep on an isolated partition, how can I do it, etc.? I wanna know everything on this topic.

The only purpose is not to have any work with the system partition before a clean install.

Plus, with the mentioned method in Windows, the only problem was that every program had to be installed again each time I had a clean install. In Ubuntu, is there a way to skip this, too, and have a working new OS in minutes with the old stuff? Of course not including the installation time. :P

Thanks in advance.

I do a periodical reinstall from time to time, probably more often than twice a year. the trick is to make a separate home partition, just like you mentioned. now to answer your questions: all your configuration files are kept on your home partition, so reinstalling will not erase your settings. I like to make a fresh account for myself, when I do a reinstall, but it's not necessary. my mum has kept her settings for many system reinstalls now, and she barely even notices when I reinstall. no redirecting of the configure paths should be necessary, but individual programs will have to be installed anew, as they are kept on the system partition.
oh yeah, the user accounts have to be created every time you do the reinstall, but their folders are kept.

---

### Post by sstusick on 2008-06-08
Your D: drive would have to be formatted as a Linux File system such as Ext3. 

All of your documents, application data and settings are stored in /home. 

When installing Ubuntu, make sure to make 2 separate partitions, 1 for / = the root of the system, and another for /home.

See here for more info: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Bimbambum on 2008-06-09
Thank you both. :)

---

### Post by SunnyRabbiera on 2008-06-09
Ubuntu's release cycle is annoying I agree though, but its better then some update systems out there.

---

### Post by DBrocks on 2008-06-09
Just give yourself a new partition for '/home'

---

### Post by The Cog on 2008-06-09
See this link.
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I do a fresh install every 6 months. Yes I have to reinstall all the apps. I really ought to maintain a script that goes somethng like:
**sudo apt-get install wireshark openvpn geany subversion meld mysql-query-browser mysql-admin etc. etc. **
Maybe I'll try to remember that next time.
Reinstalling keeps the accumulated rubbish to a minimum - things I try out etc.

---

### Post by AusIV4 on 2008-06-09
I used to re-install with each release. The upgrade to Hardy went smoothly enough that this was unnecessary though.

As others have suggested, I keep a separate /home/ partition, which let me keep my personal files and configuration in tact. Before wiping my root partition, I would follow [these instructions](http://ubuntuforums.org/showthread.php?t=261366) to back up my package list. After the install, I would follow the rest of the instructions to re-install all of the packages I'd had in my prior installation.

Unless you install much software that's not in the repositories, this will be a fairly seamless transition between installations.

---

### Post by kansasnoob on 2008-06-09
A method I've come to prefer for trying any new distro, or even if I want to try something new to me which means I just might break things, is to free up about 10 GB on my hard drive and install whatever distro I want to try (or play with). 

When I'm done playing I can delete that partition if I don't want it, or I can shrink or delete any other old partition if I want more room for my new OS. Worst case scenario is having to change a few things in GRUB, since the last distro installed always becomes the default boot, but that's pretty simple (and real easy if you create a GRUB backup with a name you can remember).

That's definitely what I'll do when Intrepid comes out. Then I'll still have my working Hardy to use while I fiddle and diddle with Intrepid as time allows. No frustrations that way. I doubt that I'll ever use the upgrade path again .............. it seems to be about like tossing a coin, half the time it works fine, the other half not so good.

---

### Post by ralyon on 2008-06-09
I have a media server which I reinstall once or twice a year as well as additional systems. I have a separate /home partition as well as a separate raid for my media files (about 1.4TB). I usually do a backup just before an upgrade just in case using this command:
```
sudo tar cvpzf /your_backup_loc --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/media --exclude=/sys --exclude=/dev --exclude=/home --exclude=/other_parts_not_2b_reformatted
```

I also do an additional backup of my databases and 3 files: /etc/fstab, /etc/X11/xorg.conf, /etc/samba/smb.conf as it is easier to pull data from these without having to open the backup. The backup file only ends up being about 2GB so its not a problem to keep around all though I have yet to use one.

This has been working well for me, hope the info helps you as well.

ralyon

---

### Post by jrharvey on 2008-06-09
I use to backup and restore my home drive every time but now i just keep a separate partition with all my personal files. That way when i reinstall ubuntu, I do not need to spend hours putting my backup in my home directory. I simply open that partition. Also it really helps when using a dual boot with windows. I dont have to fish through alot of other files to access my music and such.

---

### Post by Bimbambum on 2008-06-10
I'd like to thank everyone for the replies. I've made a separate partition for /home. Just a last question: If I get it right, installing a fresh Ubuntu "on the top" of the previous one (which means without formatting or something) is all right and one should do so. Do I get it right?

---

### Post by wolfen69 on 2008-06-10
i personally never bother having a seperate /home partition. i feel that doing a clean install, i should have a clean home also. i just keep all valuable files on a seperate partition/hard drive. there's nothing like that new OS smell!

---

### Post by wolfen69 on 2008-06-10
> **Bimbambum said:**
> I'd like to thank everyone for the replies. I've made a separate partition for /home. Just a last question: If I get it right, installing a fresh Ubuntu "on the top" of the previous one (which means without formatting or something) is all right and one should do so. Do I get it right?

you cant do a fresh install "on top of" your present install. that would be called upgrading. a fresh install wipes out the previous install completely. i dont recommend upgrading. fresh is always best.

---

### Post by cariboo on 2008-06-10
There is really no need to do a clean install every six months. This is a Windows problem. In linux there is no registry that gets loaded with cruft after a few months of usage, Most of the  linux application configuration files are located in /etc. Got a problem with an application just uninstall it using synaptic or if you installed from source, make sure you keep the source directory and uninstall it from there.

The only reason I do a clean install is if I have been beta testing a distribution and when the final release come out then it's time for a clean install. Remember Linux is not Windows, most of what you did as maintenance in windows is not valid in linux.

Jim

---

### Post by tom56 on 2008-06-10
A separate home partition isn't needed anymore. The installer detects the /home folder and offers to keep it whilst deleting everything else.

---

### Post by ralyon on 2008-06-11
> **Bimbambum said:**
> I'd like to thank everyone for the replies. I've made a separate partition for /home. Just a last question: If I get it right, installing a fresh Ubuntu "on the top" of the previous one (which means without formatting or something) is all right and one should do so. Do I get it right?

During the install when it asks to set up the partitions, go to manual. You will probably see the partitions set to mount as /mnt/sda1 and /mnt/sda2. Select the partition for the root, set the mount point to / and select to format. Select the home partition, set the mount point to /home and make sure it is not set to format.

I also agree with cariboo907 that a fresh install usually isn't necessary and an upgrade usually does well, unless your going between different versions like Mint or UE to Ubuntu or you have a bunch of programs you want to get rid of.

> **tom56 said:**
> A separate home partition isn't needed anymore. The installer detects the /home folder and offers to keep it whilst deleting everything else.

I've not seen this before. When did they add that option? I'll have to check it out next time I get a chance.

ralyon

---

### Post by tom56 on 2008-06-11
> **ralyon said:**
> I've not seen this before. When did they add that option? I'll have to check it out next time I get a chance.

[http://brainstorm.ubuntu.com/item/138/](http://brainstorm.ubuntu.com/item/138/)
[https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2008-May/004210.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2008-May/004210.html)

though I admit I've not tried it myself yet

---

### Post by decoherence on 2008-06-11
I also suggest backing up the /etc folder if you've done anything 'out of the ordinary' with the system.

---


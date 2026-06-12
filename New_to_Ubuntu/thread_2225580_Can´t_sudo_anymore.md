---
title: "Can´t sudo anymore"
date: 2014-05-22
forum: New to Ubuntu
---

### Post by jwn-2 on 2014-05-22
I am using Ubuntu 13.10.

For some mysterious reason I suddenly cannot sudo anymore. I just get the following message: 

" sudo: effective uid is not 0, is sudo installed setuid root?". 

A few days ago I was still able to sudo and I have no clue what I did wrong in the meantime. Please help.

---

### Post by slickymaster on 2014-05-22
Your _sudo_ binary doesn't have the _setuid_ flag, as it correctly guessed. Try the following```
sudo -i # in order to get a root prompt
```Afterwards run```
chmod u+s /usr/bin/sudo
```

---

### Post by Impavidus on 2014-05-22
I'm not sure you can fix sudo using sudo. You may need the recovery console and run the chmod command there. [http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

It would be good to know why the setuid bit was lost. If you somehow messed with permissions, those of other files in /usr/bin may be wrong too.

---

### Post by slickymaster on 2014-05-22
> **Impavidus said:**
> I'm not sure you can fix sudo using sudo. You may need the recovery console and run the chmod command there. [http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

It would be good to know why the setuid bit was lost. If you somehow messed with permissions, those of other files in /usr/bin may be wrong too.

You're absolutely right Impavidus. That's just goes to show you that I should always have a fresh mug of coffee before posting in the morning, to prevent this kind of dumbness.

@jwn-2
Besides Impavidus advise, there's also another away of doing it (and I'm just posting it for future reference).

With a Ubuntu LiveCD it's possible to reset the permissions. What you need to do is boot onto the CD and open a terminal.

Within the opened terminal you need to find what drive your partition is on, you can do that using ```
sudo fdisk -lu
```The output will show something similar to the following:```
Disk /dev/sda: 107.4 GB, 107374182400 bytes
255 heads, 63 sectors/track, 13054 cylinders, total 209715200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ac416

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   108152438    54075195+  83  Linux
/dev/sda2       108152832   200312831    46080000   83  Linux
/dev/sda3       200312832   209713151     4700160   82  Linux swap / Solaris
```
My root partition here is sda1, if you've only got 1 drive on it yours is something similar. But if you're unsure, you're looking for the device which has the System column set to "Linux".

Once you know the partition that you're Ubuntu is installed into you, you need to mount it, replace **/dev/sda1** with your device in the following:```

sudo mkdir /mnt/recover
sudo mount /dev/sda1 /mnt/recover
sudo chmod -R root:root /mnt/recover/usr
sudo chmod -R a+rX /mnt/recover/usr
sudo umount /mnt/recover
```

Again, I'm posting this option as future reference only. Impavidus option is perfectly valid.

---

### Post by jwn-2 on 2014-05-22
I have now tried both Slickymaster's and Impavidus' advice, and now I have managed to render Ubuntu completely unusable, to such an extent that I had to boot back to Windows to be able to post this. I do like Ubuntu. I can do a lot with it that I cannot do with Windows. But it does seem to be a dangerous OS if you don't have a proper knowledge of how it works.
 
Okay. I have first tried Impavidus' advice. Before I changed anything I also noticed that the ownership of /usr/bin has somehow changed to me instead of root (don't ask me how that happened, I don't know). I have managed to change that back to root also, but sudo still does not work.
 
Then I tried Slickymaster's advice, and now I have managed to completely bugger everything up. When I rebooted from hard drive I had several serious problems. Here is a list of what I was able to notice:
 
- The following error message is displayed:
 
   Sorry, Ubuntu 13.10 has experienced an internal error
   ExecutablePath
   /usr/lib/gnome-setting-daemon/gnome-setting-daemon
 
- Ubuntu is as slow as hell. So much that it is almost impossible to do anything.
 
- Menu fonts seen to have changed.
 
- I am unable to connect to the internet.
 
- I can't shut down properly. I have to use the hard switch to terminate Ubuntu.
 
Please guys, help. What would be the safest way to get Ubuntu working again, without doing anymore damage, and without loosing any data. My install disk does not seem to allow me to re-install ubuntu without loosing my data.

---

### Post by Impavidus on 2014-05-23
First of all, boot from your live disk to run a live session. Backup all your documents to an external drive and disconnect the drive. They will be safe there.

It appears that your permissions have been completely mixed up. It's either a tedious job to find out which directories and files are broken and then fix them, all from the live disk (maybe the recovery console works too), or a clean install. You may consider installing 14.04. It will save you from upgrading or reinstalling in July, when support for 13.10 ends. Your choice.

---

### Post by slickymaster on 2014-05-23
> **Impavidus said:**
> First of all, boot from your live disk to run a live session. Backup all your documents to an external drive and disconnect the drive. They will be save there.

It appears that your permissions have been completely mixed up. It's either a tedious job to find out which directories and files are broken and then fix them, all from the live disk (maybe the recovery console works too), or a clean install. You may consider installing 14.04. It will safe you from upgrading or reinstalling in July, when support for 13.10 ends. Your choice.

A big +1 on what Impavidus said.

After **_backing up your data_**, one other option you might consider is to install Ubuntu 14.04 without losing the content of your /home folder partition.


[LIST=1]
[*]Boot from from a LiveUSB
[*]Follow the prompts until the "Installation type"
[*]Choose the "Something else" option
[*]When the partitioning window shows up, be sure to select the **/** partition (/dev/sd?) to format in ext4, make bootable and select the mount point as [B]/
[/B]
[*]Select **/home**, without formatting it (_**DO NOT tick the format box**_), select the mount point as **/home**
[*]Select **/swap **select the mount point as [B]/swap
[/B]
[*]Enter your names and password (_**they have to be the [B]s**ame you previously had[/B]_), choose to update during install etc
[*]Reboot, install updates, install any apps you regularly use that are missing.
[/LIST]

---

### Post by jwn-2 on 2014-05-23
Thanks Impavidus and Slickymaster. I have also thought of upgrading to 14.04 even before you suggested it, and have now decided to do that. I have downloaded it and burned it to a DVD and tried to install. However, now I have two new problems. I do have a suspicion that problem 2 is caused by problem 1, but I am not sure. It may even be that problem 1 is also the reason I could not re-install 13.10.
 
Problem 1: At the step where there are three recommendations for installing, it claims that I have no internet connection, although I do have internet connection and can even confirm it by using it from firefox when trying Ubuntu 14.04. There is just no way that I can convince the install software that I do have a valid connection.
 
Problem 2: When I get to the step where I have to choose what to do, Upgrade from 13.10 to 14.04 is there, but not available to choose. All the available options involve deleting everything and installing 14.04 fresh. Is this caused by problem 1, or are the two problems independent of each other?
 
Unfortunately I cannot upgrade directly from 13.10 because I can’t get booted into 13.10 any more.
 
Is there no way I can make the install software allow me to just upgrade, or do I have to go through all the steps Slickymaster suggested in his last post? It does look somewhat complicated and I am worried that I just might do even more damage. I have in the meantime backed up my home directory, but I would feel much better if it was possible to upgrade without loosing anything.

---

### Post by LastDino on 2014-05-23
Out of curiosity, how are you connecting to internet? (Wifi, derect-wire or something else?)

---

### Post by jwn-2 on 2014-05-23
I have a cellphone WiFi connection. I have tried direct connection as well as WiFi connection. There is also a third option (I don't know what it is called) where I can connect to it as a cellphone. I have tried all options, but the result remains the same.

---

### Post by slickymaster on 2014-05-23
> **jwn-2 said:**
> Thanks Impavidus and Slickymaster. I have also thought of upgrading to 14.04 even before you suggested it, and have now decided to do that. I have downloaded it and burned it to a DVD and tried to install. However, now I have two new problems. I do have a suspicion that problem 2 is caused by problem 1, but I am not sure. It may even be that problem 1 is also the reason I could not re-install 13.10.
 
Problem 1: At the step where there are three recommendations for installing, it claims that I have no internet connection, although I do have internet connection and can even confirm it by using it from firefox when trying Ubuntu 14.04. There is just no way that I can convince the install software that I do have a valid connection.
 
Problem 2: When I get to the step where I have to choose what to do, Upgrade from 13.10 to 14.04 is there, but not available to choose. All the available options involve deleting everything and installing 14.04 fresh. Is this caused by problem 1, or are the two problems independent of each other?
 
Unfortunately I cannot upgrade directly from 13.10 because I can’t get booted into 13.10 any more.
 
Is there no way I can make the install software allow me to just upgrade, or do I have to go through all the steps Slickymaster suggested in his last post? It does look somewhat complicated and I am worried that I just might do even more damage. I have in the meantime backed up my home directory, but I would feel much better if it was possible to upgrade without loosing anything.

The ISO file you're using may be corrupt. I would check that files integrity with [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM").

---


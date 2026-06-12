---
title: "Initial setup advice wanted - newbie with a lot of kit to set up !"
date: 2021-03-19
forum: New to Ubuntu
---

### Post by netrix-g on 2021-03-19
Hi all,
To first give a bit of info - I have a background in IT so am comfortable using command line, I did "dabble" with an HPE Microserver a few years back but alas succumbed to a Windows server install as time was tight !
I now have access to the following kit to "play with" and would like advice, if possible, on how to best set it up from the get-go - I have time on my hands now so am keen to learn a new skill


[LIST]
[*]HPE Gen9 server running 2 Intel Xeon E5-2667 (3.20Ghz)
[*]96GB Ram
[*]8 drive bays in the server but have 6x300GB SAS and 8x4TB SAS drives
[/LIST]

Probably a bit over the top for a home setup but hey, it didn't cost me anything !

Useage:
Initially as home NAS running Plex - so storing backups of laptops etc, streaming music/movies around the house, storing photos.
I'd like to play with a VM setup and maybe have a Windows VM set up - not sure if this can be added at a later date without disturbing the setup too much ?
Eventually I would like to have 
[LIST]
[*]a web server installed (nothing fancy, just to dabble)
[*]store/manage an IP CCTV system
[*]maybe an ftp server to share "stuff" - if it's not too risky (have read some bad reviews of having ftp enabled)
[/LIST]

My initial thoughts were to set up Ubuntu server on one of the 300GB SAS drives, but for a modicum of resilience plug two drives in and setup as Raid 1.
Then, with the remaining 6 drive bays, have 6x4TB drives setup as Raid 5. [around 20GBs storage ?]This will leave me some spare drives for drive failures (all drives are used so expect to have failures along the way)

Does this approach seem ok or should I look to install an SSD for the OS ? On the Micro server I think I'm correct saying that the OS was installed on a USB pen-drive inserted in a motherboard usb slot.

The sort of questions running around my mind are what if I need to reinstall the OS - will settings like firewall setup, SSH settings, user accounts be affected ? I assume yes to those so is there a way to back those up on one of the data partitions in the Raid 5 array (assuming I go down that route)

I already have a couple of documents "on the go" for command line help, I do not have the 4TB drives yet as they are being wiped of their original data. I have already setup the 2x300GB drives as Raid 1 and installed Ubuntu server 20.04 LTS, but I do not want to go through too much more setup if your advice would suggest something else.

Thanks in advance for any assistance !

Regards

Netrix

---

### Post by ActionParsnip on 2021-03-19
The default SSH settings are fairly sane. Iptables is installed by default, as well as ufw. You can use either (choose one, don't configure both). The default rules allow all traffic. The openssh-server will also give you an SFTP server but you can configure NFS/Samba for file sharing if you need that functionality. Loads of guides online including YouTube on headless Plex servers. You can use apache/nginx and so on if you want a web sever but be sure to use different ports to your Plex install as it also has a web interface by default.

All the configurations of these services are stored in text files, mainly in /etc so just add that folder to the scope of your backups. If you reinstall, you can simply restore the config files and restart the service and you are back in business. Very simple.

The OS being on the slower drives will be fine. The SSD will just improve boot times and I'm guessing you won't be rebooting this thing much.

---

### Post by CatKiller on 2021-03-19
> **netrix-g said:**
> I'd like to play with a VM setup and maybe have a Windows VM set up - not sure if this can be added at a later date without disturbing the setup too much ? 

Create them, delete them, move them to another host, no worries. They're just files when they aren't running. 

>  The sort of questions running around my mind are what if I need to reinstall the OS - will settings like firewall setup, SSH settings, user accounts be affected ?

User settings and data are just stored in the user's Home directory. You can back it up and restore it easily. If you make /home a separate partition to / then if you reinstall the OS you can tell the installer to just use your existing /home partition as /home and carry on as before. By adding the users in the same order (since ownership is determined by user number) it will be completely seamless.

System settings, to the extent that they differ from defaults (in which case there's nothing more needs to be done) are just text files. Back them up like any other file. If you copy them somewhere else, make a note somewhere of where they came from. Job done.

---

### Post by netrix-g on 2021-03-19
Thanks for the replies, I'm struggling to get SSH working at the moment but I'll start another thread for that.

Regards

Netrix

---


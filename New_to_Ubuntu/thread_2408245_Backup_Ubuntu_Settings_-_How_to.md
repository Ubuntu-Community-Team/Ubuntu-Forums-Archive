---
title: "Backup Ubuntu Settings - How to ?"
date: 2018-12-16
forum: New to Ubuntu
---

### Post by spazz2 on 2018-12-16
Hi all ! 

I need to do a fresh install of Ubuntu, and I am wondering if there is a way to backup my settings and system preferences?
That is : 
All the settings I have edited in the settings manager, such as : 
-- All the keyboard shortcuts I have created for window manager.
-- The general appearance of my system (System fonts , font sizes , desktop themes and icon style)

All that kind of stuff. 

Sorry if this question has already asked. I'm sure it must have been asked numerous times. 
However : I've just trawled through 10 pages of 255 results by typing "backup settings" in this forums search, and couldn't find an answer ! So I tried.

I read that backing up the "home" folder will also backup the settings, but if so : where abouts in "home" are the files for the settings and configs in question ? I cannot find it. Are the files hidden perhaps ? 

I don't want to back up the whole system -- as I've corrupted it.

I do not need to backup any other data.
============================
On a separate note , regarding these forums : 
Would anybody know how to display all search results within these forums on a single page ?
Search results here only display about 25 results per page.

I would much rather just read through one long page of results, rather than having to continually click to "next page".
I can't find a forum preference or search preference for that.

Thanks very much for any and all assistance !!

---

### Post by TheFu on 2018-12-16
**aptik** is probably what you want.

Settings are in your HOME for that single userid. Each different userid has settings in their respective HOME directories.
Each program determines where their settings might be stored and most can be overridden by individual settings. So, where any setting might be is controlled by you, your DE, your WM, and which OS you are running.  Generally, many program settings are placed into ~/.config/  but not all of them are.

In all Unix systems, files and directories that begin with a . (period), aren't displayed in a normal ls listing.  Not showing them is a convenience and extremely well understood. 

As for whether your system is corrupted or not - if you use root or sudo too much, that is likely.  But if you don't, then the issue is most likely in these settings you are trying to back up.  Instead, create a new userid and login using that. Everything will be new again and any bad settings from the other account won't impact this other userid at all.

If you are really new to Linux there are a few overview articles which explain some of the main ideas clearly.  [https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html) is one of the best.

---

### Post by oldrocker99 on 2018-12-16
A compete backup of your /home partition will keep all of your settings.

If you ever reinstall, make a separate /home partition. Then, when you ever reinstall, mount that partition as /home, and no backup of /home needs to be restored.

Here's how to create a separate /home partition in an already installed Ubuntu system:
[https://www.howtogeek.com/116742/how-to-create-a-separate-home-partition-after-installing-ubuntu/](https://www.howtogeek.com/116742/how-to-create-a-separate-home-partition-after-installing-ubuntu/).

Of course, still backing up your /home folder is an ***absolute MUST***.

---

### Post by spazz2 on 2018-12-20
TheFu :
Thanks ! I will try aptik.
I definitely have been doing a few sudos in terminal (I tried to install unity desktop over xfce : Didn't realise it would be too much of a mess to undo what I did.
Now I have boot errors -- system only intermittently boots up from power off : about half the time gets stuck on a terminal screen after boot, and won't log in, with other things affected).
I will definitely try creating and logging in with another user id though.
Thanks for the info on config files.
I probably should have tried to educate myself with google a bit, but it helps to have somebody quickly spell it out for me.
Thanks for the links to the article. I am gathering linux-reading materials as I go, and all recommendations are appreciated.

---

### Post by spazz2 on 2018-12-21
Thanks oldrocker ! That is some sound advice !
It sounds as though settings and config files are stored in various random and possibly hidden locations within home.
That's a bit of a bummer -- since backing up and restoring the entire home folder may become unfeasible if I am hoping to transfer my system settings and preferences across multiple machines.

Transferring entire home folders which may contain "huge" -- or consistently-expanding and accumulating -- amounts of data for the sake of wanting to preserve and copy a few tiny measly config files (and some time) across machines seems like an inefficient way to achieve such a task, and I am hoping there is a way to xfer just Desktop / GUI / system configs.

I'm wondering if config files tend to be stored in a particular location / locations somewhere :
Since the home folder itself may contain a LOT of other extraneous data (eg. media) which I would rather backup separately to system configs (which are presumably only small files) -- 

Ideally : It would be good to apply my configs and settings and preferences to other computers running ubuntu (as I have gradually accumulated a few computers for free (disposals) -- which I am envisioning / would like to try to network together, all as ubuntu machines -- which will NOT contain same data / media -- but which I would like to have the same desktop / system settings).

---

### Post by spazz2 on 2018-12-21
TheFu !
I am just looking into aptik now.
I am using the terminal install directions on the bottom of this page

[http://ubuntuhandbook.org/index.php/2014/01/aptik-simple-tool-backup-packages-ubuntu/](http://ubuntuhandbook.org/index.php/2014/01/aptik-simple-tool-backup-packages-ubuntu/)

Which are 
sudo add-apt-repository -y ppa:teejee2008/ppa
sudo apt-get update
sudo apt-get install aptikDoes this seem right to you?

I heard from a friend to be careful with PPAs.
I need to research linux vulnerabilities, but I think he said PPAs can be a linux vulnerability.

I'm going to do it anyway, because I'm going to reinstall the system, which is currently an experimental / non-commital system (before I learn more about what I'm doing).

I'm just curious if this poses a security risk to my system ?

---

### Post by spazz2 on 2018-12-21
Dear all : 
I have found this guide for backing up XFCE 4 desktop environment configs and settings (roughly my XFCE version).

[https://www.addictivetips.com/ubuntu-linux-tips/back-up-the-xfce4-desktop-settings-linux/](https://www.addictivetips.com/ubuntu-linux-tips/back-up-the-xfce4-desktop-settings-linux/)

(Got to this by net-searching "backup ubuntu desktop preferences"   -- sometimes just need the right search)

I have run the "full backup" command in terminal to produce the backup.

tar -czvf full-backup.tar.gz ~/.config

The guide warns that this will take longer and be a bigger backup file, than if you were to be careful and selective about which configs you backup.

It took about 5 seconds, and the file is 90.5kB

(:

I may take a bet on this and see how it goes on a system reinstall (?)

---

### Post by spazz2 on 2018-12-21
Hey Oldrocker.
As mentioned in my previous comment : 
Copying home folder to a backup for the sake of preserving configs :
As I mentioned : My problem or concern with that being that it would backup all other extraneous / extra data (media etc.) when I just want desktop configs and other configs .

I've now backed up my home folder to an EXT HD.
There is a bit of weirdness :
My home folder in the file manager states that it is only 4.1kB (which I know is not correct).
When copying, it said it was backing up 15gb (which it did, with an error),
and the resultant copied file on the ext hd states in the file manager that it is 4.1kB 
(but is actually 15GB when I look in the folder properties !!!) 
Weird, right ? 
Or normal?

---

### Post by TheFu on 2018-12-21
Don't use tar for backups.  That tool was made to backup 50MB of data, not 500MB or larger.  Use tar like you would use a ZIP file.  Small, specific, stuff.

Also, don't keep media files in your HOME.  You can use symbolic links to the other storage to reach those files easily, but large files that never change make backups a hassle.  Your HOME should be settings and documents and small data, not media.

PPAs are risk, but so are the Canonical repos.  As the admin, you have to learn which security risks are huge and which are tiny.  Using Canonical repos is a tiny risk.  If you found instructions from a reputable site which say to use a PPA, then I'd rate the risk as only slightly higher using that PPA.  There are bad PPAs created by disreputable people. Every PPA use requires vigilance and doing our homework. There aren't any absolutes, but as you use Ubuntu more and more, you'll see the same reputable sources of information over and over. These will reference reputable PPAs.  

Reputation is everything and really all we have.

You and I trust Linus implicitly just by running Linux systems.  Why is that?  Reputation.  He trusts 5-10 people who feed Linux kernel updates to him.  Each of them trust 5-10 people who feed them kernel changes.  The trust isn't absolute.  Screw up and everyone up the chain will see who recommended a change.  Hiding bad code in the kernel is hard, but attempts are made.

The same methods apply to every package you and I can install from the repos and PPAs.  I try to stick with Canonical's repos whenever possible based purely on their reputation to patch any security issue, but not alter functionality for most packages.  I don't need/want the newest code. Stability is more important than "new" to me, almost always.  But there are exceptions.  Sometimes only the PPA has a fix that I need or features that I must have for my business.  I avoid random PPAs and want to only use the PPA created and maintained by the official project team.  I think that reduces the risks.

BTW, settings are placed randomly, but there isn't 1 MASTER CONTROLLER of settings either.  Gnome has a method they like to follow.  Same for KDE.  But there are popular programs which don't follow either of those project guidelines - like firefox or thunderbird or Chromium.  As part of their security, those programs introduce a random directory name to make outside programs trying to compromise the browser settings have just a little bit more difficult time.

There's always a reason for why things are done the way they are. It might be a bad reason in our estimation, but the person or team that decided on it certainly gave it _some_ thought.  As much as I dislike netplan or resolvconf or systemd, I can't deny that those teams were trying to solve a problem. It just wasn't any problem that I had ever seen.

Be careful following random google answers.  As someone new, you can't tell whether they started learning Linux 1 day before you did or not.  Often the people who create "how-to" guides are far from experts and don't handle any of the unknowns each system has.  There are almost always exceptions to every how-to guide.

I suggested aptik, not because I use it.  It doesn't do what I need in a backup tool.  I suggested it because you seemed to need a point-n-click tool with checkboxes to selectively backup things.  I use LVM snapshots paired with rdiff-backup to "pull" backups from the different systems here.  I've written extensively about it in these forums.  I've seen some other long-time forum volunteers post links to their backup how-to for using LVM + rdiff-backup. I don't remember exactly which poster did that, sorry, but I did see a link in a new post in the last 7 days.

And don't use tar. ;)

---

### Post by oldfred on 2018-12-21
This is why we often suggest separating / from data and for newer users use /home or once a bit more advanced use data partition(s). With your own data partition you have to manually mount (in fstab) and set your own permissions & ownership. With /home that is automatic, so easier for a newer user.
I do not use LVM, and mount my data in /mnt/data. TheFu prefers mounting off / directly, but I started years ago and now is a bit more work to change.

```
fred@bionic-z97:~$ sudo du -hx --max-depth=1 / 2> /dev/null
[sudo] password for fred: 
14M    /etc
847M    /lib
4.0K    /cdrom
4.0K    /lib64
12M    /sbin
12K    /snap
[COLOR=#ff0000]537M    /home[/COLOR]
176K    /mnt
4.0K    /srv
5.0G    /usr
176M    /boot
4.0K    /opt
13M    /bin
16K    /lost+found
2.1G    /var
1.5M    /root
8.0K    /media
[COLOR=#ff0000]8.7G    /[/COLOR]

```

With the normal data folders not in /, a /home is tiny.
I also move Firefox & Thunderbird profiles which are also larger to my data partition.
```
2.4G    thunderbird
1.1G    firefox

```

---

### Post by spazz2 on 2019-01-04
[FONT=arial]TheFu : 
Thanks again for your extremely generous time and information.
I really appreciate the ideas and sound advice on how best to organize the system --
and extra clues to better backups.
I wonder if you write articles for any Linux websites ? Great info.
There is a bunch of articles on Hackaday called "Fu Linux" : is that you ?


The overview you gave of the Linux system, securities / vulnerabilities, and the way the community works in a general - overall sense, and more about the philosophy and structure of the whole thing was really good..... and about maintaining stability. Life is too short to constantly reinstall O/S's.
Helped me understand a lot (or at least gave me info to work with).
[COLOR=#D9D4CC]
[/COLOR][/FONT]
PS.
I put a separate home partition on my new install :
(maybe bigger than necessary 250GB / 1TB drive )
However, I don't seem to be able to move media off the home part. into any folder within the main / root partition 750gB. 
I think I will need to watch Joe Collins videos again about folder structures and permissions.
Should I perhaps have had 3 partitions for root , home , and media + applications ?

---

### Post by oldfred on 2019-01-04
I think most of us keep / smaller (I use 25 or 30GB) and have data in other partitions.
If you run df -H or du commands I posted above, you can see how much you have used.

Some do like to keep media separate, but if you start creating too many partitions then you may fill one, but have lots of space available in another.

---

### Post by TheFu on 2019-01-04
> **spazz2 said:**
> [FONT=arial]TheFu : 
Thanks again for your extremely generous time and information.
I really appreciate the ideas and sound advice on how best to organize the system --
and extra clues to better backups.
Clear questions get clear answers and usually I'll add some experience-based information too. Glad it is helpful, but I'm sure that is the hope for 99.999% of the replies here.

> **spazz2 said:**
> [FONT=arial]
I wonder if you write articles for any Linux websites ? Great info.
There is a bunch of articles on Hackaday called "Fu Linux" : is that you ?
That isn't me on Hackaday. I don't use TheFu anywhere else but here.  Anywhere else that I post gets a different alias.

I've written for Lifehacker long ago and have a blog.jdpfu.com .  Haven't written much the last few years. Pretty much said all I wanted to say in those places. My blog tends to be the "why", not the "what to type".  Also, every article there has a date, so how old it is can easily be known.  For example, I wrote lots about tuning for virtual machines for a few years.  Why the exact details have changed, the over all ideas have not.  If you need to be told to check the 5th box down, my articles won't help you.  But if you can understand that using the latest Intel chipset supported by you hypervisor is best for performance and can find that setting, great!

> **spazz2 said:**
> [FONT=arial]
The overview you gave of the Linux system, securities / vulnerabilities, and the way the community works in a general - overall sense, and more about the philosophy and structure of the whole thing was really good..... and about maintaining stability. Life is too short to constantly reinstall O/S's.
Helped me understand a lot (or at least gave me info to work with).
Learning Linux: [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux)

> **spazz2 said:**
> [FONT=arial]
PS.
I put a separate home partition on my new install :
(maybe bigger than necessary 250GB / 1TB drive )
However, I don't seem to be able to move media off the home part. into any folder within the main / root partition 750gB. 
I think I will need to watch Joe Collins videos again about folder structures and permissions.
Should I perhaps have had 3 partitions for root , home , and media + applications ?

Sometimes I split /home off into a dedicated LV/partition, but usually I don't bother.  Most of my systems are servers, not desktops, so /home might have 20 scripts and no data at all.  It just isn't worth splitting off.  For a desktop, I'd do something like this:
/ 25GB - OS + installed apps + themes, if you must.
/home/ - maybe 25GB - more if I'm a java programmer, less for everyone else.
/D/ - whatever remains for data.
If you run services like mariaDB, nginx, or virtual machines, those files are generally placed into /var/lib/ or /var/www/ so mounting extra storage directly to those placed might be desired.

For example, I have a VM host called hadar.  
```
$ df -h /var
Filesystem                       Size  Used Avail Use% Mounted on
/dev/mapper/vg--hadar-lv--hadar  314G   89G  209G  30% /var
```
 /var/ has a few virtual machines under it and needs more storage.  

It was cool to pull a HDD from a 2009 box and just drop it into the new system and only have a few things to fix for all to work.  Only unexpected change was changing the hypervisor specified CPU from Intel to AMD.  The other things like the NIC device name and GPU were expected. I have to do something about the very old GPU (GeForce 7200 GS), but it is working at 1024x768p just fine with the F/LOSS drivers.  Nvidia hasn't made a compatible driver for the 4.15.x kernel.  I think an nvidia 1030 ($70) will fix that later today.  Not interested in DisplayPort. My KVM switch is VGA and the 2nd monitor is HDMI.  Need to research connections a little more.  Minor inconvenience. Also need to tune the DDR4 RAM some, since I'm not seeing anywhere near the label speeds.

---

### Post by spazz2 on 2019-01-04
oldfred :
Thanks ! I think I'm spotting a mistake I have made by ONLY making a root and home partition ): One partition too few !
Yes, I don't like having a ton of partitions. Just what is necessary to optimise my system. Still, I'm hoping I don't have to do a full reinstall to add a media partition off root ! Blunders....

---

### Post by spazz2 on 2019-01-04
TheFu :
Thanks ! I checked your blog. Looks like a great resource with a lot I could use ! 
Has reminded me to put that William Schotts book on my phone and dip into it.


I think I can understand the suggestion that selecting the latest intel chipset supported by a hypervisor is best for performance, and now that you mention it, it is a setting I should find , if it is not automatically detected by the hypervisor (virtualbox in my case)  (:


Based on what you've said about partition layout  :
I think I have made a big mistake in my new system reinstall :
I have only made a root and home .
No separate media partition.
...I don't seem to be able to add folders and files to root within GUI (which is probably a bad idea to do anyway, come to think of it).
This is probably a big blunder then, isn't it ?


I may be getting ahead of myself , but if this is the case :
Am I going to need to do a full reinstall to have a separate media partition ? 
Or is there a way I could perhaps boot Ubuntu installer off USB and make a partition off the large 750gB root partition I have made?


Probably not I guess : Since that would wipe root 
(I guess I could back-up root, or make a full system image somewhow...)
Otherwise, if I need to reinstall all 
==============================
Good tips also on adjustments to make to VM Hosts when transferring an old HD to a new box !
I work as a junior / dumb grunt in a broadcast facility, and the only KVM connections I have ever seen are all VGA with PS/2 connectors (maybe I have seen USB, but rare) , even on the most modern hardware, which I find a bit odd, but anyway.
==============================
Sorry if too much info :
I'll tell you a little about my system requirements.
I have come across quite a few desktops and laptops recently found in the bins at work and on the street.
Since computers have become so good in the past 10 years, but people don't see them as having value, I have decided to see "what I can do" with these old beasts, for various reasons.


My initial plan for this first desktop I am running Ubuntu studio on was to simply use it as a server for my personal Apple Macs.
(Still trying to learn how to use SFTP to move files back and forth : SMB over Network cable / through router just doesn't seem reliable for large amounts, or very good at all).


The initial idea was just so I could stick all my music and movies and other large data on the Ubuntu machine, and free up my Mac for music production and research for my college and personal research / interests (since I have "junked it up" with media).


(I am a junior electronics technician (hardware). I have a strong interest in music as my hobby, and am afflicted with an artsy-fartsy streak.
Have done a TINY bit of very basic coding (college exercises) in assembly, C# , Java.


Having explored Ubuntu Studio a bit, I see that it is ALSO an amazing creative utility, which I like in many ways as much as Macs for different reasons --
and so now I am interested in having this desktop as a split-function media server and music production machine. 
"Creative" applications take up quite a large amount of space (especially since I install a ton of them!!) : 
And I assume these generally install themselves in home and root -- so perhaps my large home folder size was not an awful idea?
(again, I'm not sure exactly where applications tend to install themselves : I would assume mainly in /bin , therefore making my requirement for a root folder perhaps larger than for yourself and OldFred and other sensible stream-lined system users).


-- Still, perhaps best for me just to use Home for symbolic links to media folders on another partition and to /bin or wherever apps are stored ?
==============================
Sorry, that's an awful lot of writing.
Good luck with your new / old frankenstein system and graphics drivers (:

---

### Post by oldfred on 2019-01-04
If it just is / that is too large, you should be able to shrink it with gparted.
Then create a new data partition or media or whatever you want to call it. I now prefer to mount using labels, not UUIDs & rarely device (/dev/sda5).
I try to remember to add label when creating partition with gparted. When I forget I use Disks, but do not like Disks for modifying fstab.
You will have to add an entry to fstab for your new partition. Then give yourself ownership & permissions.

I have always mounted /mnt/data, but TheFu suggests just mounting off / if linking folders or directly into /home.
       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, you can change mount points.


Because I have multiple installs, I use one large data partition and mount it in every install, so I have same data. And I link folders back into /home.
        [https://askubuntu.com/questions/1013677/storing-data-on-second-hdd-mounting](https://askubuntu.com/questions/1013677/storing-data-on-second-hdd-mounting) & 
[https://askubuntu.com/questions/1058756/installing-all-applications-on-a-ssd-disk-and-putting-all-files-on-hdd-disk](https://askubuntu.com/questions/1058756/installing-all-applications-on-a-ssd-disk-and-putting-all-files-on-hdd-disk) 
   [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by TheFu on 2019-01-05
Storage layout and management is always a moving target based on our individual skills and needs.  For my 1st 10 yrs on Unix systems, I didn't do storage the way I have for the last 15 yrs. My understanding and skills weren't ready for it.

Unix to Unix storage sharing on the same LAN should use NFS. Over the internet, something based on ssh should be used or a full VPN is necessary to use any other sharing method.  CIFS/Samba should never be used over the internet (for most values of "never").

Using sftp is easy.  Setup openssh-server on the remote system, inside almost any Linux file manager, use the sftp:// or ssh:// at the beginning of the URL and that will access the remote system.  I always install fail2ban on my ssh-server systems to block brute force attacks.  scp, sftp, and ssh services are all enabled by installing openssh-server.  Most Unix backup tools work over ssh and obviously remote connections between the different Unix systems is done via ssh.  

OSX is Unix, BTW.  You just need to translate the name Apple gives these common tools into Apple-speak. I have no idea why they change the names for common protocols and tools, but they do.  When I was forced to use a Mac for a few weeks, it seemed they were just trying to screw with me. Painful, it was. No control.

Linux programs aren't big.  25G should let you install all the "creative" programs you can stand into /usr/bin/ ... Google "*file system hierarchy standards*" for where Linux places things. All the major Linux distros follow that standard. The **data** those programs use is a different story.  That is where you have the control.  In general, I keep media on different physical drives and on different systems than my desktop or most servers. Access to those files is via NFS from inside the LAN and through a VPN + (Nextcloud or Plex or other) from outside the LAN.  All our wifi devices are outside the LAN, so they must use the VPN to access internal files.  Security is important.

If you haven't figured backups out already, you need to.  Daily, automatic, versioned, backups.  It solves 1,001+ problems. Be certain to test and validate the restore process.  Using a VM to test all this stuff out is smart and carries effectively ZERO risks.  The storage layout directly impacts how easy or hard backups might be.  For a few years, I used virtualization snapshots and full copies of the .vdi files as a "backup."  This was a failure because it required downtime and huge amount of storage. Backups started taking more time than we had allowed daily and something had to change.  Switched over to treating each VM like a separate physical machine and started doing backups just like we would for physical machines.  Backups that were taking 90 minutes dropped to 2-4 minutes, with one taking about 20 minutes, but it is an email server full of data.  Before we could only keep a few backups and now we have 60-180 days of versioned backups using less storage. I call that a win.

I don't consider it a Frankenstein system at all.  It has components that I specifically picked. I've been burned a few times buying pre-built computers. No plans to ever do that again, though I suppose raspberry Pi systems are pretty close. ;)  SBCs are pretty amazing these days.  The Pine64Pro can do some amazing things for just a tad more cash than a r-pi and doesn't have the same I/O limitations that a Pi has.  AMD has some SBCs that are pretty amazing too if you need a real computer for cheap that is silent and can be wall mounted.  SBC - Single Board Computer.

---

### Post by TheFu on 2019-01-05
As usual, great links Oldfred.

Something I see all the time is different recommendations for editing system files.
```
sudo -H gedit /etc/fstab
sudo nano /etc/fstab
sudo vim /etc/fstab
gksudo gedit /etc/fstab
pkexec gedit /etc/fstab
```

Each method above has different failures.

Leave off the -H on the 1st method and logins or gnome-based programs might crash due to root owning config files. Also, gedit won't work on a remote system which is common for Amazon EC2 systems.

Nano is just a bad editor. Yuck!

gksudo is deprecated and shouldn't be used anymore. It had security issues.

pkexec - huh?  gedit assumes a desktop is being used with a GUI and that gnome stuff is installed. No gnome, no pkexec.

What is a noob/expert to do?

Use "**sudoedit**", of course!   sudoedit is part of the sudo package. It works with any editor, as configured by the EDITOR environment variable.  This variable has been around since the 1970s, so honoring it is expected.  sudoedit copies the system file to a safe, protected location using elevated privileges, opens it using the editor of choice under the normal userid, we edit the file, when closing the editor, the file is copied back to the original location using elevated privileges again.  All is right with the world.  Because the editor is run with normal userid, breaking out as root into a root shell isn't a concern.

```
sudoedit /etc/fstab   # <---- that's the safe way to edit system files on desktop, servers, local or remote.
```
Want to use gedit always?  Add this to your ~/.bashrc ... ```
export EDITOR=gedit
```  Want vim? Well, the easy way is to simply ```
sudo apt purge nano
```. ;)  Removing unwanted programs/packages is a good thing in my book and after rnano is gone, vim becomes the default editor.
Every system can have a different EDITOR, but you still use the same command. In my mind, fixing 1 thing, 1 time that solves many future problems BEFORE they can happen is a win.

A few years ago, we had a discussion about this in the forums after someone used sudo gedit on a brand new install and ended up not being able to run a browser or any gnome programs because root:root had owned the ~/.config/ directory.

Anyway, using sudoedit solves all sorts of issues, some very much hidden to the average user.  Plus, we're already used to typing sudo.... something, so sudoedit isn't hard like pkexec.  And sudoedit works on every platform that uses sudo, which is every Unix-like system, unlike pkexec.  

rant off.

---

### Post by spazz2 on 2019-01-19
Thanks oldfred ! My apologies for slack response !
Really hot weather in Sydney lately. Not great for running computers, either for computers or myself (patience for techie work in tropical heat).


I try to make time at work where it's air-conditioned, and when there's down-time, (but there hasn't been much past couple weeks).
At home , it's just been too sweltering lately.
=======================
So, root can be shrunk (or partition sizes modified) without wiping them? 
That sounds different? Have I misinterpreted what you said?
I'll need to read right through the links you gave.
=======================
I have at least 3 computers I've been setting up for ubuntu and one debian, so I will experiment with your system layout on one and TheFu's on another.


Thank you so much for collating all those links for me !!!! Wow !
I started reading Morbius's post, but it just got too hot for me the past couple weekends to follow through implementing.

I WILL give it all a go, and let you know how I get on.
Please excuse my slow moving-ness.

---

### Post by spazz2 on 2019-01-19
TheFu !
Awesome as always. 
Please excuse my late response, and see my post above to oldfred about the awful hot weather recently here being not conducive to using computers for much time at home --
(plus work study commitments ramping up).

Thanks for elaborating on the differences between SFTP and FTP (I read some of the entries in your blog regarding this, which were very informative about most-secure best methods, and why FTP outside LANS for most-part is redundant / poor choice).
-- And how to implement this on Linux. 
Probably dead-simple now, with your instructions here!

Bloody apple, ey ? It's love-hate for me.
I'm sure I'll get more ticked-off with apple's bash as I get more familiar with Linux / Unix terminal,
and want to switch between the 2.

I wonder if anybody might have created an automated translator for the 2 bashes ? That would be cool. So one could write in a linux terminal emulator on mac which can be input into mac's bash.
Wishful thinking , probably.

Unfortunately, all the best musical / audio apps are written for apple , as with many other great apps.
Would be awesome if same apps were available for linux, I'd make the switch -- but it will never be.

That being said , my needs and desires for what I actually want and need a "creative" system to do are being whittled down and decreased. 
Too many options become paralysing in a way, and it is better to work with certain limitations -- and I am very HIGHLY impressed with what is available on Ubuntu Studio, which in many ways covers many or most of my essential needs.

Still , DAWS like Ableton, Logic, Reaper etc are mainly designed for apple.
Although I see Bitwig runs on Linux !

[https://www.slant.co/topics/6067/~daws-for-linux](https://www.slant.co/topics/6067/~daws-for-linux)

I'm not positive how many virtual instruments can be run on linux yet -- for all I know, it can do most of what apple's do.

I too always put quotes around "creative" as it's a bit of a rubbishy word IMO. But w/e :P
======================
"Google "file system hierarchy standards" for where Linux places things"
Excellent, I had been googling things like that, and that is probably a better search term.
==================================
Your info about VM backups is going to be soooooo useful !!
I'm probably going to have some Q's for you on that later down the road.
I haven't had the opportunity past fortnight to implement most of the important info I've been given so far .  ---  so I'll get through that first.
==================================
Eheh, I meant "frankenstein system" in a good way (: A creature of your own design (:
Not in the sense that it was going to cause havoc.... I could have picked better words. Custom high-speed racer?

Yes, that is another thing in apple's favour, of course, is that all componentry just works together --
never have to worry about gfx drivers or any drivers in general for the most part etc. The NVIDIA thing on Linux is painful.
Tho, the cost of a new mac is astronomical -- which is why all mine have been purchased used and a few years old :P

I can definitely understand why many computing professionals have a big distaste for them though.

That said, I'm still a rank amateur and in small-system thinking. I'm not managing huge beasts like yourself.

I found a Raspberry Pi in the bin at work the other day !!
Definitely something to play with. I was very impressed with the i/o on this tiny box !


Cheers (:

---

### Post by spazz2 on 2019-01-20
Fu :
"A few years ago, we had a discussion about this in the forums after someone used sudo gedit on a brand new install and ended up not being able to run a browser or any gnome programs because root:root had owned the ~/.config/ directory."
======================
O_O        root owning root and preventing root from accessing config stored in root ?
meta-root and meta privileges ?

That's how it sounds to this clueless lay-person.

I know this was directed to oldfred but : 
Thank you for this "rant" , ie. very useful information.
I'm sure keeping this in mind will prevent me from making an awful goof in the near future.

---

### Post by TheFu on 2019-01-20
> **spazz2 said:**
>  
O_O        root owning root and preventing root from accessing config stored in root ?
meta-root and meta privileges ?

That's how it sounds to this clueless lay-person.


Not meta at all, just requires understanding that 
/home/thefu == $HOME == ~/

If HOME is set to /root/, then ~/ == /root/
But if HOME is set to /home/thefu, then ~/ == /home/thefu.

HOME is set at login by the value set in the password entry - **getent passwd thefu**
HOME is an extremely important environment variable.  Generally, no management of it is needed, but with sudo you can end up with a program running with root as the userid, but HOME still set to the normal user account's value.  This is almost always bad, but it is the GUI programs that tend to automatically create and write settings to the HOME directory.  CLI programs just don't do this. I don't know why.  This is why sudo nano isn't so bad, but sudo gedit is terrible.

Claro?

---


---
title: "dual installation with Windows 7 - hard disk question"
date: 2013-06-20
forum: New to Ubuntu
---

### Post by conure on 2013-06-20
Hi all,

I've finally got Ubuntu onto a DVD rather than USB stick and the installation now works flawlessly (using it on my laptop as the primary OS).

The problem is that I'm a first year Software Development and Robotics student and there is some software for my course which does not work on Ubuntu (RobotLab is developed by my uni and has no Ubuntu support :( )

As such, I have to keep a copy of W7 around for the rare occasions that I need to use robotlab. If I dual install Ubuntu alongside W7, how does the disk allocation work? Would I be best off partitioning the drive from within Windows? I'm not too confident of the best way to install them side by side. I only have a 120gb SSD (most of my files are stored online via a fibre connection so disk space is not really an issue).

Another option would be to run W7 in virtualbox within Ubuntu (or any other virtualisation software?) - would this work well?

Hope you guys can advise!

Thanks.

---

### Post by Frogs Hair on 2013-06-20
I think opinions vary on this, but I too need Win 7 for school .  I used Windows Disk management  create the partition and simply use the same space for new Ubuntu installations . My partition is not that large because the latest release is installed every six months and I backup in Ubuntu One.   I have not used virtual box, but remember reading it can require quite a bit of memory so I would check. The SSD is new territory for me and can offerer no advice.

---

### Post by billcecil on 2013-06-20
Have you tried to use "wine" to run this application?

---

### Post by DestructiveLabs on 2013-06-20
**@**[**[COLOR=#000000]conure[/COLOR]**]("http://ubuntuforums.org/member.php?u=1789934")

I have run all of my computers dual-boot and, in my experience, gparted is an easy way to manage the partitions on your drive. It should be available on your live boot DVD of Ubuntu.

I have used the windows partitioning tools... they aren't bad but they aren't anything fancy. I guess it all comes down to preference and I get mine from the many times I've installed Ubuntu on different machines. 

I wouldn't recommend wiping win7 completely and running it in a VM as you may lose some software packages you actually like/need. Also, sometimes, your VM can experience some fatal errors and you can end up losing all of your work :frown:!! Saw that happen to a guy in my web dev and architecture classes. (backups are key!)

As far as disk space allocation is concerned: if storage is not an issue for you why not just split your drive 50/50 win/ubun with a bit as swap space? or maybe 40/60? When installing Ubuntu and re-partitioning your drive, the installation process will advise a swap partition = the amount of RAM your PC has. (for more on swap: [read this]("http://help.ubuntu.com/community/SwapFaq")[COLOR=#000000]<- kind of long and boring though[/COLOR] ) 

Hope this helps.

-K

---

### Post by zrdc28 on 2013-06-20
The easy way to do it is to use windows 7 and split your ssd as you wish 50/50 or etc.
Next use gparted or pmagic to make your particians. Download and burn a iso of gparted and boot from it.
Please note that you can have only 4 primary particians under the old legacy scheme and you will need 5.
With this scheme you will need 5, so first make a logical or expanded partician with gparted of 60 gb or what ever the split is.
Next make a swap partician of 2 x memory that you have.
Next make a boot partician just use the symbol /.
Next make a /home partician.
save and then install ubuntu.

With a /home partician you can upgrade without loosing your data in home.

---

### Post by verymadpip on 2013-06-20
Hi there.
As has been mentioned (briefly) use the Windows disk management tool to shrink your Windows partition - nothing else.  Using another tool may result in corruption of the Win 7 file sysytem leaving you with an unbootable OS.
Once more for the cheap seats: Windows disk management for shrinking Windows.

Good luck dude, it'll all be ace!

---

### Post by fantab on 2013-06-20
> **conure said:**
> Hi all,

I've finally got Ubuntu onto a DVD rather than USB stick and the installation now works flawlessly (using it on my laptop as the primary OS).

The problem is that I'm a first year Software Development and Robotics student and there is some software for my course which does not work on Ubuntu (RobotLab is developed by my uni and has no Ubuntu support :( )

As such, I have to keep a copy of W7 around for the rare occasions that I need to use robotlab. If I dual install Ubuntu alongside W7, how does the disk allocation work? Would I be best off partitioning the drive from within Windows? I'm not too confident of the best way to install them side by side. I only have a 120gb SSD (most of my files are stored online via a fibre connection so disk space is not really an issue).

So, do you already have Ubuntu installed? and this is the only OS on the computer? If yes, then you can resize the Ubuntu partition, using Gparted, then create another partition and format it with NTFS. However, you MUST reformat the partition with NTFS using Windows tool during installation.
If you install Windows after Ubuntu then you will have to [reinstall GRUB, boot-loader for Ubuntu using liveDVD/USB]("https://help.ubuntu.com/community/Grub2/Installing#via_the_LiveCD_terminal").

If you want to start-over then: 
/dev/sda1 50GB Primary NTFS (to install Windows, the size is 50GB assuming that you only use it for RobotLab. If space is an issue then make it 40GB, which is a sort of minimum for Windows7)
/dev/sda2 20-25GB Primary Ext4 '/' (for Ubuntu system)
/dev/sda3 2-4GB Primary Linux SWAP
/dev/sda4 All the remaining GB Primary Ext4 /home (to store your Data like music, documents etc).

It is adviced that you use only GParted to create Linux partitions. 
Windows cannot access linux partitions but Ubuntu can. Meaning you can access your files in Windows from Ubuntu but not the other way round.

Good Luck.

---

### Post by conure on 2013-06-20
Thank you all for the replies - The laptop is Ubuntu but I want to put it on my desktop which is a fairly hefty gaming machine. I don't really find myself gaming anymore though so that's not really an issue.

I've managed to get robotlab working via Wine which is great news - the only challenge remaining is to get my Senseboard ([http://www.raspberrypi.org/archives/3240](http://www.raspberrypi.org/archives/3240)) working with Ubuntu...

So far the transition has been so easy. My girlfriend (IT illiterate!) has had no issues using Ubuntu to do her email checks, browsing and music listening with spotify. Looks like we'll be saving some money on an OS upgrade over the next few years :)

---

### Post by Mark Phelps on 2013-06-20
Some folks have been extraordinarily luck and not had their Win7 installs get corrupted when they used the Ubuntu installer or Gparted to mess around with their Win7 partitions.  Problem is, if you have a lot of time and effort invested in Win7, relying purely on luck is a really risky way to install Ubuntu.  If it fails, as it often does, you will have a very difficult time repairing Win7 to get it working again.

The SAFER way to do this is to use ONLY the Win7 Disk Management tool to mess around with Win7 partitions.  It's primitive and kludgy,  but it won't damage Win7 in the process.  And, after you do the shrinkage, be sure to boot into Win7 a couple of times to allow it to do any filesystem adjustment it needs.

Also, while in Win7, do yourself a favor and use the Win7 Backup feature to create and burn a Win7 Repair CD.  That will prove invaluable later if you need to repair Win7 from damage resulting fom the dual boot installation.

---

### Post by Paqman on 2013-06-20
> **Mark Phelps said:**
> Some folks have been extraordinarily luck and not had their Win7 installs get corrupted when they used the Ubuntu installer or Gparted to mess around with their Win7 partitions.

While I agree that it's good to be cautious (paranoid even...) when messing about with disk partitions, I've never actually heard of any confirmed case of the Ubuntu installer doing anything other than a good job of partitioning modern NTFS drives. I've done so myself several times without incident. 

I suspect Gparted's alleged lack of compatibility with Win7/8/whatever is something of an urban myth amongst Linux users. IIRC it originated when Win Vista came out and there was a lack of clarity about whether the available Linux parititioning tools supported the updated NTFS spec. I certainly wouldn't have any worries about whether a recent version of Ubuntu was using partitioning tools that were compatible with an older version of Windows like Win 7.

---


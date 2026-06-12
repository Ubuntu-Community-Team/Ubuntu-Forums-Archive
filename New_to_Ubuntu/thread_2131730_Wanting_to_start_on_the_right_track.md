---
title: "Wanting to start on the right track"
date: 2013-04-02
forum: New to Ubuntu
---

### Post by docJ on 2013-04-02
Hi everyone,
my very first time here, I have about 1 week experience with Ubuntu, but about 15 years with Windows.

I presently have a brand new machine being built to spec. (i5 with 8G ram to start, 4x WD green 2Tb drive) 
My need is a home "media server", basically a computer to hold large amount of video and music files. Once the data will have been imported from a poorly performing D-Link DNS-343 NAS on those huge internal storage drives,
I will eventually access the data from 2 windows7 pc's. The NAS will change role to essentially a backup Raid for the new "storage server"

This brings me to my first question; considering my needs and planned usage, as I do not plan to do much direct interaction with the system other than initial setup, the rest will pretty much be system always "on" to serve and receive media from/to the 2 windows 7, and perform occasionnal backups to the NAS, **is Ubuntu desktop 12.10 the best choice for me?** 
I have no experience whatsoever with open source, I'm a little scared of using Terminal and command lines.

Secondly, having played with it a little (on temporary machine) so far to get my hands dirty, I have selected EXT4 as a file format. Having used nothing but NTFS for the last 10 years, and considering I will do most of the after-setup acces from windows 7 pc's, [B]is EXT4 a good choice over the other available formats?
[/B]
Lastly (for now), I see Ubuntu (and others) being offered in 32/64 bits versions. Considering I will be installing on a spanking new machine, **should I automatically go for the 64 bit version**, I noticed the install instruction

---

### Post by DuckHook on 2013-04-02
Hi docJ and welcome to the forums and to Linux/Ubuntu in general.

Others are bound to give different advice, with very valid reasoning, but here is mine:

I do not recommend Ubuntu for your desired usage, not because it makes a poor server (in fact, it makes an excellent server) but because you are not yet familiar enough with Ubuntu or Linux to leverage it into a critical usage role.

In short, the drawback to Linux in your case is not technical, but experiential.

I give such a recommendation with something of a heavy heart. I use nothing but Linux on my servers and they work incredibly well. However, in my experience, there is no such thing as a maintenance-free server, and once they require maintenance, you want to be working on a platform with which you are familiar. Otherwise, they will leave you with nothing but frustration and long periods of downtime which, in the case of a server, is not acceptable.

I strongly suggest that you fulfill your curiosity about this wonderful OS in a non-critical, non-production environment first. Perhaps a spare box that you are not using for anything else, or in a dual boot environment on your current desktop box, or even in a virtual machine running inside Windows. You want to be thoroughly comfortable with Ubuntu before committing to its use as a server.

Just my two pennies worth.

---

### Post by arpanaut on 2013-04-02
Welcome to the forum, good idea to get to know the system before you jump into your project.
It will take some time as there is a learning curve to overcome, but lotsa people around here to help.
Just to start your research...

A couple of links for "media server"
[https://help.ubuntu.com/community/MediaTomb](https://help.ubuntu.com/community/MediaTomb)
[http://mediatomb.cc/](http://mediatomb.cc/)

---

### Post by grahammechanical on 2013-04-02
Another point to consider if you do take the plunge is Ubuntu 12.10 is supported until April 2014. You might want to consider Ubuntu 12.04 which is supported for another 4 years. Ubuntu Long Term Support (LTS) releases come out every 2 years. The last was in April 2012, hence its name 12.04. The next in April 2014 - Ubuntu 14.04.

Then again it may be that you have little experience with server operating systems to start with. So, if you are learning the subject from the beginning, then why not learn and become an expert in Linux/Ubuntu servers?

Another consideration. Ubuntu server does not install a desktop environment. But a DE can easily be installed. There is no law against administering a home server from a desktop. This way you get the server administration applications and a graphical user interface to run them.

Regards.

---

### Post by d0006 on 2013-04-02
I will offer my opinions:

Distro: You have conflicting requirements; Ubuntu will be the easiest to set up and maintain because it has great GUI support but it may not be the "fastest" distro.  Other distros will require you to use the command line more than Ubuntu (you will still need to use the command line in Ubuntu, and you should learn as much as you can. After the initial learning curve it will make things easier).  Do a search on "Linux distro chooser"  and see what they say.  These are not jokes, people have really worked on these and they help.  Two possibilities are Kubuntu and Linux Mint.

Filesystem: XFS will be the best for serving large video files, EXT4 for everything else.  You can partition your drive with an XFS partition for your media files and EXT4 for everything else.  Linux doesn't care!

I would go 64-bit. Support, drivers, etc., are very good and you will maximize the performance of your system.

Command line:  You should learn it.  There are MANY excellent tutorials and guides on the web. It is a pain in the beginning but you can do ANYTHING and EVERYTHING with the command line interface (CLI).
```
apropos <topic>
```
and
```
man <command>
```
are your friends!

You don't HAVE to use the CLI but you will have some limitations.

Finally, in a world of constantly diminishing freedoms, Linux is one of the very few areas where you have real freedom.

---

### Post by docJ on 2013-04-03
Thanks everyone for your input,
indeed my knowledge of Linux is dismal for now, but I know how to use google and use fine forums like this one: I just hope you won't get tired of me because I am at a digital life crossroad and I need to do improve upon my relying solely on the NAS I have.
I looked and looked for software solution, like other Linux flavors (man, how many of them are there!?!) nas4free, freenas, open media vault, Amahi (this one is different!), even tried WHS, I even toyed with the idea of running windows 7 24/7 with shared drives, & ended up full circle back to original plan.  
 I will pop the Ubuntu 12.04 64bits in the brand new computer later on this evening & see how it goes from there.
Later...

---

### Post by DuckHook on 2013-04-03
Absolutely the best of luck, then. We are cheering for you from the sidelines. From a previous thread, these resources may help:

As originally recommended by @slickymaster
[http://lnag.sourceforge.net/downloads/LinuxNewbieAdministratorGuide.pdf](http://lnag.sourceforge.net/downloads/LinuxNewbieAdministratorGuide.pdf)
[http://ftacademy.org/files/materials/fta-m2-admin_gnulinux-v1.pdf](http://ftacademy.org/files/materials/fta-m2-admin_gnulinux-v1.pdf)
[http://debian-handbook.info/download/stable/debian-handbook.pdf](http://debian-handbook.info/download/stable/debian-handbook.pdf)

---

### Post by docJ on 2013-04-05
Hi again,
so I have my brand new computer, which I burnt-in a litlle to make sure I could proceed.
12.04 64 bits is just installed, and soon after, the little thingy signaled some 120-something minor updates, that is now all taken care of.

In my mind, the next logical step would be to make sure Ubuntu uses the most appropriate/recent drivers.
I noticed my m/b cd has a linux drivers folder. The board is an ASUS P8b75-m/csm and the processor is Intel i5-3470 lga1155.
video, sound and LAN are all onboard. I am used to install drivers for windows, but I am now at a total loss.

Can someone give me good tutorial link(s) to help me with this? 
Thanks in advance !

DocJ

---

### Post by r-senior on 2013-04-05
If video, sound and networking are working OK, you don't need to update drivers. The kernel will have probed your hardware and installed the latest versions of appropriate drivers. You'll automatically get updates as they become available.

---

### Post by mastablasta on 2013-04-05
in linux drivers (for the most part) are part of kernel (core of the OS). as the core updates so do the drivers. the exception are some proprietary graphics drivers and drivers for wireless chips. also some printers require special drivers.

no one mentioned to you but you can administrate your server from your windows7 computers using a browser interface (internet explorer, chrome, firefox..). you can install ***webmin***, then there is ***zentyal*** (which also has it's own ubutnu based distribution). then there are special distributions with GUI ment for file storage such as for example openmediavault. Clear OS is another GUI distribution but based on CentOS->which is based on Red Hat Enterprise Linux (which has really long support time and is very stable).

another thing to meniton here (Since you plan to have a media server) is to have a look at XBMC project.

as for the file system they already gave a good advice. just avoid NTFS and you will be fine :-) ext4 and others don't have such high fragmentations. so while windows NTFS gets slower over the years and then needs defragmenting the ext4 doesn't. there are also other benefits to ext 4, xfs, zfs and others...

have fun learning about the new OS and i found virtual box to be a good way to test things before implementing them. oh and don't be afraid to ask. people will help.

---

### Post by docJ on 2013-04-05
I will leave the defaults drivers alone, thanks for the infos...
 
I have 4 hdd in my pc, the first is all setup properly, so I need to take care of the 3 ''data'' drives. 

1) I need to create mount points; In the Disk utility, after I clicked the Mount point button, the Disk Utility tells me Mount Point: Mounted at **/media/b** (and **/media/c** and **/media/d** for the 2 others drives)
Is this OK? What I mean is does it need another ''slash something'' before or after or can I leave it at that?

My next question might be about having those drives mount automatically (after a reboot), but for now I just want to make sure I grasp the mount point thing correctly...

---

### Post by arpanaut on 2013-04-05
This should help you with auto-mounting.
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by docJ on 2013-04-06
Yes, very helpful indeed; I was able to auto mount using the mount point listed earlier.


After that, I truncated the Fstab from the url to see more subjects; my bookmarks are filling up like crazy! 

Making progress thanks to lots of you, thanks for your patience

---

### Post by docJ on 2013-04-06
Moving right along, I changed owner of the data drives to myself using chown, I then shared them with gksudo nautilus. 
I password protect with smbpasswd

When I test my acces from windows computer, it should ask for a password, but it doesn't, did I do something wrong?

---

### Post by docJ on 2013-04-07
I thought I would end this thread on a shinning bright note
One of the main reason I needed to build a new media server was the catastrophic performance of my D-Link NAS.
My home network could never read/write faster than 10MBps to/from it; in reality I was getting access speed much lower, sometimes under 1MBps... Dealing with multi-Tb of data was a test of patience to say the least.

I just sent an errant avi 700mb file from windows straight to Ubuntu (without passing thru my NAS) & could not beleive my eyes
TeraCopy showed me a speed close to 70MBps and the copy took like 5 or 6 seconds....  
I almost cried....
Ubuntu Rocks ! :guitar:

---

### Post by docJ on 2013-04-07
I was looking at forum guidelines in regards to thread solved; When I click thread tools, I do not see any way to mark it as "Solved"
Maybe for lack of privileges as I have not enough post yet (?)

---

### Post by CatKiller on 2013-04-07
No, it's just a problem with the new theme. You can edit the first post to change the prefix for now.

---

### Post by UrbanDictionary on 2013-04-07
I found the resources posted by DuckHook to be helpful, and I own a netbook.

---


---
title: "Two Linux (Linux-learner) Backup-computer partitioning..."
date: 2020-05-18
forum: New to Ubuntu
---

### Post by Mike Krall on 2020-05-18
Have an almost-never-used 2012 Toshiba Satellite L750D with MBR Windows 7... 4GB RAM... 500GB HDD...  AMD A4-3305M APU  with Radeon HD Graphics 1.90 GHz (believe it's a 6480G).   

Can't (shouldn't) use the Windows 7 on the internet now no longer supported.

Need to have a computer to use as others need work or are in a replacement cycle, and this machine is likely to hold up 'forever'.  

Thought to have two linux because one of the users (a Windows person) might find one or the other suited better.  I could do a lot of different things here... separate data partition being one... NOT doing two Linux OS being another.

Because this machine will only be turned on to update/upgrade/clean install/use as backup, it would be basically empty.  A person *might* collect some music or recipes or a few documents or pictures, and they could easily be transferred to regular machine.

I looks to me like a shared /home is a simple way to do this.  Each Linux would have it's own user (same 'Name', same 'Hostname').

So... two things:  

1)  With different users, I can't figure out what aspects of /home are actually shared... or maybe that is I don't understand if I'll see two of everything (Documents, etc.) in the shared /home.  Could some one please give me a simple description of what /home will and won't be in this set-up, please?

2)  How to partition?  It looks to me like a person would use GPartEd to clear the machine, then pre-partition.  It seems 'right' to me to do this:  /,  /,  swap (I know of the swap file movement),  extended, /home (to disk end). Would then put in one Linux ( /, swap, /home)... point /dev/sda MBR boot...  cycle... check... install 2nd /... point /home... etc.  
I'd like to get some views on this and/or other ideas on setting this computer to the use, if you would make the time.

Thanks...

Mike

---

### Post by Holger_Gehrke on 2020-05-18
The normal way of doing things on Linux is to have separate directories for every user inside /home, for example /home/user1 and /home/user2. Since programs store their settings for each user in the users home directory or sub directories of it, having one home for more than one user is not a good idea. A better idea would be to have both users be members of a group, set that group as their standard group so files they create belong to that group and have a directory writeable by members of that group (for example /home/common). You'd then create subdirectories in that directory and replace the standard directories (Documents, Music, Video, Pictures, Templates etc) with links to these directories.

If at all possible, use GPT partitioning. No more extended partitions necessary. So then / on one partition and /home on another is fine. swap on a partition might be faster by a few microseconds because access to a raw partition doesn't have to go through a file system driver, but compared to the difference in access time and transfer speed between RAM and HD it doesn't help enough to be worthwhile. A swap file on the other hand can shrink or grow as needed, something not easily done with a swap partition.

Holger

---

### Post by TheFu on 2020-05-18
i wouldn't use the same hostname.  There are cryptographic functions where having the same name but different crypto-signatures will cause problems.

Also, don't load an entire new OS just to have a different gui.   You can load 5+ different guis on the same install, just use a different username/userid for each different GUI.

What is this "regular machine?   Linux is a regular machine.

Linux is multiuser from the top to the bottom.  if you need multiple users to have access to each other's files, then use normal Unix permissions and put those userids into the same group. This is extremely common. Happens millions of times a day around the world.  Search these forums for "working together"

About MBR. Use GPT which allows 100+ primary partitions.  GPT has been around over 10 yrs and supported by all OSes.  Windows mandates GPT for UEFi booting.  You can use gparted or fdisk or parted or any other partitioning tool.  **Gparted** is probably what I&#8217;d use, if I had a GUI available.

For a disk layout,  [https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277](https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277) is one.

---

### Post by oldfred on 2020-05-18
I also suggest using gpt.
But with BIOS boot on gpt you need a tiny 1 or 2MB unformatted partition with the bios_grub flag.

I did that starting back in 2010 before PCs had UEFI. Windows required MBR for BIOS boot, but Ubuntu worked from gpt.
Later when PCs started having UEFI, I made first partition an ESP for UEFI boot (even though I did not yet have UEFI) and used bios_grub for booting. But then could move drive to newer system, reinstall grub can convert to UEFI without having to totally redo drive.

---

### Post by Mike Krall on 2020-05-19
> **TheFu said:**
> [COLOR="#0000CD"]i wouldn't use the same hostname.  Their are cryptographic functions where having the same name but different crypto-signatures will cause problems.[/COLOR]

Also, don't load an entire new OS just to have a different gui.   You can load 5+ different guis on the same install, just use a different username/userid for each different GUI.

What is this "regular machine?   Linux is a regular machine.

Linux is multiuser from the top to the bottom.  if you need multiple users to have access to each other's files, then use normal Unix permissions and put those userids into the same group. This is extremely common. Happens millions of times a day around the world.

About MBR. Use GPT which allows 100+ primary partitions.  GPT has been around over 10 yrs and supported by all OSes.  Windows mandates GPT for UEFi booting.  You can use gparted or fdisk or parted or any other partitioning tool.  Gparted is probably what I&#8217;d use.

For a disk layout,  [https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277](https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277) is one.

[COLOR="#0000CD"]Blue...[/COLOR]  Thank you for that.  I thought it was only true for different machines on same connection... and NEEDED to be same for same machine, different Linux OS.

Not looking for different GUI per se. Simple enough to put in Linux Lite and go on with the next thing (light, simple, designed specifically as good place for a 'new to Linux', life long Windows person to start).  The idea of another available light OS (Ubuntu MATE) is to have a choice (and the choices within that choice).  Simply, I hope that will present Linux well.

Not looking to have two user access, really.  It's just a machine to use when a person's 'regular' machine isn't usable.  I thought a common /home, if able to be structured to avoid configuration problems, would make upgrades, clean installs easier.  I could just dump in /, /, swap and call it done.   

My 'regular' machine is an 'oldfred' version of separate data partition (/mnt/data)... 7 Linux OS... most not used any more.  I switched to Linux in Jan. 2007... didn't like using MS machines... thought there might be a better way... was right.  I didn't know anything when I started and I know very little more now.  I like it, though. 

I said a little about MBR vs GPT in response to Holger.  My ASUS laptop is GPT.  I'm aware to an extent, chronologically, of the evolving away from MBR and to GPT... problems with it in Linux.  That is not to say I know anything.  I would switch the Toshiba to GPT if I KNEW it was going to be effortless... I don't... and my looking hasn't found me enough understanding to 'just do it'. 

Thank you for your time, and your help...  and for the link.  I like trying to learn this stuff

Mike

---

### Post by Mike Krall on 2020-05-19
> **oldfred said:**
> I also suggest using gpt.
But with BIOS boot on gpt you need a tiny 1 or 2MB unformatted partition with the bios_grub flag.

I did that starting back in 2010 before PCs had UEFI. Windows required MBR for BIOS boot, but Ubuntu worked from gpt.
Later when PCs started having UEFI, I made first partition an ESP for UEFI boot (even though I did not yet have UEFI) and used bios_grub for booting. But then could move drive to newer system, [COLOR="#0000FF"][COLOR="#000000"][COLOR="#0000FF"]reinstall grub can convert to UEFI without having to totally redo drive.[/COLOR][/COLOR][/COLOR]

Like this 'oldfred'?  See partition structure charts 3/5's down page... #3... "BIOS/GPT example layout"...  [https://wiki.archlinux.org/index.php/Partitioning]("https://wiki.archlinux.org/index.php/Partitioning")

[COLOR="#0000FF"]Blue...[/COLOR] Would you point me somewhere for this, 'oldfred'?  Is in signature link?  And do I get it... makes work without switching HDD type? 

Mike

You know, one of these days I ought to figure out how to get a screenshot into a post...  =[

---

### Post by mastablasta on 2020-05-19
> **Mike Krall said:**
> 

Thought to have two linux because one of the users (a Windows person) might find one or the other suited better.

a windows person is used to having a DE shoved down their throat. pick one, install that. 

we moved to KDE (Kubuntu). kids find no issues in switch, father had no issues (we moved him in version 12.04), wife had no issues with the switch. we switched from winxp and win7. father was used to win8 and 10 at work. interface is the most similar to windows. similar interface is also found in Cinnamon and XFCE desktops. but the fee is still the most similar in KDE. windows often also "borrowed" design functions from KDE. since design is kind of similar it is no issue for the user to make the switch. windows apps are ran through Play on linux. though we currently have only games there. :)



you can also stay on win7 for a while longer. just make sure you have good firewall (e.g. Comodo suite is comprehensive) and good antiviurs (from the free ones avast detects good and behaves nicely with Comodo, so does Avira). Comodo has it's own antivirus but detection rate is a lot lower (i took reviews and test through many years into account here), so i don't install that or turn it off. it does very well in other areas. MS security essentials also still has updates for virus definitions and provides descent protection. also works nicely with Comodo.

---

### Post by Impavidus on 2020-05-19
> **Mike Krall said:**
> 
Not looking to have two user access, really.  It's just a machine to use when a person's 'regular' machine isn't usable.  I thought a common /home, if able to be structured to avoid configuration problems, would make upgrades, clean installs easier.  I could just dump in /, /, swap and call it done.If you use two different Linux systems with the same /home partition, make sure you use different usernames on both, or you'll be asking for problems. Different versions of Linux will get you different versions of applications with different, incompatible versions of config files, stored in the same place. So you can't use the same home directory on both, which means a different /home partition or different usernames. (Technically, the home directory doesn't have to be /home/username, so you could avoid it, but I don't think that will be a good solution.) You can have a shared data partition for both and replace Documents, Downloads etc. by symlinks to the directories on this data partition. Just make sure that both systems use the same userID.

> 
I said a little about MBR vs GPT in response to Holger.  My ASUS laptop is GPT.  I'm aware to an extent, chronologically, of the evolving away from MBR and to GPT... problems with it in Linux.  That is not to say I know anything.  I would switch the Toshiba to GPT if I KNEW it was going to be effortless... I don't... and my looking hasn't found me enough understanding to 'just do it'. 

A computer from 2011 probably has UEFI, but set to legacy mode. My current laptop is from 2011 and is like that. Whether that UEFI nicely conforms to the standard is another matter, so I can't say if it's going to work in UEFI mode. You can keep it in legacy mode if you like. Legacy mode+GPT partitioning can be done. But then, as you only intend to use this laptop as a spare, without significant document storage, it doesn't really matter. Just partition it once and do it right, then there should be no need to ever change any partitions before the hard drive breaks.

A swap partition is a good idea. You can use a swap file too, but with two different Linux systems installed, you can share a swap partition, but you can't share a swap file (not easily anyway).

---

### Post by TheFu on 2020-05-19
> **Mike Krall said:**
> Like this 'oldfred'?  See partition structure charts 3/5's down page... #3... "BIOS/GPT example layout"...  [https://wiki.archlinux.org/index.php/Partitioning]("https://wiki.archlinux.org/index.php/Partitioning")

[COLOR="#0000FF"]Blue...[/COLOR] Would you point me somewhere for this, 'oldfred'?  Is in signature link?  And do I get it... makes work without switching HDD type? 

Mike

You know, one of these days I ought to figure out how to get a screenshot into a post...  =[

a) please DON'T use screen shots.  Use text methods.  If there's some data you'd like to show, we can provide commands to access it as text for posting.  Don't use 10K when 200 bytes works better.  Plus, we can copy/paste selected parts of text back in our answers.

Partitioning doesn't need to be complex.  Ignoring the /boot/ and /boot/EFI stuff, most of my systems have 2 or 3 "partitions" - that really isn't true because I usually leverage LVM, which is an advanced file system management technique, but for discussions here, an "LV" can be considered the same as a "partition".
```
Filesystem                      Type  Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root     ext4   25G   12G   12G  52% / 
/dev/mapper/ubuntu--vg-home--lv ext4   74G   21G   51G  29% /home 
/dev/mapper/ubuntu--vg-stuff    ext4   99G  367M   93G   1% /stuff

```
/ is for the OS.  Selected parts of this get backups.
/home is for real human logins. This get backups.
/stuff is where I put stuff that I never need to backup. See the delineation for that storage? It is about keeping different parts separate based on the backup needs primarily, next is a convenience aspect.

The swap partition (LV) is 4.1G in size, but doesn't show up in the **df -Th** output above.  The **swapon -s** command will show it.  That system isn't on the network right now, so I can't post it. A different system:
```
$ swapon -s
Filename                                Type            Size    Used    Priority
/dev/dm-1                               partition       4300796 36540   -2

```

For most people, there's no need to follow a complex partition layout like that arch link shows.  In the early 1990s, is **was** necessary to split up different parts of the OS to prevent system crashes due to full file systems, but HDDs were 20MB back then.  I remember when my UNIX workstation at the job came with a 2GB HDD - I didn't know what I'd do with all that storage.  Turned out that loading emacs on the workstation used enough to make space tight. ;)

[LIST]
[*]I'm in favor of separate swap partitions. I have reasons, but those may not apply to everyone. LVM lets me resize a swap LV in a fairly painless way, unlike using partitions.
[*]I'm in favor of using separate userids for different DEs.
[*]I'm in favor of using separate userids if you run different OSes from different families.
[*]I'm in favor of keeping partitioning simple - the minimal needed.
[*]I'm in favor of using GPT tables whenever possible, regardless of the disk size.
[*]I'm in favor of using symbolic links from a user's HOME to storage mounted elsewhere, especially when multiple userids need to access the same files.
[/LIST]

A good, free, reference book: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) There is a chapter about userids.

help.ubuntu.com has many guides and step-by-step instructions specifically written for non-technical people - well, for the desktop guides.  Google "ubuntu desktop guide" ... but be aware this is for the default "gnome3" ubuntu desktop.  Mate, XFCE, LXQt, KDE versions will all be a little different unless the exact same program is used.  Never forget that the GUI is just another program. It isn't the "OS."

Everyone posting here has good ideas based on their experiences. Only you can decide which makes the most sense.

---

### Post by Mike Krall on 2020-05-20
It has been a very long day...

I got to read all the new posts this morning.  Thank you all... thank you very much.  

As 'The Fu' said in the last line of post #9... about all the good ideas there are, are here.  Right now I don't know what I'll do for a structure. I'll start with 'oldfred' and BIOS/GPT... a couple of MiB.  From there, ???

The thinking about this I was able to do during the day caused me one more question.  I've got 500 GB drive and, in some scenarios, about 60 - 100 GB of 'stuff'.  Somewhere I got the idea a person should allocate space available.  Yeah, I know... sometimes a person wants to have held-back-space available if it can be arranged strategically.  I think that's not this instance.  Should I be looking to use the whole drive? 

Mike

Oh...  I've replaced my 4th addition copy of Wm. Shotts book with the 5th edition linked. And I did run 'xman'.  That is a nice thing to know... thank you.

Edit:  And I'll let you know what I did, maybe why, and how it worked out... and I PROMISE I'll click "SOLVED" when it is...  =]

---

### Post by Dennis N on 2020-05-20
Welcome back, Mike Krall. I recognized your user name. You had a previous enormous 43-page thread with 426 posts on custom grub menus and multi-booting, even using separate data partition, back in 2017-2018. I know because I participated in it over several months. You should consider yourself an experienced user, not new to Ubuntu!

---

### Post by TheFu on 2020-05-20
> **Mike Krall said:**
>  
The thinking about this I was able to do during the day caused me one more question.  I've got 500 GB drive and, in some scenarios, about 60 - 100 GB of 'stuff'.  Somewhere I got the idea a person should allocate space available.  Yeah, I know... sometimes a person wants to have held-back-space available if it can be arranged strategically.  I think that's not this instance.  Should I be looking to use the whole drive? 

I don't allocate all the storage, especially on SSDs.  There is proof that leaving 20% unused drastically increases the life of the SSD.
Because I use LVM for storage management and LVM allows growing each LV in about 5 seconds (1 command), while online, active, reallocating more where needed isn't a hardship.  LVM even has ways to automatically add more of the available storage where it is needed automatically. As a control freak, I don't use that.  Our best guesses for how storage will be used is seldom correct.  I'm never right, after over 25 yrs doing this.

I've already posted a link to my storage layout above. It uses LVM. Happy to answer questions about it, but many of the answers will be "because it seemed reasonable at the time and I could increase it later, easily."  Making LVs/partitions smaller is hard.  Making LVs larger is trivial, but making partitions larger can be either hard or trivial, it depends on the layout created and free space before and after each partition.  

With SSDs the actual way things are stored has NOTHING to do with the layout we see. It is all virtual, but our partitioning tools don't have a way to deal with that.  LVM provides that capability, for a little more complexity.  LVM has been used in Enterprises over 20 yrs.  
Following a few simple rules and LVM can be great. Do something foolish with it, which I've done, can lead to massive data loss. I have 1 main rule about LVM to prevent data loss.  Don't have LVs span disks unless RAID1 mirroring is the goal AND the backups easily store the data/files on a single physical volume.

---

### Post by Mike Krall on 2020-05-20
'The Fu'... 

Thank you for the answer and the education... 

I've avoided looking at LVM.  It was a quite logical approach to what I wanted to do in 2017... get involved with a number of different Linux types.  At the time I felt I understood the data partition structure better and I had to go one way or the other.  Now, I may just be too old and lazy to dig into it.  A person never knows what a person doesn't know, so we'll see. 

I do think I ought to stretch out whatever form I use for the two Linux OS on 500 HDD, though.  I've the luxury of not having to actually live with the outcome...  no data held, nothing added, and handy .iso files makes a lot of slack in a system.

Mike

---

### Post by Mike Krall on 2020-05-21
> **Dennis N said:**
> Welcome back, Mike Krall. I recognized your user name. You had a previous enormous 43-page thread with 426 posts on custom grub menus and multi-booting, even using separate data partition, back in 2017-2018. I know because I participated in it over several months. You should consider yourself an experienced user, not new to Ubuntu!

Hello Dennis N...  =] 

I knew I'd come word to word with you again someday.  Already had a standard short-yap with 'oldfred' in this one... got one thing straight with minimal words.  

My memory of the GIANT /mnt/data thread was you and 'oldfred' (and quite a few others) maintaining patience and civility long enough to get me through it.  Though I messed with a number of OS's, switched out a few after the set up functioned,  I am not what a person would call any kind of fluid with it.  I'd need to go reread all those posts to do it again, I'm pretty sure. I did get quite a bit of outside reading done during that thread, though...  made me aware of an awful lot of stuff.  Still, my function level is right here in this sub-forum, truth be known. I am NEVER going to know and understand things well enough to come up with ```
for i in `echo /mnt/data/*`;do ln -s $i; done
```Not ever...

And it's really a very nice place here... the in-house regulars are a lovely bunch of folks with wonderful understanding(s). 

I may need to find you at Manjaro, 'Dennis N'... looked for and didn't find my note of your user name there.  Would have it again if you would. 

Mike

Oh... here's a thing (Off --yet on-- Topic, for sure)... I came clear on the Coronavirus thing with this... have sent it to every and all...  would suggest same...  epidemiologist... teacher... short read... has pictures...  =] 

[https://www.erinbromage.com/post/the-risks-know-them-avoid-them?campaign_id=9&emc=edit_nn_20200511&instance_id=18384&nl=the-morning&regi_id=67919543&segment_id=27239&te=1&user_id=465e853b9a8e6283e41ff0fc35d97b2a]("https://www.erinbromage.com/post/the-risks-know-them-avoid-them?campaign_id=9&emc=edit_nn_20200511&instance_id=18384&nl=the-morning&regi_id=67919543&segment_id=27239&te=1&user_id=465e853b9a8e6283e41ff0fc35d97b2a")

---

### Post by Dennis N on 2020-05-21
Good Article - thanks. I'm keeping it.

Manjaro Forum - I have only made a few posts there in the past - all were questions about Manjaro - really nothing to see. It's overflowing with expert help - including that of the maintainers of Manjaro who always seem to be on there ready to help. I frequent the Ubuntu Forum only and use Ubuntu most of the time.

LVM - I use it. It's worth learning if you want something new to try. I've also been using QEMU/KVM virtual machines for all the Ubuntu versions starting with Ubuntu 18.10. My VM host is Fedora Workstation (installed with LVM, of course). This is also worth learning.

---

### Post by Mike Krall on 2020-05-21
> **Dennis N said:**
> Good Article - thanks. I'm keeping it.

Manjaro Forum - I have only made a few posts there in the past - all were questions about Manjaro - really nothing to see. It's overflowing with expert help - including that of the maintainers of Manjaro who always seem to be on there ready to help. I frequent the Ubuntu Forum only and use Ubuntu most of the time.

LVM - I use it. It's worth learning if you want something new to try. I've also been using QEMU/KVM virtual machines for all the Ubuntu versions starting with Ubuntu 18.10. My VM host is Fedora Workstation (installed with LVM, of course). This is also worth learning.

*  Good you liked the read.  I'm hoping everyone in the world gets to see it.  

*  If I need to, I'll talk with the Manjaro folks.  I think I've dug out a solution but it's one of those 'simple-if-you-know-what-ALL-the-references-are' things.  I could just ask, but I'm likely to go deciphering first.  I spent a lot of time with Manjaro early on... Arch Wiki.  Haven't been there in a long time.

*  I would have gotten this handed back to you sooner, 'Dennis N', but you got me sidetracked to QEMU/KVM virtual machines for a bit... =]   Now I've got yet one more folder.  Maybe we'll see about this LVM, etc. thingy.  I'll at least try to find a beginning read for it...  a rough explanation/view point.

I'm going to mess with this current thing tonight... thank you, and have a good evening, 'Dennis N'.

Mike

---

### Post by Dennis N on 2020-05-22
> Maybe we'll see about this LVM, etc. thingy. I'll at least try to find a beginning read for it... a rough explanation/view point.
Two suggestions for when you feel like a little light reading:
[LVM Demystified]("https://www.linuxjournal.com/content/lvm-demystified")
[Ubuntu LVM Guide Part 1]("https://tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html")
These were the first two articles I read on LVM. Enough here to attempt one's first LVM install.

---

### Post by Mike Krall on 2020-05-23
'Dennis N'...

Ah... LINKS!!!  =]
Thank you...

Mike

---

### Post by TheFu on 2020-05-23
A always assume people can perform a web-search for any terms they don't understand. The way I need things explained is seldom the way someone else needs it explained, though I do post links from time to time.

---

### Post by Mike Krall on 2020-05-24
> **TheFu said:**
> A always assume people can perform a web-search for any terms they don't understand. The way I need things explained is seldom the way someone else needs it explained, though I do post links from time to time.

Yes.  You do post links from time to time.

I was just going to start into a couple of hundred words on links.  I'm going to partition instead.

I'm in favor of discriminating linking.

Mike

---

### Post by Mike Krall on 2020-05-26
> **oldfred said:**
> I also suggest using gpt.
But [COLOR="#0000CD"]with BIOS boot on gpt you need a tiny 1 or 2MB unformatted partition with the bios_grub flag.[/COLOR]

I did that starting back in 2010 before PCs had UEFI. Windows required MBR for BIOS boot, but Ubuntu worked from gpt.
Later when PCs started having UEFI, I made first partition an ESP for UEFI boot (even though I did not yet have UEFI) and used bios_grub for booting. But then could move drive to newer system, reinstall grub can convert to UEFI without having to totally redo drive.

I've been trying to reconcile a couple of questions pertaining to 'oldfred' post.  The whole thing, but pointing to [COLOR="#0000CD"]Blue[/COLOR]. 

And... looking at Grub Manual 4.4 - BIOS installation:  [https://www.gnu.org/software/grub/manual/grub/html_node/BIOS-installation.html#BIOS-installation]("https://www.gnu.org/software/grub/manual/grub/html_node/BIOS-installation.html#BIOS-installation")  Specific:  Last para. MBR and GPT from "*but it can also be used on BIOS platforms...*"... then on.

And...  the Arch Wiki Partitioning page (charts 3/5's down): [https://wiki.archlinux.org/index.php/Partitioning]("https://wiki.archlinux.org/index.php/Partitioning") ... third chart...  "*BIOS/GPT example layout*".  

The three look to be saying the same but I don't have a way of telling for sure.

And then... if I've got this right... I don't need the 'parted' code in GRUB 4.4 because the installer has the same facility built in... does what the code would do...  Is right?   

And then...  I've gotten confused with what GRUB-thing needs to happen with following OS install.  Have seen "install to ' / ' " ...  ignore the question... do one or the other (or another) then goto first install (OS with GRUB in small BIOS_grub flag partition) and code ????????.  I just keep looping back on myself with this.  In the end, I'd like to have a boot screen come up and show both OS.  What's the move of highest likelihood for that with GRUB and the other OS?
----------------------------------------------------    

A thing I wonder:  Using GPartEd to partition prior to installing...  blanking out Windows 7 ("Create New Partition")...  Because of the disk/BIOS structure (( from Belarc Advisor:  *Boot Mode: Legacy BIOS in UEFI (Secure Boot not supported*), and I should have put that in at the beginning of this thread ))...  Will there be a remnant area at disk front -- the "*at least 31 KiB (63 sectors) from the start of the disk...*" (from Grub 4.4)?  If yes, does it matter in relation to 'oldfred' "*tiny 1 or 2MB unformatted partition with the bios_grub flag*"?  If yes,  is there an approach with  GPartEd that would erase that?  If yes, how? 

Is that enough?

Mike

---

### Post by oldfred on 2020-05-26
The 63 sectors is before the first partition with old systems XP era & maybe early Windows 7. It now is 2048 for alignment with new systems. 
Grub in BIOS mode installs to MBR, but MBR is so tiny it needs more code and uses the space after the MBR for core.img. Windows also uses that space for some security info like flexnet. Used to create conflicts but grub works around that.
Windows also installs its boot loader to MBR in BIOS, but then has more code in PBR, partition boot sector & its boot partition or main install partition whichever has boot flag.

Windows has required UEFI/gpt since release of Windows 8 in 2012. Windows 7 can be installed in UEFI mode, but usually was BIOS/MBR. Large customers still wanted BIOS mode with newer hardware so even Windows 10 can be installed in BIOS mode. There is some discussion  that new systems in a year or two will eliminate the BIOS mode, but old hardware would not be affected.

If only using one drive, you have to install all systems in same boot mode. And Windows sets rule.
Windows requires MBR partitioning with BIOS boot.
Windows requires gpt partitioning with UEFI boot.
Ubuntu does not seem to care, but incorrectly lets you install Ubuntu in UEFI mode to MBR drive and then conflicts with Windows. If no Windows on drive it would be ok, but gpt is better than MBR, so no reason to use MBR unless you have to have Windows in BIOS boot mode. 

If using newer gpt partitioning there is no space after MBR, so a BIOS install of grub needs space for core.img and has to have the 1MB unformatted partition bios_grub.
With gpt Windows has to have the system reserved partition which is where is puts the info it used to have right after MBR. So now no conflicts with grub & Windows.

Use Windows tools for Windows & use Linux tools for Linux is best advice. Windows will not see nor work with Linux and while some third party Windows tools will see the Linux partitions better in almost all cases to use Linux tools.

If you have newer UEFI based hardware better to have both Windows & Ubuntu in UEFI boot mode. A few have so many issues with older UEFI implementations they do stay with BIOS/CSM/Legacy boot, but that is really the hardware vendor's UEFI or user preference. UEFI also has more settings since it also can be BIOS and some systems need multiple settings to install Ubuntu.

---

### Post by Dennis N on 2020-05-26
Your second link (to arch linux wiki) is broken - no charts there.

Here is example of bios grub partition needed on GPT-partitioned disk when used for bios install. 2 MB was specified as the size, and bios_grub flag was set. The partition editor in the installer seems to be the same as the stand-alone gparted. In fact, in my last install, I think I used the installer's partition editor to do the work. It works. As you can see, this setup is not limited to 4 (primary) partitions as MSDOS partitioning would be.

```
Model: ATA Samsung SSD 860 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  3146kB  2097kB                     bios_grub
 2      3146kB  44.0GB  44.0GB  ext4
 3      44.0GB  296GB   252GB                      lvm
 4      296GB   401GB   105GB                      lvm
 5      401GB   469GB   68.2GB                     lvm

```
(The disk is sdb, because it was added later and changed to be the first boot disk in BIOS.

---

### Post by oldfred on 2020-05-26
I started conversion to gpt in 2010 and had to have a bios_grub. Grub just would not install without it. Windows XP then was separate MBR drive.
Then in 2012, as new hardware was UEFI, I started to add both an ESP & the bios_grub partitions to all new drives and larger flash drives, even though still BIOS system. I figured I could then move drive to new UEFI system without major re-partitioning.  Most of my flash drives are full boot installs, but really for emergency boot and backup data. Now I do not add bios_grub anymore. 

Oldfred's partitions with new NVMe Feb 2020 UEFI 
[https://ubuntuforums.org/showthread.php?t=2437535&p=13934695#post13934695](https://ubuntuforums.org/showthread.php?t=2437535&p=13934695#post13934695)
Oldfred's partitions Dec 2015 has ESP & bios_grub
[http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413](http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413)

---

### Post by Mike Krall on 2020-05-26
> **Dennis N said:**
> Your second link (to arch linux wiki) is broken - no charts there.

Fixed link, 'Dennis N'... checked it for function. 

Be back later... working on house building.

Mike

---

### Post by Dennis N on 2020-05-26
> The three look to be saying the same but I don't have a way of telling for sure.
Yes, they agree. In the "BIOS/GPT example layout", beside the bios boot partition, you need a partition to serve as / for the installation; if you are using Ubuntu only (no multi-boot), you don't need the swap partition because Ubuntu will create a swap file in it's / partition. Nor do you need the Home partition. If you install Manjaro or Fedora, I'm not sure they can use a swap file - a swap partition may be needed.

The information doesn't cover LVM setup at all, so I will skip that. 

Summary:

bios-boot-partition + ext4 partition for / is enough for standard (non LVM) Ubuntu install in BIOS mode using GPT. A 'Home' partition is optional.

Unencrypted installs (standard and LVM) don't need a /boot partition. This is so for Ubuntu flavors, Manjaro varieties and Fedora at least.

---

### Post by Mike Krall on 2020-05-27
Thanks 'oldfred'... Thanks 'Dennis N'...

I think I'm coming clearer on this... lots of reading tonight. 
-----------------------------------------

There won't be any Windows 7. Will put in Linux Lite, then Ubuntu MATE... both /, /home and a swap partition.  Will GPartEd all the partitions from Linux Lite, then install it... then, etc. 

In the Belarc Advisor Report, besides "*Boot Mode: Legacy BIOS in UEFI (Secure Boot not supported)*", I saw this :  "*UEFI: Insyde Corp. 1.50 11/23/2011*"  The Win. 7 is definitely partitioned MBR... Windows says so... GParted says so...  "sudo parted -l"says so.  There is NO CSM/Legacy switch in BIOS/firmware... I've looked and looked.  I'm wondering, if Windows weren't in the machine, if it becomes a GPT/UEFI set up.  A mention by 'oldfred' in one of the links given speculates a thing like that... a switch.  

With MBR partitioning...  1-2 MiB boot_grub... extended... /... /... swap... /home... /home

Could leave 'unallocated' of size for EFI_boot between boot_grub and extended... could just make the EFI_boot partition in that position and let the OS-es sort it out.  Potential problem I see with that is Linux Lite is not "modern" with GPT/UEFI.  They have two different install versions... most up to date (4.8) is MBR... If a person needs to do GPT/UEFI, the procedure is to install 4.2, then immediately run an upgrade to 4.8.  The upgrade is more a big version change rather than say, an Ubuntu 16 to Ubuntu 18 upgrade.  At the end of which Linux Lite is then fine with UEFI.     

Seems like going the BIOS/GPT route with the 'unallocated' space is sounder right now.  I'll be doing upgrades in less than a year... about when Ubuntu MATE 18.04 looses support (and about when 20.04 will be 20.04.1 or .2) and Linux Lite has some time in with it's Ubuntu 20 base.  May have to redo to UEFI then, but ???.  

Mike

---

### Post by oldfred on 2020-05-27
I would check if you have a UEFI/BIOS update.
Often the early UEFI implementations needed updates as vendors were also fixing things.

If not an gpt drive, you have to in gparted choose to change it. That will totally erase drive.
You can also use gparted but must change default partitioning first.
Select gpt under device, advanced over msdos(MBR) default partitioning before starting.

If data is well backed up, but you want to keep a partition, you can convert MBR to gpt.
Converting to or from GPT - must have good backups.
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

---

### Post by Mike Krall on 2020-05-27
> **oldfred said:**
> [COLOR="#0000CD"]I would check if you have a UEFI/BIOS update.
Often the early UEFI implementations needed updates as vendors were also fixing things.[/COLOR]

If not an gpt drive, you have to in gparted choose to change it. That will totally erase drive.
You can also use gparted but must change default partitioning first.
Select gpt under device, advanced over msdos(MBR) default partitioning before starting.

If data is well backed up, but you want to keep a partition, you can convert MBR to gpt.
Converting to or from GPT - must have good backups.
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

I seem to get confused easily...

[COLOR="#0000CD"]Blue[/COLOR]:  I've checked every way I could find... looking at firmware and available updates... Windows in Windows... Windows in Linux.  Not seeing UEFI/BiOS update.  Windows (Disk Management...Disk 0... only one disk) won't let me convert to GPT and that is just one Windows in Windows approach with that conclusion. 

I understand I can maybe do this through GPartEd (or possibly your link to Rod Smith... he's always tough for me to follow... get left in the dust a lot).  I'll try going to GPartEd site and see what they say about step-by-step to convert.

Still have this nagging wonder if somewhere in this mid-2012 machine is an inherent lock to MBR and/or ???  Wonder if Belarc Advisors "Secure Boot Not Supported"  is an indication of this.

Thanks 'oldfred'...  

Mike

---

### Post by oldfred on 2020-05-27
Windows 7 supports UEFI, but does not support UEFI Secure Boot.

You can look into your UEFI/BIOS and see version number, then look online for your vendor's support site and see if there is an update. Since pretty old, it may not have a recent update, but may have something newer with some fixes.

Attached some old screen shots from gparted. Newer will look a bit different, but is same function.
You have to click on device at top menu first, before anything else and choose gpt. With small drives it defaults to MBR. Installer in BIOS mode defaults first to whatever drive is, and uses MBR if smaller drive in BIOS mode.
In UEFI mode it uses gpt, unless drive is MBR. It really should not allow UEFI on MBR drives, but does.

---

### Post by Dennis N on 2020-05-27
> I've checked every way I could find... looking at firmware and available updates... Windows in Windows... Windows in Linux. Not seeing UEFI/BiOS update. 
Did you try Google? "Toshiba Satellite L750D bios updates" - First hit shows there is a version 2.10 bios update 6/28/2012.
Download here:
[https://support.dynabook.com/support/viewContentDetail?contentId=3413451](https://support.dynabook.com/support/viewContentDetail?contentId=3413451)

Good luck upgrading the bios.

---

### Post by Mike Krall on 2020-05-28
> **oldfred said:**
> You can look into your UEFI/BIOS and see version number, then look online for your vendor's support site and see if there is an update. Since pretty old, it may not have a recent update, but may have something newer with some fixes.

UEFI: InsydeH2O System BIOS version 1.50 (EC version 1.30) 11/23/2011... [https://support.dynabook.com/support/viewContentDetail?contentId=3461141]("https://support.dynabook.com/support/viewContentDetail?contentId=3461141")

Pretty well don't know what I'm looking at in the various version updates.  Seeing only one thing in all (Version 2.10 - 2012-06-28)... "Added Windows 8 support" possibly have some impact... like maybe getting a 'Secure Boot' switch...  =]

I can tell you, I've got a rationalized irrational aversion to the idea of updating BIOS... like, it ain't broke.  I will take help given, though... 'cause I asked for it.  What do you think 'oldfred'?  

Mike

---

### Post by oldfred on 2020-05-28
I always suggest updating UEFI/BIOS.
Just make sure you are not using just battery power if laptop, nor in middle of thunderstorm. Any power interruption can cause a major issue.

There are a few cases where someone "bricked" their computer, but I never have seen it.
There was a issue with one vendor where UEFI had major issue, blamed on Linux but was vendor's UEFI that bricked system when UEFI internal memory was over 50% full (too many boot entries).

---

### Post by Mike Krall on 2020-05-28
Last night I didn't realize this thread had turned another page and missed 'Dennis N' post.  His link and mine are different by one version upgrade.  I'm figuring I'll put in the newest... 2.10, given the download page headings are the same  Stop me quick if I'm about to step on myself...  =] 

Edit:  After I update the BIOS, I'll F2 into it and see if I find differences.  I've got a pretty complete map of the current version.

Edit2:  Downloaded ver. 2.10... then ver. 2.00... then ver. 1.50.  Opening in Windows 7 the first two show for Toshiba Satellite L755/L755D.  Only ver. 1.50 download says [COLOR="#B22222"]L750D[/COLOR]/L755D. Version 1.50 is in this machine now.  Yeah, I know, just do it.  Still... looks to me like *don't.*  Your view?

Edit3:  OK... went to Toshiba. Ran s/n in download search function. Version 2.10 not in list.  Ran into discussion on this... that if a person runs the model number, they may end up with ???  The serial number pretty well locks it to THIS machine.  I'm going to miss not having a "secure boot" switch with ver. 2.10's "Windows 8 support")...  =[

Edit4:  Well, that's done... ver. 2.00 and the BIOS set up is as identical as I can remember.  Anyone think I ought to put in ver. 2.10? It IS listed in official Toshiba/dynabook for the model?  Is this where people get in binds?  =]

Edit5:  [https://en.wikipedia.org/wiki/Curious_George]("https://en.wikipedia.org/wiki/Curious_George")

Edit6:  I hate stuff like this:  Looking at actual download... ver. 2.10. Has Instruction sheet... > ACPI Flash BIOS version 2.10 for Satellite L750D/L755D )PSK32*/PSK36U
This BIOS is applicable to the following models:
* Satellite L750D/L755D models having part numbers beginning with "PSK32U"
* Satellite L755/L755D models having part numbers beginning with "PSK32M"
[COLOR="#FF8C00"]For purposes of this document, the term **Satellite L755/L755D** is used to generically refer to all of the models listed above.[/COLOR]
The model is an L750D - PKS32U. So version 2.10 is almost for sure, probably OK...  =] =[ 

Mike

---

### Post by Dennis N on 2020-05-29
>  Anyone think I ought to put in ver. 2.10? It IS listed in official Toshiba/dynabook for the model? Is this where people get in binds? =]
I've only updated a BIOS (or UEFI firmware) a couple of times. In those cases, there was a specific issue the upgrade fixed. Otherwise, if there was no problem that affected my computer to fix, I passed on the available upgrades.
-------------------------------------------
Example: on my 2014 Asus H97 system, an upgrade was needed in order to get full NVMe support (like booting from such a drive).

(Old upgrades with BIOS machines were more of a hassle. I recall having to use FreeDOS to access and apply the update file. With the Asus H97, there is a built in UEFI utility that took care of it.)

Oh - Did the upgrade fix your problem?

---

### Post by Mike Krall on 2020-05-29
> **Dennis N said:**
> I've only updated a BIOS (or UEFI firmware) a couple of times. In those cases, there was a specific issue the upgrade fixed. Otherwise, if there was no problem that affected my computer to fix, I passed on the available upgrades.
-------------------------------------------
Example: on my 2014 Asus H97 system, an upgrade was needed in order to get full NVMe support (like booting from such a drive).

(Old upgrades with BIOS machines were more of a hassle. I recall having to use FreeDOS to access and apply the update file. With the Asus H97, there is a built in UEFI utility that took care of it.)

[COLOR="#0000CD"]Oh - Did the upgrade fix your problem?[/COLOR]

Didn't have a problem, 'Dennis N'...  'oldfred' made me do it...  =]  

And now I'm waiting to see if 'oldfred' thinks I ought to *"in for a penny, in for a pound"* and put in ver. 2.10 ([https://support.dynabook.com/support/viewContentDetail?contentId=3461141]("https://support.dynabook.com/support/viewContentDetail?contentId=3461141")).  If asked to describe advantage of end result, I'd have to say it will facilitate GPT partitioning with Windows 7 gone... further details not forthcoming (not from me, anyhow).

One thing about Windows... they do diapers... decades long of little step, by little step though every and all processes.  The BIOS update adhered to the form. 

Mike

---

### Post by oldfred on 2020-05-29
I  thought you were updating to the newest. 
I often have skipped multiple versions as I had not checked for a while and vendor put out multiple updates in a short time.

UEFI/BIOS issues are not always on like of fixes. 

But I used gpt on a BIOS only system from 2006 (in 2010). I believe back then were were some BIOS that had issues with gpt on flash drives, but I never had an issue. Since gpt has a protective MBR (to prevent old MBR tools from erasing a drive), I do not know how BIOS would care as all it really does is look for a MBR and then toss booting into that MBR.

---

### Post by Mike Krall on 2020-05-30
There are the two sides of BIOS updating...

1)  "If it ain't broke, don't fix it".  There is a risk.  Is there a problem?  If you don't know, there isn't.  Is there a gain?  If you don't know, there isn't.

2)  "It's just parts."  There's baseline stuff that can be better... some is actually wrong.  It's just like a "recall"... your windshield wipers will work better and/or won't quit you in the middle of the heaviest ("worst", or not) summer rain in decades (rush hour traffic at 75+ mph).  Why would you ever think of not? 

Have I got that right?
--------------------------------------------------------  

*  dynabook BIOS update downloads.  Version changes.
> Change History
---[COLOR="#0000CD"]Version 2.10[/COLOR] - 2012-06-28
---Added: Windows 8 support
---Fixed: HWID cannot be read in Fast Boot mode.
---EC V1.80: Added SMBus deadlock protection.

I've been looking into things...

This looks like a good idea...
"SMBus deadlock protection"... no returns... "prevention", yes... down page... [https://en.wikipedia.org/wiki/Deadlock]("https://en.wikipedia.org/wiki/Deadlock")
And for a "simple" understanding of SMBus... [http://www.ti.com/lit/an/slua475/slua475.pdf?ts=1590810620007]("http://www.ti.com/lit/an/slua475/slua475.pdf?ts=1590810620007")

This looks irrelevant to "No Windows". Also looks... well... OK, no comment...
[https://www.webopedia.com/TERM/H/HWID.html]("https://www.webopedia.com/TERM/H/HWID.html")

For the life of me I cannot find reference to what is changed in BIOS constituting "*Added: Windows 8 support.* I've been at this awhile.  There's little sense in running  a list of speculations.  At end, and in view of what I'm doing here (yeah, I need to look down the road too), the only things I can cleanly say are... will this help?... will this hurt?... is this irrelevant?  Answers:  **None**

It has gone late... I'm done. 

Mike

---

### Post by Dennis N on 2020-05-30
> I've been looking into things...
I think you're getting too deep into the weeds. Come back before it's too late. SMBus? I've never heard of it. I would leave that stuff to the Designers and IT pros.

---

### Post by Mike Krall on 2020-05-30
> **Dennis N said:**
> I think you're getting too deep into the weeds. Come back before it's too late. SMBus? I've never heard of it. I would leave that stuff to the Designers and IT pros.

Was my conclusion, too!  

Had seen SMBus before.  Left it lay then...  operating on "need to know" principal (simple switch: yes or no... no dithering... no hedging... go or not).  I only went into it to get a quick idea on it's aspect in version update... good, bad, indifferent.  So, there's a level of "not function as well as liked" in some aspect of SMBus in BIOS, and the version update is looking to make that better (not to say "perfect" because it doesn't look like SMBus is one of those things having a 'final answer' in any given complexity... maybe in a specific simplicity, though).

I guess I'll look a little more at the "Added: Windows 8 support".  Figuring I'll only lay new tracks on top of old tracks, but a person never knows.  Someone out there has talked about it. Finding (figuring out how to find, really) is always tough for me. 

Mike

---

### Post by oldfred on 2020-05-30
Do not know for sure, but Windows 8 was the first with UEFI Secure Boot.
Many UEFI/BIOS have setting that says "Windows" or "Other", others have UEFI Secure Boot on or off.
The one's using "Other" type setting have fine print somewhere that says if booting Windows 7 in UEFI mode, use "Other". Windows 7 does not support UEFI Secure Boot that started with Windows 8 in 2012.

I have seen a lot of reasons to just update UEFI. Not specifically your model.  But a couple of examples on why you typically do want to update.

Last year AMD put out a fix that was required for Linux to work. But motherboard vendors had to push out new UEFI updates with that fix.
AMD UEFI/BIOS update for Ryzen 3000 series
[https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-3000-BIOS-Update-Good](https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-3000-BIOS-Update-Good)
ASUS ROG CROSSHAIR VIII HERO WiFi - update supports Ubuntu 19.04
MSI has also put out BIOS updates in Aug as a "beta" though without explicitly acknowledging the Linux fix. 

This would not apply to your older cpu, as it does not speculate.
And almost all newer cpu including your Raspberry Pi and IBM mainframe that speculate on what next bit of code will be and load it into RAM before needing it,  have needed UEFI updates. And Both Linux & Windows updated operating systems, also.
Almost all systems need UEFI updates, anyway, for mitigation of Meltdown and Spectre CPU vulnerabilities from cpu speculative execution and caching. 
Ubuntu 18.04 LTS has the Linux 4.15 kernel, GNOME Shell 3.29.1, Mesa 18.0-rc5, GCC 7.3.0, Python 2.7.15rc1, Python 3.6.5, and is mitigated for Meltdown with KPTI while for Spectre V1 it opts for __user pointer sanitization over OSB and for Spectre V2 has full Retpolines. 

Or there are a lot of things in background going on, and not everyone knows all the details.

---

### Post by Mike Krall on 2020-05-31
> **oldfred said:**
> Do not know for sure, but Windows 8 was the first with UEFI Secure Boot.
Many UEFI/BIOS have setting that says "Windows" or "Other", others have UEFI Secure Boot on or off.
The one's using "Other" type setting have fine print somewhere that says if booting Windows 7 in UEFI mode, use "Other". Windows 7 does not support UEFI Secure Boot that started with Windows 8 in 2012.

[COLOR="#0000CD"]Or... there are a lot of things in background going on, and not everyone knows all the details.[/COLOR]

Thank you 'oldfred'... I've got a working view now.

So I put in ver. 2.10.  Did not come into proud ownership of a new brick.  Pretty sure there are no differences in the BIOS pages. Did not acquire either a 'Secure Boot' switch or 'Windows'/'Other' choice.  And *still* did not find discussion of what constitutes "Windows 8 Support" for changes to a Windows 7 machine.  But I AM happy with my SMBus reordering...  =]  

Wondering a thing... I've come across folks having troubles with getting up and running with Linux (different manufacturers and BIOS related) where a solution was found having put password(s) into BIOS...  seemingly needing 'Supervisor/Administrator'... if I'm remembering well.  Under *BIOS Password* I've got 'User' and 'Supervisor' ('Not Registered' --set to now-- or a password entry area for each).  Under *HDD/SDD Password* there is 'Mode' (User Only or User+Master) with User below ('Not Registered' --set to-- or a password entry). Is this a 'Do it when/if' thing... or ???  And just thought that last maybe only has relevance if Windows is in the machine... 

Mike

---

### Post by oldfred on 2020-05-31
Acer for one, has the UEFI password to get more settings and allow "trust". It seems to be the only one that works well, but requires user to trust a new UEFI entry.
Most of the UEFI have password so you cannot change settings for security reasons. Anyone with physical access to a system then can compromise syste. With UEFI Secure boot, no boot from USB or external devices set in UEFI, and UEFI password, so you cannot change those settings, you can have a pretty secure system.

I do not set a UEFI password on my systems which are desktops, so security a bit less critical as always in office at home.
We do see multiple cases of users who say they forgot UEFI/BIOS passwords. Hope they are not breaking into someone else's system and have really just forgotten UEFI password. It is one password if set you cannot forget.

---

### Post by Mike Krall on 2020-05-31
> **oldfred said:**
> Acer for one, has the UEFI password to get more settings and allow "trust". It seems to be the only one that works well, but requires user to trust a new UEFI entry.
Most of the UEFI have password so you cannot change settings for security reasons. Anyone with physical access to a system then can compromise syste. With UEFI Secure boot, no boot from USB or external devices set in UEFI, and UEFI password, so you cannot change those settings, you can have a pretty secure system.

I do not set a UEFI password on my systems which are desktops, so security a bit less critical as always in office at home.
We do see multiple cases of users who say they forgot UEFI/BIOS passwords. Hope they are not breaking into someone else's system and have really just forgotten UEFI password. [COLOR="#0000CD"]It is one password if set you cannot forget[/COLOR].

Thanks for all, 'oldfred'. 

[COLOR="#0000CD"]Blue[/COLOR]:  Yeah, so I write them down.  The "then what" is coming... when I can't remember where the paper is.  Seemingly no solution when the access to passwords requires passwords point is reached. 

Mike

---

### Post by oldfred on 2020-06-01
I had in middle of ring binder of other things, a page with passwords, but just scribbled all over. Got to point I could not read my own notes on passwords & phrases.
I now use keypassx or keepassXC. Only have to remember one password & it lets me copy & paste passwords. Most sites work with auto entering the username & PW if cursor on correct field.

---

### Post by Mike Krall on 2020-06-02
> **oldfred said:**
> I had in middle of ring binder of other things, a page with passwords, but just scribbled all over. Got to point I could not read my own notes on passwords & phrases.
I now use keypassx or keepassXC. Only have to remember one password & it lets me copy & paste passwords. Most sites work with auto entering the username & PW if cursor on correct field.

Thank you 'oldfred'... I'll try to remember that.  I need to do something before I can't remember I need to...  
------------------------------------------------------------

I've been reading.  Trying to come to a working understanding of BIOS/UEFI... MBR/GPT (I thought I had things fairly straight from the /mnt/data thread... not really).  Why?  Well, I really never know why.  I'll get over it.  

Here are things I feel I do understand.  The machine's firmware is BIOS, not UEFI.  The machine's partition table is MBR, not GPT.  The two Linux installs need a MBR partition table.  To run GPT the tricking ("not caring", I think you said) happens at /dev/sda1... small space... 1 - 2 MiB... boot_grub... unformatted.  

Then on... mindful of needing an extended partition at some point (thinking /dev/sda2) because of 2x /,   'swap',  and 2x /home.
------------------------------------------------

Because of Belarc Advisor scan:  1) * Boot Mode:  Legacy BIOS in UEFI (Secure Boot not supported)*...and...  2) Under *'Main Circuit Board':  UEFI: Insyde Corp. 1.50* (now 2.10).  Thought down the road might be switching disk... might be needing ESP partition... might be 'who knows'.   Based on that, thought to leave 512 to 1024 MiB unallocated after /dev/sda1 (maybe just have /dev/sda1 be that size), and make 4096 MiB at disk end (I like the look of the number).

Also... because not doing MBR... and likely solidity of Ubuntu MATE 'GPT aware'... it seems like I ought to install it first (all OS partitions made with GPartEd prior).  Maybe that helps putting in Linux Lite and avoiding potential problems. 

Anyhow... didn't need to do all that yapping.  Taking a break from reading / searching. 

Mike

---

### Post by oldfred on 2020-06-02
I am to the point of saying only use MBR if you must boot Windows in BIOS mode on same drive. Otherwise use gpt.
I have used gpt since 2010. Time for MBR to go away.

Most vendors call UEFI as BIOS. Since 2012 Microsoft required vendors to install Windows 8 in UEFI mode on gpt drives. So if system newer than 2012, it really is UEFI. UEFI currently has CSM.
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

MBR has the four primary partition limit and often uses the extended partition to hold logical partitions.
Gpt has a 128 partition soft limit. User can change that (no idea how, and never seen anyone require it). Then all partitions are in effect primary.

Links to lots more info at end of my post in link in my signature below.

---

### Post by Mike Krall on 2020-06-02
> **oldfred said:**
> I am to the point of saying only use MBR if you must boot Windows in BIOS mode on same drive. Otherwise use gpt.
I have used gpt since 2010. Time for MBR to go away.

Most vendors call UEFI as BIOS. Since 2012 Microsoft required vendors to install Windows 8 in UEFI mode on gpt drives. So if system newer than 2012, it really is UEFI. UEFI currently has CSM.
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

MBR has the four primary partition limit and often uses the extended partition to hold logical partitions.
Gpt has a 128 partition soft limit. User can change that (no idea how, and never seen anyone require it). Then all partitions are in effect primary.

Links to lots more info at end of my post in link in my signature below.

I knew better than to do 'random yapping' last night... did it anyhow. 

I know better than to read a reply a couple of times and reply back quickly... doing it anyhow.

There's a thing I must not understand... like I'm seeing a thing you and others have said (GPT, etc.) upside down... or backwards... or have (incorrectly) this-before-that... or have not picked up one or more pieces necessary to picture... or ???
---------------------------------------------

There will be no Windows 7, therefore I will '*use GPT*'. Not looking to do otherwise.  

The **only** step I see that I *think* is '*use GPT*' is...   [COLOR="#0000CD"]/dev/sda1...  1 - 2 MiB...  unformatted... bios_grub flag[/COLOR].  Past that point, all I know is, I'm wrong. 

I'm not arguing 'oldfred'... I just don't get it.

Mike

---

### Post by oldfred on 2020-06-02
I use gparted on a new drive or when totally repartitioning & reformatting a drive (erasing it).
First thing is to select gpt under devices in top bar and change default from MBR to gpt. It only uses gpt for drives over 2TB or installers default to gpt if drive is blank and installing in UEFI boot mode. Ubuntu lets you install in UEFI boot mode to MBR drives. And does not seem to let you choose gpt if installing in BIOS mode.

So you have to partition in advance.
I now create both ESP & bios_grub but only really need one or the other. Originally had BIOS, so had to have bios_grub partition, but then thought I may move drive to a newer UEFI system so create booth. Now having UEFI systems, I just create ESP.

The bios_grub is a tiny 1 or 2MB unformatted partition anywhere in the first 2TB of a drive. I normally make it first, so out of way. You right click in gparted to assign the bios_grub flag.
Old screen shots but still the same with new graphics.

---

### Post by Mike Krall on 2020-06-03
> **oldfred said:**
> I use gparted on a new drive or when totally repartitioning & reformatting a drive (erasing it).
First thing is to select gpt under devices in top bar and change default from MBR to gpt. It only uses gpt for drives over 2TB or installers default to gpt if drive is blank and installing in UEFI boot mode. Ubuntu lets you install in UEFI boot mode to MBR drives. And does not seem to let you choose gpt if installing in BIOS mode.

So you have to partition in advance.
[COLOR="#0000CD"]I now create both ESP & bios_grub but only really need one or the other[/COLOR]. Originally had BIOS, so had to have bios_grub partition, but then thought I may move drive to a newer UEFI system so create booth. Now having UEFI systems, I just create ESP.

The bios_grub is a tiny 1 or 2MB unformatted partition anywhere in the first 2TB of a drive. I normally make it first, so out of way. You right click in gparted to assign the bios_grub flag.
Old screen shots but still the same with new graphics.

Thanks 'oldfred'...

[COLOR="#0000CD"]Blue[/COLOR]: I'd like to be sure I understand.  My read is:  Both get created, but you could just create one or the other.  If I'm understanding... they are both there but the OS finds the one it needs... that, it doesn't see the other... and...  if just creating one, it would be for the machine type?  (In my case bios_grub)? 

If I have that right... 

It's really unlikely the drive would move.  Are there other reasons a person would want to create both bios_grub... unformatted and /boot/efi... unformatted in the GUID partition table?  

Mike

---

### Post by Dennis N on 2020-06-03
The only time you need to include the 1-2 MB unformatted bios grub partition is on a GPT- partitioned drive in a BIOS computer on which you are going to install a grub bootloader. If it's a GPT-partitioned data-only drive in the BIOS computer, you don't need it.

---

### Post by oldfred on 2020-06-03
Dennis is correct, you do not even need either ESP or bios_grub on a data only drive.
Its just I have no data only drives. Or even if planned now to be data only, I may want a system on drive later.
With new drive sizes, both ESP & bios_grub are tiny.

Installer will not create both, but if installing in UEFI mode it will use ESP for UEFI boot. If installing in BIOS boot mode on a gpt partitioned drive, it will use bios_grub. If drive is pre-partitioned, it may not add partition or if install is to sdb or external drive it may look for ESP or bios_grub on first drive and then throw error that it cannot install grub.
I put both on for years as I was converting from BIOS to UEFI and thought I may move a drive from one system to another.

Some reasons to have a system on every drive.
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and keep a current testing one on every drive, but smaller partition if just for emergency boot.

---

### Post by Mike Krall on 2020-06-04
> **oldfred said:**
> Dennis is correct, you do not even need either ESP or bios_grub on a data only drive.
Its just I have no data only drives. Or even if planned now to be data only, I may want a system on drive later.
With new drive sizes, both ESP & bios_grub are tiny.

Installer will not create both, but if installing in UEFI mode it will use ESP for UEFI boot. [COLOR="#0000CD"]If installing in BIOS boot mode on a gpt partitioned drive, it will use bios_grub.[/COLOR] If drive is pre-partitioned, it may not add partition or if install is to sdb or external drive it may look for ESP or bios_grub on first drive and then throw error that it cannot install grub.
I put both on for years as I was converting from BIOS to UEFI and thought I may move a drive from one system to another.

Some reasons to have a system on every drive.
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and keep a current testing one on every drive, but smaller partition if just for emergency boot.

[COLOR="#0000CD"]Blue[/COLOR]:  The second Linux installed will use the bios_grub also?  That is, will find it and use it?

Why the note about Knoppix, 'old fred'?  I looked at the link, then a few other references.  Do you have Knoppix on every drive?  To what purposes? 

Mike

---

### Post by mastablasta on 2020-06-04
> **Mike Krall said:**
> [COLOR=#0000CD]Blue[/COLOR]:  The second Linux installed will use the bios_grub also?  That is, will find it and use it?

Why the note about Knoppix, 'old fred'?  I looked at the link, then a few other references.  Do you have Knoppix on every drive?  To what purposes? 

Mike

he says it in the end:
> [COLOR=#000000]*Except I have multiple Ubuntu installs and keep a current testing one on every drive, but smaller partition if just for emergency boot.*[/COLOR]

in multidisk system this might not be such a bad idea. if one disk fails you can just use thew other drive to restore it or save it. not sure how you would keep them all updated. or would they be just live session?!?! hmm...

---

### Post by TheFu on 2020-06-04
For my "save my butt" needs on physical computers, I just boot from a flash drive with a recent Ubuntu-Mate on it.  Since I'm an LTS-only guy, that means 16.04 almost always.  For virtual machines, I'll just connect up the ISO file to the VM and have it boot that for any "butt saving" needs.

I find this pretty easy since over the years a few vendors have been giving away 8G flash drives that always boot on all my devices. They have a unique graphic on the outside, so it isn't hard to know which to use compared to the other flash storage or SDHC media.  Just grab the one with green and boot.  When it seem old, I'm not afraid to slap a new ISO onto it using ddrescue.  Lots of people are afraid of dd/ddrescue, but I'm not. Every Unix OS has it. Quick an easy.  Used it 4 times yesterday to play with 4 different OSes on some new router hardware.

I've read that some people like to keep a 2nd minimal Ubuntu to boot that has backup tools like fsarchiver and LVM already installed. I suppose if downtime for backups and manually backup effort is fine, great.

---

### Post by Dennis N on 2020-06-04
> Blue: The second Linux installed **will use the bios_grub also**? That is, will find it and use it?
They don't both use it. The MBR (+bios grub partition) is only used by one OS - the one that boots on startup and presents the grub menu. Any other OSes started from the grub menu don't need the MBR+bios-grub at all.

---

### Post by Mike Krall on 2020-06-04
'mastablasta'...

> **mastablasta said:**
> he says it in the end: > Except I have multiple Ubuntu installs and keep a current testing one on every drive, but smaller partition if just for emergency boot.

I see it now... 'oldfred' system already has function equivalent... thank you for setting it so I could see it. 

Mike

---

### Post by Mike Krall on 2020-06-04
> **Dennis N said:**
> They don't both use it. The MBR (+bios grub partition) is only used by one OS - the one that boots on startup and presents the grub menu. Any other OSes started from the grub menu don't need the MBR+bios-grub at all.

Thanks 'Dennis N'... another picture piece.

Mike

---

### Post by Mike Krall on 2020-06-05
I found this in the morning...  [https://help.ubuntu.com/community/DiskSpace]("https://help.ubuntu.com/community/DiskSpace")  Wish it had been in the BIOS/UEFI folder.  It always helps me to hear a same (or nearly) thing in a different place, or in different words... makes dimensional for me some how... seeing a thing from a different point of viewing.  

I've also spent some time at GPartEd.org.  In the FAQ's there is this... #7...  > Is there a maximum to the amount of operations in the list?

Nope, that is, not one an ordinary human being will ever reach.
I myself tested it with up to 150 operations and it went smoothly.

[COLOR="#0000CD"]HOWEVER, I think it's wise to keep the amount of succesive operations limited. After all it's your data which is at risk.
Especially when doing complex operations (copy,resize) I advise you to take it one step at a time.[/COLOR]

When resizing boot NTFS partitions, it is advisable to perform this as a single operation only. After resizing, boot into Windows twice to allow Windows to perform its checking operations.

I understand what I'm doing here is *not* a complex operation.  I think doing one thing at a time might let me see things better... maybe keep my view focused... who knows.
----------------------------------------------------------

I'm going to boot the Live Ubuntu-Mate USB and 'Create a New Partition'... flip box from MSDOS to GPT ... and apply it.  Figured I'd ```
# fdisk -l
``` afterwards.  I think that will show me if the disk is GPT.

I still don't know just how I'll set the partitions for the 2 Linux OS... swap...  and 2 /home... space at end... other unallocated (maybe a /boot/efi instead for some of it).  I mean, in the end, there's no telling what would be handy to have done when it was easy.

I guess I don't need to say... the reason for 2 /home's instead of a shared /home...  Down the road I think one or the other (or some other) OS will be chosen.  A person could then just switch to a single OS easier (I think).  I looked around a fair amount for undoing shared /home and didn't come up with anything.  Couldn't even get a vague view of why there was little to no information (aside from me being a consistently lame searcher). 
-----------------------------------------------------------------

Yup... it's a GPT disk...  =]   That took a lot of work, didn't it 'oldfred'...

Mike

---

### Post by Mike Krall on 2020-06-05
I meant to ask and forgot...

If putting in /boot/efi partition, I thought it to be unformatted also.  But it's not that way in my UEFI/GPT machine... Fat 32...  /boot/efi mount point.  Should be I'd do it the same as... but there is no telling if I've missed another thing.

Mike

---

### Post by TheFu on 2020-06-05
The EFI partition will be FAT32. That is required, part of the EFI standard.  I don't know if you have to format it or not.  I never have.

---

### Post by oldfred on 2020-06-05
In post #24 I posted my partitions. They show FAT32 for ESP.

I typically partition & format in advance, but using Something Else you can do it during install. Its just installer will not let you change to gpt with a BIOS install, but will install in BIOS if you have a bios_grub partition.

There are 100's of posts on partitioning. Almost all on dual booting Linux will say not to share /home.
I now suggest keeping /home inside / (root) as it really is small and mostly hidden files, its your data that is large. So then have a separate data partition or two and mount that in every install. Firefox & Thunderbird can be somewhat larger also and are in hidden folders in /home. But I have always moved those to my data partition also as way back with XP I shared them between XP & Linux. I was trying to learn Linux & my wife complained about having to reboot into XP to see email.

---

### Post by TheFu on 2020-06-05
> **oldfred said:**
> In post #24 I posted my partitions. They show FAT32 for ESP.

I typically partition & format in advance, but using Something Else you can do it during install. Its just installer will not let you change to gpt with a BIOS install, but will install in BIOS if you have a bios_grub partition.

There are 100's of posts on partitioning. Almost all on dual booting Linux will say not to share /home.
I now suggest keeping /home inside / (root) as it really is small and mostly hidden files, its your data that is large. So then have a separate data partition or two and mount that in every install. Firefox & Thunderbird can be somewhat larger also and are in hidden folders in /home. But I have always moved those to my data partition also as way back with XP I shared them between XP & Linux. I was trying to learn Linux & my wife complained about having to reboot into XP to see email.

Oldfred, putting data on a data partition used to be workable, before snap packages. Now that snaps don't allow access outside of HOME, what do you do?

---

### Post by CelticWarrior on 2020-06-05
> **TheFu said:**
> Oldfred, putting data on a data partition used to be workable, before snap packages. Now that snaps don't allow access outside of HOME, what do you do?

They do provided users enable such access. It works for anything mounted in /media or /mnt. Are you planning to mount data partitions anywhere else and if so, why?

---

### Post by TheFu on 2020-06-05
> **CelticWarrior said:**
> They do provided users enable such access. It works for anything mounted in /media or /mnt. Are you planning to mount data partitions anywhere else and if so, why?

The Linux File System Hierachy Standards are pretty freakin' clear.  
   [https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

> **The /mnt/ directory** is reserved for _temporarily mounted file systems_, such as NFS file system mounts. For all removeable media, use the /media/ directory. 

> **The /media/ Directory**
The /media/ directory contains subdirectories used as mount points for _removeable media_, such as 3.5 diskettes, CD-ROMs, and Zip disks. 

We have permanent storage, shared by groups of users. Some is locally RAID1 connected and some is NFS.  
Snaps don't work if your HOME is NFS mounted or for any NFS storage. The problem has been known since at least 2017.

If I wanted to be forced to setup a computer a specific way, I'd run OSX.

---

### Post by oldfred on 2020-06-05
First thing I do is uninstall all snaps and install synaptic, so I get .deb versions.

I used to like to have both Firefox & Chromium, but now do not have Chromium as it is only officially a snap. Have not tried the ppa yet.
Noticed that Mint not using snaps either.

---

### Post by TheFu on 2020-06-05
Ah.  You can run the chromium that is part of the snap install directly, without using the snap wrapper.  I haven't figured out how to wrap it in **firejail** for my preferred constraints yet. 

The chromium browser team has an annual habit of doing something deep in the kernel namespace capabilities to provide more security to their application, that happens to break any outside sandboxing.  So the snap and chromium developers working with that does have an upside, provided we don't want to load local HTML presentation files from storage outside our HOME or other places where snaps don't work.

---

### Post by Mike Krall on 2020-06-06
Couldn't post this morning.... last night's info.  

Once I got clear on using GPartEd to 'Create Partition Table'... directing it to be a GPT... the rest of everything fell into place.  Made 'bios_grub' area as mentioned, then ESP, then /, swap, /home, /, /home with bigger than necessary space at table end... only to find afterwards what looked like disk end wasn't, so now there is a 'more bigger' unallocated space at end-disk.  Why does that happen, I ask rhetorically.    

Both Ubuntu-MATE and Linux Lite run fine... get a boot menu for choice...  last in, Linux Lite, is now in first place and listed as 'Ubuntu'... "same as it ever was"... I started to head to 'efibootmgr' (that ain't going to work so I've got a little project).  

There's one oddity noticed... not looking to get into it here... but I'll mention it because maybe someone knows the simple answer.

**/etc/default/grub**...  both OS are 'Ubuntu'.  Linux Lite... second Install... first in GRUB startup menu... GRUB_TIMEOUT=10.  Ubuntu Mate... installed first... now second in GRUB menu...  GRUB_TIMEOUT=0

I've looked here to start...  [https://www.gnu.org/software/grub/manual/grub/html_node/Simple-configuration.html#Simple-configuration]("https://www.gnu.org/software/grub/manual/grub/html_node/Simple-configuration.html#Simple-configuration")

Mike

---

### Post by oldfred on 2020-06-06
Do not know why you would have 0 for grub timeout.
I normally change default 10 to 3, so I have some time to press a key but not a lot so boot a few seconds faster.
At 0 you do not have time to press a key and if you need to get into grub menu, it can be difficult or impossible.

Last install will be first in grub boot order.
But with multiple installs, a major grub update will reset that install to first. So you have to manage your grub.
I prefer to turn off os-prober and add my own grub stanza into 40_custom.

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config](https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

This thread is even longer than your threads. :)
Best to review first page then jump to end & work backwards as newest info is at end.
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

---

### Post by Dennis N on 2020-06-06
> Do not know why you would have 0 for grub timeout.
I think Ubuntu MATE was installed first and was the only OS present at the time. In that case GRUB_TIMEOUT is being set to 0. See the default settings for MATE 20.04 from my recent install:
```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```
(This was a UEFI install.)
As you say, maybe not the best choice for a default OS. If it's not the default, it wouldn't matter what the value is.

---

### Post by Mike Krall on 2020-06-06
'oldfred'...  

*  I think I'll be able to manage this machine using 'enough time to see and pick' at the GRUB menu. I'll be on this computer for a while, so I'll find "annoyance" if it's there. 

*  CavsFan... and still going...  =]  I've not been to "Maintenance Free" in a long time now.  I read almost all of it back in time (just caught up this morning).  Why?  Well, because it's there I guess.

*   Thanks for the GUB2 section, 'oldfred'... it's a nice, clean piece. 
-------------------------------------------------------------------------

"Dennis N"...

I felt there should be a simple answer to GRUB_TIMEOUT=0... thank you.  I'll get changes done tonight.
-----------------------------------------------------------------------------

I guess this is "Solved" now and I'll edit it to that........................... right after........

* Because it came up, I dabbled at skim on "snap, snaps, snapd" last night.  Ran into a short piece at Arch Wiki.  Came away with the impression of negatives... could easily be incorrect "reading into", though. Do any of "all-yawl" have links to (or things to say on) what you feel as pertinent discussion of it... potentially good places to get a view of this?  I'd appreciate it.

Thank all of you for the help with this thread question...

Mike

---

### Post by oldfred on 2020-06-06
[https://news.slashdot.org/story/20/06/05/2148219/linux-mint-dumps-ubuntu-snap](https://news.slashdot.org/story/20/06/05/2148219/linux-mint-dumps-ubuntu-snap)

[https://ubuntuforums.org/showthread.php?t=2391341](https://ubuntuforums.org/showthread.php?t=2391341)
[https://ubuntuforums.org/showthread.php?t=2409173](https://ubuntuforums.org/showthread.php?t=2409173)
[https://blog.ubuntu.com/2019/03/28/snap-startup-time-improvements](https://blog.ubuntu.com/2019/03/28/snap-startup-time-improvements)
General snap discussion:
[https://ubuntuforums.org/showthread.php?t=2411218](https://ubuntuforums.org/showthread.php?t=2411218)
[https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb](https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb) & 
[https://askubuntu.com/questions/948861/why-would-i-want-to-install-a-snap-if-i-can-install-via-apt-instead](https://askubuntu.com/questions/948861/why-would-i-want-to-install-a-snap-if-i-can-install-via-apt-instead)

---

### Post by Mike Krall on 2020-06-07
Ahhh, reading matter...  =]

Thanks, 'oldfred'... see you next time...

Mike

---

### Post by Dennis N on 2020-06-07
> I dabbled at skim on "snap, snaps, snapd" last night. Do any of "all-yawl" have links to (or things to say on) what you feel as pertinent discussion of it... potentially good places to get a view of this? I'd appreciate it.

Many users here have expressed negative opinions on Snap packages. I don't share those feelings. You really need to use them for awhile and judge for yourself. Also, don't ignore Flatpak. Flatpak applications are rarely discussed here on these forums. I do like Flatpak applications and use a number of them. More Flatpaks than Snaps, actually.

---

### Post by Mike Krall on 2020-06-08
> **Dennis N said:**
> Many users here have expressed negative opinions on Snap packages. I don't share those feelings. You really need to use them for awhile and judge for yourself. Also, don't ignore Flatpak. Flatpak applications are rarely discussed here on these forums. I do like Flatpak applications and use a number of them. More Flatpaks than Snaps, actually.

Thanks, 'Dennis N'.  

I haven't made time to look at all of 'oldfred's links on Snap.  In the end, I may not have enough base understanding to have other than impressions.  Right now, what I believe is, 'oldfred' found it to be problematic with his form of separate-data partitions.  I want/need to know about that aspect because it is my form, too.  I'll start from there.  

Mike

... There's a great big hole in the world where Daniel Mock was...

---

### Post by Dennis N on 2020-06-08
> Right now, what I believe is, 'oldfred' found it to be problematic with his form of separate-data partitions. I want/need to know about that aspect because it is my form, too. I'll start from there.
Good. I also use a separate data partition, and have not had any problems with that when using Snap or Flatpak applications. I'd be interested to find what the concerns might be. Ubuntu installs its Snap Store by default now, so you have that ready to go.

---

### Post by Mike Krall on 2020-06-09
> **TheFu said:**
> You can run the chromium that is part of the snap install directly, without using the snap wrapper.

Would you either say or point me to a description of doing this, please?

Mike

---

### Post by Mike Krall on 2020-06-09
> **Dennis N said:**
> Good. I also use a separate data partition, and have not had any problems with that when using Snap or Flatpak applications. I'd be interested to find what the concerns might be. Ubuntu installs its Snap Store by default now, so you have that ready to go.

I'll try, 'Dennis N'... 

Mike

---

### Post by Dennis N on 2020-06-09
Here's one justification for Snap or Flatpak.

My original thinking back in the beginning of snap-awareness was that I could use them keep my main applications in the LTS version Ubuntu 16.04 as up-to-date as possible. 
So I installed LibreOffice Snap on it. It's always the current version - now 6.4.4; otherwise I would have likely still be on version 5.1.6 from the repos.  
From there, I did the same for a few other of my most-used applications: Firefox, Gimp, Inkscape in particular, although Firefox is kept up-to-date in the repos as well. 
I later-on did the same in 18.04 (I use Flatpak here, after investigating it). So especially in LTS releases, many users may find Snap or Flatpak makes sense.

---

### Post by Mike Krall on 2020-06-12
I've done a little looking, 'Dennis N', but not much.  Way too little to have an impression. I have an approach to things.  It might not suit this.  Comes from design.  A person looks for the negatives.  They are ALWAYS more obvious and ALWAYS way fewer in number.  In a design world, finding and deleting the negatives leaves all positives.  No, nothing is that simple but the approach is valid... suited to this, I don't know.  And then there's... will I even vaguely understand what I'm reading?   

I'd ask a question. Do you have any "same function", one in Snap and one not, in the same computer... something where difference in speed would be noticeable?  If yes, is there? 

Mike

---

### Post by Dennis N on 2020-06-12
> I'd ask a question. Do you have any "same function", one in Snap and one not, in the same computer... something where difference in speed would be noticeable? If yes, is there?
First of all, you can have a Snap version or Flatpak version of a package installed installed alongside the one from the Ubuntu repository, so it's easy to compare on any machine.

You will read that Snap packages take longer to open - it may take two seconds longer (well, maybe 10 sometimes), because it's stored in a compressed format and needs to decompress. But that is only the first time you start it in any one session, from what I see. A Flatpak program does NOT take longer to start. I assume it's not compressed. Using say, Gimp as an example, where I have actually tried all the different types - Flatpak, Snap, Repo Version on the same computer, I see no difference in interface, functionality (what you asked about) and performance when using it. Snaps used to not conform to the system theme, but more recently, they seem to have fixed that in the popular applications.  

If a Snap needs to open/save your files, like a word processor, you can access home folder, the /media folder, and the /mnt folder. My separate data partition, where I keep personal files, is mounted under /mnt, so I have no access problems, as I alluded to in another post somewhere. 

Well, Better stop there - I'm getting away from the actual question.

---

### Post by Mike Krall on 2020-06-14
I wish I could have gotten to this sooner, but I couldn't.  

I don't really have anything to say here.  I'm happy to have the information, the "users" view.  Thanks for that 'Dennis N'.  
> Snaps used to not conform to the system theme, but more recently, they seem to have fixed that in the popular applications.
I don't understand this.  Do understand it might not be a thing that is easy to explain further without creating many more questions.  Consider your audience, 'Dennis N'...  =]  ...I won't be heartbroken over you passing on this.

Mike

---

### Post by Dennis N on 2020-06-14
> Snaps used to not conform to the system theme, but more recently, they seem to have fixed that in the popular applications...I don't understand this. Do understand it might not be a thing that is easy to explain further  

I've wondered about this too. I think there are some 'resource' snaps that play into this. My inferences follow. How is the Gimp Snap (for example) aware of my system theme (Yaru-dark)?

Some facts from a Ubuntu blog post:

> Snaps have security at their heart, and are designed to ensure all applications support the principle of least privilege / authority. That is, each package only has access to the common groups of resources that it requires to perform its intended function.

To support this, each package is sandboxed so that it runs in a constrained environment, isolated from the rest of the system &#8211; this is achieved via a combination of AppArmor, seccomp, mount namespaces, cgroups and traditional UNIX permissions. To then allow a package access to common resources, the snap system provides &#8216;interfaces&#8217; to which packages can be granted access as required or determined by the user. This includes things like files within the user&#8217;s home directory, or files on removable media, as well as hardware devices such as webcams or audio devices (for a full list of interfaces see the snap documentation). **Interfaces can also be provided from one snap to another, for example to let one snap provide services via DBus to another snap application, or to provide _shared content_ from one snap to another.**

Excerpt from: [https://ubuntu.com/blog/a-guide-to-snap-permissions-and-interfaces](https://ubuntu.com/blog/a-guide-to-snap-permissions-and-interfaces)


Once it (somehow) detects my system theme, the application could be accessing  a relatively-new snap resource bundle of common gtk themes that I notice has been installed (but not by me). These are 'shared content'. Originally (as with the first snap offerings like 'Calculator') the theme probably was included with the application.

Notice in the snap list:
```
dmn@Sydney-vm:~$ snap list | grep gtk
gtk-common-themes     0.1-36-gc75f853             1506  latest/stable/&#8230;  canonical*  -

```
Pending further infornation, I'm going with this explanation for now.

---

### Post by Mike Krall on 2020-06-15
Do I understand... a Snap package decides it needs/wants (or maybe it's just "could have"?) a thing and goes and gets it (or it comes?)  

I see that gtk-common-themes 0.1-36-gv75f853 is something a person would like to have in GIMP and that there is a fair amount of work involved with figuring out how to get in and make it stick. 

Mike

---

### Post by Dennis N on 2020-06-15
I would imagine Snaps could be built with the requirement that this themes package must be available, and the snap manager will add it during installation if it's not.

---

### Post by Mike Krall on 2020-06-17
Thanks, 'Dennis N'.  I'm going to have to make time for this.  There's just too much of it where I'm "unclear on the concept".  

Mike

---


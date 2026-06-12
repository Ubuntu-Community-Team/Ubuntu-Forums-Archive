---
title: "Update headache"
date: 2012-07-12
forum: New to Ubuntu
---

### Post by BobJam on 2012-07-12
I've been putting this off for wayyyyy too long, and now I'm faced with what is probably going to be a headache.

Currently I'm on 9.10 and that "sooner or later" time has arrived and it's certainly time to update to 12.04.

There are other "update" posts here recently, but I don't see any with my specific circumstances.

So, the questions:

1.   I'm assuming I'm going to have to go through each individual update to  get to 12.04.  IOW, I just can't jump to 12.04.  Is that correct?

2.   My /home directory is on a separate partition.  I'm assuming I could  keep this intact throughout, BUT 9.10 uses the old GNOME desktop, so I'm  guessing that somewhere along the process, the new Unity desktop may  screw things up.  What do I need to do, what do I need to watch out for,  etc.

3.  I'd like to have things as I have them now . . . GNOME desktop, panel applets, etc.  Can I do that, and if so . . . how??

4.  Programs and panel applets . . . do I make a list?   (As I recall, there's a command to do that for the programs but NOT the panel applets.  I've downloaded some of the applets because what I wanted did not show up on the "Add to panel . . ." window.  So will I need to go to the URL's I downloaded the applets from and do it again?).

5.  What "profiles" should I backup and restore?   (Firefox . . . I'm on 13 now . . . and Thunderbird for sure . . . more?)

6.   I run a Sun VM with Windows XP as a guest . . . I run it because I have  all my finances on Quicken.  (I tried Wine, but it was too buggy and I  finally ended up using a VM.)  I have a "snapshot" of my Windows guest .  . . can I use that or will a restore of the .VirtualBox folder in my /home do it?  Or would I better ask this question on the Oracle/Sun VM forum?

My machine is a Dell Inspiron 1545.  The graphics board is Intel and I've had some trouble with it.

After I launch into this, I will post in this thread any hiccups I had so that maybe other noobs can benefit from my mistakes.  But I don't want to do anything until I get some responses here.

TIA

---

### Post by TheGuyWithTheFace on 2012-07-12
I would say simply back up all your data, including your virtualbox VMs, and simply do a clean install. they tend to work better anyway. Restoring your files afterwards is usually pretty easy.

---

### Post by jmfal on 2012-07-12
##1 I don't think you can do upgrades from 9.10 
          Tried to help another the other day from 10.10 and it wouldn't let him.
          Better off going with a fresh install.  
##2 I'm pretty sure you can leave it intact.
         Not sure about the rest.

---

### Post by DingusFett on 2012-07-12
Yeah, I would just back up your important things and do a clean install.

---

### Post by Paqman on 2012-07-12
> **BobJam said:**
> 
1.   I'm assuming I'm going to have to go through each individual update to  get to 12.04.  IOW, I just can't jump to 12.04.  Is that correct?


Sort of.

You can upgrade directly to 10.04, which is still a supported version and uses the Gnome 2 desktop you like. Since it's an LTS release you can upgrade directly to the next LTS which is 12.04.

> 
2.   My /home directory is on a separate partition.  I'm assuming I could  keep this intact throughout, BUT 9.10 uses the old GNOME desktop, so I'm  guessing that somewhere along the process, the new Unity desktop may  screw things up.  What do I need to do, what do I need to watch out for,  etc.


Yes you could keep it. Settings for Gnome 2 and Gnome 3 would be kept separate so nothing would break as such. If you moved to the new Unity desktop (Gnome 3) then it would be set up from scratch and wouldn't have any of your old settings.

> 3.  I'd like to have things as I have them now . . . GNOME desktop, panel applets, etc.  Can I do that, and if so . . . how??

By sticking with Gnome 2 on 10.04. There are ways to try and shoehorn Gnome 2-like desktops onto 12.04, but I'm not the person to talk to about that.

> 4.  Programs and panel applets . . . do I make a list?   (As I recall, there's a command to do that for the programs but NOT the panel applets.  I've downloaded some of the applets because what I wanted did not show up on the "Add to panel . . ." window.  So will I need to go to the URL's I downloaded the applets from and do it again?).

Programs from the repos will be upgraded automatically. Third-party sources (such as PPAs and repos from Google or Oracle) would be disable during the upgrade, you would need to swap them over to the correct settings for the new version once the upgrade was complete and run Update Manager to get the new versions.

> 5.  What "profiles" should I backup and restore?   (Firefox . . . I'm on 13 now . . . and Thunderbird for sure . . . more?)

That's all stored in your home folder and would be preserved.

> 6.   I run a Sun VM with Windows XP as a guest . . . I run it because I have  all my finances on Quicken.  (I tried Wine, but it was too buggy and I  finally ended up using a VM.)  I have a "snapshot" of my Windows guest .  . . can I use that or will a restore of the .VirtualBox folder in my /home do it?  Or would I better ask this question on the Oracle/Sun VM forum?

Again, all this is in your home folder and should be fine. As mentioned above you should switch the VBox repo to the correct one for your new version (just a job of changing the name in Software Sources)

---

### Post by deadflowr on 2012-07-12
If at all possible, just upgrade to 10.04,LucidLynx. You'll still be on the ole gnome, and you'll have some breathing room until next april.

---

### Post by BobJam on 2012-07-13
Looks like a fresh install is the consensus.

I had tried 10.04 once and it was very unstable (which is why I went back to 9.10), so I might just do a fresh install of 12.04.

@ Paqman,

It's been a long time since I did a "fresh install".  Is there an option in the 12.04 install routine whereby I can keep my existing /home partition.  What I DON'T want to do is wipe that partition clean.  I just want to install / and the programs I like.

Should I post another question on how to "shoehorn" GNOME 2 into Unity?  Anybody know if there's a "how-to" on this?

Anyway, this "shoehorn" business sounds like what I want to do.  Anybody:  If I do that, would the "shoehorned" GNOME 2 take it's settings from my /home?

@ All,

Thanks VERY much for the responses.

This is the "headache" part.  Will be busy the next few days taking screen shots of various programs and configs I have and backing up to USB sticks (BTW, do I plug them in during the installation of 12.04 or not?  I have a vague memory that having them in during an installation is a No-No.)

What I don't want to end up with is a situation where I'm saying to myself, "I know I had something like that before, what the heck was it?"

Actually, now that I think of it, I have plenty of unallocated room on my HDD.  So, can I install 12.04 AND keep 9.10 and have them both draw from my /home?  I assume then (if it's even possible), I would get some sort of a boot menu.  If I can do that, I would eventually ditch 9.10, but I could use it during the transition to 12.04 to see "how it was" . . . and the tedious screen shots would not be necessary.

Still taking a deep breath on this.

---

### Post by TheGuyWithTheFace on 2012-07-13
> **BobJam said:**
> 
Actually, now that I think of it, I have plenty of unallocated room on my HDD.  So, can I install 12.04 AND keep 9.10 and have them both draw from my /home?

Short answer: Yes.

---

### Post by BobJam on 2012-07-13
@ TheGuyWithTheFace,

That's good news.  Can you point me to a "how-to" on this?

---

### Post by Miljet on 2012-07-13
I always have two versions of Ubuntu on my computers, the one I am using and the one I switched from. When I am comfortable with the new version, the old one becomes dormant until it is time to upgrade again. Kind of like keeping the old kernel version and the latest one.

---

### Post by kansasnoob on 2012-07-13
> Actually, now that I think of it, I have plenty of unallocated room on my HDD. So, can I install 12.04 AND keep 9.10 and have them both draw from my /home? 

It's typically NOT a good idea to share /home because your individual desktop profile exists in /home so each time you switch from 9.10 to 12.04 all of your settings will be gorfed :(

You might get by with it if you use a different user ID but then you might encounter some difficulties with file "ownership". OTOH if this is the only Linux OS on the machine you should be offered options similar to this:

[ATTACH]221214[/ATTACH]

Note: If you don't understand or like the options you're offered the QUIT button is there for a reason!

I've personally had very good luck with the "upgrade" option but you're always foolish NOT to back up everything important!

And you can get really close to a classic gnome look and feel in 12.04:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

---

### Post by Paqman on 2012-07-14
Two installs can share a home folder, you just need to use two separate accounts so that the config files are kept separate. You can put your data in a common location that both accounts have permission to access.

---

### Post by BobJam on 2012-07-15
OK . . . a coupla things now.

@ Miljet,

That definitely sounds like what I want to do, but kansasnoob says I shouldn't use the same /home for both.  If you're in agreement with that, then do you have two different /homes?  IOW, should I create a separate /home partition for my 12.04?  (Same question to @ kansasnoob.)  Paqman apparently has a sort of workaround.

Also, would the installation of 12.04 create a separate swap file for its use only, or would it use the existing swap?

@ kansasnoob,

In that installation options screenshot of yours, if that's what I'm presented with, I'm guessing I would use the fourth option:  "Something else".  I certainly don't have 11.10 on my machine and I definitely don't want to "erase everything".  So that's the only option left.  Will that then go on to give me screens to create a 12.04 / partition and a 12.04 /home partition?

I am still considering the upgrade route (based on Paqman's recommendation that "*You can upgrade directly to 10.04, which is still a supported version and uses the Gnome 2 desktop you like. Since it's an LTS release you can upgrade directly to the next LTS which is 12.04*" here:  [http://ubuntuforums.org/showpost.php?p=12097542&postcount=5](http://ubuntuforums.org/showpost.php?p=12097542&postcount=5) ) but I'm still leaning toward a fresh install anyway, especially if I can have both 9.10 and 12.04.

I favor 9.10 so much, and my existing settings, mostly because I've worked so hard to make it stable.  For example, I had quite a bit of trouble with my touchpad and the cursor moving all over the place, but I finally solved that with a synclient script (can't remember what file I put it in.)  Plus my video was buggy, but I finally resolved that too (can't remember what I did now.)  So that's why I want to keep my settings and am still considering the upgrade path.

But I assume that the kernel code has changed so much that I might not have the touchpad or video problems anyway, but I may have an entirely new set of problems.  It might be misleading to say "problems".  I'll likely just have to tweak it to get things the way I want them . . . like I did with 9.10.  And everybody has to do that to some degree, so it's to be expected.  Hopefully it won't be as intense as it was with 9.10.

Should I use GParted from a LiveCD to format my unallocated area for ext4 BEFORE I try the installation routine, or will the install routine do that?  I expect I'll have to do something with GParted first, since the unallocated region is NOT formatted at all.

And, yes, BTW, I'm making a lot of backups and screenshots.

@ Paqman,

So just exactly how would I go about running the install routine to accomplish keeping the config files separate as you suggest.

If you guys havn't figured it out yet, I can use a step-by-step guide, like:

1.  Run GParted to <blah, blah, blah>.

2. Burn the 12.04 CD from the ISO you download from here: _ _ _ _

3.  Run the 12.04 installation routine by selecting <this> and <this> etc.

4.  Modify the fstab files in both versions to reflect <blah, blah, blah>.  (I have no idea if this is necessary . . . just using it as an example.)

5.  Boot

6.  Follow kansasnoobs instructions for installing the gnome-classic like DE.

Now I know that's asking a lot, so if you all choose not to do that, I know I'll muddle through it anyway.  But if any of you can at least point out those things that would definitely bork my efforts, I sure would appreciate it.  I'm going to have to go through this minefield myself, so if anyone can point out where the mines might be . . . that would be kewl.  The more specific the help the better.

Anyway, TIA and thanks already for the help you've given so far.

BTW, here's my current partitioning:

---

### Post by Paqman on 2012-07-16
> **BobJam said:**
> 
If you guys havn't figured it out yet, I can use a step-by-step guide, like:


[LIST=1]
[*]Boot the Live CD
[*]Run the installer
[*]Choose "do something else..." on the partitioning page
[*]Select the unallocated space to be mounted at /, format as ext4
[*]Select the old home partition to be mounted at /home, **do not format**
[*]When you set up the first user account, use a different user name from the existing install
[*]Profit!
[/LIST]

If you don't want to use all the unallocated space on that disk, use Gparted to carve it up before proceeding to run the installer. The end result of this process will be two root partitions for two different releases of Ubuntu, and one home partition with two sets of user home folders. You could also create a shared data partition with relatively permissive permissions if you like, and the locations in each user's home folders could be linked to it if you want to keep things tidy.

---

### Post by BobJam on 2012-07-21
OK . . . one more round of responses and then I'm going to take a deep breath, fasten my seat belt, and pull the trigger.

@ kansasnoob,

These are responses to your post here:  [http://ubuntuforums.org/showpost.php?p=12104577&postcount=104](http://ubuntuforums.org/showpost.php?p=12104577&postcount=104)

Yes, I've decided I will just do a fresh install of 12.04, NOT go through the update process.

First of all, you clearly have been through the (installation) drill, done the dance, heard the music, and I hold your experience there in high regard.  And, the more I think of it, having two separate /homes (Old/home and New/home, though I assume these are just labels and not mount points/paths.  The paths would be /home/new/[user name] and /home/old/[same user name?]?) makes more sense to me considering that I'll have the reference of the Old/home available to draw on in building the New/home that suits my needs with the 12.04 version.

But I'm not quite clear on the partitioning method (though you've provided good explanatory screenshots, and I'm just flat out dense about this . . . as you can see in my stated confusion about the home paths above), so let me state here what my understanding is, and please correct me if I'm wrong.

1.  On the creating and sizing, you suggest creating a partition (from the unallocated portion) destined for the 12.04 system (New/? Just a "label", right?  So would I give it a mount point, and then how would this be seen as different from the 9.10 /?)

2.  And then another formatted and sized partition from the unallocated partition destined for the 12.04 home (New/home?  Just a label, right?  Same question, how would the mount point of the 12.04 /home be seen by the boot as different from the 9.10 /home?  Wouldn't the system get confused and cranky? Or does the fact that they are on different sda designations take care of that?)

3.  From all your screenshots of partitioning, it appears as though I don't need to create another swap file dedicated to 12.04, but rather my existing swap will be sufficient.  Is that correct?  Do I need to resize THAT partition?  Will there be somewhere in the installation routine that I can point the 12.04 / to the existing swap?

4.  I like having a lot of free space in both / and /home.  That may be a holdover habit from Windows.  How much do I really need for Ubuntu?  Should I shrink those partitons?

5.  Looking at the screenshot for all your "testing" distros, it looks like you DON'T have a separate /home anywhere in there, so I assume your /homes are just part of the / partitions?  Is that correct?

6.  And the only mount point I see for / is your 12.04 partition on sda12.  So does that mean your machine boots by default into 12.04 . . . though I expect a Grub menu gives you a selection . . . confused, obviously.

7.  In [http://ubuntuforums.org/attachment.php?attachmentid=221288&d=1342351863](http://ubuntuforums.org/attachment.php?attachmentid=221288&d=1342351863) I see "label" but not "mount point" . . . why?  And what about mount points for each of my versions (9.10 and 12.04) . . . will the 12.04 installation routine stall if I don't give the 12.04 system and home a mount point?  (It doesn't look like you did for all your testing distros.)  Clearly I'm getting confused between "mount point" and "label".  As I understand it, "mount point" is pretty much cast in stone, and "label" is arbitrary (I mean, you could label a partition "cucumber" if you wanted, but "mount point" has to be somewhere on the tree.)

8.  To use GParted to mess with partitions on my machine, I need to use the GParted on the LiveCD?  Something about mounting stuff, isn't it?

That [http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html") reference is for a dual boot with Windows . . . would it essentially be the same for dual boots between two versions of Ubuntu or are there differences not discussed in this?  I'm also looking at your [http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388) thread . . . that's 12 pages and I haven't digested it all yet.

I had been wondering whether to use GParted to prep new partitions out of "unallocated" space or whether to just use the installer to do it?  As I'm understanding this reference, it (and you) recommend prepping with GParted first?  Correct?

(BTW, I see you visit HTG.  I do also and I like that site. And nice touch of humor there:  "*No operating systems were harmed in the making of this web page.*")

In prep, would you recommend downloading the Super Grub Disk?

My machine currently boots to a Grub-like selection for kernels, recovery-mode, and memtest.  I assume this is Grub from 9.10 (actually, it HAS to be because I don't have any other Ubuntu version on the machine right now.)

So, I assume there will be a Grub component in 12.04.  If so, which one would prevail on boot?  Do I need to do something here?  I'm trying to digest this page:  [http://members.iinet.net.au/~herman546/p15.html#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems]("http://members.iinet.net.au/%7Eherman546/p15.html#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems") .  Am I going in the right direction? Though it appears that maybe 9.10 uses Grub2, so I may not have any problems there?  Or does 12.04 use a Grub version that's wayyy different from 1.98?

BTW, once I get the 12.04 ISO burned, I'm going to first try it running just off the CD to see if my hardware is compatible and if I can get on line wirelessly (my machine has a Broadcom wireless card with Broadcom's BCM4311-, BCM4312-, BCM4321-, and BCM4322-based hardware and the Broadcom STA wireless driver *Edit in 9.10*.)

I see this is getting wayyyyyy too lengthy, so just two more questions.

I'm planning on going back to my "old home" and copying some of the old dot files, like .Skype, and pasting that into my "new home" just to see if it will carry my old settings into the "new home" (my 12.04 Skype installation in this example).  Any cautions there?

And finally, can you give me any "DON'T DO THIS FOR SURE" advice . . . something that will definitely bork my whole effort.

Oh, one more thing.  Is there a way I can toggle between the systems or do I have to log out in one and log back in the other every time?  (I ask that because I'll probably at first be going back and forth a lot to get the "new/home" as close to the old as I can.

@ Paqman,

Thanks very much for the step-by-step.  That's exactly what I was looking for, except it looks like there are two things you show that I may not do.

It looks like your steps would use the LiveCD installer to do the partitioning.  I think I'm going to use the LiveCD Gparted to do the partitioning prep instead *EDIT:  which I see you added as an option at the end of your post*.

It also looks like your steps do a shared /home, which was what I was first going to try, but now I think I'll make a separate "new home" for 12.04.

Considering that I now will use two /homes, will I still need to set up two different user names for them?

---

### Post by kansasnoob on 2012-07-21
My installation advice differs and I guess it caused some confusion:

[http://ubuntuforums.org/showpost.php?p=12120057&postcount=113](http://ubuntuforums.org/showpost.php?p=12120057&postcount=113)

[http://ubuntuforums.org/showpost.php?p=12104577&postcount=104](http://ubuntuforums.org/showpost.php?p=12104577&postcount=104)

I have in the past encountered permission problems trying to share /home with different users but at some point every end user must decide who's advice to take :D

---

### Post by kansasnoob on 2012-07-21
> **BobJam said:**
> OK . . . one more round of responses and then I'm going to take a deep breath, fasten my seat belt, and pull the trigger.

@ kansasnoob,

These are responses to your post here:  [http://ubuntuforums.org/showpost.php?p=12104577&postcount=104](http://ubuntuforums.org/showpost.php?p=12104577&postcount=104)

Yes, I've decided I will just do a fresh install of 12.04, NOT go through the update process.

First of all, you clearly have been through the (installation) drill, done the dance, heard the music, and I hold your experience there in high regard.  And, the more I think of it, having two separate /homes (Old/home and New/home, though I assume these are just labels and not mount points/paths.  The paths would be /home/new/[user name] and /home/old/[same user name?]?) makes more sense to me considering that I'll have the reference of the Old/home available to draw on in building the New/home that suits my needs with the 12.04 version.

But I'm not quite clear on the partitioning method (though you've provided good explanatory screenshots, and I'm just flat out dense about this . . . as you can see in my stated confusion about the home paths above), so let me state here what my understanding is, and please correct me if I'm wrong.

1.  On the creating and sizing, you suggest creating a partition (from the unallocated portion) destined for the 12.04 system (New/? Just a "label", right?  So would I give it a mount point, and then how would this be seen as different from the 9.10 /?)

2.  And then another formatted and sized partition from the unallocated partition destined for the 12.04 home (New/home?  Just a label, right?  Same question, how would the mount point of the 12.04 /home be see as different from the 9.10 /home?  Wouldn't the system get confused and cranky? Or does the fact that they are on different sda designations take care of that?)

3.  From all your screenshots of partitioning, it appears as though I don't need to create another swap file dedicated to 12.04, but rather my existing swap will be sufficient.  Is that correct?  Do I need to resize THAT partition?  Will there be somewhere in the installation routine that I can point the 12.04 / to the existing swap?

4.  I like having a lot of free space in both / and /home.  That may be a holdover habit from Windows.  How much do I really need for Ubuntu?  Should I shrink those partitons?

5.  Looking at the screenshot for all your "testing" distros, it looks like you DON'T have a separate /home anywhere in there, so I assume your /homes are just part of the / partitions?  Is that correct?

6.  And the only mount point I see for / is your 12.04 partition on sda12.  So does that mean your machine boots by default into 12.04 . . . though I expect a Grub menu gives you a selection . . . confused, obviously.

7.  In [http://ubuntuforums.org/attachment.php?attachmentid=221288&d=1342351863](http://ubuntuforums.org/attachment.php?attachmentid=221288&d=1342351863) I see "label" but not "mount point" . . . why?  And what about mount points for each of my versions (9.10 and 12.04) . . . will the 12.04 installation routine stall if I don't give the 12.04 system and home a mount point?  (It doesn't look like you did for all your testing distros.)  Clearly I'm getting confused between "mount point" and "label".  As I understand it, "mount point" is pretty much cast in stone, and "label" is arbitrary (I mean, you could label a partition "cucumber" if you wanted, but "mount point" has to be somewhere on the tree.)

8.  To use GParted to mess with partitions on my machine, I need to use the GParted on the LiveCD?  Something about mounting stuff, isn't it?

That [http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html") reference is for a dual boot with Windows . . . would it essentially be the same for dual boots between two versions of Ubuntu or are there differences not discussed in this?  I'm also looking at your [http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388) thread . . . that's 12 pages and I haven't digested it all yet.

I had been wondering whether to use GParted to prep new partitions out of "unallocated" space or whether to just use the installer to do it?  As I'm understanding this reference, it (and you) recommend prepping with GParted first?  Correct?

(BTW, I see you visit HTG.  I do also and I like that site. And nice touch of humor there:  "*No operating systems were harmed in the making of this web page.*")

In prep, would you recommend downloading the Super Grub Disk?

My machine currently boots to a Grub-like selection for kernels, recovery-mode, and memtest.  I assume this is Grub from 9.10 (actually, it HAS to be because I don't have any other Ubuntu version on the machine right now.)

So, I assume there will be a Grub component in 12.04.  If so, which one would prevail on boot?  Do I need to do something here?  I'm trying to digest this page:  [http://members.iinet.net.au/~herman546/p15.html#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems]("http://members.iinet.net.au/%7Eherman546/p15.html#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems") .  Am I going in the right direction? Though it appears that maybe 9.10 uses Grub2, so I may not have any problems there?  Or does 12.04 use a Grub version that's wayyy different from 1.98?

BTW, once I get the 12.04 ISO burned, I'm going to first try it running just off the CD to see if my hardware is compatible and if I can get on line wirelessly (my machine has a Broadcom wireless card with Broadcom's BCM4311-, BCM4312-, BCM4321-, and BCM4322-based hardware and the Broadcom STA wireless driver.)

I see this is getting wayyyyyy too lengthy, so just two more questions.

I'm planning on going back to my "old home" and copying some of the old dot files, like .Skype, and pasting that into my "new home" just to see if it will carry my old settings into the "new home" (my 12.04 Skype installation in this example).  Any cautions there?

And finally, can you give me any "DON'T DO THIS FOR SURE" advice . . . something that will definitely bork my whole effort.

Oh, one more thing.  Is there a way I can toggle between the systems or do I have to log out in one and log back in the other every time?  (I ask that because I'll probably at first be going back and forth a lot to get the "new/home" as close to the old as I can.

@ Paqman,

Thanks very much for the step-by-step.  That's exactly what I was looking for, except it looks like there are two things you show that I may not do.

It looks like your steps would use the LiveCD installer to do the partitioning.  I think I'm going to use the LiveCD Gparted to do the partitioning prep instead.

It also looks like your steps do a shared /home, which was what I was first going to try, but now I think I'll make a separate "new home" for 12.04.

Considering that I now will use two /homes, will I still need to set up two different user names for them?

I need to go out and bounce around on an old tractor so I may not get back to this until tomorrow, sorry :(

---

### Post by kansasnoob on 2012-07-21
OK, I'm back. But before I begin answering any of your questions I need to ask you two questions. In this post:

[http://ubuntuforums.org/showpost.php?p=12104577&postcount=104](http://ubuntuforums.org/showpost.php?p=12104577&postcount=104)

I posted some general hints/examples/comparisons but I then said:

> But lets stop and discuss three other things:

#1: Before beginning the installation (or the testdrive of the Live desktop) always check the disc/USB for errors. In Lucid they began hiding the boot options so when the first screen appears with the two small logos at the bottom you have a whopping 3 seconds to press a key and display the language selector followed by the boot options. Be sure to choose "check disc for defects". It takes several minutes to complete but I can't think of anything more frustrating than finding out the installation media was faulty. Look here:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

#2: I'm guessing you have a laptop. It's always best to use a wired power source when partitioning or installing. Imagine the battery dieing when you're nearly done! Even then my general rule is to backup all valuable data to some external source - the data that's not backed up is always the data that gets lost.


Never mind #3 on that list for now, after posting that I noticed that you did mention how much RAM you had and we'll deal with that later.

So my question #1 (in four parts):

(a) Have you downloaded and created your Ubuntu 12.04 live CD/USB?

(b) Which is it (CD or USB)?

(c) Have you checked it for errors as I described?

(d) After making sure it was error free have you tried the live desktop?

**You MUST have good live/installation media before beginning, and running the live desktop can sometimes rule out hardware problems that may be encountered either during or after the installatio**n :)

My question #2:

Do you have all of your important data backed up to an external device?

**The data you don't have backed up is always the data you lose!**

*******************

In my next post I'll try to answer some of your questions. Please wait for some more specific partitioning advice before attempting the installation - unless you just decide to "pull the trigger".

BTW Paqman is just as qualified as I am, and undoubtedly smarter :)

You can ask 10 died-in-the-wool Linux users the same question and get 40 or 50 different answers from just those 10 users because the options are almost limitless ;)

---

### Post by kansasnoob on 2012-07-21
Trying to figure out how to best answer your questions :confused:

I obviously confused you with the screenshots here:

[http://ubuntuforums.org/showpost.php?p=12104577&postcount=104](http://ubuntuforums.org/showpost.php?p=12104577&postcount=104)

Because you said:

> the more I think of it, having two separate /homes (Old/home and New/home, though I assume these are just labels and not mount points/paths. The paths would be /home/new/[user name] and /home/old/[same user name?]?) makes more sense to me considering that I'll have the reference of the Old/home available to draw on in building the New/home that suits my needs with the 12.04 version.

But I'm not quite clear on the partitioning method (though you've provided good explanatory screenshots, and I'm just flat out dense about this . . . as you can see in my stated confusion about the home paths above), so let me state here what my understanding is, and please correct me if I'm wrong.

1. On the creating and sizing, you suggest creating a partition (from the unallocated portion) destined for the 12.04 system (New/? Just a "label", right? So would I give it a mount point, and then how would this be seen as different from the 9.10 /?)

2. And then another formatted and sized partition from the unallocated partition destined for the 12.04 home (New/home? Just a label, right? Same question, how would the mount point of the 12.04 /home be seen by the boot as different from the 9.10 /home? Wouldn't the system get confused and cranky? Or does the fact that they are on different sda designations take care of that?)

Your confusion actually makes me confused :D

Labels and mount points are two totally different things!

I used those labels with that blank 160GB drive only to show proportionally what I recommended doing. Let me try and think about how to better explain that.

I obviously need to truly explain this step by step. So make sure you have a defect free installation media and I'll think about how to do this :)

---

### Post by kansasnoob on 2012-07-21
> 3. From all your screenshots of partitioning, it appears as though I don't need to create another swap file dedicated to 12.04, but rather my existing swap will be sufficient. Is that correct? Do I need to resize THAT partition? Will there be somewhere in the installation routine that I can point the 12.04 / to the existing swap?


Yes, only one operating system runs at a time, so they can share the same SWAP. I actually linked to this:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

And it says:

> you’ll find that the installer will use any and all existing SWAP partitions

---

### Post by kansasnoob on 2012-07-21
> I like having a lot of free space in both / and /home.

Well look at what you have now:

[http://ubuntuforums.org/attachment.php?attachmentid=221276&d=1342334326](http://ubuntuforums.org/attachment.php?attachmentid=221276&d=1342334326)

That's really not good disk management. The reason I posted a screenshot of my testing machine was only to show that my root partitions never get large enough to require the size you have allocated.

Your /home is a different story. If you follow my advice you'll have to transfer a lot of data and then do even more repartitioning, and given your reluctance and obvious lack of skill I'm now thinking my suggestion is foolish.

I don't know. I really need to rethink this ......... I wish you lived across the street :)

Make sure you have a working live CD/USB and let me rethink this :???:

---

### Post by BobJam on 2012-07-21
> **kansasnoob said:**
> So my question #1 (in four parts):

(a) Have you downloaded and created your Ubuntu 12.04 live CD/USB?

(b) Which is it (CD or USB)?

(c) Have you checked it for errors as I described?

(d) After making sure it was error free have you tried the live desktop?

My question #2:

Do you have all of your important data backed up to an external device?Doing all that now.  May take a while.  Stand-by, I will report back with answers to each question.

On question #2, I've started, but I want to be thorough, so I'm meticulously and tediously going through EVERYTHING, from panel applet names and versions to license/key numbers for Windows on some software in my VM (like WinPatrol and SnagIt), to scripts I have written for the touchpad sensitivity to things as mundane as simple data (that's the easy part.).  Have a special file on a USB stick labeled "12 backups".  Am taking some screenshots too.  Perhaps overkill, but I have relied heavily on my existing tweaks and my productivity (write for blogs) is dependent on a machine that runs flawlessly . . . which again is why I stayed with 9.10 for so long, I got it to be extremely stable.

I'm taking this thing pretty seriously, so I definitely appreciate all the help you and Paqman have given.  No slight to Paqman, but you have been especially helpful.  Thanks.

> **kansasnoob said:**
> Please wait for some more specific partitioning advice before attempting the installation - unless you just decide to "pull the trigger".After an ominous warning like that, I'm definitely going to wait.


> **kansasnoob said:**
> You can ask 10 died-in-the-wool Linux users the same question and get 40 or 50 different answers from just those 10 users because the options are almost limitless ;)Well put.

And thanks again.

---

### Post by BobJam on 2012-07-21
> **kansasnoob said:**
> Your confusion actually makes me confusedSorry for that.  Actually, the only mystery to me was why your GParted screenshot didn't show a "mount points" column . . . a relatively minor mystery that I can easily live with.

> **kansasnoob said:**
> Labels and mount points are two totally different things!Sorry again, I think I was overly dramatic there.  I have my arms around the differences between labels and mount points (which is why I made the "cucumber" analogy) . . . and, yes, I realize they are two entirely different concepts.  It was just that I was wondering why one of your screenshots showed only a column for labels and none for mount points.  Mostly a cosmetic hangup on my part.  Of no great consequence.  Perhaps I'm over-analyzing things . . . I do have a tendency to do that.

The question I have that may be of some consequence is, to repeat:  If I create two homes, one old for 9.10 and one new for 12.04, would each require a different user name?

***EDIT:***[B]Some of these may sound like stupid questions, and now-and-then when I look back on them, I think, "You should have thought that through, you moron.  What a stupid question, and it has an obvious answer.  These guys must think you're an absolute I.D.10T."  But, as you may have deduced, I'm not entirely confident, never having done this exact kind of manipulation before (have done bits and pieces of it maybe twice or so, but have never tried to get two versions of Ubuntu on my machine.)  So better to ask dumb questions than be sorry later.  (Don't want to find myself smacking myself on the forehead and saying "Dohhhhh . . . I should have thought of that."  And got lucky finding someone with patience like you have.)
[/B] 
> **kansasnoob said:**
> I used those labels with that blank 160GB drive only to show proportionally what I recommended doing. Let me try and think about how to better explain that.I think I got it as you already explained it.  Probably not very important that you "*think about how to better explain that.*"  You're already spending a lot of time 'splaining a lot of things to me, so I don't want to waste your time on stuff that may be peripheral.

> **kansasnoob said:**
> I obviously need to truly explain this step by step. So make sure you have a defect free installation media and I'll think about how to do this :)Step-by-step is GOOD.

I think the first step might be checking all the things you mentioned in post #18 . . . and as I said, I'm working on it and will report back.  So no need to rush any "think about" you may be doing.  Take your time.  Thanks again.

---

### Post by BobJam on 2012-07-21
> **kansasnoob said:**
> Yes, only one operating system runs at a time, so they can share the same SWAPSo do I need to resize it, or is it the right size already?

---

### Post by BobJam on 2012-07-21
> **kansasnoob said:**
> Well look at what you have now:

[http://ubuntuforums.org/attachment.php?attachmentid=221276&d=1342334326](http://ubuntuforums.org/attachment.php?attachmentid=221276&d=1342334326)

That's really not good disk management. The reason I posted a screenshot of my testing machine was only to show that my root partitions never get large enough to require the size you have allocated.

Your /home is a different story. If you follow my advice you'll have to transfer a lot of data and then do even more repartitioning, and given your reluctance and obvious lack of skill I'm now thinking my suggestion is foolish.

I don't know. I really need to rethink this ......... I wish you lived across the street :)

Make sure you have a working live CD/USB and let me rethink this :???:Take your time "rethinking".  I'm going to be busy with all the backup and installation prep.  BUT, I definitely want to read more of what you have to say, so keep me on one of your front burners if you can.  Next, I will report on my prep.

Can't say this enough . . . THANKS!

---

### Post by BobJam on 2012-07-22
> **kansasnoob said:**
> (a) Have you downloaded and created your Ubuntu 12.04 live CD/USB?Done.  MD5 checked and OK.

> **kansasnoob said:**
> (b) Which is it (CD or USB)?CD

> **kansasnoob said:**
> (c) Have you checked it for errors as I described?Yes.  Ran "check disk for defects" and all was OK.

> **kansasnoob said:**
> (d) After making sure it was error free have you tried the live desktop?Yes, All ran OK.

Coupla' observations.

There was about a 4 or 5 second lag between selecting "what to do" on the CD.  During that lag, there is no "feedback", progress bar, whatever.

Now I know that the LiveCD takes more time to respond, and I heard my CD motor churning, so I didn't panic.  But nature abhors a vacuum and so do noobs.  So an impatient noob might be inclined to start pounding keys or otherwise bork the process.

Now after about 5+ seconds, those Ubuntu dots showed up (sort of a progress bar), but the thing just sits there like it's frozen for those 5+ seconds . . . enough to make a noob antsy and apt to panic.

Again, I know the CD spinning is the cause, and knew enough to wait.  But is there anything Canonical can do to make an instant message . . . something like "wait while the CD spins to start the process . . ."?  Would help noobs.

I noticed that the Canonical version of FF is 11.  The regular Mozilla update channel is already up to 14.  I guess this Mozilla stuff of almost monthly updates has the Canonical guys in a tizzy trying to keep up.  I know the Canonical version lags by a few weeks, but now a few weeks may mean more than just one version behind.

[B]*EDIT*:  This (directly above) is one of those many things that is a good example of NOT thinking it through.  I imagine the repository may have FF version 12 or 13, maybe even 14 (though I doubt it's gotten that far.)  In any case, big Duhhhhh . . . here.  I was a little premature in pointing the finger at Canonical for not having a more recent version of FF.  LOOK IN THE REPOSITORY DUMMY!  There's probably an update.  (As I recall, there's a checkbox in the 12.04 installation routine to have it download updates during the routine.  May take more time though.  May just do updates later and unburden the installation routine there.)

All-in-all though, the exercise so far has been pleasantly WITHOUT hiccups.  Still waiting for the other shoe to drop.  Probably shouldn't be so pessimistic about it all.
[/B] 
I tested both ethernet and wireless connections, and everything worked fine.

One curious thing on that.  I had disconnected my ethernet and was watching it trying to "download" the Broadcom STA driver so that it could "activate" my wireless card.  In the middle of that I thought, "Geeezz, I should still have the ethernet connected so it can get on line to "download", and fully expected it to give me a warning message that it couldn't connect to "download" the driver.

Well, the CD must have the driver stored on it somewhere, and "download" is NOT the correct term (or at least as far as it implies being "on line") because it completed and I was able to connect wirelessly (once I set up my connection SSID and WPA password.)

Anyway, it also saw all my USB sticks, and I played a little with that Unity thing.

Looking at it, I could get around just fine but whether I use Unity or your "Classic (No effects)" DE, I expect I'll be making quite a few tweaks for my own productivity.

BTW, is LibreOffice the same as OpenOffice?  I was able to load some of my OO documents from one of my USB sticks.

One more thing . . . Unity seemed to run just fine and play well with my graphics card, Compiz and all.

> **kansasnoob said:**
> Do you have all of your important data backed up to an external device?Only thing left to do.  But since I'm being so anal about it, will probably take me a few days for this.  All data is on USB sticks, so that's not a problem, but want to do those "other things" I spoke of (screenshots, panel applet names and versions, Windows (as guest in VM) licenses/keys, etc.)

---

### Post by kansasnoob on 2012-07-22
> But since I'm being so anal about it, will probably take me a few days for this.

That's cool. I actually noticed this just now:

> going through EVERYTHING, from panel applet names and versions to license/key numbers for Windows on some software in my VM (like WinPatrol and SnagIt),

I hadn't thought about you having Windows running in a VM. **That fact alone makes me think Paqman's suggestion of sharing /home is a safer bet!**

It's kind of hard for me to explain but basically Windows is extremely finicky about being "moved", even in a VM sometimes. So IMHO it's worth the minimal risk of having to sort out "ownership" issues than having to reinstall Windows. 

That said I'm not incredibly knowledgeable regarding VM's! About the only time I use a VM anymore is to test new iso images before burning a disc.

So don't do any partitioning just yet! I'll try to provide some more appropriate examples of exactly what you need to do with Gparted and the installer.

---

### Post by kansasnoob on 2012-07-22
> Some of these may sound like stupid questions, and now-and-then when I look back on them, I think, "You should have thought that through, you moron. 

You're doing fine :)

We all have different skill levels with different things. I've used and tested the live-installer a lot so I know how it works, and I've used Gparted a lot also.

But for just two examples of areas I'm lacking in;

(a) You'll notice that my Gnome classic guides for both Precise and Oneiric say I've never cared for the Compiz window manager, so if someone needs help with Compiz I'm clueless.

(b) My fear of sharing /home is based on one bad experience so long ago that I can't even remember what two distros I tried it with. Someone just said, "use different user names", so I did and I had some "permissions" problems - BUT I may have been mixing Ubuntu with either Fedora or Mandriva - it's just been a long time ago and I honestly can't remember :redface:

I do trust Paqman though! So let's figure out where to create a root "/" partition for Precise and I'll try to provide some decent screenshots of just what you need to do :)

---

### Post by BobJam on 2012-07-22
@kansasnoob,

Posting from the 12.04 LiveCD.  Pretty excited with all this so far, though I'm not sure I like Unity at all . . . is premature to make a judgment right now, but I'm definitely leaning toward your "Classic (No effects)" DE.

> **kansasnoob said:**
> I hadn't thought about you having Windows running in a VM. That fact alone makes me think Paqman's suggestion of sharing /home is a safer bet!Ummmm . . . see below.

> **kansasnoob said:**
> It's kind of hard for me to explain but basically Windows is extremely finicky about being "moved", even in a VM sometimes. So IMHO it's worth the minimal risk of having to sort out "ownership" issues than having to reinstall Windows.Wait a minute . . . wait a minute.  I'm a little confused on what you're saying about Windows "being moved".  If I created the VM brand new (in the "New home") from scratch, using the Windows CD I already have (license is valid) and which I used already to create the Windows Guest VM in 9.10 (Sun, now Oracle, VirtualBox), how would that be "moving"?

I'm pretty set on creating a "new home" anyway and not sharing the existing home, as long as I can go back to 9.10 now-and-then and see how I had it.  The reason is NOT related to any considerations of problems with permissions (though that IS a negative) but rather the opportunity that may give me to see new ways, and even perhaps something different that 12.04 might present.  (Now I realize sharing the same home would likely give me the same opportunity of "seeing new ways" if I chose to upgrade my VM, but I'm pretty set now on creating a new home [with your help, of course] because I like the idea now of building new stuff.  Previously, I thought that perhaps I could do this migration painlessly by sharing homes [permissions problems notwithstanding], but now it's apparent that I'm going to have to do a lot of tweaking anyway . . . this DE is a good example.  So, my thinking now is "What the heck, if I have to do a lot of tweaking anyway, why not build a new home too", especially if I can still go back and see how I had it.)

Let me try to 'splain myself.  I went kicking and screaming from DOS to Windows 3.1, then kicking and screaming from 3.1 to 95, then kicking and screaming to 98, then kicking and screaming to XP (and then that 500 pound gorilla MS pissed me off, and I went to 'nix - glad now those guys at MS pissed me off and chased me over to Ubuntu).  I'm just not good at adapting to change, but I've seen that it always turns out to be better in the long run.

Anyway, each time I got settled in with an OS and made it stable, I always thought at first (for the first few weeks anyway), "What in the heck are they changing it for?  Works fine for me."  Like when I had 3.1 down and stable, I at first wanted 95 to look and behave just like 3.1.  Then after a few weeks of grumbling, I thought the next progression was just fine.  Then the whole cycle would repeat itself . . . kicking and screaming, grumbling, and finally fanboy.  So that's why I want to build a new home.  Plus my reasoning of "I have to tweak a lot anyway, so why not go all the way?"  And my thing about "productivity" isn't THAT much of an issue . . . I can still be productive while tweaking, albeit at maybe a reduced rate.

And, if I really don't like it after more than a few weeks of "adjusting", I can always try to copy and paste an individual dot file from the old home.

> **kansasnoob said:**
> That said I'm not incredibly knowledgeable regarding VM's! About the only time I use a VM anymore is to test new iso images before burning a disc.I can't necessarily say I'm a pro at VM's either, but I've been using VBox for several years now, and pretty much know my way around it.

For example, my 9.10 version of VBox is virtualbox-4.0_4.0.12-72916~Ubuntu~karmic_i386, and I can't go any further (I think VBox is up to 5 or 6 or higher now) because 9.10 does not have the libraries necessary for the dependencies of further versions.

> **kansasnoob said:**
> So don't do any partitioning just yet! I'll try to provide some more appropriate examples of exactly what you need to do with Gparted and the installer.Am definitely waiting for your guidance, but unless you have some overwhelming reason, I'd rather do the partitioning prep for a separate 12.04 home.

Yes, I've really morphed on this roller coaster ride.  At the beginning I was all for sharing one home, and now I'm a solid "two homes" kinda guy.  Again, *(EDIT from 9.10:  Made this bold)* **not really because of anything you said about permissions problems, but rather my own (twisted perhaps?) reasoning.**

---

### Post by BobJam on 2012-07-22
@kansasnoob,

Back in 9.10 now.

**Don't forget all the questions I had in my post #15**, particularly the questions I had about GRUB, and whether or not the 12.04 GRUB would prevail or if the system would get cranky if I didn't make any mods in some file having to do with GRUB.

Don't mean to be arrogant or abrasive . . . I mean it's not as if I "expect" you to help me.  So if you have the time and inclination, can you address those questions at some point?

---

### Post by kansasnoob on 2012-07-23
@ BobJam,

Be a bit patient. The whole thing about sharing /home peeked my interest and I'll soon need to test the upgrade path from Lucid (10.04) to Precise (12.04) when the first point release drops in a few weeks so I installed Lucid on a 80GB test drive to simulate what you have:

[ATTACH]221671[/ATTACH]

Then I took a few screenshots to show how and where I created a new root partition for Precise:

[ATTACH]221672[/ATTACH]

[ATTACH]221673[/ATTACH]

[ATTACH]221674[/ATTACH]

[ATTACH]221675[/ATTACH]

I now have the Precise installation completed along with screenshots, but I need to go play outside before the heat sets in so be patient :)

BTW I imported a variety of files to that Lucid install to see if I encounter any difficulties sharing /home with a new user name on Precise. I realize you're using 9.10 instead of 10.04 but I doubt that would make much difference.

IMHO you have nothing to worry about with grub! As long as you have an undamaged Ubuntu live CD you can fix anything that goes wrong with grub :)

Just be patient, please :D

---

### Post by yuvraj23 on 2012-07-23
MMM buddy! Update like that is not recommended.. Do fresh install.. backup all important directories like /home/ /etc/ etc and save it to a hard drive.. you can also make an iso image file of your drive.. Now use a software called aptoncd.. If its not there then download it.. put a blank cd in your drive and burn all pakages..

Now download Ubuntu 12.04 iso from main website and boot it up..Install it.. then copy all package files of cd to a new folder say home/yuvraj/packages , open terminal and write 

 ```
 Code : cd packages
              sudo dpkg -i *
```

Thats it... all your packages will be installed

---

### Post by kansasnoob on 2012-07-23
> **BobJam said:**
> @kansasnoob,

Back in 9.10 now.

**Don't forget all the questions I had in my post #15**, particularly the questions I had about GRUB, and whether or not the 12.04 GRUB would prevail or if the system would get cranky if I didn't make any mods in some file having to do with GRUB.

Don't mean to be arrogant or abrasive . . . I mean it's not as if I "expect" you to help me.  So if you have the time and inclination, can you address those questions at some point?

I'm not forgetting .............. well, that's not entirely true because when you posted here:

[http://ubuntuforums.org/showpost.php?p=12104182&postcount=102](http://ubuntuforums.org/showpost.php?p=12104182&postcount=102)

And here:

[http://ubuntuforums.org/showpost.php?p=12104188&postcount=103](http://ubuntuforums.org/showpost.php?p=12104188&postcount=103)

I completely forgot that you had Windows running in a VM :(

We need to concentrate on one thing at a time!

You've now tested Precise on your hardware and all seems well, but that's not a 100% guarantee that it will work perfectly once installed ...... more like 99% ;)

Right now we need to concentrate on the best installation/upgrade option and I'm glad that I tried the "same /home with different user name" approach for myself again. **IMO it's a total dud**!

But **what I suggested here would be no better**:

[http://ubuntuforums.org/showpost.php?p=12104577&postcount=104](http://ubuntuforums.org/showpost.php?p=12104577&postcount=104)

**Both of those ideas suck!**

IMHO the best suggestion is to do what I said here:

[http://ubuntuforums.org/showpost.php?p=12099894&postcount=11](http://ubuntuforums.org/showpost.php?p=12099894&postcount=11)

Now that you have a known good Precise Live CD you could boot to the live desktop and then choose "install". The first two screens are pretty simple:

[ATTACH]221696[/ATTACH]

[ATTACH]221697[/ATTACH]

**If the next screen does not offer upgrading from 9.10 to 12.04 then just click on quit!**

There are no guarantees in life so you must decide if you want to keep using an OS that's had no security updates since April 2011 or "pull the trigger" ;)

---

### Post by BobJam on 2012-07-24
> **kansasnoob said:**
> Be a bit patient

but I need to go play outside before the heat sets in so be patient

Just be patient, pleaseClearly I gave you the idea that I was "IMpatient".  On the contrary, I've said repeatedly, "no rush".  You are doing me a favor here, so anything you do is gratuitous and I don't want you to think I'm "IMpatient".  As I said before, **at your leisure and if and ONLY if you have the time and inclination.**  There is NO rush!  And thanks again.

I'm trying to be methodical and thorugh here, so the more thought that's given to this, the better.

> **kansasnoob said:**
> I realize you're using 9.10 instead of 10.04 but I doubt that would make much differenceNot so sure about that.  I went to 10.04 one time, and it was extremely buggy, so much so that I went back to 9.10 to get stability.  HOWEVER, that was BEFORE 10.04.3 came out (which my Update Manager now tells me it will go to if I update), so perhaps those bugs have been remedied.

What is your opinion of what this person yuvraj23 has to say?  (No, I'm not asking you to flame this person, but the reason I'm asking is because I don't understand much, if any, of that post and you're pretty good at 'splaining stuff.)  For example:

> **yuvraj23 said:**
> you can also make an iso image file of your drive.Is this person talking about something  like "PartImage" or "Clone this" or any one of a number of image programs?  (No, I know your not a mind reader, but what is your opinion?)

> **yuvraj23 said:**
> Now use a software called aptoncd.. If its not there then download it.. put a blank cd in your drive and burn all pakages..What the heck is "aptoncd"?

What does it do?  Ever heard of it, kansasnoob?

And burn what "packages"?

Where would I download it?  (ATM, I'd have to Google it.)

> **yuvraj23 said:**
> Now download Ubuntu 12.04 iso from main website and boot it up..Have already done that.

> **yuvraj23 said:**
> Install it..Whoa . . . Dude.  Not installing anything yet, and won't unless I have my arms around what I'm doing . . . and that includes kansasnoob's recommendations . . . ANYBODY for that matter.  I have to understand what I'm doing, and I definitely don't here.

> **yuvraj23 said:**
> then copy all package files of cd to a new folder say home/yuvraj/packages , open terminal and write 

 ```
 Code : cd packages
              sudo dpkg -i *
```Thats it... all your packages will be installedWhat packages?

And, what does this line do specifically?

> **kansasnoob said:**
> I completely forgot that you had Windows running in a VMThat explains that "moving' stuff you wrote on, and had me confused.  (Don't worry about "confusing me".  "Confusion" is my natural state . . . probably a consequence of being 65 and senile.  Seriously, I AM a bit dense, if you haven't noticed already.  So don't agonize over 'splaining things to me . . . except maybe the "dud" and "sucks" stuff I ask about below.  I'm NOT going to do anything until I MYSELF have my arms around what I'm doing.  A good faith effort is fine, and that's what you've done, and the rest is up to ME.)

> **kansasnoob said:**
> We need to concentrate on one thing at a time!Agreed!

> **kansasnoob said:**
> You've now tested Precise on your hardware and all seems well, but that's not a 100% guarantee that it will work perfectly once installed ...... more like 99%Interesting that you should mention that.  In my paranoid state, I went ahead and made several copies of the 12.04CD, and checked each one.

> **kansasnoob said:**
> Right now we need to concentrate on the best installation/upgrade optionI thought we were "concentrating" on partitioning, but on thinking about it, it appears I may have been too far ahead of where we're at now.  I agree with your approach, especially considering that you've "tested" those configs.

> **kansasnoob said:**
> and I'm glad that I tried the "same /home with different user name" approach for myself again. **IMO it's a total dud**!If you don't mind me asking, what does "It's a total Dud" mean?  Can you expand on that?  Not doubting your expertise, but I need to know for myself what the details are.

> **kansasnoob said:**
> But **what I suggested here would be no better**:  [http://ubuntuforums.org/showpost.php?p=12104577&postcount=104](http://ubuntuforums.org/showpost.php?p=12104577&postcount=104)  **Both of those ideas suck!**Same question again.  Can you be more specific on what you mean by "suck"?  (Please don't take offense . . . as I said, am not questioning your skills, they are much above mine, but I need to know for MYSELF what the details are.  I know "suck" means "not good", but to get my arms around the concept, I need to know "WHY" it "sucks".)  

> **kansasnoob said:**
> IMHO the best suggestion is to do what I said here:  [http://ubuntuforums.org/showpost.php?p=12099894&postcount=11](http://ubuntuforums.org/showpost.php?p=12099894&postcount=11)Wait a minute . . . wait a minute.  Lemme see if I understand this correctly.  You're now saying (after considerable testing, which I respect and appreciate) that going through the update process is the best way to do this, rather than a fresh install and/or sharing homes?  Is that correct?  (I don't think so, see below.)

> **kansasnoob said:**
> Now that you have a known good Precise Live CD you could boot to the live desktop and then choose "install". . .  **If the next screen does not offer upgrading from 9.10 to 12.04 then just click on quit!**So I was in error above?  You're NOT suggesting that I go through the update routine within 9.10, as Paqman said in post #5?:

> **Paqman said:**
> You can upgrade directly to 10.04, which is still a supported version and uses the Gnome 2 desktop you like. Since it's an LTS release you can upgrade directly to the next LTS which is 12.04

**What you're recommending is a clean install IF the install routine displays a "willingness" to go from 9.10 to 12.04?**

If not, then what?  Any "fallback" approach?  (Just do a fresh install, period?)

---

### Post by BobJam on 2012-07-24
OK . . . I Googled "aptoncd" and now I think I'm getting it.  Have to think about this one a bit, though.

---

### Post by BobJam on 2012-07-26
OK . . . read more on that aptoncd, and it looks promising.

Thanks, yuvraj23.

Sorry about speaking of you in the third person in that post . . . sometimes that can appear offensive.  But I just wanted to see if kansasnoob had any take on it, though I probably should have made the remarks to you directly also (sort of did a few times.)

Anyway, apologize if I pissed you off.

However, I DO have a few more questions on it.  A  lot of the packages that I downloaded (and I think that's what you meant) were just simple .debs off the web and I just double clicked them to install . . . I mean I didn't use "apt-get" or synaptic (I know, bad practice.)  So, the question there:  would aptoncd still find them?

Plus, I downloaded a few panel applets that weren't on "add to panel".  I'm guessing aptoncd wouldn't detect them?

@ All,

I am in danger of "paralysis by analysis".  I know I have to stop dallying around and soon choose a method.  I'm still making some screenshots and backups and will likely be at least another few days (this isn't the only thing I've been doing.)  So when I'm done making the backups, I'll likely decide and "get off the pot".  Thanks for all the input.  I think maybe kansasnoob has a few more things to say, so I'm hoping that will come in the next few days (still NO RUSH, kansasnoob, in case you think I'm being IMpatient, and thanks again for all your patience, but it's got to be wearing thin on you . . . just need to end this dallying around sooner rather than later.)

---

### Post by kansasnoob on 2012-07-26
@ BobJam,

Sorry to just disappear but I had a minor health issue arise. Let's start by going back to your post #34 and I'll try my best to explain :)

In my previous response I said, "I realize you're using 9.10 instead of 10.04 but I doubt that would make much difference". And your reply to that was:

> Not so sure about that. I went to 10.04 one time, and it was extremely buggy, so much so that I went back to 9.10 to get stability. HOWEVER, that was BEFORE 10.04.3 came out (which my Update Manager now tells me it will go to if I update), so perhaps those bugs have been remedied.


I was talking ONLY about the idea of sharing /home between either 9.10 or 10.04 and 12.04 with a different user name! I doubt that the difference between 9.10 and 10.04 in that regard would be much different.

In fact now that I've actually tried it I don't think it would make any difference if someone were sharing /home with identical distros and different user names. You would still have to copy everything from the old users profile to the new users profile which would double the size of "used space" in your existing /home :(

And you do NOT have enough room to do that! Also I think it's unlikely that you'd keep your Windows VM alive doing that!

BTW regarding this in particular:

> Not so sure about that. I went to 10.04 one time, and it was extremely buggy, so much so that I went back to 9.10 to get stability. HOWEVER, that was BEFORE 10.04.3 came out (which my Update Manager now tells me it will go to if I update), so perhaps those bugs have been remedied.


**[COLOR="Red"]Forget about upgrading to 10.04 using the Update Manager![/COLOR]**

**Your 9.10 has had no updates, not even security updates, since April 2011!**

Update manager quit working when support died! When was the last time you were notified of an update?

BTW 10.04 is now at 10.04.4, but support for the desktop version will end in April of next year!

The upgrade process using the Live CD (if it's offered) works in a totally different manner than upgrading through the update manager or through the terminal!!!

Totally different!

I'm going to continue in my next post :)

---

### Post by kansasnoob on 2012-07-26
> What is your opinion of what this person yuvraj23 has to say?

Great!

But what he's talking about is a totally fresh install, not even attempting to save your old Windows VM, etc.

And APTonCD only attempts to restore the packages previously installed. The .debs must not only exist but also be compatible with the new OS :(

The suggestion of using Gparted to create backups of an entire partition (or partitions) is excellent. That's generally what I do unless Windows exists in that partition, in which case I still use "dd" but I absolutely will NOT spend a week explaining "dd" basics to anyone! (I still struggle from time to time)

At the end of the day it's just another "back up all of your stuff and do a fresh install" approach. Nothing wrong with that. Has anyone said there's no need to back up everything before performing an upgrade or re-installation?

BTW whether using APTonCD, a procedure similar to [this]("http://savvyadmin.com/backup-and-restore-package-lists-in-ubuntu/"), or the new Ubuntu Live CD upgrade path you are not going to get an exact duplicate of 9.10 out of 12.04!

Some people truly should just let other people take care of there computers, there's no shame in that :)

---

### Post by BobJam on 2012-07-26
> **kansasnoob said:**
> **[COLOR=Red]Forget about upgrading to 10.04 using the Update Manager![/COLOR]**

**Your 9.10 has had no updates, not even security updates, since April 2011!**

Update manager quit working when support died!It seems to be working (for the version update only.)  I have an "upgrade" button.  It shows this:

---

### Post by waynefoutz on 2012-07-26
I'm jumping in this thread late in the game, but Bob, have you considered Linux Mint 13 with the MATE desktop? It is, for all intents and purposes, Gnome 2. You can also install MATE on Ubuntu 12.04, but it makes somewhat of a mess with duplicate applications in your menus.

---

### Post by BobJam on 2012-07-27
> **waynefoutz said:**
> I'm jumping in this thread late in the game, but Bob, have you considered Linux Mint 13 with the MATE desktop? It is, for all intents and purposes, Gnome 2. You can also install MATE on Ubuntu 12.04, but it makes somewhat of a mess with duplicate applications in your menus.Yes, I,ve considered other distros seriously in the beginning, but I'm comfortable with Ubuntu and really don't want to change horses at this stage of the game.  Though if this effort goes south, I may consider them again.

Mint is indeed a backup candidate.  But I've come this far (and kansasnoob has also dedicated a lot of time), so ATM I'm going to go with Ubuntu 12.04.

Thanks for the suggestion.

---

### Post by BobJam on 2012-07-27
OK . . . let me end this agonizing thread.

First, thanks everybody for all the suggestions, particularly kansasnoob, who I know has spent a lot of time trying to help me out.

Key to any of these efforts is a backup of not only data, but screenshots and URL's of packages/applets that I now use and like. Some though won't work in 12.04, so I've resigned myself to "substituting" when necessary.  But I'm still going through my whole backup routine.

As an example of the need to "substitute", I use "parcellite", a clipboard utility in 9.10. But as it happens, when I tried it in 12.04 (running off the CD), it did not function in Unity. However, there is another similar clipboard utility that DOES function in 12.04 Unity.  It's called "ClipIt" and is listed in the 12.04 software downloads.  It works very much like parcellite, and I expect I'm going to run into a lot of that.

Bottom line, this thread has convinced me that it's not only time to move on, my desire to remain with everything working like it did in 9.10 is absolutely foolish and unrealistic.  I need to step into the 21st Century and put my stubby pencil down.  I need to leave the crutch of 9.10 in the dust and not look back.

So, here's what I've decided.  (I'm going to take a deep breath, fasten my seat belt, hold on, and go fot it . . . WITH A BACKUP ON REMOVABLE MEDIA.  The eight most dangerous words in the English language:  "Fasten your seat belt, I'm gonna try something.")

First, the notion of sharing my 9.10 home with 12.04, while maybe possible, is something I don't want to try.

My primary effort is going to be going through the update process to get to 12.04, especially since my Update Manager indicates 10.04 is available, and pretty much rely on what Paqman said in post #5:

> **Paqman said:**
> You can upgrade directly to 10.04, which is still a supported version and uses the Gnome 2 desktop you like. Since it's an LTS release you can upgrade directly to the next LTS which is 12.04.

As far as the DE goes, I'm going to try kansasnoob's method to secure the "Classic (No effects)" DE.  But I'm getting a little ahead of myself there.  First I need to get to 12.04 and I need to get it stable.  Right now, when I ran it off the CD **several times**, it looked like it worked well and played nice with my hardware, so that's promising.

If the update process goes south on me, there's always the clean install route.  That's my backup and ace-in-the-hole effort, in which case all the work I'm doing now on backups will come in handy.

I don't think I'll have to worry about partitioning if the upgrade process works, but I will have to attend to it if I have to fall back on the clean install method off the CD.  ATM, my feeling is to wipe out 9.10 totally (hence the backups) and just have the CD install on it's own, **if I have to go the clean install route**.  But I'm not going to do that until I've exhausted the upgrade attempt.

Thanks again, everyone, and a special thanks to kansasnoob.

I'm going to mark this "SOLVED", but will report back how it all goes.  Who knows, some other poor soul who is stuck on 9.10 may benefit from this also.

---

### Post by kansasnoob on 2012-07-27
> My primary effort is going to be going through the update process to get to 12.04, especially since my Update Manager indicates 10.04 is available

Bad, bad, bad idea ](*,)

Since you don't trust me read this:

[https://help.ubuntu.com/community/EOLUpgrades/](https://help.ubuntu.com/community/EOLUpgrades/)

IMHO the method explained there is not only complicated but very likely to result in a total freaking mess!

You stand a much, much better chance of upgrading if offered an upgrade via the live CD as I explained here:

[http://ubuntuforums.org/showpost.php?p=12099894&postcount=11](http://ubuntuforums.org/showpost.php?p=12099894&postcount=11)

Simply boot to the live desktop, then double-click install and you'll see two simple screens:

[ATTACH]221859[/ATTACH]

[ATTACH]221860[/ATTACH]

The third screen will offer the available options. If the upgrade option is offered choose that and proceed. **If the upgrade option is not offered click on Quit**!

If you're offered the upgrade option and you proceed you should expect to see something like this during the upgrade process:

[ATTACH]221862[/ATTACH]

That's because some existing settings and/or applications can't (and shouldn't be) restored!

I realize that documentation on that process is very much lacking but look at the last post here:

[http://ubuntuforums.org/showthread.php?t=1970397](http://ubuntuforums.org/showthread.php?t=1970397)

There is no 100% guarantee of anything but I can assure you that performing an upgrade via Live CD (if it's offered) is a gazillion times more likely to succeed than an upgrade using the Update Mangler ..... particularly with an EOL release!

---

### Post by BobJam on 2012-08-04
SUCCESS!!!!! 

For novices that are as idiotic as I was and have an Ubuntu version that's wayyyyy out of date (and no longer supported) but want to upgrade and still be able to go back to the old version to see how things were set up, lemme' cut to the chase (details below) and give the solution I found that did ALL I wanted and had absolutely NO hiccups:

From the 12.04 LiveCD, I had it run through the install routine.

It detected my 9.10, and I selected the option to have it install 12.04 BESIDE 9.10.

From there, it went through the install routine with ABSOLUTELY NO further input from me and NO WARNINGS or HICCUPS . . . just an install progress bar.  THAT WAS IT!

I now have 9.10 AND 12.04 on my machine, both functioning flawlessly AND GRUB2 allows me to select either 9.10 or 12.04.

Now for the details.

I had agonized on how to do this (as you can see by reading through this thread) . . . clean install, upgrade, share home, prep with GParted, etc.  Well . . . forget about all that stuff.  With the exception of making a backup (see [http://ubuntuforums.org/showpost.php?p=12121749&postcount=22](http://ubuntuforums.org/showpost.php?p=12121749&postcount=22) and my explanation in that post on question #2 that kansasnoob posed) AND checking the integrity of the file system and the 12.04 CD (see [http://ubuntuforums.org/showpost.php?p=12121980&postcount=26](http://ubuntuforums.org/showpost.php?p=12121980&postcount=26) ), I did ABSOLUTELY NOTHING . . . no prep with GParted, etc.

Since I had completed my backups on removable media, just yesterday, I was then ready and anxious to try the 12.04CD.

After all that agonizing, I finally decided just to do a clean install and be done with it . . . which if you read the first page of this thread was the overwhelming suggestion anyway.  I had the backups I wanted (stored on USB sticks), especially screenshots of what I had in 9.10 and some instructions to myself on how I had done things in 9.10, so I figured I'd just have to use those things if I needed them.

I was pretty sold on just flat out doing a clean install over 9.10.  That seemed like the most trouble-free way to do this.

Then in the selection screen for how to do the install, the 12.04 install routine presented me with the option of installing 12.04 ALONGSIDE 9.10.  At first my temptation was to ignore that option and just do the clean install.

But the more I looked at that option, the more I thought, "What the heck, if there's any major hiccups, I can always just do a clean install from the CD."  Indeed, if there had been even minor hiccups, I was ready with the trigger finger to just abort the whole thing, reinsert the 12.04CD, and do a clean install over top of 9.10.

Well, I'm glad now I tried this install alongside 9.10 routine.  (Of course, I'll get rid of 9.10 once I get done using it as a reference for what I had.)  The install routine, after that selection, ran flawlessly.  As I said, NO warnings, no "Do you want to . . . ?" questions, NO nothin' except the install progress bar.

After it was done, I fully expected that either 9.10 or 12.04 would be borked.  BUT NEITHER WAS!!!

Now I'm happily at work customizing my 12.04, going back to 9.10 now-and-then, to see "how the heck did I have that and how did it work?"

I've already started to use some of kansasnoob's guidance on how to tweak for the "Classic (No effects)" DE ( [http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370) )and so far everything is going flawlessly . . . compliments to kansasnoob on that one.  Dumped Unity.

Compliments also to the developer(s?) that did the 12.04 install routine.  It was absolutely painless and did exactly what I wanted.

BTW, the installation routine gave my machine a different device name and also a different user name . . . it did this by default . . . I have no idea where it got those names, but I didn't change them.

I DID provide a different password from the one I use on 9.10 though.  Whether or not this had something to do with the routine running flawlessly, I really don't know, but just to be on the safe side, I made the password different and didn't change the machine device name or the user name suggested by 12.04.

Plus, it sees my old home and my new home as two separate items.

BTW, here are screenshots of how my partitions were and how they are now via the 12.04 install "alongside" routine.  (First is the Old 9.10 partitions BEFORE the 12.04 install, and the second is the New partitions as done by the 12.04 install.)

I may yet play with the partitioning BEFORE I go much further on customizing, but for now everything is running fine:

---


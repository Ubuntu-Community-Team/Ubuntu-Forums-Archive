---
title: "partioning help"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by chado52 on 2008-05-25
ok well ive been looking around and i see some people with installers like this [IMG]http://www.psychocats.net/ubuntu/images/installinghardyplus10.png[/IMG]
but i have something like this 
[IMG]http://news.softpedia.com/images/extra/LINUX/small/ubuntu804installationguide-small_007.png[/IMG]
what do i do, i still need my XP so im not choosing guided but i have no idea how to partion manually

---

### Post by shifty_powers on 2008-05-25
think you might be missing the second picture?

---

### Post by chado52 on 2008-05-25
fixed 2nd picture

---

### Post by forestpixie on 2008-05-25
You installing in virtualbox? Did you make the harddisk for buntu 5.3Gb?

---

### Post by shifty_powers on 2008-05-25
is that an actual screenshot from when you go to install?

---

### Post by trothigar on 2008-05-25
Try defragging.

---

### Post by forestpixie on 2008-05-25
Looks to me like you have a virtualbox 8Gb drive which you installed XP on and are now trying to install buntu on the saem vbox hardrive - if thats the case you need to crfeate a virtual machine for the buntu installation.

---

### Post by chado52 on 2008-05-25
> **forestpixie said:**
> You installing in virtualbox? Did you make the harddisk for buntu 5.3Gb?
sorry what virtualbox, im sorta computer illiterate 
> **shifty_powers said:**
> is that an actual screenshot from when you go to install?
ya it is

---

### Post by shifty_powers on 2008-05-25
> **trothigar said:**
> Try defragging.

excuse me? is that sarcasm?

fail to see what that has to do with anything here ;)

---

### Post by shifty_powers on 2008-05-25
> **chado52 said:**
> sorry what virtualbox, im sorta computer illiterate 

ya it is

right ok.

did you physically reboot the computer and ubuntu started from the livecd, or are you trying to install ubuntu from WITHIN windows?

---

### Post by chado52 on 2008-05-25
> **shifty_powers said:**
> right ok.

did you physically reboot the computer and ubuntu started from the livecd, or are you trying to install ubuntu from WITHIN windows?

i rebooted from the cd and then tested out ubuntu with out installing and then i clicked on the install icon on the desktop

---

### Post by trothigar on 2008-05-25
Nope. I found that the defragging the ntfs partition solves the problem of ubuntu not detecting the xp partition.

---

### Post by sayakb on 2008-05-25
Defrag your disks. That pushes the data to one side and creates many contiguous blocks of free space and you might get the first option enabled. What the first option does is that utilizes that free space from end/beginning of drives and installs ubuntu to it.

---

### Post by forestpixie on 2008-05-25
If you're in the install now - open aterminal pleaase and run this command - post the output here

[code]sudo fdisk -l[code]

re - defragging - if you didn't defrag before you did the install it is in fact a good idea to do it at least a couple of times.

---

### Post by sayakb on 2008-05-25
> **trothigar said:**
> Nope. I found that the defragging the ntfs partition solves the problem of ubuntu not detecting the xp partition.

You are absolutely right :)
I've tried this and this actually works.. :popcorn:

---

### Post by shifty_powers on 2008-05-25
heh well my apolgies mr trothigar ;)

suppose it does make sense really, windows is notorious for fragmenting and spreading it's files here there and everywhere.

just got so used to ubuntu, that i don't think about ti anymore ;)

edit: and w00t 700 posts ;)

---

### Post by chado52 on 2008-05-25
> **forestpixie said:**
> If you're in the install now - open aterminal pleaase and run this command - post the output here

```
sudo fdisk -l[code]

re - defragging - if you didn't defrag before you did the install it is in fact a good idea to do it at least a couple of times.

[CODE]ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
240 heads, 63 sectors/track, 25841 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24612   186066688+   7  HPFS/NTFS
/dev/sda2           24614       25841     9283680    c  W95 FAT32 (LBA)
```
i did defrag before i installed, so should i defrag a couple times more and try again?

---

### Post by forestpixie on 2008-05-25
> edit: and w00t 700 posts \\:D/

I just got past a year last week - still remember windows unforunately - Dad can you do this and I get the call from my mum, I'll be glad when her printer and scanner die and I can force her to het linux friendly stuff :)

---

### Post by forestpixie on 2008-05-25
> i did defrag before i installed, so should i defrag a couple times more and try again? Yea couple of times I would, also - if when you've done it - there's a big green bit floating about on it's own - trun off the pagefile and do it again.

Edit - if you don't know how - right click My Computer - Properties - Advanced - Performance Options - once at pagefile turn it off - it will whine at you. XP is similar - but I have absolutely no idea about vista :)

---

### Post by sayakb on 2008-05-25
> **forestpixie said:**
> \\:D/

I just got past a year last week - still remember windows unforunately - Dad can you do this and I get the call from my mum, I'll be glad when her printer and scanner die and I can force her to het linux friendly stuff :)

I'm very new as compared to you guys. But yeah, I have had enough nightmares in my Windows days, not because viruses or trojans or BSoDs, but those backdoors.. aargh ](*,)
Anyway, no point in looking back to the DARK past :D :D

---

### Post by chado52 on 2008-05-25
> **forestpixie said:**
> Yea couple of times I would, also - if when you've done it - there's a big green bit floating about on it's own - trun off the pagefile and do it again.

well im computer illiterate so how do you turn off the pagefile

---

### Post by sayakb on 2008-05-25
@OP
You might use Auslogics disk defragments. It is very effective and would serve your purpose methinks :)

---

### Post by trothigar on 2008-05-25
np [shifty_powers]("http://ubuntuforums.org/member.php?u=51870"), though I'm relatively new to ubuntu/debian, I've used gentoo for quite a while on the desktop. Still can't get my head around how people deal with apt but I love ome of ubuntu's features, and its polish.

---

### Post by shifty_powers on 2008-05-25
heh, seem to have been hanging around here sice the dark days of 2005.

good lord the old days of 5.10 and breezy badger ;)

heh, been back and forth from windows a few times since then,

think this is the last time though, windows should be gone for good ;)

---

### Post by sayakb on 2008-05-25
> **chado52 said:**
> well im computer illiterate so how do you turn off the pagefile
Right click on My Computer and click properties.

Click advanced... one of the buttons says virtual memory, click it.... click tab at the top about virt. mem.

Change your drive assignments.

---

### Post by shifty_powers on 2008-05-25
> **chado52 said:**
> well im computer illiterate so how do you turn off the pagefile

heh there's a q ;)

erm...

right click on My Computer, then click Advanced, then Settings under Performance, click advanced tab and then CHANGE next to virtual memory.

Select the drive that says it has a paging file and select NO PAGING file then click SET. OK everything and reboot and you're done!

---

### Post by forestpixie on 2008-05-25
> **shifty_powers said:**
> heh, seem to have been hanging around here sice the dark days of 2005.

good lord the old days of 5.10 and breezy badger ;)

heh, been back and forth from windows a few times since then,

think this is the last time though, windows should be gone for good ;)

I had a few flirtations with buntu then and god only knows how many other distros, including something you installed within windows long before wubi that I can't remember the name of, but could never get my head around getting a speedtouch330 to work - then I got AOL for a free router and been here since :)

---

### Post by chado52 on 2008-05-25
ok well ive defragged my disk twice and turned off the pagefile, and tried installing ubuntu again but it still only gives me the options of 
guided - use entire disk
SCSL1 (0.0.0) ....
Manual

---

### Post by sayakb on 2008-05-25
You seem to have only one option left then. Open GParted (System->Administration->Partition editor) and shrink the Windows volume (if you don't already have a spare empty partition). Just leave atleast 8GB of free space. Now start the installation and select Manual partitioning. Create a 7GB partition with mountpoint / (filesystem ext3) and create a 1GB partition as swap (or create a swap equal to your RAM size and the remaining as / )
Since you can utilize your Windows partitions for data, all you need your / is for the base system and application package files, and 7GB should be OK, You might leave more if you need.

---

### Post by chado52 on 2008-05-25
> **LinuxIsInnovation said:**
> You seem to have only one option left then. Open GParted (System->Administration->Partition editor) and shrink the Windows volume (if you don't already have a spare empty partition). Just leave atleast 8GB of free space. Now start the installation and select Manual partitioning. Create a 7GB partition with mountpoint / (filesystem ext3) and create a 1GB partition as swap (or create a swap equal to your RAM size and the remaining as / )
Since you can utilize your Windows partitions for data, all you need your / is for the base system and application package files, and 7GB should be OK, You might leave more if you need.

ok well i opened up GParted, and i tried to resize but it wont let me do lotsm it says Minimum size:181706 Maximum Size: 181713
and i dont know what to do now

---

### Post by shifty_powers on 2008-05-25
do me a favour, go into manual, (don't worry it won' do anything bad), go to the partiton table and take a screenshot ;)

---

### Post by sayakb on 2008-05-25
> **chado52 said:**
> ok well i opened up GParted, and i tried to resize but it wont let me do lotsm it says Minimum size:181706 Maximum Size: 181713
and i dont know what to do now

Seem like there itself is the problem. There are fragments of data at the end of the Windows partition of yours that are preventing the disk to be resized. Do you have a spare space of about 8-9GB in your HDD?
Plus, also do what shifty_powers said :) That might be useful to us..

---

### Post by chado52 on 2008-05-25
[http://img84.imageshack.us/img84/7862/screenshotvi9.png](http://img84.imageshack.us/img84/7862/screenshotvi9.png)

---

### Post by chado52 on 2008-05-25
> **LinuxIsInnovation said:**
> Seem like there itself is the problem. There are fragments of data at the end of the Windows partition of yours that are preventing the disk to be resized. Do you have a spare space of about 8-9GB in your HDD?
Plus, also do what shifty_powers said :) That might be useful to us..

ya i have tons of space left 8)

---

### Post by sayakb on 2008-05-25
How much free space do you have in your /dev/sda1 ? Seems like things might get a little more complicated :/

---

### Post by shifty_powers on 2008-05-25
whats that fat32 drive used for?

---

### Post by chado52 on 2008-05-25
130-135gb

---

### Post by chado52 on 2008-05-25
> **shifty_powers said:**
> whats that fat32 drive used for?

its my system restore drive

---

### Post by sayakb on 2008-05-25
Actually, it is the data fragmentation problem. Since you are using XP, you would not be able to use Microsoft disk management to shrink your drive (which is available for Vista). Plus neither can you remove your 9GB recovery. Download partition magic pro or something equivalent to shrink your Windows partition.

---

### Post by forestpixie on 2008-05-25
I would download the defrag tool that linuxis (I think) was referring to and try to defrag with that, it's better than the win oone - I used it once or twice, it's free

[http://www.auslogics.com/en/software/disk-defrag/download](http://www.auslogics.com/en/software/disk-defrag/download)

For the sake of a bit more time I'd do as much as I could to majke sure it's going to work properly.

I would also be making sure I had suitable backups of anything I couldn't afford to lose.

---

### Post by chado52 on 2008-05-25
> **LinuxIsInnovation said:**
> Actually, it is the data fragmentation problem. Since you are using XP, you would not be able to use Microsoft disk management to shrink your drive (which is available for Vista). Plus neither can you remove your 9GB recovery.

so, does that mean i can't have ubuntu on my computer

---

### Post by shifty_powers on 2008-05-25
well firslty, he could *acquire* something such as diskeeper to sort out his fregmentation.

secondly partiton magic could create a spare partition.

thirdly, i find restore partitions a pain in the ***, and am always happy to get rid of them....

---

### Post by sayakb on 2008-05-25
Have you created recovery DVDs. If yes, then you should be able to remove the recovery partition. Can you?

---

### Post by shifty_powers on 2008-05-25
> **chado52 said:**
> so, does that mean i can't have ubuntu on my computer

no, you would just have to use a third party disk management tool such as partition magic or the like

---

### Post by chado52 on 2008-05-25
> **LinuxIsInnovation said:**
> Have you created recovery DVDs. If yes, then you should be able to remove the recovery partition. Can you?

the recovery part isnt on the same drive. so does the recover drive still make a problem?

---

### Post by sayakb on 2008-05-25
No. If you have created recovery DVDs, then you might be able to delete the recovery drive and use it for ubuntu. But I think it would void the software warranty (how does that matter anyway ;) )
Even if you don't have recovery DVDs, but you were provided with a genuine WinXP disk, you can get rid of the recovery and use that for ubuntu.

---

### Post by chado52 on 2008-05-25
> **LinuxIsInnovation said:**
> No. If you have created recovery DVDs, then you might be able to delete the recovery drive and use it for ubuntu. But I think it would void the software warranty (how does that matter anyway ;) )
Even if you don't have recovery DVDs, but you were provided with a genuine WinXP disk, you can get rid of the recovery and use that for ubuntu.

I think i might just put it on my main HDD =] 
this is confusing as it is :)

---

### Post by sayakb on 2008-05-25
Even the recovery is on your main HDD (it is just a separate partition)
Anyway, if you don't wish to remove your recovery, just download partition magic and try shrinking the main partition by about 10GB.

EDIT: Here's the link: [http://www.soft32.com/download_151.html](http://www.soft32.com/download_151.html)

---

### Post by chado52 on 2008-05-25
should i still install and defrag with Auslogics Disk Defrag or just download partion magic

---

### Post by sayakb on 2008-05-25
First try shrinking using partition magic  since Auslogics would take a long time to complete. If partition magic fails, use auslogics to compact your files and then try again with partition magic.

---

### Post by chado52 on 2008-05-25
Ok i finished backing up my important files on a dvd
and i downloaded partionmagic and im wondering how much should i partion for ubuntu

---

### Post by sayakb on 2008-05-25
If you have handsome amount of space, 10GB will do. Keep a swap of slightly larger size than your RAM and rest for ubuntu. Though for ubuntu, even 7GB is enough :)

---

### Post by shifty_powers on 2008-05-25
well, i'd have three partitions.

two ext3 partitions, mounted as / (that is root), and /home.

/ should be 5-10gig
/home as big as you want it - rememeber this is where all your user datat, e.g. music and eveyrthing else

then a third partition mounted as /swap. should be about 1-2gig.

the easiest thing is to use partition magic to create a unformatted space, and then use the manual partitioning in the ubuntu installer ;)

---

### Post by arcarsenal on 2008-05-25
I've got a question related to partitioning so I figure it is well-suited here. 

I'm assuming once you partition, you cannot adjust it? I have a 160 gig HD, so when I partitioned I pretty much split it 50/50 and made it around 80GB for each OS (XP and Ubuntu). 

I'm realizing now that I only have about 10 GB left of free space on XP. My problem is that I had been downloading music using Soulseek, which is not compatible with linux.. so I'm thinking I will have to go back to XP to download it and then just move the files into Amarok when I log back into Ubuntu. 

I think I might have fudged that all up by partitioning the way I did, though. 

Any suggestions?

---

### Post by shifty_powers on 2008-05-25
go adn find and download partition magic ;)

---

### Post by sayakb on 2008-05-25
@chado52
Keep the /home small. The reason being that you will have your primary partition available in ubuntu for read/write access so you can directly use it. Also, after you have done setting up ubuntu, if you want the ubuntu partitions to be accessible from XP, install the EXT2IFS driver from here: [http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)

---

### Post by arcarsenal on 2008-05-25
> **shifty_powers said:**
> go adn find and download partition magic ;)

Was that in response to my post? If so, thanks! I'll check it out. I'm kind of freaking out thinking that I may have partitioned in a way that isn't going to be very useful... so hopefully I can fix it.

---

### Post by sayakb on 2008-05-25
> **arcarsenal said:**
> I've got a question related to partitioning so I figure it is well-suited here. 

I'm assuming once you partition, you cannot adjust it? I have a 160 gig HD, so when I partitioned I pretty much split it 50/50 and made it around 80GB for each OS (XP and Ubuntu). 

I'm realizing now that I only have about 10 GB left of free space on XP. My problem is that I had been downloading music using Soulseek, which is not compatible with linux.. so I'm thinking I will have to go back to XP to download it and then just move the files into Amarok when I log back into Ubuntu. 

I think I might have fudged that all up by partitioning the way I did, though. 

Any suggestions?

As I mentioned in my previous post, download the EXT2IFS driver. This would enable read/write support for ext3 filesystem under Windows. So you can directly download the files to the ubuntu partitions through Windows. :)

---

### Post by chado52 on 2008-05-25
OK so with partionmagic should i partion like 40GB
and then i can put 10GB to / and 29GB to /home and 1 to swap?
this is all new to me :)

---

### Post by arcarsenal on 2008-05-25
> **LinuxIsInnovation said:**
> As I mentioned in my previous post, download the EXT2IFS driver. This would enable read/write support for ext3 filesystem under Windows. So you can directly download the files to the ubuntu partitions through Windows. :)

Thanks so much... I'm going to give that a whirl. I'll probably end up having another question or two along the way. :)

---

### Post by chado52 on 2008-05-25
yes thank you guys. i partioned my drive with partionmagic and now when i ran the installer for ubuntu i got all the options for partioning :D 
thanks again and i will be back soon with my problems ;)

---


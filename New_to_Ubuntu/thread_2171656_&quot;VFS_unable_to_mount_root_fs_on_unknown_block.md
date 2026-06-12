---
title: "&quot;VFS unable to mount root fs on unknown block (1,0)&quot;"
date: 2013-08-31
forum: New to Ubuntu
---

### Post by cody_searles on 2013-08-31
How's it going guys? To start out i'll post my specs and ubuntu version for future reference. This is a fresh install off a DVD as well.

PC SPECS
CPU: AMD A8-5600k quad core at 3.6 ghz
MOTHERBOARD: MSI FM2 A75-P33
RAM: G-skill 2x2 4gb 1866mhz
HDD: Western Digital caviar blue 500gb.
PSU: Corsair cx500w
Ubuntu version: latest desktop 12.0 realese.

Ok, on to my problem. I just built my computer and i figured i would give ubuntu a try as my friends said it was a pretty legit OS. Now, i downloaded it to a verbatim 4.7gb disk and put it in my PC...that's where the trouble began.It started up and asked me if i wanted to try it from the disk,install it or test my disk. I clicked on "test disk" and it said i had one error, i figured it was fine so i reset my PC and chose try it from disk and it loaded for a few seconds and then gave me the error message"2.2098571 kernal panic-not snycing: VFS unable to mount root fs on unknown block (1,0)". i also get the same error but it say's "2.051951]" with the same error after it. I also got it to get passed this error once and it brought me to a screen with numbered lines and it keeps displaying the line "timedout killingt '/sbin/blkid-0udeu-p'deu/sdq (293)" it only went to this screen once. i can't for the life of me figure this out. Can some one tell me what these errors mean and how or if i can fix them? let me know if you need more information

---

### Post by Petro Dawg on 2013-08-31
[COLOR=#000000]"Ubuntu version: GNU GRUB version 1.99-21 ubuntu3.10" ???

I believe that is only specifying the version of Grub you have installed, not Ubuntu.

Hopefully you are trying to install Ubuntu 12.04 or later from the DVD.  Also, are you dual booting with windows or installing Ubuntu only? [/COLOR]

---

### Post by cody_searles on 2013-09-01
oh god...that midnight **** up :D. yeah it's the latest desktop 12.xxx version. i'm a complete linux noob. sorry.

---

### Post by Petro Dawg on 2013-09-01
> **cody_searles said:**
> I clicked on "test disk" and it said i had one error


When you did the initial disk test, did the test provide any other information, or just "1 error"?  Depending on what the error is, I expect that could cause issues.

Also did you try to install grub before installing Ubuntu?  Are you letting the installation program install on the full disk with default settings or are you assigning partitions on your own?

You also may want to look here...  [http://wiki.gentoo.org/wiki/Knowledge_Base:Unable_to_mount_root_fs](http://wiki.gentoo.org/wiki/Knowledge_Base:Unable_to_mount_root_fs)

---

### Post by cody_searles on 2013-09-01
It just stated i had one error. and i just downloaded the first torrent on ubuntus website. I didin't mess with any partitions. i'll look at that link. Sorry i can't give you more information.

---

### Post by cody_searles on 2013-09-01
"dosen't know mount [your]("http://wiki.gentoo.org/your") partition because it doesn't know how to [access]("http://wiki.gentoo.org/access") the file system (a likely candidate if the message gives a non-zero figure in the first number set, such as unknown-block(2,0))" think this could be the problem?

---

### Post by Crusty Old Fart on 2013-09-01
Did you make sure your installation disk was good by checking its MD5SUM?

---

### Post by Petro Dawg on 2013-09-01
> **cody_searles said:**
> "dosen't know mount [your]("http://wiki.gentoo.org/your") partition because it doesn't know how to [access]("http://wiki.gentoo.org/access") the file system (a likely candidate if the message gives a non-zero figure in the first number set, such as unknown-block(2,0))" think this could be the problem?


Seems like a likely candidate to me.  You can either try the Resolution outlined in the link I mentioned earlier....  

Or perhaps a bit easier (and ultimately faster); is just download the latest version of Ubuntu 13.04 and try a fresh install of it (since you tried installing 12.xxxx). If you run into the same problem again after installing a different version, then we might have to look into BIOS and hardware issues.

---

### Post by Bucky Ball on 2013-09-01
> **cody_searles said:**
> I clicked on "test disk" and it said i had one error, i figured it was fine ...

Says it all and not sure why you figured it was fine. 

Burn another disk on the slowest possible speed then check again. Make sure disk is clean before burning or booting from; no greasy finger marks or anything else.

I see no point wasting time trying to fix a defective burnt disk. To my knowledge that's not possible.

Good luck.

PS: The advice regarding downloading 13.04 is off-topic and has nothing to do with this. 12.04 LTS is the current stable long-term support release, supported until 2017 and a great place to start. The problems being encountered have NOTHING to do with the release. You could try the 12.04 LTS alternate instead of the desktop version. This sometimes help, but you need an error-free disk first, which you didn't have to start with. Torrents here, and probably where you've been:

[http://www.ubuntu.com/download/alternative-downloads](http://www.ubuntu.com/download/alternative-downloads)

First on the list down the page for 12.04 is the alternate. You can also try the Desktop again and don't bother going ahead if it throws another error. My guess? Fast burn to start with, known to be problematic.

---

### Post by Crusty Old Fart on 2013-09-01
> **Petro Dawg said:**
> ...Or perhaps a bit easier (and ultimately faster); is just download ..,. and try a fresh install...
Yup, that gets my vote, especially this early in the game. It's always a good idea to check the MD5SUM on your downloaded .iso file before you burn an install disk, and again on the disk itself after you burn it. Otherwise, you can't really rule out the installation disk as a source of the problem.

Also, when you burn the disk, do it at a SLOW speed.

---

### Post by cody_searles on 2013-09-01
Ok, i'll try a new download and burn of 12.04. how do i ck it with MD55UM?

---

### Post by Crusty Old Fart on 2013-09-01
> **cody_searles said:**
> Ok, i'll try a new download and burn of 12.04. how do i ck it with MD55UM?
This should help: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Edit: Fixed the link. Sorry for hosing it in the first place.

---

### Post by cody_searles on 2013-09-01
thanks i'll post back how it ends up.

---

### Post by Crusty Old Fart on 2013-09-01
> **cody_searles said:**
> thanks i'll post back how it ends up.
You're mighty welcome.
Just a little bit of motherhood from an old man: Now is not the time to be in a hurry. Now is the time to be careful, go slowly, and know exactly what you're about to do, before you do it.
Good luck.

---

### Post by Bucky Ball on 2013-09-01
> **Crusty Old Fart said:**
>  It's always a good idea to check the MD5SUM on your downloaded .iso file before you burn an install disk, and again on the disk itself after you burn it. Otherwise, you can't really rule out the installation disk as a source of the problem.

Also, when you burn the disk, do it at a SLOW speed.

+1. Yes and yes. Defective disk not ruled out in the first place. Just the opposite, disk reported errors in the first place. ;)

Check MD5SUM on the .iso you have downloaded to this point. If that comes out fine chances are problem was faulty burn/disk, so try burn another disk. Check MD5SUM on that. All good there, proceed with install and report back with next error or details of successful install!

---

### Post by Petro Dawg on 2013-09-01
> **Bucky Ball said:**
> PS: The advice regarding downloading 13.04 is off-topic...

I didn't suggest that the OP go out and buy a puppy; that would be off topic.  I suggested installing the latest Ubuntu operating system which uses a later Linux kernel.  Since the OP said he recently built his computer, it is not out of the realm of possibility that there is a hardware compatibility issue with the Linux kernel 3.5 (used by Ubuntu 12.04) that might not be found in Linux kernel 3.8 (used in Ubuntu 13.04).  

Yes I agree, the issue is probably a crapped out disk (which would be resolved from the new burn I suggested), but it also might be something else.

---

### Post by Crusty Old Fart on 2013-09-01
> **Petro Dawg said:**
> I didn't suggest that the OP go out and buy a puppy; that would be off topic...
Better watch it there, Dawg.
The Venerable Staff (and I mean that sincerely) caught one of my many off topic posts and put it in jail :cool:

@Bucky Ball:
Howdy Buck:
Been a loooong time. Good to see you here.
Hope all is well with you.

---

### Post by cody_searles on 2013-09-01
got a new ISO. now how exactly do i check it to see if it works? the link crusty posted dosen't seem to work for me.

---

### Post by Crusty Old Fart on 2013-09-01
> **cody_searles said:**
> got a new ISO. now how exactly do i check it to see if it works? the link crusty posted dosen't seem to work for me.
Yup. I hosed the link. So sorry about that.
I fixed it several minutes ago. It works now.
You might have to refresh this page, or clear your browser cache.
Again, my sincere apologies.

Oh, what the hell. Here it is again: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by cody_searles on 2013-09-01
Hmm. the ISO didin't have a match on ubuntuhashes....i assume that's bad?

---

### Post by Crusty Old Fart on 2013-09-01
> **cody_searles said:**
> Hmm. the ISO didin't have a match on ubuntuhashes....i assume that's bad?
Bad?...well, I'd say that's putting it mildly.
On the other hand, maybe it's something really simple, like perhaps you're not checking it against the correct MD5SUM for the .iso file that you downloaded.
If you could tell us which .iso file you downloaded, and give a link to the page from where you got it, as well as the MD5SUM you're using, we could double check that you have the correct MD5SUM.

---

### Post by cody_searles on 2013-09-01
[http://www.ubuntu.com/download/alternative-downloads](http://www.ubuntu.com/download/alternative-downloads)

Got the first 64 bit 21.04 torrent on this page. i'm using winMd5sum

---

### Post by Crusty Old Fart on 2013-09-01
> **cody_searles said:**
> [http://www.ubuntu.com/download/alternative-downloads](http://www.ubuntu.com/download/alternative-downloads)

Got the first 21.04 torrent on this page. i'm using winMd5sum
Being dyslexic, I can read that as 12.04--no problem. Thanks.

The MD5SUM hashes for 12.04.3 that I found are in the following code box:
```

**[COLOR=#0000FF]ca4ecd32f1a4c6917c951f45395901ff *ubuntu-12.04.3-alternate-amd64.iso[/COLOR]**
927f06b00821cb4069ce359fe1ec7edb *ubuntu-12.04.3-alternate-i386.iso
e2da0d5ac2ab8bedaa246869e30deb71 *ubuntu-12.04.3-desktop-amd64.iso
c4f4c7a0d03945b78e23d3aa4ce127dc *ubuntu-12.04.3-desktop-i386.iso
2cbe868812a871242cdcdd8f2fd6feb9 *ubuntu-12.04.3-server-amd64.iso
e7917ff0543d8248d00ffb166def849e *ubuntu-12.04.3-server-i386.iso
eed92cd490736ad54e3076b168ffd7ac *ubuntu-12.04.3-wubi-amd64.tar.xz
a9ea62ad52681dca4e3a832436b32ba0 *ubuntu-12.04.3-wubi-i386.tar.xz
da0cd423b2b4e4b899751f05a27adba0 *wubi.exe

```
Yours should be the first one in the list (**[COLOR=#0000FF]bold blue text[/COLOR]**).
I found them here --> [http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

---

### Post by cody_searles on 2013-09-01
Well, i gusse at 2am you lose your ability to count....:D so where do i go from here? am i good to burn it?

---

### Post by Crusty Old Fart on 2013-09-01
> **cody_searles said:**
> Well, i gusse at 2am you lose your ability to count....:D so where do i go from here? am i good to burn it?
Only if you got a perfect match from running winMd5sum on your .iso file.
If not, you'll be making coasters until hell freezes so solidly that all subatomic particle motion ceases.

---

### Post by cody_searles on 2013-09-01
upon further inspection, they don't match :( winMD5SUM states that the MD5 sum is d8be612c8787c35d011ab5450471f0cds.

---

### Post by Crusty Old Fart on 2013-09-01
> **cody_searles said:**
> upon further inspection, they don't match :( winMD5SUM states that the MD5 sum is d8be612c8787c35d011ab5450471f0cds.
Hah! Not even close.
You just discovered one of the reasons why I never use torrent downloads.
Here's the non-torrent full image straight from Ubuntu --> [http://releases.ubuntu.com/precise/ubuntu-12.04.3-alternate-amd64.iso](http://releases.ubuntu.com/precise/ubuntu-12.04.3-alternate-amd64.iso) (taken from the same page I linked above) 
The link in this post will start the download.
Hopefully, you're not trying to do this through a wireless connection to the 'nut.

---

### Post by cody_searles on 2013-09-01
I know. torrents really aren't worth the speed boost, leasson learned. Now do i need the other two folders? or just the ISO

---

### Post by Crusty Old Fart on 2013-09-01
> **cody_searles said:**
> I know. torrents really aren't worth the speed boost, leasson learned. Now do i need the other two folders? or just the ISO
I don't know. I've never noticed other folders. What are they?

You will only be using the .iso file to make the installation DVD. Nothing else should be on it.
You probably already know this, but just to prevent another charlie foxtrot in case you don't, you have to burn .iso files to DVD as an image. It's a different kind of burn.
Here's a link that explains how to do it --> [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by cody_searles on 2013-09-01
fpp_setup.exe folders

---

### Post by Crusty Old Fart on 2013-09-01
I really don't know what you're doing. I've tried to make this as easy as I can.

Here's what I did:
I clicked on the link that I put in **[post=12775760]Post #27 [IMG]http://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG][/post]** and it downloaded the .iso file to my computer. The download did not bring in any folders, only the .iso file.
The download took about 25 minutes to complete.

Then I checked the MD5SUM on the file with the following command:
```

md5sum ubuntu-12.2.04.3-alternate-amd64.iso
[B][COLOR=#008000]
~~~ Output ~~~[/COLOR][/B]

[COLOR=#008000][B]ca4ecd32f1a4c6917c951f45395901ff  ubuntu-12.2.04.3-alternate-amd64.iso
[/B][/COLOR]
[COLOR=#0000ff]**~~~ From Post #23 ~~~**[/COLOR]

[COLOR=#0000ff]**ca4ecd32f1a4c6917c951f45395901ff *ubuntu-12.04.3-alternate-amd64.iso**[/COLOR]

```
Looks like a perfect match to me.
Although, I'll admit I'm clueless as to why the downloaded file was named with number 12.2.04.3 instead of 12.04.3. Maybe the Ubuntu geeks got a little sloppy when they named the file. Nobody's perfect.
Would you like me to burn a disk and mail it to you?

---

### Post by Bucky Ball on 2013-09-01
What you appear to be doing is downloading Wubi!!!

This is not what you want. Unless you are intending to install Ubuntu as a program inside Windows.

Repeat: You should have NO other files in the download apart from the ISO. Just the ISO. .exe files are for Win and not regular Ubuntu install related.

* Hi Crusty! ;)

---

### Post by Crusty Old Fart on 2013-09-01
> **Bucky Ball said:**
> ...* Hi Crusty! ;)
Hey Buck.
I think I'll pass the torch to you on this one and hit the sack. It's getting pretty far into the night for this old man's wrinkled little butt.
Take care,
G'night.

---

### Post by cody_searles on 2013-09-01
I have done the same thing as you. I'm very linux ignorant but i'm very capable of burning a DVD and have burned many in the past. My download manager simply threw two random folders into the download quene, was just curious to see if they were needed at some point. Once you expresed confusion as to what they were i deleted them. I am just trying to get a perfect ISO with a perfect burn as to be sure i'm not having a hardware problem(which i doubt as i have tested all my componets prior to posting this thread) i have been building PCs for myself and my customers for 15 years, although this is my first time dabaling with linux, Not to sound like an arrogant, ungratefull ass. I really do appriciate your patience with me and the help you have given thus far :)

---

### Post by Crusty Old Fart on 2013-09-01
No worries, Cody. It's been a pleasure. You're on the right path and you're doing the right things by making sure your .iso gives you a perfect hash match, as well as your disk after you burn it.
But, I really need to crawl into bed now. I'll check this thread tomorrow and see how you made out.
Good luck.

Oh, and thanks for the appreciation. That is appreciated on this end more than you might think.
G'night.

---

### Post by Bucky Ball on 2013-09-01
@cody_searles: All good. As Crusty said, you're doing the right thing. Make sure you have only the ISO in the queue then burn the image to disk (slower burn the better). Boot from the disk and let us know what happens.

Do whatever checks you need along the way and hopefully you'll be looking at the desktop running from the install disk soon. You can install directly from there (icon on desktop). If you do have success with this burn, you will get some options. Choose 'Try Ubuntu' and that will take you to a desktop. This will give you an idea of how Ubuntu likes your hardware.

Generally, the disk burn and boot is problem free but on the odd occasion, and hopefully this is one of them and nothing more sinister, there is a glitch. As you build the beasts you are obviously sure about the hardware being functional so can rule that out. Are you, by any chance, dual-booting with Windows, or attempting to, or have partitions on the disk you are installing to already?

Anyhow, hopefully it was the error at the beginning of all this that is still the issue and once overcome with a nice, clean disk all will be well. Good luck.

* PS: Did some random files (exe or otherwise) happen to get thrown in the queue for the first burn? If so, there's your error no doubt. If that's the case, go back to where you started, take 'em out of the cue and try again. ;)

---

### Post by Crusty Old Fart on 2013-09-01
> **Bucky Ball said:**
> ...Do whatever checks you need along the way and hopefully you'll be looking at the desktop running from the install disk soon. You can install directly from there (icon on desktop). If you do have success with this burn, you will get some options. Choose 'Try Ubuntu' and that will take you to a desktop. This will give you an idea of how Ubuntu likes your hardware...
Well, that would be the case if Cody installs with a desktop .iso, but I don't think he's following that path right now. Consider the following:
[INDENT]> **Bucky Ball said:**
> ...You could try the 12.04 LTS alternate instead of the desktop version. This sometimes helps...
I think Cody took your suggestion to heart. Lately, we've been trying to get a good hash match from the alternate .iso.
Unless Ubuntu has changed the alternate installations from the way they used to work back when I was using them, if he burns the alternate .iso to disk and uses it to install, he'll be working in a text-only interface. He won't be looking at a desktop running from the disk, nor will he have the option to 'Try Ubuntu' like he would if he was installing from a desktop .iso (often referred to as a "Live Disk"). His first experience with the desktop won't occur until after the installation is complete, the system reboots, and the desktop loads from the installation on his HDD.[/INDENT]

> **Bucky Ball said:**
> ...Are you, by any chance, dual-booting with Windows, or attempting to, or have partitions on the disk you are installing to already?...
It would be nice to know the answers to these questions. Petro Dawg asked them earlier in this mosh pit, but they seem to have fallen to the bottom of it and been stomped flat. :cool:
My guess, based on Cody's machine being newly home-built, is that the HDD has yet to be partitioned. Another guess is that he has no intention of installing any version of Windows. But, I'm just guessing.

Cody:
Here's a little warning for you: If you have any intentions of installing Windows, it should be the FIRST OS installed. Windows expects to have the whole computer to itself during installation. Consequently, it doesn't play nice if it doesn't. It's REALLY fussy, even downright NASTY, about this.

---

### Post by cody_searles on 2013-09-02
Ok, sorry i have been away. i got a perfect ISO of desktop 13.04. i burned it on the slowest speed in imgburn. i use high quality verbatim DVDs and i verifiyed that data on the disk to the data in the ISO folder. So the disk and data on said disk is as close to perfect as you can get. Now when i try and boot from the dvd it gives me the error "kernal panic-  not syncing: UFS unable to mount root fs on inknown block (1,0). can some one shed some light on what this means exactly?

---

### Post by Crusty Old Fart on 2013-09-02
> **cody_searles said:**
> Ok, sorry i have been away. i got a perfect ISO of desktop 13.04. i burned it on the slowest speed in imgburn. i use high quality verbatim DVDs and i verifiyed that data on the disk to the data in the ISO folder. So the disk and data on said disk is as close to perfect as you can get. Now when i try and boot from the dvd it gives me the error "kernal panic-  not syncing: UFS unable to mount root fs on inknown block (1,0). can some one shed some light on what this means exactly?
Are you saying that you got a perfect match to the MD5SUM when you ran winMd5sum on the .iso file and the DVD?

---

### Post by cody_searles on 2013-09-02
Indeed, Everything is in check. Now what does that error mean? i have seen other people with this error but it was (0,0) instead of (1.0). the solution for the latter was some command in the menu. any ideas on how to proceed?

---

### Post by Crusty Old Fart on 2013-09-02
Unfortunately, I don't know what this error means. I've seen similar messages but with VFS instead of UFS.
Are you able to put the DVD in tryout mode?

---

### Post by cody_searles on 2013-09-02
no i get this error when ever i try and do anything. Forgive the typo, it is indeed VFS not UFS.

---

### Post by Crusty Old Fart on 2013-09-02
I'll be happy to help the best I can.
In order to do that, I'll need to ask a fair amount of questions.
First, there were two earlier questions for which we hoped to get answers:
[LIST=1]
[*]Are you wanting to set up a dual boot machine?
[*]Have you done any partitioning of your hard drive yet?
[/LIST]

Now, for a new question: Do you have another computer that you can use to boot from your installation disk and see if that machine will let you run Ubuntu in tryout mode?

---

### Post by cody_searles on 2013-09-02
For the first question. No this is a going to be a 100% linux machine for use in an office enviornment. As for the partitioning of my drive, it is an old drive i reused from another build that had windows 7 on it. It did however have a courrupted BOOTMGR on it so i did a complete format and it should be working as well as a fresh new drive, save storage saturation. As for the last question i have a laptop with WIN vista installed and a high end gaming PC with WIN 7 on it. i'd preferably not like to mess with the gaming PC as it cost me an arm and a leg.

---

### Post by Crusty Old Fart on 2013-09-02
Thanks.
The last time I know of someone being able to fix the problem you are having, they did it by upgrading the firmware for their optical drive. This problem is often caused by either a defective disk, a defective optical drive, or a bad setting in BIOS.
The "desktop.iso" installation disk you are using should give you an option to "try out Ubuntu" without making any changes to your system, assuming it boots far enough to get you to a screen that will show that option. See if you can get that far on the laptop and let me know what happened. We're doing this to try to determine if the disk is at fault or if there's a problem associated with either your optical drive or BIOS in your new machine.

---

### Post by cody_searles on 2013-09-02
Ok, really appriciate the help man, i'll try it on the laptop and see if i can get it to boot. i'll be back!

---

### Post by Crusty Old Fart on 2013-09-02
> **cody_searles said:**
> For the first question. No this is a going to be a 100% linux machine for use in an office enviornment. As for the partitioning of my drive, it is an old drive i reused from another build that had windows 7 on it. It did however have a courrupted BOOTMGR on it so i did a complete format and it should be working as well as a fresh new drive, save storage saturation. As for the last question i have a laptop with WIN vista installed and a high end gaming PC with WIN 7 on it. i'd preferably not like to mess with the gaming PC as it cost me an arm and a leg.
Thanks for the detail here.
We may end up filling the Master Boot Record (MBR) with zeros, which is something that formatting won't do. Also, Linux doesn't use the NTFS format, but we can deal with that later as well. Nice to know a little bit more about what we're working with.
It would also be nice to know what graphics card you're using in your new box.

---

### Post by cody_searles on 2013-09-02
Ok. is it normal for it to come up as wubi in a windows enviornment? as for the gpu i will be using the a8-5600k on board graphics as it will be used in an office for normal office work. and the APU has nice performance for a $90 chip. :D

---

### Post by Bucky Ball on 2013-09-02
Yep, old Win hard drive? As kinda suggested, see if you can get to a desktop from the DVD rather than charging straight into the install. This will give you the opportunity to reformat the disk Linux style. 

You will find Gparted (partition manager) is available at the desktop. Launch that and see what is actually on the disk already. Whatever is on there, wipe it so it all shows 'Free Space'. Back to desktop and click the install icon which should be there.

This is all depending on whether you can get to a desktop via 'Try Ubuntu' of course. But it sounds like you can't. So, for clarity, you boot from the disk and all that happens it you are taken directly to a screen showing the VFS message?

PS: (1,0) means it is looking for the first partition on your ***second*** hard drive, which you don't have. Unsure why it's looking there as it should be (0,0). Also, you are trying to install the 64bit version and not the 32? (Or vice versa if you have a 32bit machine).

Also, is there a way of changing the mode on the (presumably) SATA drive? I haven't had one out of the box and looked for sometime. Was it in a RAID array previously?

---

### Post by Crusty Old Fart on 2013-09-02
> **cody_searles said:**
> Ok. is it normal for it to come up as wubi in a windows enviornment?
I don't think so. Windows shouldn't be involved at all. In fact, if you're booting from the installation disk, you don't even need a hard drive in the machine.
Did you set your BIOS boot priority on the laptop to boot from CD? <-- You have to do that.

---

### Post by cody_searles on 2013-09-02
buck, the error occurs once i try and load the desktop, i see a purple screen for a bit and then it gives me the error. And i don't think i can get into my laptops BIOS. i will take a closer look though.

---

### Post by Bucky Ball on 2013-09-02
> **Crusty Old Fart said:**
>  you don't even need a hard drive in the machine.
Did you set your BIOS boot priority on the laptop to boot from CD? <-- You have to do that.

The first bit: good thinking! To run a desktop from the install disk you don't need a drive in. Take it out and see what result you get when you hit 'Try Ubuntu'.

Also, FYI, you can format the drive appropriately as part of the Ubuntu install when you eventually get there by hitting 'Something Else' at that section of install, so don't worry that you need to set the disk up first. Just thought I'd mention ... ;)

Adding to the second bit from Crusty and elaborating on my previous thought in my last post: in the BIOS you can set the SATA mode to AHCI or RAID (and possibly other things, I'm not sure). You do have it set to AHCI? Crusty may be able to elaborate even further on that ...

---

### Post by Crusty Old Fart on 2013-09-02
> **Bucky Ball said:**
> The first bit: good thinking! To run a desktop from the install disk you don't need a drive in. Take it out and see what result you get when you hit 'Try Ubuntu'.

Also, FYI, you can format the drive appropriately as part of the Ubuntu install when you eventually get there by hitting 'Something Else' at that section of install, so don't worry that you need to set the disk up first. Just thought I'd mention ... ;)
Hey Buck, before we do any partitioning or formatting, I'd really like to have Cody zero write the Master Boot Record (MBR). Otherwise, we could be in for one helluva fight trying to get a working install of Grub. The zero write is easy to do and only takes a few seconds for the boot sector. We'll have to teach Cody how to use the shell, but we'd probably have to do that eventually anyway, so might as well get the baptism done with the zero write of the MBR.

> **Bucky Ball said:**
> Adding to the second bit from Crusty and elaborating on my previous thought in my last post: in the BIOS you can set the SATA mode to AHCI or RAID (and possibly other things, I'm not sure). You do have it set to AHCI? Crusty may be able to elaborate even further on that ...
Good thinkin'. I'm still running antediluvian hardware. I get my computer parts at the dump...seriously. I don't have a single SATA drive in this house.

---

### Post by cody_searles on 2013-09-02
Allright, i can get ubuntu to boot into the desktop on my laptop, so that rules out the disk. and yes my BIOS is set to AHCI. as most my PCs are. except the RAID 0 i have in my gaming PC.

---

### Post by Bucky Ball on 2013-09-02
> **cody_searles said:**
> buck, the error occurs once i try and load the desktop, i see a purple screen for a bit and then it gives me the error. And i don't think i can get into my laptops BIOS. i will take a closer look though.

Ah, then you are getting the list after boot saying 'Try Ubuntu' 'Install' etc.? If so, hit F6 when you get there, a list of options should pop up, choose 'nomodset' then proceed with 'Try Ubuntu' to the desktop. Out of left field, but can you now get to a desktop?

Desktop BIOS should be easily accessible. Straight after boot, it should tell you what key to press to get there, but it is quick so take note. Failing this, generally it's delete key, escape key, F2, F12 or sometimes F8, but it varies from machine to machine. Do a search for what it is on that model lappy.

Just read your last post. Okay, so the drive is set to AHCI on the machine you are actually wanting to install on?

---

### Post by cody_searles on 2013-09-02
Hm this time it just stays on the purple loading screen...no error just a logo with lights under it. i'll give it a little bit and see if it gets me to the desktop.ok. it says it is unable to find a medium containing a live file system.. yes its set to AHCI on the pc i desire to put linux on.

---

### Post by Crusty Old Fart on 2013-09-02
> **cody_searles said:**
> Hm this time it just stays on the purple loading screen...no error just a logo with lights under it. i'll give it a little bit and see if it gets me to the desktop.ok. it says it is unable to find a medium containing a live file system.. yes its set to AHCI on the pc i desire to put linux on.
Okay, I think you're optical drive is on the fritz. Do you have a spare that you can swap in?

If not, turn off the machine and unplug both ends of the data cable that connects your optical drive to your motherboard and plug them back in. Repeat this three times. You'd be surprised how badly a little contact resistance can mangle communication. Replugging the connectors is a pretty decent way to polish away the contact resistance. While you have the box open, it wouldn't hurt to do the same with the power connector to the optical drive either, and maybe even the configuration jumper on it. This little trick has saved my bacon so many times over the years, you wouldn't believe it.

---

### Post by cody_searles on 2013-09-02
Not right now, all my parts are at my shop...probably should keep some stuff around here. i can get one tommorow though. you're fairly sure it's the optical drive? it does seem likely from that error.

---

### Post by Crusty Old Fart on 2013-09-02
> **cody_searles said:**
> Not right now, all my parts are at my shop...probably should keep some stuff around here. i can get one tommorow though. you're fairly sure it's the optical drive? it does seem likely from that error.
Well, we're fairly certain the disk is good because it gave us a nice show in the laptop. We're pretty sure that your BIOS settings are good in your new box or it wouldn't have booted from your optical drive. And since your optical drive is failing at different places, with different results, it suggests that it's flaky.

Read my last post again. I did some editing about contact resistance in connectors.

I'll hang in here with you, but if you decide to bail for the night please let me know so I don't wait at this machine for a last post that will never arrive :cool:

---

### Post by cody_searles on 2013-09-02
ok, i'll open her up and take a look. as well as try your trick. thank god for thumb screws. dosen't seem to have worked. unplugged and plugged in the sata cables 4 times. same with the power plug, hell i even plugged the optical into the 3gb/s port on the MOBO. getting the same slew of errors.

---

### Post by Crusty Old Fart on 2013-09-02
Whoah baby!

I just read through this thread again. We all keep editing our posts. Buck asked about 32bit architecture vs. 64 bit architecture. I've been assuming that the motherboard in your new box is 64 bit. But, the install disk booted your lappy. So...what's the architecture of the lappy? Also, what's the architecture of you new box? 32 bit or 64 bit? And what is the EXACT file name of the .iso that you burned into your installation disk?

---

### Post by cody_searles on 2013-09-02
My new system is 64bit. as for the lappy i think it's 32 bit..hmm thats weird. as for the one i downloaded, i got the 64bit version of the 13.04 desktop [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
i also can't seem to find the .ISO image on my drive..it just vanished. very weird.

---

### Post by Crusty Old Fart on 2013-09-02
> **cody_searles said:**
> My new system is 64bit. as for the lappy i think it's 32 bit..hmm thats weird. as for the one i downloaded, i got the 64bit version of the 13.04 desktop [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
Yeah. It's weird. That's why we need to be sure of what we're dealing with, especially the EXACT name of the .iso file that you burned into your install disk. It's easy enough to make a mistake downloading from the page you used. So, is there any chance you still have the .iso file saved somewhere, or maybe in your recycle bin, so you can post the name of the file?

And the lappy?...If you can post the make and model of it, I'll help you look for its spec. sheet.

---

### Post by cody_searles on 2013-09-02
It's 100% a 32bit laptop...what the hell i made sure it was a 64bit version, i'll keep looking for the file. where dose to download to by default? i can't find it any where and i did not delete it;

---

### Post by Crusty Old Fart on 2013-09-02
> **cody_searles said:**
> It's 100% a 32bit laptop...what the hell i made sure it was a 64bit version, i'll keep looking for the file. where dose to download to by default? i can't find it any where and i did not delete it;
Assuming your were using Windows for the download, look for the file in a sub folder of "Documents and Settings" for your username. Maybe one named: Downloads, or Media, or something else. Sorry I'm not much help here. I'm still running XP. I swore I'd never buy another MS OS when they screwed the pooch with Vista.

I'm going to reboot and get into XP and start the download so I can give you a definitive answer as to where it goes by default in my next post.

---

### Post by cody_searles on 2013-09-02
hmm never found the file itself but i left winmd5sum open with the number. it is ubuntu-13.04-desktop-amd64.iso
wow. now its at a purple screen with more options. testing disk,test memory(with memtest86, whice i use all the time, weird its on my live disk, cool though) help menu. i seem to make progress and then fail before i get into the desktop. very weird.

---

### Post by Crusty Old Fart on 2013-09-02
> **cody_searles said:**
> hmm never found the file itself but i left winmd5sum open with the number. it is ubuntu-13.04-desktop-amd64.iso
Okay. That's the right file for you new box. Sometimes 64 bit software will work on 32 bit systems. It's kind of a backward compatibility thing going on. But, 32 bit software usually chokes on a 64 bit system. So, though it may be somewhat surprising that the lappy ran the installation disk, it's not a shocker.[HR][/HR]So, just to follow up, in XP the default destination for me was:
[FONT=Verdana]C:\Documents and Settings\username\My       Documents\Downloads

Ho[FONT=Verdana]wever, I think I ma[FONT=Verdana]y have [FONT=Verdana]create[FONT=Verdana]d the "Downloads" folder [FONT=Verdana]and changed the system default destination to it.

The initial factory default may have been:
[/FONT][/FONT][/FONT][/FONT][/FONT][/FONT][FONT=Verdana][FONT=Verdana]C:\Documents and Settings\username\My         Documents\My Received Files[/FONT][/FONT] (which I thought was a really lame name)
[HR][/HR]I think at this point we can blame the problems on a flaky optical disk.
My hat is out of rabbits for tonight. How about we see what happens tomorrow after you swap in a more reliable (hopefully) drive.
What say you, Cody?

---

### Post by cody_searles on 2013-09-02
i will swap in a new, higher end drive tommorow and see what happens. i really appriciate your support. you deserve a medal for dealing with my linux-ignorant butt. :D have a good night. :)

---

### Post by Crusty Old Fart on 2013-09-02
Thanks. It's been fun.
Sleep well.
See you tomorrow.

---

### Post by Bucky Ball on 2013-09-02
+1 to testing another optical drive. Definitely appears to be the next logical step after reading everything that's been discussed in my absence. Nothing else obvious jumps out. It seems to be, as you say, getting to the desktop in fits and starts, possibly signifying the optical drive choking then coming good, ad infinitum. It might get to a desktop in ten hours of spluttering! Then again, maybe not. ;)

Fingers crossed for the next experiment working. It's all good either way; Ubuntu was going to be a learning curve whether it worked out-of-the-box or not so ... welcome to the curve, the forums and Linux. Enjoy!

---

### Post by Crusty Old Fart on 2013-09-02
Just had to log back in to leave my parting shot for the night...

Cody, if things go really well for you tomorrow, and you want to try installing the OS before I show up to tell you how to zero write the MBR, there isn't much I think I could write here to convince you to wait for me. After all, you may end up with a successful install on your own.

On the other hand, if you find the grub bootloader ends up getting hosed, we can always zero write the MBR and redo the installation.

Good Luck.

I'm off to bed.

---

### Post by Bucky Ball on 2013-09-02
> **Crusty Old Fart said:**
> ... we can always zero write the MBR and redo the installation.

Forgot to respond to that idea earlier. Yes, zero writing MBR is a good idea (and could be what's preventing this ... could be). But yea, if it is the optical drive probably doesn't matter. 

@Cody: Have you tried the optical drive in another box? Forgive me if you have and posted the result of that earlier. ;)

---

### Post by cody_searles on 2013-09-02
i have not tried it in another system. it's a fresh drive from liteon. i'll try a more expensive asus one in the morning and see if that works.

---

### Post by Crusty Old Fart on 2013-09-02
Ya ha ha! The mosh pit is open again after a long day of maintenance. Let's DANCE!

> **Bucky Ball said:**
> ...PS: (1,0) means it is looking for the first partition on your ***second*** hard drive, which you don't have. Unsure why it's looking there as it should be (0,0)...
Well, well, well, Buck...this little afterthought comment of yours kept playing in my head all night long as I slept. And as my little brain worked overtime on it, I began to wonder about some possibilities that I hadn't considered before.

So, I'll share my thoughts and welcome any comments.

Here's the error that has been plaguing us since Cody's first post:
```

kernel panic - not snycing: VFS unable to mount root fs on unknown block (1,0)

```
Usually, we see this error ending in (0,0) -- indicating that the kernel is looking for the first partition on the ***first*** hard drive. And usually, we see this error coming at us from a kernel that has already been ***installed*** to disk.

But, when we're running from a Live Disk, it may be that a virtual drive is created in RAM (often referred to as a RAMDISK), which may take first place in the drive list [i.e. disk (0)]. if I'm right about that, and the kernel running in RAM looks for the first partition on the next available drive, it seems to make sense that it would be looking for (1,0).

And, if we continue accepting this assumption, then in Cody's new box, it would find a hard drive with a corrupt master boot record, choke on it, and panic.

With regard to the failure coming at different times as the Live Disk is trying to load the desktop, that could be a matter of the kernel's polling priorities, how it handles returns while it's polling hardware, and how quickly it chokes when it gets crap rammed down its throat. It's hard for me to say for sure, since I didn't write the code, but it isn't that hard for me to imagine that the failure could easily occur at different times while the Live Disk is trying to get a desktop on the display.

The easiest way to test this line of thinking would be to physically unplug the data cable from the hard drive and see if Cody can bring up a desktop by booting from his Live Disk.

I'll readily admit that I'm not sure about any of this. Just thinkin' -- and putting it up on the thread as a target for anyone who wants to throw darts at it.

There's more I have to write about this, but it may end up being irrelevant, depending on what happens when Cody tries to run his Live Disk without his hard drive connected. So, I'll wait to hear back from him.

Thanks for planting the seed, Buck. I doubt any of this would have crossed my mind without you.

[HR][/HR]
Cody:

If the Asus optical drive presented the same flaky behavior as the Liteon drive did, then leave the Asus drive in place, disconnect power to the box, open it up, physically unplug the data cable from the hard drive, and then boot from the Live Disk in the Asus drive and tell us what happens.

If that doesn't work, the next suspect would be the data cable that connects the optical drive to the motherboard. Take that cable out of the box completely. Then connect the optical drive to the motherboard using the data cable from the hard drive. Leave the hard drive disconnected. Finally, try to boot up and get to a desktop using the Live Disk in the optical drive. Again, post back here and let us know what happened.

Good Luck.

---

### Post by cody_searles on 2013-09-03
Thanks for the help guys, after running memtest86 for 2 days i finally got an error. decided to put some new RAM in and everything booted just fine. Apparently one little error in my memory was causing the boot to fail. I really do want to thank you all for the help and i will definitly come back here for any linux related problems. You're a great bunch of people. :D cheers.

---

### Post by Bucky Ball on 2013-09-03
Excellent news! Enjoy and see you in the swim. ;)

---

### Post by Crusty Old Fart on 2013-09-03
> **cody_searles said:**
> Thanks for the help guys, after running memtest86 for 2 days i finally got an error. decided to put some new RAM in and everything booted just fine. Apparently one little error in my memory was causing the boot to fail...
Well, Hot Damn! Congratulations!
From early on in this thread, I pretty much settled on this problem being related to hardware. Once, for a fleeting moment, I even thought the RAM might be suspect, but ignored it.
Nice job, Cody. A tip of the hat to you for finding the problem.

> **cody_searles said:**
> ...I really do want to thank you all for the help and i will definitly come back here for any linux related problems. You're a great bunch of people. :D cheers.
You're mighty welcome. Now you know why they pay us the BIG BUCK$. The huge piles of money they heap on us for being here are so obscene, they're just this side of being pornographic. :cool:

Now that you have a working Linux box, the fun begins. Enjoy!

All the best wishes to you,

Crusty

---

### Post by Bucky Ball on 2013-09-03
> **Crusty Old Fart said:**
> Now you know why they pay us the BIG BUCK$. The huge piles of money they heap on us for being here are so obscene, they're just this side of being pornographic. :cool:

Huh? Something's not right. I only ever get to clean the staff latrines, smell the occasional doughnut, clean up around the forums and was told I had to pay for the privilege ... :-k

---

### Post by Crusty Old Fart on 2013-09-03
> **Bucky Ball said:**
> Huh? Something's not right. I only ever get to clean the staff latrines, smell the occasional doughnut, clean up around the forums and was told I had to pay for the privilege ... :-k
Ugh!
That is such a major bummer, Buck.
They dump such a huge haul on me that I'll never live long enough to spend it all.
Tell you what, I'll split it with you:
```

echo $(( Obscene_Crusty_pay / 2 )) >> Buck_bank_account

```

---


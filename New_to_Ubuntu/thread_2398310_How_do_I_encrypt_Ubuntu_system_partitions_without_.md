---
title: "How do I encrypt Ubuntu system partitions without encrypting the whole drive?"
date: 2018-08-10
forum: New to Ubuntu
---

### Post by mikeubu2 on 2018-08-10
The problem I'm having is with some of the limited encryption options on the install disc. The option for encryption is...

> "encrypt the new ubuntu installation for security"

but from what I can it's for full disk encryption, which I don't want because I want my hard drive to have a large unencrypted partition at the end to store things that I don't want encrypted.
My hard drive currently has....

```
/dev/sda1 File System: ext4, Mountpoint: / Size: 39.06GB
/dev/sda2 File System: swap, Mountpoint: none Size: 6.09GB
/dev/sda3 File System: ext4 Mountpoint: /home size: 39.06 GB
/dev/sda4 File System: ntfs Mountpoint: /media/memu/193B33170F6B467D Size: 4.47TB
```  

The larger partition at the end of the drive is the one I don't want encrypted, preferably I'd like to have the first three listed above encrypted.[/INDENT]
I already have the OS installed (with nothing important on it yet) so If I can encrypt them after installation that'd be great.  The only other alternative to that which I can think of is to encrypt the whole drive with the Ubuntu installation software and then resize the encrypted system partition after to make room for the other partition but I've read that's also complicated.

I'm open to other ideas though, such as third-party software. I'm very new to Linux and Ubuntu and literally haven't messed with it for more than two days so if I need to type commands or do something complicated I'd need to know step by step how to do it. Thanks in advance for any help, setting this up has been a nail biter.

---

### Post by TheFu on 2018-08-10
[https://ubuntuforums.org/showthread.php?t=2357627](https://ubuntuforums.org/showthread.php?t=2357627)
It is non-trivial.

---

### Post by oldfred on 2018-08-10
Do not use nor know encryption.

But prefer the idea of only encrypting some of system as I believe in Pareto (80/20 rule) where most data does not require encryption. 

I believe Ubuntu dropped the /home encryption as that tool was not as reliable as desired.
From 18.04 Release notes:
The installer no longer offers the encrypted home option using  ecryptfs-utils. It is recommended to use full-disk encryption instead  for this release. ([1756840]("https://bugs.launchpad.net/bugs/1756840")) Lots of discussion in bug report.

Arch always has good info.
[https://wiki.archlinux.org/index.php/disk_encryption](https://wiki.archlinux.org/index.php/disk_encryption)

---

### Post by mikeubu2 on 2018-08-10
Thanks for the links guys. Fu, the instructions that Paddy Landau laid out are great, I learned some new information from them.  The issue I have is that I am a very literal person due to how my brain functions.  His instructions are detailed, but the example he laid out appeared to be for two hard drives which is different than the scenario I'm dealing with, so I'd need to know exactly what to do and what to type for my scenario simply because I'm so new and know that I can't make a mistake.  That's a lot to ask members here but if anybody can collaborate with me on his instructions catered for my scenario I'd be grateful.  I have 3 days of experience with Linux and Ubuntu and barely got it working without encryption.  

I know how to open the Terminal but don't know most of the commands or how to navigate it, I know how to use Gparted enough to create, delete, and resize partitions, but would still need specific instructions in that area so that I know I'm creating the right kind of partitions for my scenario, and if I'd need to do anything different on the install disc to accommodate this scenario I'd need to know some about that too. I have a functional install of Ubuntu on the same drive I mentioned in the opening post, If it'd be easier to encrypt the partitions after installation we could do that but there's nothing important on them if I need to start over. 

Some more about what I'm working with, in my situation...

> I'm using Ubuntu 18.04.1 L

I want everything related to Ubuntu on one drive which is an external USB 3.0 5tb Seagate drive.

The internal drive on my laptop has Windows with its own bootloader, if possible I don't want any of that altered. I'd want the Ubuntu bootloader on the same external drive as Ubuntu so that I only have to worry about seeing a password screen if I have the external drive plugged in.

The layout of partitions I'd want is what I mentioned in the opening post or something close to it if it needs to be changed, to recap....

/dev/sda1 File System: ext4, Mountpoint: /, Size: 39.06GB
/dev/sda2 File System: swap, Mountpoint: none, Size: 6.09GB
/dev/sda3 File System: ext4 Mountpoint: /home, size: 39.06 GB
/dev/sda4 File System: ntfs Mountpoint: /media/memu/193B33170F6B467D, Size: 4.47TB

While it's not mandatory I'd prefer to be able to hibernate.



In the tutorial, it said something about swap no longer being needed for the new release of Ubuntu for this situation *"[COLOR=#333333][FONT=Ubuntu]Remember that swap is relevant only to systems prior to 18.04, otherwise you can ignore it.", [/FONT][/COLOR]*so if I don't need that, that's okay, just let me know and let me know if I'd need an extra partition, the above is based on a normal install of Ubuntu that I got to work. 

The key thing for me is the very large NTFS partition at the end of the quote above, that's the one I don't want encrypted, it'll be used for general data that can be read by both Windows and Ubuntu, I don't care what it's assigned to as long as it works and isn't encrypted. It doesn't necessarily need to be formatted NTFS during the install or partitioning procedure if that's a problem, as long as there's that free unallocated space left to do so after installation. Other than that requirement I was thinking roughly 40GB for both the system files assigned to / and the home partition assigned to /home.

To give an example of how literal I need the instructions to be, it would perhaps read out something like this...

1. Go to _____ and type _____
2. then type _____
3. Exit _____ and install _____ , it can be found _____

(Filling in the appropriate terms), although any help is appreciated. 

I sent a private message similar to this to Paddy Landau to see if perhaps he can guide me some and I'll give him a link to this forum, but that's a lot to expect so I figured if more people know my situation perhaps someone would be willing to guide me.

---

### Post by TheFu on 2018-08-10
I don't think it is possible for someone not physically at the machine to help you in the way you seek.

At this stage of your skills, I'd strongly suggest you gain normal Linux knowledge, then Level 1, level 2 and level 3 admin skills BEFORE attempting to accomplish what you seek with encryption.

** It is a non-trivial problem.**

You can't run a 3 minute mile when you haven't learned to crawl yet, if you understand my meaning.

But only you can determine how much effort you are willing to put into this.  I'm just trying to provide realistic advice.

Nobody knows most of the commands on any Unix system. We look them up as needed using the help system (manpages) on the machine because looking online will show the wrong help for different versions of the commands.

---

### Post by mikeubu2 on 2018-08-10
I'd bet so, I learned how to install Ubuntu in a couple days. I didn't know anything about what directories to create but learned. I can look up some of the stuff if I'm told to and can be very patient. I follow directions well if they're specific and if I have a problem with the instructions that are laid out or run into a snag, I can always ask about what I'm stuck on specifically.

Beyond a week from now, I won't be able to dedicate as much time to learning due to an upcoming move so I was hoping to have the backup OS running by then. It's up to the members here though, I'll understand if it's too much to ask. The only alternatives I can think of are the following....

Go with Windows 7 since veracrypt will do a system encryption on Windows platforms without complications, Win7 is more secure than the later releases, but they're going to stop support for it in a couple of years and I'm starting to hate the intrusiveness of Windows generally speaking. 
 
I could find another Linux distro that has customizable encryption options on the disc.

Or perhaps do a full disc encryption using the Ubuntu installer and then later resize the unnecessarily large home partition to fit the unencrypted partition that I want at the end of the drive, but I don't know how practical that is or if it's even possible.

---

### Post by mikeubu2 on 2018-08-10
I'm reading a lot on his tutorial about the terminal right now and trying to do what I can on my end, I just hope I can get this worked out before the 1 week deadline, I really don't want to be stuck with Windows.  I wouldn't be able to work on this for weeks if I don't get this sorted out in the days to come, about 7 days to be exact.  

Any advice is welcome, give me a holler if anybody here has something new to share and thanks as always.

---

### Post by TheFu on 2018-08-10
Or use an external disk, flash drive or SD card for the shared storage.  Saw a 128G microSDHC today for $26 on slickdeals.  THAT would be much more cost effective for your time.  IMHO.

Not sure if I said this already, but I wanted something similar and it took many attempts to get it working. When I was all done, I'm positive 2-5G of storage was wasted because the calculations for the boundary location weren't perfect, but after all the failures, I was happy it booted.  The total storage I had on that SSD was 120G.  BTW, the SSD failed about a year later and today I'm using a 64G SSD in that machine with FDE.  No unencrypted areas on the SSD except /boot/.  When I need more, I use either flash or SDHC storage.

I'm not stubborn enough to spend 14 hrs a day, for 2 weeks, to solved something that $25 effectively solves.  But the world  needs stubborn people to make things like this easier for others.

---

### Post by mikeubu2 on 2018-08-10
I tend to be stubborn as well :P  In this case it's only stubborn in terms of wanting to figure this out somehow.  As far as what you're suggesting if I were to get something extra, it'd have to be cheap like what you're presenting but I wonder, instead of using it for the shared storage between Windows and Linux, (I need terabytes worth for that), if I could use something like that to simply install Ubuntu with full disk encryption.  I'd be worried about speed some, the microSD cards I have are painfully slow, although I'm not sure about the one you're talking about.  If I could install the encrypted OS on something like what you mentioned, or a USB 3.0 flash drive I wouldn't have to worry about my new external hard drive needing to have both a shared storage partition and the system partitions on one drive.  Only thing I'd have to be sure of is that I could use a port multiplier on my laptop for both the flash drive with the OS and one of my other devices, due to the limited number of USB ports I have.  

I'd be willing to try something like that if the members here think that'd work, the Ubuntu installer does have a full disc encryption option that I assume is much more straightforward as long as it can use something like a flash drive and maintain reasonable speeds.

---

### Post by mikeubu2 on 2018-08-10
If I can install Ubuntu onto this with full disc encryption without too much in the way of complications I'd buy it...

[https://www.amazon.com/SanDisk-Ultra-Flair-Flash-Drive/dp/B015CH1NAQ/ref=sr_1_7?s=pc&ie=UTF8&qid=1533966792&sr=1-7&keywords=usb+3.0+flash+drives&refinements=p_n_size_browse-bin%3A10285016011](https://www.amazon.com/SanDisk-Ultra-Flair-Flash-Drive/dp/B015CH1NAQ/ref=sr_1_7?s=pc&ie=UTF8&qid=1533966792&sr=1-7&keywords=usb+3.0+flash+drives&refinements=p_n_size_browse-bin%3A10285016011)

It's in my price range and it's USB 3.0 which helps with speed some.

---

### Post by HermanAB on 2018-08-11
Howdy,

With Linux, any configuration that you can think of is possible.  However, there are a few things to think about though:
The reason for encrypting a disk is to protect data at rest - when the computer is switched off - it provides no security while the computer is running.
The reason for protecting data at rest, is to protect your data after the machine was stolen and the disk is flogged off on Ebay.
That happened to me once already.  Fortunately the machine was encrypted.

Leaving parts of the disk unencrypted, makes it easier to attack the machine, by providing space where an Evil Maid can gain a foot hold and install programs to subvert it.  It also provides space where important information can leak to inadvertently and that information then has no protection.

Attacks only get better over time and there is little you can do to plan for attacks that were not invented yet.  In general, the more encryption you use and the longer your passwords, the better your system security will be.  Also bear in mind that encryption doesn't slow the machine down (about 3% only), since the processor has special instructions to make encryption efficient.

If you are thinking: "There is only $100 in my bank account, so it doesn't matter":
An evil comp sci student can get a credit card in your name, buy a car, sell your house and run away with the money while you are on holiday, etc...

These are all real problems that people have run into, so you really cannot be paranoid enough.

---

### Post by Paddy Landau on 2018-08-11
> **mikeubu2 said:**
> I sent a private message similar to this to Paddy Landau…
And here I am! ):P

> **HermanAB said:**
> … after the machine was stolen and the disk is flogged off on Ebay. That happened to me once already.
Gah, that sounds awful!

I tend to agree — you should leave your partition unencrypted only if you have to. If you're using NTFS, it probably means that you need to connect to Windows. I recommend [VeraCrypt]("https://www.veracrypt.fr/en/Home.html") to encrypt the NTFS partition, because VeraCrypt is open source, independently verified, cross-platform, and easy to use once you've learned it. If you choose to use VeraCrypt, please consider donating to the project.

So, to the next point:

The instructions are currently in a state of flux as I rewrite them for some of Ubuntu 18.04's new functions. I hope to finish it soon, but long-term illness is slowing me down. Right at the [top of the instructions]("https://help.ubuntu.com/community/ManualFullSystemEncryption#PLEASE_READ_FIRST") is a message that says, "This message will be removed once the changes are complete." Please wait until then.

Once they are finished, simply follow the instructions. Here are some specific points for you.
[LIST]
[*]Running from an external drive means that you will be able to boot onto any computer (unless it has been locked down), not just your own — although it would have to be UEFI-compatible. Nice and portable!
[*]If you have an older computer, consider using [Lubuntu]("https://lubuntu.me/") instead of Ubuntu.
[*]As you will be booting from both your internal disk and your external disk, you'll actually need two ESPs (EFI System Partitions).
[LIST]
[*]The first ESP already exists on your hard drive — leave it alone!
[*]The second ESP will go onto your external hard drive. When you follow the instructions, create an ESP on the external drive. If you have enough space, make it the full 550MiB.
[/LIST]

[*]Create the second partition being enough to fit your boot and system. Unless you want to hibernate your external drive (which might not work!), you don't have to worry about swap.
[*]Create and format the third partition for your NTFS (while [using GPartEd]("https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessPartitionFormatEncrypt")), but don't include it when you encrypt the drive.
[*]When you follow the instructions to install Ubuntu (or Lubuntu), when you [select the bootloader]("https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessInstallUbuntu#Select_the_bootloader"), be sure to choose your external drive and not your internal drive. Your external drive will probably be [FONT=lucida console]/dev/sdb[/FONT], but you'll have to check.
[*]Once everything is working properly, install VeraCrypt on both your Ubuntu system and your Windows system. Once installed, encrypt the NTFS partition with VeraCrypt.
[*]Finally, test that you can read and write files on the encrypted NTFS in both Windows and Ubuntu.
[/LIST]
I hope that this helps!

Thank you for your patience while I update the documentation.

---

### Post by mikeubu2 on 2018-08-11
No worries, take the time that you need.  The following point above clarified a good bit given my scenario is a little different...

> As you will be booting from both your internal disk and your external disk, you'll actually need two ESPs (EFI System Partitions).
The first ESP already exists on your hard drive — leave it alone!
The second ESP will go onto your external hard drive. When you follow the instructions, create an ESP on the external drive. If you have enough space, make it the full 550MiB.

Having everything on the external drive will certainly help me, being able to boot Linux wherever I go is one of the reasons I'm going with having everything on the external drive.  

I'm happy to wait for the tutorial, the one thing I'd want to do now if I need to hold off on the OS encryption/installation is to be able to go forward with creating the large NTFS partition at the end of the external drive now so that I can start to use it.  With the moving preparations I have coming up in about a week I've been wanting to get at least that part out of the way because I have a lot to copy to it due to only having one copy of all my family photos, videos, music, movies, and writings.  I always keep two or more copies of all of my data but only have the money to have the bulk of it copied twice.  One of those external hard drives for my second backup recently failed completely which is why I have a new external 5tb drive ready to use.  Assuming my other external hard drive fails I'd lose the only remaining copy of most of my data which is why it's important I create the very large NTFS partition at the end of the new drive soon.   As long as that won't interfere with the installation and encryption of Ubuntu down the road.  

I'm planning on wiping the clean installation I have on the new drive now so I can leave about 100 to 150GB of free space at the beginning of the external drive, which is a little more space than how I set up unencrypted Ubuntu initially to test out the full version.  If anybody knows if that'd be okay and not interfere with the installation it would help a great deal. 

As far as encrypting the NTFS partition goes, I always just created an encrypted image on the unencrypted partition with Veracrypt for any important information, then I would encrypt the OS, but I suppose I could consider just encrypting the whole NTFS partition as well so that nothing is unencrypted.  The lazy part of me didn't want to have to type in an additional password to deal with general data but change isn't a bad thing either. :)  

Hope you get feeling better Paddy, that sounds rough man, thanks for your help and down the road when you're in a better spot and have wrapped up what you're doing, check in here again if you want, no worries if not though.  I'm hoping enough of what you're writing in your tutorial applies to this scenario not to have to do guesswork.  What I'll likely do if I can't get it done or need help is come back here and make a list of everything I did step by step to see if anyone can point out where I'm messing up.

---

### Post by Paddy Landau on 2018-08-12
> **mikeubu2 said:**
> … go forward with creating the large NTFS partition at the end of the external drive now so that I can start to use it.
You can absolutely create the NTFS partition right now, and it doesn't matter whether it's at the front or back of the physical disk. Just be sure to leave enough space for the following:

[LIST]
[*]You won't need swap as you won't want to hibernate from your external drive.
[*]The ESP (½Gb)
[*]System partition: 30Gb recommended to fit everything apart from things like video collections, so make it big enough to fit everything that you want.
[/LIST]
I don't think that you should have a separate data partition.

Remember that the NTFS partition won't be encrypted unless you use something like VeraCrypt.

---

### Post by mikeubu2 on 2018-08-13
> **Paddy Landau said:**
> You can absolutely create the NTFS partition right now, and it doesn't matter whether it's at the front or back of the physical disk. Just be sure to leave enough space for the following:

[LIST]
[*]You won't need swap as you won't want to hibernate from your external drive.
[*]The ESP (½Gb)
[*]System partition: 30Gb recommended to fit everything apart from things like video collections, so make it big enough to fit everything that you want.
[/LIST]
I don't think that you should have a separate data partition.

Remember that the NTFS partition won't be encrypted unless you use something like VeraCrypt.

Got it, thanks again, Paddy.  Funny thing is that I used to be very tech savvy.  I still can be but years back I dabbled in game design and created my own 3D worlds and knew enough about scripting and animation to make an environment the user could interact with.  Granted I was using open source graphical engines I didn't create and photoshop but that stuff got complicated.  It's just that things change fast and I can be slow to catch on.  Windows command prompt, and originally DOS, I understood enough to do a number of things but technology is always evolving, being out of the loop for a while will leave some people in the dust if they let it. #-o

I'll be seeing what I can do to get Linux familiarized some though.

---

### Post by Paddy Landau on 2018-08-22
Thank you for your patience. It's all ready now, so please check the [new MFSE thread]("https://ubuntuforums.org/showthread.php?t=2399092").

---


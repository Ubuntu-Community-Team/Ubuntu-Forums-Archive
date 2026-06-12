---
title: "I want to make a backup cd of my fresh install with new software &amp;updates."
date: 2011-11-30
forum: New to Ubuntu
---

### Post by EngineersGarage on 2011-11-30
Hi, I'm very new to ubuntu, my 3rd day(2-3Hrs/day). I have installed ubuntu10.10, done the updates, installed multiple softwares and a antivirus. Now, I want to make a backup/bootdisk of all this hard work for the just in case days that will come eventually... I have downloaded "Remastersys" installed it, made a backup with it, burned it to disc, but when I want to test it on another pc it tells me that " could not find ramdisk image: /casper/initrd.gz ":confused:
As if I would know what they mean by that...Ha!:confused:
I'm fed up with windows and all its nasty viruses so I want to switch to ubuntu, and want to atleast be able to help myself so that I could encourage others to switch and be able to assist them.
If anyone could please help me out here, I would really apreciate it! Thanx!

---

### Post by BC59 on 2011-11-30
The application to do it is called Remastersys.

You can go to the specialized thread for that:

[http://ubuntuforums.org/showthread.php?t=1870607](http://ubuntuforums.org/showthread.php?t=1870607)

---

### Post by EngineersGarage on 2011-11-30
Hi, didnt you read what  I wrote?? I've already used REMASTERSYS. 

Please read all of what I said.

Thank You.

---

### Post by BC59 on 2011-11-30
Oups sorry!

With Remastersys there is a problem. The project was abandoned for some years so there was no support up to now. 

I don't know which version you used. There is a way to install it through PPA but the version installed is old of Karmic era.

The new developer created a Remastersys 3.0 beta which is here

[http://www.remastersys.com/repository/ubuntu-testing/](http://www.remastersys.com/repository/ubuntu-testing/)

A good guide on how to do it is here

[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys) (a little out of date)

So finally the problems you have are natural, because Remastersys does not collaborate perfectly with newer Ubuntu versions.

Try again to do it and hope it will work this time. And just install the .iso on a USB to check it and do not burn a DVD, to avoid the cost.

---

### Post by EngineersGarage on 2011-11-30
I've used rematersys, burned a disk(actually 2 becuase i thought i did something wrong with the first one because it gave me the same error) and even with the second disk, same thing....

could not find ramdisk image: /casper/initrd.gz

what do i do now??

Thanx for the effort though!

---

### Post by EngineersGarage on 2011-11-30
Oh HELL!! Lol... ok, thanx alot!

Will try that then. Will be back shortly with update!

Thanx!

---

### Post by EngineersGarage on 2011-11-30
I must be a idiot... i cant get it to work... I've downloaded the new one that u gave me, installed it. made the new backup. burned the iso with brasero disk burner. inserted the dvd in the new pc, powered up, it went through the bootup, then a screen appeared, it gave me some options, instal live,memtest.etc. i tried every option and the machine just froze on that screen... nothing happens...

can you spoon feed me, just in case there is more idiots like me out there that doesnt understand this system...

please...

Thank You!

---

### Post by BC59 on 2011-11-30
Don't worry, always there is a plan B.

Try to do the same with Clonezilla. Is a little more complicated because you need to install Clonezilla to a USB or CD and then to perform the backup of the system.

Follow the instructions from here:

[http://geekyprojects.com/cloning/how-to-use-clonezilla-tutorial/](http://geekyprojects.com/cloning/how-to-use-clonezilla-tutorial/)

and of course from the official website:

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by EngineersGarage on 2011-11-30
LOL... I wanted things to get easier! Lol..:D

Okay, atleast I will get more experience in doing this and laying the brick one by one to freedom!:o

Thanx.

Will keep you updated!:D

---

### Post by EngineersGarage on 2011-12-01
Do I really need 10 Masters Degrees just to do a simple backup of my system???

I've downloaded clonezilla..burned it to disk...followed the tutorial...everthing went fine until it told me my usb stick is full and could not complete the image...(I had some stuff on there2.4gb of a 4gb stick)...so i shut down following the instructions, copied my stuff onto another pc and made sure the flash is empty, but now when i want to redo all the previous steps...when i get to the actual creating the image part... during the process it says failed! In RED! cant carry on further, then i have to press enter then it gives me options, 1)shutdown 2)reboot 3)start from the beginning, etc... WTF, it worked earlier but now it keeps on giving me the same failure???

Man, never thought it was this difficult just to do a BACKUP!!!

ANY HELP?? ANYONE??  Ive spent 3days now just trying to make a backup...Rediculous!

Please guys...I need to be able to do a backup of my system, I just cant carry on without knowing im safe, just in case I do something wrong and mess up the system in my learning process...

---

### Post by bigseb on 2011-12-01
This is a very cool thread. I have been wondering how to do the same thing.

Keep the suggestions and tips coming!!

---

### Post by Gone fishing on 2011-12-01
Partclone?

Simply clone your / partition put it on some other media and if you break the system use the cloned image of the partition.

have a look at [http://partedmagic.com](http://partedmagic.com)

---

### Post by EngineersGarage on 2011-12-01
this must probly be a very tough thing to do... :( 

All i want is to make a bootable disc of ubuntu10.10 with all the updates and software that ive already downloaded so that i could use it on my other machine and for this one in case something fails, whenever it does like Hdd crash or something...

I'm not asking alot... just that...please, there must be a way to do this... You guys are Genius'es on Here...Come'on Man! 

Have you never made a backup of you system??

Thanx!

---

### Post by EngineersGarage on 2011-12-01
must i do all these staps too??

**11/24/2011: Parted Magic 2011_11_24**

     
 There are some major changes that might cause some issues with the  Multi-Boot-CD crowd. For a long time the pmagic-<version>.sqfs and  Initramfs would not be found on completely supported computers. 
  
 Reason #1: This was caused by Windows based zip programs failing to  convert the file names properly. The file name would be named  PMAGIC_<VERSION>.SQFS when burnt to the CD or copied to a USB  drive. Solution: Rename the file PMAGIC_<VERSION>.SQFS and don't  compress the ISO images anymore. 
  
 Reason #2: I wasn't using the mkisofs -J option when making the official ISO  images. Windows file managers saw the file as  PMAGIC_<VERSION>.SQFS and it would be copied to a USB drive with  uppercase letters. This would cause the failure to boot.  Solution:  Rename the file PMAGIC_<VERSION>.SQFS and use the -J option. 
  
 Reason #3: Somebody would remaster the ISO  image and not use the mkisofs -l option. This was caused by the long  file name of /pmagic/initramfs. Solution: Rename the file initrd.img.  Some of the most popular distributions use this name, so why not?. You  can still boot the initrd.img with or without the -l option now.
  
 Direct ISO booting: Remove _i486, _i686, or _x86_64 from the name of the ISO  image. Parted Magic won't be able to find the squashfs image if you  don't. Also take into account that initramfs was renamed to initrd.img.
  
 Major Bug: There was a dummy file mistaking left in /usr/local/bin that  caused the secure erase command to fail. It's been removed. 
  
 Updated Programs: lilosetup-0.2.9.1, testdisk-6.13, linux-3.1.2. 





Im a newbie,,, like brand new to Ubuntu!! my first week(4th day wich i spent 3days just to make a backup)!!

---

### Post by corncob on 2011-12-01
A google search for 'backup linux image' gave me an overwhelming number of hits.  Maybe you could find something there.

---

### Post by jockyburns on 2011-12-01
I'm not entirely sure that you can make a complete installation disc , incorporating updates installed after the initial install. Best thing to do is to create either a bootable CD or USB for 11.10 and regularly backup your personal data etc to either usb or external HD or CD/DVD. 
If your present system crashes, corrupts or otherwise becomes unuseable, you can do a completely fresh install using the usb/CD, do the updates then use your backups to copy personal data back. 

I have 11.04 on a usb, reserved for just such an eventuality. (had a power cut a few weeks back and this managed to corrupt the OS) Just did a complete reinstall, updated then, copied my data back onto it from CD. Lost very little in the way of personal data.

---

### Post by EngineersGarage on 2011-12-01
I thought this is the place to go if you need help with Ubuntu??

Can I ask... 

[SIZE=3]**Has anyone ever made a bootable backup cd of their system?**[/SIZE]

If you have, please tell me/us, what you used and how you've done it as I am sure their must be Thousands of people wanting to do this... 
All my previous attemps following this tread came to zero successfull outputs. I could also just be a idiot that I may have missed something, so I will work through this thread from the beginning using "Remastersys" waste some more dvd's(as the other machine cant boot from usb-as ive never done that before) and just see were i get at... 
In the mean time, ANYBODY THAT KNOWS SOMETHING PLEASE LEAVE US WITH SOME OF UR EXPERIENCE AND KNOW HOW.

Thank you!

---

### Post by EngineersGarage on 2011-12-01
thats the thing... ive downloaded alot of programes and updates... I DO NOT WANT TO REDO ALL OF THAT AGAIN...once I made a new install... thats just wasting... I know you can do it...

BUT WITH UBUNTU... The question is HOW?

---

### Post by corncob on 2011-12-01
Before you even do that google search I suggested, you might take a look at 'ISO Master'.  Its in the Ubuntu Software Center.

---

### Post by EngineersGarage on 2011-12-01
After reading what Remastersys can do... I know there must be some how we can do it!

---

### Post by EngineersGarage on 2011-12-01
what do i do with it?? Just through all my files in there and create a iso from it??

---

### Post by EngineersGarage on 2011-12-01
will i be able to re-install ubuntu with all my updates and extra softwares on it?

---

### Post by EngineersGarage on 2011-12-01
can we delete this tread so that i can start a new one that will hopefully be short and sweet consirning the backup issue?

something that works  and doesnt cost Gigabytes of downloads to get this solved?

---

### Post by Glkanter on 2011-12-01
[SIZE=2]EG - Take a deep breath, and relax.

This is a great forum with some great folks that are knowledgeable and willing to help.

I asked a very similar question last April. Honestly, I never quite got the answer I "wanted".

I was trying to clone or ghost or make an image or something when I just started. I'll find the thread, and see what the best suggestions were.

You're going to really like Ubuntu, but I'm not sure why you're on 10.10.

Garry[/SIZE]

---

### Post by Glkanter on 2011-12-01
[SIZE=2]I wanted to copy and create a bootable hard drive. Never quite got it done, but I think maybe with some help I could, now.

[http://ubuntuforums.org/showthread.php?t=1730367](http://ubuntuforums.org/showthread.php?t=1730367)

Clonezilla and Brasero were highly recommended at the time. I have used both. Clonezilla back then, and Brasero a few times since then, and they are both robust and reliable.

Good luck![/SIZE]

---

### Post by Glkanter on 2011-12-01
[SIZE=2]And while it's none of my business, EG, I suggest you try to avoid responses that included phrasings like this:
> Hi, didnt you read what  I wrote?? I've already used REMASTERSYS. 

Please read all of what I said.You'll catch lots more flies with honey, rather than vinegar, on this forum.

Garry
[/SIZE]

---

### Post by EngineersGarage on 2011-12-01
Ok, Thank You...

10.10... i got it from a friend a couple of months ago...just never thought that i would ever use it as i was happy with using XP... but now im seriously fed up with Windows.. got Win32Vitro virus from a "friend" wanted some of his software. That managed to mess up my laptop, my home pc, my 3 ext hdd's.... so i thought i could maybe save my files,books, music, Irreplaceable pictures,etc with ubuntu and then just nuke the hdd's because apparently that is the only way to get rid of that virus. but now that i have ubuntu installed on a spare server of mine,  i thought i will actually stay with ubuntu and leave Windows in the ditch, bleeding itself to death! 

But before i can stick those hdd's in here i want to make a backup, as i have already downloaded alot of software and updates for this machine/ubuntu...

I will wait for ur reply.

Thanx again!

---

### Post by Glkanter on 2011-12-01
[SIZE=2]Caution: I'm the least Ubuntu-savvy guy you will encounter on this forum.

One of the great things about Ubuntu is the software updates and upgrades. They are painless.

So, before investing lots of time making backups, and having troubles with software, you may want to upgrade to 11.04 or 11.10.

But here's the thing: I cannot stand the new user interface called Unity. So I go through some steps to enable the old UI called something like Gnome Classic. It's not that hard to accomplish, but it's something I want to be sure you are aware of.

I have a PC, and Android phone, and an Android tablet. I am SO HAPPY to be done with Windows.

Garry[/SIZE]

---

### Post by Glkanter on 2011-12-01
[SIZE=2]So your original goal was to use Ubuntu as a HDD copying tool, because Windows was so infected?

One thing I've taken advantage of is Ubuntu's willingness to read various HDD formats.

I think I just stuck my old hard drives in my new Ubuntu system, and they were immediately recognized.

Now, there are a couple of really minor kinks. There's something fishy about a particular spreadsheet I try to read from there when opening it from the Calc program (I should just move it), and a music program acts weird with the music files from the HDDS, but the HDDS seem very secure and available otherwise.

Garry[/SIZE]

---

### Post by EngineersGarage on 2011-12-01
if i do the update to the newer versions of ubuntu, will i still have all the software i already installed?

Yes, my intension was to only Use Ubuntu to save my files,etc. knowing that it wont get infected with the virus so that i could run avast and remove the virus and make backup with of all my files.
But after thinking about it, I think I will loose XP and stay with Ubuntu, just have alot to learn from scratch again.
But i will have to have one pc for XP so that i can play games with my friends(our monthly lan's)... 
Or is there a way that I could use ubuntu to play my games, run my Cad Programes,etc.
I have 2 64bit servers, 3 desktops and 1 laptop...

---

### Post by Glkanter on 2011-12-01
[SIZE=2]The Ubuntu world is your oyster.

I think the upgrades are operating system only, so you would not lose anything. 

But, like I said, I'm the least knowledgeable guy here. Heck, I don't even know the proper terminology.

I suggest you prioritize your Ubuntu goals. You have a lot of them, and it's exciting, because the software is sooo much better than Windows, and it's all free.

Anyways, prioritize your issues, then very methodically address them one at a time. Starting a new thread with only one item on each, and start the next one only after the open thread has been resolved to your satisfaction.

Do a search of this forum before you start a thread, but you don't have to go crazy. I still post exclusively on the beginner's board, because I don't understand half of what everyone is talking about. On this board, it's ok to be a learner.

Garry[/SIZE]

---

### Post by EngineersGarage on 2011-12-01
Haha! Ok. let me do the updates... then i will see if i can make use of remastersys...

I'll be back later with updates!

Thanx G!

---

### Post by Glkanter on 2011-12-01
[SIZE=2]Here's a link I found regarding remastersys...

[http://www.remastersys.com/forums/index.php?topic=757.0](http://www.remastersys.com/forums/index.php?topic=757.0)[/SIZE]

---

### Post by Paddy Landau on 2011-12-01
@EngineersGarage:

I'd like to take a step back, because I'm reading something that may be a bit of a worry.

You say that you have downloaded and installed a number of programs.

Did you do that from the Ubuntu Software Centre, or did you do that using the Windows way -- searching the Internet, downloading programs, and installing them?

Installing programs on Ubuntu is dead easy. You go to the Ubuntu Software Centre (USC); find the program you want to install; and press the Install button. To deinstall, you do the same but press the Remove button. That's all. The USC takes care of downloading, installing, any dependencies, any conflicts that might arise, and deinstalling. The Update Manager will automatically download and install updates for you.

If you do not do it this way, you lose all of the advantages.

(Advanced topic: If you want to install a program that is not on the default repository, you find where that program's repository is located, add just that repository to the USC, then tell the USC to install your program.)

Most seasoned Ubuntu users back up only their data. Why? Because when the time comes to upgrade the system, they usually do a fresh install, which takes under an hour; install their extra programs (using the Ubuntu Software Centre); and finally restore their data.

It is so much easier than you are used to in Windows.

I used to back up my entire disk when I had Windows precisely because of the horror of reinstalling after viruses. At first, I did the same with Ubuntu; but I have found it takes more time to do it that way!

The other topic is that of an antivirus. An antivirus will do absolutely nothing on a Linux system other than protect any Windows users should you forward an email virus to them. Unless you forward many dodgy emails or run an email server, you might as well uninstall your antivirus. At the time of writing, there are no known Linux viruses in the wild.

If you are not behind a router, we can advise you on how to turn on your firewall.

---

### Post by BC59 on 2011-12-01
> **Paddy Landau said:**
>  Most seasoned Ubuntu users back up only their data. Why? Because when the time comes to upgrade the system, they usually do a fresh install, which takes under an hour; install their extra programs (using the Ubuntu Software Centre); and finally restore their data.

That's the central idea. That's why is so difficult to make the entire backup of the system. Because there is no reason to do it.
It's not like Windows where you have to buy and register the programs. In Linux you just press a button and you have installed the app in a matter of minutes, without passwords, original disks and strange code registrations, which work only once.

---

### Post by jockyburns on 2011-12-01
Last year I was running Win XP. After a power surge, I had no option but to re-install Win XP off the original discs. Once installed Win Update Manager connected to the internet and downloaded SP3 and a load of other updates. This took several hours, and I can't honestly see any other OS allowing you to make an install disc which includes all the latest updates you've downloaded and installed. Updates are brought out at regular intervals as an OS develops. Ubuntu certainly don't change the downloadable ISO everytime there's an update ,, Do they?

---

### Post by bigseb on 2011-12-01
GE,

I was in a similar situation to you i.e. sick of Windows wanted to change to something safer, quicker, more fun, etc. Now, Linux is great but it has some shortcomings... 

... One of them is the updates. Here in South Africa bandwidth is expensive and unreliable. It seems every time I turn on my system there are some kind of updates. Just too much for my time and wallet.

Another downfall is that much of my software doesn't work on Linux. I do CAD for a living and use Alibre Design, MoI, Keyshot and various part libraries daily. These don't (yet) gel too well with Linux so I have a Windows 7 partition too. On that note MoI (Moment of Inspiration - nurbs surface modellor) does now run in Wine.

To your original question regarding the backups... I would love to just install Linux on one machine, do all updates, install wine and virtualbox and whatever else I like in the repositories and save all of that to a disc so I can upload that as a 'new, complete OS' on my other machines. Would love to see an answer to this.

---

### Post by BC59 on 2011-12-01
I had a problem today and made a fresh install of my 11.10 in 1 hour and a half, included the updates. If you make a backup now and you have to reinstall the system after 4 months, you don't have to download all the updates again? Or you are going to make a 4 DVD backup of your system every 10 days?

---

### Post by EngineersGarage on 2011-12-01
I'm also from South Africa... and yes, bandwidth is slow and VERY expensive!!

To give an example, I was on 10.10, i'm busy upgrading to 11.04... I'm already over 2hours into it and the estimated time is still 1h20min left... so after this upgrade I will do all the updates and then I would wish to make use of Remastersys to make a backup... just in case I make a stuff up in my learning curve with this new OS( in my POV). and can then just start from there again...

O-yes, about the software... I have been using the software centre, I only downloaded a deb file of adobe flash player because i needed flash for some thing... got it eventually installed and its working now...

I'm a CAD designer and Cnc Programmer, I use Solid Works and Master Cam. Is there a programe that I could use on Ubuntu that will allow me to use those programes in ubuntu? or will I have to have a dif pc for that or partition?

---

### Post by bigseb on 2011-12-01
My bru, where are you? Cape Town?

---

### Post by EngineersGarage on 2011-12-01
No..PE

---

### Post by bigseb on 2011-12-01
> **EngineersGarage said:**
>  I use Solid Works and Master Cam. Is there a programe that I could use on Ubuntu that will allow me to use those programes in ubuntu? or will I have to have a dif pc for that or partition?

Never worked with MasterCAM so I wouldn't know about that. Solidworks might run in virtualbox but as you know SW is a real resourcehog so you'll prolly need a powerful PC for starters. Worth a shot though.

If you're hellbent on CAD in linux check out MoI3d. Only costs $295.

---

### Post by EngineersGarage on 2011-12-01
No...Its Xmas time and I dont want to spend that kind of money on software! lol...

I have a few good systems, I'll just dedicate one to the cad.

Have you tried remastersys yet??

---

### Post by bigseb on 2011-12-01
> **EngineersGarage said:**
> No..PE

Pity... I spent the last few days downloading the latest versions of Ubuntu, Kubuntu, Xubuntu and Mint. Puppy too. If you were here in CT I would have just made you copies and driven them over. Plenty to play around with then. Mint is lekker smart imo.

---

### Post by bigseb on 2011-12-01
> **EngineersGarage said:**
> No...Its Xmas time and I dont want to spend that kind of money on software! lol...

I have a few good systems, I'll just dedicate one to the cad.

Have you tried remastersys yet??

No. Got my 20 gig bundle from Vodacom today, just finished getting the updates  for mint (214Mb - took 2,5 hours to download). Going to start installing Virtualbox and Wine, also Gparted, warzone, and a few other goodies. At that point I would like to do my 'backup'.

---

### Post by EngineersGarage on 2011-12-01
what did you pay for that? I have adsl 5Gb Cap.

---

### Post by bigseb on 2011-12-01
> **engineersgarage said:**
> what did you pay for that? I have adsl 5gb cap.
  
r499

---

### Post by Paddy Landau on 2011-12-01
Some excellent questions, and I suppose that those of us lucky enough to have unlimited bandwidth take it for granted.

So, let me answer the questions.

> **bigseb said:**
> ... bandwidth is expensive and unreliable.
Fair comment. Please use [CloneZilla]("http://www.clonezilla.org/"). You can choose to back up your entire disk (including the boot-up bit), or only selected partitions. It is not intuitive to use, but once you've done it three times you'll find it easy as pie. It's reliable, and easy to restore (I know -- I've done it often to restore Windows after the kids have downloaded viruses!).

> **jockyburns said:**
> ... Win XP ... connected to the internet and downloaded SP3 and a load of other updates. This took several hours... Ubuntu certainly don't change the downloadable ISO everytime there's an update ,, Do they?
Indeed. Even Windows 7 drove me nuts with its updates. Download; install; reboot; download; install; reboot; download (yawn)...

Ubuntu, on the other hand, takes about 20 minutes to install and 20 minutes to download all the updates (assuming broadband, of course) and install them with just a single reboot. It's quick and easy.

> **EngineersGarage said:**
> I would wish to make use of Remastersys to make a backup...
Please look at CloneZilla. The wonderful thing about Ubuntu is that you can clone it to a different PC and it will still work. Ubuntu will just download any drivers the new computer needs. CloneZilla will let you do that -- restoring (or cloning) is quicker than making a copy using Remastersys and then having to re-install.

> **EngineersGarage said:**
> ... I only downloaded a deb file of adobe flash player because i needed flash for some thing... got it eventually installed and its working now...
Flash is in the repository. It should have been installed during the initial installation -- please ask if something like that is missing, so we can help you find it.

BTW, Wine... If you wish to use Wine, I strongly recommend that you use PlayOnLinux instead (it's in the repository). PlayOnLinux is a front-end for Wine, making it much easier to install and deinstall programs in Wine. In fact, I don't even know how to use Wine even though I use it, because PlayOnLinux has always handled Wine for me.

---

### Post by Ms. Daisy on 2011-12-01
> **Paddy Landau said:**
> Most seasoned Ubuntu users back up only their data. Why? Because when the time comes to upgrade the system, they usually do a fresh install, which takes under an hour; install their extra programs (using the Ubuntu Software Centre); and finally restore their data.

It is so much easier than you are used to in Windows.

I used to back up my entire disk when I had Windows precisely because of the horror of reinstalling after viruses. At first, I did the same with Ubuntu; but I have found it takes more time to do it that way! Thank you for that statement, Paddy!  That concept took me about 3 months to figure out on my own.  Backups in Ubuntu are VERY different than Windows, that's very important to understand.

You mentioned that you switched over because you were "fed up with viruses".  Paddy touched on this, and I would encourage you to read the link in my signature to learn about security on Ubuntu, which also requires a VERY different mindset than in Windows.

---

### Post by Karlchen on 2011-12-01
Hello, EngineersGarage.

If I remember right after reading 5 pages, your initial idea was doing a system backup using [**Remastersys**]("http://www.geekconnection.org/remastersys/").

Therefore, let me correct some of the details which were told about Remastersys in this thread and add a few details which have not been mentioned at all:

[LIST]
[*]Remastersys v2.0.18.1 can be got here: [**Remastersys (Karmic)**]("http://www.geekconnection.org/remastersys/repository/karmic/remastersys_2.0.18-1_all.deb")
[*]Though this version was created for Karmic Koala initially, it can be used on Lucid Lynx and on Maverich Meerkat as well. - Personally I have not tried it on anything newer.
[*]The development of the Ubuntu Remastersys version had been discontinued for some months. But by now the original author, fragadelic, has started to continue the Remastersys development. This is why he is currently working on Remastersys v3.0. - Personally I have not taken the time of testing it, yet.
[*]The best place to learn about Remastersys and to ask for help should be fragadelic's forum, section about Remastersys: [**Remastersys Help**]("http://www.remastersys.com/forums/index.php?board=38.0").
[*]Personally, I have created a small number of Karmic Koala and Lucid Lynx system backups (32-bit desktop versions) with the help of Remastersys v2.0.18.1. All of these system backups have been burnt to DVDs and could be booted and used as live systems on different machines (notebooks, desktop machines).
[*]In the meantime I have even figured out how to make sure that the ISO image of my system created by Remastersys can be booted by a multiboot USB stick by directly loading the ISO image (simple: add lupin-support and lupin-casper to your system before using Remastersys). This spares the hassle of actually burning the image to a DVD and there is no longer the need to sacrifice a complete USB stick and have only the Remastersys backup system on it.
[*]Keep in mind when doing a Remastersys system backup that the overall size of the backup system ISO image cannot exceed 4 GB in size.
 In order to keep your backup below this size limit you may have to exclude large data folders from the system backup.
Yet, after all it is a system backup. Data backups can be performed more efficiently using various other backup programmes.
[*]Before using Remastersys, consult the existing Remastersys tutorials, e.g.
+ [**Remastersys - Create custom Ubuntu (live) CD - Tutorial**]("http://www.dedoimedo.com/computers/remastersys.html")     
+ [**Make your own Ubuntu remix with Remastersys**]("http://www.psychocats.net/ubuntu/remastersys")
[/LIST]
[U]Summary:
[/U]
Creating a Maverick Meerkat system backup with the help of Remastersys is feasible. If you do it right the resulting ISO image file created by Remastersys will be bootable and usable as a live system and as an installation medium.

If the created CD / DVD is not usable, then you should check for error messages generated by Remastersys during the process of creating the ISO image. If there are none, the problem may have been caused by the burning software. It is essential to burn the ISO file as an image to the CD / DVD. Do not create a data CD / DVD holding the ISO file.
Sometimes it is helpful to instruct the burning software not to burn at full speed, but at a lower speed, 4 times or 8 times instead of 40 times or faster.
If this is not the source of trouble with the boot medium either, then there is always the chance that there is a technical problem affecting either the burning device or the device that refuses to read the boot CD / boot DVD properly. (This is why I love using USB sticks as boot devices.)

HTH,
Karl
--
In case by now you have decided to follow Paddy's advice and try CloneZilla instead of Remastersys, fine, definitely not a bad choice either.

---

### Post by EngineersGarage on 2011-12-02
WOW!! Geez, thanx guys for your support!!

I have noticed in all my attempts to use Remastersys, I had some failures... here is the log of my result.

Cannot stat source directory "/home/remastersys/remastersys/dummysys/" because No such file or directory
Cannot stat dir/file //home/will/.gvfs because Permission denied, ignoring
File //home/will/.cache/ubuntuone/log/syncdaemon.log changed size while reading filesystem, attempting to re-read

Failed to read file //home/will/.local/share/gvfs-metadata/home-23d0a916.log, creating empty file
llistxattr for //home/will/.local/share/gvfs-metadata/home-23d0a916.log failed in read_attrs, because No such file or directory
------------------------------------------------------
Mount information
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/will/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=will)
------------------------------------------------------
Disk size information
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              71G   17G   51G  25% /
none                  2.0G  492K  2.0G   1% /dev
none                  2.0G  196K  2.0G   1% /dev/shm
none                  2.0G  100K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
------------------------------------------------------

It said i should test it in virtual machine?? How do i do that? I've already wasted 3dvd's... the backup is only 1.8Gb... 
When I go look in home/remastersys/remastersys/custom-iso....1.8Gb

I have tried clonezilla, downloaded it, burned to dvd, booted from the disk, followed the instructions but at the end i forgot to first wipe my usb clean. After I realized(when the prgme told me the usb is full and has to terminate) so i wiped the usb, and when I wanted to redo all the steps, at the end where it actually has to do the clone part in that dos mode, it says failed something....i followed the exact same steps as before as i wrote them down 1-4-1... and ran into a brick wall!
So i thought remaster is easier,friendlier, and i want to use that aprouch. I have upgraded to 11.04 last night, but when i rebooted it told me that my hardware doesnt support unity and that i have to run in classic mode...im still working off my server and just want to get all these upgrades and updates to disk so that i can put it to my home pc and then just load ubuntu server on my server... not that i know how to use it properly, i just got it for really cheap so i took them, 3 64bit servers...

So, afer reading what u said, i might have a problem somewhere that i first have to sort out before attempting to use remastersys again...

Any idea how to do it?

o-yes before i forget, i firt used the 2.0sumting version of Remastersys when i had Ub10.10, I remember also seeing an failed error think it is the same one as my latest, then i downloaded the 3.0 version of Re, tried it,no luck, so i upgraded to Ub11.04, ran 3.0 and again have error(Failed some stuff)...
+ I dont know how to use virtual machine...

---

### Post by Paddy Landau on 2011-12-02
CloneZilla will work best of all when saving to an external USB hard drive. These days, in most countries at least, USB hard drives are cheap, and at least it will save you dozens of DVDs. (Good luck with your Remastersys; I've never used it, so I don't know how to make it work.)

---

### Post by EngineersGarage on 2011-12-02
> **Paddy Landau said:**
> Some excellent questions, and I suppose that those of us lucky enough to have unlimited bandwidth take it for granted.

So, let me answer the questions.


Fair comment. Please use [CloneZilla]("http://www.clonezilla.org/"). You can choose to back up your entire disk (including the boot-up bit), or only selected partitions. It is not intuitive to use, but once you've done it three times you'll find it easy as pie. It's reliable, and easy to restore (I know -- I've done it often to restore Windows after the kids have downloaded viruses!).


Indeed. Even Windows 7 drove me nuts with its updates. Download; install; reboot; download; install; reboot; download (yawn)...

Ubuntu, on the other hand, takes about 20 minutes to install and 20 minutes to download all the updates (assuming broadband, of course) and install them with just a single reboot. It's quick and easy.


Please look at CloneZilla. The wonderful thing about Ubuntu is that you can clone it to a different PC and it will still work. Ubuntu will just download any drivers the new computer needs. CloneZilla will let you do that -- restoring (or cloning) is quicker than making a copy using Remastersys and then having to re-install.


Flash is in the repository. It should have been installed during the initial installation -- please ask if something like that is missing, so we can help you find it.

BTW, Wine... If you wish to use Wine, I strongly recommend that you use PlayOnLinux instead (it's in the repository). PlayOnLinux is a front-end for Wine, making it much easier to install and deinstall programs in Wine. In fact, I don't even know how to use Wine even though I use it, because PlayOnLinux has always handled Wine for me.


What and where is the repository??

---

### Post by EngineersGarage on 2011-12-02
> **Paddy Landau said:**
> CloneZilla will work best of all when saving to an external USB hard drive. These days, in most countries at least, USB hard drives are cheap, and at least it will save you dozens of DVDs. (Good luck with your Remastersys; I've never used it, so I don't know how to make it work.)

 I wanted to use clonezilla but it doesnt want to work anymore??

---

### Post by bigseb on 2011-12-02
> **EngineersGarage said:**
> What and where is the repository??

Open up the software centre. Type in whatever software you're looking for and press install. Everything in there is from "*the repositories"*. Its the safest easiest way to install stuff. Synaptic does the same thing, gives you a bit more scope though. Personally I prefer Synaptic.

This is one area where Linux beats all other OS's imo. Safe and easy :)

---

### Post by corncob on 2011-12-02
> **EngineersGarage said:**
> if i do the update to the newer versions of ubuntu, will i still have all the software i already installed?

Yes

---

### Post by EngineersGarage on 2011-12-02
Ok cool, thanx...

Is Synaptic default? or do i have to download it?

---

### Post by EngineersGarage on 2011-12-02
Ive joined theRemastersys forum to get some help with it... So that i can update here and tell about my progress in Successfully using Remastersys... 
As to now, a beginner is toast to the working of ubuntu and thinking of a backup using Remaster... As i made fresh install, didnt change anything,only made some updates and new softwares, and cant get it to do backup... looks like you must make some changes to get it to work, thru my experience, but still await reply from the site...

how do i clean my machine? if i run janitor,will it remove valuable data?

---

### Post by Paddy Landau on 2011-12-02
> **EngineersGarage said:**
> What and where is the repository?
A *repository* is a place where applications are stored in a way that the *package manager* can access. There are two types of repositories: those that store the source code, and those that store the programs ready to use. You are interested in the latter. Programmers would be interested in the former.

The package manager can also update programs automatically.

**Ubuntu Software Centre**, **Synaptic Package Manager** and **Update Manager** are just three different ways to access the package manager. There are other ways.

The package managers stores a list of repositories approved on your machine. You can add to the list and remove from the list. If you start **Software Sources** on your computer, you can see a GUI method of adding to, and removing from, the list of repositories. The list is in fact stored in a file called [FONT=Fixedsys]/etc/apt/sources.list[/FONT], which you can look at -- but please don't modify it manually unless you know what you are doing.

> **EngineersGarage said:**
> Is Synaptic default? or do i have to download it?
If you wish to use Synaptic Package Manager, go to Ubuntu Software Centre and install it.

> **EngineersGarage said:**
> how do i clean my machine? if i run janitor,will it remove valuable data?
This is Linux, not Windows. It cleans itself. The Janitor can remove applications that you may want to keep, so best not to run it.

If you are desperately short of disk space, let us know and we can help you clean the computer, but it not would be much at all.

---

### Post by EngineersGarage on 2011-12-03
Thanx Paddy! Looks like I've got a long hill to climb still!:p

I have manage to use alot of space for someone who has done almost nothing on this pc.... Downloaded&Installed some apps and updates... Cant Imagine that its over 25Gb worth of software, there is no way!! 
How do i check where all this space is used? and to clean it up? i have barely done anything as I first want to make a backup...but everyday i just have less and less gigs on my hdd...how is this possible and how do i rectify it?

---

### Post by Paddy Landau on 2011-12-03
> **EngineersGarage said:**
> Thanx Paddy! Looks like I've got a long hill to climb still!:p
The main thing to remember is that there is usually a simple way to do something in Linux. If you are doing it a complicated way, stop and ask for help.

> **EngineersGarage said:**
> Cant Imagine that its over 25Gb worth of software, there is no way!!
My word, indeed not. My system (excluding my data), which includes several installed programs, takes only 5.5Gb.

I suspect it may be something to do with your having "downloaded" programs. That really is the wrong way to go about it.

Find the programs that you have downloaded. Perhaps you have kept the installation files, which can be deleted?

In your place, I would do this:

[LIST]
[*]Don't worry about the disk space for now (unless you are tight on space -- are you?).
[/LIST]

[LIST]
[*]The next release, Precise Pangolin 12.04, is due end of April. This will be a Long-Term Support (LTS) release. When it comes out, wait one month for the dust to settle.
[/LIST]
Then...
[LIST=1]
[*]Back up all your data. Ask on this forum if you have any doubts whatsoever about how to do this.
[*]Install 12.04, completely overwriting your current installation. But ensure that you install your system (i.e. root or "[FONT=Fixedsys]/[/FONT]") into a 10Gb partition, and your data (i.e. your [FONT=Fixedsys]/home[/FONT] folder) into a separate partition, as large as you like. Again, ask on the forum if you have any doubts about how to do this.
[*]Do not download programs, but instead install through Ubuntu Software Centre.
[/LIST]

---

### Post by EngineersGarage on 2011-12-03
Yes that is whayt i meant when i say ive downloaded programes...(used software centre to download and install new programes)

out of a 80Gb Hdd, I have like 51gb left...and havent even started loading My Own Stuff on yet...all programes from software centre... But i cant see it being that big..5gb max imo.

---

### Post by roger_1960 on 2011-12-03
Hi

Have you by any chance, in your efforts to backup, set up something like a daily backup using Deja Dup, backintime or similar programme.  That could quite quickly fill a hard drive!

---

### Post by jaimeaux on 2011-12-03
Have you tried using System Rescue CD and an external hard drive? Just boot up the disk, and run partimage. As long as you can navigate from the CLI it should be no problem.

---

### Post by EngineersGarage on 2011-12-04
All my ext hdd are infested with viruses win32vitro virus....i have to nuke the drives to get rid of the viruses...but before i nuke them i have to save my files...that is why i loaded ubuntu, because i cant do it on a window pc...it F up everymachine i tried to save my data with... that is why i want to backup ubuntu before i try saving my data...just in case something hapens..

And no, I havent used any other backup form other than Remastersys or clonezilla to wich i still have no success with with either one.

---

### Post by bigseb on 2011-12-04
Have a look at APTonCD, I stumbled across this yesterday. Might not be exactly what you want, could be of help though when it comes to saving downloads. Haven't worked with it myself though.

---

### Post by EngineersGarage on 2011-12-04
Thanx,

Will have a look at it!

---

### Post by EngineersGarage on 2011-12-04
how do i delete this folder? will it harm the system if i do?i want to clean up the system so that i can make backup.. 

i went to my computer,open the Hdd, then on top is a folder,2011-12-01-13-img. can i delete it? and How?

---

### Post by bigseb on 2011-12-04
> **Paddy Landau said:**
> My system (excluding my data), which includes several installed programs, takes only 5.5Gb.


Out of interests sake I looked at my own disk usage stats... was blown away... 50 gigs used!!! And that on a system I only installed a week ago. Then I subtracted the space for the vb drive and my personal data... still came to 13gig... a lot in my opinion :?

---

### Post by Paddy Landau on 2011-12-04
> **EngineersGarage said:**
> i went to my computer,open the Hdd, then on top is a folder,2011-12-01-13-img. can i delete it? and How?
It looks as though it is some sort of backup image, though I cannot be sure.

Either it is a mounted external drive, or it is saved on your root.

If it is something that is mounted, you don't delete it. If it is a file saved on your root, you can either:

[LIST]
[*]Press Alt-F2 and type:```
gksudo nautilus
```That will open Nautilus with root privileges. **Warning:** Be careful what you do in that window! Navigate to the file; delete it; empty the rubbish bin from that same window (otherwise it's not really deleted); then close the window.

or:
[*]Open a terminal and type the following command.```
sudo rm 2011-12-01-13-img
```
[/LIST]

---

### Post by bigseb on 2011-12-04
> **bigseb said:**
> Out of interests sake I looked at my own disk usage stats... was blown away... 50 gigs used!!! And that on a system I only installed a week ago. Then I subtracted the space for the vb drive and my personal data... still came to 13gig... a lot in my opinion :?

Just emptied trash... another 4Gb gone. All is well :D

EDIT: Just double checked... with trash, vbox and data taken into account the actual install with some extra software added only comes to 5Gb. Looks like Paddy was bang on...

---

### Post by EngineersGarage on 2011-12-05
Lol..Paddy's THE MAN!
 Im gona try it now!

---

### Post by magnon on 2011-12-06
> **EngineersGarage said:**
> how do i delete this folder? will it harm the system if i do?i want to clean up the system so that i can make backup.. 

i went to my computer,open the Hdd, then on top is a folder,2011-12-01-13-img. can i delete it? and How?

Hello there,

That is the normal naming convention that CloneZilla would use when you save a disk [save-disk] or partition [save-parts].

If that is what it is, then it's safe to delete.

-Magnon

---

### Post by Paddy Landau on 2011-12-06
> **EngineersGarage said:**
> Lol..Paddy's THE MAN!
Which man? :confused:

---

### Post by EngineersGarage on 2011-12-06
Ok thanx Mag! Hey Paddy!

I have reloaded my system with ubuntu server....then i couldnt use it because it was like in DOS mode...i couldnt do anything,nothing....only put in my username and password...
That sucked!!!wasted alot of time!!

Now ive loaded 11.10, ive made a backup of my software(10.10version) with AptCD(or something like that),
can I now install that backed-up software on the new version11.10??
((Please say yes, ive spent alot of Mb to download all those programes...))

After i do the installs then i want to try remastersys again on this new system.

---

### Post by Paddy Landau on 2011-12-06
I've not heard of AptCD, so sorry, I can't answer your question. As I say, I would have used the Ubuntu Software Centre to install applications. Bear in mind that different versions of Ubuntu may use different versions of applications; for example, Firefox for 11.10 is a little different from Firefox for 10.10.

---

### Post by EngineersGarage on 2011-12-06
APTonCD...is what i meant!

so you would suggest i install all new software for 11.10? 
would it damage the system if i had to install the software, that ive downloaded for10.10, from a backup cd that ive made?

---

### Post by Paddy Landau on 2011-12-06
I don't know APTonCD, sorry.

Honestly, I don't even know how you would "back up" software from Ubuntu in order to install on another installation.

In other words, I'm confused by what you are telling me!

The right way to install software is via the package manager, the easiest of course being the Ubuntu Software Centre (USC). For example, to install (say) GIMP (something like Photoshop), you open USC, search for GIMP, press Install, and you're done. The same would apply to Skype and Google Earth, to choose two other examples. There's no "download" and "install" process that you have to go through, as you would with Windows.

In rare cases, you first need to add a PPA (a repository) to your Software Sources, for example if you want to install Virtual Box. But once you've added the PPA, the process is the same: open USC, search for Virtual Box, and press Install.

(In very rare cases, there is no PPA. For example, to install Truecrypt, you have to download the "deb" file. But when you double-click the downloaded file, guess what... Yes, USC opens to install it for you.)

That's why I'm confused about your talk of downloading, installing and backing up your software.

---

### Post by beew on 2011-12-06
> **BC59 said:**
> Oups sorry!

With Remastersys there is a problem. The project was abandoned for some years so there was no support up to now. 

I don't know which version you used. There is a way to install it through PPA but the version installed is old of Karmic era.

The new developer created a Remastersys 3.0 beta which is here

[http://www.remastersys.com/repository/ubuntu-testing/](http://www.remastersys.com/repository/ubuntu-testing/)

A good guide on how to do it is here

[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys) (a little out of date)

So finally the problems you have are natural, because Remastersys does not collaborate perfectly with newer Ubuntu versions.

Try again to do it and hope it will work this time. And just install the .iso on a USB to check it and do not burn a DVD, to avoid the cost.

I think development has resumed, there was a thread in the Cafe very recently by the developer. Can search for it and may be ask a few questions.

---

### Post by beew on 2011-12-06
> **Paddy Landau said:**
> @EngineersGarage:

I'd like to take a step back, because I'm reading something that may be a bit of a worry.

You say that you have downloaded and installed a number of programs.

Did you do that from the Ubuntu Software Centre, or did you do that using the Windows way -- searching the Internet, downloading programs, and installing them?

Installing programs on Ubuntu is dead easy. You go to the Ubuntu Software Centre (USC); find the program you want to install; and press the Install button. To deinstall, you do the same but press the Remove button. That's all. The USC takes care of downloading, installing, any dependencies, any conflicts that might arise, and deinstalling. The Update Manager will automatically download and install updates for you.

If you do not do it this way, you lose all of the advantages.

(Advanced topic: If you want to install a program that is not on the default repository, you find where that program's repository is located, add just that repository to the USC, then tell the USC to install your program.)



Well I take exception. I install a lot of things from ppas, download a few debs and compile a few. The "Ubuntu way" is dead easy except that many of the offer in the repo are outdated and some just plain don't work.  How about finding minitube 1.3 in Natty's repo while 1.4 was available for Maverick in ppa even months before Natty's release? 1.3 was not only old, it plainly didn't work and 1.4 was the bug fix version.

Yes, you would have an easier time upgrading if you only install "the Ubuntu way" but I would rather do a clean install everytime while keeping my software functional and up to date.

Edited: Oh I see you are recommending ppas. That is not strictly "the Ubuntu way". :) My only difference is I install from ppas even if the software is in the official repo for the reasons above, I have made my Ubuntu box into a "quasi-rolling" OS, it is a lot more stable than having to update (and worse, "upgrade") every 6 moths (and risk breaking everything if you have a buggy new release like 11.10) just to get an updated software or just one that would actually work! (bug fixes doesn't go to the repo unless it is security related, if your app just crashes on you it is not security related)

---

### Post by Paddy Landau on 2011-12-07
> **beew said:**
> Well I take exception...
Bear in mind that the OP is a beginner posting in the Absolute Beginner Talk section. What you do is perfectly acceptable, but it's a bit more "advanced".

---

### Post by EngineersGarage on 2011-12-07
Lol...yeah, i still have my training wheels on! lol.

Paddy, no disrespect, i think you are too clever! that is why you dont understand what im trying to say! LOL!!HAHA!!

I dont know the "Ubuntu" terminology for installing and stuff like that yet.... But to give peace of mind, i did use USC for all my software,i opened USC-chose some Apps and clicked on the install button(to me that is downloading programes) accept Adobe_FlashPlayer wich i downloaded from the adobe site a Deb file(Flash player). and the author of Remastersys sent me via email the new Remastersys3.0.0.1.deb which i doubleclicked on went to USC and pressed the install button(to me that is installing programes on ubuntu)

I have now wiped my system, LOADED 11.10, which I dont like, it doesnt seem to work propperly.
[SIZE=4][COLOR=Red]
DO NOT DOWNLOAD THE 11.10 VERSION, IT SUCKS!!!!!!!!!!![/COLOR][/SIZE]

Im going to switch back to 10.10 and then use my cd that ive made using APTonCD to create a backup of all the Apps that ive installed using the USC to get my system the way it was in the beginning and the way i Liked IT!

What do you reckon? Will i be making a mistake?

---

### Post by EngineersGarage on 2011-12-07
How do you unmount something? just have a look at the attachedment to see what i meen...

---

### Post by Paddy Landau on 2011-12-07
> **EngineersGarage said:**
> ... [except] Adobe_FlashPlayer...
That is also on the repositories. When you install, you are given the options to download updates and install licensed software. Tick them both, and Flash should install automatically.

> **EngineersGarage said:**
> LOADED 11.10, which I dont like, it doesnt seem to work propperly.

DO NOT DOWNLOAD THE 11.10 VERSION, IT SUCKS!!!!!!!!!!!
That is your experience and a very general statement. If you are having problems, please start a new thread asking for help, being *specific* about your problem. It would be better to get it working, so that when the next LTS comes out (in April), you can install it without suffering from problems.

> **EngineersGarage said:**
> Im going to switch back to 10.10 and then use my cd that ive made using APTonCD to create a backup of all the Apps that ive installed using the USC to get my system the way it was in the beginning and the way i Liked IT!
Well, it may work. You can try.

> **EngineersGarage said:**
> How do you unmount something? just have a look at the attachedment to see what i meen...
Looking at your error, I suspect that you have your CD open in Nautilus (your file browser). I have not seen that error before, so I am not sure. If you log out, you should be able to eject your CD without problem, because logging out will release all locks.

---

### Post by bigseb on 2011-12-08
EG:

Listen to Paddy. You have to break the Windows mindset of backups, installing software, etc. Ubuntu, and Linux in general, is so incredibly simple to get going. In fact you should be able to do 95% of your general PC stuff out the box. If you don't like Ubuntu then use a different distro. They are veyr similar under the hood, its really just the looks (UI) that different. I hated the new Ubuntu look too so I tried them all and ended up using Mint. I do think though you should rather use a new distro as opposed to one that already a year old.

Try a different distro and play around with it as is. I only installed a main menu organiser (alacarte), a start_up manager, proprietry Nvidia drivers, Clementine (removed Banshee) and did the updates. Thats my basic OS right there. All of that only used 300MB too. Then obviously I started added other stuff. Give it a bash and for get the Window. way

---

### Post by EngineersGarage on 2011-12-08
I was looking at mint and peppermint last nite... what ive read is that mint 12 is buggy? and peppermint is super fast...?

you have any experience with these?

---

### Post by EngineersGarage on 2011-12-08
oh yes, and do you get the same software for these OS as for ubuntu?? or most of them compatible?

---

### Post by bigseb on 2011-12-08
> **EngineersGarage said:**
> oh yes, and do you get the same software for these OS as for ubuntu?? or most of them compatible?


Yep, for the most part they're all the same. Shouldn't be any compatibility issues.

---

### Post by EngineersGarage on 2011-12-09
just a quick question, If i have Xp on my laptop and Ubuntu, and I want to check for viruses on a friends Hdd before I download some of his apps &stuff. Can I boot in Ubuntu, then plug in his hdd and run a virus check and not worry that if there is one that it wont jump over to my Xp partition?
And if there was a virus found, could i use say Avast for ubuntu to remove the virus then bot the hdd in my Xp installation to copy over the apps and know that i would be safe following this procedure??

Thanx.

---

### Post by bigseb on 2011-12-09
> **EngineersGarage said:**
> just a quick question, If i have Xp on my laptop and Ubuntu, and I want to check for viruses on a friends Hdd before I download some of his apps &stuff. Can I boot in Ubuntu, then plug in his hdd and run a virus check and not worry that if there is one that it wont jump over to my Xp partition?
And if there was a virus found, could i use say Avast for ubuntu to remove the virus then bot the hdd in my Xp installation to copy over the apps and know that i would be safe following this procedure??

Thanx.

The admins will probably tell you to start a new thread but I'll answer quickly. If you're worried about viruses here's what you do: buy all your software from a store or download directly from a very reputable site in the case of drivers and stuff. Most importantly keep your machine up to date. Windows 7 has brilliant safety feature that come installed. Use them properly and you most likely won't need an anti-virus. The second you start sharing stuff you're asking for trouble.

---

### Post by EngineersGarage on 2011-12-09
thanx...


i also read that mint 9 has its own backup programe where i can create my own live cd with just the install files or i could through in all the aps and settings almost similar to remastersys would do..

something i still havent got to get right yet.

---

### Post by lsemmens on 2011-12-09
I have a similar issue but not backup related. I am currently running Ubuntu (11.10) from a USB stick on a laptop with no HDD but none of my settings/passwords seem to be saved to my stick so I have to "re-install" everything after a re-boot. 

As to a complete backup of everything. A possibility, though a) not free and, b) not Linux, is the use of Norton Ghost which will do a, IIRC, byte by byte image of your HDD or just a normal clone of the OS partition.

---

### Post by Paddy Landau on 2011-12-09
> **lsemmens said:**
> I have a similar issue but not backup related. I am currently running Ubuntu from a USB stick on a laptop with no HDD but none of my settings/passwords seem to be saved to my stick so I have to "re-install" everything after a re-boot.
When you create your Live USB, you must specify "persistence". The instructions are on the [download page]("http://www.ubuntu.com/download/ubuntu/download").

> **lsemmens said:**
> As to a complete backup of everything. A possibility, though a) not free and, b) not Linux, is the use of Norton Ghost which will do a, IIRC, byte by byte image of your HDD or just a normal clone of the OS partition.
We've already discussed [CloneZilla]("http://clonezilla.org/"), a free (albeit not as user-friendly) alternative.

---

### Post by EngineersGarage on 2011-12-10
I havent tried clonezilla again...i will try that on my other machine that has 11.10 on it.may this time it will work. 

Im still confused why it didnt want to work the second time i tried to use it....1st time it went half way through the process then told me my usb is full. so i formated the thing and second time it kempt on giving errors.. aanyway...will try it later

---

### Post by lsemmens on 2011-12-10
> **Paddy Landau said:**
> When you create your Live USB, you must specify "persistence". The instructions are on the [download page]("http://www.ubuntu.com/download/ubuntu/download").Thanks Paddy, got that sorted.


> We've already discussed [CloneZilla]("http://clonezilla.org/"), a free (albeit not as user-friendly) alternative,I realised that. I'm not familiar with that package, but just suggesting an alternative that may work.

---

### Post by noobed on 2011-12-10
Ran into this problem myself a few days ago.. Luckily found this website to help me out..:D

[http://maketecheasier.com/backup-instal-your-linux-applications-with-aptoncd/2009/06/13](http://maketecheasier.com/backup-instal-your-linux-applications-with-aptoncd/2009/06/13)

---

### Post by mastablasta on 2011-12-10
> **noobed said:**
> Ran into this problem myself a few days ago.. Luckily found this website to help me out..:D

[http://maketecheasier.com/backup-instal-your-linux-applications-with-aptoncd/2009/06/13](http://maketecheasier.com/backup-instal-your-linux-applications-with-aptoncd/2009/06/13)


is that like remastersys? does it only create image of system or a LiveCD/DVD?

---

### Post by Paddy Landau on 2011-12-10
> **mastablasta said:**
> is that like remastersys? does it only create image of system or a LiveCD/DVD?
If you read the post, you'll see that it makes a copy of the cached packages from the source machine to the target machine. That allows you to use the package manager (apt-get, Synaptic Package Manager or Ubuntu Software Centre according to your personal preference) to install those programs without being connected to the Internet.

Of course, if you are going up a version of Ubuntu, it means that some of the packages will be out of date; but that's better than not having them at all.

---

### Post by EngineersGarage on 2011-12-10
Paddy...Hi,

Can I use software that i had on 10.10 and made a backup of on mint9? or will there be compatibility issues?

---

### Post by Elfy on 2011-12-10
This is now turning to a different subject - which you have now created a new thread for - use that for the new subject. 

Closed

[http://ubuntuforums.org/showthread.php?t=1893420](http://ubuntuforums.org/showthread.php?t=1893420)

---


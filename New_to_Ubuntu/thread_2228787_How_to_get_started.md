---
title: "How to get started"
date: 2014-06-09
forum: New to Ubuntu
---

### Post by peter118 on 2014-06-09
I downloaded the latest version  of Ubuntu. When it finishes the download it is in rar format. I keep reading about burning the iso image but where is it? During the download it says it is downloading a .iso file but when it finishes I'm left with a rar. I unzip it and can't see any .iso file. There is an installer icon but I do not want to install  it on the cpu I am currently using.  What I am trying to do is make a bootable disk. I just formatted an XP computer. First boot device is the DVD drive but when I boot with the disk I created it says to insert a system or boot disk or something. The cpu I am using to download uses Windows 7. So in a nutshell How can I make a disk that I can use to install Ubuntu on an already formatted cpu. This is taking a lot longer than I figured. Thank you to anyone who can help

---

### Post by Vladlenin5000 on 2014-06-09
Hi, welcome.

From where are you downloading and with what software (and OS)?

---

### Post by monkeybrain20122 on 2014-06-09
You should download the iso here [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
Obviously you downloaded it from somehwere else, no Linux site would put the download in .rar.

---

### Post by LastDino on 2014-06-09
Is your WinRAR set to open ISO? It might be that you're simply seeing the RAR icon. Check the extension of the file downloaded, you should probably enable show extension from windows tools in your my computer. It helps you more than most antivirus and malware  detectors do :P

Please link us where you downloaded from, if what I'm guessing is not right, then download that ISO from link monkeybrain provided.

---

### Post by oldos2er on 2014-06-09
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by 3rdalbum on 2014-06-09
It is not a Rar, it's an ISO. If you have WinRAR installed it will show a WinRAR icon but the file is an ISO. Do not open the file, just burn it using the "Burn Image to Disc" function of your burning software.

---

### Post by peter118 on 2014-06-10
I downloaded from this site. The cpu I am downloading with is new with Windows 7. So I am still getting used to that having used XP for years. I have an old Sony Vaio that was my XP cpu that I was hoping I could install Ubuntu on. When the download is finished the icon for the file shows that it is a wjnrar file not iso. During the download however Internet Explorer in the view downloads window says it is an .iso file, So I'm still trying to grasp how Windows7 works besides getting Ubuntu. . Sorry for being such a newb and thanks for all your help

---

### Post by peter118 on 2014-06-10
That is where I downloaded from monkeybrain20122. I downloaded the 32bit version since my old Sony Vaio only has 512M ram. Thank you

---

### Post by peter118 on 2014-06-10
Thanks LastDino. I will check that out.

---

### Post by peter118 on 2014-06-10
Thanks 3rdalbum.. You were right. Nero10 saw the rar as an iso and burned it to disk. It is now installing as I type this.. Everything is new to me on this Windows 7 cpu including the burning software so it's just another learning curve. Just can't figure out why downloads are being saved as rar files or at least with the WinRAR icon. Another learning curve here again. Thanks to all for your help and I will report back once Ubuntu finishes the install Cheers  :D

---

### Post by LastDino on 2014-06-10
They are not saved as RAR, they are showing RAR icon because when you installed RAR you selected ISO extension to open with RAR by default. By the way, there is nothing wrong with it, so no need to worry. Just turn on the ''show extension of files'' option, it should be there in tools option of my computer. Or google that, I don't use windows so I can't be more specific about how to enable it, sorry. But simply typing ''show extension of files in W7'' should lead you to thousands of results guiding on how to.

---

### Post by peter118 on 2014-06-10
Ok so I passed one hurdle and was able to finally get ubuntu .iso file burned to disk. I loaded it into  my dvd /cd burner and rebooted. It saw the disk and began goin thru the install process. When finished I rebooted as instructed took out the install disk and waited for the cpu to boot. It got as far as a blank page with just the word Ubuntu on it and it stayed like that for over an hour before I just shut off the cpu. At this point I don't know what else to do. Frustrated!!!!!!!!

---

### Post by Vladlenin5000 on 2014-06-10
At this point you need to provide detailed information about your hardware in order for someone to figure out what you need to change in the boot options...

---

### Post by oldos2er on 2014-06-10
A small bit of googling tells me Ubuntu could be problematic on some older Sony Vaio's. Perhaps you should give Xubuntu or Lubuntu a try, they have lighter system requirements than plain Ubuntu.

---

### Post by beameup on 2014-06-11
If that Rar icon is confusing, it can easily be changed by opening winRar, go into settings and uncheck the box next to .iso in file associations.

screenshots: [http://winrar.software.informer.com/screenshot/37356/](http://winrar.software.informer.com/screenshot/37356/)

And oldos2er is right. You should try Xubuntu or Lubuntu for their lighter system requirements on older hardware.

---

### Post by peter118 on 2014-06-13
Ok so I burned the image onto a disk and went through the whole install process, rebooted ( the disc was ejected) and printed my username and password and  all I get is the word "Ubuntu" on the screen. Stayed like that for an hour. Is there no desktop of some sort. This is just too crazy. Seriously I didn't think it would be this complicated. Thanks again to anyone with help for this.

---

### Post by peter118 on 2014-06-13
Thank you very much

---

### Post by peter118 on 2014-06-13
Thank you oldos2er

---

### Post by peter118 on 2014-06-13
My cpu is a Sony Vaio Pentium 4  2Ghz processor with 512Meg of ram. 64Meg built in video card and that's about it.

---

### Post by yancek on 2014-06-13
The Ubuntu minimum hardware requirements site below shows 512MB RAM as the minimum required.  If you get it installed with that it won't run well.  You might try running something lighter like Lubuntu or Xubuntu or Bodhi Linux.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by sudodus on 2014-06-14
> **peter118 said:**
> My cpu is a Sony Vaio Pentium 4  2Ghz processor with 512Meg of ram. 64Meg built in video card and that's about it.

Standard Ubuntu will not work well below 2 GB RAM. With only 512 MB RAM I recommend Lubuntu 14.04 LTS, which has an ultra-light desktop environment, and can perform fairly well with your hardware.

You may still have problems with the graphics chip and wifi chip. If you specify them, it will be easier to give relevant advice.

---

### Post by Topsiho on 2014-06-14
As a (once upon a time, math) teacher I simply can't resist the temptation to inform you that a computer and a cpu are not the same thing :)
A cpu is one of the parts in a computer system, the chip that does the processing of the commands given to the computer (Central Processing Unit). The processor that you mention.

I agree with those who advise to install Lubuntu (or Xubuntu) on this lightweight system of yours. Probably will run much better. Three of my four systems run very badly on Ubuntu, but reasonably well on Lubuntu or Xubuntu. Even using Firefox and LibreOffice, which I think are heavyweight.

Topsiho

---

### Post by peter118 on 2014-06-14
Thank you Yanek. Once I find a lighter version of Ubuntu I will give it a go. Thanks to all for your help so far  :D

---

### Post by peter118 on 2014-06-14
Graphics chip is An Intel and wifi I don't know. Since I formatted the Sony I do not have more detailed info. I just know that the video chip was built in to the motherboard. Thank you Sudodus

---

### Post by peter118 on 2014-06-14
Thank you Topsiho. You are correct. I type slow and if I can abbreviate when I can I do. The CPU in my Sony Vaio computer is a Pentium 4/ 2Ghz . Thank you  :D

---

### Post by sudodus on 2014-06-14
> **peter118 said:**
> Thank you Yanek. Once I find a lighter version of Ubuntu I will give it a go. Thanks to all for your help so far  :D

Xubuntu is a medium light version of Ubuntu. It needs 1 GB RAM to run well. Lubuntu is an ultra light version of Ubuntu. It needs 512 MB RAM to run well, but in order to browse the internet you may need more RAM and a more powerful CPU (depending on the web sites).

[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

---

### Post by rado1 on 2014-06-14
Once i tried to install ubuntu and lubuntu on laptop with cpu that was not supporting pae flag.
this might clear things : [https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

---

### Post by mörgæs on 2014-06-14
This is a Pentium 4 so no PAE problem here.

---

### Post by peter118 on 2014-06-16
I have installed Lubuntu finally and it seems to be ok. A little slower than I thought but it is ok. Having used Windows for so long I imagine there is a bit of a learning curve. How does the OS detect a printer or external hard drive. Also I made two partitions. It is a small HD to begin with (60gig) so when I was installing Lubuntu I made a 10G and a 50G partition. I tried to format the 50G to NTFS but it would not. I had backed up the files on the Sony before I formatted it to that external Seagate 2T HD and was hoping to retrieve them. My printer is a HP photosmart p1000. I have some Avery templates saved (I hope) in my back up and would like to  get some printed off. I was hoping when I installed Lubuntu that things would be detected  and away you go but I guess not. Again any help would be appreciated.

---

### Post by LastDino on 2014-06-16
You can't format drive into NTFS during installation. 10 GB is probably insufficient if that's the only partition you're planning to assign Linux. Hit the mark of 25GB, if both ''/'' and ''/home'' are to be on same partition. 
Google bit for ''Linux file system'' and ''partitions required for installation of Linux''. 

Post different threads for printer configuration, external HD should be detected though. Linux has no problem in using NTFS/FAT32 for data storage.

---

### Post by peter118 on 2014-06-17
Thanks LastDino. The partitions were made during install, After install I tried to format the 50G partition as NTFS. Ok I will try to increase the 10G partition.

---

### Post by mörgæs on 2014-06-17
Why do you want NTFS?

---

### Post by peter118 on 2014-06-17
I have software that I would like to use such as Avery label maker and I cannot install it with Lubuntu. Thought if it was formatted NTFS I could install these programs. . Lubuntu finally saw my External HD and I managed to get my printer recognized so I am making some progress. Downloaded onboard audio utility for my motherboard but that won't install either. Everything is windows based. My back up files on the Seagate 2T EHD associated with ;for example Avery, won't open without the Avery program installed. I can't or don't know how I would be able to install something like Avery. The whole idea behind installing Lubuntu was to make my computer run quicker. When XP was on there it took forever to get started with the updates from AVG and ASC and who knows what. The drive was just cluttered with apps and the hard drive would be spinninig forever before I could do anything with it, and the computer is too old to install Windows 7 or higher. So here I am.  Also trying to enlarge a partition but am lost. My hard drive is only 60G and when I click on disks it shows me as having 4 partitions. 10G home, 50G extended, 50G file system and a 500M swap partition. I was trying to enlarge the 10G as suggested by someone in this thread. I suppose I could transfer everything to  my new Windows 7 computer but the Sony Vaio still works and I thought I could keep it to run some apps such as Avery and not be bogged down by virus and cleanup software slowing things to a crawl like with XP.
Anyway that was my plan but it is proving to be a much tougher ask than I expected. Thanks to all for your help and advice.

---

### Post by 3rdalbum on 2014-06-17
> **peter118 said:**
> I have software that I would like to use such as Avery label maker and I cannot install it with Lubuntu. Thought if it was formatted NTFS I could install these programs.

Sorry mate, this is a different operating system, not just "a lighter Windows". Windows programs don't run - well, there's an exception, if you install Wine you can run some Windows programs, but this is pretty much a last-resort as not many Windows programs work. NTFS will not help, it's only a filesystem (a way of arranging the files on disk).

You can try Wine for your label-making software, but don't be surprised if it doesn't work. It might not talk to your printer, either; I'm not sure how good Wine is at talking to Linux printers.

> Downloaded onboard audio utility for my motherboard but that won't install either.

No, Windows drivers won't work on Linux. Wine or no Wine. If you can hear sounds on your Lubuntu machine then you already have the audio driver.

---

### Post by mörgæs on 2014-06-17
In stead of dealing with NTFS and other partition problems I suggest a fresh install where you let Lubuntu make all the decisions. Just follow the defaults and it will choose ext4 for data and a swap partition of the correct size.

After that we can take a look at Wine - or maybe even better, applications like Glabels.

---

### Post by LastDino on 2014-06-17
> **mörgæs said:**
> In stead of dealing with NTFS and other partition problems I suggest a fresh install where you let Lubuntu make all the decisions. Just follow the defaults and it will choose ext4 for data and a swap partition of the correct size.

After that we can take a look at Wine - or maybe even better, applications like Glabels.

+ 1 to this and post above this as well.

Your life would be much easier if you forgot about making NTFS as that HD is going to contain only one OS; Lubuntu.

---

### Post by oldos2er on 2014-06-17
Maybe a read through [Linux is not Windows]("http://linux.oneandoneis2.org/LNW.htm") is in order.

Although Linux can read and write to NTFS partitions, it cannot use NTFS partitions as its system (including /home/) partitions; NTFS doesn't support Linux file system permissions.

---

### Post by Topsiho on 2014-06-18
HP printers and scanners are, generally speaking, well supported in Linux. Just make sure hplip is installed.

Topsiho

---

### Post by peter118 on 2014-06-20
Thanks to all. Will tackle these hurdles as time permits. Being summer and all  am not at the computer as much. ;) Cheers

---


---
title: "step zero"
date: 2020-03-08
forum: New to Ubuntu
---

### Post by seeker17 on 2020-03-08
Hello.
Very new to Ubuntu.
Still trying to install.

I downloaded the iso file for Ubuntu.  
When I clicked on it I was asked to burn to DVD.
So I did.

I now have an approximately 2 GB file on a DVD.
How do I use it to install Ubuntu?

I was told I can "dual boot" Ubuntu from a Windows computer, which is what I am trying to do.

But every time I click on the DVD I am asked what I want to use to open it.

When I explore the DVD there are a number of files, but clicking none of them starts any process.

What am I missing?

---

### Post by CatKiller on 2020-03-08
> **seeker17 said:**
> I now have an approximately 2 GB file on a DVD.
...
What am I missing?

The install image is an *image*. Most burning software can handle those. That's what you need to do, rather than just copying the file onto a DVD. That will give you a whole bunch of files on the DVD with weird sounding names rather than a single file. You can then boot from that to try out or install Ubuntu.

You'll probably need to change a setting in the BIOS/UEFI to tell your computer to boot from the DVD drive rather than your hard drive.

---

### Post by MoebusNet on 2020-03-08
This will explain how to burn the Ubuntu .iso file to a DVD:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
This is useful if you want to or must use an optical drive.

This will explain how to use a USB Flash Drive to install Ubuntu:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
This is useful if you do not have an optical drive and can boot from USB.

---

### Post by sdsurfer on 2020-03-09
And this explains how to set up a dual boot with Windows using GRUB2.
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by mastablasta on 2020-03-10
you need to boot from the DVD or USB: [https://ubuntu.com/tutorials/tutorial-install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/tutorial-install-ubuntu-desktop#1-overview)

before you commit to install, try it out. if you plan dual boot make sure you prepare the disk first with some free unformatted disk space. 

windows 10 with secure boot complicates the install of additional OS. and you will likely install in UEFI mode: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

f you just want to toy around with Ubuntu, then i suggest an installation inside virtualbox: [https://itsfoss.com/install-linux-in-virtualbox/](https://itsfoss.com/install-linux-in-virtualbox/)
this one is the safest option as it won't make any changes to current OS and you can just delete it after you are done playing.

---

### Post by seeker17 on 2020-03-15
Of course!  Thank you everyone.  I just realized that when I installed my old software into my new Windows 10 computer I neglected to install my burning software.  
I will do so immediately and burn the iso.

As far as booting from the DVD, I planned to install Ubuntu on my older Windows 7 computer.  I've played around with Ubuntu years ago and am ready to commit to using it as a working computer.

I read the section on UEFI.  I will be dual booting with Windows 7.

How does one get a computer with only Ubuntu on it?  Does one have to buy it like that?

Thank you everyone for the advice.  I'll see how it works.

---

### Post by ipv on 2020-03-15
> **seeker17 said:**
> How does one get a computer with only Ubuntu on it?  Does one have to buy it like that?

you can buy a dos desktop / laptop which basically means a computer sans an operating system, install ubuntu & during installation let ubuntu use the entire hard disk.

---

### Post by CatKiller on 2020-03-15
> **seeker17 said:**
> How does one get a computer with only Ubuntu on it?  Does one have to buy it like that?

It's not clear what you mean by that question. *Nuke everything and just install Ubuntu* is one of the options (it might even be the default option) in the installer.

Otherwise you can buy a computer with Ubuntu pre-installed, or build or buy a computer with no OS installed and then install Ubuntu onto it, or buy a computer with a different OS installed and install Ubuntu instead of that OS.

---

### Post by seeker17 on 2020-03-15
Thanks for the information about buying a computer with only Ubuntu on it (where?) or an computer with no operating system.

But it appears I have a more fundamental problem.

I installed Nero to burn a DVD of the iso but I guess I don't really know what settings to use. 

None of what I tried would make a DVD that actually installed  Ubuntu.[ATTACH=CONFIG]285222[/ATTACH]  Here is one of the Nero dashboards.  If anyone is familiar with Nero and can tell me what to do I would be most appreciative.
I did set to compilation and got a single file instead of an explorer set of individual files, but Windows asked me what program I wanted to use to open it.  I guess i still created the wrong type of file.
I really want to do this but I guess i am not creating the right type of DVD.
Thank you.

---

### Post by Impavidus on 2020-03-15
As you already have a new Windows 10 computer, do you really need to keep your Windows 7 system? If not, you can simply wipe it and install Ubuntu. Simplest way is to use the Ubuntu installer and tell it to wipe the entire hard drive and install Ubuntu. It's the first option.

---

### Post by CatKiller on 2020-03-15
> **seeker17 said:**
> If anyone is familiar with Nero and can tell me what to do I would be most appreciative.
Not familiar at all: I haven't used Windows for 15 years. From the screenshot you showed, the DVD Copy option would seem to be the most likely, with your iso file as the source rather than a disc in the drive, but I have no idea what's lower down in that window. There may be an option labelled up specifically for burning an image.

---

### Post by ajgreeny on 2020-03-15
Like CatKiller I haven't used Windows for about 15 years, so O don't know Nero either but it didn't take long to find [this site]("https://neroknowhow.com/2016/05/10/how-can-i-create-and-burn-iso-images-with-nero-burning-rom/") with a search for "burn iso image with nero".

---

### Post by oldrocker99 on 2020-03-15
What you need is a Nero option to "burn an image." That is how to do it. A far better way is to burn the .iso to a USB thumb drive, using the free program Rufus, which works like a champ. 

Win7 is no longer supported, and is very vulnerable, so copy all the personal information to another drive and use the whole disk to install Ubuntu, or any other Linux version. You'll have a very stable, incredibly secure operating system, with which you can do anything you want a computer to do.

Here's a detailed page on how to install Ubuntu with a separate /home partition, which is highly desirable.

[https://www.psychocats.net/ubuntu/installseparatehome](https://www.psychocats.net/ubuntu/installseparatehome)

Don't be afraid to ask questions. Every one of us were complete newbies at the beginning!

---

### Post by ipv on 2020-03-15
> **seeker17 said:**
> If anyone is familiar with Nero and can tell me what to do I would be most appreciative.

you do not need nero.

windows 7 can burn .iso to disc with out the need for any software. just right click on the .iso & click on **burn disc image**.

in the next step you choose the drive which is your **dvd drive** & then click on **burn**.

have a look here : [https://www.howtogeek.com/80094/how-to-burn-an-iso-image-in-windows-7/](https://www.howtogeek.com/80094/how-to-burn-an-iso-image-in-windows-7/)

---

### Post by TheFu on 2020-03-15
For completeness, ubuntu team/official documentation:
[LIST]
[*][https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[*]Windows: [https://ubuntu.com/tutorials/tutorial-burn-a-dvd-on-windows](https://ubuntu.com/tutorials/tutorial-burn-a-dvd-on-windows)
[*]OSX: [https://ubuntu.com/tutorials/tutorial-burn-a-dvd-on-macos](https://ubuntu.com/tutorials/tutorial-burn-a-dvd-on-macos)
[*]Ubuntu: [https://discourse.ubuntu.com/t/how-to-burn-a-dvd-on-ubuntu/](https://discourse.ubuntu.com/t/how-to-burn-a-dvd-on-ubuntu/)
[/LIST]

Pick your poison (instructions of choice).

Most of us would use a flash drive to install any linux OS.  Keeping a flash drive around with an Ubuntu Desktop flavor is smart.  This flash drive isn't just for installing, but should anythng bad happen, it is also a "Try Ubuntu" environment useful to troubleshoot another install, backup any data from other disks, and have a way to hop on the internet quickly should you accidentally screw something up.  People new to any OS often screw things up, as they learn.

i would strongly push towards using a virtual machine for the first few months to see what can be done.

i would also say there are some things that still only work on Windows, but for me, that list is down to 3 things.  The other 20,000+ things i use computers for work better on Linux than Windows or OSX.  i still use Wndows almost daily, but haven't installed it in about 10 yrs. 

Nothing against the other provided links, just we should probably share the guides created by ubuntu-centric, knowledgeable people, from clearly reputably web domains.

---

### Post by seeker17 on 2020-03-22
Yes, Impavidus, I could use the installer to wipe Windows 7 and install Ubuntu, but I like to do things in small steps.  But I have a more fundamental problem.  I don't seem to be able to correctly burn the Ubuntu installer DVD.  Thank you, CatKiller & ajgreeny.  Ajgreeny, if oldrocker99's advice regarding Rufus and a thumb drive doesn't work I will try that. I will try to follow those instructions on the Nero page.  And thank you, oldrocker99.  That was fascinating about the separate home partition.  Because I am just learning, I will not do that yet, but I see the point of it.  As to Windows 7, I have already moved all my files to the new Windows 10 computer.  I left next to nothing on the Windows 7 computer other than a few programs.

So ipv, I actually tried burning the DVD without Nero, just using Windows 7.  I'll have to see what i did wrong.

TheFu, I don't need the 7 machine for anything else, that is why I will install Ubuntu.

I'll let everyone know if I am successful.  Or not.

Thanks.

---

### Post by seeker17 on 2020-03-22
All right......I think I am going to need the "Instructions for Idiots" (that is, me) version.  

This time I tried the USB thumb drive method.

Here is what I did:
1.  I downloaded a new copy of ubuntu-18.04.4-desktop-amd64
2.  I clicked "send to" on the file and sent it to my thumb drive.
3.  I took the thumb drive to the target computer, the Windows 7, put it in the USB port, hit the power button and pressed F12.
4.  I got a window asking me where I wanted to boot from and I chose the thumb drive.

No success.  The computer booted to Windows 7.

Questions:
1.  Do I have to erase everything else that was on the thumb drive?
2.  Was there something I had to do to ubuntu-18.04.4-desktop-amd64 before I put it on the thumb drive?  I get the feeling there is, but this is the part I don't fully understand.

Hoping you folks don't lose patience with me.  I really want to do this, but I am stuck at step zero.

Thanks again.

---

### Post by CatKiller on 2020-03-22
> **seeker17 said:**
> 2.  I clicked "send to" on the file and sent it to my thumb drive.

No, you absolutely do not want to have that file on the drive. You use that file to say what *should* be on the drive. Think of the .iso file as a .zip file if you like. It's an image of the contents of a filesystem.

>  Do I have to erase everything else that was on the thumb drive?

The act of writing the contents of the image to a drive will wipe everything that was on there before.

---

### Post by ipv on 2020-03-22
> **seeker17 said:**
> I think I am going to need the "Instructions for Idiots" (that is, me) version.

dvd : [https://www.youtube.com/watch?v=gCb6_Up0GCw](https://www.youtube.com/watch?v=gCb6_Up0GCw)

usb : [https://www.youtube.com/watch?v=gCb6_Up0GCw](https://www.youtube.com/watch?v=gCb6_Up0GCw)

---

### Post by yancek on 2020-03-22
If you are using Nero, the link below (very dated) explains its use.  You need to select an option to burn the iso file of Ubuntu as an image and not burn/copy it as data.  If you choose that option (burn data) it will not be bootable.

[http://www.ntfs.com/bootdisk_quest_burn_nero.htm](http://www.ntfs.com/bootdisk_quest_burn_nero.htm)

---

### Post by Impavidus on 2020-03-23
> **seeker17 said:**
> Yes, Impavidus, I could use the installer to wipe Windows 7 and install Ubuntu, but I like to do things in small steps.Just wiping Windows 7 and installing Ubuntu is easier than installing Ubuntu as dual boot. The small steps you want to take are larger than the steps I suggested. Note that this is only true because you already have a new computer with Windows 10. Dumping Windows altogether when first installing a Linux distribution is generally a bad idea.

> **seeker17 said:**
> 
2.  I clicked "send to" on the file and sent it to my thumb drive.As told to you by others, that won't work. To give you a slightly simplified version of the technical details: to be able to boot from a usb drive or a dvd, you need a specific piece of software, called a bootloader, in a specific place on the usb drive/dvd. This bootloader is present in the .iso file, but if you simply copy the .iso file somewhere into the filesystem of the usb drive, it won't end up in the right place. So you have to "burn" it to the usb or burn it "as an image" to the dvd. This replaces the entire filesystem of the usb drive with the filesystem present in the .iso file, which will put the bootloader in the right spot, making the usb bootable. Same on a dvd: instead of creating a new filesystem containing an .iso file, you have to use the .iso file itself as the filesystem of the dvd.
> 
1.  Do I have to erase everything else that was on the thumb drive?By replacing the filesystem on the usb drive, everything that was there will be erased automatically.

---

### Post by seeker17 on 2020-03-29
I am very excited.

I followed the Nero instructions that yancek was kind enough to provide.  I was able to correctly burn an iso (no, I don't fully understand what an iso is, but the job is done!).

I rebooted, pressed F12 and the DVD installed Ubuntu on its own partition.  The program updated and here I am.

I will look around this new (to me) OS, next time I a have a free moment.

I am sure I will have plenty to ask.

Perhaps I can now change the title of this thread to "Step One"!

Thank you everyone.  And thank you Impavidus for that explanation about iso files.  I think I am beginning to understand.

I'll be back.

---

### Post by CatKiller on 2020-03-29
Glad to hear you're up and running now.

> **seeker17 said:**
> (no, I don't fully understand what an iso is, but the job is done!).

[https://en.wikipedia.org/wiki/ISO_image](https://en.wikipedia.org/wiki/ISO_image)

---

### Post by him610 on 2020-03-29
> How does one get a computer with only Ubuntu on it? Does one have to buy it like that?

Yes, you can buy a computer with Ubuntu installed - [https://system76.com/]("https://system76.com/")
You can buy one without any operating system installed - search for 'refurbished without OS'.
You can replace your current HDD/SSD with a new one without OS - they are pretty cheap now.
You can build one from parts - [pcpartpicker.com]("pcpartpicker.com")

Have fun.

---

### Post by seeker17 on 2020-04-05
Back with some questions.  Excited to have this working.  I can really only get on non-work-related projects one day a week so here I am for this week.

I have installed one or two things from the Ubuntu Software - icon on left side of screen.

I am playing around with Office Libre; I can see there's a lot to learn here.

Some basic Step One questions:
1.  does an antivirus install with Ubuntu or do I have to download one?
2.  is the name of my wireless network visible - a security/privacy question
3.  does an equivalent of Windows Notepad install with Ubuntu?   I am looking for something very simple that I can open quickly with a right-click on the desktop.

Thanking everyone again.

Seeker17

---

### Post by Impavidus on 2020-04-05
1: There's no antivirus coming with Ubuntu and you don't really have to install one. Viruses aren't really a problem on Linux. That doesn't mean you shouldn't worry about malware at all on Ubuntu, but virus scanners are mostly used on email servers.

2: I assume that would depend on the settings of your wireless router. Some people hide their network. I read that it's less of a security and privacy benefit than you'd expect on first sight.

3: There are many text editors around and some of them will be installed by default: gedit, emacs, nano, mousepad, vim, kate, pluma, nedit, ne, e3, dav, gprompter, yudit, joe, jove, levee, vile, vis, ed. Search the package manager. I think most use gedit. I always use vim.

---

### Post by TheFu on 2020-04-06
Seems you might be making the mistakes that people coming fro other OSes commonly make when they get to Linux/Ubuntu.  That mistake is thinking that what they've learned or been taught is relevant anymore.  Linux/Ubuntu is a completely different OS. It isn't like OSX or Windows.  Programs for it aren't created with the same overall philosophy as they are for those other systems, so many assumptions you bring with you aren't good to have. They are a hindrance.

For a quick overview about major differences, read this: [https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html)  Sure, it is from 2014, but it is still relevant.

Onto the questions:
1) Best to read the "Sticky Threads" at the top of the Ubuntu Forums Security sub-forum. [https://ubuntuforums.org/forumdisplay.php?f=338](https://ubuntuforums.org/forumdisplay.php?f=338)  Usually, we don't run AV software on our desktops. The architecture of Linux means there isn't much need for it, since normal users can't really harm the system. Gaining access to the admin user(s) takes a specific request that isn't accidental.  

2) Wireless network connections (wifi, bluetooth, cellular data) are all non-secure.  Nothing you or I can do about that. Whether that is a risk sufficient for you to modify behavior is a different question.  If you live 10 miles into the woods with no neighbors for 20 miles, perhaps worrying about wifi isn't all that important.  OTOH, if you live in a densely packed dorm or apartment complex, perhaps using a VPN with your wifi, always, would be smart?  The answer about bluetooth stuff is really easy.  Don't use bluetooth if you don't want to be hacked.  I'm 100% serious.  Hacking bluetooth isn't even a challenge.  As for wireless data from your cellular phone company, those guys have a trade-off to make and they routinely trade security for battery life every time.

3) Editors.  In any Unix-like OS, which included Ubuntu systems, having a text editor is much more important than for Windows.  I use a text editor probably 40+ times every day.  Initially, most people start with nano or whatever the built-in editor (in their menus) might be. Over time, as they want more power, they will seek out editors more like notepad++.  Then finally, they'll outgrow those and learn vim.  I've been a programmer, systems admin for almost 30 yrs and I started out using the simple editors of the time just like everyone else whenever I could.  vim didn't exist back then. We had vi and it was installed on every system, including routers.  I've never seen any other editor installed on routers. vi and vim are closely related and the basics are the same. Someone unfamiliar with vi/vim will eventually need to learn it just a little, if only enough to learn how to exit the program.

Editor choice is a holy war for Unix people.  Use whatever you like.  Expect someone to suggest a different editor. Some people might harass you based on the editor - sorta like how Ford people hassle Chevy drivers. Any program we use a bunch becomes important to us and that shows in stupid arguments.  Use whatever editor you like.

There are many Beginner steps for Ubuntu websites out there.  Just depends on why you use Ubuntu what you might want/need to learn first.  A casual user, surfing, music, videos, a few native games would learn stuff completely different from what someone who wants to be a Linux Admin, get a job, would need to learn.  Same for someone trying to learn to program for servers - completely different skills than those other two types of people are needed.

---

### Post by seeker17 on 2020-04-12
Thank you impavidus and TheFu.  I will go to the two areas mentioned in your post, TheFu.
I will accept that I do not need an AV while I read why.
Regarding the wifi security, it seems just another reason for me to get a VPN, which I plan to do soon.  Of course "soon" for me is a relative statement.
Text editors:  where is the "package manager" you refer to, impavidus.  That's me speaking from ignorance again.

---

### Post by TheFu on 2020-04-12
[https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html) is the first link to be read. Please. it explains package managers among other very basic things.

While you can use a paid VPN, that won't help secure your local wifi access.  You need to run your own VPN server on the LAN for that and only use wired connections whenever possible.

---


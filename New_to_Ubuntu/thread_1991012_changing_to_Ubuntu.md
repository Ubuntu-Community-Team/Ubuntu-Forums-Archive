---
title: "changing to Ubuntu"
date: 2012-05-30
forum: New to Ubuntu
---

### Post by kosachilles on 2012-05-30
As the title says, i am in the process of wanting to change to Ubuntu from Windows 7 but have some questions before i do. I would really appreciate any and all help that you all can provide me with! I apologize if these questions have been asked before.

I will list the questions that i have than provide a list of software i would like to know if they will work in Ubuntu as well as provide all (hopefully) the info you guys may need to answer my questions. Again thank you for your time and help as i really appreciate it!

List of questions.

1. What anti virus do you all recommend?
2. What firewall do you all recommend?
3. Does firefox and adblock plus work the same (and as well) as in windows 7?
4. Where do i download drivers from for my sound and video?
5. Do i need software for modem (DSL) driver?
5. Will software i use in Windows 7 work in Ubuntu? If not, are their alternatives to them? 

List of software's i would like to keep using. 
1. Truecrypt
2. Ccleaner
3. Auslogics Disk Defrag 

Here are my sound and video cards. Do not know the one for modem (DSL)

Sound: 
Intel (R) High Definition Audio HDMI
            Realtek High Definition Audio

Video:
Intel (R) G45/G43 Express Chipset

Here is my system setup:

Pentium (R) Dual Core CPU E5400 2.70 GHz
4.00 GB Ram
64 Bit OS

Thank you for any and all help you guys and gals can give me. Really do appreciate you taking your time to help out a newbie. Will check back later to see if their are any questions or if their is any info you might need to help me better. Thanks!

---

### Post by zombifier25 on 2012-05-30
1. No, generally you don't need antivirus in Ubuntu. But if you want to, try ClamAV.
2. Ubuntu has a firewall by default, ufw. Type this command to enable it
```
sudo ufw enable
```
to configure it, you can use the command line or install gufw for the GUI.
3. Firefox addons only depends on Firefox, so yes, it will work the same way.
4., 5. If Ubuntu does not support a piece of hardware by default, it would download the driver for you via "Additional Drivers".
6. Linux is NOT Windows. Period. For almost all Windows software there are always Linux alternatives. If you want to run some Windows software on Ubuntu, install Wine, via the Software Center.

And for your softwares,
1. Truecrypt: There's a Linux version.
2. Ccleaner: You can install a system cleaner in Ubuntu, BleachBit. It works pretty good.
3. Auslogics Disk Defrag : Ubuntu's ext4 file system does not need to be defragged.

---

### Post by nothingspecial on 2012-05-30
Questions

1. You don't need it.

2. Ubuntu comes with an inbuilt firewall iptables, by default all ports are blocked so you don't really need it unless you are going to be opening up your system. See here [https://help.ubuntu.com/10.04/keeping-safe/C/firewall.html](https://help.ubuntu.com/10.04/keeping-safe/C/firewall.html)

3. Yes afaik

4. Ubuntu comes with the drivers included in most cases.

5. No, windows software will not work. There are alternatives for most things.

Software

1. I believe there is a linux version of truecrypt
2 and 3 Ubuntu doesn't need cleaning up or defragging like windows does. There are some programs like bleachbit or ubuntu tweak that perform similar actions.

The important thing is that Ubuntu is not windows and does not behave the same way or need maintaining in the same way.

---

### Post by xedi on 2012-05-30
Edit: My typing was too slow, most things are already answered -.-

> 1. What anti virus do you all recommend?

None, as an average user you should be fine without one on Ubuntu. I haven't used it for ages, but ClamAV seemed ok two years ago or so, in case you want to scan for Windows viruses.

> 3. Does firefox and adblock plus work the same (and as well) as in windows 7?

I use Adblock Plus on Chrome, so I don't know specifically about Firefox but I don't see a reason why it shouldn't and yes Firefox has the same functionality and works just as well on Windows and Ubuntu. On Ubuntu you also have the advantage of using the HUD: you can press alt and then search for some menu entry in case you forgot where it is or want to access it faster. This Ubuntu feature works also with many other programs.

> 4. Where do i download drivers from for my sound and video?

Intel video drivers should be already included in the default Ubuntu installation and I'm not sure but my guess is also the sound card drivers, too. If not, Ubuntu will try to get drivers from the internet and in case where you have the choice between open source drivers and proprietary, it will ask which one you want to use. There is hardware which will not work out of the box (or not at all) but chances are that your sound and video should be fine.

> 5. Do i need software for modem (DSL) driver?

Not that I would know of. I think I would start worrying about drivers if something does not work.

> 5. Will software i use in Windows 7 work in Ubuntu? If not, are their alternatives to them? 

Short Answers: No, Yes

Long Answer: You can get many Windows programs to work with Wine, but many will not work and many will work only to some degree, especially complex programs like some video games might not work at all with Wine so it depends what Windows program you will want to run.

Fortunately, there are plenty of alternatives. I have used Ubuntu almost exclusively for three years now and that would not be possible if there were no alternatives to Windows only programs.

---

### Post by 2F4U on 2012-05-30
If Wine is an option for you and if you would like to check whether your applications are supported, check the Wine applications list:

[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by westie457 on 2012-05-30
> **kosachilles said:**
> As the title says, i am in the process of wanting to change to Ubuntu from Windows 7 but have some questions before i do. I would really appreciate any and all help that you all can provide me with! I apologize if these questions have been asked before.

I will list the questions that i have than provide a list of software i would like to know if they will work in Ubuntu as well as provide all (hopefully) the info you guys may need to answer my questions. Again thank you for your time and help as i really appreciate it!

List of questions.

1. What anti virus do you all recommend?
2. What firewall do you all recommend?
3. Does firefox and adblock plus work the same (and as well) as in windows 7?
4. Where do i download drivers from for my sound and video?
5. Do i need software for modem (DSL) driver?
5. Will software i use in Windows 7 work in Ubuntu? If not, are their alternatives to them? 

List of software's i would like to keep using. 
1. Truecrypt
2. Ccleaner
3. Auslogics Disk Defrag 

Here are my sound and video cards. Do not know the one for modem (DSL)

Sound: 
Intel (R) High Definition Audio HDMI
            Realtek High Definition Audio

Video:
Intel (R) G45/G43 Express Chipset

Here is my system setup:

Pentium (R) Dual Core CPU E5400 2.70 GHz
4.00 GB Ram
64 Bit OS

Thank you for any and all help you guys and gals can give me. Really do appreciate you taking your time to help out a newbie. Will check back later to see if their are any questions or if their is any info you might need to help me better. Thanks!

Welcome to the Fora.

In answer to your questions.

1 Anti-virus software is not needed for the OS. Only needed if sharing files with Windows users. There are no known viruses in the wild for Linux.

2 Firewall is built-in, though you do have to enable it. By default Linux OSes in general have no open ports.

3 At least as well. Personal choice I do not use Firefox so cannot say for definite.

4 Drivers are mostly built in to the kernel so usually you do not have to find them. Those that are not supplied are usually a mouse click or two away.

5 Probably not. See above.

6 There is alternatives to most Windows Programs that are at least as good and sometimes better. Windows software will not work in Linux, for that there is Wine - which is a whole topic in itself.


The software you would like to keep using.

1 Truecrypt, have no idea as have never used it.

2 Ccleaner, not needed and does not run in Linux

3 Disk defrag, again not needed. The Ext4 file-system handles files differently to Windows.

Best advice is to download the .ISO and burn a CD. Set your BIOS to boot from the CD and choose 'Try' see what works out of the box. Plug a cable in just in case you need to install other drivers. They will be suggested to you.

Play on the Live Desktop. Most of it will wok immediately, however mp3 files will not play, for that open the Software Centre, search for ubuntu restricted extras and install them. You will have to redo this everytime you use the LiveCD because things are stored in RAM and not written to the Hard drive.

---

### Post by Paddy Landau on 2012-05-30
Regarding Wine: As already stated, most Windows programs will not work on Wine. However, if you do decide to experiment with it, I strongly recommend you use [PlayOnLinux]("http://www.playonlinux.com/") . PlayOnLinux is a front-end to Wine, hiding its complexity.

As a newcomer, you will need to know a few things that are different from Windows — things that bewilder most people new to Ubuntu (including me, once upon a time).

[LIST]
[*]Installing and uninstalling programs in Ubuntu is dead easy! You do **not** search the Internet, find programs, download and install. Instead, you open the Ubuntu Software Centre, and install or uninstall from there. It handles everything for you — keeping track of what's installed, handling dependencies, downloading on your behalf.

For example, you would install PlayOnLinux in that way.

Ubuntu also comes with the Update Manager (which works in tandem with the Ubuntu Software Centre). The Update Manager will **automatically** detect updates to programs, and update them for you (after prompting you for permission). This includes, say, Firefox.

Unfortunately, a few application developers do not use the package manager. TrueCrypt is one of them. When it comes to installing TrueCrypt, you will have to download and install, and you will have to check regularly for updates. Ask if you struggle to install TrueCrypt on Linux, because it's dead easy.
[/LIST]

[LIST]
[*]Linux does not suffer from viruses. (It may do in the future, but for now it just doesn't.) The **only** reason you would need an antivirus would be if you are worried about passing viruses that Windows users emailed to you along to other Windows users. If you are a normal email user and you aren't running an email server, just don't worry about it.
[/LIST]

[LIST]
[*]The Linux firewall, as already stated, is built in. If you are behind a router, you don't need to enable it. If you want to enable it, e.g. you use your laptop in Starbucks, it can be done via the command line (as already stated) or just ask for how to do it with the mouse.

Unlike Windows, you do **not** install a firewall, because it's already built in. Instead, you install a firewall-manager.

If you have installed (say) three firewall managers, they all act on the same built-in firewall. You don't have to keep your firewall manager running; once you've made your changes, the built-in firewall remembers them. You can close your firewall-manager.
[/LIST]

[LIST]
[*]Unlike Windows, Linux does not suffer from an increasing build-up of junk files. There is no need to use the equivalent of CCleaner. Just don't worry about it.

If you have an ancient computer with a tiny disk drive, ask and we'll give you two simple commands to clean up the package manager cache; Bleachbit, although it works, is not really recommended.
[/LIST]

[LIST]
[*]Unlike Windows, the Linux hard drive (which uses ext4 instead of NTFS) does not become increasingly fragmented. There is no need whatsoever to defragment your hard drive. All deframenting will do is reduce the lifespan of your drive. Just don't worry about it.
[/LIST]

[LIST]
[*]Linux was built from the bottom-up for multi-user. Yes, it is possible for more than one user to log into one computer and use it at the same time (e.g. your spouse could be using your computer at home, while you log in over the Internet, and neither of you would be aware of the other apart from some slowdown in speed).

This means that two users never interfere with each other.

It also means that program settings are **not** stored in a Registry as does Windows. Instead, each user has his own, independent, settings in his own home folder. Thus, if your settings for a program are wonky, uninstalling and reinstalling the program will do nothing but waste your time. You need to delete your settings from your home folder, and when you restart the program it will re-initialise the settings. Just ask if this ever is a problem for you, and we'll tell you where to find your settings.
[/LIST]
I hope that helps.

---

### Post by kosachilles on 2012-05-30
Thanks for the fast response and all the help everyone! I have been looking around and it seems Avast makes a Antivirus for linux so hopefully it will work. Says system requirements are: Any Linux distribution (x86 platform only) with GLIBC version 2.1 or higher and pthreads libraries installed. I would assume the newest version has what is needed? Also it's great that Ubuntu has firewall built in and you just need to activate it.

Also went and looked around and it seems that truecrypt makes a linux version as well as someone mentioned above in a post. And someone mentioned a version of Ccleaner for Ubuntu so that is great. So far so good, glad it seems to be so easy to switch. Only concern is if truecrypt Linux version will work on my external hard drive since it is encrypted with the windows version or if i have to save files, download truecrypt linux version and re-encrypt the external hard drive again, than save the files back to external hard drive. Will look into this later after work but even that is no big deal.

It is great that Ubuntu will probably have all software for my drivers already and won't require me to install anymore software like windows. It is also great (if what i read is correct) that Ubuntu uses less space/CPU yet is faster than windows. 

Again thanks for the fast replies and all the help. I really do appreciate all of you helping out a newbie.

---

### Post by Paddy Landau on 2012-05-30
> **kosachilles said:**
> ... it seems Avast makes a Antivirus for linux
It detects Windows viruses, not Linux viruses (because Linux viruses don't exist). Some Linux users have reported excessive false positives with this software. Again, if you aren't forwarding suspicious emails to Windows users, just don't waste your time over it.

> **kosachilles said:**
> And someone mentioned a version of Ccleaner for Ubuntu so that is great.
It's not a Linux version of CCleaner. Again, don't worry about it; you're wasting your time.

> **kosachilles said:**
> Only concern is if truecrypt Linux version will work on my external hard drive since it is encrypted with the windows version...
It should work without any problem.

> **kosachilles said:**
> ... Ubuntu uses less space/CPU yet is faster than windows.That's why it is faster! If you have an old computer with low specifications, you may find Ubuntu a little too slow. In that case, try using [Lubuntu]("http://lubuntu.net/") instead. It's an official Ubuntu derivative for low-spec computers.

---

### Post by mastablasta on 2012-05-30
see the link in my signature regarding antivirus use. i do not suggest clamav. it seems it has poor detection rate. would be much better to use avira free antivirus for linux or some other option. but as said before they are only needed if you share files with people that have windows mashcines (which is likely) and you don't want to send them infected files.
 
regarding Truecrypt - there is a linux version. however ubuntu during install will ask you if you want to encrypt /home. the default encryption (forgot it's name) is as good as truecrypt. it is also suggested to encrypt the swap parition. ofcourse if you prefer truecrypt you can install that one.
 
---
 
what i believe no one mentioned is that you can boot into live OS (select try it after boto menu comes up) where the whole OS is loaded into ram and doesn't make any changes to your system. you can do all you want in it, check out how you stuff works, if any additional drivers are needed etc. if it all works only then do the real install. if you would like to keep some settings of live os on reboot you need to use LiveUSB and create persistance file (live USB is easilly created with programmes *unetbootin* or *linuxliveUSB*)

---

### Post by kosachilles on 2012-05-30
> **Paddy Landau said:**
> It detects Windows viruses, not Linux viruses (because Linux viruses don't exist). Some Linux users have reported excessive false positives with this software. Again, if you aren't forwarding suspicious emails to Windows users, just don't waste your time over it.

I must be really reading what Avast is for cause it seems their is new version that does scan linux files. Take a look at this link and tell me what you think please. [http://www.avast.com/linux-home-edition](http://www.avast.com/linux-home-edition)


It's not a Linux version of CCleaner. Again, don't worry about it; you're wasting your time.

Okay thanks!


It should work without any problem. 

Will give it a try to make sure but thank you!

That's why it is faster! If you have an old computer with low specifications, you may find Ubuntu a little too slow. In that case, try using [Lubuntu]("http://lubuntu.net/") instead. It's an official Ubuntu derivative for low-spec computers.

Well my computer isn't even a year old and the specs are good. I have no trouble running windows 7 but if Lubuntu is faster that even better. Thank you!

---

### Post by mastablasta on 2012-05-30
> **Paddy Landau said:**
>  
That's why it is faster! If you have an old computer with low specifications, you may find Ubuntu a little too slow. In that case, try using [Lubuntu]("http://lubuntu.net/") instead. It's an official Ubuntu derivative for low-spec computers.
 
correct. in linux you can install a desktop environment (DE) of choice (windows has usually only one environment available).
 
LUbuntu and Xubutnu for light system resoruce usage (we are talking modern OS with modern programmes running nicely on less than 256 MB ram)...
then you have Ubuntu and Kubuntu - they take a bit more, btu again it depends what you enable/install. for exmapel with effetcs off and low resource package you can reduce ram consumption below 250MB ram. think how many RAM and CPU is then left for programmes!!!
 
There are other DE and widnows managers. soem go even lower with resoruce usage. you can get a modern OS with new programmes on 64Mb mashcines... it really is an amazing aspect of this OS.
 
but like i said before it pays off to boto it and try it first just to see if it all works well..

---

### Post by kosachilles on 2012-05-30
> **mastablasta said:**
> correct. in linux you can install a desktop environment (DE) of choice (windows has usually only one environment available).
 
LUbuntu and Xubutnu for light system resoruce usage (we are talking modern OS with modern programmes running nicely on less than 256 MB ram)...
then you have Ubuntu and Kubuntu - they take a bit more, btu again it depends what you enable/install. for exmapel with effetcs off and low resource package you can reduce ram consumption below 250MB ram. think how many RAM and CPU is then left for programmes!!!
 
There are other DE and widnows managers. soem go even lower with resoruce usage. you can get a modern OS with new programmes on 64Mb mashcines... it really is an amazing aspect of this OS.
 
but like i said before it pays off to boto it and try it first just to see if it all works well..
I have a dual core 2.70 GHz and 4.00 GB or Ram so i don't think it would be a problem running Ubuntu but like i said, if their is a lighter OS than even better.

---

### Post by Paqman on 2012-05-30
> **kosachilles said:**
> I have a dual core 2.70 GHz and 4.00 GB or Ram so i don't think it would be a problem running Ubuntu but like i said, if their is a lighter OS than even better.

I'd advise trying them out before installing. The lighter desktops are quicker, but they do lack some of the nice features of full-fat desktops.

You can download a LiveCD of each of the various versions and boot up into it. That'll allow you to try out the various desktops without committing to a full install. The choice of desktop you go for is really just personal taste, especially on hardware like yours that can run them all nice and smoothly.

---

### Post by rasmus91 on 2012-05-30
again, on the antivirus thing, don't bother. it won't be a problem for you.

also, dont bother with defrag.

---

### Post by Paddy Landau on 2012-05-30
> **kosachilles said:**
> Well my computer isn't even a year old and the specs are good. I have no trouble running windows 7 but if Lubuntu is faster that even better. Thank you!
In that case go for the full Ubuntu. If your computer runs Windows 7 without problem, Ubuntu will run very well. It uses the new Unity interface, which in my personal opinion is the best yet developed. I would choose the 64-bit download if you have at least 2Gb RAM, because it runs faster.

---

### Post by samitharansara on 2012-05-30
> **2F4U said:**
> If Wine is an option for you and if you would like to check whether your applications are supported, check the Wine applications list:

[http://appdb.winehq.org/](http://appdb.winehq.org/)

Check the WineHQ rating.  If it is platinum or gold, means you can rely on it.  Otherwise, just forget and look for alternatives..:KS

---

### Post by Shadius on 2012-05-30
> **mastablasta said:**
> see the link in my signature regarding antivirus use. i do not suggest clamav. it seems it has poor detection rate. would be much better to use avira free antivirus for linux or some other option. but as said before they are only needed if you share files with people that have windows mashcines (which is likely) and you don't want to send them infected files.
 
regarding Truecrypt - there is a linux version. however ubuntu during install will ask you if you want to encrypt /home. the default encryption (forgot it's name) is as good as truecrypt. it is also suggested to encrypt the swap parition. ofcourse if you prefer truecrypt you can install that one.
 
---
 
what i believe no one mentioned is that you can boot into live OS (select try it after boto menu comes up) where the whole OS is loaded into ram and doesn't make any changes to your system. you can do all you want in it, check out how you stuff works, if any additional drivers are needed etc. if it all works only then do the real install. if you would like to keep some settings of live os on reboot you need to use LiveUSB and create persistance file (live USB is easilly created with programmes *unetbootin* or *linuxliveUSB*)

I second this. Create the Ubuntu LiveCD or LiveUSB and test it out on your computer first before doing the real installation. You'll be able to get a feel for Ubuntu and see how it performs on your system.

---

### Post by Paqman on 2012-05-30
> **rasmus91 said:**
> 
also, dont bother with defrag.

I'd just like to point out that EXT4 can get fragmented if it's run at very close to capacity. As long as that never happens you can safely ignore the effect of fragmentation.

There is no actual defrag tool for EXT filesystems anyway. The only way to defrag one would be to image it then write it back to the disk.

---

### Post by oldos2er on 2012-05-30
> **kosachilles said:**
> Thanks for the fast response and all the help everyone! I have been looking around and it seems Avast makes a Antivirus for linux so hopefully it will work. 

As someone else said, it only detects Windows viruses, which won't work on Linux anyway. If you plan on sharing files with Windows' systems, it might be useful for that.

There are other kinds of malware that may be of more concern for a Linux user; I recommend you read the stickies at the top of the Security Discussions forum, [http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

---

### Post by TheGuyWithTheFace on 2012-06-01
It seems a lot of people are talking about using Wine. Don't get me wrong, I love wine too, but if you find one of your favorite programs doesn't work well with wine, you could dual-boot Ubuntu with windows. I use Ubuntu 99% of the time, but if you find a program you occasionally need that doesn't work with wine, you can simply boot into windows. Bear in mind, though, when you use Ubuntu consistently and suddenly have to use windows again, windows looks pretty bad...

---

### Post by Shadius on 2012-06-01
> **TheGuyWithTheFace said:**
> windows looks pretty bad...

You got that right! I haven't touched my Windows since I installed Ubuntu.

---

### Post by critin on 2012-06-01
> 1. What anti virus do you all recommend?

Ubuntu.  lol

You know when you install Windows, the first thing you have to do is hurry and install an anti-virus.  That's why the distro comes with Norton/Macafee ready to install.

When you install ubuntu, the first thing I do is change the desktop wallpaper.

---

### Post by Shadius on 2012-06-01
> **critin said:**
> Ubuntu.  lol

You know when you install Windows, the first thing you have to do is hurry and install an anti-virus.  That's why the distro comes with Norton/Macafee ready to install.

When you install ubuntu, the first thing I do is change the desktop wallpaper.

:lolflag: And say Ooo-buntu!

---

### Post by finny388 on 2012-06-23
moving to linux is such a change of mindset
reading the orig post was a good reminder of life in Windows.

anyway, my 2 cents: in the terminal run the clean command to clean up unneeded temp/install files.

```
sudo apt-get clean
```

I save a few 100 mb of space every few weeks this way.
welcome!

---


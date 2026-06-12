---
title: "ubuntu working with windows"
date: 2012-03-15
forum: New to Ubuntu
---

### Post by longshanks62 on 2012-03-15
Hi,
I have become interested in ubuntu since reading various comments on different forums and I am now ready to try it out. My existing system is Windows based where I run a duel boot win 7 and XP, from the primary HDD, I have two installed additional HDD's one of which I am thinking of installing Ubuntu on, Will there be any problems with this? some advice please on how obtain and install Ubuntu
regards

---

### Post by wadie on 2012-03-15
Download ubuntu from here:
[http://www.ubuntu.com/desktop](http://www.ubuntu.com/desktop)

There shouldn't be a problem in installing Ubuntu on one of your HDDs. I've tried it.

---

### Post by krishnan t s k on 2012-03-15
Try ubuntu out first before you go and install it... you can also install ubuntu inside windows through wubi which i would suggest.... Also make sure that all your hardwares, webcams and printers work before you install ubuntu... Else you will be spending many hours either searching for solutions to your problems or screwing ubuntu for something that didnt work
You could also wait for a little over a month(i would suggest 2 to be safe) as the LTS(Long Term Support) version is going to be released on 26th of April.... In case you encounter any problems, you can search for or post in the forums :):)
Have a nice day :)

---

### Post by Mark Phelps on 2012-03-15
I've found, through experience, that the best way have multiple OSs when you have multiple drives, is to have them installed in separate drives.  This minimizes the risk of doing accidental damage to existing OSs.

I would recommend the following:
1) Disconnect the Windows drive
2) Boot from the Ubuntu desktop CD
3) Install Ubuntu to the drive, including GRUB
4) Reattach the Windows drive -- but continue to boot from the Ubuntu drive
5) Open a terminal in Ubuntu and enter "sudo update-grub"

That will regenerate the default GRUB config file and when you reboot, you should get a GRUB menu with entries for Ubuntu and Windows.

---

### Post by longshanks62 on 2012-03-16
Mark, thanks,I am quite new to this so please excuse my ignorance .In your reply above, 5 open a terminal and enter"sudo update-grub" can you elaborate please
regards

---

### Post by mraandtux on 2012-03-16
Install Ubuntu with Wubi is recommended.

---

### Post by Rodney9 on 2012-03-16
Download Ubuntu, burn it to a disk as an image, then boot from the cd.

It will load a from the cd into ram and will not touch your hard drives, this is the best way to see if you like it and can use it with all your hardware.

Rodney

---

### Post by ixtok on 2012-03-16
> **mraandtux said:**
> Install Ubuntu with Wubi is recommended.

Wubi is the closest thing Ubuntu has to a virus. If the OP has spare available hard drives, instalation on one is the logical way to go.

---

### Post by FulciLives on 2012-03-16
Go into your BIOS at boot up time and change the boot order of your drives so that the first HDD to boot to is the empty drive you will be installing ubuntu on.

Make sure your CD drive is frist then this empty HDD.

Then boot with a Ubuntu "live" CD and do an install to the empty HDD.

Now when you boot to that drive you get a menu that let's you select Ubuntu (by default) or your Windows install (on the other HDD).

---

### Post by NikTh on 2012-03-16
Hi , 
Just install Ubuntu anywhere you like. There will be no problem. To separate HDD or alongside windows.  
Wubi is recommended Only for testing. It is virtual installation that allows you to see how is Ubuntu from inside of windows. It is slower and maybe problems occur at future. I don't suggest wubi, never. 
I suggest to install Ubuntu properly(regular install) . Here ,take a look at this Video tutorial on how to install ubuntu --> [http://www.youtube.com/watch?v=fiVZhnTCZOs&feature=related](http://www.youtube.com/watch?v=fiVZhnTCZOs&feature=related) 
or see here --> [http://www.youtube.com/watch?v=dMTL_-XJjyU](http://www.youtube.com/watch?v=dMTL_-XJjyU) on how to install ubuntu alongside windows. (dual boot)

---

### Post by Mark Phelps on 2012-03-16
> **longshanks62 said:**
> Mark, thanks,I am quite new to this so please excuse my ignorance .In your reply above, 5 open a terminal and enter"sudo update-grub" can you elaborate please
regards

First of all, FORGET about Wubi.  You have a separate drive for Ubuntu.  THAT is the way to go.

To get a terminal, click on the "dash" button on the upper-left part of the desktop, enter "terminal" and select the result.  That will open a terminal on your desktop.

Then enter the sudo command as written.

---

### Post by flemur13013 on 2012-03-16
> **Mark Phelps said:**
> I've found, through experience, that the best way have multiple OSs when you have multiple drives, is to have them installed in separate drives.  This minimizes the risk of doing accidental damage to existing OSs.

I would recommend the following:
1) Disconnect the Windows drive
2) Boot from the Ubuntu desktop CD
3) Install Ubuntu to the drive, including GRUB
4) Reattach the Windows drive -- but continue to boot from the Ubuntu drive
5) Open a terminal in Ubuntu and enter "sudo update-grub"

That will regenerate the default GRUB config file and when you reboot, you should get a GRUB menu with entries for Ubuntu and Windows.

That's my method too, except I select the boot disk with BIOS - NO "update-grub" - and grub doesn't (have to) know that windows exists.
1 - Connect one physical disk, disconnect all others.
2 - Install OS1 on it.
3 - Connect a different disk, disconnect all others.
4 - Install OS2.
5 - Connect both disks, boot and select OS1 or OS2 disk from BIOS.

The OSs can normally see each other's disks, they just don't know - or care - that there's another OS on the other disk.

---

### Post by QIII on 2012-03-16
Easier to make a selection in GRUB menu than to open BIOS at every boot.

I want to reitetate MarkPhelps' recommendation.  It may not seem necessary to you, but disconnecting the other drives preserves the master boot record (MBR) on any OSes installed on those drives AND assures that you don't accidentally install Ubuntu on the wrong drive by accident and destroy what is there.

---

### Post by Holdolin on 2012-03-16
Either Mark or flemur's suggestion should work for ya.  Personally, i like choosing the boot drive from the BIOS, but some may wish not to have to enter it just to choose thier OS.  Pick your poison :)

Also, welcome to the goodness that is Ubuntu.

---

### Post by mamalmeyti on 2012-03-16
hey,
I`ve read all posts and I have a question
I have one drive and a vista/ubuntu dual boot. is that bad that i don't have two separate drives and/or a swap drive?! and if i ever want to install windows 7 or 8 (a new install) u experts recommend i make 3 or 2 drives or this config is fine, I want to do it the right way, thanks in advance.

---

### Post by NikTh on 2012-03-16
> **qiii said:**
> easier to make a selection in grub menu than to open bios at every boot.


+1

---

### Post by longshanks62 on 2012-03-17
> **longshanks62 said:**
> Hi,
I have become interested in ubuntu since reading various comments on different forums and I am now ready to try it out. My existing system is Windows based where I run a duel boot win 7 and XP, from the primary HDD, I have two installed additional HDD's one of which I am thinking of installing Ubuntu on, Will there be any problems with this? some advice please on how obtain and install Ubuntu
regards

many thanks to you all this is the type of info which helps a lot for a newby trying to learn a new O/S.

---

### Post by longshanks62 on 2012-03-17
> **longshanks62 said:**
> Hi,
I have become interested in ubuntu since reading various comments on different forums and I am now ready to try it out. My existing system is Windows based where I run a duel boot win 7 and XP, from the primary HDD, I have two installed additional HDD's one of which I am thinking of installing Ubuntu on, Will there be any problems with this? some advice please on how obtain and install Ubuntu
regards

I have now got the Ubuntu 11.10 burnt onto cd and I have booted from that as suggested to try it out and I decided that I want to install it onto one of my spare HD's which I have cleared and formated. choosing the install option the wizard takes me through the install process but does not give me the option to install to my preferred HD. I am doing something wrong here methinks.

---

### Post by longshanks62 on 2012-03-18
> **longshanks62 said:**
> Hi,
I have become interested in ubuntu since reading various comments on different forums and I am now ready to try it out. My existing system is Windows based where I run a duel boot win 7 and XP, from the primary HDD, I have two installed additional HDD's one of which I am thinking of installing Ubuntu on, Will there be any problems with this? some advice please on how obtain and install Ubuntu
regards

I have now installed Ubuntu on my second drive and it works ok but it does not show up on my computer when in windows. Were do I find Grub and how do I install it? also

---

### Post by verymadpip on 2012-03-18
Hi longshanks62.

If you are getting the option to choose which OS to boot at startup then GRUB is installed & working, as far as I can tell.

I think I'm correct in saying that Windows can't see the native file system of Ubuntu (ext4 these days in a fresh install I think).

If you check in Windows disk management it will tell you there's a disk, how many & what size the partitions are (if any) but that's about it.

I seem to recall hearing about a 3rd party application that may help.  That's all I remember, sorry.

---

### Post by longshanks62 on 2012-03-18
Thank you my friend,This has got worse After installing Ubuntu onto a spare HD successfully and then re-booting as requested this HDD has disappeared, meaning it does not show in my computer when in my main O/S which is win 7 also it is not shown in the bios!!!.some advise please
regards

---

### Post by verymadpip on 2012-03-19
H'mmm.
I know this will seem silly, but is your Ubuntu HDD connected properly?  I've had that happen to me in the past.
Also, is your Ubuntu HDD SATA or PATA/IDE?  Those ribbon cables can be a pain.

What I'm suggesting first is: try disconnecting & reconnecting the Ubuntu drive, check the BIOS to see if it's there.
If it is shown in the BIOS set it to be the first HDD to boot so we can get into Ubuntu.

Let's see how we get on with that for now.

To clarify: In W7 your Ubuntu HDD ***won't*** be show in 'Computer'. Windows is unable to see it.  However, if you right click 'Computer', then click 'Manage' & then select 'Disk Management' it may show up there.  Unfortunately this will really only tell us that it's installed & give us very basic information about it, nothing more.

---

### Post by tbhatia4 on 2012-03-19
> **mraandtux said:**
> Install Ubuntu with Wubi is recommended.

i won't recommend this as the result of windows corruption you would loose ubuntu too

---

### Post by Mark Phelps on 2012-03-19
If the drive is connected via SATA port, it should show up in the BIOS regardless of any settings.  

If it's connected via IDE ports, check the jumpers on the drive.  If you added/removed a jumper to install to it, and you only had that one drive connected via IDE ports, you will have to change the jumpers for the BIOS to see it if now you have multiple IDE drives connected.

Also +1 to NOT installing via Wubi.  Not that it's necessarily a bad thing -- it's not. It's just that it's not a good long term solution.

---

### Post by verymadpip on 2012-03-19
Yeah, jumpers.  I've managed to "hide" drives from myself by setting them incorrectly.

Good call Mark.

---

### Post by longshanks62 on 2012-03-19
Thanks one and all for your advice, my system has a 500Gb sata drive partitioned and containing win 7 and XP one on each I also have installed, two 80 Gb IDE drives one of which I have formatted and then installed ubuntu on, to do this I first removed the sata HD cable first as not to corrupt the MBR I also disconnected the other IDE HD untill the installation was complete,I then removed Ubuntu live cd and rebooted as directed, I then re connected both sata and 2nd IDE HD,s  I then rebooted again to reinstate boot sequence, that's  when I noticed that only the IDE drive containing Ubuntu was missing, the cable on that drive was not touched but I take your point and I have checked all connection's

---

### Post by verymadpip on 2012-03-20
Sorry for the delay replying.

For the next step I would go with Mark Phelps' suggestion of checking the jumpers on the IDE drives.

If you're using 2 IDE drives on one cable set one to 'master' & the other to 'slave'.  There should be a helpful diagram on the HDD.  At least that's how I'd do it as I've had issues with the cable select option in the past.

I'm aware that you probably already know this stuff, but sometimes it's the simple little things that catch us out...well, they catch me anyway :)

Let's see how that goes for now.

---

### Post by longshanks62 on 2012-03-21
Thanks verymadpip.I appreciate your's and everyone else's advise. I have checked all jumpers, leads, connections, I have even changed arround the ide cable connecting both my IDE drives, I have changed cable select to master, I can't think of anything more to do, I have followed all the above advise.
  I have downloaded the live cd tried it then loaded it and so far this has proven  to be a bit of a disaster I still have my main O/S win 7 working fine but I now cannot see my ubuntu loaded drive in the bios or my computer it has disappeared after all my fault finding, nothing.
 I really would like an answer.

---

### Post by Mark Phelps on 2012-03-21
Sorry ... but unless the Ubuntu drive has actually failed, it HAS to be the jumpers. (Actually, it could also be the cables, but I presume you already checked that and am using the same cables you did when you installed Ubuntu on the drive).

Back when I used to mess around with IDE drives, I remember looking at a jumper diagram on a drive, where it said to put a jumper on the second set of pins from the left for MASTER.  Easy, right?

Well ... it was not that easy.  Why?  Because when you held the drive to look at the diagram, the "left" edge was on one side of the drive; when you held the drive to see the pins, the "left" edge was on the other side of the drive.  I had to experiment to figure out which "left" edge they meant when counting the pins.

---

### Post by HiImTye on 2012-03-21
I don't think jumpers are an issue in any modern computer, as most new drives use only SATA (well, PATA too but most people just use SATA). most new drives don't even have a jumper setting or the setting is simply to do a drive reset of some sort

make sure that both cables (power/data) are properly secured (can be a bit of a pain with some boxes) and that your cmos settings are correct (most setups now a days simply have 'autodetect' or 'disable')

---

### Post by verymadpip on 2012-03-21
Hello again.
My next suggestion, mentioned by HIImTye, is to check that the drive auto-detect feature in your BIOS is on.

Can you boot Ubuntu if it's the only drive in the box & is set to 'master' I wonder?

This is beginning to vex me too longshanks62...

---

### Post by longshanks62 on 2012-03-21
Hello all,
 pardon my frustration but I have answered all Q's and advise given. All I have done is install ubuntu onto a previously working stable PC no cables were touched apart from my one sata HD which contains my working O/S win7/XP which as I previously stated " I removed that data lead as a precaution so as not to corrupt MBR" that's it one cable. once the installation was complete I replaced that cable and rebooted re-ajusted the boot order in the bios. I am lost for an answer it is as if the HDD died!! strange that suggestion though everything was working perfectly well before I encountered ubuntu.
I thank you all for your time in answering this post.

---

### Post by verymadpip on 2012-03-22
Well, if you changed the boot order in the BIOS it must be showing up, or it has at least once.

The bootloader GRUB should have been installed to the Ubuntu HDD & that drive set to boot first.

HDDs do die by the way & not necessarily for any obvious reason.

I've reached the limit of my knowledge, good luck.

---

### Post by Mark Phelps on 2012-03-22
> **HiImTye said:**
> I don't think jumpers are an issue in any modern computer, as most new drives use only SATA ...

Right ... and did you bother to read the part where the OP mentioned having problems where an IDE drive was not being seen?

If all we had been discussing here was SATA drives, I would not have said anything about jumpers in the first place.

---


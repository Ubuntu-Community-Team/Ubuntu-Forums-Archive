---
title: "Newbie Xp and Ubuntu questions"
date: 2013-02-10
forum: New to Ubuntu
---

### Post by Curbie on 2013-02-10
I’ll spare everyone the sob story, but I’ve dealing with XP pro issues since December and any time over the last several years I’ve had to deal with Windows issues, I check out Ubuntu as I did last December.
   
  Since I had to reload Windows anyway, I tried several times to set that drive to dual boot XP pro/Ubuntu with no luck. I’m sort of stuck with Office Pro which I've done work in for 25 years and have accumulated 25 years worth of data I can’t lose.
   
  I was thinking about setting an up XP pro system to work on data and another Ubuntu system to deal with web access, I used Ubuntu in December to correct a HP “code purple” bomb the HP loaded and I’d be running Ubuntu for the Web already if I could have gotten the dual boot the function.
   
  So, my questions are:
  1)      Can I network a XP pro and a Ubuntu machine to together just to push Win files back and forth from the web?
  2)      Has any heard of anyone using Ubuntu just for the Web, and as a pseudo hardware firewall to isolate Windows from the Web?
  3)      Is there a link for setting up Ubuntu in a single boot configuration?
4)   A better way to accomplish the same thing?

   
  Thanks for any replies.

---

### Post by sudodus on 2013-02-10
Welcome to the Ubuntu Forums :-)

I will come back with a longer reply soon. I think you will be able to solve your tasks.

---

### Post by chadk5utc on 2013-02-10
I have in the past used XP pro dual boot with many versions of linux I found the easiest way to do this was to have windows installed first then install linux following the installer directions for dual boot was easy to setup. I now only use single boot. linux systems with the exception of the work laptop.
 As for using linux as a router/firewall yes this is possible and done all the time there are tons of how to's online for this, heres one:  [https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)
Also on this note there are linux distro's like pfsense, ClearOs and many others but keep in mind these take some experience to get setup. There are a number of Ubuntu based how to's that should get you going fairly easy.

---

### Post by sudodus on 2013-02-10
> **Curbie said:**
> ...   
  Since I had to reload Windows anyway, I tried several times to set that drive to dual boot XP pro/Ubuntu with no luck. I’m sort of stuck with Office Pro which I've done work in for 25 years and have accumulated 25 years worth of data I can’t lose.

Do you mean Microsoft Office? Unless you have special formating in your Office documents, you can read and edit them with Libre Office in Ubuntu. But I guess you have checked that already.
> 
  I was thinking about setting an up XP pro system to work on data and another Ubuntu system to deal with web access, I used Ubuntu in December to correct a HP “code purple” bomb the HP loaded and I’d be running Ubuntu for the Web already if I could have gotten the dual boot the function.
   
  So, my questions are:
  1)      Can I network a XP pro and a Ubuntu machine to together just to push Win files back and forth from the web?

I guess that you have bad experiences from connecting Windows to the internet.

Are you thinking of two computers, one with Windows XP and one with Ubuntu? Or are you thinking of dual booting the same computer, or running Ubuntu and inside it run a virtual machine (for example VirtualBox) with Windows XP?

Ubuntu can mount Windows file systems, FAT32 and NTFS on the same computer. It is common to have an NTFS data partiton for access from both Windows and Ubuntu on dual boot systems. If you have two computers, you can access the other computer via network sharing, and this is independent of the file system.

So yes, you can write a file in Windows and let Ubuntu read it (or send it via the internet). You can also get a file via the internet using Ubuntu, and write it to a drive, where Windows can use it. But I have not done it automatically, and I don't know how to do that.
> 

  2)      Has any heard of anyone using Ubuntu just for the Web, and as a pseudo hardware firewall to isolate Windows from the Web?

I don't have any own experience of that. But I guess that you can disable the network while running Windows, either by unplugging it or switching it off. There used to be an option to 'run off-line' in Windows.
> 
  3)      Is there a link for setting up Ubuntu in a single boot configuration?

This is the simplest case. You hardly need a link for it. Just boot from the Ubuntu install drive (CD or USB) and install the system.

[[COLOR="Red"]http://www.ubuntu.com/download/help/install-desktop-long-term-support[/COLOR]]("http://www.ubuntu.com/download/help/install-desktop-long-term-support")

But depending on your computer specs (cpu, ram, graphics chip, wifi chip), you might need or prefer another flavour, than [vanilla] Ubuntu: ***Lubuntu*** or ***Xubuntu*** with light-weight desktop environments, or ***Kubuntu*** with KDE (fancy eye-candy but a different style than ***Unity of Ubuntu***)

***But you must backup (or move) any data, that you want to keep*** from that drive before the installation.
> 
4)   A better way to accomplish the same thing?
   
  Thanks for any replies.
If your computer has enough horsepower (CPU) and RAM, and if you have a licence key for Windows XP, you can install it to a virtual machine inside Ubuntu. But you still have to be careful with firewalls, anti-virus etc for internet access or switch if off.

---

### Post by DuckHook on 2013-02-10
Please provide much more info about your physical system: CPU, system RAM, video subsystem, video RAM, HDD capacity, etc. If easier, boot up with Ubuntu LiveDVD and post output of this:

```
sudo lshw -short -sanitize
```Another poster today asked about XP. Rather than repeat, I encourage you to read my reply to him [here]("http://ubuntuforums.org/showthread.php?p=12501191#post12501191"). There appear to be many commonalities with your requirements.

Please also list all the Windows programs (including version) that you feel to be indispensable. If its just MSWord, then WINE can be very effective at running it inside Linux. There's an excellent article on WINE in Wikipedia. You can also visit WINE's website [here]("http://www.winehq.org/about/").

Sudodus is right. Won't be a quick process to ascertain your needs and answer your question, but the above info will go a long way.

---

### Post by Locus Kiesselbachi on 2013-02-10
Hello!
How old is your computer?
As Im new to Linux and software is not my strongest side:
I would recommend to add another hard-drive/hard-disk, to but new OS on that. 
Then choose "boot-drive" order from BIOS which chooses your OS to start. Now you can swap files back and forth regarding of what OS or user-privileges you have on the other  harddrive.
Best regards!

---

### Post by Paqman on 2013-02-10
> **Curbie said:**
> 
4)   A better way to accomplish the same thing?


As mentioned above, a virtual machine. 

Win XP is quite light, any dual core or better machine with more than about 3GB of RAM should be able to run XP and Office on top of Ubuntu. You can run Virtualbox in "seamless mode" that will allow Office to look like it's running as an application on your Ubuntu desktop.

---

### Post by deadflowr on 2013-02-10
I think the easiest thing would be to setup XP in a virtualbox and create a shared folder.
[https://help.ubuntu.com/community/VirtualBox]("https://help.ubuntu.com/community/VirtualBox")

And to answer question two, yes I've known and read of quite a few people who browse and access the internet with a linux system and completely disable their windows system's networking functions.

---

### Post by sudodus on 2013-02-10
> **DuckHook said:**
> ... Another poster today asked about XP. Rather than repeat, I encourage you to read my reply to him [here]("http://ubuntuforums.org/showthread.php?p=12501191#post12501191"). There appear to be many commonalities with your requirements.

Please also list all the Windows programs (including version) that you feel to be indispensable. If its just MSWord, then WINE can be very effective at running it inside Linux. There's an excellent article on WINE in Wikipedia. You can also visit WINE's website [here]("http://www.winehq.org/about/").
...
+1
There are several good points in that link :-)

---

### Post by Curbie on 2013-02-10
Wow, I was hoping for a response, lots of responses!
   
  Sudodus
   
  When I say can’t do without… Office pro is Word, Excel, Access and others: I’m never going to get away from Access, but instead of boring some and pissing off others, I’ll write a few lines on the 100’s of Excel files I have written and still use over the years. 
   
  We’ll start with the libraries of User Defined Functions that drive them:
  Balance.Bas, Constants.Bas, Distance.Bas, Energy.Bas, Excess.Bas, GasLaw.Bas, Globals.Bas, GoalSeek.Bas, H2ODensity.Bas, HETP.Bas, McCabe.Bas, Moles.Bas, MolecularWeights.Bas, Pressure.Bas, Properties.Bas, SIUnits.Bas, Still.Bas, Temperature.Bas, Vacuum.Bas, Volume.Bas, Weight.Bas
  …each library contains UDFs like:
  Attribute VB_Name = "Distance"
  ' Distance Conversion Routines
  ' Between (M)eters, (C)entimeters, (mm)millimeters, (F)eet and (I)nches
  Option Explicit                               ' force explicit declaration of all variables
   
  ' *** Meters to:
  Public Function CD_M2C(M As Double) As Double
  ' Returns distance in Centimeters for the given distance in Meters.
  CD_M2C = M * 100
  End Function
   
  Public Function CD_M2mm(M As Double) As Double
  ' Returns distance in Millimeters for the given distance in Meters.
  CD_M2mm = M * 1000
  End Function
  … and those UDFs, literally 100’s of them are scattered in the expressions of 100s of spread-sheet, I.E. =IF(Units = "A",((Wp(CT_F2C(TF), "DenL") / Kilo) * (l2gal * Kilo)) / g2lb,(Wp(TF, "DenL") / Kilo))
   
  My Access needs are worse, and that doesn’t include all the other programs and their data files I have, maybe I can make some transitions but certainly not overnight, when I say can’t do without, let’s go with that. I need a XP pro machine, I want an Ubuntu machine to talk to net and buffer the XP machine from harm.
   
  I don’t care if a have to build a separate box for Ubuntu, in December I loaded Ubuntu 4 times in different dual boot configurations and couldn’t get any to function, so now I’m thinking that a dedicated Ubuntu system may be the ticket, I’m just a little shell shocked from 4 tries in December.
   
  Of course I have had bad experiences on the net I’ve been there since ARPAnet, but that doesn’t bother me, that what’s mirrored backups are for, dealing with HP factory loaded bombs and paying MS $300.00 for the same thing every time I have a motherboard problem or upgrade does. Enough sob stories, everybody has one, I’m just trying to solve problems and get back to using computers as a tool to find answers to things that matter to me
   
  Yes, I’m  thinking of two computers, one with Windows XP and one with Ubuntu and I was hoping XP and Ubuntu would network, I don’t mind the idea of pushing files back and forth over a local network as long as I protect the Windows.
   
  And I read DuckHook’s post before I posted, I know MS is going to stop support for XP, I’ve always had two choices, stay with MS totally (new Win 8 system and programs), or freeze and protect XP, if I have to learn a new system, I’d prefer to learn Ubuntu and just freeze and protect XP, and transition what I can at my own pace.
   
  I have a year to figure all this out, so I should start now by getting some more hard drives to see if Ubuntu loads as a single system.
   
  And to everyone who replied, what a pleasant surprise, I hope some of you folks are around when I try to load Ubuntu as a single boot system, I wish I knew about this board last December, THANKS.

---

### Post by sudodus on 2013-02-10
> **Curbie said:**
> ...
  When I say can&#8217;t do without&#8230; Office pro is Word, Excel, Access and others: I&#8217;m never going to get away from Access
...
  Yes, I&#8217;m  thinking of two computers, one with Windows XP and one with Ubuntu and I was hoping XP and Ubuntu would network, I don&#8217;t mind the idea of pushing files back and forth over a local network as long as I protect the Windows.
   
  And I read DuckHook&#8217;s post before I posted, I know MS is going to stop support for XP, I&#8217;ve always had two choices, stay with MS totally (new Win 8 system and programs), or freeze and protect XP, if I have to learn a new system, I&#8217;d prefer to learn Ubuntu and just freeze and protect XP, and transition what I can at my own pace.
   
  I have a year to figure all this out, so I should start now by getting some more hard drives to see if Ubuntu loads as a single system ...

I understand that you need Windows, and plan to continue with Windows XP (to have it protected from the internet preparing for the end-of-life next year).

It is certainly possible with dual-boot, but if you feel safer, and maybe also want the flexibility of two computers, fine! Then you can select a suitable computer to run Ubuntu (or Lubuntu, Xubuntu, Kubuntu). Since you need only fair graphics for on-line video, it need not be a new computer. In many countries there is a market for used professional computers at very reasonable prices, and an old desktop or laptop with a core2duo CPU will run very well with Lubuntu or Xubuntu. Or you can select a new computer with lower end or medium specifications.

Connect the two computers in a local area network via a router. Get a router that is also a firewall (most of them are). If it is a little more than the simplest router, you can configure it to block internet access to and from your Windows computer (that IP address).

***Edit***: If you are concerned about security, a wired network connection is better than wireless.

---

### Post by DuckHook on 2013-02-10
I run XP in a VM and intend to run it well past it's die-date. For that matter I run Win 95 in a VM and it expired years ago. Neither have anti-virus or any other sort of bloat loaded. In Win 95's case, such measures are no longer available or effective anyhow. But here's the absolutely critical key: I never, ever, on pain of self-flaggelation and self-recrimination, surf with Windows, download anything, load anything or run anything except some tried-and-true trusty-but-musty games that I've enjoyed for decades. If they harbour viruses which will pop up only now after close to twenty years of use, well, c'est la vie. All communication with the outside world is done with Ubuntu. All chances are taken with the better OS. XP is used for nothing but the half-dozen apps that are the only reason for its continuing existence. If you can similarly constrain your XP usage with this ironwilled discipline, there is no reason why you can't use it for years past its die-date.

A VM has a further advantage: you can roll back to a last working snapshot if something goes wonky. This is infinitely better than suffering through the hours of Windows' interminable install process. You will end up regretting that you had not already been using this method for years.

You have described your dependency on MS Office admirably. I agree that you will not be able to get away from it--at least not without months of stress-testing and analysis. This is clearly a production environment for you and must be absolutely solid. LibreOffice is unlikely to cut it for you and WINE is a long way off, so *@deadflower's* and others' recommendation of a VM is absolutely the way to go. It is very simple to set your XP VM up so that it shares certain directories with Ubuntu. The reading of files from this shared directory tends to be slow and quirky, but you have already stated that you don't mind its taking its time so long as it is reliable.

You will likely need a new machine. I am assuming that your current box is pretty old. But notwithstanding, it appears to be suspect given your constantly recurring need to reinstall XP. Since you are obviously counting on this box a great deal, I wouldn't bother with a "minimal" box, but one that is practical--even overkill--for your needs. I've just built a new box for Christmas, but I don't actually recommend that you go this way. The difference is, I'm a retired tinkerer with no production pressure; you need something that works right out of the box and with no complications. Therefore, I recommend a Linux machine from any of the vendors who specialize in making and preloading Linux boxes. These are guaranteed to work and will have components specifically chosen for compatibility with Linux. IMO, Dell is an excellent choice (get their four-year extended warranty and phone support), or you can Google for dozens of reputable Linux prebuilt vendors who all make good stuff. You don't need fancy. Focus on reliability.

Once the new box arrives, the people on this forum are more than happy to help you spin up your first VM. As a primer, you can read [this]("https://help.ubuntu.com/community/VirtualMachines"). At this point, the idea is to only provide you with an understanding of what is possible. Do not actually proceed until you get lots of advice and instructions from this forum. So far, I use KVM and VirtualBox and am starting to explore Xen, but strongly recommend that new users stick to VirtualBox. It is easier to set up and more widely used. The operative principle of stress-free computing is: "Keep It Simple, Stupid".

<edit>
[Here]("http://www.zdnet.com/blog/open-source/the-top-five-linux-desktop-vendors/9313") is a pretty decent article on Linux box builders. It seems that Dell has fallen off the train recently with regard to Linux. My info appears to be outdated.
</edit>

---

### Post by Curbie on 2013-02-10
Sudodus & DuckHook, thanks for the replies.
   
  I just bought and put together a  new machine with a AMD Anthon II triple core 3.2Ghz (800ghz x 3) with 8gb of memory as a replacement for the XP machine (I know XP only uses 4gb) or as a box for Ubuntu, I’m still not sure what this new XP/Ubuntu configuration will look like.
   
  I guess I can use it to test the different configuration notions, dual or single boot, or virtual machine, I suppose I’d be better off running a VM if the new machine is fast enough to test it, I can always buy a faster machine if I go with the VM option.
   
  I too am retired, although I still spend 5+ hours/day on my computer so I have time to twink around with different configuration notions ONCE, I don’t want to spend time learning how to do the same thing a different way with their style over substance non-sense.
   
  I suppose I should get some new hard drives to start testing these different configurations, although I could get kicked off the board by bombing it with questions as I test each configuration, but it is pretty important to me I come up with the best way to solve this problem.
   
  What do you think?

---

### Post by DuckHook on 2013-02-10
You are full of surprises!

...a Fellow Retahhrdee... well then, you've got plenty of time and you've been playing us along all the while!;)

Barring any unsupported components, your new machine is perfect for Linux. Just the right power, will easily run an XP VM, and seeing as you've already built it--you scoundrel--all of my previous comments re: buying one are academic. Most definitely let's make your current box sing. No need to spend further money.

Seeing whether Ubuntu will run is simplicity itself: just burn a LiveDVD, boot it up to a Live session (do not install yet) and take if for a test drive. If the system boots up to a pretty desktop and you can surf the Net, then the Linux gods are smiling and all is well with the world. However, it is important to do a few things prior to installing that will make the later process even easier:

1. Burn not just Ubuntu, but Kubuntu, Xubuntu and Lubuntu. You can and should test drive all these flavours to see which you are most comfortable with. Take your time. I'm betting that you will prefer Lubuntu due to its similarity to XP, but my own personal preference is Ubuntu. Unity has quite grown on me.

2. While you are in the Live session, do the following (previously requested):
```
sudo lshw -short -sanitize
``` and post results to this thread. Additionally...
3. ```
sudo lspci -vk | grep -iA20 'vga\|eth'
``` All of this is designed to look at your video subsystem and network chips--the two areas that give the most problems on new installs.
4. What size is your HDD?

Next we will consider partition schemes, but let's see what HW you've got first.

---

### Post by Curbie on 2013-02-10
DuckHook,
   
  Well, I have time for anything important, but I’m not in love with computes, not the CDCs I started on or my first computer, a PDP-11, computers have always been a tool to solve problems, and in my retirement the problem that keeps busy is alternative energies.
   
  This is a problem I have to solve, so if is beneficial to spend money to build a faster machine, I will, remember I’ll have to buy a new XP pro license for the virtual machine, and XP activation will still be tied to that motherboard, if I choose that option I’d still be able to upgrade the motherboard for new versions of Ubuntu, but not without a new XP pro license, it seems like a better idea to settle on an XP/Ubuntu solution, then buy and build the biggest machine it can run on.
   
  I have one older version and the two latest versions (as of December) of Ubuntu (I tried two different versions in December trying to figure out what I was doing wrong). I didn’t problems booting any of them from CD, I couldn’t get dual boot to setup on one, and the other wouldn’t setup at all, but listening to people on this thread, this all had to either hardware compatibility issues, or something I consistently did wrong, although I’ve setup more than a few machines in my time. I’ll just start from starch, and I’ll just buy another drive for testing, so assume .5tb drive for testing.
   
  Is there any capability differences between Ubuntu, Kubuntu, Xubuntu and Lubuntu or are the differences just basically skins, I didn’t have any problems navigating Ubuntu, but would give Lubuntu a try if it’s closer to XP without losing capabilities or support. I don’t need fancy looking desktops, just functional and intuitive tools.

---

### Post by DuckHook on 2013-02-10
To cut to the chase, then, use Xubuntu 12.04. They all work from the same foundation. These days, "skin" is merging with base functionality, but the fixes and techniques that work for the one will work for the other. In your case, I recommend Xubuntu over Lubuntu (which is actually closer to XP) because Xubuntu 12.04 is long term support whereas Lubuntu has no LTS. Since you want to install it and forget it, you want the version that will be supported for as long as possible.

You should still take it for a test drive. Seeing how you like it is only one goal: you want to make sure it works without chokes or complaint. Download from [here]("http://xubuntu.org/getxubuntu/"). Make sure you choose 12.04 64 bit. Not 12.10. Not 32-bit. If you know how to torrent, that is the best method. It is self error checking and I get the best ISOs that way. If you don't want to torrent, then locate the closest mirror site and download the traditional way. Either way, make sure you hash the image, do the burn, hash the burn.

After satisfied that a LiveDVD session won't break (provide output of commands already requested), post back for further instructions. (Very) General preview:

1. Backup what needs backing up.
2. Partition HDD
3. Install Xubuntu
4. Configure Xubuntu to your comfort.
5. Add VirtualBox PPA (preferred over repository version for various reasons)
6. Install VirtualBox
7. Install XP ***Important*** Do not install your new XP Pro on another piece of HW. The license you purchase will be used up on the VM, which virtualizes a motherboard, processor and HDD UUID.
8. Once installed, you can copy off the XP VM to a backup medium for safekeeping.
9. Install MS Office in XP VM.
10. Transfer current files to XP VM

Voila.

Again, you will be burning up the XP license on the VM, so don't install it separately to dual boot unless you change your mind and forego VM.

BTW, XP on a VM is highly transferable. You will have to decide whether merely moving the same copy from one HW platform to another constitutes a re-licensing event.

---

### Post by sudodus on 2013-02-11
A lot has happened while I have been sleeping :-)

It seems you are doing well. I'll pop in later, if there is something I can add.

---

### Post by Curbie on 2013-02-11
Well, this procedure kicked up yet another problem, this time with my DSL, when I tried to download xubuntu-12.04.1-desktop-amd64.iso I discovered my 10mbs DSL is running at a terribly hobbled rate, something like 28kbs, and the phone side isn’t working at all.
   
  So I’ve spent the afternoon bouncing between a neighbor’s on phone with DSL technical support and my home DSL marching through technical support problem verification list, which included me driving to store to buy a phone to verify to technical support that problem wasn’t with my phone. I get 1 call per month, maybe, so I don’t even know how long this has been going on, but it’s made downloading xubuntu a 4 hour task.
   
  I was however able to buy a .5tb drive to test these xubuntu configurations on my phone journey, and while I was waiting I had plenty of time to revisit the Ubuntu downloads I did in December and they were both i386 versions 12.04 & 12.10, so I hoping that was why my December loads failed. (dummy x 2)
   
  I downloaded xubuntu-12.04.1-desktop-amd64.iso and its MD5 hash (16fea2603876247caf41f30066bc95e4) and using winMd5Sum.exe checked the download iso’s hash, which matched, burned a DVD (wouldn’t fit on a CD), then checked the DVD’s hash which also matched.
   
  Now that the new hard drive has had time to come to room temperature, I’ll remove my loaded hard drives to protect their data and try a xUbuntu single boot install as the first test.

---

### Post by mastablasta on 2013-02-11
> **Curbie said:**
> I was however able to buy a .5tb drive to test these xubuntu configurations on my phone journey, and while I was waiting I had plenty of time to revisit the Ubuntu downloads I did in December and they were both i386 versions 12.04 & 12.10, so I hoping that was why my December loads failed. (dummy x 2)
.
 
nope. the 32 bit works just nicely on 64 bit CPU. but 64bit OS won't work on 32bit CPU.
 
To me Kubuntu is the closest to windows (the way it acts and interfaces with the user). especially with classic K menu turned on. these desktop environments are different because they :
- are based on different libraries (e.g. KDE is based on qt, Unity is based on GTK+)
- use different set of default programmes as a result (though you can install a programme from another desktop they might not feel so integrated)
- have a different way in how they draw widnows and graphics on the screen
- they communicate with user differently (e.g Unity/Gnome hide some settings from GUi so as not to overwhelm the user, while KDE has plenty of settings done via GUI)
- have different levels of desktop customisation available. also the methods how to do them in some are via GUi while others have text files that need to be changed "manually"
- use different amount of system resources. icewm can use as low as 50 MB on boot, XFCE about 80-100 (though xubuntu a bit higher), LXDE also about 70-80 MB. KDE is over 200 MB as well as Unity in default Ubuntu. some of them look like win95, but with all the modern stuff on.
 
 
Point is it payes to try them out to see which one you like most. To me KDE (Kubuntu) and XFCE (Xubuntu) seem most intuitive. and everytime i search for something (a setting or somehting else) i can find it easilly by myself. which is why i use the two. LXDE is also nice as it's fast and light, but something there it never worked on my maschines. so i let it be. but it might end up on a netbook in virtualbox. still testing it.
 
anyway good luck with your project. there is also a help IRC channel for more immediate help if you get a big issue..

---

### Post by Curbie on 2013-02-11
Well, that didn't work either, the xUbuntu DVD I burned won't boot, I get a message a "Reboot and select proper boot device or insert boot media in selected boot device as press any key" which smells to me like a bios message.
 
I then tried an old version of Ubuntu to test the notion of booting from a DVD vs. CD (a shot in the dark) which was burned on a DVD and it booted to Ubuntu from the DVD, but I couldn't access the internet with firefox, more on that later.
 
I checked the MD5 hash both for the downloaded and burned ISOs and both matched the the MD5 hash downloaded from xUbuntu, and the hardware is all new AMD Anthon II triple core 3.2 ghz, a Biostar A780LC3 motherboard loaded with 4gb of memory.
 
I first loaded it with XP and it has been running fine for a while until I removed the XP OS and data drives and tried to load xUbuntu onto the .5tb drive I bought today for testing which wouldn't boot xUbunto, it did boot an old verion of Ubuntu, but firefox couldn't access the internet.
 
So I reattached to XP OS drive and rebooted XP to report these steps here, and now XP can't access the net, no DNS server found, and there now there are no networks shown or network adapters in device manager.
 
The only thing I can make out of all this is that xUbunto or Ubuntu clobbered something having to do with the on-board NIC in bios flash memory, but that's a guess. 
 
Anyway the only fully function system I have up now is a Win 8 system, which I hate that I bought to handle my net communications until I got XP up and going last December in which I'm posting the message with.
 
The cheezy picture documentation that came with the motherboard mentions a jumper to clear the CMOS if the "CMOS data has become corrupted" this option talks about the BIOS menu's supervisor/user password and cpu clock set in BIOS, but I have no clue what else is there.
 
Any ideas of what I shoud do next?

---

### Post by sudodus on 2013-02-11
> **Curbie said:**
> ... 
The only thing I can make out of all this is that xUbunto or Ubuntu clobbered something having to do with the on-board NIC in bios flash memory, but that's a guess. 
...

I don't think so. If I remember correctly Ubuntu does not change the BIOS settings at all. So I think you have an issue with the internet connection outside the computer. Do you use a router or are you connecting directly via the DSL to your internet service provider? Where is your IP address managed?
[B][I]
Edit[/I][/B]: Do you use wired or wireless connection?

---

### Post by Curbie on 2013-02-11
> **sudodus said:**
> I don't think so. If I remember correctly Ubuntu does not change the BIOS settings at all. So I think you have an issue with the internet connection outside the computer.
I think you're right about that, the DSL people just called to say they found a problem and now my phone is working, and the internet speed tests are showing 10mbs again. One problem down.

> **sudodus said:**
> Do you use a router  or are you connecting directly via the DSL to your internet service  provider? Where is your IP address managed? Do you use wired or wireless connection?
Just a DSL box, and I would imagine that it is a dynamic IP but I don't know for sure, on a wired connection.

I'm going to try booting and loaded xUbuntu on the new drive again. This massage was sent from XP which is fully functional again and the Win 8 machine is in the corner, where it should be collecting dust.

---

### Post by Curbie on 2013-02-11
Same issues as yesterday, the xUbuntu DVD I burned won't boot, I just get a message "Reboot and select proper boot device or insert boot media in selected boot device and press any key" which smells to me like a bios message.
 
 
  I rechecked the MD5 hash and it matches the one downloaded from xUbuntu, it just doesn’t make sense that the xUbutu DVD won’t boot with the proper MD5 hash, it only tickles the DVD during startup like there’s no boot information on that DVD.
   
  Yesterday, I got an old version of Ubuntu to boot, I have a bootable drive mirror CD, I guess I’ll see if that boots, and try to reboot the old version of Ubuntu to see if the DSL fixes allows Firefox in that version to access the web, but I’m quickly running out of ideas.
   
  Is ?Ubuntu real picky about the hardware it runs on?

---

### Post by Curbie on 2013-02-11
It just doesn’t make sense that the xUbuntu DVD won’t boot with the proper MD5 hash, so went back out to xUbuntu and there’s a new version xubuntu-12.10-desktop-amd64.iso which I downloaded with its MD5 hash (f5f80e22cb1c80232efcbd8e2c5955f8). I know DuckHook recommended against 12.10, but I’m running out of ideas.
   
  I started from scratch again using winMd5Sum.exe checked the download iso’s hash, which matched, burned a DVD, then checked the DVD’s hash which also matched.
   
  Same issues as yesterday, the 12.10 xUbuntu DVD I burned won't boot, I just get a message "Reboot and select proper boot device or insert boot media in selected boot device and press any key" which smells.
   
  I have a 12.10 version of Ubuntu from the December tries, and it boots and runs from DVD fine, and now that my DSL is fixed Firefox is working too, although I couldn’t figure out where to type in sudo lshw -short –sanitize and  sudo lspci -vk | grep -iA20 'vga\|eth' which looks like command line stuff to me.
   
  I never did the a md5 hash on the Unubtu DVD in December, I’ll try to find the hash total for that and check it against the DVD, I guess I’ll download Ubuntu and go through the same procedure with that, but I'm starting to through crap at the wall in hopes that something will stick.
   
  Any ideas of what I should do next?

---

### Post by Dodeca on 2013-02-11
> **Curbie said:**
> It just doesn&#8217;t make sense that the xUbuntu DVD won&#8217;t boot with the proper MD5 hash, so went back out to xUbuntu and there&#8217;s a new version xubuntu-12.10-desktop-amd64.iso which I downloaded with its MD5 hash (f5f80e22cb1c80232efcbd8e2c5955f8). I know DuckHook recommended against 12.10, but I&#8217;m running out of ideas.
   
  I started from scratch again using winMd5Sum.exe checked the download iso&#8217;s hash, which matched, burned a DVD, then checked the DVD&#8217;s hash which also matched.
   
  Same issues as yesterday, the 12.10 xUbuntu DVD I burned won't boot, I just get a message "Reboot and select proper boot device or insert boot media in selected boot device and press any key" which smells.
   
  I have a 12.10 version of Ubuntu from the December tries, and it boots and runs from DVD fine, and now that my DSL is fixed Firefox is working too, although I couldn&#8217;t figure out where to type in sudo lshw -short &#8211;sanitize and  sudo lspci -vk | grep -iA20 'vga\|eth' which looks like command line stuff to me.
   
  I never did the a md5 hash on the Unubtu DVD in December, I&#8217;ll try to find the hash total for that and check it against the DVD, I guess I&#8217;ll download Ubuntu and go through the same procedure with that, but I'm starting to through crap at the wall in hopes that something will stick.
   
  Any ideas of what I should do next?


My suggestion to you is ...

be sure to burn your install dvd as an .iso and burn at  slowest speed

to enter command line stuff ... do it in a TERMINAL ( press control -alternate - t ) to open a terminal

---

### Post by DuckHook on 2013-02-11
> **Curbie said:**
> Is ?Ubuntu real picky about the hardware it runs on?

The different flavours of Ubuntu are no pickier than XP, but yes, this means that there is some HW out there that is difficult and must be tweaked to run.

It is possible that your DVD drive is having trouble reading certain DVDs. This happens to me occasionally. Don't know why. Some DVD brands work, some don't. It is impossible to diagnose without more info. Have you set your BIOS to boot from the DVD? You can also try the key combo for your motherboard that brings up the one-time boot menu. Final option: use the Ubuntu 12.10 DVD that does work, boot into live DVD mode and run the commands. If you like this version and it works, there may simply be no need to go searching any further. This would render the issue of Xubuntu academic.

The commands I asked you to run are indeed command line stuff. The easiest way to bring up a terminal in Ubuntu is with the following key combo: <Ctrl>+<Alt>+<t>. Then cut and paste the commands using your mouse.

---

### Post by Curbie on 2013-02-11
Dodeca & Duckhook,
   
  The DVD reader and writer is an MSI SATA, it make some sense that it would be the problem because it’s only component common to the HP computer that wouldn’t load in December and the new system. I’ll try dodeca’s suggestion and slow down the burn rate to as slow as possible and re-burn xUbuntu 12.04 and 12.10 to see if that was causing them not to boot.
   
  Either way, I’ll get and post that command line information to see if that can clear anything up.

---

### Post by Curbie on 2013-02-12
More of the same, I rechecked the MD5 hash totals for xUbuntu 12.04 & 12.10, re-burned them at as slow as possible (4x), checked the hash totals for the DVDs, shut the machine down, removed the XP drive and installed the (new raw un-formatted) drive, and tried to boot both 12.04 & 12.10 and no go.
  

Then I booted ubuntu 12.10, I did run the command lines asked for, I hope they shed light on my troulbes:
  ubuntu@ubuntu:~$ sudo lshw -short -sanitize
  H/W path        Device      Class       Description
  ===================================================
                              system      A780L3C (To Be Filled By O.E.M.)
  /0                          bus         A780L3C
  /0/0                        memory      64KiB BIOS
  /0/4                        processor   AMD Athlon(tm) II X3 450 Processor
  /0/4/5                      memory      128KiB L1 cache
  /0/4/6                      memory      512KiB L2 cache
  /0/24                       memory      4GiB System Memory
  /0/24/0                     memory      4GiB DIMM Synchronous 667 MHz (1.5 ns)
  /0/24/1                     memory      [empty]
  /0/24/2                     memory      [empty]
  /0/24/3                     memory      [empty]
  /0/1                        processor   
  /0/1/0                      memory      128KiB L1 cache
  /0/1/1                      memory      512KiB L2 cache
  /0/2                        processor   
  /0/2/0                      memory      128KiB L1 cache
  /0/2/1                      memory      512KiB L2 cache
  /0/100                      bridge      RS780 Host Bridge
  /0/100/1                    bridge      RS780/RS880 PCI to PCI bridge (int gfx)
  /0/100/1/5                  display     RS780L [Radeon HD 3000]
  /0/100/7                    bridge      RS780 PCI to PCI bridge (PCIE port 3)
  /0/100/7/0      eth0        network     RTL8101E/RTL8102E PCI Express Fast Ether
  /0/100/11                   storage     SB7x0/SB8x0/SB9x0 SATA Controller [IDE m
  /0/100/12                   bus         SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
  /0/100/12.1                 bus         SB7x0 USB OHCI1 Controller
  /0/100/12.2                 bus         SB7x0/SB8x0/SB9x0 USB EHCI Controller
  /0/100/13                   bus         SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
  /0/100/13.1                 bus         SB7x0 USB OHCI1 Controller
  /0/100/13.2                 bus         SB7x0/SB8x0/SB9x0 USB EHCI Controller
  /0/100/14                   bus         SBx00 SMBus Controller
  /0/100/14.1                 storage     SB7x0/SB8x0/SB9x0 IDE Controller
  /0/100/14.2                 multimedia  SBx00 Azalia (Intel HDA)
  /0/100/14.3                 bridge      SB7x0/SB8x0/SB9x0 LPC host controller
  /0/100/14.4                 bridge      SBx00 PCI to PCI  Bridge
  /0/100/14.5                 bus         SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
  /0/101                      bridge      Family 10h Processor HyperTransport Conf
  /0/102                      bridge      Family 10h Processor Address Map
  /0/103                      bridge      Family 10h Processor DRAM Controller
  /0/104                      bridge      Family 10h Processor Miscellaneous Contr
  /0/105                      bridge      Family 10h Processor Link Control
  /0/3            scsi0       storage     
  /0/3/0.0.0      /dev/sda    disk        500GB ST500DM002-1BD14
  /0/5            scsi3       storage     
  /0/5/0.0.0      /dev/cdrom  disk        DVD A  DH20A6L
  /0/5/0.0.0/0    /dev/cdrom  disk        
  /0/5/0.0.0/0/1              volume      753MiB Hidden HPFS/NTFS partition
   
  **************************************************************
   
  ubuntu@ubuntu:~$ sudo lspci -vk | grep -iA20 'vga\|eth'
  01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS780L [Radeon HD 3000] (prog-if 00 [VGA controller])
      Subsystem: Biostar Microtech Int'l Corp Device 0017
      Flags: bus master, fast devsel, latency 0, IRQ 18
      Memory at d0000000 (32-bit, prefetchable) [size=256M]
      I/O ports at d000 [size=256]
      Memory at febf0000 (32-bit, non-prefetchable) [size=64K]
      Memory at fea00000 (32-bit, non-prefetchable) [size=1M]
      Expansion ROM at <unassigned> [disabled]
      Capabilities: [50] Power Management version 3
      Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
      Kernel driver in use: radeon
      Kernel modules: radeon
   
  02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
      Subsystem: Biostar Microtech Int'l Corp Device 230d
      Flags: bus master, fast devsel, latency 0, IRQ 42
      I/O ports at e800 [size=256]
      Memory at fdfff000 (64-bit, prefetchable) [size=4K]
      Memory at fdff8000 (64-bit, prefetchable) [size=16K]
      Capabilities: [40] Power Management version 3
      Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
      Capabilities: [70] Express Endpoint, MSI 01
      Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
      Capabilities: [d0] Vital Product Data
      Capabilities: [100] Advanced Error Reporting
      Capabilities: [140] Virtual Channel
      Capabilities: [160] Device Serial Number 5d-00-00-00-36-4c-e0-00
      Kernel driver in use: r8169
      Kernel modules: r8169

---

### Post by mastablasta on 2013-02-12
> **Curbie said:**
> Same issues as yesterday, the 12.10 xUbuntu DVD I burned won't boot, I just get a message "Reboot and select proper boot device or insert boot media in selected boot device and press any key" which smells.

 
it means the burned DVD is not a bootable DVD.
 
i am curious, do you actually have multiple files and folders on the Xubuntu DVD? or just one .iso file of which you are checking the md5sum?
 
furthermore, if you have at least 2GB USB stick you can use that along with programme like linuxliveusb or unetbootin to create a bootable Linux USB stick in windows.
 
edit: sorry, 1 GB USB stick is enough.

---

### Post by sudodus on 2013-02-12
> **mastablasta said:**
> it means the burned DVD is not a bootable DVD.
 
i am curious, do you actually have multiple files and folders on the Xubuntu DVD? or just one .iso file of which you are checking the md5sum?
 
furthermore, if you have at least 2GB USB stick you can use that along with programme like linuxliveusb or unetbootin to create a bootable Linux USB stick in windows.
 
edit: sorry, 1 GB USB stick is enough.
+1
I'll add some details, that might help.

- You need to burn the CD/DVD in such a way, that the iso file will be imaged (or cloned) to the disk, not a simple copy. Since you can run a live session with Ubuntu 12.10, you can try ***Brasero*** to 'burn an image: burn an existing cd/dvd image to a disk'

- I have good experience with Unetbootin, to make a bootable USB drive. Also here, run a live session with Ubuntu 12.10, install Unetbootin
```
sudo apt-get install unetbootin
``` and run it! There is a straight-forward graphical user interface, that will help you.

But before that you need to check that the USB drive has a partition with the FAT32 file system, and that there is at least 1 GB free. You can check and do whatever necessary with ```
gksudo gparted
``` also from the live Ubuntu 12.10.

---

### Post by Curbie on 2013-02-12
> **mastablasta said:**
> i am curious, do you actually have multiple files and folders on the Xubuntu DVD? or just one .iso file of which you are checking the md5sum?
 
So far I have 6 separate DVDs and 3 CDs all with one .iso each that have been hash cheched, I'm downloading the i386 versions of Ubuntu and xUbuntu now just to see if it will boot in a hobbled 32 bit mode, if it does, I will probably play with loading single boot, but I haven't pondered what would mean for running an actual hobbled 32 bit system.

> **mastablasta said:**
> furthermore, if you have at least 2GB USB stick...I don't.

---

### Post by sudodus on 2013-02-12
> **Curbie said:**
> So far I have 6 separate DVDs and 3 CDs all with one .iso each that have been hash cheched, I'm downloading the i386 versions of Ubuntu and xUbuntu now just to see if it will boot in a hobbled 32 bit mode, if it does, I will probably play with loading single boot, but I haven't pondered what would mean for running an actual hobbled 32 bit system.

I don't.
I'll encourage you to boot into the working Ubuntu disk, and use Brasero according to my previous post.

'burn an image: burn an existing cd/dvd image to a disk'

---

### Post by Dodeca on 2013-02-12
To be clear in these instructions on burning an .iso image on a dvd.

Be sure to burn the dvd AS AN ISO IMAGE

and not just copy a .iso file to a blank dvd

---

### Post by Curbie on 2013-02-12
> **sudodus said:**
> I'll encourage you to boot into the working Ubuntu disk, and use Brasero according to my previous post.

'burn an image: burn an existing cd/dvd image to a disk'
A working Ubuntu disk or Ubuntu DVD, so far all I've been able to get up and running is Ubuntu 12.10 running from the DVD, does Brasero come with Ubuntu 12.10, and can I burn a DVD while Ubuntu is running from the same DVD drive?

---

### Post by sudodus on 2013-02-12
> **Curbie said:**
> A working Ubuntu disk or Ubuntu DVD, so far all I've been able to get up and running is Ubuntu 12.10 running from the DVD, does Brasero come with Ubuntu 12.10, and can I burn a DVD while Ubuntu is running from the same DVD drive?
It should work like this :-)

To be sure that it works, I booted with a Lubuntu 12.04 64-bit install CD. It is important to boot to RAM (otherwise it will not be happy, when you remove the system CD).

First you select language, then you click F6 (as shown at the bottom of the screen). Do not select any of the pop-up alternatives, remove those pressing the ***escape*** key. Now you have a line starting with 'Boot options' and ending with 'quiet splash --'. Add ***toram*** so that the end of the line will be (press the ***end*** button and ***arrow left*** to get the cursor in the correct position)

'quiet splash [COLOR="Red"]toram[/COLOR] --'

and then select

'Try Ubuntu without installing'

After installing, you need to install (temporarily) Brasero from a terminal window 

***ctrl + alt +t***

with the command
```
sudo apt-get install brasero
```

Then run brasero.

- Select 'Burn image'

- 'Click here to select a disk image' and browse to your iso file that you want to burn and select it.

- Replace the system disk for the running live system (Ubuntu 12.10) with an empty CD/DVD disk and wait until Brasero finds it.

- Click on properties and select the slowest possible burning speed.

- Click on 'Create image' to burn the CD (or DVD) disk

After burning, you might get an error message (probably because the system disk is absent). But the burning operation should have finished.

* At least it finished for me, and I had a new boot CD afterwards. I tested that all the files were good, and that I could boot from it.

Good luck :-)

---

### Post by Curbie on 2013-02-12
> **Dodeca said:**
> To be clear in these instructions on burning an .iso image on a dvd.
 
Be sure to burn the dvd AS AN ISO IMAGE

and not just copy a .iso file to a blank dvd
  Good catch! It had to be something common to both the Decmeber & current load attempts, and since the only one piece of hardware in common, the DVD, that really left just operator stupidity, THANKS! I had one DVD that boots, so I compared the file directories of it, to the ones that didn’t boot and there was a big difference, I guess I’m out-ed as the last person on earth that actually buy all copyrighted material instead of ripping it.
   
  I test booted xUbuntu and Ubuntu 12.04.1 and both booted just fine, and than loaded xUbuntu with no problems and I’ll do more twinking with that tomorrow, and load Ubuntu and twink with that too, but I probably try to mimic DuckHook’s exact configuration, to get the XP virtual machine setup properly.
   
  I apologize to all for my stupid mistakes and the needless post they generated and thank those who offered lots of honest help, hopefully setting up and running Virtual Machine will be less eventful.
   
  Should I start a new post when that time comes?

---

### Post by mastablasta on 2013-02-12
> **Curbie said:**
> So far I have 6 separate DVDs and 3 CDs all with one .iso each that have been hash cheched, .
 
as others said you are doing it wrong. there should be a bunch of files and folders on the disk.
 
here is a howto for widnows users: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
 
since you have XP scroll down the page a bit and there are instructions on how to do it with **infra recorder** (it's a nice, small free programme available for windows xp).
 
nero and other disk burners work in similar way. in *nero burning rom* for example you open image file and then burn it.
 
then it should work. once you boot you can verify the disk before installing or trying it out.

---

### Post by sudodus on 2013-02-12
> **Curbie said:**
> ...
   
  I test booted xUbuntu and Ubuntu 12.04.1 and both booted just fine, and than loaded xUbuntu with no problems and I&#8217;ll do more twinking with that tomorrow, and load Ubuntu and twink with that too, but I probably try to mimic DuckHook&#8217;s exact configuration, to get the XP virtual machine setup properly.
   
  I apologize to all for my stupid mistakes and the needless post they generated and thank those who offered lots of honest help, hopefully setting up and running Virtual Machine will be less eventful.
   
  Should I start a new post when that time comes?

I'm glad you can burn iso files to boot CD/DVD disks now :KS

No need to apologize, we have all been newbies, and we are still making mistakes (at least I am).

And yes, I think it is a good idea to start a new thread with an appropriate title for the virtual machine with Windows XP. Please make a final post here with a link to that thread to make it easy for us to find it :-)

---

### Post by Dodeca on 2013-02-12
> **Curbie said:**
> Good catch! It had to be something common to both the Decmeber & current load attempts, and since the only one piece of hardware in common, the DVD, that really left just operator stupidity, THANKS! I had one DVD that boots, so I compared the file directories of it, to the ones that didn&#8217;t boot and there was a big difference, I guess I&#8217;m out-ed as the last person on earth that actually buy all copyrighted material instead of ripping it.
   
  I test booted xUbuntu and Ubuntu 12.04.1 and both booted just fine, and than loaded xUbuntu with no problems and I&#8217;ll do more twinking with that tomorrow, and load Ubuntu and twink with that too, but I probably try to mimic DuckHook&#8217;s exact configuration, to get the XP virtual machine setup properly.
   
  I apologize to all for my stupid mistakes and the needless post they generated and thank those who offered lots of honest help, hopefully setting up and running Virtual Machine will be less eventful.
   
  Should I start a new post when that time comes?


Ya ... I would start a NEW post and **mark this one solved**.

below is a cut n paste on that !

**How to mark your thread as SOLVED**

 Find your  thread, and at the top of the page, click the "Thread Tools" Menu and  then "Mark this thread as Solved".

---

### Post by Curbie on 2013-02-12
Ok, so the next step is to test dual boot, I’ve read, and been have told that for a dual boot Win/xUbuntu install, Windows should be loaded first, so I made a drive image of my existing XP drive to the new test drive, so now I will try to load xUbuntu in a dual boot configuration and test dual boot. 
   
  xUbuntu seems pretty intuitive, but I want to play some more with setting up xUbuntu’s desktop and programs, so a functioning dual boot configuration will give me some "no pressure" time to play with xUbuntu.
   
  If that goes well, , and try to load Virtual Machine, and test VM with an Ubuntu load, I’ll probably test Virtual Machine on xUbuntu with a few other OSs before I burn another, hopefully my last XP license. 
   
  I all goes well up to that point, I’ll load this new test drive with a clean single boot configuration of xUbuntu and VM and burn a XP license for VM's final load, that’s the plan anyway, we’ll see what reality has to say about it?

---

### Post by Curbie on 2013-02-13
So far reality hasn't monkeyed with my plan, I mirrored my XP drive onto my new test drive because of my understanding that xUbuntu likes XP to be loaded first (step 01, check), then booted the system up with xUbuntu and did a xUbuntu/XP dual boot install which boots as expected for either xUbuntu or XP (step 02, check).
 

 Then I've spent the rest of the day playing with xUbuntu trying to set it up to be as intuitive (eye of the beholder) as possible, so I don't have to think about getting from here to there, I removed every program that came in preloaded with xUbuntu that I wasn't familiar with, my notion being that I don't want to focus on learning new program right now, I can do that in time, I want to focus on making a smooth transition from Windows to  xUbuntu.
 

 I only had one small hitch, I removed a program called Gnumeric using the Software Center because I'm not familiar with it, and unlike others that I removed using the  Software Center, the Application Menu still shows an icon for it Gnumeric and if I click on it, I get a message with words to the effect of “No such file or directory”.
 

 But so far that's it, there are still things that I wasn't able to accomplish like making xUbuntu desktop type larger and easier for me to read, but I haven't given up trying those setups yet. So far, things are looking good, I seriously doubt that if I can solve my transition issues, I'll even remember the effort I spent solving them.
 

 Posted from  xUbuntu.

---

### Post by sudodus on 2013-02-13
Gnumeric is a light-weight spreadsheet program, similar to Microsoft Excel. There is another and more powerful free alternative, Libre Office Calc. Many people use the Libre Office suite of programs, and if you do, you will probably not need Gnumeric and AbiWord. On the other hand, you need not remove them (at least not yet). It is enough to avoid starting them and focus on other software, that you want to test ;-)

A simple way to get larger fonts is to change the screen resolution, but I think you want full resolution. I'm not familiar enough with Xubuntu, to help you tweak its font size. Let us wait for someone who uses Xubuntu regularly to advice what to do.

---

### Post by Curbie on 2013-02-13
susdodus,

Thanks, I already loaded Libre Office Calc, Write, Base, and Math today, I still like the idea of cleaning off unused or unknown programs from the load, I think this is going to be a big enough endeavor as is without adding things now, that can always be added later.  
 

 Was just curious on why the Software Center removed both the programs and icons for the other programs I removed, and left just an unlinked icon for Gnumeric, oh well there is bound to be some advanced command to remove it, and I’ll run in to it in time.
 

 All in all, it was a productive day out of curiosity tested Write on one of may larger Word documentation files and it loaded and displayed fine, although Gnumeric still seem to associated to .XLS file extension so I couldn't really test Calc, apparently Sketchup is not available for xUbuntu, Skype is supposed to be but  I can't find it.
 

 I want to kill the network connection in XP to protect it, and I can do Sketchup from there, but since Skype in an Internet application, I want to run all Internet applications from  xUbuntu.

---

### Post by mastablasta on 2013-02-13
> **Curbie said:**
> susdodus,
 
Thanks, I already loaded Libre Office Calc, Write, Base, and Math today, I still like the idea of cleaning off unused or unknown programs from the load, I think this is going to be a big enough endeavor as is without adding things now, that can always be added later. 
.
not a good idea to do that because often programmes are integrated into desktop. not sure how much this is the case in xubuntu, but i went on removal rampage in Kubuntu and now i have a stupid popup message. it's not worth removing them as they don't take much space. the hwole installed system should tak ebaout 5 or 6GB. which by today's "standards" practically nothing. and that's with all the included programmes.
 
 > 
Was just curious on why the Software Center removed both the programs and icons for the other programs I removed, and left just an unlinked icon for Gnumeric, oh well there is bound to be some advanced command to remove it, and I’ll run in to it in time.
not sure. it could be a bug. Items in menu in xubuntu can be manually removed via GUI. no command line is needed. i don't have linxu at work so i can't tell you form the memorry how you do it. i just know it's a few click and it's gone. this often happens to me in winXP. 
 
 > 
All in all, it was a productive day out of curiosity tested Write on one of may larger Word documentation files and it loaded and displayed fine, although Gnumeric still seem to associated to .XLS file extension so I couldn't really test Calc, apparently Sketchup is not available for xUbuntu, Skype is supposed to be but I can't find it.

Libre office has a new version with improved compatibility with new office formats  .docx, .xlsx.
 
Skype should be in software center. you might need to enable other repositories in software sources. otherwise you can also donwload the .deb file from skype website and then double click it to install it. 
 
> 
I want to kill the network connection in XP to protect it, and I can do Sketchup from there, but since Skype in an Internet application, I want to run all Internet applications from xUbuntu. 
 
scetchup alternatives: [http://askubuntu.com/questions/50070/is-there-an-equivalent-to-google-sketchup](http://askubuntu.com/questions/50070/is-there-an-equivalent-to-google-sketchup)
 
scetchup 8 has gold status in wine: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=21290](http://appdb.winehq.org/objectManager.php?sClass=version&iId=21290)
 
as you can see it seems some things do not work. you can use a GUI front end for wine named Play on Linux to install it. another option is porbably virtual box or simply run it on windows XP when you need it.

---

### Post by sudodus on 2013-02-13
> **Curbie said:**
> 
 All in all, it was a productive day out of curiosity tested Write on one of may larger Word documentation files and it loaded and displayed fine, although Gnumeric still seem to associated to .XLS file extension so I couldn't really test Calc, apparently Sketchup is not available for xUbuntu, Skype is supposed to be but  I can't find it.
 
--

 I want to kill the network connection in XP to protect it, and I can do Sketchup from there, but since Skype in an Internet application, I want to run all Internet applications from  xUbuntu.

In your file browser (I guess you use Thunar, the default browser in Xubuntu) you right-click on a file that you want to open with another program. Select Properties and select the program you want to use instead of the present one. So for ods files and xls files, change it to open with LibreOffice Calc.

Skype is there in Linux, usually an older version than in Windows, but a fully functioning version with chat, voice, video and text messaging. I checked with Synaptic, and Skype is in 'precise/main (archive.canonical.com)', which should be activated by default.

It may seem a little more complicated to use Synaptic than the Software Centre, but you have better control using Synaptic, so I think you will prefer it at least after a while, when you know more about [X]Ubuntu.

***Edit***: Install programs from the repositories with ***Synaptic***, ***Software Centre*** or (command line) ```
sudo apt-get install packagename
``` when available. These versions are tested with Ubuntu. The only reason to download and install a deb package or download and compile a source code package (tarball) is that you need a bleeding edge new package or you need some program that is not in the repositories.

---

### Post by mastablasta on 2013-02-13
> **sudodus said:**
>  
Skype is there in Linux, usually an older version than in Windows, but a fully functioning version with chat, voice, video and text messaging. 
 
Skype for linux version numbers do not follow the windows version pattern. Which is why it mgith looks as they are older version but are actually not and are current. I think version in 12.04 should have most if not all the things windows version has. didn't notice the ads though... :D
 
 
also i think Skype is in cannonical partners (or at least it used to be) which has/had to be enabled.

---

### Post by sudodus on 2013-02-13
> **mastablasta said:**
>  
also i think Skype is in cannonical partners (or at least it used to be) which has/had to be enabled.

You are probably right about that. I was just checking with Synaptic, and it showed Skype, when I selected 'precise/main (archive.canonical.com)' in the left window, but that might be a bad way to check it.

Anyway, if Skype is not available, you select more repositories (until you find the one, where it is).

---

### Post by black veils on 2013-02-13
general font size:

***settings manager*** application >> ***appearance*** >> ***fonts*** tab >> ***default font***

---

### Post by Curbie on 2013-02-13
> **mastablasta said:**
> not a good idea to do that because often programmes are integrated into desktop. not sure how much this is the case in xubuntu, but i went on removal rampage in Kubuntu and now i have a stupid popup message. it's not worth removing them as they don't take much space. the hwole installed system should tak ebaout 5 or 6GB. which by today's "standards" practically nothing. and that's with all the included programmes.
 
 
not sure. it could be a bug. Items in menu in xubuntu can be manually removed via GUI. no command line is needed. i don't have linxu at work so i can't tell you form the memorry how you do it. i just know it's a few click and it's gone. this often happens to me in winXP. 
 
   	 	 	 	 	 	   Thanks, it seems that both the preloaded programs Gnumeric & Document Viewer don't remove properly, my concern here, besides just cosmetics, is file associations and the notion that programs loaded for evaluation may also have this removal issue and the system would get real cluttered over time if removal is an issue for some programs, sometimes.
 

 Now maybe this issue only affects programs preloaded with xUbuntu, maybe also random programs loaded with the Software Center, I don't know, and it's the “I don't know” that I can fix even if I can't fix the removal issue, and you're correct that Windows has these same issue, and I can use the same drive mirroring technique I use to keep Windows from bloating and leaving setup surprise turds with xUbuntu.
 

 The general notion for particular programs, mainly Excel, Sketchup, Skype, and maybe some others is collaboration, I ping lots of mathematical (Excel), visual (Sketchup), textual (Word), and verbal (Skype) concepts around for collaboration, these programs for collaboration have settled on for years by all, and it would be unfair of me to try to force collaborators to change their establish methods just because I've chosen to make a system change. Thus the need to maintain some Window functionality.
 

 I also post some results of this work and reality dictates I post in a manner that will benefit the greatest number of people, and for the time being, Windows is still on 80%+ of user systems, reality must be respected.
 

 The plan is, to run dual boot on a test drive and document my xUbuntu setup steps through XP setup as a virtual Machine on xUbuntu, and if I can setup xUbuntu and XP in way that meets my needs, then repeat the documented setup in a final and permanent single boot xUbuntu system.

---

### Post by Curbie on 2013-02-13
> **black veils said:**
> general font size:

***settings manager*** application >> ***appearance*** >> ***fonts*** tab >> ***default font***
Bingo, I missed that when I visited Settings Manager, my old eyes thank you!

---

### Post by sudodus on 2013-02-14
> **Curbie said:**
> ...
 The general notion for particular programs, mainly Excel, Sketchup, Skype, and maybe some others is collaboration, I ping lots of mathematical (Excel), visual (Sketchup), textual (Word), and verbal (Skype) concepts around for collaboration, these programs for collaboration have settled on for years by all, and it would be unfair of me to try to force collaborators to change their establish methods just because I've chosen to make a system change. Thus the need to maintain some Window functionality.

I think you will be happy with the linux version of ***Skype***, when you find it and install it. For many but not all purposes, ***Libre Office Calc and Writer*** can replace Microsoft ***Excel and Word***. I don't know ***Sketchup***, but if you describe what you do with it, someone might suggest a similar linux program.
> 
 I also post some results of this work and reality dictates I post in a manner that will benefit the greatest number of people, and for the time being, Windows is still on 80%+ of user systems, reality must be respected.
...
I suggest that you ***post results in the pdf format***, which is very easy, because it is built-in in Libre Office 'export to pdf'.

---

### Post by Curbie on 2013-02-14
> **sudodus said:**
> I think you will be happy with the linux version of ***Skype***, when you find it and install it. For many but not all purposes, ***Libre Office Calc and Writer*** can replace Microsoft ***Excel and Word***. I don't know ***Sketchup***, but if you describe what you do with it, someone might suggest a similar linux program.

I suggest that you ***post results in the pdf format***, which is very easy, because it is built-in in Libre Office 'export to pdf'.
Today I loaded and tested Skype and found no problems, then I spent the rest of the day testing xUbuntu and compiling my installation and configuration documentation I'll use to load the permanent install of xUbuntu if all goes well, and so far it has.
 

 As part of the xUbuntu testing, I played with Libre Office and for me anyway, “Write” handles my largest documentation Word files seamlessly with no significant differences, although “Calc” barfs on my more complex Excel spread-sheets, seeing that it's handling some of my libraries, I may be able to fix those issues in time.  Libre Office, Open Office(?) has come a long way since I last evaluated it,
 

 When I post documentation, I've always post in .pdf and I noted the .pdf feature in “Write”, when I post something that gets calculated however, I've always posted Excel spread-sheets (.xls) because it seems to be usable by the widest range a users, both older (.xls) and newer (.xlsx) Excel versions can read and use them, as well as Libre or Open Office user, I think, at least I haven't gotten any feedback about people not being able to read them.
 

 Sketchup is a free 3D CAD program, I also have “Art of Illusion”, but Sketchup has a very small learning curve and is pretty powerful based on its learning curve, real intuitive. The issue with XP running Skype, Sketchup, Word, and Excel is collaboration, which is real important to me.
 

 Tomorrow, I think I'll reload xUbuntu and XP in the dual boot, this current install was sort of to see if things could be configured the way I need them, the next install will be to better document how they were configured for use in setting up the permanent install.
 

 Thanks for your suggestions, I don't know anyone including me, that is real comfortable groping around in the dark.

---


---
title: "[SOLVED] Live cd to hdd, Never partitioned a disk before"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by Dutch70 on 2008-06-04
Wow, just wow! I'm lovin it!

 I have the Live cd and had it on the net(wireless), currently in vista, and I am really new to computers period.

 Anyway, I have got to get this on my hdd before I move from this seat! So I am going to go read some more about that, if anyone has any advice, tips anything to say at all, lol...I would really be greatful...Ha! actually already am! ...TIA

---

### Post by Duck2006 on 2008-06-04
This may help with installing.

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by rbc on 2008-06-04
If you are going to dual boot with Vista, check this:
[http://www.pronetworks.org/forum/about78184.html](http://www.pronetworks.org/forum/about78184.html)

---

### Post by housam on 2008-06-04
Read this guide in partitioning :[[COLOR="Red"]_http://www.psychocats.net/ubuntu/partitioning_[/COLOR]]("http://www.psychocats.net/ubuntu/partitioning")

---

### Post by Duck2006 on 2008-06-04
> **housam said:**
> Read this guide in partitioning :[[COLOR="Red"]_http://www.psychocats.net/ubuntu/partitioning_[/COLOR]]("http://www.psychocats.net/ubuntu/partitioning")

Thats will only be good for win 2000 and XP, win vista need to be partitioned from within it's self to work.

---

### Post by FlyingPenguin542 on 2008-06-04
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty]("http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty")

---

### Post by housam on 2008-06-04
> **Duck2006 said:**
> Thats will only be good for win 2000 and XP, win vista need to be partitioned from within it's self to work.
Thanks for the tip. I had never used vista . only xp under pressure.

---

### Post by Paqman on 2008-06-04
Btw, partitioning isn't compulsory to get Ubuntu installed. If you put your LiveCD in while running Windows you can use an installer called Wubi. It creates a virtual hard drive on your Windows partition and uses the Windows bootloader to select which OS you want at boot.

---

### Post by dimitri57 on 2008-06-04
Welcome to a fun new world.  I was where you are only a two weeks ago.  I followed the instructions here:

[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm")
along with advice from here:

[[COLOR=Red]_http://www.psychocats.net/ubuntu/partitioning_[/COLOR]]("http://www.psychocats.net/ubuntu/partitioning")

and it worked like a charm.

When I asked Vista (Home Premium SP1, 32-bit version) to shrink the partition, it only freed up about 25% of a 250gb drive.  From the Live CD, I used the "manual" option and was able to shrink the partition even further.  I also (per psychocats) created a separate /home partition.  After installing FS-Drive ([http://www.fs-driver.org](http://www.fs-driver.org)) in Vista, i am now also able to read and write files in my /ext3 partitions.  Hardy Heron (AMD64 version) also seems to handle files in my NTFS Vista partiion just fine too.

Good luck!

---

### Post by Dutch70 on 2008-06-04
Wow again, lol, I ended up having to leave. just got back and scrolled through all these post. Now thats alot of help. goin to check em out now....Thanks all!

edit: 

1. Do I need to delete my restore points or defrag my hdd before I begin the install? 

2. I hear 10-20 GB is plenty for linux, but I have about 300GB free, so I wouldnt mind using 100GB or so. Or is that totally    
   unnecessary ?

---

### Post by Dutch70 on 2008-06-04
Well I just shrank my hdd and it gave me 96GB of unallocated space, so I guess Im on my way. I decided against the wubi thing, thats still vista, is it not? 

one step at a time but before I take the next step I come here to check, so if anyone has anymore tips now that I know which direction I am going, that would be great. 
thanks!

---

### Post by housam on 2008-06-05
Just go for it. do partition that unallocated space to 3 partitions : 20 gb for the root partition ( / ) ext3 foemat , 2gb for the swap partition and the rest for the /home partition ext3 format.

---

### Post by Paqman on 2008-06-05
> **Dutch70 said:**
> 
1. Do I need to delete my restore points or defrag my hdd before I begin the install? 

Definitely defrag. You may have trouble shrinking your Windows partition if you don't.

Also, don't forget to back up your data. It's a pain, but worth doing, just in case.

> 
2. I hear 10-20 GB is plenty for linux, but I have about 300GB free, so I wouldnt mind using 100GB or so. Or is that totally    
   unnecessary ?

For the system 20GB is plenty. It depends where you want to store your data, really. Don't sweat too much about partition sizes, you can always tweak them later if you need to. If in doubt, just make them bigger than you think you'll need. After you've been using Ubuntu for a while you'll get a feel for how big things are.

---

### Post by Paqman on 2008-06-05
> **Dutch70 said:**
> I decided against the wubi thing, thats still vista, is it not? 

Nope, it's proper Ubuntu. It's just installed in a virtual partition instead of a physical one.

---

### Post by Dutch70 on 2008-06-05
Well, sure wish I would have used wubi now, at least I did back up my my stuff. 

I think I really goofed, The install went fine I believe, not sure how vista is yet, anyway, here is whats happening best I can tell you...

1. Terminal-"sudo lshw-C network" wont let me put in my password, it just flashes like it doesnt recognize the keyboard.

ifconfig- ESSID shows the name of my network, but when I go to network tools-Traceroute type in the name of my network, it cant find it.

dont know if that even matters now, because I rebooted with the disk and went to system recovery, as of now there is an icon of a cd on the ubuntu desktop and I dont have a clue where to go from here. (edit...ok I ejected the cd)

If anyone can help with that mess I wont throw in the vista recovery cd in. and start all over, but if I do, I'll mark this thread solved first. Thanks again!:popcorn:

---

### Post by chrisdugdale on 2008-06-05
Go for it. You should backup all your data before installing. Partitioning is about the riskiest operation there is, though it is automatic and seems to always work perfectly with the Ubuntu Live CD. If you made the disk from an iso file, use MD5SUM to check the iso file before you do anything. Make sure you run the cd check option (when you boot with the live cd) first too. Give it 100Gb or more I reckon, then you can handle lots of extras and data and videos etc. You can just insert the disk with Windows running and take the top option that comes. I installed by starting up with the cd in. When you done it all, make sure you follow the Ubuntu 8.04 Hardy Heron stuff for help. A lot of the hassles with earlier versions don't exist in Hardy. PS I've installed it lots of times on my pc, and on a few friends pc's too. They all love Ubuntu.

---

### Post by Dutch70 on 2008-06-05
Ok, now I can breathe, so judging by the post above, should I try to fix ubuntu?, if so, what kind of info should I try to get. and should I start a new thread with it?

I am on the pc I installed it on now and vista is fine, all went well on the install, it was letting me put is my password in the terminal prompt at first, then I think I typed a command wrong like sudo lswh instead of lshw. 

thanks

---

### Post by Paqman on 2008-06-05
> **Dutch70 said:**
> should I try to fix ubuntu?

What exactly is wrong with it? Are you having network problems?

---

### Post by Dutch70 on 2008-06-05
Hi chrisdugdale we must have been posting at the same time. too late for me to use wubi now. unless I use system restore to undo the partition since I did shrink the disk in vista before installing ubuntu. I really dont want to attempt that. though the longer I wait, less chance there is that it woould work. So close, yet so far.

network problems, although the icons show that I am connected. and manual configure is the only option it gives me from the icons. 
wont let me put my password in the terminal. just flashes

---

### Post by Dutch70 on 2008-06-05
Hey Paqman, lol...I'm really slow here I answered your question with an edit...this is hilarious

---

### Post by chrisdugdale on 2008-06-05
Been doodling elsewhere, sorry on this delay. Are you getting to log into the Ubuntu desktop ok? I'm not sure what you mean by 
"network problems, although the icons show that I am connected. and manual configure is the only option it gives me from the icons.
wont let me put my password in the terminal. just flashes"
does that mean you've done an install and now got a black screen asking you to login or what?

---

### Post by chrisdugdale on 2008-06-05
Once you have Ubuntu running, it can be used to sort out your partitions. Get gparted by searching for it in System>Administration>Synaptic Package Manager. But first I guess you're trying just to get the install to work? I doubt that a Vista restore will work but haven't tried it. Partition changes are pretty much permanent as far as I know. If you have checked your live cd etc, then the install seems to work pretty good. I don't have a network though.

---

### Post by Dutch70 on 2008-06-05
ok, I was answering paqman on the network problems. I got the post a little messed up there. sorry for the unnecessary confusion.
 

Yes, I have ubuntu installed and I can get to the desktop, but when I open a terminal to uhh, type in a command, the keyboard works, but if it is a "sudo" command, and prompts me for my password, when I hit the keys on my keyboard to type in the password. there is no response on screen. 

Icons- the two flashing PCs that show a red x if your not connected, if you click on them, it should give you options like connect to a network or create one. my network was showing up there but now it is not, just the option to configure manually, and if I bring that box up, it shows my network there with a checkmark, Also ESSID shows my network. 

keep in mind that I had ubuntu on the net yesterday, but that was before I put it on my hdd. Hope that helps some.

---

### Post by Samhain13 on 2008-06-05
> **Dutch70 said:**
> Yes, I have ubuntu installed and I can get to the desktop, but when I open a terminal to uhh, type in a command, the keyboard works, but if it is a "sudo" command, and prompts me for my password, when I hit the keys on my keyboard to type in the password. there is no response on screen. 

That's normal, the terminal really doesn't show you what you're typing if it's a super-user password (for security reasons)-- not even "***". You just have to trust your fingers and hit ENTER when you're done. If you typed in the wrong password, you'll be told "sorry, try again" and you just have to type in the right password next time.

---

### Post by chrisdugdale on 2008-06-05
The password goes in at the sudo prompt, but nothing shows onscreen. That's correct. once your password is entered just hit enter and whatever you're doing continues. So if you just type sudo, it just returns you to the prompt, but you're now root. anyway, now you should do the update stuff.
Running: 
sudo apt-get update 
takes a while, then do 
sudo apt-get upgrade 
and finally 
sudo apt-get dist-upgrade 
You may like to set System>Administration>Software Sources to a local mirror first
Then if you need to get multimedia etc, just check out:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
For desktop effects just use Synaptic to add the compiz-settings-manager to your System>Preferences menu
Look at Synaptic's Edit menu and go to mark packages by task to set up Samba (networks including M'soft) LAMP server etc

---

### Post by Dutch70 on 2008-06-05
ok , I'll give that a try, if it solves that issue, I'll be one step closer. 

 At one point the toubleshooter told me to go to system> administration> hardware information, and hardware info wasnt even an option anywhere.

wish I could do a recovery on the ubuntu install with the live cd, and get it back where it was before I got in there messing around.

I'm going to load ubuntu back on this pc and go post on another one. maybe that will help.

---

### Post by Dutch70 on 2008-06-05
I cant get on the net with it, its a wireless network, but I will refer to that post if and when I do get the internet connected.

---

### Post by Dutch70 on 2008-06-05
Password worked...of course...lol

how do you boot the kernel (to pci=noacpi)

we may be getting somewhere now, thats one of the things the troubleshooter is telling me to do. 

but the network manager icon should allow me to click on a network, but the only option it gives is manual configuration.
that is definitely something I done, it was showing my network at first,but it wasnt enabled. by the time I git it enabled I must have goofed something else up, that caused the network manager issue. 

reminder- hardware information isn't showing up under system>preferences>"hardware information" 

Its really nice to have people here to help, would of already reformatted vista if not....so thanks again!

---

### Post by Samhain13 on 2008-06-05
To get your hardware information in the terminal (wasn't able to find "hardware information" from the preferences menu also), type this:

```

sudo lshw

```

It will ask for your password, which we've settled already. And, it will show you something like this:

```

description: Desktop Computer
product: KM266A-8235
vendor: VIA Technologies, Inc.
width: 32 bits
capabilities: smbios-2.2 dmi-2.2 smp-1.4 smp
configuration: boot=normal chassis=desktop cpus=1

```

It's going to be a long list, depending on how much hardware you have. But that will be useful information to our friends who can help you with wireless networking. :)

---

### Post by Dutch70 on 2008-06-05
ok here it is, hope this is all you needed.

*network
description: wireless interface
physical id: l 
logical name: wlan0
serial: 00:le:e5:9e:ca:4b
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


The pc is a presario SR5350F if that helps any. 

just to clarify, what I meant by hardware information isnt there, Im talking about the selection. I thought I had clicked on it before and then got destracted and closed it, is it likely that I deleted it?

---

### Post by Samhain13 on 2008-06-05
> I thought I had clicked on it before and then got destracted and closed it, is it likely that I deleted it?

This happens to me too: finding it one time and not being able to find it at another time. I tried looking for it in my menus too but really wasn't able to find it. :confused:

Hence, the terminal "lshw" suggestion as knowing your wireless network hardware seems very important.

---

### Post by Dutch70 on 2008-06-05
well then maybe that is not such a big deal that it isnt there.

yes...lshw is what I used to get the info I posted.

---

### Post by Dutch70 on 2008-06-05
Actually, I have it on hdd now, and it is working great,thanks to everyone that posted here to help me. the responses were quick and thats always nice...This issue is solved. just need to get on the net with it now.

Thanks a lot to everyone that posted here!  ):P


                [SOLVED}

---


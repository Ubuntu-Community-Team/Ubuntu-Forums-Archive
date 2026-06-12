---
title: "Looking to Escape From Windows"
date: 2011-11-11
forum: New to Ubuntu
---

### Post by burntflowers on 2011-11-11
Hello,

Over the last year I have been toying around with the idea of taking all my computers at home and putting Linux on them. I have two of my own machines both running Windows 7 and a family member has a machine in Windows Vista. However earlier in the week one of my machines has began to run really slow taking well over five minutes to boot up, it is not a hardware issue I spent days testing and it seems the instant Windows is installed anything that is can and does happen. The family machine that is running Windows Vista is now blue screening once again I thought it was a hardware issue but after running several tests it was a corrupted driver in Windows I have tried to fix it but the problem still occurs. 

My objective or goal is to find an Linux Distribution that is simple to use but robust that I have still have control over my machines like a power user. I have had one friend recommend I install ClearOS to one of my machines as it sits in the corner of the room basically being used as a storage unit, I'm not sure that is what I am even looking for. I have also been suggested that I try Fedora 15. 

My concerns is my machines. The first of which is an AMD 1090t x6 Black Edition that is basically being used for storage however it is being cooled by a Corsair Hydrocool H70 unit that surprisingly keeps the CPU at insanely low temperatures, for that machine I typically like to keep an eye on the CPU/MB temperatures as its the only machine being cooled with this type of unit and for some bizarre reason I think that it will overheat and burn up in Linux. My second machine is an Intel I7-860 it has a stock hsf/fan and runs just fine this way I am not a gamer, if I do play games, I do that on my PS3. I use this machine for most of my web browsing, facebooking, movie watching, music listening computer. I play the occasional game on pogo or something sometimes I will convert a video file is it needs it, also this computer has RocketRAID card in it, I've check its compatible to run in Linux with a source driver build. And finally the 3rd machine hasn't been formatted since I put it together almost 4 years ago, its a family machine so if its not virused or spyware or malwared then I would be shocked, it simply needs a format and OS for web browsing and video watching.

These machines run okay in Windows, but with the constant updating and security threats, how quickly they can get infected with spyware, virus, malware, not counting all the 3rd party programs you need to run I simply want to move away from Windows so that I don't spend every few months formatting the machines or running virus/spyware scanners every few days. 

Would Ubuntu/Kubuntu be a good choice to use an OS? Or should I look at other Distributions?

---

### Post by matt_symes on 2011-11-11
Hi

I'm sure you've asked this question before. :P

Download some ISOs  and make a LiveUSB and have a play. See what you like. See how they perform on your PCs. You can use unetbootin to create them on Windows.

Ubuntu is a good distribution. 11.10 is the newest version and uses Unity. Use 10.04 if you like panels.
Fedora is a good distribution. Fedora 16 is the newest version and uses Gnome shell.
Mint is a good distribution. Another good, solid distribution.
Bodhi is a good distribution. Uses the enlightenment desktop. 

There are loads out there. Have a play and see what you and your family like.

Kind regards

---

### Post by Lars Noodén on 2011-11-11
You might want to use a CD RW so you can reuse the same disc after trying out the distro.  You might also want to take a look at Xubuntu.  It has more of a traditional, familiar interface.

---

### Post by jackyboy633 on 2011-11-11
Hey there!

Ubuntu/Kubuntu would be great choices for your Linux system! OpenSuSE, Mandriva and Mint are also good. As the previous poster said, you can use a spare USB stick and run UnetBootin to make yourself a LiveUSB so you can have a play around. 

Hope you enjoy the world of Linux! :popcorn:

Kind regards, Jackyboy633 :)

---

### Post by PPN13 on 2011-11-11
I have an AMD 1075t (no black edition 6x 3 Ghz) and it has balances around 53-52C under full load on all cores (a stress test) which is within safe temps. And its with just the stock fan from AMD retail box. So it should be fine. 

I also don't see why the i7 would overheat.

---

### Post by burntflowers on 2011-11-11
Yeah appears I have asked this question in the past, weird I didn't look to check and see these posts before. I completely forgot about the LiveCDs to toy around with. I have friends who are hardcore Linux guru's each of them give me hell about running Windows and for the last year have told me that if I switch to Linux I would actually spend more time doing other stuff aside from the constant virus scanning or at worst fixing a Windows installation. I've had quite a few people tell me that Fedora is the best distro, and some others say Ubuntu is good but I like to keep things simple. I've had my eye on Kubuntu for a while now. I recently tried Fedora 15 with GNOME 3.0 and on my monitor not sure what GNOME 3.0 was trying to do but it looks like a giant smart phone. 

I do appreciate the feedback so quickly. I have the weekend to get my machines switched over as I have waited as long as possible and patient with Windows and did months of research asked questions and wanted other peoples opinions and with the fast responses on the forums I am leaning towards a kubuntu installation.

@PPN13 I have had an issue in Fedora 13-14 releases for some reason on my AMD Box (to be honest I think its my imagination) that lm_sensors isn't reporting the right temps back to me, but at idle that computer in windows with 3 different programs shows these current temperatures. (See attached post) with lm_sensors it shows the CPU around 35-38c motheboard @ 40-41c and yes those are the values reported from 3 different programs. I thought I was going crazy. The I7 reports 34-37c idle, it has been known under heavy load to go as high as 54c with stock HSF. That was back when I played Final Fantasy 14 which that game required your system to have the most rediculous setups in the world. a SSD was a requirement.

Basically if you were me and you had these machines what would you do? I'm newbish when it comes to stuff like this Windows was shoved in my face since Win2000 but I hate the NTFS filesystem its horribly slow and with 2tb full harddrives defrags can take a LONG TIME. I've heard wonders about EXT3/4 not needing a defrag which would be a life saver and really anything I do turns out I can do in Linux, and if I have to run a Windows application I know that WINE supports some Windows apps.  

Also I do apologize for the multiple posts asking the same question, I should have check and thanks for not biting my head off. I'm just wanting to make the transition I just get worried that something bad will happen and I won't know how to fix it.

---

### Post by kurt18947 on 2011-11-11
There are options to get you away from the "giant smart phone" interface. Xubuntu is quite mature, it's ver. 4.8. Lubuntu is fairly young but seems to work pretty well and seems very good on older/less powerful machines.  These options keep the help and repos found with Ubuntu available to the  alternative desktops/window managers.  I'm running Ubuntu 11.10 but seldom use Unity.  My desktop of choice is Gnome-shell.  The first thing I do after installing is to add synaptic from the repos.  Then I added xfce4-desktop also from the repos. You could also add gnome-session-fallback if you want a gnome2-like experience.  There is a thread about tweaking gnome-session-fallback behave very much like gnome 2 by adding & removing packages.  

For me Gnome-shell and Xfce-desktop work.  I'm going to keep an eye on alternative Gnome-shell add-ons.  There are some interesting looking projects going on.

---

### Post by beew on 2011-11-11
Unlike others my suggestion would be to choose between 11.04 and 10.10. 10.04 is too old and 11.10 is too buggy and unstablle,--many things don't work if you look at the list of bugs that are not fixed yet.
LTS just means it hasn't been updated for 1.5 years, hardly something to celebrate or recommend.

---

### Post by waynefoutz on 2011-11-11
Burntflowers, there really isn't a one size fits all answer. People have different likes and dislikes, also what works well on one computer might not on another. Personally, I'd steer a new person like yourself over to Linux Mint. It's based on Ubuntu, only more polished and everything is configured to run properly out of the box. They even have a KDE edition if that is more to your liking, although the standard Gnome edition has been altered to make Windows users feel more at home. They just posted a screen shot of their new Gnome 3 edition coming out later this month, and it's beautiful as well. That would be the first place I'd send someone new like yourself.

---

### Post by waynefoutz on 2011-11-11
> **beew said:**
> Unlike others my suggestion would be to choose between 11.04 and 10.10. 10.04 is too old and 11.10 is too buggy and unstablle,--many things don't work if you look at the list of bugs that are not fixed yet.
LTS just means it hasn't been updated for 1.5 years, hardly something to celebrate or recommend.


I disagree. One of my biggest complaints about Ubuntu is the short lifespan of non LTS versions. I applaud Ubuntu's decision to lengthen the LTS support to 5 years. Some people just don't want to reinstall their OS every six months. I have several machines. All but one run LTS versions. The only one not is the one I'm on now, because I'm constantly tinkering with it. Your suggesting 11.04 over 10.04 makes no sense to me, since 10.04 has a longer life-span. 

Burntflowers, what we're talking about, is the Long Term releases have a 3 year shelf life (5 with the next one) while the interim releases are only supported for 18 months. !0.04 was the last LTS release, 12.04 will be the next one. If you follow my Linux Mint suggestion, Linux Mint 9 is built on top of Ubuntu 10.04. I have Mint KDE version 9 on my desktop at home btw, it's spectacular.

---

### Post by beew on 2011-11-11
> **waynefoutz said:**
> Personally, I'd steer a new person like yourself over to Linux Mint. It's based on Ubuntu, only more polished and everything is configured to run properly out of the box. They even have a KDE edition if that is more to your liking, although the standard Gnome edition has been altered to make Windows users feel more at home.

Why would someone who says he wants to "escape from Windows"  find it desirable to " feel "more at home" with something that tries to look like Windows??:P

---

### Post by beew on 2011-11-11
> **waynefoutz said:**
> I disagree. One of my biggest complaints about Ubuntu is the short lifespan of non LTS versions. I applaud Ubuntu's decision to lengthen the LTS support to 5 years. Some people just don't want to reinstall their OS every six months. .

No one says you have to reinstall your OS every 6 months, non LTS are supported for 18 months. 

Canonical churns out a buggy release every 6 months that would take another month or two for the bugs to clean up, it would be insane to tie your upgrade/update schedule to Ubuntu's release cycle That's why I don't understand why the rush to "upgrade" to 11.10 while 11.04 has just become stable and solid about 2 months ago after waves of bug fixes and updates whereas 11.10 is anything but stable and solid at this point. I find it best to be 1/2 to 1 version behind (ie, hold off updating for 3 to 6 months but I may also skip 11.10 all together)

---

### Post by burntflowers on 2011-11-11
To me personally it can "look" like Windows as much as it wants without it actually being the Windows OS itself. As long as I can get Linux on it, get my drives converted over to EXT3/4 and not have to reboot the machines constantly due to a driver update or something related to a Windows patch or god forbid when something happens to the machine and the Windows Network goes down and the only way to get it back up for the other machines to see it on the network is to reboot. I can't tell you the number of times I've had to shutdown everything, reboot, then open everything back up. 

I also understand that its not always a suitable idea to run the latest release of a distro of linux because of bugs, stability. I found this out when I did an install of Fedora 15 a week after it was released and that was in itself not fun. I appreciate all the replies and I didn't want anyone to get into an argument for now I will try the live cd's. See which of them I like and go from there. Screen shots are nice, but I really need to use, look and feel and see which I am comfortable with and then go from there. I do hope networking is much more simple in Linux. Windows 7 and "Homegroups" is downright terrible imho.

---

### Post by donkyhotay on 2011-11-11
Don't forget that liveCD's will run really slow compared to a regular install. They'll give you a good idea on how the standard interface of a distro will be not how it will perform. For that you'll need to actually install it.

---

### Post by Ms. Daisy on 2011-11-11
Hello burntflowers, I'm a new user of Ubuntu.  IMO there is a fairly steep learning curve moving from Windows to any Linux distribution that's going to eat up a lot of your time.  If you choose to reformat all three of your machines with Linux right now, then surely some sort of bad things will happen and you won't know how to fix them.  For that reason, I would HIGHLY recommend that you install a virtual box or run a live CD (as recommended by previous posters), or at the most install Linux on a partition of ONE of your machines & play around with it.  Give yourself time to learn how it works. Read an OS manual, play with the terminal, check out the software options. Be prepared to reinstall it when you type something stupid into terminal and totally break it (which you will if you're really testing stuff out). Only then would I recommend that you make the complete transition from Windows if you choose that route.  This advice comes from my own personal experience and frustrations.  Good luck!

---

### Post by pqwoerituytrueiwoq on 2011-11-11
if you like the layout of the windows taskbar/start menu i think you will be happy with linux mint as it is out of the box
i think i will switch my laptop to mint but i am happy with 10.04 on my desktop (probably keep it till eol in 2013)
you will probably be prompted to install a gpu driver (quick and easy in a couple clicks) at 1st login since you do not have a intel gpu (i know your cpu is a amd hex core and have not seen a amd board with a intel gpu on it)

unetbootin can make testing a linx distro easy, i suggest dual booting one of your machines for a week so you can have any needed drivers installed

btw wired network will work as soon as it is booted wireless requires confirmation at the least to connect

---

### Post by burntflowers on 2011-11-11
@Ms. Daisy : Yes I am doing one machine for right now, I went ahead did a livecd of kubuntu and did an install since I needed a machine to toy around with it. I have been messing around with it and I have to say this I like they layout of the GUI and I think this will fit what I need and I intend to hold off on my other machines until I get the handle of it.

---

### Post by djsephiroth on 2011-11-11
I'd suggest a flavor of Ubuntu for your first Linux experience.

Xubuntu, Lubuntu, or perhaps Mint. 

If you run the distro from a live USB instead of a live CD, you can have a much smoother experience since a USB drive can move data at about ten times the speed of a CD.

I carry around a decently sized USB drive created with YUMI. It contains several distros that can be booted to a live environment. Great for trying out several distros, or for keeping a set of tools on one drive. Never know when you might need to boot into BackTrack, UBCD, Puppy, or some other specialized distro. Very handy for rescuing broken systems.

---

### Post by oldfred on 2011-11-11
I always suggest small system partitions for both Windows & Linux with data in other partitions, either a separate /home for a newer user to make a reinstall easier or separate /data or /shared (NTFS) if dual booting with Windows. With my 640GB drive I have several Ubuntu / (root) partitions and a few other installs. Data is linked into all, and even Firefox & Thunderbird profiles are in the shared so Windows & Linux have the same mail & links.

If you have larger drives, you can easily install several full systems to test. But as others have said you do have a learning curve to change. I converted while in XP to OpenOffice, Firefox & Thunderbird, so I had few applications to learn new ways, but learning the details of Linux takes a while.  Part of the problem with Linux is that there are so many choices and each of use like different things. Good luck.:)

---

### Post by beew on 2011-11-11
Try out Unity, you may just like it. I think some users are imposing their own dislike of Unity by pushing 10.04, Xubuntu, Lubuntu and Mint.

Since it is going to be  new experience, you may as well come with an open mind. Well unless you have old or weak hardware (say a netbook) then Lubuntu is definitely the way to go. But if you have a reasonably up to date (say not older than 6 years) and robust system I would definitely recommend a full feature OS instead.

As others say, live CD is slow, live usb is better, but still very slow. If you have a spare harddrive the ideal way to test would be to make a full install into the external drive and boot from it. It gives you the real performance (except boot time may be a bit slow, depending mainly on the BIOS) Once you are comfortable you can just wipe Windows off your drive,--my understanding is that you want to "escape from Windows", hence dual booting is not something that you would look forward to.

---

### Post by kurt18947 on 2011-11-11
> **beew said:**
> Try out Unity, you may just like it. I think some users are imposing their own dislike of Unity by pushing 10.04, Xubuntu, Lubuntu and Mint.

Since it is going to be  new experience, you may as well come with an open mind. Well unless you have old or weak hardware (say a netbook) then Lubuntu is definitely the way to go. But if you have a reasonably up to date (say not older than 6 years) and robust system I would definitely recommend a full feature OS instead.

As others say, live CD is slow, live usb is better, but still very slow. If you have a spare harddrive the ideal way to test would be to make a full install into the external drive and boot from it. It gives you the real performance (except boot time may be a bit slow, depending mainly on the BIOS) **Once you are comfortable you can just wipe Windows off your drive,--my understanding is that you want to "escape from Windows", hence dual booting is not something that you would look forward to**.

All good advice but keeping a small clean basic Windows install can be useful.  There are hardware related needs -- such things as BIOS updates,  firmware & database updates for  GPSs, cameras, printers and such that are very easy using Windows and difficult or impossible using Linux.  It's a shame but that's reality today, I'm afraid.

---

### Post by mastablasta on 2011-11-11
> **burntflowers said:**
> To me personally it can "look" like Windows as much as it wants without it actually being the Windows OS itself. As long as I can get Linux on it, get my drives converted over to EXT3/4 and not have to reboot the machines constantly due to a driver update or something related to a Windows patch or god forbid when something happens to the machine and the Windows Network goes down and the only way to get it back up for the other machines to see it on the network is to reboot. I can't tell you the number of times I've had to shutdown everything, reboot, then open everything back up. 


Just hope you know that converting them to ext4 will need a reformat od the drive (i.e. deletes all data).

> 
I also understand that its not always a suitable idea to run the latest release of a distro of linux because of bugs, stability. I found this out when I did an install of Fedora 15 a week after it was released and that was in itself not fun. I appreciate all the replies and I didn't want anyone to get into an argument for now I will try the live cd's. See which of them I like and go from there. Screen shots are nice, but I really need to use, look and feel and see which I am comfortable with and then go from there. I do hope networking is much more simple in Linux. Windows 7 and "Homegroups" is downright terrible imho.Fedora is known for their support for new hardware, they have new programmes etc. but they are not the most stable one out there. they are development/community version of Red Hat Enterprize Linux (which needs to be payed i believe for and is usually deployed to large businesses and organisaitons)..

if you want stability then you would have to go debian, however debian stabel has a bit older programmes (i guess new ones can be installed manually) and is not as user friendly (a lot of setup is required after install due to their Opensource only policy) as for example Ubuntu. But there are distributions that converted it a bit and made it more firendly such as Linux Mint debian edition (can be tied to debian stable) and Chrunchbang Linux.

I went with Kubuntu and so far i am quite pleased. you can go with 11.10 version and then upgrade to LTS when it comes out in April (only you upgrade about 5 or 6 months after it comes out to get a more stable variant). then you can stay with that LTS for next 5 years.

i have only 2 issues with Kubuntu - my audio CD don't play (only in command line). They can be ripped to MP3 and then played though.

Second issue is that sometimes sound doesn't always work when it wakes up form hibernaiton. but this is my motherboard specific issue. using Intel HD audio (realtek) - bad support still... could be sovled by byuing linux supported sound card.

---

### Post by beew on 2011-11-11
Why is this binary thinking? Either the latest buggy release (11.10) or outdated LTS (10.04) How about 11.04? It generally takes a month or more for a new release to become stable and bugs to be fixed, with 11.10 it is going to take a lot longer if you look at the number of serious bugs in the bug trackers, many are marked "high" in urgency but not even assigned! (not unexpected because of change to gnome3)   Now just when one release has matured to become a great joy to use everyone abandones it and rush to the next beta, so basically your computer is a constant beta testing box, I think that is crazy.

---

### Post by waynefoutz on 2011-11-12
> **beew said:**
> Try out Unity, you may just like it. I think some users are imposing their own dislike of Unity by pushing 10.04, Xubuntu, Lubuntu and Mint.



The original poster sad he did not like the "smartphone" look of gnome-shell in Fedora 15, so I assume that would rule out Unity as well. Personally, I use Unity overall I like it, but there are things I would change if it was in my power to do so. I suggested Mint because I think it's the closest thing the op said he was looking for. I'm sorry, but for new users, Mint is a better choice hands down.

---

### Post by waynefoutz on 2011-11-12
> **beew said:**
> Why is this binary thinking? Either the latest buggy release (11.10) or outdated LTS (10.04) How about 11.04? It generally takes a month or more for a new release to become stable and bugs to be fixed, with 11.10 it is going to take a lot longer if you look at the number of serious bugs in the bug trackers, many are marked "high" in urgency but not even assigned! (not unexpected because of change to gnome3)   Now just when one release has matured to become a great joy to use everyone abandones it and rush to the next beta, so basically your computer is a constant beta testing box, I think that is crazy.

11.10 is running pretty stable for me. My only gripe is it's on top of Gnome3 instead of Gnome2 like 11.04 was, and Gnome3 isn't quite finished yet, in my opinion. My problem with 11.04 is that it has less than a year left.

---


---
title: "Dreamlinux 3.0 Final Edition RELEASED!"
date: 2008-03-30
forum: Other OS Talk
---

### Post by handy on 2008-03-30
[I]Dreamlinux Desktop Edition 3.0 is a complete redesign of the distro, now supporting a
totally independent architecture named Flexiboost, based on overlaid modules.

The latter feature allows the co-existence of two (or more) separate window managers
(currently Gnome and Xfce), sharing the same customized appearance. Both working
environment share all the applications available.

What our community can expect from this final DL3? [nelsongs - Dreamlinux Developer]
1 - Stability. We have, as I have already mentioned, frozen our working packages to
the RC1 ones, with some minor improvements and additions.

2 - Efficiency. Dreamlinux continues to be reported as one of the most efficient
Linux distros, in terms of speed and memory consumption. I think no other distro
delivers a Gnome environment so clean and with a low comsumption rate. Not to mention
Xfce...

3 - Hardware detection (mostly talking about video cards detection): I think I
reached a good balance in this area. With normal video cards I guess nobody will
experience problems. Those who use video cards made in Mars maybe will continue
experiencing flaws. Let's see. Anyway, this is an area in which I am putting a lot of
energy and I can guarantee to you that it will continue evolving and improving fast.
And remember I am talking about scripts and applications made totally in-house.

4 - Dreamlinux Installer. Now we are addressing (I think) Greeks and Trojans. I have
improved DLI in terms of usability and robustness. Now nobody can (I hope) complain
that the "way to select the mounting points, filesystems and if it is to be
formated or not" is difficult to grab or understand. I have also included the
feature of installing to an entire disk, withouth the need to repartition, etc. This,
I think, will please the newbies and even some commercial oriented guys. Of course, I
am using the principle of least effort here. Nothing is asked to the user, other than
providing his/her username and password, root password and box name, and an optional
title to the new box in Grub.  DLI is creating only two partitions in the HDD: one
1GB swap partition and the rest of the disk dedicated to the root partition. And I am
using ext3 to this root partition. I know it is not the most efficient one (actually
it is extremely inneficient in formating and setting up the journal) but it proved to
be more reliable
 than reiserfs. Still regarding this issue, I did not have time to try out the other
filesystems (xfs and jfs) in this "Entire Disk Install" scheme. What I can
(and possibly will) do is to leave this filesystem type partition to reside inside
dli.yaml (DLI configuration file) so, if anyone decides to try other filesystem for
this specific task, it is just a matter of editing that file and change ext3 to jfs
or whatever. I do not recommend xfs as root partition due to a known flaw on the
current Grub incarnation regarding this. Unfortunately I did not have the time to
test Grub2 as you suggested.This will be addressed in the first upgarde to DL3.
Myself, I am using jfs as my root filesystem and xfs as my home one.
Another interesting feature I have improved in DLI is to make it possible to install
Dreamlinux, regularly or as an "Entire Disk Installation", to a USB HDD. So
now, you can carry Dreamlinux in your pocket, with these small-sized USB HDD. The sad
note in this process was that I made a confusion and reformated my working USB HDD
(250 GB). So, all the stuff I have collected and developed, since I started the
Dreamlinux Project back to 2005, is gone!
I have tested all the possibilities we have been discussing in the Forum regarding
installations schemes: One partition only, /home in separated partition, Grub
installed to mbr, Grub installed to root, etc..  All of them, except for xfs as the
root partition (due to that Grub flaw) worked nicely and neatly.

5 - Dreamlinux Pen Installer - This is one long-awaited addition of ours. I have
using these two former days only for writing, test, rewrite, retest and be happy with
the final results. Now we have (I confidently affirm) the best Pen-Drive (USB STICK,
USB flash-driven, whatever you name it) installed distro!
I was intending to add this feature to DLI, but decided (yesterday) to have it as a
separate application due to its flexibility and features. Simply put, Dreamlinux
Community has now a tool to install Dreamlinux iso image to a pen-drive, and does not
matter if running Dreamlinux Live or HDD installed. Together with MkDistro
LiveRemaster (also appearing refurbished to this new DL3) you can even customize you
Distro and install it in a pen-drive in only one shot.
What really amazed me in its development (made from scratch) is that I could end up
with a system in which you can change the way you like it. Let's say that we develop
a new kernel module and make it available to our community. You simply download this
new kernel module and replace it (yes, simply replace it!) in your pen-drive
installed Dreamlinux! Actually, you can replace anything (I mean it, anything!) in
this pen installed Dreamlinux (I am naming its default label to Dream_on_A_Pen)
without the need to reinstall! I think everyone will love this new feature. And it is
Dreamlinux exclusive. To my knowledge there's nothing similar out there. You'll see
for yourself.

6 - One thing I am very dissapointed is not to have had the time to work on my new
kernel module (2.6.24 series). BTW, this was in that USB HDD drive I formatted! So, I
think that annoyance reported by piotrpiano and others in that specific thread is not
yet being addressed with the official release. Actually I am not sure exactly where
the problem resides because I have never experienced it. It seems to be something
specific to some kind of hardware, that's why I suspect it is inside the kernel
configuration I did. But, as I told you above, this will be our first module to be
launched as an upgrade. I have to finish all the current work I am doing today, by
mid-night at most, in order to send them to Andre Felipe, who will be closing the iso
and uploading to Linorg and possibly to my own website.

7 - There is also some new works regarding graphics design and usability made by
Andre Felipe. Some of them is a duplication of what you have done to the awn themes,
etc...So, Dreamlinux is starting to become more and more a real Community distro, as
I wish. We hope to select some of our forum members to be more involved in DL
development. I remember having read one post of someone that wishes to be part of our
Development Team. I will try to locate this post again and invite the guy to work
with me directly and assess if he can join us in the Development Team (currently only
myself, Andre Felipe and some Ruud Kuin's contributions).

***Download it now***
You can download it via torrent from here.

***_[http://www.mininova.org/tor/1282584](http://www.mininova.org/tor/1282584)_***

To unsubscribe from these announcements, login to the forum and uncheck "Receive
forum announcements and important notifications by email." in your profile.

You can view the full announcement by following this link:

***_[http://dreamlinuxforums.org/index.php?topic=1142.0](http://dreamlinuxforums.org/index.php?topic=1142.0)_***

Regards,
The Dreamlinux Forum Team.
[/I]

---

### Post by wolfen69 on 2008-03-31
sounds really great! i was pretty impressed with the last release. this one sounds even better. cant wait to try it. i'll be seeding this one for a while.

---

### Post by Takmadeus on 2008-03-31
Great news!!!! this is my dostro of choice on those PCs allergic to ubuntu and its derivatives ;)

---

### Post by swoll1980 on 2008-03-31
I tried the rc for this one and had a ton of problems with gnome intergration of the awn, and other apps  it failed to detect my nvidia 6200 I couldn't get the drivers to install from nvidia.com in safe mode from the terminal I forget now what the problem was, and there is no helper script like envy avalable so  I decided to go ahead with my intel 845 card but couldn't get compiz fusion to work. I ran into some more problems as well I tried to google
for solutions but couldn't find any and there isn't a communuity for dream like there is for ubuntu. It seems like a nice distro I can't live without compiz though maybe the problems I had got worked out but I don't know if these were known issues or not. Like all distros though it might work perfect for some one and if thats the case i'm sure they will enjoy it cause those guys did a great job with the way it looks and feels.

---

### Post by handy on 2008-03-31
> **swoll1980 said:**
> I tried the rc for this one and had a ton of problems with gnome intergration of the awn, and other apps  it failed to detect my nvidia 6200 I couldn't get the drivers to install from nvidia.com in safe mode from the terminal I forget now what the problem was, and there is no helper script like envy avalable so  I decided to go ahead with my intel 845 card but couldn't get compiz fusion to work. I ran into some more problems as well I tried to google
for solutions but couldn't find any and there isn't a communuity for dream like there is for ubuntu. It seems like a nice distro I can't live without compiz though maybe the problems I had got worked out but I don't know if these were known issues or not. Like all distros though it might work perfect for some one and if thats the case i'm sure they will enjoy it cause you guys did a great job with the way it looks and feels.

Yes RC.1 gave me hell too.  I'll check out the final sometime though, there pen installer sounds interesting too.

I had a lot of trouble with my AGP nVidia 7950GT.  It has only ever been handled right in the Sabayon Linux versions from 3.4e on.

I have just a few minutes ago finally got the nVidia proprietary drivers to work in Arch, after at least 12 hours of trying, 'cause I really like Arch.  The answer for my card was as simple as putting the following line in my xorg.conf under Section Device:

***Option "NvAgp" "0"***

Boy did that make me happy.

Now I will try the same with my Gutsy Ubuntu, it may very well be the same problem that has caused me trouble with the proprietary drivers on so many distro's.  It might not be too, but I have my fingers crossed. :-D

---

### Post by swoll1980 on 2008-03-31
good luck!

---

### Post by smoker on 2008-03-31
think i'll put this at the top of my 'next distro to try' list!

---

### Post by r76 on 2008-03-31
> **handy said:**
> ***Download it now***
You can download it via torrent from here.

***_[http://www.mininova.org/tor/1282584](http://www.mininova.org/tor/1282584)_***

The torrent needs a little help.  I started downloading 5 hours ago and only got 5.6% so far, then I downloaded the whole thing in a few minutes from a mirror (av speed 1858.7KB/s).

How can I help seed it using the fully downloaded version?  I'm using utorrent on XP if anyone has any ideas...

EDIT:  I think I did this right - I found a folder on my computer I didn't create called Dreamlinux 3.0, in it there was an .iso file with the same name as the one I downloaded.  I deleted the torrent then copied my .iso over the top, then re-downloaded the torrent file.  Now it's uploading steadily ~800-1000kB/s.  I think that's a good sign?  Please let me know, I don't want to have screwed it up for other people!

---

### Post by ComputerHermit on 2008-03-31
I downloaded it a few days ago and I put it on a a hard drive I had laying around I used it off the live CD and I thought it was not user friendly to install I had problems 
installing it I pardoned the hard drive and I still had problems with it I got to take more time with it

---

### Post by Twitch6000 on 2008-03-31
This seems to be worth a try :o.Does it have a livecd or just standard?

---

### Post by r76 on 2008-03-31
It's liveCD, installable like Ubuntu - and can also easily be remastered to a custom distro.  I'm interested in trying the new USB install...

---

### Post by blonder on 2008-03-31
It is a great Distro but i miss Gnome 2.22

---

### Post by wolfen69 on 2008-03-31
im using the live cd right now, and have to say it's pretty damn good. impressed so far. very fast too.

---

### Post by Twitch6000 on 2008-03-31
There aren't many streamers right now :(.I am only getting about 20 kb per second :(.
Edit:Nevermind I found a direct download.

---

### Post by swoll1980 on 2008-03-31
> **ComputerHermit said:**
> I downloaded it a few days ago and I put it on a a hard drive I had laying around I used it off the live CD and I thought it was not user friendly to install I had problems 
installing it I pardoned the hard drive and I still had problems with it I got to take more time with it

installation is a little confusing when they were developing this they forgot that we didn't know what we were supposed to do. the installation is easier  than other distros if you know what you are doing but there are no instructions so you have to figure it out on your own

---

### Post by Twitch6000 on 2008-03-31
Ok I am using the live cd on Vbox and its just wow.I can say this thing will give the other distros a run for uhhh... their community?

---

### Post by wolfen69 on 2008-03-31
> **Twitch6000 said:**
> Ok I am using the live cd on Vbox and its just wow.I can say this thing will give the other distros a run for uhhh... their community?

i agree. it has a really nice assortment of apps and features. its visuals alone will appeal to alot of people. i could see myself using this on a semi-regular basis. at least it's debian based.

---

### Post by handy on 2008-03-31
> **Twitch6000 said:**
> There aren't many streamers right now :(.I am only getting about 20 kb per second :(.
Edit:Nevermind I found a direct download.

Could you post your direct download link?

There may be others who need to use it from time to time.

---

### Post by r76 on 2008-03-31
Hmmm. In my hands...
[LIST]
[*]Much longer boot time than other recent live distros including Hardy beta. (but runs fast)
[*]Network manager can see but not connect to my wireless
[*]Even if it could the signal strength indicator is unclear (blue on blue?)
[*]By default everything is a bit smaller than on Ubuntu (fonts, taskbar), difficult to see on high dpi monitor - I'm sure there are options to change them though.
[*]System beep on shutdown :roll:
[*]Haven't checked packages etc yet (it's difficult to do much until I get the wireless working)[/LIST]
It looks smart, although I'm not a fan of the Mac look.  If I can get the wireless working I might try an install. :)

I've mostly tried the Gnome version.  I can't find much difference from the XFCE, even in speed.  Anyone else have any views?  I don't know how to decide.

---

### Post by Twitch6000 on 2008-04-01
> **handy said:**
> Could you post your direct download link?

There may be others who need to use it from time to time.

ok here you go :).
[http://www.dreamlinux.com.br/download.html](http://www.dreamlinux.com.br/download.html)

There are 5 links on it the third is the direct link.

---

### Post by |2A|N on 2008-04-01
Cool I am going to try it out also :guitar:

---

### Post by handy on 2008-04-01
> **Twitch6000 said:**
> ok here you go :).
[http://www.dreamlinux.com.br/download.html](http://www.dreamlinux.com.br/download.html)

There are 5 links on it the third is the direct link.

Thanks Twitch, its bound to help someone. :-)

---

### Post by shuttleworthwannabe on 2008-04-01
Now look at this distro's presentation: glossy icons with all the bling-bling...and backed up by Debian; so then tell me why one would just not try this ditro out? I am all for presentation, but also inside the hood, the distro must deliver. From what I am reading this version is a real improvement from its previous versions. I used v1.x sometime ago, but could not get my ATI card to work properly.

hmmm..if only Ubuntu devs could get the glossy icons and presentation right...then ubuntu would be magic made in disro-heaven!

I will give this one a try...downloading

---

### Post by sujoy on 2008-04-01
ya ubuntu could do with some change in looks

---

### Post by Twitch6000 on 2008-04-01
> **handy said:**
> Thanks Twitch, its bound to help someone. :-)

Anytime I can help I will :).

---

### Post by smoker on 2008-04-01
i ran the live cd, and liked the look of it so much i installed it on a second machine. this is a great distro, playing around with the gnome desktop at the moment. it is pretty slow to boot, but a delight to use, and once the desktop is up and running it is quite sprightly.

would recommend anyone interested should give it a try. if hardy turns out to be a disappointment later this month, dream may make it onto my main machine.

---

### Post by shuttleworthwannabe on 2008-04-02
my download bombed out on me; isp not like me to download so much linux...
anyway, i am looking for feedback on ati cards, how does DL3.0 handle ATI cards and is it easy to install the damn drivers and make the screen resoultion work? just curious before I try downloading again.
S

---

### Post by handy on 2008-04-02
> **shuttleworthwannabe said:**
> my download bombed out on me; isp not like me to download so much linux...
anyway, i am looking for feedback on ati cards, how does DL3.0 handle ATI cards and is it easy to install the damn drivers and make the screen resoultion work? just curious before I try downloading again.
S

I'd suggest that you ask on the DL forum, the dev's will appreciate your feedback as well.

---

### Post by bartos on 2008-04-05
Hi All

Dream linux is nice
I can't seem to set my resolution over 1024x768.  My Screen resolution changer in gnome panel has 4 options but when i check my xorg.conf file I only have one. I have the Nvidia X server applet but can't change resolutions in it either.

I just would like to know where I can edit xorg to change my resolution higher.

Thank you
Bartos

---

### Post by CouchMaster on 2008-04-06
I've been using the new DreamLinux for 3 days now; it's a good solid distro...
I would rate it on par with SimplyMepis, and just below PCLinux.
And, in my opinion Ubuntu 7.10 is a far better distro than anything else out there.

---

### Post by ErusGuleilmus on 2008-04-10
I just tried this distro.... I have been VERY Impressed with the XFCE Live CD session that I am typing this in. As soon as I am done with my current project, I think that I may install this on its own partition.

---

### Post by Wobedraggled on 2008-04-11
I installed this on a spare machine, took 2 tries to get it to install.

Handbrake installs but doesn't run(yes I did mono first) , and Firefox installed but did not run.


Interface is nice, and it seems to run at a nice speed. I'll let it sit for a bit.

---

### Post by trmiv on 2008-04-11
Trying the live cd, it looks really nice.  I'm not sure I'm willing to install it on my main computer though.

---

### Post by kamaboko on 2008-04-11
> **trmiv said:**
> Trying the live cd, it looks really nice.  I'm not sure I'm willing to install it on my main computer though.

Come on...do it.  Risk that perfect setup for something new.

---

### Post by zmjjmz on 2008-04-13
I have 2.2.MMGL edition on an old (1999) Thinkpad with a 700MHz P3, 384MB RAM, and 12GB HDD.  Did anyone feel that it was significantly heavier than 2.2MMGL? (Which runs fine on said computer).

---

### Post by MONODA on 2008-04-15
*says in shrill voice* ohhh how i have waited for this day to come. but seriously, I have been waiting for this and cant wait to install it! it sounds great for noobs!

---

### Post by iaculallad on 2008-04-17
Im just wondering if ntfs-config works well with DL3.0? I tested and installed its LiveCD (downloaded and successfully installed ntfs-config too) but it seems that it does not function well with DL3.0. Application does not start.

---


---
title: "Dual-boot, wubi or VM???"
date: 2012-06-28
forum: New to Ubuntu
---

### Post by Sarys on 2012-06-28
Hello! I was just wondering how should I install my Ubuntu? Like what's the plus side of dual-booting, wubi or VM and what are the minus sides? (sorry for bad English by the way) I still need to have my win 7 for playing and making let's play videos to youtube and I would you linux to....well i'm not sure yet.

---

### Post by NikTh on 2012-06-28
Hi , 
If you want to test Ubuntu and see how it works go for Wubi or VM. (imo VM has less mess).
When you decide that Ubuntu covers your needs  you can do a regular install , dual-boot with windows.

---

### Post by Sarys on 2012-06-28
> **NikTh said:**
> Hi , 
If you want to test Ubuntu and see how it works go for Wubi or VM. (imo VM has less mess).
When you decide that Ubuntu covers your needs  you can do a regular install , dual-boot with windows.

Ok in that case I dual-boot it since I have used Ubuntu few times in the past.
Thanks for your answer.

---

### Post by sudodus on 2012-06-28
I suggest that you test one or several of Ubuntu, Kubuntu, Lubuntu and/or Xubuntu. They are basically the same linux with different desktop environments. Test them in ***live sessions booted from a CD or USB drive***, and decide after that if one of the flavours is good for you.

At that stage, I think you are ready for a regular dual boot installation (instead of wubi or VM).

If you want more detailed help, please let us know the specification of your computer, particularly CPU, RAM, graphics chip/card. And later on, from a live session, post the output of the following command
```
sudo fdisk -lu
``` in a reply. That will tell us what needs to be done with your hard drive in order to make the dual boot.

* Also remember that editing partitions and installing to hard drives is risky, so get an external hard disk drive and ***backup*** Windows and all your data before starting.

---

### Post by Sarys on 2012-06-28
> **sudodus said:**
> I suggest that you test one or several of Ubuntu, Kubuntu, Lubuntu and/or Xubuntu. They are basically the same linux with different desktop environments. Test them in ***live sessions booted from a CD or USB drive***, and decide after that if one of the flavours is good for you.

At that stage, I think you are ready for a regular dual boot installation (instead of wubi or VM).

If you want more detailed help, please let us know the specification of your computer, particularly CPU, RAM, graphics chip/card. And later on, from a live session, post the output of the following command
```
sudo fdisk -lu
``` in a reply. That will tell us what needs to be done with your hard drive in order to make the dual boot.

* Also remember that editing partitions and installing to hard drives is risky, so get an external hard disk drive and ***backup*** Windows and all your data before starting.

I will use Ubuntu since it's the one I have experience. And I don't have any external hard drives so I have to go without. Well if something goes wrong I just lose few games plus their save files xD

EDIT: And all I know is that I have emachines e725 laptop

---

### Post by Sarys on 2012-06-28
> **sudodus said:**
> 
If you want more detailed help, please let us know the specification of your computer, particularly CPU, RAM, graphics chip/card. And later on, from a live session, post the output of the following command
```
sudo fdisk -lu
``` in a reply. That will tell us what needs to be done with your hard drive in order to make the dual boot.
.

So I take "Try linux" and input that code and tell you what it says in order to know what to do to install linux without problems?

---

### Post by nipunshakya on 2012-06-28
be sure to check the following links before plunging to dual boot:
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html) for partitioning....and
[http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/)

Goodluck

---

### Post by Sarys on 2012-06-28
> **WinuxUser said:**
> be sure to check the following links before plunging to dual boot:
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html) for partitioning....and
[http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/)

Goodluck

Thanks luck is what I need. Luck and time to read trough all of this.

---

### Post by nipunshakya on 2012-06-28
Take your time... and whatever you do, be patient on it... Goodluck

---

### Post by Sarys on 2012-06-28
> **WinuxUser said:**
> Take your time... and whatever you do, be patient on it... Goodluck

Yeah I will. I don't have a hurry to get Ubuntu anyway I just want to get it and learn more about it. My dream is to be abel to make games to linux. xD

---

### Post by Shadius on 2012-06-28
> **WinuxUser said:**
> Take your time... and whatever you do, be patient on it... Goodluck

Agreed. Don't rush. You might be anxious to install Ubuntu, but it's better to understand a few things first so you know what you're getting into. Partitioning is one thing I think you should read up on so you understand what you're doing.  :)

---

### Post by Sarys on 2012-06-28
Oh yeah by the way how much disk space I should give to Ubuntu? My hard drive is about 250 GB.

---

### Post by Shadius on 2012-06-28
> **Sarys said:**
> Oh yeah by the way how much disk space I should give to Ubuntu? My hard drive is about 250 GB.

I believe 15 - 20 GB are the miniumum space requirements, but you can use more space if you like. Ubuntu can run on as little as 5 GB. I have my Ubuntu on an 80 GB hard disk drive.

---

### Post by nipunshakya on 2012-06-28
> **Sarys said:**
> Oh yeah by the way how much disk space I should give to Ubuntu? My hard drive is about 250 GB.
  u want dual  boot? Go for 3 partitions:
1. For windows, around 60-70 gb
2. One NTFS partition(primary) around 100 gb for data sharing between windows and ubuntu
3. One **extended partition(named as logical partition in gparted)** around 90 gb for ubuntu, which can be further divided into /,/home and swap as 18,70 and 2 gb respectively... 
To do this, use the first link i gave to you on my previous post...

Note: if your windows partition is already around the estimation, don't disturb it...

Goodluck.

---

### Post by Sarys on 2012-06-28
> **WinuxUser said:**
> u want dual  boot? Go for 3 partitions:
1. For windows, around 60-70 gb
2. One NTFS partition(primary) around 100 gb for data sharing between windows and ubuntu
3. One **extended partition(named as logical partition in gparted)** around 90 gb for ubuntu, which can be further divided into /,/home and swap as 18,70 and 2 gb respectively... 
To do this, use the first link i gave to you on my previous post...

Note: if your windows partition is already around the estimation, don't disturb it...

Goodluck.


But I need space for my games.

---

### Post by nipunshakya on 2012-06-28
okay... first thing first... please start disk manager in windows and take a screen shot of how your partitions currently appears... maybe something might come out of it...

---

### Post by Sarys on 2012-06-28
> **WinuxUser said:**
> okay... first thing first... please start disk manager in windows and take a screen shot of how your partitions currently appears... maybe something might come out of it...
 
If you have time to wait for few hours. I'm still working and after work I will go to gym so after that.

---

### Post by nipunshakya on 2012-06-28
Lets c where time will take me after this post... maybe i will party??

---

### Post by Lyfang on 2012-06-28
Wubi doesn't involve "risky" formatting or partitioning. However "Ubuntu cannot be booted if Windows has not been shut down cleanly, you have to clear the Windows filesystem from Windows (there is no chkdsk equivalent for Linux yet)." [https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu](https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu)

---

### Post by Sarys on 2012-06-28
> **Lyfang said:**
> Wubi doesn't involve "risky" formatting or partitioning. However "Ubuntu cannot be booted if Windows has not been shut down cleanly, you have to clear the Windows filesystem from Windows (there is no chkdsk equivalent for Linux yet)." [https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu](https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu)

I'm not gonna use Wubi anymore. I've desided to dual-boot.

---

### Post by nipunshakya on 2012-06-28
> **Lyfang said:**
> Wubi doesn't involve "risky" formatting or partitioning. However "Ubuntu cannot be booted if Windows has not been shut down cleanly, you have to clear the Windows filesystem from Windows (there is no chkdsk equivalent for Linux yet)." [https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu](https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu)

Have you seen the following link:
[http://askubuntu.com/questions/8159/wubi-performance-difference](http://askubuntu.com/questions/8159/wubi-performance-difference)

---

### Post by kd5mkv on 2012-06-28
I first tried Wubi, than when I was comfortable with Ubuntu I dual-paritioned. Ubuntu live dvd/cd makes it so easy to do this, Virtualbox and Vmware player are another way to try a different version. Take your time and read up on the different flavors of Ubuntu!

---

### Post by Sarys on 2012-06-28
It looks like it will take years before I get Ubuntu.....
Well...I have time.

---

### Post by Sarys on 2012-06-28
> **WinuxUser said:**
> okay... first thing first... please start disk manager in windows and take a screen shot of how your partitions currently appears... maybe something might come out of it...

There you go it's in Finnish so I hope that dosen't matter that much

---

### Post by nipunshakya on 2012-06-28
:D its not there buddy... where is the pic?? lol

---

### Post by Shadius on 2012-06-28
:lolflag: Forgot to include the screenshot, huh? Happens to me all the time.

---

### Post by Mark Phelps on 2012-06-28
> **Sarys said:**
> But I need space for my games.

These are Windows games, right?  Which, even if they DID run in Ubuntu, would be pointless having them run in two different locations.

So, presuming you want to keep these in Windows, my suggestion would be to cut the Ubuntu OS space to 40GB.  Ubuntu takes up a LOT less room than Win7, and since you're planning on a shared data partition anyway, you can afford to cut it to 40GB -- and still have a lot of room to spare.

---

### Post by Sarys on 2012-06-28
I did put the pic the internet connection is too bad to upload it outside office

---

### Post by Sarys on 2012-06-28
> **Mark Phelps said:**
> These are Windows games, right?  Which, even if they DID run in Ubuntu, would be pointless having them run in two different locations.

So, presuming you want to keep these in Windows, my suggestion would be to cut the Ubuntu OS space to 40GB.  Ubuntu takes up a LOT less room than Win7, and since you're planning on a shared data partition anyway, you can afford to cut it to 40GB -- and still have a lot of room to spare.

So you mean 40GB for linux and 40 for the one between linux and win7?

---

### Post by nipunshakya on 2012-06-29
from post #14, just cut the ubuntu space from 90 gb to 40 gb, and add the 50gb to your windows. Thats what he meant i guess.

---

### Post by Sarys on 2012-06-29
> **WinuxUser said:**
> from post #14, just cut the ubuntu space from 90 gb to 40 gb, and add the 50gb to your windows. Thats what he meant i guess.

I'm just thinking do I need partition to share data between win7 and ubuntu?

---

### Post by nipunshakya on 2012-06-29
> **Sarys said:**
> I'm just thinking do I need partition to share data between win7 and ubuntu?

Its better to have an extra NTFS partition for sharing backup for ubuntu as well as windows..but its not a compulsion. Later, you may regret for not having an extra partition to share betn ubuntu and win. So just a precaution to u...

---

### Post by Sarys on 2012-06-29
> **WinuxUser said:**
> Its better to have an extra NTFS partition for sharing backup for ubuntu as well as windows..but its not a compulsion. Later, you may regret for not having an extra partition to share betn ubuntu and win. So just a precaution to u...

I just don't know how to use it if I do it. And my partitions are already kind of weird. Like I have one 20GB partition that I didn't make

---

### Post by nipunshakya on 2012-06-29
post # 7 had it all...u just didn't show us the pic we asked... if u don't cooperate, how can we help?

---

### Post by Sarys on 2012-06-29
> **WinuxUser said:**
> post # 7 had it all...u just didn't show us the pic we asked... if u don't cooperate, how can we help?

I tried but like I said the internet connection is to bad in the flat I live in. I can try to give you guys pic of it if I'm not too busy at work. (office network is much faster)

---

### Post by Sarys on 2012-06-29
> **Grombtib said:**
> Has found a site with a theme interesting you.

?

---

### Post by Sarys on 2012-06-29
Ok there's the pic (hope fully it's there this time)

---

### Post by Sarys on 2012-06-29
> **WinuxUser said:**
> post # 7 had it all...u just didn't show us the pic we asked... if u don't cooperate, how can we help?

Well thers pic now, right? Above this post that is.

---

### Post by mojo risin on 2012-06-29
Wubi is okay but I wouldnt use it as a long term solution-- It is always a bit slower as to my experience , and it always depends on windows being alright. Also there are some things which can't be done if you are on wubi.
I would go for a dual boot thats the best option f you want a fully operable windows at the same time. 
I have a vM in my lubuntu but I only use the win in there for a single application and thats all so that is alright for me- I wouldnt use vm if you wanted to use it as a daily system.

---

### Post by Sarys on 2012-06-29
> **mojo risin said:**
> Wubi is okay but I wouldnt use it as a long term solution-- It is always a bit slower as to my experience , and it always depends on windows being alright. Also there are some things which can't be done if you are on wubi.
I would go for a dual boot thats the best option f you want a fully operable windows at the same time. 
I have a vM in my lubuntu but I only use the win in there for a single application and thats all so that is alright for me- I wouldnt use vm if you wanted to use it as a daily system.

Next time read the post. Ok? We are talkina about partitions so yeah i´m Trying to dual-boot.

---

### Post by Sarys on 2012-06-29
> **WinuxUser said:**
> post # 7 had it all...u just didn't show us the pic we asked... if u don't cooperate, how can we help?

Well here's even other pic that might be better (I hope it's visible)

---

### Post by nipunshakya on 2012-06-29
it seems like u are one heck of a gamer... u have three partitions, one for ubuntu i guess, the next has windows(alot of space there) and next is just the system recovery thing.....
since the first partition has no label on it, i assume its for linux, unless otherwise.
Doesn't your c: have 179.85 gb free? or is it the space currently being used??

For me it looked a bit messy... you can install ubuntu to that 20 gb if you want... 

But if i were you, i would have totally shrunk c: to somewhat 60-80 gb and make an extra Primary NTFS partition of the new space.... anyways, its ur call

---

### Post by Sarys on 2012-06-29
> **WinuxUser said:**
> it seems like u are one heck of a gamer... u have three partitions, one for ubuntu i guess, the next has windows(alot of space there) and next is just the system recovery thing.....
since the first partition has no label on it, i assume its for linux, unless otherwise.
Doesn't your c: have 179.85 gb free? or is it the space currently being used??

For me it looked a bit messy... you can install ubuntu to that 20 gb if you want... 

But if i were you, i would have totally shrunk c: to somewhat 60-80 gb and make an extra Primary NTFS partition of the new space.... anyways, its ur call

Well the thing is there should only be on partition. I guess last time when I tried to install Ubuntu (it failed) messed up my partitions.

---

### Post by nipunshakya on 2012-06-29
there would always be two partitions, one with your c: and other would be system recovery thing...
the one with no label means you have ubuntu's partitions still there.... if u want, install ubuntu there, my suggestions are already up. u can do according to ur will now.

---

### Post by Sarys on 2012-06-29
> **WinuxUser said:**
> there would always be two partitions, one with your c: and other would be system recovery thing...
the one with no label means you have ubuntu's partitions still there.... if u want, install ubuntu there, my suggestions are already up. u can do according to ur will now.

Ok but you think the best way to go is to make C smaller and make the new partition to share data. So how much I give to C (remember I play windows games and make let's play videos so I need disk space) and how much to the "extra" drive and how much to ubuntu?

EDIT: Oh and what do I use to do that? I know I can shrink C with my win7 but I presume I  use linux to do the other partition.

---

### Post by nipunshakya on 2012-06-29
Post #7,#14 and #30. It explains all.

The tool called disk manager, from where you showed your partition, that can be a handy tool as well for shrinking your c:. google on how to use disk manager in windows 7.

---

### Post by Sarys on 2012-06-29
> **WinuxUser said:**
> Post #7,#14 and #30. It explains all.

The tool called disk manager, from where you showed your partition, that can be a handy tool as well for shrinking your c:. google on how to use disk manager in windows 7.

ok

---

### Post by nipunshakya on 2012-06-29
Post #7,#14 and #30. It explains all.

The tool called disk manager, from where you showed your partition, that can be a handy tool as well for shrinking your c:. google on how to use disk manager in windows 7.

---

### Post by Sarys on 2012-06-29
> **WinuxUser said:**
> Post #7,#14 and #30. It explains all.

The tool called disk manager, from where you showed your partition, that can be a handy tool as well for shrinking your c:. google on how to use disk manager in windows 7.

I minimal space I can get for C is 119,63 GB

---

### Post by Sarys on 2012-06-29
Ok this is what it looks like at the moment. (Final "product")

EDIT: I just realized that I failed. Well I guess I have to format my computer and try again

---

### Post by Lyfang on 2012-06-29
> **WinuxUser said:**
> Have you seen the following link:
[http://askubuntu.com/questions/8159/wubi-performance-difference](http://askubuntu.com/questions/8159/wubi-performance-difference)

Have you seen the following? Wubi Performance Difference "Disk performance is slightly slower. You should not be able to notice any difference under normal circumstances."

---

### Post by nipunshakya on 2012-06-29
> **Sarys said:**
> Ok this is what it looks like at the moment. (Final "product")

EDIT: I just realized that I failed. Well I guess I have to format my computer and try again

what failed bud? your new partitions seems okay to me... you could have included the swap within your extended sda1 partition and that would have been great.... 
Further more, leave the unallocated space as it is coz i don't think you will be able to create a partition out of it... you are already full of 4 partitions...

So , the best is, format the swap, get it inside the sda1, and then make the unallocated space an NTFS partition.

Goodluck

---

### Post by nipunshakya on 2012-06-29
> **Lyfang said:**
> Have you seen the following? Wubi Performance Difference "Disk performance is slightly slower. You should not be able to notice any difference under normal circumstances."

Its good to stick at your end.. Im just trying to show the facts here... and say it now or then, when your windows crashes, your ubuntu will vanish in the air if u use ubuntu as wubi... hope thats not what u want...:guitar:

---

### Post by Mopar1973Man on 2012-06-29
Thinking outside the box here... Give you another idea on this...

I used to be a big Windows user and then finally gave up and made the switch to Ubuntu 11.10. (Now at 12.04) What I did was left my windows drives alone and added a 3rd physical drive (old 250 GB) to install Ubuntu on as a dual boot. In the beginning I set Grub for defaulting to Windows. Now after I've gotten used to Ubuntu I'm now booting mostly to Ubuntu (default drive). I also like to fire up a game now and then and relax too so I'm going to leave my Windows system intact but eventually shrink up the boot drive (150 GB to about 75 GB) and fit Ubuntu behind it. (Not there yet). So now for the little odd programs I don't want to shutdown and reboot for I just use Oracle VirtualBox for Windows so I can runs those small programs.

My Windows side has 2 hard drives totalling 2.5 TB (2,500 GB). I'm sure when I'm skilled enuogh I'll shoehorn in the Linux and ditch the old 250 GB drive. ;)

---

### Post by Lyfang on 2012-06-30
> **WinuxUser said:**
> Its good to stick at your end.. Im just trying to show the facts here... and say it now or then, when your windows crashes, your ubuntu will vanish in the air if u use ubuntu as wubi... hope thats not what u want...:guitar:
You have a point. It still is possible to recover your personal files. Wubi installs a file system within a file system (root.disk). I've recovered files from a Linux Mint system installed with Mint4Win. Since that system would not boot. [http://www.linuxportalen.se/blogs/lyfang/2011/05/15/hur-kommer-man-t-wubi-ubuntumint4win-linux-mint-filerna-om-inte-att-wubimint](http://www.linuxportalen.se/blogs/lyfang/2011/05/15/hur-kommer-man-t-wubi-ubuntumint4win-linux-mint-filerna-om-inte-att-wubimint) (in Swedish)

---

### Post by nipunshakya on 2012-06-30
> **Lyfang said:**
> [http://www.linuxportalen.se/blogs/lyfang/2011/05/15/hur-kommer-man-t-wubi-ubuntumint4win-linux-mint-filerna-om-inte-att-wubimint](http://www.linuxportalen.se/blogs/lyfang/2011/05/15/hur-kommer-man-t-wubi-ubuntumint4win-linux-mint-filerna-om-inte-att-wubimint)

Good one:guitar:

---

### Post by Sarys on 2012-07-01
Ok. I formated my computer and tried again this time it went better (at least I think so)

---

### Post by nipunshakya on 2012-07-01
> **Sarys said:**
> Ok. I formated my computer and tried again this time it went better (at least I think so)

There is no need to think so for it man... this is awesome....

See, i told ya, you are a step ahead of being called a noob now...

Atleast, your partitions looks clean, you will be gamer and none will stop from booting to windows with alot of room there... and you can experiment well with ubuntu as well...

Pretty impressed with your achievements and im glad you made it...


:guitar: ):P Goodluck and keep on Linuxing ):P :guitar:

---

### Post by Shadius on 2012-07-01
> **Sarys said:**
> Ok. I formated my computer and tried again this time it went better (at least I think so)

Looking good! Let me say, welcome to Ubuntu Linux!

---

### Post by Sarys on 2012-07-01
Thanks guys. But yeah should I install all my games that I can play with win and linux (with wine) to the drive "between" win and linux?

---

### Post by nipunshakya on 2012-07-01
Don't totally depend on wine for your games... if u got windows, use it for gaming.... there may be added exception of installing it in shared drive, but i suggest use the shared drive for backup purpose only... 

Keep windows as gamelicious as possible and Ubuntu as professional as possible... Thats what i've had learnt with my dual boot a year ago...

---

### Post by Sarys on 2012-07-01
> **WinuxUser said:**
> Don't totally depend on wine for your games... if u got windows, use it for gaming.... there may be added exception of installing it in shared drive, but i suggest use the shared drive for backup purpose only... 

Keep windows as gamelicious as possible and Ubuntu as professional as possible... Thats what i've had learnt with my dual boot a year ago...

So if I want to play with my Ubuntu I should use Linux native games?

---

### Post by nipunshakya on 2012-07-01
I dont game much in ubuntu... but recently i've started to play 'lord of ultima' and 'command and conquer' available freely at software center.... nice strategy games btw..

---

### Post by nipunshakya on 2012-07-01
oh yes.. there is a thing called 'playonlinux' available at the software center too, especially designed for some serious gaming in ubuntu... and a good substitute for wine (in context of gaming) as well... worth a try.... there are alot of supported games available... check them out too...

---

### Post by Sarys on 2012-07-01
> **WinuxUser said:**
> I dont game much in ubuntu... but recently i've started to play 'lord of ultima' and 'command and conquer' available freely at software center.... nice strategy games btw..

I see. Well I guess I will check software center.

---

### Post by jemadux on 2012-07-01
some time ago i as experiment with virtualbox and still wubi works on vm but ...the good point is to test ubuntu clear on vm

---

### Post by nipunshakya on 2012-07-02
> **jemadux said:**
> some time ago i as experiment with virtualbox and still wubi works on vm

Whoa...!!! you mean u installed a guest OS(windows i guess) on a vm and then tried wubi inside it?? isn't that just making your CPU work more???

---

### Post by vpak on 2012-07-02
I recently experimented with both.

I'm running a 64-bit AMD processor in an Acer laptop with 4gb of RAM and a 60gb SSD. It shipped with Windows Home Premium, I wiped it and put Ubuntu on there...but I couldn't get my 2nd external monitor (connected via USB DisplayLink adapter) working so I wiped again and put Windows back on.

That was a few months ago...last week I decided to try installing Ubuntu 12.04 in a VirtualBox instance. Had problems with the 64-bit vbox so installed the 32-bit version and got Ubuntu working. After I installed guest additions it even worked on both screens! However it wasn't very stable and crashed frequently (I've had good luck with vbox in the past so not sure what was up with that).

Encouraged by vbox handling both of my screens I decided to try wubi...it works fine, but I can't get my second monitor working, just shows bright green. 

I guess it depends on what you're trying to do but personally I would recommend you give vbox a try first then wubi. The only thing I hate about wubi is if you uninstall it you still get the boot-screen (or at least in the past this was the case) - only way to get rid of that is to reinstall Windows from scratch and wipe all the partitions.

---

### Post by nipunshakya on 2012-07-02
> **vpak said:**
> I recently experimented with both.

I'm running a 64-bit AMD processor in an Acer laptop with 4gb of RAM and a 60gb SSD. It shipped with Windows Home Premium, I wiped it and put Ubuntu on there...but I couldn't get my 2nd external monitor (connected via USB DisplayLink adapter) working so I wiped again and put Windows back on.

That was a few months ago...last week I decided to try installing Ubuntu 12.04 in a VirtualBox instance. Had problems with the 64-bit vbox so installed the 32-bit version and got Ubuntu working. After I installed guest additions it even worked on both screens! However it wasn't very stable and crashed frequently (I've had good luck with vbox in the past so not sure what was up with that).

Encouraged by vbox handling both of my screens I decided to try wubi...it works fine, but I can't get my second monitor working, just shows bright green. 

I guess it depends on what you're trying to do but personally I would recommend you give vbox a try first then wubi. The only thing I hate about wubi is if you uninstall it you still get the boot-screen (or at least in the past this was the case) - only way to get rid of that is to reinstall Windows from scratch and wipe all the partitions.


If you could have cared enough to take a good look at what the thread starter has achieved, you wouldn't have had typed such a long opinion of yours... so its better worth carefully reading all the posts before randomly just posting anything just reading the topic...):P

---

### Post by SirWhy on 2012-07-02
I just want to add my two cents. 

Dual booting Ubuntu with Windows 7 is one of the better decisions I've made, especially since it's my laptop, so I can't upgrade much. 

It was an easy enough install and Ubuntu has tools to make dual-booting easy. Give Ubuntu a try first on a VM (like Virtualbox) to try it, don't leave it at that though as you won't be using it to it's full potential. Same with wubi. It'll just be Ubuntu running on top of another operating system, making it slower than it can be.

Good luck

EDIT: I didn't read all the posts and have seemed to have made the same mistake as vpak.... Still my two cents for anyone looking at this in a few days/weeks/months/years...

---

### Post by nipunshakya on 2012-07-02
SirWhy, I loved the reason why u edited your post :)

---

### Post by Sarys on 2012-07-03
Well it looks like I made yet another mistake when installing linux. I don't have swap disk because of that mistake....

---

### Post by nipunshakya on 2012-07-03
post #57 and the above post's partitions isn't different...except the swap area which was functional back in post #57 and unknown as in recent post....

Did u do something with your filesystems after installation?

---

### Post by Sarys on 2012-07-03
> **WinuxUser said:**
> post #57 and the above post's partitions isn't different...except the swap area which was functional back in post #57 and unknown as in recent post....

Did u do something with your filesystems after installation?

No it was like that after installation

---

### Post by Sarys on 2012-07-03
So do I need to Install Ubuntu again? Or can it be fixed?

EDIT: And if I need to Install Ubuntu again how to backup everything? I know where to.

---

### Post by sudodus on 2012-07-03
> **Sarys said:**
> So do I need to Install Ubuntu again? Or can it be fixed?

EDIT: And if I need to Install Ubuntu again how to backup everything? I know where to.

Don't rush! Did you choose encrypted home folders? In that case the 
unknown sda7 partition could be an encrypted swap partition.

Check with ***top ***if you have any swap! And check the content of the file ***/etc/fstab***

---

### Post by Sarys on 2012-07-03
> **sudodus said:**
> Don't rush! Did you choose encrypted home folders? In that case the 
unknown sda7 partition could be an encrypted swap partition.

Check with ***top ***if you have any swap! And check the content of the file ***/etc/fstab***

Sorry too late for that. I'm installing Ubuntu again :D

---

### Post by nipunshakya on 2012-07-03
hold on mate.. there is no need for a reinstallation... sorry for late reply though..

you can boot to live cd mode and then select 'something else' and then just select your swap partition, mark it to format, and then select it to be your swap partition.... first try that... later if it won't work, we can figure something out...

---


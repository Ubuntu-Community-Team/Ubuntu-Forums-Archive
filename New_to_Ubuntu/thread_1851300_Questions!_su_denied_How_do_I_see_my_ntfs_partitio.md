---
title: "Questions! su denied? How do I see my ntfs partition? NOOB with Android experience"
date: 2011-09-28
forum: New to Ubuntu
---

### Post by Phateless on 2011-09-28
Android is actually what drew me to Linux. I've been rooting and flashing to my heart's content for about a year. I've done some very basic commands in terminal with Android and have a glacier, sensation, and vibrant all running cm7 nightlies. Some of you will probably recognize my screen name from XDA. I'm comfortable with the basics of adb and fastboot but don't know any programming at all.

I'm currently running Ubuntu Gnome 11.04 on a dual-boot setup with my xp media center toshiba satellite m115-s3094 laptop. I actually chose "install inside windows" from the installer but for some reason ended up here instead, which I think I'm happier with anyway.  *shrug*

I'm trying to figure out if I can view my windows files on the ntfs partition, or can Linux not read it? I know Android (also ext4) does just fine with fat32. Is there a way for me to view files on the other partition?

I'd like to commit completely to Linux as my only os but I want to make sure I'm still compatible with all my other files. I only started poking around with this earlier today but so far I'm loving it! All of my data is already backed up in dropbox and firefox sync so I'm good to go!

My friend (software developer and long-time linux geek), to test that I really am in dual-boot, told me to save a file, reboot, reopen it and give her the output of the df command from Terminal. Here it is, I'm not sure what I'm looking at.

josh@ubuntu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/loop0             6797452   2139836   4312324  34% /
none                    501160       652    500508   1% /dev
none                    507768       184    507584   1% /dev/shm
none                    507768        96    507672   1% /var/run
none                    507768         0    507768   0% /var/lock
/dev/sda1             77834892  74327344   3507548  96% /host

I tried the su command and it asked for the password, but then no characters would register when I tried to type in my password so of course I got su denied when I hit enter. Not sure wtf that's about.

Thanks in advance for any help!   :popcorn:

---

### Post by IronHead on 2011-09-28
Hi,new to site here,just though id ask a few tech auestions if you don't mind

---

### Post by IronHead on 2011-09-28
My wife and I have druid globals, I would like to know how hard they are to hack and other is..... how hard is it top get into a lap top and access web cam/what controls/would one Have.wireless?

---

### Post by Elfy on 2011-09-28
> **Phateless said:**
> Android is actually what drew me to Linux. I've been rooting and flashing to my heart's content for about a year. I've done some very basic commands in terminal with Android and have a glacier, sensation, and vibrant all running cm7 nightlies. Some of you will probably recognize my screen name from XDA. I'm comfortable with the basics of adb and fastboot but don't know any programming at all.

I'm currently running Ubuntu Gnome 11.04 on a dual-boot setup with my xp media center toshiba satellite m115-s3094 laptop. I actually chose "install inside windows" from the installer but for some reason ended up here instead, which I think I'm happier with anyway.  *shrug*

I'm trying to figure out if I can view my windows files on the ntfs partition, or can Linux not read it? I know Android (also ext4) does just fine with fat32. Is there a way for me to view files on the other partition?

I'd like to commit completely to Linux as my only os but I want to make sure I'm still compatible with all my other files. I only started poking around with this earlier today but so far I'm loving it! All of my data is already backed up in dropbox and firefox sync so I'm good to go!

My friend (software developer and long-time linux geek), to test that I really am in dual-boot, told me to save a file, reboot, reopen it and give her the output of the df command from Terminal. Here it is, I'm not sure what I'm looking at.

josh@ubuntu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/loop0             6797452   2139836   4312324  34% /
none                    501160       652    500508   1% /dev
none                    507768       184    507584   1% /dev/shm
none                    507768        96    507672   1% /var/run
none                    507768         0    507768   0% /var/lock
/dev/sda1             77834892  74327344   3507548  96% /host

I tried the su command and it asked for the password, but then no characters would register when I tried to type in my password so of course I got su denied when I hit enter. Not sure wtf that's about.

Thanks in advance for any help!   :popcorn:

You won't see your password - type it and enter. 

Use sudo instead of su

---

### Post by Elfy on 2011-09-28
> **IronHead said:**
> Hi,new to site here,just though id ask a few tech auestions if you don't mind

Please start your own thread - here's a link that'll start one - [http://ubuntuforums.org/newthread.php?do=newthread&f=326](http://ubuntuforums.org/newthread.php?do=newthread&f=326)

---

### Post by Phateless on 2011-09-28
> **forestpiskie said:**
> You won't see your password - type it and enter. 

Use sudo instead of su

That was my first thought, but I tried it multiple times and it didn't work.

Will try again with sudo.

I took another look in my windows file system and I do see an ubuntu directory sized about 7gb. Ubuntu is also listed in windows programs as something I can uninstall, so it appears it did install inside windows after all.

So does that mean there is no way to access the windows file system from within ubuntu? Does that also mean if I wipe and install only ubuntu that it will run much faster?

My 80 gb hard drive only has 3gb available right now...

As a side note, can anyone tell me some basics on the differences between kde and gnome, and different versions of gnome? I don't even know where to begin.

---

### Post by Elfy on 2011-09-28
You are using wubi - your windows files are available already in /host.

I've changed the prefix to suit as well.

---

### Post by Phateless on 2011-09-28
> **forestpiskie said:**
> You are using wubi - your windows files are available already in /host.

I've changed the prefix to suit as well.

Thanks! So where did I get gnome from? And a trip back to windows confirms that ubuntu shows up in my add/manage programs list, and there's a 7gb ubuntu directory on C.

---

### Post by 3rdalbum on 2011-09-28
> **Phateless said:**
> Thanks! So where did I get gnome from? And a trip back to windows confirms that ubuntu shows up in my add/manage programs list, and there's a 7gb ubuntu directory on C.

Wubi is only a method of installing Ubuntu - once it's installed, it's pretty much standard Ubuntu. So, you get Gnome and Unity and it looks and feels exactly like normal Ubuntu, because it is :-)

---

### Post by Phateless on 2011-09-28
> **3rdalbum said:**
> Wubi is only a method of installing Ubuntu - once it's installed, it's pretty much standard Ubuntu. So, you get Gnome and Unity and it looks and feels exactly like normal Ubuntu, because it is :-)

Got'cha. So it's basically full-fledged Ubuntu, but the installation (and removal) can take place under windows? I can not get inside Ubuntu from within windows, I have to reboot and select it from the boot menu.

Will it run much faster if I install it solo?

---

### Post by Elfy on 2011-09-28
Wubi is not designed to be a long term thing, I'd always be inclined to persuading people to install it as a dualboot. 

One thing that wubi can cause issue with is when there's a new release, I'd not recommend upgrading it - which means backing up, removing and reinstalling.

Yes you have to reboot it.

If you want to use within the other then you might (assuming you have sufficient RAM) want to look into running ubuntu in a virtual machine like vbox inside windows - in that case you can be running them both at the same time.

---

### Post by Phateless on 2011-09-28
> **forestpiskie said:**
> Wubi is not designed to be a long term thing, I'd always be inclined to persuading people to install it as a dualboot. 

One thing that wubi can cause issue with is when there's a new release, I'd not recommend upgrading it - which means backing up, removing and reinstalling.

Yes you have to reboot it.

If you want to use within the other then you might (assuming you have sufficient RAM) want to look into running ubuntu in a virtual machine like vbox inside windows - in that case you can be running them both at the same time.

Got'cha, thanks for your replies. Yes, I am only using it this way to poke around before I commit fully to Linux, which I plan to do.  ;)

Uh oh, I'm letting it download and install updates right now. Maybe I'll be wiping sooner than I thought, lol.

This computer doesn't have nearly enough resources for that. It's a t2050 (I think), 1.6 ghz, core duo, only 1 gb of ram.

I'm assuming it will run MUCH better as a standalone install? What are the pitfalls of going only Linux as opposed to Windows? I know some programs aren't compatible, but what else should I look out for? Today I plugged in my android phone and Linux didn't register it, although the printer it registered and installed drivers right away.

---

### Post by duke.tim on 2011-09-28
Mainly it is just different (as a pitfall to some). Based on my experience more drivers work out of box with Ubuntu than Windows, didn't need to do anything for my android to work.

A lot of pitfalls IMHO can also be considered the strength of linux. 

-Terminal for practically everything, not always the case with gui / not easy for beginners 
-Text config files (configuration editor sorta like regedit) / spread out over system mainly in /etc and /Home/[user]/
-Prompted for root/admin password when changing the system / strong security but annoying
- Free software and repositories / Have to compile sometimes if not in repository
-Harware support, some things just aren't supported / dig around the internet might be a fix out there

---

### Post by Elfy on 2011-09-28
> What are the pitfalls of going only Linux as opposed to Windows?In a nutshell - the things you NEED might not all work if they are windows - _some_ win apps work through wine - but _not_ all.

As you have wubi now - I'd run with it while I was tinkering - make notes of what you learn/find/discover and then in a month or so when the new one's released look to a dualboot or if you're sure that you don't need to run windows go with that.

---

### Post by Phateless on 2011-09-29
> **duke.tim said:**
> Mainly it is just different (as a pitfall to some). Based on my experience more drivers work out of box with Ubuntu than Windows, didn't need to do anything for my android to work.

A lot of pitfalls IMHO can also be considered the strength of linux. 

-Terminal for practically everything, not always the case with gui / not easy for beginners 
-Text config files (configuration editor sorta like regedit) / spread out over system mainly in /etc and /Home/[user]/
-Prompted for root/admin password when changing the system / strong security but annoying
- Free software and repositories / Have to compile sometimes if not in repository
-Harware support, some things just aren't supported / dig around the internet might be a fix out there

> **forestpiskie said:**
> In a nutshell - the things you NEED might not all work if they are windows - _some_ win apps work through wine - but _not_ all.

As you have wubi now - I'd run with it while I was tinkering - make notes of what you learn/find/discover and then in a month or so when the new one's released look to a dualboot or if you're sure that you don't need to run windows go with that.

Thanks to both of you, that's great advice. I was told tonight by a friend that Netflix streaming won't work due to drm issues. If that's true I would need to keep a windows install on hand.

---


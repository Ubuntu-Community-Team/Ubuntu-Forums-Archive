---
title: "Ubuntu Netbook Remix too Slow!"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by geobz on 2008-07-25
Hi guys,

Just installed ubuntu netbook remix on my [redfox wizbook800]("http://http://www.redfoxtechnologies.com/wizbook800.html"). It's suppose to be great in machines like mine but its just too darn slow for me. It feels like my subnotebook might hang any minute especially when I'm in the desktop environment. The mouse arrow moves sluggishly and it takes awhile to show the menu items I chose.

Anyway, my question is, how do i revert to the ordinary ubuntu?

Thanks.

---

### Post by gn2 on 2008-07-25
It's optimised for the Intel Atom CPU which has a three times higher clockspeed than your Wizbook.

Maybe try Xubuntu, Debian Xfce or Arch.

---

### Post by loell on 2008-07-25
oh, my bad, for suggesting remix without looking at the spec processor :(

could you reinstall ubuntu or as also suggested xubuntu?

---

### Post by SarahKH on 2008-08-01
ALT+F2
gnome-terminal

ps -ef | grep ume
<look for ume-launcher>
kill <pid of ume-launcher>

That should help temporarily.   Now. Lets get dangerous :)  In the terminal you opened type this:

sudo apt-get remove ume-launcher 

It's so dead even McCoy couldn't save it now.  You might find maximus to be quite useful on such a small screen (same resolution as my eee 701), if you want it dead replace ume-launcher with maximus and use the above command.  However, looking at the link you provided it seems that you've got an AMD Geode processor inside that thing.  

I would consider throwing as much memory as possible in to that thing, I'd then paitently google for "Ubuntu speed up" and look at the various guides about killing services from boot-up and user sessions.  I'd even, if your a confident Linux user, google "Ubuntu kernel compile" and make a stripped out Geode compiled kernel.  

I've just finished a two day marathon of getting a Transmeta based Flybook going in Gentoo (distcc is my hero) and that took some serious tweaking to make Gnome 2.22 usable.  I suspect you've got even less horsepower in that netbook.

---

### Post by KEYofR on 2009-04-09
I have a new Vaio P-series which does NOT have a geode,, DOES have an atom, a 1.33 ghz atom w/hyperthreading and 2 gigs of 533mhz ram, and I can say that eeebuntu nbr from intrepid is very snappy, and regular ubuntu nbr from jaunty daily as of yesterday is an absolute dog, _worse_ that the factory Vista.

Why in the 9 levels of the sulfurous subterrain is something with "netbook" in it's name running gnome???

Also, eeebuntu nbr from intrepid automatically recognized the very odd screen size (1600x768) and configured X for the native resolution and the latest jaunty daily regular nbr filled the screen but zoomed & stretched some smaller resolution, things are fuzzy and aspect ratio is off.

knoppix 6 (made into usb with unetbootin) is very snappy too and also configures the correct native screen size automatically.

When the original poster says he finds ubuntu nbr too slow, I say, he's right, it really is way too slow, not that his hardware is insufficient.
There should almost be no such thing as insufficient hardware for an OS that is supposedly specifically targeted to netbooks.

---

### Post by AK Dave on 2009-04-23
I'll check things again this evening, but I've been trying to use UNR every night for the last week and it is simple un-usable. Slow. Doggy. Sluggish. 

It seems like it is something in the UME itself that it so slow, because once ... I ... finally ... see ... an app ... pop up, then the app itself runs fine.

Here's what I have:
Dell Mini-9, 2gb ram, 32gb SSD w/ Jaunty installed (ext4, encrypted /home) and UNR applied via apt-get (sudo apt-get install ubuntu-netbook-remix).

I have a primary login account for the netbook which gives me a standard gnome/metacity interface (UNR not enabled), and a secondary user account with UNR enabled. UNR is installed, but I can Switch-User to page back and forth between on and off.

My impression: UNR is a sluggish pig. But with Intrepid, it was fine!

---

### Post by eythian on 2009-04-24
It is this bug:

[https://bugs.launchpad.net/ubuntu/jaunty/+source/linux/+bug/349314/](https://bugs.launchpad.net/ubuntu/jaunty/+source/linux/+bug/349314/)

It is painfully slow. But, if you install the kernel mentioned in there, it will be nice and fast again. The problem is bad Intel drivers not supporting something that is needed in the launcher.

---

### Post by AK Dave on 2009-04-24
Wasn't that bug fixed in final? Thats what I have now.

Here's something I've noticed that makes a HUGE difference:
1. If I login direct to the user account with UNR enabled, it works fine. Pretty good.
2. If I login to the user account with UNR disabled, and Switch User to the UNR account, the UME launcher is fugly slow.

---

### Post by jespdj on 2009-04-24
> **AK Dave said:**
> Here's what I have:
Dell Mini-9, 2gb ram, 32gb SSD w/ Jaunty installed (ext4, encrypted /home) and UNR applied via apt-get (sudo apt-get install ubuntu-netbook-remix).

I have a primary login account for the netbook which gives me a standard gnome/metacity interface (UNR not enabled), and a secondary user account with UNR enabled. UNR is installed, but I can Switch-User to page back and forth between on and off.

My impression: UNR is a sluggish pig. But with Intrepid, it was fine!
I have the same hardware as you: a Mini 9 with 2 GB RAM and a 32 GB SSD (from RunCore).

I don't find UNR slow at all - it works really nice and quick. It boots fast (20 seconds from GRUB screen to login prompt) and I haven't noticed any delays, lags or hangs at all. It's really nice and snappy.

I did a fresh install of [Ubuntu Netbook Remix](http://www.ubuntu.com/getubuntu/download-netbook) which is now an official version of Ubuntu besided the desktop and server versions; I did not install the regular desktop Ubuntu 9.04 and installed UNR on top of it, as you seem to have done. I did format my SSD to ext4.

---

### Post by jaqrah on 2009-04-24
I have noticed many of you are using ext4.  I thought the common wisdom was to stick with ext2, easier on the ssd.  Has something changed with ext4?

---

### Post by snowpine on 2009-04-24
> **jaqrah said:**
> I have noticed many of you are using ext4.  I thought the common wisdom was to stick with ext2, easier on the ssd.  Has something changed with ext4?

ext2 is not a journaling file system, so your data is harder to recover in the event of disc failure, power outage, etc. Speaking for myself, that is the reason I never use ext2 any more. My Dell Mini 9 with Ubuntu 8.04 pre-installed used the ext3 filesystem; Dell, who knows their hardware best, did not choose ext2.

I've only been using ext4 for a couple of weeks, so it is too early to render a verdict yet. No crashes or anything yet.

---

### Post by meeples on 2009-04-24
> replace ume-launcher with maximus and use the above command.

urrggh i hate using maximus, made it so awkward to close and hide windows, i personally think that a regular desktop works fine on a netbook as long as you only have one panel :)

---

### Post by jaqrah on 2009-04-24
> **snowpine said:**
> ext2 is not a journaling file system, so your data is harder to recover in the event of disc failure, power outage, etc. Speaking for myself, that is the reason I never use ext2 any more. My Dell Mini 9 with Ubuntu 8.04 pre-installed used the ext3 filesystem; Dell, who knows their hardware best, did not choose ext2.

I've only been using ext4 for a couple of weeks, so it is too early to render a verdict yet. No crashes or anything yet.

Thanks for your reply.  Considering I am pretty hardcore about backing up, I am not too worried about data recovery in event of failure.  I would just like to get the most mileage out of my ssd.

Btw, are you the same snowpine who is also a #!crunchbang pro?

---

### Post by snowpine on 2009-04-24
> **jaqrah said:**
> Thanks for your reply.  Considering I am pretty hardcore about backing up, I am not too worried about data recovery in event of failure.  I would just like to get the most mileage out of my ssd.

Btw, are you the same snowpine who is also a #!crunchbang pro?

Guilty as charged. I heart #!.  :)

I am currently using ext4 with the "noatime" option for my / partition, and ext3 with noatime for my /home partition (because I dual boot with SliTaz, which doesn't support ext4 yet). If you are not familiar with noatime, it is worth reading about, apparently it is a good option for SSD's, but I can't really explain the particulars.

---

### Post by murphykieran on 2009-04-28
> **eythian said:**
> It is this bug:

[https://bugs.launchpad.net/ubuntu/jaunty/+source/linux/+bug/349314/](https://bugs.launchpad.net/ubuntu/jaunty/+source/linux/+bug/349314/)

It is painfully slow. But, if you install the kernel mentioned in there, it will be nice and fast again. The problem is bad Intel drivers not supporting something that is needed in the launcher.I'm having issues with an Asus Eee PC 904HD where the UME is painfully slow but applications themselves run fine once they're launched (Firefox is perfectly fine for example) and I'd like to try this solution but I don't even know where to start.  There's a post on that page linking to a list of .deb files ([http://people.ubuntu.com/~apw/lp349314-jaunty/](http://people.ubuntu.com/~apw/lp349314-jaunty/)) and I don't know which one I should be using and even if I can just double click the file once it's downloaded or if it needs some esoteric command line magic.

Can anyone point me in the right direction?

---

### Post by Takmadeus on 2009-04-29
Well, I have experienced the sheer slowness of the netbook remix :(

It is a shame that a system that should be a lot faster is actually unusable due to the fact that they just added some nifty effects... I wish there was a way to turn the cool effects off, so the interface ran better.

As for ext4, well, actually it is a SSD saver AFAIK, since it minimizes the amount of disk reads, buy doing the process a lot more efficiently, ext4 is actually faster because it does not have to read as much to get any amount of work done.

Now, is there a way to fix this netbook remix slowness so far?

---

### Post by kneedalz on 2009-04-29
I have the asus eee 701, just installed the unr 9.04, and it is sluggish on my laptop too.  I removed the netbook remix using the synaptic package manager, and now my windows don't have the top bar that has the minimise and close buttons. How do I get this bar back?

---

### Post by gjosef on 2009-06-05
> **kneedalz said:**
> I have the asus eee 701, just installed the unr 9.04, and it is sluggish on my laptop too.

I've done the same thing. Just like everyone else, the menu is painfully sluggish, but the apps themselves run fine once started.

What are the working alternatives for removing the menu?

TIA

---

### Post by gjosef on 2009-06-05
> **gjosef said:**
> I've done the same thing. Just like everyone else, the menu is painfully sluggish, but the apps themselves run fine once started.

What are the working alternatives for removing the menu?

TIA

I discovered it is very easy to disable the UME.
Go to Preferences -> Switch Desktop Mode and select the Classic Desktop. The EEE 701 is a lot snappier at once, but you loose the advantages of the improved UI. 
Would be nice to have those in a snappy setting.

---

### Post by omgitsmit on 2009-06-05
I fixed the sluggish GUI on my ASUS eeePC 900 Netbook by patching the kernel.

I don't know how to patch a linux kernel so i found some .deb's that do it for me :)

You can get them here: [http://timashley.me/?q=node/7](http://timashley.me/?q=node/7)

---

### Post by uha8 on 2009-06-07
> **eythian said:**
> It is this bug:

[https://bugs.launchpad.net/ubuntu/jaunty/+source/linux/+bug/349314/](https://bugs.launchpad.net/ubuntu/jaunty/+source/linux/+bug/349314/)

It is painfully slow. But, if you install the kernel mentioned in there, it will be nice and fast again. The problem is bad Intel drivers not supporting something that is needed in the launcher.

I have this bug on an Eee pc 900, but that link is far too technical for me .. Could you post a guide?

---

### Post by omgitsmit on 2009-06-07
> **uha8 said:**
> I have this bug on an Eee pc 900, but that link is far too technical for me .. Could you post a guide?

Patching a kernel was a bit to technical for me also, that's why i've put up a link with two .deb installation packages that will do it for you!

[http://timashley.me/?q=node/7](http://timashley.me/?q=node/7)

Easy as pie!

---

### Post by uha8 on 2009-06-08
> **omgitsmit said:**
> Patching a kernel was a bit to technical for me also, that's why i've put up a link with two .deb installation packages that will do it for you!

[http://timashley.me/?q=node/7](http://timashley.me/?q=node/7)

Easy as pie!

Thank you! I'll try it, when I get to the computer probably in the weekend.

---

### Post by gjosef on 2009-06-09
> **uha8 said:**
> Thank you! I'll try it, when I get to the computer probably in the weekend.

It worked well on my Asus 701! And easy indeed.

---

### Post by uha8 on 2009-06-09
I have a bigger problem with my Eee, that I hope this will fix too. When I installed UNR and restarted a few times, the title bars and system tray suddenly disapeard, have you any idea if this patch will help?

---

### Post by pauna on 2009-06-09
> **uha8 said:**
> I have a bigger problem with my Eee, that I hope this will fix too. When I installed UNR and restarted a few times, the title bars and system tray suddenly disapeard, have you any idea if this patch will help?

You have hit a bug in UNR, which the proposed patch does not solve.

You need to get a command shell window. Try ALT-T. If that does not work, do a right click and create a launcher for "gnome-terminal" to your desktop and run the command shell from there.

Then you can get your panels and title bard back by executing the commands "gnome-panel" and "gnome-wm".

Then you need to make sure you session is saved when you log out.

---

### Post by uha8 on 2009-06-09
> **pauna said:**
> You have hit a bug in UNR, which the proposed patch does not solve.

You need to get a command shell window. Try ALT-T. If that does not work, do a right click and create a launcher for "gnome-terminal" to your desktop and run the command shell from there.

Then you can get your panels and title bard back by executing the commands "gnome-panel" and "gnome-wm".

Then you need to make sure you session is saved when you log out.

Wow that's it? Will it fix the prob permanently or just until reboot?

---

### Post by omgitsmit on 2009-06-09
> **gjosef said:**
> It worked well on my Asus 701! And easy indeed.

Im glad i could help!

If you have any other issues, feel free to ask in chat (see signature) ):P

---

### Post by uha8 on 2009-06-11
> **omgitsmit said:**
> Im glad i could help!

If you have any other issues, feel free to ask in chat (see signature) ):P

I'm glad you did, ty!
Btw nice blog

---

### Post by jzacsh on 2009-06-21
> **omgitsmit said:**
> Patching a kernel was a bit to technical for me also, that's why i've put up a link with two .deb installation packages that will do it for you!

[http://timashley.me/?q=node/7](http://timashley.me/?q=node/7)

Easy as pie!

I'd love to ue this installer,but I get a message saying something like its "out of date" and I should find the updated version. using your article I couldn't see how I'd find an updated verion, and the same as  the other person on this forum: the kernel patch is something I would be willing to do if I knew where to start.

any help anyone?

---

### Post by uha8 on 2009-06-22
> **jzacsh said:**
> I'd love to ue this installer,but I get a message saying something like its "out of date" and I should find the updated version. using your article I couldn't see how I'd find an updated verion, and the same as  the other person on this forum: the kernel patch is something I would be willing to do if I knew where to start.

any help anyone?

If it's the same message as I get, you can press ignore or something, and choose to install anyway. That's what you should do, then restart and it works.

---

### Post by markyb86 on 2009-06-22
I love gnome on my EeePC 900 (which is a 900mhz Intel Celeron)
I cannot stand the netbook launcher (ume-launcher)
That app is sooooo slowwwwwwwwwww. ubuntu 9.04 desktop edition is where its at.
Use it on both my desktop and netbook.

---

### Post by jzacsh on 2009-06-22
> **markyb86 said:**
> I love gnome on my EeePC 900 (which is a 900mhz Intel Celeron)
I cannot stand the netbook launcher (ume-launcher)
That app is sooooo slowwwwwwwwwww. ubuntu 9.04 desktop edition is where its at.
Use it on both my desktop and netbook.

I was considering trying that, but how did you get your desktop-edition iso onto a flash drive properly?

**ps, for anyone else looking for help:**
I visited the suggested launchpad page, and followed [comment number 74]("https://bugs.launchpad.net/ubuntu/jaunty/+source/linux/+bug/349314/comments/74") and [comment number 79]("https://bugs.launchpad.net/ubuntu/jaunty/+source/linux/+bug/349314/comments/76")'s instructions successfully. however, after rebooting (as suggested) my netbook was a LITTLE bit faster, but not as I'd like (as I've seen NBR on an acer aspire).
Next I tried [comment 125]("https://bugs.launchpad.net/ubuntu/jaunty/+source/linux/+bug/349314/comments/125")'s solution: [Adam McDaniel's suggestion]("http://www.array.org/ubuntu/setup-jaunty.html") - this also yielded the same *only-slightly-better* result (but still nauseating to watch).

---

### Post by markyb86 on 2009-06-22
Same way I get all iso's on it, I use unetbootin 3.19 on windows and it "Just works" I have never used unetbootin on linux but my colleagues on easy peasy forums assure me it also "Just works"

It is a very easy proceedure, just download iso, stick in flash drive (erase it if you already have a linux on it), then run unetbootin, select the drive and hit ok. It will say OK or Reboot now, which all you have to do is say OK, then take the drive and put it in the eee. when the eee boots and you see the Eee logo on a grey screen, press esc., and then select the flash drive.

OH and also after installing it, make sure you disable Compiz by right clicking the desktop, change background, then goto the effects tab, and click none. compiz isnt necessary on these computers.

---

### Post by jzacsh on 2009-06-22
> **markyb86 said:**
> Same way I get all iso's on it, I use unetbootin 3.19 on windows and it "Just works" I have never used unetbootin on linux but my colleagues on easy peasy forums assure me it also "Just works"

It is a very easy proceedure, just download iso, stick in flash drive (erase it if you already have a linux on it), then run unetbootin, select the drive and hit ok. It will say OK or Reboot now, which all you have to do is say OK, then take the drive and put it in the eee. when the eee boots and you see the Eee logo on a grey screen, press esc., and then select the flash drive.

OH and also after installing it, make sure you disable Compiz by right clicking the desktop, change background, then goto the effects tab, and click none. compiz isnt necessary on these computers.

great advice, thanks! i'll try unetbootin tonight!

---

### Post by markyb86 on 2009-06-22
sorry its so jumbled if you want a better walkthrough let me know

---

### Post by Wiebelhaus on 2009-06-22
> **geobz said:**
> Hi guys,

Just installed ubuntu netbook remix on my [redfox wizbook800]("http://http://www.redfoxtechnologies.com/wizbook800.html"). It's suppose to be great in machines like mine but its just too darn slow for me. It feels like my subnotebook might hang any minute especially when I'm in the desktop environment. The mouse arrow moves sluggishly and it takes awhile to show the menu items I chose.

Anyway, my question is, how do i revert to the ordinary ubuntu?

Thanks.

UNR isn't to slow , your computer is.

---

### Post by markyb86 on 2009-06-23
I don't even know why they are selling 400 mhz machines.

---

### Post by markyb86 on 2009-06-23
> **geobz said:**
> Hi guys,

Just installed ubuntu netbook remix on my [redfox wizbook800]("http://http://www.redfoxtechnologies.com/wizbook800.html"). It's suppose to be great in machines like mine but its just too darn slow for me. It feels like my subnotebook might hang any minute especially when I'm in the desktop environment. The mouse arrow moves sluggishly and it takes awhile to show the menu items I chose.

Anyway, my question is, how do i revert to the ordinary ubuntu?

Thanks.
You should look into DSL (Damn Small Linux)
Ubuntu isnt made for a 400 MHz processor.

[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

---

### Post by uha8 on 2009-06-23
> **Wiebelhaus said:**
> UNR isn't to slow , your computer is.

That's not right. As I wrote before, I had the same lag or speed problem on the same computer - Eee 900, but after installing that patch, it runs smooth and nice!

---

### Post by jzacsh on 2009-06-25
> **markyb86 said:**
> sorry its so jumbled if you want a better walkthrough let me know

Awesome! my netbook flies now - wish I would've just done this sooner. Now I just need to research what they did with UNR that makes it more "efficient for mobility" (power, resources, unnecessary apps), and see if I can custom tweak my Desktop to be nearly as efficient.

actually - just kind of interesting: I'm surprised that Evolution comes with UNR - I removed it right away, being as I'm not going to start using an email client to collect mail on/clutter my hard drive (I normally use webmail with a desktop **anyway** - what happened to "*cloud computing*" with the netbook?).

---

### Post by snowpine on 2009-06-25
> **jzacsh said:**
> 
actually - just kind of interesting: I'm surprised that Evolution comes with UNR - I removed it right away, being as I'm not going to start using an email client to collect mail on/clutter my hard drive (I normally use webmail with a desktop **anyway** - what happened to "*cloud computing*" with the netbook?).

Evolution is part of the Gnome desktop and is installed by default on all Gnome-baseed Linux distros (including Ubuntu). One of the reasons many users complain that Gnome is "bloated." ;)

---

### Post by philcamlin on 2009-06-25
glad everything works :popcorn:

---

### Post by jzacsh on 2009-06-25
> **snowpine said:**
> Evolution is part of the Gnome desktop and is installed by default on all Gnome-baseed Linux distros (including Ubuntu). One of the reasons many users complain that Gnome is "bloated." ;)

That I figured, but I just thought that UNR was supposed to be the _customized_ take of the standard desktop.

> **philcamlin said:**
> glad everything works :popcorn:

as am I!

---

### Post by markyb86 on 2009-06-25
That's awesome I am glad it worked for you!!!

---

### Post by jrev on 2009-06-27
Why not use eeebuntu 3.0 standard, NBR or base ?
You will not have anything slow on your eeepc :D

---

### Post by uha8 on 2009-06-28
> **jrev said:**
> Why not use eeebuntu 3.0 standard, NBR or base ?
You will not have anything slow on your eeepc :D

I would really like to know the differences between those!

---

### Post by jzacsh on 2009-06-28
> **jrev said:**
> Why not use eeebuntu 3.0 standard, NBR or base ?
You will not have anything slow on your eeepc :D

I'm actually going to try eebuntu myself now. this thread is the first i've heard of it.

I thought that my installation of Ubuntu Desktop had solved my problems but then I kept getting this weird behavior:

With the original Desktop installation (just after the login screen) I'd have only a mouse and a black background. Nothing I pressed would do anything

(which is very weird, because after installation, and a couple of reboots and installation packages from synaptic - everything was running smoothly).

After this^ I thought, "maybe I messed up the installation", so I reinstalled Ubuntu Desktop from my flash drive. everything was fine, did a couple reboots (one of them, just following update manager's instructions) installed all kinds of stuff (apache, gnome do, mysql, phpmyadmin, etc). Then, sure enough, I had the same problem - a black screen after login (with only a mouse).

_some googling found me this:_
**[http://ubuntuforums.org/archive/index.php/t-926232.html](http://ubuntuforums.org/archive/index.php/t-926232.html)**
*which is really a thread with the same exact problem - but no one really answered the person. Though, from that thread I decided to try **Gnome Failsafe**.*

I got an error message that said something like "**a gnome installation could not be found**". Then:
> *This is the Failsafe xterm session. You will be logged into a terminal console so that you may fix your system if you cannot log in any other way. To exit the terminal emulator, type 'exit' and enter into the window.*

**Now the bottom-right corner of my monitor is a white box with the command line in it.** _I have no problem navigating through the terminal_, but I don't know where to start - or if its even worth trying to fix. *Also, there's really no reason I can think of that this even happened - so if I fix it with out knowing why it happened and how to prevent it, than just getting it fixed would be fruitless, no?*

Any advise is greatly appreciated (**maybe I should start a new thread** all together? maybe this is still **related to the fact that I'm on a netbook?**).

---

### Post by uha8 on 2009-06-29
> With the original Desktop installation (just after the login screen) I'd have only a mouse and a black background. Nothing I pressed would do anything


I had this problem too, but I found out that it's the desktop switcher (Ubuntu nbr > classic Gnome) that has the bug, that appears when you are using an Eee pc 900 or 901, I think. Try to reinstall the system, and then don't touch that switcher!
I heard that it's gonna be fixed soon.

---

### Post by jzacsh on 2009-06-29
> **uha8 said:**
> I had this problem too, but I found out that it's the desktop switcher (Ubuntu nbr > classic Gnome) that has the bug, that appears when you are using an Eee pc 900 or 901, I think. Try to reinstall the system, and then don't touch that switcher!
I heard that it's gonna be fixed soon.

I'm not sure which switcher you're talking about. nbr, as in Netbook Remix? Netbook Remix is no longer installed on my netbook. What I did was a fresh install of Ubuntu Desktop edition, and installed over "entire hard drive" (on both occassions). So there shouldn't be anything left of Netbook Remix on my machine.

Let me know if I'm just misunderstanding you.

---

### Post by uha8 on 2009-06-29
> **jzacsh said:**
> I'm not sure which switcher you're talking about. nbr, as in Netbook Remix? Netbook Remix is no longer installed on my netbook. What I did was a fresh install of Ubuntu Desktop edition, and installed over "entire hard drive" (on both occassions). So there shouldn't be anything left of Netbook Remix on my machine.

Let me know if I'm just misunderstanding you.

Oh I thought you had Netbook Remix.. I had the exact same problem that you describe with that system :/

---

### Post by jzacsh on 2009-06-29
> **uha8 said:**
> Oh I thought you had Netbook Remix.. I had the exact same problem that you describe with that system :/

:) thanks anyways. does anyone else know what might be going on with my installs?

---

### Post by vroegahh on 2009-06-30
> **omgitsmit said:**
> Patching a kernel was a bit to technical for me also, that's why i've put up a link with two .deb installation packages that will do it for you!

[http://timashley.me/?q=node/7](http://timashley.me/?q=node/7)

Easy as pie!


I fixed the video delay problem on my eeepc 900 with this patch. When I installed new updates today though the same problem came back :( .

Does anybody know how to fix this? I already tried to reinstall the patch but that didn't work out.

---

### Post by gjosef on 2009-07-03
> **vroegahh said:**
> I fixed the video delay problem on my eeepc 900 with this patch. When I installed new updates today though the same problem came back :( .

Made the same mistake.... :-(

---

### Post by mpc350 on 2009-08-05
This is wonderful.  I was so annoyed at how slow the interface worked,and was just about to reinstall everything and then found "the patch".  Things working well now with the new old kernel.

Only problem -- my touchpad is way too slow.  I sped it up as much as possible in mouse preferences panel, but still not good enough.  A very noticeable difference from the last kernel.    Any ideas anyone?

Thanks

Specs:  eeebuntu; asus 900a, 1gb, atom 1.6ghz

---

### Post by ousama on 2009-08-09
**Known problem on Remix**
I brunched my computer to an external monitor, so ubuntu changed the resolution in the file /etc/X11/xorg.conf . When unconnecting the monitor it does not re-change the resolution inscribed in this file. This makes launcher very slow as well as the computer. All I had to do is to undo the changes in this file with gedit.

---

### Post by Fabben23 on 2010-11-11
I installed Ubuntu Netbook Remix on an old PC with a 24" monitor  attached. I had all the problems listed here. Mainly mouse usuable, main  screen unresponsive and netbook-launcher running at 100%

After a month of trying various things and getting nowhere - I was ready  to give up.
Then I tried changing the screen resolution - IT WORKED.

Then I tried all the resolutions for my monitor - some work and some  don't. It's a night and day difference. If it works, it works very well  but if it doesn't work, it's unusable.

Can it be that something that had me perplexed for so long, just needs  the monitor's resolution tweaked a little and then it's fixed?

---


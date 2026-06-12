---
title: "Ubuntu VS XP - worth it?"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by NNNDaddy on 2008-06-17
Hi everybody. I'm new to these forums, and to Linux in general.

I apologize already if this is posted in the wrong section of the board. Feel free to move this thread. The forum has a ton of sections and I figured that this would be the most appropriate one.

My oldest computer is running XP SP2. It has a 1.6ghz P4, 512mb of ram, integrated graphics, and 80 gb of hd space. 

It runs just "okay". It freezes often when running applications like Firefox, for lack of RAM I suppose. 

I just wanted to know - would it be beneficial for me to put Ubuntu on this computer? My parents use this computer for nothing more than surfing the web and checking email. Nothing resource intensive.

Thank you in advance for all help.

---

### Post by saj0577 on 2008-06-17
Why not give it ago, dont take other peoples opinions and views for solid as people have many different opinions some more biased then others. So why not create your own opinion.:)

Eithee use the live cd or on the new install cd for 8.04 there is an option to install it inside your current XP install so if you dont like it you simply remove it and everythings back to how it was before. 

Hope it helps.

Saj

---

### Post by Duck2006 on 2008-06-17
ubuntu will run ok on that system, my other system is a P3 700Mhz cpu with 68Mb of ram and it runs ok. This may help with installing ubuntu.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by gameryoshi600 on 2008-06-17
Yeah. You should do a dual boot give ubuntu 8-20 gigs of space. Ubuntu would run better than xp on that. You can also try xubuntu cause it uses a window manager for slower computers.

---

### Post by NNNDaddy on 2008-06-17
> **saj0577 said:**
> Why not give it ago, dont take other peoples opinions and views for solid as people have many different opinions some more biased then others. So why not create your own opinion.:)

Eithee use the live cd or on the new install cd for 8.04 there is an option to install it inside your current XP install so if you dont like it you simply remove it and everythings back to how it was before. 

Hope it helps.

Saj

Thanks.

I have a couple of questions:

What is the difference between a Live cd and a normal cd?

If I am installing inside XP, doesnt that mean I will be running linux through XP, like a VM? That would run like crap. Or, do you mean Dual booting?

---

### Post by aktiwers on 2008-06-17
Hi and Welcome!

Give it a shot and see if you like it. Ubuntu would run fine on those specs :)

---

### Post by NNNDaddy on 2008-06-17
Cool. Thanks. I know how to dualboot.

---

### Post by aktiwers on 2008-06-17
> **NNNDaddy said:**
> Thanks.

I have a couple of questions:

What is the difference between a Live cd and a normal cd?

If I am installing inside XP, doesnt that mean I will be running linux through XP, like a VM? That would run like crap. Or, do you mean Dual booting?

No that means that the installer creates a virtual disk on XP and installs Ubuntu on that virtual disk. Then adds the disk to windows bootloader, letting you choose to boot from it when you startup. (it's nothing like virutalbox or vmware).

---

### Post by lazyart on 2008-06-17
> **gameryoshi600 said:**
> Yeah. You should do a dual boot give ubuntu 8-20 gigs of space. Ubuntu would run better than xp on that. You can also try xubuntu cause it uses a window manager for slower computers.

Eh, you don't need to go to xubuntu-- 1.6 ghz + 512 megs is plenty for ubuntu to be happy with.

---

### Post by gameryoshi600 on 2008-06-17
> **lazyart said:**
> Eh, you don't need to go to xubuntu-- 1.6 ghz + 512 megs is plenty for ubuntu to be happy with.

Yeah I guess. But Xubuntu if you want awesome performance.

---

### Post by avtolle on 2008-06-17
Installing within XP I believe is referencing the use of Wubi to install Ubuntu. It is NOT a virtual machine, but rather when booted, runs Ubuntu "natively", no emulation. I've been running 8.04 AMD-64 with a Wubi install and it runs very well, much better than a virtual machine installation of 7.10 did on the same machine. According to the documentation, the only thing that is a bit slower is access to the hard drive, which for most people, me included, is not noticeable.

All that said, installing to disk in separate partitions is the optimal way to go for a dual boot.

Live CD=one which installs the system into the RAM, can run it from there (albeit slowly) to see if it "works". No changes are made to the system, and when the user logs out, the system is back to where it was before booting the Live CD. Be aware that the Live CD sometimes doesn't do well on older hardware. The other option is to install from what is known as the "alternate install" cd, which uses a text-based installer, which, IMO, is very easy to use. If you use this, you will be installing to the HDD, there not being a way to run it in the "Live CD" mode and it (alternate install) cannot currently be used with Wubi.

---

### Post by thejstupid on 2008-06-17
The difference between a live cd and a install cd or what ever...
The difference being, you can insert the cd, boot up your computer, and it will run right off the CD. You can try it out with out installing it. It will however run a little slower because its running off of your cd drive. I am running ubuntu hardy, as well as fedora core. I enjoy linux. I daul boot either one. Ubuntu has changed so much since it was first coded. You will really have fun with it. It is way more easier and safer to use then before. It will just continue to evolve into something that everyone will use in the future. (NO MORE MICROSOFT YAY). Since its free... its a bonus. There are many linux's out there but ubuntu is the best if your a beginner at linux. Ubuntu was my first choice when i went to linux because it had way more easy installer options.But as like someone commented before, make your own opinion. The forums are a great place for people to ask questions, get info, etc. But to ultimately know what ubuntu is, you have to dive into it yourself. Hope this helps.

---

### Post by NNNDaddy on 2008-06-17
One last question:

If I make a seperate partition with say, 5gb of space, and end up REALLY liking Ubuntu, could I delete the XP partition, and have all the space go to my Ubuntu partition?

---

### Post by avtolle on 2008-06-17
> **NNNDaddy said:**
> One last question:

If I make a seperate partition with say, 5gb of space, and end up REALLY liking Ubuntu, could I delete the XP partition, and have all the space go to my Ubuntu partition?
Likely not, for the following reason. Linux partitions add/remove space "from the end", not the beginning. The XP partition is, I'm sure, on the first partition of the HDD. Deleting the XP partition will create a bunch of room, but, as it is before the beginning of the Ubuntu partition, you won't be able to add it to the Ubuntu partition. It can be used for things like setting up a /home partition, but to expand (resize) the Ubuntu partition to take advantage of this space, you'll need to back up the Ubuntu home folder, for example, totally reformat the HDD, then reinstall Ubuntu. Just fyi.

---

### Post by NNNDaddy on 2008-06-17
> **avtolle said:**
> Likely not, for the following reason. Linux partitions add/remove space "from the end", not the beginning. The XP partition is, I'm sure, on the first partition of the HDD. Deleting the XP partition will create a bunch of room, but, as it is before the beginning of the Ubuntu partition, you won't be able to add it to the Ubuntu partition. It can be used for things like setting up a /home partition, but to expand (resize) the Ubuntu partition to take advantage of this space, you'll need to back up the Ubuntu home folder, for example, totally reformat the HDD, then reinstall Ubuntu. Just fyi.

Okay. That makes sense. Thanks.

Hmmmm...

Ill try it. Thanks for all of your help. Everybody.

---

### Post by Duck2006 on 2008-06-17
> **NNNDaddy said:**
> One last question:

If I make a seperate partition with say, 5gb of space, and end up REALLY liking Ubuntu, could I delete the XP partition, and have all the space go to my Ubuntu partition?

Yes you could do that, but a clean install will be better.

---

### Post by crjackson on 2008-06-17
> **NNNDaddy said:**
> One last question:

If I make a seperate partition with say, 5gb of space, and end up REALLY liking Ubuntu, could I delete the XP partition, and have all the space go to my Ubuntu partition?

Yes.  You need to use "gnome partition editor" to do that.  you can google "gparted" and download the newest live cd version.

---

### Post by Fixman on 2008-06-17
> **NNNDaddy said:**
> One last question:

If I make a seperate partition with say, 5gb of space, and end up REALLY liking Ubuntu, could I delete the XP partition, and have all the space go to my Ubuntu partition?

Of course you can, you must just use gParted (its on th Live CD).

Anyway, don't forget to do a swap partition (when you use Ubuntu, even before you stop dual booting) or Ubuntu will go really slow.

---

### Post by kansasnoob on 2008-06-17
Well, for a few months every computer in my home has been dual-booted (or more) with at least one Ubuntu partition and Win XP. Now for just a few weeks I'm "empty nesting" and have only one computer left that's dual booted with Hardy and XP.

It makes little sense to me to throw XP overboard since I have several years of proprietary software that I might as well use when needed, but if some rule were passed tomorrow that dual-booting was an international offense I'd keep Ubuntu Hardy Heron and say bye-bye to XP.

Why? The first reason is security, the second is stability. Since I figured out that pre-released and unsupported Updates are not for nOObs I've had ZERO breakage! My third reason has to be the simplicity of Abiword. My fourth reason is this community of volunteers that simply seem to thrive on helping one another.

I could go on, but it'd be pointless, although I should mention that XP will soon be "off the market" and Vista just stinks!

---

### Post by walmartshopper67 on 2008-06-17
Yeah, Ubuntu will run fine on almost anything, depending on what you want to do with it. It'll probably run great for you - but operating system choices are highly subjective. I love it and have used Ubuntu as my sole desktop operating system since Breezy (old,old version of Ubuntu). 

There's 4 very personal things I don't like to discuss and make recommendations about: Religion, Politics, Relationships, and Operating System Choice. 

Just remember, unlike (most) drugs, it's GOOD to experiment with operating systems. All the cool kids are doing it :cool:

---

### Post by billgoldberg on 2008-06-17
Ubuntu would be better than xp for that pc.

Ubuntu by itself is faster than xp and since you won't need to run anti-virus, anti-spyware, ... programs in real time, you will really feel the performance difference.

That being said, ubuntu uses gnome to present it users interface.

There are others like xfce, fluxbox, ... that are lighter, but gnome should do good.

If you switch to ubuntu you will have some questions, feel free to ask everything here.

The first thing you'll need to do is open "system -> administration -> synaptic manager" and download and install the package "ubuntu-restricted-extras" and "sun-java6-jre" some other sun-java6 packages.

I also refer to my "media" and "customizing guide" in my signature.

---

### Post by scotcella on 2008-06-17
I have the exact same specs for my Dell laptop. 

Everything works just fine, don't worry too much about it. Of course make sure you do a test on the Live CD to make sure everything is working out of the box. 

The only problems I can see happening are hard ware issues, you  never know. If you do, you can always tweak around and get it right. It's not that hard. I dont have ubuntu installed on the said laptop but I did a Live CD test and everything was working including the wireless.

If you run into problems, just post a question on the forums or do a search for similar issues. 

I've been using Ubuntu for on and off for about two years now, it's only in the last month or so I've used it exlusively- due to the excellent software improvements when Hardy was released. The previous version what ever it was called- Edgy I think, I could never get the wireless working. 

Don't worry about asking stupid questions, it's better you find out than learn the real hard way if you lose all your data.

Anyway, welcome!!!

---


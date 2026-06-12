---
title: "Ubuntu slow on my netbook"
date: 2012-03-08
forum: New to Ubuntu
---

### Post by poshin on 2012-03-08
I installed Ubuntu 11.10 on my netbook (Intel Atom, 1 GB Ram, 1.6 GHz) using Wubi.  However the Ubuntu was slower than my Windows XP and even a simple click took time to load...any help on this?  :confused::confused::confused:

---

### Post by rollcast on 2012-03-08
Have you tried using one of the light weight desktop environments such as xfce?

---

### Post by poshin on 2012-03-08
@rollcast,

No I haven't.  I'm sorry but I'm a complete noob at this.  Now what is xfce and what do I exactly do with it?

---

### Post by rollcast on 2012-03-08
If you just installed Linux right now you'll probably be using the Unity UI. It should look a bit like this,

[IMG]http://4.bp.blogspot.com/-SCQze0-rF1s/Tb_1K9WoBXI/AAAAAAAABQQ/4FtvDfC9Ofs/s1600/ubuntu-unity.png[/IMG]

However there are alternative UI s availible for Ubuntu that use more or less computing power by having more or less features.

Xfce is a lightweight desktop environment for ubuntu, so it cuts down on system overheads and should speed up your system.

I'm not sure but wubi may install xfce as an alternative by default. So log out of you account and when the login screen comes up click on the button that looks a bit like a sun thats to the right of your account name. A list should drop down and if xfce is in there then click on it and proceed to login and try out xfce to see if it improves your system speed.

If its not there then log back into your account and install xfce.

Instructions : [http://www.linuxthebest.com/how-to-install-xfce-on-ubuntu-11-10/](http://www.linuxthebest.com/how-to-install-xfce-on-ubuntu-11-10/)

That should explain a bit more about xfce and how to install it.

Hope this helps,
AL

---

### Post by Paqman on 2012-03-08
Before changing the whole desktop environment, try using a more suitable one that you already have installed. Log out, click the cog by your username and select "Unity 2D". It should be a LOT better.

I run Unity 2D on a netbook with the same spec, and it's fine.

---

### Post by Paqman on 2012-03-08
> **rollcast said:**
> 
I'm not sure but wubi may install xfce as an alternative by default.

No, the standard desktop is ubuntu-desktop, which is Gnome. If you do want XFCE then install the package xubuntu-desktop. However, as mentioned above, try the lightweight version of Unity that you do have installed first. XFCE will be quite a large download, and you'd then have to remove Gnome afterwards.

---

### Post by poshin on 2012-03-08
@Rollcast,

I'll try that over the weekend and hopefully it fixes the problem.  Thank you so much.  :D  

Just one question.  When the article says "In console write:

sudo apt-get install xubuntu-desktop"

I got to the terminal and type that right?

---

### Post by poshin on 2012-03-08
> **Paqman said:**
> Before changing the whole desktop environment, try using a more suitable one that you already have installed. Log out, click the cog by your username and select "Unity 2D". It should be a LOT better.

I run Unity 2D on a netbook with the same spec, and it's fine.


The 2D is also slow.  Guess my netbook is too old for it.

---

### Post by cortman on 2012-03-08
Actually, if you can download and create a bootable Xubuntu flash drive, I would recommend a fresh reinstall to cut down on crud, and avoid having multiple extraneous programs.

---

### Post by I2k4 on 2012-03-08
I'm happily running one of the lightweight versions (Lubuntu 10.10) on my Acer netbook - same specs as yours.

I suggest pre-testing several versions on Live USB using these instructions - if a version runs decently on USB it will run even better from your HDD:

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

My netbook experience is that the move from version 10 to version 11 of Ubuntu and its variants was a major change in resource demands, similar to the move from XP to Vista in Windows.  The new Ubuntu is primarily designed for higher spec hardware and so be it - even though others here are correct that the lighter weight interfaces for 11.x run better on little netties, none of them run as well as Ubuntu 10.10 and its lightweight variants.  

Also be aware that it's worth spending some time learning your way around Linux on the very newbie-friendly Ubuntu desktop version before installing the lightweights, because while snappier, they are also cruder and less helpful for anyone moving from Windows.

---

### Post by nothingspecial on 2012-03-08
I agree. Ubuntu is designed for hi-spec machines and why shouldn't it be.

The netbooks in my house run Lubuntu. :)

---

### Post by poshin on 2012-03-09
> **cortman said:**
> Actually, if you can download and create a bootable Xubuntu flash drive, I would recommend a fresh reinstall to cut down on crud, and avoid having multiple extraneous programs.
Thinking of doing that exact same thing.

---

### Post by poshin on 2012-03-09
> **I2k4 said:**
> I'm happily running one of the lightweight versions (Lubuntu 10.10) on my Acer netbook - same specs as yours.

I suggest pre-testing several versions on Live USB using these instructions - if a version runs decently on USB it will run even better from your HDD:

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

My netbook experience is that the move from version 10 to version 11 of Ubuntu and its variants was a major change in resource demands, similar to the move from XP to Vista in Windows.  The new Ubuntu is primarily designed for higher spec hardware and so be it - even though others here are correct that the lighter weight interfaces for 11.x run better on little netties, none of them run as well as Ubuntu 10.10 and its lightweight variants.  

Also be aware that it's worth spending some time learning your way around Linux on the very newbie-friendly Ubuntu desktop version before installing the lightweights, because while snappier, they are also cruder and less helpful for anyone moving from Windows.
I've used Ubuntu 10.04 and loved that and that is the reason I'm switching...I'll try Xubuntu.

---

### Post by Paqman on 2012-03-09
> **poshin said:**
> The 2D is also slow.  Guess my netbook is too old for it.

It probably won't be much quicker on Xubuntu then. I can't comment on Lubuntu, as I've never really used it, but I suspect you'll find the same thing. If Unity-2D is slow then your problem probably isn't a lack of RAM.

Bear in mind the apps you choose to run make more of a difference than your DE. Big fat packages like LibreOffice will be just as slow on X/Lubuntu as under Gnome. Instead use a web app or something like Abiword and Gnumeric.

The only thing I've done to my netbook is swap out the nasty old 5400rpm magnetic drive for one of the budget SSDs (Intel X25-V), and it made a huge difference. I haven't found the need to boost the RAM, Unity-2D runs well on 1GB. More RAM is never a bad idea though if you've got the money, as you can always start doing things like using it for ramdisks, and it'll prevent the machine swapping to disk if you do use up the RAM.

Whatever DE you use, installing [preload]("apt:preload") might help the machine be a bit more responsive, but it takes a few days of use before it starts to have an effect. I'd also [reduce the swappiness]("https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F") of your machine, Ubuntu's default is way too high.

---

### Post by Odyssey1942 on 2012-03-09
Poshin,

I recently built a new quad core 16GB computer and installed 11.10 on it. After spending a horrified day (thinking why, why, why are they doing this?) trying to get it set up so that I could use it, I chucked it, beat a hasty retreat, and did a clean install of 10.04, which is the power house version that I have been using on my older computer.

I stayed with 10.04 because it is the best O/S and productive interface I have found, and because it is LTS. Cannot stand Unity or any other Apple type interfaces.

Having said that, 10.04 is going to require more resources than the netbook is going to be able to provide. I went to a new 16GB computer because 8GB was not enough for my work style.

---

### Post by poshin on 2012-03-10
> **Odyssey1942 said:**
> Poshin,

I recently built a new quad core 16GB computer and installed 11.10 on it. After spending a horrified day (thinking why, why, why are they doing this?) trying to get it set up so that I could use it, I chucked it, beat a hasty retreat, and did a clean install of 10.04, which is the power house version that I have been using on my older computer.

I stayed with 10.04 because it is the best O/S and productive interface I have found, and because it is LTS. Cannot stand Unity or any other Apple type interfaces.

Having said that, 10.04 is going to require more resources than the netbook is going to be able to provide. I went to a new 16GB computer because 8GB was not enough for my work style.

I followed your advice and have installed Ubuntu 10.04 LTS and it works perfectly well and for somehow like this UI better...  Going to stick with this.
:D :D

---

### Post by poshin on 2012-03-10
I decided to stick with Ubuntu 10.04 rather than try XUbuntu and KUbuntu...and downloading the ISO file and mounting it with Magic Disk and installing just is so much easier than following that Windows Explorer - Wubi.  

Am pleased with Ubuntu 10.04 and long live FOSS!

---

### Post by disabled20191128 on 2012-03-10
try lubuntu

---

### Post by I2k4 on 2012-03-10
> **Dennisgre said:**
> try lubuntu

I'm using Lubuntu 10.10 happily now, as above, because it's so snappy and clean as a pure OS, but can perfectly understand Poshin's choice.  The full Ubuntu is more user friendly, and the marginal performance difference may not be so important.  

Lubuntu's default pre-installed software was not the best for me - I spent (wasted) a lot of time replacing the browser, other programs, and learning how to configure that amazingly crude little panel clock.  I installed Lubuntu before becoming aware of Mint, which for my preferences has a better selection of preinstalled software (though Mint LXDE has an even more ridiculously crude panel clock, that makes you use a terminal command to install internet time-setting - OMG - for better or worse it's these little distro weirdnesses that stick in your mind.)

---


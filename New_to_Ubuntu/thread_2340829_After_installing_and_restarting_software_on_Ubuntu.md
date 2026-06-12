---
title: "After installing and restarting software on Ubuntu, the software is gone (XAMPP)"
date: 2016-10-22
forum: New to Ubuntu
---

### Post by bpinvest on 2016-10-22
Hi,

I successfully install XAMPP as per all of the Ubuntu online guides; start Apache, mySQL, etc.  

It all looks good.

Then I restart my machine (dual-boot, Vista & Ubuntu 16.04) and everything has gone !

i.e. 
/opt/lampp directory is gone
the downloaded xampp file is gone

I even made a temporary directory called /testdir (using "sudo /testdir") and this was gone when I restarted the machine.

I installed the software from a "Terminal" window

The user directory prompt shows "ubuntu@ubuntu$"

It's as though I am creating everything in a Virtual Machine and when the machine is closed down, everything gets reset when I restart the machine.

Is this permissions related?  

I didn't think it could be because I am able to install the software successfully using "sudo" but it's as though it's only permitted temporarily.

Can anyone help?  

Many thanks in advance, 

bpinvest

---

### Post by coffeecat on 2016-10-22
If your terminal prompt is "ubuntu@ubuntu $" then likely you are running a live session and any software installation, changes or new directories you make will be lost when you shut down.

So what do you mean by "dual-boot, Vista & Ubuntu 16.04"? Usually, a Windows/Ubuntu dual boot means the two operating systems installed permanently in different partitions on the internal hard drive(s) of the machine, each operating system selectable from the GRUB menu when you first boot up.

A live session is when you burn the image of an Ubuntu ISO onto a DVD or flash USB drive and boot up from that, instead of from the internal hard drive. Perhaps you can tell us more about how you "installed" your Ubuntu system.

---

### Post by rev-matthewagilmore on 2016-10-24
I have a few questions. when you log inn to your  Ubuntu that is duel booted with vista( vista really vista. anyway) is your username ubuntu.
2. I was xamp on ubuntu in a virtualbox I don't think chmod 777 work on xamp. you can give it a try. but I know you will want to  use chmod 777 on what ever folders you put in htdoc when i mean folders i mean if you make a folder in a folder use chmod on it. side note chmod 777 make everyone be able to read and right from chmod has other numbers that can be usr after it that you should look up in your spare time. 
3.if u do sudo su(this will log you in as root in the terminal) if you start the file manger in the terminal click back on the terminal and hit
 ctrl +z after that type bg  then press enter.  the type disown.
( now you have a file manger  has root permissions be careful only mass with the files you create in htdoc and do not let know one touch your laptop will that fill manger has root privileges they can deleted your whole computer with a few clicks. since you loged in to root  you mght as will start  xamp   do the  same thing  ctrl+z  bg  then disown.
oh if  you do  open up  a text editor in   the filer manger   keep in mind the file manger will have  root privileges to .

---

### Post by bpinvest on 2016-10-25
Many thanks Coffecat for coming back to me so quickly.  Apologies for the delay.  (Mum has been unwell.)

I installed Ubuntu using:

- An ISO file on my hard disk
- UNetbootin

When I start the machine, I get two options:

- Vista
- UNetbootin


I didn't use a DVD or USB drive because I didn't have one available.

Do I need to do something special if I install from the hard drive (C:) ?

From your response, and what I expected, was to be given Vista and Ubuntu options when booting-up the machine.  But I don't.

I get Vista and UNetbootin.

Is that the problem?

Strangely, though, all of the OS files remain after shutdown.  It's only software installs post OS "install" that's the problem.

Does that make sense?

Many thanks again,

bpinvest

---

### Post by bpinvest on 2016-10-25
Many thanks [[COLOR=#000000]rev-matthewagilmore[/COLOR]]("https://ubuntuforums.org/member.php?u=2020085")

Does my response above explain what I did to install linux?

---

### Post by ian-weisser on 2016-10-25
bpinvest, your response explains the problem.
Your response confirmed coffecat's suspicion. 

You did not install Ubuntu. You merely placed a snapshot of an Ubuntu system onto your hardware.
The snapshot is read-only. When you shut it down, all changes are lost.

Invest in a USB stick or a single DVD-R, and follow the installation instructions, if you want to really install a writable, persistent install of Ubuntu.

---

### Post by yetimon_64 on 2016-10-25
> **bpinvest said:**
> ...
Does my response above explain what I did to install linux?
You say your options are ...
> - Vista
- UNetbootin
 and from your first post your ubuntu prompt is ...
> ubuntu@ubuntu$

You are booting from a live image from an iso most likely stored in your windows drive. I didn't know that was actually possible to do with unetbootin but it sure sounds like it from what you are reporting.

I boot iso images directly from an external drive, using such for both installations and as tooldisks, but actually do it from a grub boot loader not from windows.

This would fully explain why you completely lose all added applications but note "all of the OS files remain after shutdown" (they are freshly loaded from within the iso image each new boot, but anything additional is automatically lost with a reboot). This is all typical behaviour for a live image boot.

---

### Post by coffeecat on 2016-10-26
> **bpinvest said:**
> 
I installed Ubuntu using:

- An ISO file on my hard disk
- UNetbootin

When I start the machine, I get two options:

- Vista
- UNetbootin


As ian-weisser and yetimon_64 have pointed out, you have not installed Ubuntu at all. You are simply using unetbootin to boot into a live session of Ubuntu in which any changes you make will not be saved. You need to understand what a live session is. Unfortunately the Ubuntu community wiki page is incomplete, neglected and out of date, but I'll link it anyway:

[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

It's titled "Live CD" because that was the traditional way of doing it. These days, Ubuntu ISOs are too big to fit onto a CD and a DVD can be used instead. Or a USB flash drive where the computer permits booting from USB (only a few old machines don't). Or some other way such as you have found with unetbootin.

Here is a wikipedia article which is a little more up-to-date but which is about live-Linux sessions generally, not specifically about Ubuntu.

[https://en.wikipedia.org/wiki/Live_CD](https://en.wikipedia.org/wiki/Live_CD)

I think you need to think about what it is you want to achieve and then start a new thread asking for help with this. A new thread will be better - a different question and a fresh thread. Setting up a dual-boot demands some preparation, particularly the first time. Fortunately for you, your Windows version is Vista which almost certainly means that you have a legacy BIOS rather than the newer UEFI BIOS, which adds its own layer of complexity for preparing a dual-booting system. (I mean, fortunate that you have a legacy BIOS, not fortunate that you have Vista! :wink:)

Off the top of my head, these are some of the things you need to think about or prepare for, but there may be others I haven't thought of:

[list][*]Backup your Windows system and backup your data. You will be manipulating partitions which always carries a risk with it. You **must** back everything up first.
[*]Get a DVD-R or USB flash stick for burning the Ubuntu ISO to. If you don't know how to do this, members here can help you when you start a new thread.
[*]Before you install Ubuntu, shrink your Windows partition (if this is necessary, which it almost certainly is) using Windows' own inbuilt tool in Vista. Do **not** let the Ubuntu installer do this for you, even though it will offer to. If you do, you risk making your Vista system unbootable. Again, members here can help you with this.[/list]

Good luck!

---

### Post by bpinvest on 2016-10-27
A very big "Thank You" to everyone for explaining the errors of my ways ;-)

Just to say, that I have a 250GB USB Drive that Partition Magic would not let me partition AND install a different OS on the new partition. 

(The error escapes me right now.  I just remember being bemused at why I couldn't install to the new partition.)

Anyway, many thanks again.

I'll have to either get my current USB drive working or invest in a new one.

Kind regards to you all,

bpinvest

---


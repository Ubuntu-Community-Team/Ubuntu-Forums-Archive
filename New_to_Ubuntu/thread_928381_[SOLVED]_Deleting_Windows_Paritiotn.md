---
title: "[SOLVED] Deleting Windows Paritiotn"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by msohn88 on 2008-09-23
I am now officially decided to use Ubuntu.

I asked "computer guy" in my class who introduced about Linux.

He said

I need to find out
1) what BIOS I have
2) have exact model info of labtop
and 3) figure out which exact wireless card I have

I have no idea how to do these... anybody can help me with this?

Thank you.

---

### Post by digitzero on 2008-09-23
BIOS isn't so much important.  What is the brand and model of your laptop?  You may want to search that model number in these forums.

---

### Post by jemate18 on 2008-09-23
Before switching totally. You might want to try ubuntu first.


Download it from [www.ubuntu.com](www.ubuntu.com)
burn it to a CD
and boot it.

(You need to set your BIOS to boot first FROM CD/DVD Drive)

After booting, you will be logged in.. Just try it first and if you decide to install it, click the Install icon in the desktop.

---

### Post by lisati on 2008-09-23
I wouldn't worry too much about those details, just yet. If you have a copy of a "Live CD" you can have a play with Ubuntu without actually installing it. That way, you can find out what works, and what doesn't work.

The amount of RAM available probably matters more than the particular version of BIOS you have...

---

### Post by msohn88 on 2008-09-23
Well, I am using Ubuntu as my partion.

---

### Post by msohn88 on 2008-09-23
I use Thinkpad T42. Is that all I need?

---

### Post by msohn88 on 2008-09-23
I don't want Windows. It's tooooooooooooooo slow.

---

### Post by kansasnoob on 2008-09-23
Step #1: burn or order the Live Cd. 

Step #2: Run the Live CD ....... a lot!

Start here:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

---

### Post by jemate18 on 2008-09-23
> **msohn88 said:**
> I don't want Windows. It's tooooooooooooooo slow.

To use LiveCD you should at least have

1. CD/DVD Drive
2. 256MB RAM (But this will be slow)
3. Pentium III or equivalent or greater (to be fast)

greater than 512MB will WORK.......

---

### Post by msohn88 on 2008-09-23
Is there any way I can *just* run Ubuntu without running CDs?

---

### Post by jemate18 on 2008-09-23
> **msohn88 said:**
> Is there any way I can *just* run Ubuntu without running CDs?

Technically yes, after you have installed it via virtualization 

Download XVM from [www.sun.com](www.sun.com) and install it.

You need at least to have downloaded the ISO of ubuntu.

Then run xVM and create new OS, then select the ISO of ubuntu to be able to install it......

BUT RUNNING IT WITHOUT VIRTUALIZATION AND WITHOUT CD?

I DONT THINK IT IS POSSIBLE? HOW WILL you be able to load the files? and what location will the files be fetch to be able to run it without cd?

---

### Post by lisati on 2008-09-24
> **msohn88 said:**
> Is there any way I can *just* run Ubuntu without running CDs?

If you want Ubuntu to replace Windows completely, you'll have to install it (ubuntu or whatever). Although there are alternative installation methods, I prefer having it on CD, which isn't needed once the installation is complete.

---

### Post by msohn88 on 2008-09-26
Sorry if my reply was too late.

But will be better to run with CD.

It won't use Windows format -- such as my wireless problem...

I mean, what I am asking is that can you 100 % use Linux with CD that has no files from Windows?

---

### Post by davidryder on 2008-09-26
If you have any other wireless card besides Intel you will most likely spend a lot of time getting it to work. 

You can find out what card you have installed with 

```
lspci | grep net
```

---

### Post by -Zeus- on 2008-09-26
> **msohn88 said:**
> Sorry if my reply was too late.

But will be better to run with CD.

It won't use Windows format -- such as my wireless problem...

I mean, what I am asking is that can you 100 % use Linux with CD that has no files from Windows?

Yes, you can completely remove Windows and Linux will work fine.  Just download the live cd from ubuntu.com/getubuntu/download and burn it to a CD, then boot to the CD, install, and windows will be replaced with Ubuntu

---

### Post by msohn88 on 2008-09-27
How do I know if I can still use the wireless card and graphic card and such?
Don't you need to know what BIOS I have to run Linux?

Thanks.

---

### Post by Seine on 2008-09-28
To run the CD, you don't need to run windows. If you have the CD in your drive and have changed the boot order in your BIOS settings to run from CD first, then the CD will run itself when you reboot.

Do this, and you can *try* Ubuntu without changing anything on your computer. You will be able to tell if it works and if you like it. If you want to install it properly after that you can click the install icon on the desktop.

---

### Post by Presto123 on 2008-09-28
You want my opinion? I would really suggest DUAL booting, which is not that hard to do. What this will do is shrink the Windows partition to whatever size you wish and is within reason of that partition and you will also have Linux. 

See, Windows and Linux do not use the same files for operating, so, you can run Linux at it's pace without needing ANYTHING from Windows, while still having a backup if you decide to change your mind.

Frankly, my laptop is this way, but not on the basis that I might change my mind, but on the basis that there are still SOME things I want Windows to run (mind you, that this is very few things, but still).

---

### Post by Presto123 on 2008-09-28
If you like that idea above, let us know how much hard drive space you have and we can probably help. 

I know that something like dual booting SEEMS very complicated as it did to me, but, Ubuntu is very straightforward about it. Just know that if you have ANY questions while doing anything, don't rush into it, take a little time and try to get some information about what you are doing.

---

### Post by msohn88 on 2008-09-28
Well, I am doing the DUAL buting like you said.

However, my friend suggested me to use ONLY Linux on the computer since people can still keep tracking my infomations since I am still using Windows, whatever that means.

---

### Post by msohn88 on 2008-09-28
So, when I put the CD on this disk and start up the computer, Windows will be deleted and Linux will be installed?

---

### Post by Excalibre on 2008-09-28
> **msohn88 said:**
> Well, I am doing the DUAL buting like you said.

However, my friend suggested me to use ONLY Linux on the computer since people can still keep tracking my infomations since I am still using Windows, whatever that means.
Well, your friend is either lying or doesn't know what he's talking about. Having both Windows and Ubuntu on the same computer at the same time is perfectly fine, and when you're running Ubuntu you're not going to face any of the potential security risks associated with Windows. The fact that it's sitting on your hard drive doesn't matter.

The reason people keep suggesting you play with a Live CD first is that it's the easiest way to figure out how well things will work -- you stick the CD in, run Ubuntu, and don't risk screwing up anything you already have. And if you put in the Live CD and your wireless card and video work automatically, you'll know you won't have to worry about that. If they don't, you'll know what exactly you have to do research on. Also, your friend is incorrect about the BIOS thing -- that's not something that's a significant concern at all.

If you decide to remove Windows completely without even trying out Ubuntu first, you may well discover that basic hardware doesn't work at all, and if your video card or wireless don't work, you won't be able to get on the web and do the research you'll have to do to make them start working.

I'm not clear on exactly what you're aiming for -- if you already have Ubuntu installed, and it's working fine and you're happy, you can easily remove Windows using something like GParted. It's there on the Ubuntu Live CD -- you boot off the CD, run GParted (System menu > Administration > Partition Editor), and delete your Windows partition. Then you expand your Ubuntu partition to fill that space (you can't do this while running Ubuntu off your hard drive -- you have to use a Live CD for that.)

But there's no big reason to do this unless you really need more space for your Ubuntu partition. Having Windows around may be useful sometime when you need to run some piece of software that doesn't have a Linux version. Windows is not going to expose you to some great risk just by sitting on your hard drive.

---

### Post by msohn88 on 2008-09-28
Thanks. 

I do like Ubuntu, but sometimes I do like to use Windows.

One more question though, when I turn on the computer, it let me decide which OS I want to learn, and it's set up as Windows. Is there any ways I can set up Ubuntu as default?

---

### Post by Excalibre on 2008-09-28
> **msohn88 said:**
> One more question though, when I turn on the computer, it let me decide which OS I want to learn, and it's set up as Windows. Is there any ways I can set up Ubuntu as default?
Yes. The instructions below look long, but it's really not hard.

First, reboot your computer and look at the grub menu that pops up. Find the menu choice you select in order to start Ubuntu, and take note of where it is in the menu -- I think by default it's the first item on the menu, but it might not be for you.

/boot/grub/menu.lst is the configuration file for the Grub bootloader, which is what actually starts your operating system -- it's the thing that pops up that menu when you turn your computer on, where you choose Ubuntu or Windows.

It's a good idea to back this file up first, since your computer won't start if it gets screwed up. In a terminal window, type "sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup". Then, if something does go wrong, you can boot with the Live CD and copy the backup over the damaged copy.

Open it up (type in the terminal window "gksudo gedit /boot/grub/menu.lst"). Look through the file -- right near the top will be a line that says

```
default 0
```

That means that the first menu item (it counts starting with zero, not one) is the menu item it'll boot. Change that number so it matches whichever menu item Ubuntu is -- remember to subtract one, so if Ubuntu is the third item on the menu, change it to 2. (If for whatever reason 'default' was set to something other than 0, that doesn't matter. Just change the number to the appropriate one. If there was no default line at all, add it at the very top of the file, with the appropriate number.)

If this doesn't make sense, post your /boot/grub/menu.lst file here and someone will be able to tell you exactly what needs to be changed.

---


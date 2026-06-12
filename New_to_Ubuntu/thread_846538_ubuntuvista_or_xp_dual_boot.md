---
title: "ubuntu/vista or xp dual boot"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by badperson on 2008-07-01
Hi,

I've been using ubuntu for four or five months now, and I really like it, but I'm in a situation where I really need to use photoshop, so I thought I'd dual boot my machine with either vista or xp.

I did a search here and google, and found some good hits (including the official documentation site), but still had a question. 

My machine (running ubuntu) has two hard drives, and I'd like to use one for ubuntu, one for vista or xp. The documentation on the official ubuntu site gives partition instructions, but with two HD's, I don't really need that, do i? 

I would mainly be using ubuntu, I'd want that to be the default, I'd really only use the windoze machine for photoshop. 

Also, I'm wondering if upgrading to vista is worth it; I'd like to work with it, but am not eager to shell out $300 for it, so I may decide to do xp. Anyone have any particular likes/dislikes with vista? 

One more thing...I wasn't able to install compiz or any of the cool desktop stuff on my ubuntu drive, I think because of video or graphics card...I may want to replace the card, but I don't want the graphic stuff so bad that I'm willing to get into a bunch of compatibility nightmare issues...


I'm running ubuntu 7.10 now, and while it is a slight PITA to reconfigure my ubuntu machine and completely start over, I'm willing to do it if the upgrade to 8.04 is worth it. any opinions on that? 

thanks, 
jason

---

### Post by aktiwers on 2008-07-01
Why dont you just install XP through Vmware ontop of Ubuntu? This way you dont have to reboot the machine to use Windows.

Here is a link for a good Howto:
[http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)

Or even better, use VirtualBox instead of Vmware, and run it seamless:
[http://ubuntuforums.org/showthread.php?t=433359](http://ubuntuforums.org/showthread.php?t=433359)

---

### Post by badperson on 2008-07-02
that looks really good, but I did want to get some experience dual booting.
Also, and this may be a complete prejudice on my part, I had the idea that dual booting was more stable and less bug prone, but that's totally anecdotal on my part, not sure if it's true. 

Also, the other thing is that I don't have a postscript compatible printer right now, I just have one of those POS dell aio printers that came with my laptop, so I'd like to be able to print with that from Vista or XP (not sure which one I want to use yet)

anyone have any direct experience dual booting with 2 HD's? 

thanks, 
bp

---

### Post by benfindlay on 2008-07-02
Have you checked to see if the features you need in photoshop are in GIMP? If so, then theres no need to run windows at all. Try a general google search for the names of the photoshop features you need along with the word GIMP, as they may be under a different name in GIMP.

Hope this helps!

---

### Post by bumanie on 2008-07-02
If you decide to dual boot, it is best to have windows on the first partition of the first/primary hard drive. Have a look at gimpshop - it has been designed with a gui similar to photoshop so that those familiar with photoshop find the transition to gimp easier.

---

### Post by theravenproject on 2008-07-02
For starters YES the upgrade to Hardy Heron is worth it.  I waited and used Dapper Drake up until the last week and man I am glad I upgraded-I chose fresh install.  As for Dual booting-Personally your windows OS is a matter of Personal Preference bro-From what I understand Mcrsft is improving driver support etc so Vista isn't what it was when it first came out and everyone was attacking it but XP is still that "Rock Solid Windows" OS; my fav Windows personally-I only use Win for cerain games these days (I Hvae a War Machine for a Computer!) and for everythingelse I use Linux!  

     As far as installing them on seperate HDD's or using Vmware...Personally I suggest doing what you want to do and setting up your dual boot system...You can get Linux to support NTFS filesystems so you can manipulate yourt Windows files etc..In the end it is up to you but good luck and happy hacking dude!

---

### Post by Sef on 2008-07-02
Read the [Illustrated Dual Boot]("http://users.bigpond.net.au/hermanzone/p14.htm").

---

### Post by badperson on 2008-07-02
cool, thanks for all the links!

as for gimp, I do use it, but I want to be able to do both. Regardless of how good gimp is, photoshop is still the lingua franca of digital editing, and I wouldn't want to completely rely on gimp; not for technical reasons, but I wouldn't want to be completely isolated from the mainstream of digital editing. I'm taking a class now, and they cover photoshop, although most of the stuff I'm learning I can translate into gimp. 

Also, I want the experience of dual booting. Will read the links, thanks again. 
bp

---

### Post by kansasnoob on 2008-07-02
"The documentation on the official ubuntu site gives partition instructions, but with two HD's, I don't really need that, do i?"

The info you absolutely must understand is how GRUB handles things. A good place to start is here:

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Whether you're using one hard drive or two you're going to have to make some adjustments in your GRUB menu.lst. Consider two different scenarios:

#1. You leave both hard drives plugged in and install Windows to drive #2: Windows will "overwrite" GRUB and you'll have to restore and edit GRUB to make Ubuntu boot again.

#2. You physically disconnect drive #1 (which contains Ubuntu 7.10) and install Windows on drive #2. This would be my personal preference of the two, but you'll still need to edit your grub/menu.lst to make Windows bootable from GRUB.

Now simply as a matter of personal preference, and considering that you're just wondering about changing to 8.04, I'd disconnect the 7.10 drive (this assumes you're comfortable fiddling with hardware) and install Windows to half (more or less) of the vacant drive (another reason for this is to have Windows recognize itself as Drive C). Then I'd reconnect the 7.10 drive and do a fresh install of 8.04 on the half (more or less) of the windows drive ................... or:

Create a vacant partition of 10GB (more if you wish) on the 7.10 drive, and then disconnect the 7.10 drive (again assuming you're comfortable fiddling with hardware) and install Windows to the entire vacant drive. Then I'd reconnect the 7.10 drive and do a fresh install of 8.04 on the 10GB partition that we created earlier.

The one great advantage to this would be that the new 8.04 install will create a new GRUB menu, and with both drives plugged in it'll recognize all of the OS's, so you'll have a fresh Windows install, a fresh 8.04 install, and your known working 7.10 install to fall back on while you work out any issues with 8.04 and/or Windows.

Installing startupmanager from synaptic will easily let you choose which OS to boot at startup and several other options, and once you get 8.04 working smooth you can just use Gparted (live from the Ubuntu CD) to delete your old 7.10 partition.

But you could ask ten people and get ten or more preferred scenarios:)

Just a note: Don't fiddle around disconnecting or reconnecting drives without properly shutting down and "powering off" your computer and always follow "anti-static" precautions!

---


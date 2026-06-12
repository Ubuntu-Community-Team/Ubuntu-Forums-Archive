---
title: "anyone know about gaming in ubuntu??"
date: 2011-09-28
forum: New to Ubuntu
---

### Post by imachavel on 2011-09-28
ok I'm new here. I'm sure you guys have gotten a billion threads like this asking about wine and gaming etc. etc. etc. blah blah blah, I don't want to take up the time of the forum for hours asking questions about wine and gaming. also, I don't want to start asking questions that are beyond the scope of this forum. but still, let me explain my predicament any way and let's see if there isn't some stuff that maybe people have encountered before.

so I was dual booting ubuntu and windows xp, and the grub got messed up, and the /dev/sda1 or /dev/sdb or whatever it is got tired of sharing the grub files with windows, and windows wouldn't load, I tried using the windows recovery disk and using fixmbr and a few other commands to try and fix it, it seemed as though it was working, but to no avail. then I went online and a nice person helped me by purging grub2 and installing a legacy grub. this made it even worst. long story short I got tired of windows problems and am a linux newbie, so I went ahead and just did a fresh install with ubuntu natty narwhal version and then downloaded virtual box and installed it and had my original oem .iso windows disk, installed that in a virtual machine.

linux seems simple enough, had to get a video codec even though I installed vlc media player, also the updates aren't too bad, sudo apt-get install update? anyway this was all simple enough, a bit of a hassle but hey, go use windows and then complain about a hassle right?

also I installed an hd 4670 radeon graphics card in the pcie slot before I reformatted with linux. Now gaming in linux is a PAIN

you have to use wine, so I installed it. but then you can't open files unless you mark them as executable. so how to play a game on a two game disk like call of duty? well take the files off the disk and put them in a directory silly. then mark them as executable. first problem, when second install disk is needed, you can't eject the 'disk' because it's really a FILE. so I couldn't get any further with that, had the second install disk files in a separate folder. obviously the game is made for windows all the files are .exe and .ini etc.

so here we go I thought "assign 128 mb video ram to the virtual machine, play call of duty in virtualbox xp" bad idea, the game installs just fine, but trying to play it is another story, the mouse keeps DRAGGING across the screen. so I also installed urban terror to see if it worked any better. no go. same thing, mouse drag non stop.

so I went to virtualbox forums, they took a look at some of my log files, and had me uninstall a few usb filters, which I needed but they said I had too many installed. also guest extensions couldn't be found, which they told me I needed to install as well. not guest additions, that was already installed.

anyway I know this isn't a virtual box forum, so not TOO much help I can get here on that, I've heard virtual box is just bad for gaming. too bad, oracle makes like the best software in the world, oh well virtualization even though it's apparently revolutionary, has it's limits does it not. shared memory and processor usage takes it's toll. shared usb's, shared disk, shared d: drive all that sharing I guess means not enough power and memory shared to the board to run so many peripherals and drives and hardware etc. oh well

so back to ubuntu, I wanted to see if a one game disk would work in ubuntu. I installed metro 2033, had to install steam service as well. same thing download it, install it, mark as executable. but then steam has to open before ubuntu can play the game. I guess wine doesn't like steam, because when I open metro 2033, steam opens, and the game appears to be loading, then nothing happens.

next part, I tried installing a game that doesn't use steam. I downloaded the crysis demo, installed it, marked it as executable. when I open it it appears to be loading, but then nothing happens, no error message, just nothing happens. if I try opening it again, it says "the crytek process is already running, do you want to open it again?"

anyway, I heard a rumor online that the reason that ubuntu natty narwhal works so buggy is because gnome shell was replaced with unity or something like that. I don't know maybe that's a rumor has ubuntu always been this buggy? I used open suse one time and man it sure as **** was buggy, WAY buggier then ubuntu natty narwhal.

on a positive note, the new ubuntu 10.4 has a much nicer sidebar feature for accessing applications and what not, and the search feature seems improved as well. maybe I'm wrong, but it's nice to see that you can configure ubuntu to look and act a bit like mac. but why wouldn't you be able to? steve jobs ripped off linux anyway when he wrote the fs file system, I hear he stipped off the front end and the back end was mostly the linux program when we wrote the os. or wait was it called the hfs file system back then? probably not, kind of like ms dos migrated to fat32 which migrated to ntfs. oh well

---

### Post by haqking on 2011-09-28
In short if you want to play games then stick with Windows or dual boot, even in a VM you wont get full hardware support.

seeing as you didnt ask a specific question that is all i can offer right now.

I know alot of people here will say the same thing, if you want games support then use windows

---

### Post by LinuxFan999 on 2011-09-28
There are a lot of open source Linux Games.
There is a list here: [http://en.wikipedia.org/wiki/Linux_gaming](http://en.wikipedia.org/wiki/Linux_gaming)

---

### Post by lolpenguin on 2011-09-28
Run the installer in Wine. It should work. So many games do.
Some popular games that work:
Final Fantasy XI, World of WarCraft, Guild Wars, Left 4 Dead, Counter Strike, Warcraft III, Half-life, StarCraft, StarCraft II, Team Fortress 2, Bioshock, Warhammer, Command and Conquer 3, Battlefield 2, Assassin's Creed...
And SO MUCH MORE!
I use Natty too, by the way. You don't need to set executable permissions if they are executable in the first place. Unity (the dash and panel and etc.) is a shell for GNOME. Don't use virtual machines, they will be very slow.

Like haqking said, if you really need to play games THAT much, it's better to get a dual-boot system (I do).

---

### Post by imachavel on 2011-09-28
thanks for the awesome advice. just an update, I know it's awesome advice to stick with executable properties and open things with wine in linux. I ran the installer in wine, no game yet has had any problem installing in wine except call of duty because etc. etc. two disk install issue

the problem isn't installing, but USING and RUNNING the game. anyway, it's no big deal. I've been having fun with linux, I designed a web site using bluefish editor editing the html, and uploaded it to godaddy, had to resave it as index.html, but now it works great and I can see it on the web at it's domain url.

anyway, I don't want to bore people drudging about what a pain linux is to use. so far it's performed MUCH better than windows, so I can't complain. I know linux is going to control the earth one day, it already from what I've heard the internet is mostly unix server file systems apache and what not. we all know the next linux distro is going to be as simple to use as windows xp and it's going to wipe windows off the map in terms of applications and performance ;)

---

### Post by anewguy on 2011-09-28
For your gaming issues, a couple of notes:

- Wine will never perform as well as Windows for a game.  Neither will Windows within a virtual machine

- you should probably try posting this in the gaming and leisure forum - that's where all the gaming information and users are for the most part.

good luck!

Dave ;)

---

### Post by Sunfist on 2011-09-29
I have been fighting this battle for years and all I can tell you is what others have said, ultimately you almost HAVE to run a full version of windows if you want the majority of games to run decently. I actually bought an older used computer on Ebay JUST to run games on and use my Linux machine for everything else. If you are really determined to run windows games under Linux I have found that a Linux/Wine program called Crossover seems to work a lot better than just wine by it's self, at least it includes an installer than usually does a fairly good job of installing the games for you, but even then the results vary, some games will run pretty well under Linux and others still have problems.

---

### Post by carverj on 2011-09-29
I have a dual boot with Windows.
I have some games successfully installed and running great in Linux and some running in Windows.
I also use Windows Media Player to play .wmv movies as I cannot run them in Ubuntu. It is great to have two completely different Operating Systems on different partitions. And Linux can access the windows files with ease.

---

### Post by iiiears on 2011-09-29
Steam doesn't work reliably in windows. See their rev. history for 
"Patched online mode" its become a running joke.

If you haven't tried "play on linux" it might be worth a shot. Though the idea of installing windows exe and other binaries from the authors site implies a significant level of trust that what you asked for is what you got.


Your best option is to dual for boot anything with DRM.

Your question will get more informed answers in "Leisure and Gaming"

Next Up. "How do i install GFWL on Ubuntu?" 

Best Wishes.

---

### Post by 3rdalbum on 2011-09-29
I know your problem isn't with installing Windows software on Linux, but I thought I'd share a handy hint.

As you've noticed, you need to set the execute permission on any Windows programs before you can run them. This also includes installers on CDs, where obviously the CD filesystem and its permissions can't be changed.

You can get around this by going to the terminal, typing *wine* and leaving a space character at the end, and then dragging the program into the terminal window. Click in the terminal window again to bring it to the front and then press Enter. The program will load.

This doesn't solve your problems with Wine, of course; but if you ever want to try installing a Windows program again to run in Wine, this is quicker and easier than copying the CD to the hard disk.

**Just be careful of what you run.** Some Windows viruses might actually be able to run in Wine and be able to set themselves up to run whenever Wine is started. Don't run anything that sounds suspicious or "too good to be true", and don't run anything that you suspect is infected or has come from an infected Windows system.

---

### Post by 3rdalbum on 2011-09-29
I know your problem isn't with installing Windows software on Linux, but I thought I'd share a handy hint.

As you've noticed, you need to set the execute permission on any Windows programs before you can run them. This also includes installers on CDs, where obviously the CD filesystem and its permissions can't be changed.

You can get around this by going to the terminal, typing *wine* and leaving a space character at the end, and then dragging the program into the terminal window. Click in the terminal window again to bring it to the front and then press Enter. The program will load.

This doesn't solve your problems with Wine, of course; but if you ever want to try installing a Windows program again to run in Wine, this is quicker and easier than copying the CD to the hard disk.

**Just be careful of what you run.** Some Windows viruses might actually be able to run in Wine and be able to set themselves up to run whenever Wine is started. Don't run anything that sounds suspicious or "too good to be true", and don't run anything that you suspect is infected or has come from an infected Windows system.

---

### Post by mastablasta on 2011-09-29
> **anewguy said:**
>  
- you should probably try posting this in the gaming and leisure forum - that's where all the gaming information and users are for the most part.
 

 
actually there is a separate wine forum for wine related issues and programmes running on wine.
 
Also urban terror has a linux verison i belive.
 
Something is wrong in the way you installed programmes. some programmes need tweaks hence people here advised playonlinux (wine frontend) that already has them. another option is to use wine site to get more information on install (also on multiple cd installations).
for example call of duty instructions: [http://appdb.winehq.org/appview.php?iVersionId=3603](http://appdb.winehq.org/appview.php?iVersionId=3603)
 
for plenty (especially a bit older games) wine works just fine and you won't even notice that you are in linux anymore.
 
also to get some error report in wine you should run it via terminal by:
 
wine yourgame.exe

---

### Post by iiiears on 2011-12-25
Never as simple as a Windows Program on Windows but if you are patient and enjoy discovering how things work most things will work eventually.

For clues.
[http://www.winehq.org/docs/winedev-guide/wine-debugger](http://www.winehq.org/docs/winedev-guide/wine-debugger)

Playonlinux script to grab and install missing libraries.

WineHQ patch and cmake.


It may seem you need a computer science degree at first but most applications fail in a familiar way So, it gets really simple with a little practice.

Have a great day!

---


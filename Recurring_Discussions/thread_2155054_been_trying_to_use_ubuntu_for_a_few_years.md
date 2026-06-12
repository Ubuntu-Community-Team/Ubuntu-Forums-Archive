---
title: "been trying to use ubuntu for a few years"
date: 2013-06-16
forum: Recurring Discussions
---

### Post by billcecil on 2013-06-16
After trying to use ubuntu for several years, I've came to the realization that I must be a complete moron. I had only gotten a printer on linux once, and when the printer went bad, never again. if I try to get help, I hear sudo this, aptget that and none of it makes any sense to an idiot like me. As much as I hate paying billgates three or four hundred bucks a year, and macafee another bill, I give up. I suppose if everyone went to college for a decade to learn this linux stuff, then it wouldn't be free. If it were easy, then everyone would have it. At least with windows you know you're in trouble, just pay another couple of hundred bucks and you're good for a little while.

---

### Post by HermanAB on 2013-06-16
Howdy,

The problem is that Ubuntu is NOT a simple, new user friendly version of Linux.  Ubuntu is intermediate to difficult, compared to other older distributions.

You would be better off starting with Mageia ([http://www.mageia.org/en/](http://www.mageia.org/en/)), PCLinuxOS ([http://www.pclinuxos.com/](http://www.pclinuxos.com/)) or even Puppy Linux ([http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm)).  Those versions have wizards for everything and you literally never have to use a command line.

---

### Post by billcecil on 2013-06-16
Thanks for the quick response.

---

### Post by cincinnatus13 on 2013-06-17
I might throw a line in for PinguyOS too. Based on Ubuntu but complete. Lot of amenities with no real work involved. Truth is, Ubuntu is like having a house built that needs the inside to be furnished.
Others are just foundations and others are complete mansions that require no work.
There's a distro for all tastes.

---

### Post by camurgo on 2013-06-17
I think you should get someone to show you in person the steps you need to take to get things working, in front of the computer. Someone in you can ask "What is this 'apt-get' business all about?" And the person will give an explanation that will neither confuse nor tire you; Also explain to you the meaning of the msgs on the terminal and so forth. Getting things working is about standard sequences of actions for the most part. Don't give up, what's the fun in that? :)

---

### Post by billcecil on 2013-06-17
if there was such a person near me. I used DOS with no problem. I haven't met anyone that runs any Linux. I told myself not to give up years ago.

---

### Post by monkeybrain2012 on 2013-06-17
> **HermanAB said:**
> Howdy,

The problem is that Ubuntu is NOT a simple, new user friendly version of Linux.  Ubuntu is intermediate to difficult, compared to other older distributions.

You would be better off starting with Mageia ([http://www.mageia.org/en/](http://www.mageia.org/en/)), PCLinuxOS ([http://www.pclinuxos.com/](http://www.pclinuxos.com/)) or even Puppy Linux ([http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm)).  Those versions have wizards for everything and you literally never have to use a command line.

I found Ubuntu very easy, when I started I had no knowledge whatsoever on computers, I used Windows xp before that but I was the kind of idiot who didn't know how to set up the simplest things because I wasn't interested in computer stuffs, I just used one or two programs, going on the internet and checking email  and that was it,  I always had to call this guy to ask very simple question for which I am now embarrassed. I couldn't make a partition if my life depended on it. 

But somehow two years ago I picked up a crappy old laptop from a friend and for some reasons that I still can't figure out I came across Ubuntu and live usb (maybe when I was randomly browsing Youtube) and found the idea rather cool, so I started playing a bit, installed Ubuntu on this laptop that no one would miss. It actually worked decently! (It had XP on it but it was so hot and slow that it was unusable) Somehow I was able to get the wifi to work (it wasn't trivial especially for someone with little background, for there was a driver conflict and I needed to blacklist a driver, i still don't know how I figured that out, I didn't know about the forum then) 

It was a very cool experience, and it was not rocket science. :)

---

### Post by mastablasta on 2013-06-17
> **billcecil said:**
> After trying to use ubuntu for several years, I've came to the realization that I must be a complete moron. I had only gotten a printer on linux once, and when the printer went bad, never again. if I try to get help, I hear sudo this, aptget that and none of it makes any sense to an idiot like me. As much as I hate paying billgates three or four hundred bucks a year, and macafee another bill, I give up. I suppose if everyone went to college for a decade to learn this linux stuff, then it wouldn't be free. If it were easy, then everyone would have it. At least with windows you know you're in trouble, just pay another couple of hundred bucks and you're good for a little while.

several years?

so you do know there are a couple of different interfaces (Ubuntu, Kubuntu, Xubuntu Lubuntu to name only a few..)? and you do know that when you asked for help you were given commands that work on all of them? i mean in case somoene else had the same problem all they need to do is use same commands to make it work.

further more you do know you can just copy and paste commands in terminal?! hwo hard can that be?

sudo is command that gives super user privileges and protect you computer from malware.

apt-get is command that gets programmes from repository. 


for both there is a graphics interface.  but see my first point. commands are same on all graphic interfaces, while graphics interfaces are different from one another. so command will work on all interfaces. while giving you GUI instructions (menues, pictures...) will only work on your specific interface which is probably not modified form stock Ubuntu. oh, the selfishness....

---

### Post by monkeybrain2012 on 2013-06-17
I think you can do most things in Ubuntu without command lines. To really make sense of what they mean you may need to read a book. :) I know, I don't like copying long random looking commands without knowing what they do (and it can be dangerous if you copy and paste from dubious sources). Fortunately those situations are rare for common tasks and in many cases you can kind of guess what they do and even remember them.

So if you don't like sudo apt-get update you can use a gui like the Ubuntu Software Centre or much better, synaptic for managing your software. 

sudo apt-get update = clicking reload button on synaptic --> updating repository indices

sudo apt-get upgrade= installing updates from synaptic

apt-get is a Debian thing to manage packages (there is also aptitude) and for other distros you have equivalence such as yum (fedora)

If you use kubuntu then instead of synaptic you should use muon (think that is installed by default) and it is similar.

Sudo is for tasks that involve modifying system files (anything outside your home directory) and if you want to start a gui application as super user (say you want to edit a system file with the text editor), use gksudo, for kde you use kdesudo etc.

---

### Post by billcecil on 2013-06-17
> **mastablasta said:**
> several years?

so you do know there are a couple of different interfaces (Ubuntu, Kubuntu, Xubuntu Lubuntu to name only a few..)? and you do know that when you asked for help you were given commands that work on all of them? i mean in case somoene else had the same problem all they need to do is use same commands to make it work.

further more you do know you can just copy and paste commands in terminal?! hwo hard can that be?

sudo is command that gives super user privileges and protect you computer from malware.

apt-get is command that gets programmes from repository. 


for both there is a graphics interface.  but see my first point. commands are same on all graphic interfaces, while graphics interfaces are different from one another. so command will work on all interfaces. while giving you GUI instructions (menues, pictures...) will only work on your specific interface which is probably not modified form stock Ubuntu. oh, the selfishness....


I suppose you were trying to help.

---

### Post by mastablasta on 2013-06-17
> **billcecil said:**
> I suppose you were trying to help.

there is nothing to help with. there is no request for help, no question, no data provided.: [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475) 

in fact this thread doesn't belong in absolute beginers section.

---

### Post by sffvba[e0rt on 2013-06-17
*Thread moved to **Recurring Discussions**.*


404

---

### Post by Buntu Bunny on 2013-06-17
I think this is why some of us hang on to a dual boot; in case we run into problems we can't solve for ourselves.

---

### Post by HermanAB on 2013-06-17
Anyhoo, the easiest Linux by far is Puppy, mentioned above.  Give it a try.  It is a very light and blazingly fast little Linux.

---

### Post by monkeybrain2012 on 2013-06-17
> **Buntu Bunny said:**
> I think this is why some of us hang on to a dual boot; in case we run into problems we can't solve for ourselves.

If you can make a dual boot you should be able to solve most problems with a little help from the forum. :p

---

### Post by monkeybrain2012 on 2013-06-17
> **HermanAB said:**
> Anyhoo, the easiest Linux by far is Puppy, mentioned above.  Give it a try.  It is a very light and blazingly fast little Linux.

How does being light and blazingly fast have anything to do with ease of use? A system without GUI would be light and blazingly fast but it wouldn't be very easy to use. 

For people who use their computers for day to day tasks, diffiulties may arise in installation, having to get hardware to work and getting the software they need. 

On all counts I think Ubuntu is probably the easist (except for Mint which includes the codecs by default)  On the other hand, installation is not so easy for Arch and sometimes it may be hard to get hardware working with Debian without some tweaks or installing extra components etc and those contribute to difficulties. 

But once you have the system set up and running all distros are pretty much the same (assumming you don't need to trouble shoot and do fancy, 'power user' stuffs) OP complains about having to use command lines, well the commands are the same in all distros (withs small variations like yum instead of apt-get and so on) and since most distros come with GUI and they are all pretty feature completed so chances are you won't even have to use the command line for day to day operations if you have a modern DE.

Overall, you can't get a lot easier out of the box experience than Ubuntu (excpet Mint, with one rather trivial tweak, as noted).Puppy runs on very low spec hardware, but it has nothing to do with ease of use.

---

### Post by montag dp on 2013-06-17
> **monkeybrain2012 said:**
> How does being light and blazingly fast have anything to do with ease of use? A system without GUI would be light and blazingly fast but it wouldn't be very easy to use. 

For people who use their computers for day to day tasks, diffiulties may arise in installation, having to get hardware to work and getting the software they need. 

On all counts I think Ubuntu is probably the easist (except for Mint which includes the codecs by default)  On the other hand, installation is not so easy for Arch and sometimes it may be hard to get hardware working with Debian without some tweaks or installing extra components etc and those contribute to difficulties. 

But once you have the system set up and running all distros are pretty much the same (assumming you don't need to trouble shoot and do fancy, 'power user' stuffs) OP complains about having to use command lines, well the commands are the same in all distros (withs small variations like yum instead of apt-get and so on) and since most distros come with GUI and they are all pretty feature completed so chances are you won't even have to use the command line for day to day operations if you have a modern DE.

Overall, you can't get a lot easier out of the box experience than Ubuntu (excpet Mint, with one rather trivial tweak, as noted).Puppy runs on very low spec hardware, but it has nothing to do with ease of use.I haven't tried Puppy Linux, but I'd like to point out that Herman didn't say or imply that Puppy Linux is the easiest *because* it is light or fast, just that is the easiest and is also light and fast.

---

### Post by MadmanRB on 2013-06-17
Well its well klnown that printers in linux are a bit of a pain to set up.
Its not really the fault of linux though as most companies dont even know what linux is.

---

### Post by 3rdalbum on 2013-06-18
I don't know if Puppy is really the easiest. If "Easy == Very similar to Windows" then I guess it's easy. However, for me, Windows is hard and Ubuntu is easy. And classic Mac OS is the easiest of the lot, and Mac OS X is harder even than Windows.

---

### Post by billcecil on 2013-06-18
> **MadmanRB said:**
> Well its well klnown that printers in linux are a bit of a pain to set up.
Its not really the fault of linux though as most companies dont even know what linux is.
This is what I was doing. Trying for the last time to get a printer to work.

---

### Post by SuperFreak on 2013-06-18
What is the make and model of printer. Perhaps someone can help you with a bit more information

---

### Post by billcecil on 2013-06-18
I get so upset when I try to get a piece of hardware to work with linux. Sorry for the rant, but if you knew what had happened in my life the week before you'de understand my rage. As I said, I started in Ubuntu with 8.4 thus "several years" . I liked it so much, I gave up my windows formatted my computers, and went with linux on all of my PCs and laptops. By the way, I did get it to print.

---

### Post by monkeybrain2012 on 2013-06-18
Well I have very good experience with printers. Have an epson which works out of the box, HP at work also works out of the box (whereas it doesn't work with Windows 7 after work computers upgrade from Windows xp) Went to my brother's place, plug a Ubuntu usb into his computer and printed right the way from his HP printer, he was like "WTF???? How come you don't have to install any driver??!!"

In general I have had no issue whatsoever with random hardware like usb wireless cards and webcams that I see lying around. But if I am shopping for hardware myself I would do some research first. Some manufacturers only support Windows, but it is not Linux's fault, you should vent your frustrations at them instead. :)

---


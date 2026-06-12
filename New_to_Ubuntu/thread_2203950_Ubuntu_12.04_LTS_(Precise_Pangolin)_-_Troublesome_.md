---
title: "Ubuntu 12.04 LTS (Precise Pangolin) - Troublesome Times with Ubuntu"
date: 2014-02-06
forum: New to Ubuntu
---

### Post by blakeaustindailey on 2014-02-06
Hello!

I would like to start off with saying: I am very new to Linux Ubuntu, despite having had my first install with 10.04. I had a netbook that had a corrupted OS, or something, and didn't feel like buying a new copy of Windows, so here I am today.

Back then, a couple years ago, I didn't have too much trouble with my Ubuntu, because I didn't use it much. Now, I have aswell put it on a desktop, because I enjoy the concept of Ubuntu so much. However, here is where the issues begin to flow.

For about four installs, or so, I have been trying to make my Ubuntu... Work.

First fresh install, a little buggy (Of course, this was my first upgrade to 12.04 LTS) but it worked, I ended up installing essential things like the latest version of WINE, and pressing the update button in the update manager regularly. Everything was fine, until I tried to install a Joystick Axis, and somehow completely fudged the system to the point where it wouldn't boot. 

Another fresh install later, I... Would get random error messages, as if it didn't install correctly. I don't actually have these handy, as I've moved on, sense. But the point is coming.

Final install (And latest), I tried to basically, buff up my Ubuntu a bit. I wanted to make sure I had all the programs and PPA's to make it run well, like any good man would. I went to this site: [http://howtoubuntu.org/things-to-do-after-installing-ubuntu-12-04-precise-pangolin#.UvNBHqFlmmi](http://howtoubuntu.org/things-to-do-after-installing-ubuntu-12-04-precise-pangolin#.UvNBHqFlmmi)

And I followed the steps to get all of the programs on there, to help with video files, and music files, and file extensions. None of it worked, in fact, it made it so I couldn't run  ```
sudo apt-get update
``` correctly, so nothing I did worked. I'll likely have to reinstall the system (Again)


But I just want to know, and I ask this with the aggrivation of someone who has tried to put all of his love and faith in this OS:

How do I improve, upgrade, and make my Ubuntu OS better at what it does?

I have..  A small list of questions, this is my first time posting on here, so if I've made this post a bit too spread out, let me know. I've had these questions in the back of my brain for a while.

---Question Group 1 [After installation, before anything else.]---

What do I need to do to my Ubuntu? Do I need to install anything, or update anything specific?

I may have missed this last time, but is my Universe Repository automatically open, as well as partner repositories, or do I have to manually open them on a fresh install? If so, how?

After installation, is there anything I can do to make Wine run better, as well as PlayOnLinux? 

Being completely green, I'm overwhelmed with how to.. Not make myself reinstall my OS weekly.

---Question Group 2 [Gaming on Linux]---

It's a shakey proposition, but I know some people manage it. I think Linux, Ubuntu in particular, is an amazing operating system, with a lot of potential. However, I've not managed to make a lot of things work on it that should have, for various, small reasons.

One I will start with is Winetricks. It's supposed to be an easy way to install .dll's to make Windows games work on Wine, however, every time I tried to use it, it made errors- Ones which I should have documented, but I'm not currently on that machine. But in short, I went through the GUI for Winetricks to find the .dll I needed, and some error would pop up on trying to install/obtain it. So that never worked.

PlayOnLinux, how do I make that work most effectively? Is there a laundry list of things I need to download to support gaming on Linux? If so, please assist.

---

I'm trying my hardest to get this system working to where I'm comfortable with it, and any help is appreciated.


Thank you for reading,

Blake

---

### Post by bc.haynes on 2014-02-06
To save time, please list the specifics on your computer: laptop?, processor, RAM, video card, etc, so that when someone more experienced than I helps you, the info will be there. Don't get discouraged, Ubuntu is worth learnng.

---

### Post by david98 on 2014-02-06
Am sorry to state the obvious but the first thing you would do is update the system *sudo update-manager* Next have a look through the software centre and install teh applications you need for me it's wine *sudo apt-get install wine* vlc player *sudo apt-get install vlc*  Then clam anti virus because I send file's across different platforms *sudo apt-get install clamtk*. As for your specific problems you are better of posting on here the exact problem at the time of it happening with screen shot's preferably. And also as @bc.haynes mentioned system spec's are very helpful.

---

### Post by newb85 on 2014-02-06
The tutorial you linked instructs to add many ppas, as well as the Medibuntu repository.   Simply adding a whole list like that without knowing the reasons for each is not good practice.   Very likely, your system won't update because there are conflicts in that list.   What error messages do you get with ```
sudo apt-get update 
```

---

### Post by BBQdave on 2014-02-06
> **blakeaustindailey said:**
> I would like to start off with saying: I am very new to Linux Ubuntu...

A few thoughts:

[LIST]
[*]Make sure Ubuntu Unity 12.04LTS is matched up to your hardware (32-bit or 64-bit)
[*]Enable *updates while installing* and *extra codecs* (Adobe Flash, Fluendo mp3 pack) - there are two buttons to check in one of the begining install windows
[*]After install - Update Manager will automatically let you know when updates are available
[*]Give yourself time to explore the default programs, explore Dash (Unity search)
[*]Use Ubuntu Software Center to add applications (tasks you can not work on with default applications)
[/LIST]

Give yourself time with the default install before tinkering :)

---

### Post by gifford on 2014-02-06
Sorry for the troubles you are having. I went to the site you referenced and found it listed sudo apt-get -qq update as the command to use. I have never come across nor ever seen this command referenced. I did Google and found no reference in relation to Ubuntu. However, the qq is a chat and messaging service used primarily in China. As for Medibuntu, it is no longer a valid ppa.

If it were me, I would immediately reformat my drive and do a new install of Ubuntu following the advice of BBQdave.  

Ubuntu does a great job of keeping the system up to date. In the future, it might be wise to ask questions of the forum when updating or using software that is not from the Ubuntu software center.

---

### Post by blakeaustindailey on 2014-02-07
Alright,


I've D-Ban wiped the hard disk, fresh install of Ubuntu. All is good, so far... Now for posting my system specifics?

How do I do that?

---

### Post by newb85 on 2014-02-07
> **gifford said:**
> Sorry for the troubles you are having. I went to the site you referenced and found it listed sudo apt-get -qq update as the command to use. I have never come across nor ever seen this command referenced. I did Google and found no reference in relation to Ubuntu. However, the qq is a chat and messaging service used primarily in China.

If I remember right, the -q option is "quiet" and suppresses some output of apt-get.  Using it twice suppresses even more.

---


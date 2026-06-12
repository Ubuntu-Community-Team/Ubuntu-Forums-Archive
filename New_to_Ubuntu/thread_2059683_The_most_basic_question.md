---
title: "The most basic question"
date: 2012-09-18
forum: New to Ubuntu
---

### Post by vaughnthevague on 2012-09-18
I'm sorry for being stupid.  I have not touched linux in a couple of years, and I was never very good at it to begin with.  

I am setting up a system for my small boy.  I pulled my old computer out of the closet.  I was running 9.something and I upgraded to the most recent LTS this morning.  I am unable to install or uninstal anything in the app center.  It gives me the message:

"The package system is broken

The following packages have unmet dependencies:

wesnoth-music: Depends: wesnoth-1.10-music (= 1:1.10.2-1) but it is not installed
               Depends: wesnoth-1.10-data (= 1:1.10.2-1) but 1:1.10.2-1 is installed"

I don't really have a clue what to do next.  When I attempt to fix or uninstal using the button it fails.  I guess I use the terminal, but I have little clue what to type in the terminal.  

He just turned 5 and Ubuntu is his first computer.  By the time he is 6 he will be better than me at this.  Until then, I will be leaning pretty heavily on you guys.  

Thanks.

---

### Post by jerrrys on 2012-09-18
9.x is no longer supported.  You going to need to burn a new CD of something, depends on your computer specs.

---

### Post by vaughnthevague on 2012-09-18
I downloaded and installed 12.04 last night without a problem.  I installed over the 9. whatever I had.  I did not have an issue with that.  

12.04 is already installed.

---

### Post by vaughnthevague on 2012-09-18
Sorry, perhaps telling everyone what I was running previously was an unintentional red herring.

---

### Post by linuxvstheworld on 2012-09-18
Just install over the 'broken' Ubuntu, if you're setting it up fresh.

---

### Post by linuxvstheworld on 2012-09-18
> **vaughnthevague said:**
>   
He just turned 5 and Ubuntu is his first computer.  By the time he is 6 he will be better than me at this.  Until then, I will be leaning pretty heavily on you guys.  

Thanks.

You're an awesome parent, literally an awesome parent for doing that, I am thinking if I have kids I'll get them Linux too. Guess I'm not the only one.

---

### Post by irv on 2012-09-18
It would also be nice to know what specs are on the old computer? Also what you are trying to run on it? Like Ubuntu, Xubuntu, or Lubuntu or whatever? And also the version #?

---

### Post by Frogs Hair on 2012-09-18
You might try the following to fix the broken package.  

```
sudo apt-get update
```
```
sudo apt-get upgrade
```

If you get errors try following and post the output in code tags using the # symbol on the reply box tool bar.```
sudo apt-get install -f 
```

The package you posted appears to be for a game and there may be a dependency problem if the game was part of 9.x installation.

---

### Post by black veils on 2012-09-18
seems like they did some kind of upgrade using the live cd, instead of fresh install, that is sure to cause problems, being that the version previous was so old..

---

### Post by mansonfan78 on 2012-09-18
> **vaughnthevague said:**
> I'm sorry for being stupid.  I have not touched linux in a couple of years, and I was never very good at it to begin with.  

I am setting up a system for my small boy.  I pulled my old computer out of the closet.  I was running 9.something and I upgraded to the most recent LTS this morning.  I am unable to install or uninstal anything in the app center.  It gives me the message:

"The package system is broken

The following packages have unmet dependencies:

wesnoth-music: Depends: wesnoth-1.10-music (= 1:1.10.2-1) but it is not installed
               Depends: wesnoth-1.10-data (= 1:1.10.2-1) but 1:1.10.2-1 is installed"

I don't really have a clue what to do next.  When I attempt to fix or uninstal using the button it fails.  I guess I use the terminal, but I have little clue what to type in the terminal.  

He just turned 5 and Ubuntu is his first computer.  By the time he is 6 he will be better than me at this.  Until then, I will be leaning pretty heavily on you guys.  

Thanks.


Do you have synaptic installed?  If you do you could open it and search for wesnoth-music and uninstall it.  You should be able to from synaptic.  You could reinstall it later after checking to see if it solves the problem.  Reinstalling should pull in the proper dependencies.

---

### Post by vaughnthevague on 2012-09-18
I will try those command lines.  

Yes, I did upgrade from a 12.04 live CD.  Then once the initial install was finished I downloaded the rest.  

It was over 2500 changes.  I'm happy to have only found one problem out of the 2500 changes.  

I have AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ × 2 with a couple of hundred gigs of space on the HD.

It is for the Battle of Wesnoth.  I had it installed 6-7 years ago on the initial install.

---

### Post by hypnot0ad on 2012-09-18
> **linuxvstheworld said:**
>  Guess I'm not the only one.
No you are not. :)

---

### Post by irv on 2012-09-18
> **vaughnthevague said:**
> I will try those command lines.  

Yes, I did upgrade from a 12.04 live CD.  Then once the initial install was finished I downloaded the rest.  

It was over 2500 changes.  I'm happy to have only found one problem out of the 2500 changes.  

I have AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ × 2 with a couple of hundred gigs of space on the HD.

It is for the Battle of Wesnoth.  I had it installed 6-7 years ago on the initial install.

For what you call an older computer you have almost the same specs as I have. It is more than enough to run 12.04 with Unity. Let us know if using the commands posted fixes your error problem.

---

### Post by vaughnthevague on 2012-09-18
I get the message from the Ubuntu Software Center 

"Items cannot be installed or removed until the package catalog is repaired"

I hit the repair button, enter the password, the repair fails and this spits out:  

(Reading database ... 334551 files and directories currently installed.) 
Unpacking wesnoth-1.10-music (from .../wesnoth-1.10-music_1%3a1.10.2-1_all.deb) ... 
dpkg-deb (subprocess): data: internal gzip read error: '<fd:4>: data error' 
dpkg-deb: error: subprocess <decompress> returned error exit status 2 
dpkg: error processing /var/cache/apt/archives/wesnoth-1.10-music_1%3a1.10.2-1_all.deb (--unpack): 
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2 
No apport report written because MaxReports is reached already
Errors were encountered while processing: 
 /var/cache/apt/archives/wesnoth-1.10-music_1%3a1.10.2-1_all.deb 
Error in function:  
dpkg: dependency problems prevent configuration of wesnoth-music: 
 wesnoth-music depends on wesnoth-1.10-music (= 1:1.10.2-1); however: 
  Package wesnoth-1.10-music is not installed. 
dpkg: error processing wesnoth-music (--configure): 
 dependency problems - leaving unconfigured

---

### Post by black veils on 2012-09-18
it should be fine if you just reinstall, boot the live cd/usb and in the install wizard, choose to erase and use entire disc.

this will give you a fresh install, instead of an upgrade from version 9 or whichever it was.

---

### Post by jerrrys on 2012-09-18
Try this

sudo apt-get clean

sudo apt-get update

---

### Post by vaughnthevague on 2012-09-18
Thank you all for your time and your help.  A fresh install rather than an upgrade may be the solution.  I will do that.  

My son seems to have inherited the computer/math/engineering aptitude that skipped right over me.  This computer should last him several years.  I'm sure he will be teaching me how to navigate and fix Linux very soon.

---

### Post by irv on 2012-09-18
If you do a fresh install check out this link:
[http://blog.sudobits.com/2012/04/14/10-things-to-do-after-installing-ubuntu-12-04/]("http://blog.sudobits.com/2012/04/14/10-things-to-do-after-installing-ubuntu-12-04/")

---

### Post by vaughnthevague on 2012-09-18
> **jerrrys said:**
> Try this

sudo apt-get clean

sudo apt-get update


Yeah!  I think this worked!

---

### Post by jerrrys on 2012-09-18
cool :)

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

---

### Post by vaughnthevague on 2012-09-18
Thanks again!

The fix worked great and I was able to install some good kid's games and some educational software.  This should last us a while.  

I think it is funny how his old computer is actually better than mine now.  Mine is just portable and I use it for business.  

I can imagine him coming home from grade school and being frustrated that he can't find the terminal on the school's computers and typing in "sudo" does absolutely nothing.

---

### Post by jerrrys on 2012-09-18
enjoy :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by irv on 2012-09-19
> **vaughnthevague said:**
> Thanks again!

The fix worked great and I was able to install some good kid's games and some educational software.  This should last us a while.  

I think it is funny how his old computer is actually better than mine now.  Mine is just portable and I use it for business.  

I can imagine him coming home from grade school and being frustrated that he can't find the terminal on the school's computers and typing in "sudo" does absolutely nothing.

Your kid is going to be the smartest one in the class when it comes to computers. The teacher will be the one asking the questions.

---


---
title: "Completely new to Linux- Have questions"
date: 2012-04-29
forum: New to Ubuntu
---

### Post by Tyrande on 2012-04-29
Greetings!

With the new computer I am building I have decided to use ubuntu as the sole OS. I have never used Linux, and know very little about it. I have a few questions, and things I am curious about.

First here is the rig I am building- [http://secure.newegg.com/WishList/PublicWishDetail.aspx?WishListNumber=14343789](http://secure.newegg.com/WishList/PublicWishDetail.aspx?WishListNumber=14343789) A large upgrade from my poor old laptop.

Is there anything I should know before I mix all of these? For example, I wish someone would have told me this or that before I installed.

I am mainly a gamer and photoshop suite user. Games I run are, Wow, The Sims 3, Skyrim, and D3 (when it comes out). I plan on using Wine. I know as much about Wine in only that it was a widely recommended program. I hear of another that you pay for, but I am a broke college student lol. I had to save, beg and borrow to collect the money for this computer. I have tried reading many tutorials, but honestly they are a bit overloaded. Can anyone suggest anything clear, and simple to get Wine setup for these game?

I've been a Win user for over 10 years, and was fairly knowledgeable about it and it's quirks. Switching to a new system is very daunting to say the least and I want to be as prepared as I can. Any suggestions/advice for the rookie will be extremely appreciated.

---

### Post by kdane4 on 2012-04-29
> **Tyrande said:**
> 
I am mainly a gamer and photoshop suite user. Games I run are, Wow, The Sims 3, Skyrim, and D3 (when it comes out). I plan on using Wine. I know as much about Wine in only that it was a widely recommended program.

I suggest Dual Booting, some windows programs (especially games) are really hard to run on wine.

Myself, I keep a copy of windows because of games.

Here's the [wine app database]("http://appdb.winehq.org/") so you could check if wine runs your programs..

Cheers :popcorn:

---

### Post by blade4 on 2012-04-29
Hi Tyrande and welcome . 

I see you're getting a very decent rig here and I can tell you that Ubuntu should run like a breeze on it .But migrating to ubuntu when you're into gaming and photoshop might not be such a good idea , especially when you know little about it 

Wine is a good program but not without its own problems .Although it can run the games you've mentioned here ( 'cept D3), there are many games it can't run , and then there are games that need massive amounts of wine tweaking to run .  

Like kdane4 says , you can try out  with dual booting . I suggest you start off by trying the wubi version ( install as a software ) and get a feel for it . Then you'll be in a better position to decide . 

Cheers

---

### Post by Perfect Storm on 2012-04-29
As other said dual boot.

That said I have Wow and Skyrim running via crossover (as you have choosen a Nvidia card - should give you minimal problems compared to other cards): [http://www.codeweavers.com/products/](http://www.codeweavers.com/products/)
In Sims3 the only thing that doesn't works is the onlineshop where you can buy extra stuff.

Also check our wine forum for help: [http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)

---

### Post by 3rdalbum on 2012-04-29
> **Tyrande said:**
> Greetings!

With the new computer I am building I have decided to use ubuntu as the sole OS. I have never used Linux, and know very little about it. I have a few questions, and things I am curious about.

First here is the rig I am building- [http://secure.newegg.com/WishList/PublicWishDetail.aspx?WishListNumber=14343789](http://secure.newegg.com/WishList/PublicWishDetail.aspx?WishListNumber=14343789) A large upgrade from my poor old laptop.

Is there anything I should know before I mix all of these? For example, I wish someone would have told me this or that before I installed.

The sound card is my only doubt. Creative's X-Fi cards were horrendous for many years on Linux as Creative's drivers were buggy and nearly unworkable. Maybe this card is okay, and the X-Fi are okay now from what I hear, but I personally would be wary and would just stick to the normal motherboard audio.

> I am mainly a gamer and photoshop suite user. Games I run are, Wow, The Sims 3, Skyrim, and D3 (when it comes out). I plan on using Wine. I know as much about Wine in only that it was a widely recommended program.

That's clear. Wine is a last resort; if you have only Linux and you really REALLY need a particular Windows program to work, then try Wine. There's about a 20% chance it will work.

Photoshop is one of the programs the Wine developers aim to have supported, but you'll need to check out the Wine HQ website to see what versions will work.

If you identify yourself as a PC gamer, then Ubuntu is sadly the wrong operating system to have. Most games released on Windows are not released for Linux, and most can't be run in Wine. Grab a PS3 or run Windows if you want games. Remember, you can dual-boot between Windows and Ubuntu; both on the same hard disk, but on every boot you can choose which to boot into.

I'm sure some well-meaning people will suggest using Windows in "Virtualbox" for the games, but this doesn't work.

> I've been a Win user for over 10 years, and was fairly knowledgeable about it and it's quirks. Switching to a new system is very daunting to say the least and I want to be as prepared as I can. Any suggestions/advice for the rookie will be extremely appreciated.

My best advice would be what you already know: Linux (and Ubuntu specifically) is a very different system to Windows. If you're a pro at Windows, you're a newb at Linux - most of what you already know is not transferrable. Be prepared to learn everything from scratch. I think you already have some concept of that so good luck :-)

Another tip: Ubuntu changes very quickly. If you want to find out how to do something on Ubuntu, make sure you're looking at up-to-date information for your version of Ubuntu. Looking at a guide from 2010 will not help you. Things in Linux move so quickly that a lot of people here even give outdated information simply because they haven't realised that their experiences from a few years ago are no longer applicable :-)

And my last little tip is that things may be easier than you imagine. Linux is easy, but sometimes it seems harder than it actually is. For instance, the terminal is RARELY required - but a lot of instructions you get given will be terminal-based. It's just because it's easier to say "Here, copy and paste this into the terminal", than to say "Click here, then click here, then if you're using 12.04 you click here, but for earlier versions type this in..." etc.

---

### Post by Anuovis on 2012-04-29
The problem with Wine is that it's a hit-and-miss situation for a lot of software. Sometimes certain versions of a particular Windows software don't work well while others run perfectly. Sometimes games have minor, sometimes big problems. It's a bit of a grind and if you plan running many different things through Wine, dual boot will probably save you a lot of headache.

As for Ubuntu, it is very different but not harder than Windows to use. You could read some introductory guides or how to do simple stuff but honestly, with the Ubuntu as it is now, you will probably figure out day-to-day tasks pretty easily.

Just keep in mind that Ubuntu doesn't run Windows software and things like Wine are just imperfect attempts to make some of the things usable. You can find lots of good Windows alternatives though.

Otherwise, the migration shouldn't be too hard since you seem to have a open mind and willingness to learn. Have fun.

---

### Post by sadaruwan12 on 2012-04-29
Welcome to the forum, I was a hard core win user due to the sole factor of games. But I realized that games is lie drugs that once you have it keeps coming back for more. I followed series like Crysis, COD, MOH, freelancer HitMan ... etc. But never had enough only takes me 24 to 48 hours to complete a game so you get the idea about what a crazy guy I was.

For the pace I was going my PC and my income couldn't handle it needed to constantly upgrade my rig to keep the games running smoothly.

I'm a Web based programmer and a System administrator by profession so gaming was my stress blow hole but it went too far. But one day my computer got a attacked by a virus which gave me a hart attack at that point I had one of those magic moments and realized this is actually not what I want to do with my PC.

So just like you want on a endeavour to search the perfect OS and I found a fawn a festiy fawn in the stable of Ubuntu. From that day on ward never looked back. Best thing is that Linux let you make your OS the way you want it.

For you friend if you can't live with out the games then dual boot a small partition with windows and a bigger portion for Ubuntu.

If you could give up the gaming part then you can use VirtualBox to run a virtual windows system for Photoshop like I do and also I use crossover to run small windows games just to keep my beast tamed.

I also like to say at first switching from Win to Lin you'll think to give the linux part 'cos you'll have big learning curve. Unlike windows the true power of linux lies in the Terminal when you learn how to control it then you can become a artist a true pro.

You'll be able to do things any windows man can't even think of, Don't give up if something goes wrong we're here to help.

When becoming apart of the open world keep your mind open look for knowledge ask question, most importantly keep updating your knowledge 'cos we change very quickly.

The most important thing when becoming a Linux user make google your best friend and the closest friend when you do that you become complete.

Once again welcome and god bless you.

---

### Post by CoDeHacKer on 2012-04-29
Hi, 

If I was going to put a machine like that together, I'd want to go with minimum 2 SATA II drives, and with the  drive xpert technology there, I'd do a raid array for games, and if I needed more storage maybe get a 
smaller mechanical drive.  I'd want 2 SATA III drives for me.  

With the SATA drive you're talking like around 130mb/s buffer to drive, I know a 25 man raid will more 
than likely create a bottleneck.  With SATA II around 250 mb/s and with SATA III around 500 mb/s.  

I guess you can always make an array out of the single drive, and get around 250mb/s maybe, so I hear. 

I'm still trying to get 12.4 on my quad :mad:

Don't get me wrong, you asked, and I would be mad if somebody didn't tell me before I went all out
and got something I'd rather have different.   That is a sweet machine nomatter what.

---

### Post by ronaldbrijo on 2012-04-29
I agree, 
Go dualboot...

---

### Post by Paqman on 2012-04-29
> **Tyrande said:**
> 
I am mainly a gamer and photoshop suite user.

Bad news: these are some of the few things for which Windows is a significantly better platform than Linux. Either just use Windows, or dual-boot.

---

### Post by xedi on 2012-04-29
I'm surprised that nobody suggested to try out GIMP as an alternative to photoshop. If you don't mind learning a new program then GIMP should be able to do everything you can do on photoshop. As far as games, you won't able to play every game even with Wine, but then again you also don't have to :p PlayOnLinux comes in handy concerning games. It uses wine but is specialized at games.

So my opinion is, if you really want to go the Ubuntu only route as a gamer, then go ahead, it's possible but expect compromises such as learning the Linux alternatives like GIMP and that you won't be able to run all Windows games you encounter. We can tell you our experiences but in the end, you have to try out and figure out yourself whether you can survive on Ubuntu only.

As many others recommended, dual boot is probably the best option, especially when the only problems are games (I just ignore photoshop for a moment). Since you usually do not do any other tasks when playing, it would not be a huge issue to have a seperate operating system dedicated for it and another for everything else. It might be even beneficial so you do not get as easily tempted when trying to get stuff done :D . I personally have on my second computer also a dual boot with Windows for a game because I have a free copy through MSDNAA. I would have not bought Windows but this way it's a nice hassle free option. On my main computer I use all the time I only have Ubuntu, though.

---

### Post by Jugurtha on 2012-04-29
Hello Tyrande,

I personally have dual boot (and planning on adding a third system):

-Ubuntu 11.10 as a default system. Grub waits 1 second and boots Ubuntu.

-Windows XP SP3 (I don't like any version made after XP, they all assume you're dumb and try to help you too much which, paradoxally, slows you down a lot)

On Windows, I have Virtual Box : I set up a virtual machine running Linux for when I just want to test something without rebooting .. BUT... I don't use it that much and the things I want to test aren't greedy, memory wise.

Being in Electronics Engineering, a lot of software is to be ran on Windows (CAD, some vendor specific software, think Siemens SIMATIC and stuff like that) .. So I keep a copy of Windows XP (which I like too).

Linux, I use for programming because the tools you get on Linux are just awesome and everything is made to make it as simple as drinking water. Many things come installed by default which is great.

The point is: The applications I use in Windows are memory greedy, so I wouldn't think of running them on a virtual machine because I would sacrifice a lot of performance when I could just boot on Windows, for example.

So in a nutshell, run stuff "natively" if I may say. Get dual boot. When something is heavy, boot the adequate system. If it's just test, load the virtual machine.


All my best..

---

### Post by tmaranets on 2012-04-29
> I am mainly a gamer and photoshop suite user.
if that is what describes you, dual-boot Windows.

---

### Post by Tyrande on 2012-05-02
Thank you all for your very informative replies!

You will be happy to know that the hard drive is temporary. When I get the money I plan on turning that into the storage drive and getting more hard core drives as my "mains".

I actually do use Gimp! However I have not found a free alternative to lightroom.

Jugurtha, I agree with the windows versions after XP. Win 7, the OS that talks down to you! I was considering getting XP (if I can find a place to buy it). However my reason for not duel booting is I simply can't afford windows anymore. I might just try looking for an inexpensive XP to DB into.

I guess I'll just dive in and see where it all goes. You'll probably hear from me again...

---


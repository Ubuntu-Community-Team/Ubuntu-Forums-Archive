---
title: "Noob Looking to Learn!"
date: 2012-10-09
forum: New to Ubuntu
---

### Post by jediknight36 on 2012-10-09
Hey all! Im pretty new to Linux in general. Hated windows since I ca remember, and now am mainly a mac guy since thats what my industry uses. But I have played with ubuntu on/off for the last year and have decided that I want a Ubuntu media/backup server. Im scared to dual boot it anymore as it seems to mess up the file system on my entire HDD when I do and 6mo or sooner down the line I end up needing to unpartition the Ubuntu partition and it wipes my drive. Or it just eats my entire drive instead of installing on one partition. Im sure its user error, so more reason to be here! 

Anyway, my plan is to build a PC like server. What I mean by that is I am cash constrained and will either modify an existing PC or, more likely, will build a PC from a brand new basic case, motherboard, etc. I HAD a NAS from Buffalo. 4TB of storage, and the processor fried. Thats what Buffalo said anyway. So I want to stick those and a 5th HDD in a PC case and use it as a media server and backup for my other two computers. 

So I guess my first question is, is there any known hardware on the market that wont work with Ubuntu? Like if I had a grocery list, is there somewhere I can compare it to? Also, any recommended reading?

Thank you all.

---

### Post by jingaling on 2012-10-09
The only hardware ive come across that categorically wont work with Ubuntu (or any linix distro) is anything with a SiS chip (Silicone Integrated Systems). Apart from that ive never had a problem with hardware.

---

### Post by Frogs Hair on 2012-10-09
Here is a starting point. [https://help.ubuntu.com/12.04/installation-guide/amd64/hardware-supported.html](https://help.ubuntu.com/12.04/installation-guide/amd64/hardware-supported.html)

---

### Post by audiomick on 2012-10-09
Ubuntu works pretty well on most stuff. Stick to at least moderately well known brands. I am using an MSI Laptop and a desktop with an MSI mainboard. That works well, but the BIOS flash update for the desktop is strictly windows. You normally shouldn't have to do that, though. I've had a bit of annoyance with Samsung drives, but I think I just had bad luck there. Might have been simply a bad SATA  cable. Any rate, known brands should work fine.

---

### Post by jediknight36 on 2012-10-09
Well, here is the list so far. Again, all I want to do is back up on it, and stream movies and music off it, albeit faster than my POS NAS. Think this with Ubuntu Server will get me where I want to go, so to speak?

---

### Post by will1982 on 2012-10-09
> **jingaling said:**
> The only hardware ive come across that categorically wont work with Ubuntu (or any linix distro) is anything with a SiS chip (Silicone Integrated Systems). Apart from that ive never had a problem with hardware.

You are the luckiest person to have ever lived.

---

### Post by DuckHook on 2012-10-09
Welcome to Linux-space!

A few years ago, I had the occasion to build pretty closely the configuration that you are referring to, and Linux ran on it like a charm. That was back in the Red Hat days, and Linux has only gotten better since. I found, however, that my biggest problem was physical. More specifically, I fried a couple of drives before realizing that a PC case is simply not sufficient for server duties. The biggest problem is airflow. Even though the mid-tower case that I used had enough slots for the five HDs that I installed, it doesn't have enough clearance between HDs to properly dissipate the heat. And even with two fans, a PC case is not really designed to circulate air efficiently enough to act as a server box. So, my input is not so much about Linux as it is about your physical setup.

Hope this helps. Otherwise, it sounds like an exciting project. Good Luck!

---

### Post by rochford77 on 2012-10-09
an iPhone will not run ubuntu

#teamandroid:guitar:


lmfao....had to:P

---

### Post by jediknight36 on 2012-10-09
> **DuckHoo said:**
> Welcome tPC Linux-space!

A few years ago, I had the occasion to build pretty closely the configuration that you are referring to, and Linux ran on it like a charm. That was back in the Red Hat days, and Linux has only gotten better since. I found, however, that my biggest problem was physical. More specifically, I fried a couple of drives before realizing that a PC case is simply not sufficient for server duties. The biggest problem is airflow. Even though the mid-tower case that I used had enough slots for the five HDs that I installed, it doesn't have enough clearance between HDs to properly dissipate the heat. And even with two fans, a PC case is not really designed to circulate air efficiently enough to act as a server box. So, my input is not so much about Linux as it is about your physical setup.

Hope this helps. Otherwise, it sounds like an exciting project. Good Luck!

That is great. The only reason I thought this was a) ive, never built anything other than pc cases and b) I am limited on budget and space, in that order. The NAS was a budget move and it had 4TB drives in it, but maybe it fried. IDK. Do you think I can get or build a server case for around this price range?

---

### Post by DuckHook on 2012-10-09
Unfortunately, most server cases will eat up your budget with the case alone. I understand the attraction of building a super-cheap budget system. There is a real challenge to it, and it's especially satisfying to actually pull it off. This challenge was what drove me to assemble my own super-cheap system so long ago.

A few general observations, and then we had better get on to Ubuntu -- after all, it's supposed to be a beginners' forum and not about hardware.

> Im scared to dual boot it anymore as it seems to mess up the file system on my entire HDD when I do and 6mo or sooner down the line I end up needing to unpartition the Ubuntu partition and it wipes my drive. Or it just eats my entire drive instead of installing on one partition. Im sure its user error...

Your problems may be due to nothing more than a wonky disk. It is very advisable to run a disk diagnostic utility on each disk that you intend to use on your future file server.

> ...will either modify an existing PC or, more likely, will build a PC from a brand new basic case, motherboard, etc.

If you stick with low price PC cases, choose a case with plenty of HD slots and then populate only every other slot. This will give them room for air circulation. Then, before spending a penny on any component, Google each component with a query along the lines of: "Is [component] compatible with Linux?"

Now, the Linux discussion:

A super-cheap budget system doesn't need a powerful processor, motherboard, video card or sound subsystem. And since this is not an enterprise server, it doesn't need much memory, a killer I/O subsystem or redundant power supply either. Keep in mind that such a system will commit suicide if any single component fails but, hey, you know that going in.

The good news is that, conceptually, your project can be done on a super tight budget. However (there's always a "however"), the Linux side is more challenging, and this is not because of Linux itself (which is more than up to the task) but because of the learning curve for new users. The problem with a bare bones base system is that it will choke to death on the overhead of a graphical interface. This is one of the reasons why Ubuntu Server Edition does not come with a GUI. But the Linux command line interface is so obscure and intimidating to new users that it sets new users, no matter how dedicated and well-meaning, up for failure. At least, this was my initial experience trying to do what you're doing.

My best advice is as follows: before spending a dime on anything, turn your existing system into a pure linux box now. As is. No dual boot, no Windows safety net, no wussing out. You mention that you have two other computers, so I'm assuming that you can install Linux on this machine that you were planning to convert anyway. This is your school. Your Linux University. Your Linux Temple. As such, you will not allow yourself to fall back to the GUI. You will open up terminal with every session and you will experiment, explore and fix your inevitable mistakes using nothing but the command line.

A good book about the command line interface can be found here:

[http://sourceforge.net/projects/linuxcommand/files/TLCL/09.12/](http://sourceforge.net/projects/linuxcommand/files/TLCL/09.12/)

The PDF is free to download, and it covers almost everything you will need to know to get started managing your server.

A few weeks of butting your head against the Linux command line in your spare time will provide you with priceless data, mostly about yourself. If you find that you cannot get your head wrapped around the commands in the book (which progress from basic to intermediate), then running an ultra-cheap Linux server is not realistic. At that point, you will have to increase your budget and build a machine that can run a GUI-based server. You may even decide to stick with Windows, but the point is: you will know. And you will not have spent a dime to get there.

---

### Post by jediknight36 on 2012-10-09
> **DuckHook said:**
> Unfortunately, most server cases will eat up your budget with the case alone. I understand the attraction of building a super-cheap budget system. There is a real challenge to it, and it's especially satisfying to actually pull it off. This challenge was what drove me to assemble my own super-cheap system so long ago.

A few general observations, and then we had better get on to Ubuntu -- after all, it's supposed to be a beginners' forum and not about hardware.



Your problems may be due to nothing more than a wonky disk. It is very advisable to run a disk diagnostic utility on each disk that you intend to use on your future file server.



If you stick with low price PC cases, choose a case with plenty of HD slots and then populate only every other slot. This will give them room for air circulation. Then, before spending a penny on any component, Google each component with a query along the lines of: "Is [component] compatible with Linux?"

Now, the Linux discussion:

A super-cheap budget system doesn't need a powerful processor, motherboard, video card or sound subsystem. And since this is not an enterprise server, it doesn't need much memory, a killer I/O subsystem or redundant power supply either. Keep in mind that such a system will commit suicide if any single component fails but, hey, you know that going in.

The good news is that, conceptually, your project can be done on a super tight budget. However (there's always a "however"), the Linux side is more challenging, and this is not because of Linux itself (which is more than up to the task) but because of the learning curve for new users. The problem with a bare bones base system is that it will choke to death on the overhead of a graphical interface. This is one of the reasons why Ubuntu Server Edition does not come with a GUI. But the Linux command line interface is so obscure and intimidating to new users that it sets new users, no matter how dedicated and well-meaning, up for failure. At least, this was my initial experience trying to do what you're doing.

My best advice is as follows: before spending a dime on anything, turn your existing system into a pure linux box now. As is. No dual boot, no Windows safety net, no wussing out. You mention that you have two other computers, so I'm assuming that you can install Linux on this machine that you were planning to convert anyway. This is your school. Your Linux University. Your Linux Temple. As such, you will not allow yourself to fall back to the GUI. You will open up terminal with every session and you will experiment, explore and fix your inevitable mistakes using nothing but the command line.

A good book about the command line interface can be found here:

[http://sourceforge.net/projects/linuxcommand/files/TLCL/09.12/](http://sourceforge.net/projects/linuxcommand/files/TLCL/09.12/)

The PDF is free to download, and it covers almost everything you will need to know to get started managing your server.

A few weeks of butting your head against the Linux command line in your spare time will provide you with priceless data, mostly about yourself. If you find that you cannot get your head wrapped around the commands in the book (which progress from basic to intermediate), then running an ultra-cheap Linux server is not realistic. At that point, you will have to increase your budget and build a machine that can run a GUI-based server. You may even decide to stick with Windows, but the point is: you will know. And you will not have spent a dime to get there.

Thats good to know. Im building a machine that can handle windows 7. Ubuntu GUI shouldnt be a big deal, should it?

I only have two machines, both dual boot mac/windows 7 for that elusive tool for android or game. I would be building a basic system from the ground up. See the shopping list above. 

Yes, I need to go through said list and make sure its compatible with linux. Got it! Thanks!

---

### Post by JawsThemeSwimming428 on 2012-10-09
I've always found Psychocats ([http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)) to be an excellent resource for a lot of things Ubuntu related. Lots of good stuff for beginners too.

---

### Post by jediknight36 on 2012-10-10
[http://www.psychocats.net/ubuntu/whichbuntu](http://www.psychocats.net/ubuntu/whichbuntu)

Ok... I was unaware that Ubuntu Server didnt have a GUI AT ALL! I thought there was a flavor that did. So... there isnt a way to make a Ubuntu file/media server using a GUI?

---

### Post by DuckHook on 2012-10-10
Ubuntu Server Edition is total overkill for your purposes. You should not even think of using it. It is true that it lacks any GUI whatsoever, but this is not because of concerns about overhead. The sort of system that Server Edition is designed for can easily support a GUI. However, in high-end servers, GUIs are avoided because they introduce needless complications and security risks.

The short answer to your concern is: if you plan on building a system that can run Windows 7, then using Ubuntu Desktop Edition (complete with its GUI) is perfectly fine for a home server. My original post was referring to a super-cheap system that may not have the resources to support a GUI. you have since made the clarification that your system will not be *that* cheap.

You should be aware, though, that any machine acting as a server will eventually require you to do things on the command line. It probably won't be much, but even some of the simple troubleshooting that new users ask us about on these forums require the command line.

---

### Post by jediknight36 on 2012-10-10
> **DuckHook said:**
> Ubuntu Server Edition is total overkill for your purposes. You should not even think of using it. It is true that it lacks any GUI whatsoever, but this is not because of concerns about overhead. The sort of system that Server Edition is designed for can easily support a GUI. However, in high-end servers, GUIs are avoided because they introduce needless complications and security risks.

The short answer to your concern is: if you plan on building a system that can run Windows 7, then using Ubuntu Desktop Edition (complete with its GUI) is perfectly fine for a home server. My original post was referring to a super-cheap system that may not have the resources to support a GUI. you have since made the clarification that your system will not be *that* cheap.

You should be aware, though, that any machine acting as a server will eventually require you to do things on the command line. It probably won't be much, but even some of the simple troubleshooting that new users ask us about on these forums require the command line.

So this:
[http://linuxhomeserverguide.com/server-config/phpVirtualBox.php](http://linuxhomeserverguide.com/server-config/phpVirtualBox.php)

is total over kill? Thats what I was hoping for! I see windows serves with a GUI. Command line isnt a big deal, as long as I know what to put in and get out of it. But basically, I want to torrent from it, stream data to the game consoles and other machines, and back up to it. Wonderful!

---

### Post by DuckHook on 2012-10-10
> **jediknight36 said:**
> So this: phpVirtualbox is total over kill?

Yes. Killed forty-two times over.

> I see windows serves with a GUI....which is at the heart of the difference between the Linux philosophy versus the Microsoft philosophy. Suffice it to say that the Linux preference for no GUI is what arguably makes Linux servers that much more robust. (I am just repeating the standard line in the interest of recapping history--so no flames please)

> Command line isnt a big deal, as long as I know what to put in and get out of it."Knowing" what you are putting in (as opposed to just blindly following a recipe) was the whole point in my long post about learning the command line. You will note that the link you pointed to for *phpVirtualbox* requires extensive use of the command line.

> basically, I want to torrent from it, stream data to the game consoles and other machines, and back up to it. Wonderful!You can (and should) do that in a simple computer with the standard desktop version of Ubuntu. No need for virtual machines (Virtualbox), dual boots, multiple OSes and other needless complexities. Half of the support requests on this forum result from people making their configurations overly complicated. Keep it simple and you will keep yourself happy.

BTW, Virtualbox is a fabulous and extremely powerful app. However, I strongly suggest that you refrain from exploring it until you have become proficient with Ubuntu, for the same reason that you should refrain from running until you have learned how to walk.

Good luck!

---


---
title: "Noob Help. Making a file server with Xubuntu."
date: 2008-11-18
forum: New to Ubuntu
---

### Post by chaulkster on 2008-11-18
Hello all,

I am seeking assistance in what may seem like a basic and rhetorical task for some of you but is actually quite the undertaking for me. So please bear with me even if I sound out of place or ignorant. Also, I'm assuming this is the right forum - so go easy if it isn't. 

Basically, here’s where I'm at: I had an old computer lying around that I built a while ago. It’s got an AMD 3200+ processor, Asus A8N-E motherboard, some older ATI Radeon graphics card, 1024mb RAM and a 200 GB hard drive. Originally I had Windows XP on it - this gave me so much grief and eventually I just got fed up with it. Around a year ago I caught wind of this "Linux" thing and looked into it. After a few weeks of reading and second guessing myself I was hooked and had to try it. I had followed some walkthroughs and ended up installing Ubuntu as a dual boot solution with XP. Over the next few months I realized that I never even used XP anymore and was pretty much only using Ubuntu for everything except for certain programs...

Unfortunately, around 6 months ago - about the same time I stopped using this computer - in a last ditch effort to get my ATI card to actually work with Ubuntu I somehow screwed everything all up and was just over my head. No worries - just an old clunker anyway.

So here am I now. Both me and my girlfriend have our own laptops(with vista) and have some things we would like to share and get off our computers as they take up a good chunk of space (we have budgets, music collections ect ect). I stumbled on to this: [http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1]("http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1")

And decided this looked like a fun project so here I am today. 

LET IT BE KNOWN: My computer knowledge is only slightly above the average man (READ: When Ubuntu gave me a problem it took hours of searching and trial and error for me to fix it - sometimes not knowing exactly what I did to fix it – and when I built this computer it was the first time I ever did anything like it so that was new to me too)... Please (and I mean please) treat me like a 2 year old and explain everything slow and clear so I can learn - trust me you won't hurt my feelings.

So if you lasted this far could you please help me with a few questions:

1. Is this even do able or even a good solution for me?
2. Will my old computer me up to the task?
3. Will I need any other hardware? (I'm just moved so I'm on tight budget here)
4. (Here’s a dumb one) How do even go about using it when it’s up and running?
5. (Hold on for another dumber one) I read on another websites that you should partition the drive(s) and store different categories of files in each partition... I don't see the benefit in this. (Mind you a lot of the information on the web is pretty old)
6. (Uh oh... a real winner) what’s all this hype of "FTP"... a little insight please? 

Please note that I googled for a couple hours before asking... It's just that I don’t seem to understand what I'm reading and can't apply it to my situation.

I'm a quick learner and would love to learn this type of stuff. I don't have big background in computers but I find them fascinating and would like learn more.

Anyways, thanks for the help everyone!

---

### Post by billgoldberg on 2008-11-18
> **chaulkster said:**
> Hello all,



1. Is this even do able or even a good solution for me?
2. Will my old computer me up to the task?
3. Will I need any other hardware? (I'm just moved so I'm on tight budget here)
4. (Here&#8217;s a dumb one) How do even go about using it when it&#8217;s up and running?
5. (Hold on for another dumber one) I read on another websites that you should partition the drive(s) and store different categories of files in each partition... I don't see the benefit in this. (Mind you a lot of the information on the web is pretty old)
6. (Uh oh... a real winner) what&#8217;s all this hype of "FTP"... a little insight please? 



So you have a Xubuntu box laying around somewhere and want it to serve/share files with Windows machines?

The article seems to mention Samba, so I guess you'll want that.

Is this correct?

--

Answers to questions:

1. Sure
2. Yes
3. No
4. See link below
5. I wouldn't bother if I were you.
6. FTP is ancient and shouldn't be used to share files in the network.

If you are willing to try Ubuntu (gnome) then this is easy as pie.

You are running Xubuntu, open up a terminal (cli). I'm not sure how to do it in Xubuntu, look through the menus.

Type in:

sudo apt-get install ubuntu-desktop

If it is done, log out.

In the log in screen, there is an option somewhere that is called session (or something like that).

Pick Gnome.

Read this article, very easy to do.

[http://linuxowns.wordpress.com/2008/10/28/share-ubuntu-folders-with-windows-samba/](http://linuxowns.wordpress.com/2008/10/28/share-ubuntu-folders-with-windows-samba/)

Done.

This can be done in Xubuntu as well, but not in the way described in the article.

Either way, installing ubuntu-desktop and setting this up shouldn't take more than 30 minutes.

--

As far as I know, you'll have to do this using the cli if you really want Xubuntu, as thunar (the file manager) isn't capable of doing this.

---

### Post by handydan918 on 2008-11-18
> 5. (Hold on for another dumber one) I read on another websites that you should partition the drive(s) and store different categories of files in each partition... I don't see the benefit in this. (Mind you a lot of the information on the web is pretty old)

There are a lot of good reasons to partition carefully. Most people don't do it, and then they post about "Ubuntu ate my family photos!" or some such drivel. If your data is important, store it carefully. If it isn't, do whatever is easy...

---

### Post by billgoldberg on 2008-11-18
> **handydan918 said:**
> There are a lot of good reasons to partition carefully. Most people don't do it, and then they post about "Ubuntu ate my family photos!" or some such drivel. If your data is important, store it carefully. If it isn't, do whatever is easy...

Meh, that's a bit of FUD.

Unless you format or reinstall Ubuntu on the same drive your info is on, you won't have problems.

Should you mess up your install, use a live cd to copy your data to a drive.

---

### Post by rubbsdecvik on 2008-11-18
Wow, you got some good questions, and we appreciate that you tried to do some research ahead of time.  I don't have a lot of links to give to you right now, but I might be able to answer some of your questions; let's give it a go.

> 1. Is this even do able or even a good solution for me?
Hell, yes.  If you had some problems before, there might be a few snags now, but it is totally worth it.  Especially if you and you're girlfriend share files (I do with mine too).  If you set things up right, you can even find other benefits too.  I can now access my files from anywhere using ssh.  If you get that far I might be able to help you out.

> 2. Will my old computer me up to the task?
I'm running mine on even older hardware.  You should be fine.

> 3. Will I need any other hardware? (I'm just moved so I'm on tight budget here)
Are you my twin and I didn't know it?  I just moved not to long ago as well.  You shouldn't need any extra hardware.  But if you find you need some, it wouldn't be much, and it won't be too hard to add more functionality in the future if you decide that this isn't enough.

> 4. (Here’s a dumb one) How do even go about using it when it’s up and running?
Not a dumb question.  If you've ever shared files before in Windows, this will be very similar.  This server can be used for a couple of tasks that are usually used for storage or other boring waiting like tasks (bitTorrent etc).  While I didn't read the whole article you referenced, it does give quite a bit of examples on how to administer and use the machine.  The more you try, the more you will figure out.  I use mine as a workstation still, but others just use it to serve files, allow for remote connectivity, bit torrent downloader, etc. If you own a small business you can even use it as a web server eventually (not really recommended with that hardware though).  

> 5. (Hold on for another dumber one) I read on another websites that you should partition the drive(s) and store different categories of files in each partition... I don't see the benefit in this. (Mind you a lot of the information on the web is pretty old)
Again, not a dumb question.  It is a bit tricky to answer though.  Using separate partitions does have it's advantages.  For example; say you have two partitions, one for your OS (Xubuntu or similar), and one for your home files (/home).  If you upgrade your Xubuntu and something breaks, you still will have your files safely on your /home partition.  Using only one partition has the advantage of not needing to configure anything beforehand (although it's not really too hard) and that you don't have to worry about one partition running out of room, (Although this can be fixed too).  

I would suggest just two partitions.  One for the system and one for /home.  Searching can help you find out how to do it, or I can help you out a little.  If you are using Xubuntu, I would suggest leaving about 5 gb for the system (probably could go with a gb or two less), and leave the rest for the /home.  That would give you plenty of space and work just fine if an update messes something up.

> 6. (Uh oh... a real winner) what’s all this hype of "FTP"... a little insight please?
FTP?  Never use it.  If you are running Windows on your laptops, then you'll probably end up using Samba anyway.  If you want to copy things back and forth over the Internet (something I do all the time), you can just use SSH and a nice program called Filezilla ([www.filezilla.com](www.filezilla.com)) that can copy files using the secure protocol SSH.

Hope that helps a little.

---

### Post by rubbsdecvik on 2008-11-18
Opps, the website is actuall [http://filezilla-project.org/](http://filezilla-project.org/)

sorry

---

### Post by rubbsdecvik on 2008-11-18
I'm sorry for posting, yet again, but I just wanted to add that I went over things rather fast, but there where a lot of questions.  If you need more questions answered just keep asking.  It's hard to know what to tell you since we did know what you need/want to know.  I hope I answered some of your questions, and hope I've added a few more for you.  That's what we're here for.

---

### Post by chaulkster on 2008-11-18
Hey guys,

Wow, that&#8217;s pretty impressive and quick. Many thanks to you all.

Let&#8217;s see if I can answer some of your questions now:

> ...
So you have a Xubuntu box lying around somewhere and want it to serve/share files with Windows machines?
....
If you are willing to try Ubuntu (gnome) then this is easy as pie.


I am willing to use any OS. Actually I would prefer Ubuntu as it is the only Linux distro that I've ever used. The only reason I am talking about using Xubuntu is because of that article. I figured there must be a reason for it. Would I follow the same procedure if I used Ubuntu?

As far as what&#8217;s on the computer right now let me clarify - It use to be a dual boot Ubuntu (7.10) and XP. I crash Ubuntu so last night I deleted the partition in the windows disk manager. The XP on the computer right now has NEVER worked right and could never figure out why. It's on its last leg right now and my plan is to after work today to load on Xubuntu or Ubuntu... depending on what you guys recommend.


> ... If you've ever shared files before in Windows, this will be very similar. This server can be used for a couple of tasks that are usually used for storage or other boring waiting like tasks (bitTorrent etc)... 

Hmm... Well have used a Windows server where, according to Windows, it just looked like another hard drive labeled "X:/" and I could just go into it save files/take files off. Would this be the same sort of thing? 

Ok, let me run this by you... You talked about bitTorrent in an interesting way. Let&#8217;s say I have a torrent file on my laptop and want to download the file directly to my server. Am I able to do this?

Thank you very much for the help guys. It is greatly appreciated.

---

### Post by rubbsdecvik on 2008-11-18
The only reason to use Xubuntu over Ubuntu is that Xubuntu uses less resources on your computer.  I personally use Gnome (Uubntu), but thought about switching to Xubuntu.  If you are going to be using it mostly as a file server, it won't matter much either way, as you won't be too worried about visual performance.

> Ok, let me run this by you... You talked about bitTorrent in an interesting way. Let’s say I have a torrent file on my laptop and want to download the file directly to my server. Am I able to do this?

You could do this fairly easily.  You just would have to set up a shared folder on the (X)Ubuntu box and then use it on your laptop.  There's other ways too.  For example.  You could do the whole thing on the (X)Ubuntu box and just share the completed file.  you can do this by.

Starting the torrent on the file server and saving the completed file to a shared folder.  Then you can connect to that folder with your other computers.

---

### Post by chaulkster on 2008-11-18
Thanks guys.

This should get me up and running... I will probably have some more operating questions later.

Once again, thanks for taking the time to lend a hand.

---

### Post by egalvan on 2008-11-18
> **chaulkster said:**
> Hello all,
I am seeking assistance

AMD 3200+ processor, Asus A8N-E motherboard, some older ATI Radeon graphics card, 1024mb RAM and a 200 GB hard drive. 

So if you lasted this far could you please help me with a few questions:

1. Is this do-able or even a good solution for me?
2. Will my old computer be up to the task?
3. Will I need any other hardware? (I'm on tight budget here)
4. How do even go about using it when it’s up and running?
5. I read on another websites that you should partition the drive(s) and store different categories of files in each partition... I don't see the benefit in this.
6. what’s all this hype of "FTP"... a little insight please? 

I'm a quick learner and would love to learn this type of stuff. I don't have big background in computers but I find them fascinating and would like learn more.

Anyways, thanks for the help everyone!


OK, others (including billgoldberg) have given some good advice,
but let me chime in with more.

1) Do-able? Yes. Good solution? I think so.

2) Computer up to task? Absolutely. Far more than needed. Serving files requires VERY modest hardware. RAM is King, as always, and you have more than enough. CPU is FAR more than needed.
 You may find you need/want more storage, but that is just adding drives later on.
(personal file server was running AMD 1.2mHz, with 2gig RAM. Ran absolutely fine.)

3) Need other hardware? Doesn't sound like it. It does have a network connection, right? The only extra would be more drive space. (Remember Wilkinson's Corollary to Moore's Law..."stuff expands to fill available space").

4) How? Read the article billgoldberg linked to. It explains rather well.

5) Seperate os and data?  PERSONALLY, I have ALWAYS separated the operating system from my data, and separated data "types" also...
 Using separate hard drives if possible.
 Using separate partitions if not.
On my current server I use at home, I have the operating system spread across three hard drives (SCSI), and my data spread across some ten hard drives (PATA & SATA).
 The critical stuff (mainly financial, but also pictures) is on a mirrored RAID.
The rest..
 music (all LP's, cassettes, CD's I own)
 movies (almost all DVD's I own),
 downloads,
 etc.
All on separate drives.

Downloads is the smallest of the drives. (80gb)
Miscellaneous is also 80gb
Music has passed 180gb
Video has hit 800gb (I started buying HD-DVD and Blu-Ray)

and yes, it is a LARGE case. It holds 24 drives!! Dual power supplies. I got a smokin' deal for a Lian-LI server case on eBay a few years ago. Totally damaged packing, the insides were perfect. 
Your mileage will vary.

6) FTP? You don't need it for what you want to do.


Now...
Xubuntu versus Ubuntu.

Xubuntu (XFCE) uses fewer resources. Ubuntu (Gnome) uses more.
But you have PLENTY of resources, so go ahead and use Ubuntu, it will make your life easier.


And since you like to "play around with computers", I recommend "playing" with this set-up before getting serious with it.
Experiment, then start using it for real.

If you want to totally wipe that original hard drive, then I recommend, as always,
 Darik's Boot and Nuke. 

dban.org

For partitioning before installation, I recommend, as always,
 PartedMagic LiveCD

partedmagic.com        <--- (don't forget to tip the authors)


And finally, the only "dumb questions" are the ones you don't ask.

ErnestG

---

### Post by cariboo on 2008-11-18
> 3. Will I need any other hardware? (I'm on tight budget here)

Every one seems to ignore this question or say you are OK. You are OK until an equipment failure. If your data is precious, have a good backup strategy. I would suggest getting an external drive when you can afford it (but don't wait to long), at least the same size as the hard drive in your server. Even better would be to have 2 external drives and keep one off site at all times.

I personally have data important to me (photos and business data) backuped up on 4 different hard drives.

Jim

---

### Post by rubbsdecvik on 2008-11-18
> **cariboo907 said:**
> Every one seems to ignore this question or say you are OK. You are OK until an equipment failure. If your data is precious, have a good backup strategy. I would suggest getting an external drive when you can afford it (but don't wait to long), at least the same size as the hard drive in your server. Even better would be to have 2 external drives and keep one off site at all times.

I personally have data important to me (photos and business data) backuped up on 4 different hard drives.

Jim

He has a point.  When I said that you were ok with your hardware, I meant that your hardware can run this type of load with little to no problems, but hardware failure can suck.  I suggest either using a backup plan like the one cariboo907 mentioned, or save things on both your laptop and on this shared server.  There are syncing software packages you can use to make this copying/mirroring easy and with minimal effort.  You can ask around for what you think is best.  

As just a file server (ignoring all accounts of hardware failure) your computer is more than ready.  Just FYI.

---

### Post by egalvan on 2008-11-18
> **cariboo907 said:**
> Every one seems to ignore this question or say you are OK. You are OK until an equipment failure. If your data is precious, have a good backup strategy. I would suggest getting an external drive when you can afford it (but don't wait to long), at least the same size as the hard drive in your server. Even better would be to have 2 external drives and keep one off site at all times.

I personally have data important to me (photos and business data) backuped up on 4 different hard drives.

Jim

Well, as I stated in my post...

*The critical stuff (mainly financial, but also pictures) is on a mirrored RAID.*

It is a HARDWARE RAID. If one drive fails, it will warn me, and stop using the drive until a new one is installed **and mirrored**.
I further have a separate drive that is in a fire-resistant safe.
This holds critical stuff, including papers.

But at what point are we OK? If a hot-enough fire destroys my home, the safe may give way.
A burglar may ransack my house, and cart it away.

Are your four drives physically inside your house?
A tornado may wipe it out.
Is one copy at a friend's house?
A hurricane may destroy his house.
Is one copy in a safe-deposit box at your bank?
What if the bank goes under? How long before you can access it?

Sorry for the post, don't want to sound mean, so take it lightly, please.
One has to find an end to the possibilities of failure.
And only you can find what works for you.:)

ErnestG

---

### Post by Sable683 on 2008-11-18
I know that you are trying to make a file server with Xubuntu, but the most simple and easiest file server that I have seen is FreeNAS.

Here is a link to a 10 minute clip to set up a very simple NAS box on your home network. Even though this is designed to run as a NAS, I have been using this to run a file server that is accessible from any computer (windows or ubuntu) in my house for the past two years with no crashes! The major benefit is that this will work on _**VERY OLD**_ systems!!!
[http://www.youtube.com/watch?v=mgJNzyTSv6c](http://www.youtube.com/watch?v=mgJNzyTSv6c)

Just my $.02,

John

PS - Please don't hate me for offering another alternative than Ubuntu!

---

### Post by handydan918 on 2008-11-18
> **billgoldberg said:**
> Meh, that's a bit of FUD.

Unless you format or reinstall Ubuntu on the same drive your info is on, you won't have problems.

Should you mess up your install, use a live cd to copy your data to a drive.

You're young, aren't you? 

"Unless you format or reinstall Ubuntu on the same drive your info is on, you won't have problems."
Seriously. That's a little like saying "Everything will  be alright as long as nothing goes wrong".

:lolflag:

---

### Post by Kellemora on 2008-11-18
Hi Chalkster

If you still have that old machine around, you may want to have a look at Edubuntu!

I know nothing about servers and want to learn, so I took an older machine and loaded Edubuntu on it, because it's already set up as a server designed to use thin clients.  I didn't want thin clients, but I figured what better place to start than with something that WORKS out of the box so to speak.

For me it was the easiest way to get my feet wet!

Now I'm in over my head, hi hi..........

TTUL
Gary

---


---
title: "Does It Really Take This Long?"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by SarahMarieNC2 on 2008-09-13
Okay, so I'm trying to just  get a working OS on my computer. It came with Vista and the Vista SP1 crashed it. It's refurbished so out of warranty. I ordered and paid for HP Recovery cds. They didn't work. I have a  boot mgr missing error and all the methods to fix this involve 1) cds that I can't get to work because I cant boot to the desktop or 2) a windows vista cd that I also dont have because my computer didnt come with one...  So someone told me about ubuntu. That's where you all come  lawin...

I tried to download it and it says it was going to take 7 hours!!! I'm on a wireless internet connection using my mother in laws laptop. Egads! 7 Hours??!!!!! It got to 33%  and then the internet got disconnected... I've tried a  few more times but the connection just isn't stable enough to get it completed.

So I ordered the cd... but the site says that can take 6-10 weeks???!! Seriously??? Is there a something I'm missing here or am I just going to have to wait it out. At this point I just want to get my computer working so I dont have to borrow my mother in laws... Is there something smaller that won't take so long? 

Thanks in advance.

Sarah

---

### Post by ninch on 2008-09-13
7 hours is a little long. I installed ubuntu a couple of weeks ago and it took about half an hour. 

It depends on your internet connection. The faster your connection is, the faster the file will download. My internet connection is pretty fast, which is why it took only half an hour.

It seems that your internet connection was not very stable, as you said, which probably affected the speeed of the download. If you can, try downloading the file with a more stable and faster internet connection.

---

### Post by ChanServ on 2008-09-13
try downloading ubuntu via torrent, the ubuntu torrnets are usualy faster than the site and it wont shut down, but it still may be slow due to you quality of your internet connection.

---

### Post by Tatty on 2008-09-13
If you order the CD to be shipped for free then it can take quite a while I believe.  However if you pay for shipping it can come quicker.

7 hours seems like a long time to me, I can download ubuntu in around 10 minutes on a 10Mb connection.

If you have a decent connection speed then it could be that theres just a lot of server traffic, try a different server or try later.

You could always try to find a decent download manager which can resume broken downloads... I *think* Firefox 3 has one built in.

---

### Post by skippuff54 on 2008-09-13
you could try download the ISO image with a torrent client. never done it myself but im sure others have.

what i'd do is go to a buddy's house with a couple of blank cds, download the ISO image (should take <20 mins MAX), use the md5 checksum to make sure the download went ok, burn the ISO image to the disc, pop it in to his/her cd drive, use the check cd for defects option...if it's all good at that point then go back home and being your install

of course with ubuntu, you can use the livecd option as well from the same disk you make to run ubuntu without actually installing it. that will help you decide if you want to go with it.

but from what you've said, doesn't seem like you have much of a choice.

---

### Post by kellemes on 2008-09-13
> **SarahMarieNC2 said:**
> So I ordered the cd... but the site says that can take 6-10 weeks???!! Seriously???

I assume you "ordered" for free from [shipit]("https://shipit.ubuntu.com/")?
As far as I know you should have your disk within days.

---

### Post by OutOfReach on 2008-09-13
It does depend on your internet connect and the location you are downloading from, try downloading from another location.

---

### Post by Mornedhel on 2008-09-13
Short answer is "no, it won't take so long". I got mine in under 10 days (I live in France).

Long answer is "no, it probably won't take so long, but if you need a really lightweight but not so easy to install and certainly not as complete or good-looking distribution, try Damn Small Linux while you're waiting, it fits on 50 Mb".

7 hours is pretty long, even for a 600+ Mb CD. Are you sure you weren't downloading the DVD version ?

---

### Post by Zzl1xndd on 2008-09-13
Heres a link to the Torrent page download, at least if you get disconnected you wont have to restart.

[http://releases.ubuntu.com/8.04/](http://releases.ubuntu.com/8.04/)

---

### Post by niccholaspage on 2008-09-13
This is why dialup and sometimes broadband stinks.Try downloading it on another PC and burning it from there.

---

### Post by jmcgovern on 2008-09-13
Agreed on where you're downloading from.  When I tried the first time, I selected the University of Colorado location, because I'm in Eastern Kansas.  It was going to take about as long as you're experiencing.  I cancelled and reselected the Chicago mirror.  Took 30 minutes.  Do you have a USB drive?  If that connection's too slow/has issues, you might think about downloading from a public access computer, if one's available, to USB.

---

### Post by LowSky on 2008-09-13
> **kellemes said:**
> I assume you "ordered" for free from [shipit]("https://shipit.ubuntu.com/")?
As far as I know you should have your disk within days.

> **Mornedhel said:**
> Short answer is "no, it won't take so long". I got mine in under 10 days (I live in France).


Hi I ordered mine and it took 4 weeks to get to New York. i completely forgot about them and was surprised They even came in. It all depend pon where you live I guess.

As for recovering the Computer, HP should have a restore partition on it that can be accessed during start up. It should fix everything

---

### Post by dESAI on 2008-09-13
If you have issues downloading Ubuntu, I recommend you use a download manager like Free Download Manager. It will not spead it up, but you can resume your download.

---

### Post by rcommer on 2008-09-13
Another method would be to use wget. wget is a utility you can download [_HERE_]("http://gnuwin32.sourceforge.net/downlinks/wget.php")

WGET is a tool used to retrieve files from the www, much like FTP.

Once you download the file, run the setup and install wget. 

Once installed, open your command line in windows: 

Start > Run > type "cmd" then click OK

Notice your prompt is the location you are currently in, Most likely it will be C:\Documents and Settings\<username>:

If you type "wget" then hit the enter key, you should get some usage text for wget. 

Now that wget is functioning on your system, this is where the magic comes in. 

Issue this command:

wget -o log.txt -t 0 [http://mirrors.cs.wmich.edu/ubuntu-releases/hardy/ubuntu-8.04.1-desktop-i386.iso](http://mirrors.cs.wmich.edu/ubuntu-releases/hardy/ubuntu-8.04.1-desktop-i386.iso) 

******Note - You can use any url that points to any downloadable file***

Now hit enter and go on about your business.

This will take a bit to download depending on your connection, but the beauty of the above method is: 

1. It logs the progress of the download (You can open the file in notepad and check on the progress of the download)

2. The -t option will tell wget to retry the download and resume from where it left off. 

You can literally set it and forget it!!!

I highly recommend verifying the download by following the checksum method described [_HERE_]("https://help.ubuntu.com/community/HowToMD5SUM") (This will save you much frustration).

---

### Post by SarahMarieNC2 on 2008-09-13
Thanks everyone :) I know lots of bits and pieces about computers but never done anything like this.

To the person who mentioned  the HP partition, we tried that. It didnt work. We tried two sets of HP specific recovery disks for my computer  build, they didn't work. We did high level and low level harddrive erase. We did Smart Self Tests short and extended on the harddrive. I took it to Firedog and had a diagnostic done on it. Nothing is wrong with the machine structurally speaking. They wanted to charge me $130 to put Vista back on it. I won't tell you how I feel about that ;)

Okay, now, going to go and try to get this ubuntu to download. On a side note, those of you who use it.. how do you like it? I'm pretty simple to please. The computer I had before I bought my new one ran Windows 98. So I don't see not liking ubuntu. Even if it takes a little getting used to. 

Thanks again, and sorry I ran off on a tangent. 

Sarah

---

### Post by richg on 2008-09-13
I live on the east coast of the USA. PM me with your mailing address and I will send a DVD for free of 8.04 that I used to install on my desktop.

Rich

---

### Post by Mornedhel on 2008-09-13
I think Ubuntu hits the right spot between hiding the internals and being easy to use. There are excellent CLI tools for pretty much every conceivable task (an advantage shared by all Linux ditributions) and good GUI tools for those who need it.

You can spend your life on the terminal, but you don't *have to*. Likewise, you can point-and-click through everything, but you don't *have to* : automating tasks through shell scripts and [insert your favorite scripting language here] scripts is horribly useful. You may never want to go back to Windows.

I know the only reason I keep a Vista dual-boot is for
1. games : sadly, with everyone developing for DirectX I can't really see the situation evolving, even though there *are* good toolkits for Linux
2. Office 2007 : some of my fellow students insist on using .docx, which is not supported by OpenOffice (or KOffice or gnome-office or anything), unless that plugin made tremendous progress in the last three months.

Oh, and having a centralized repository for installs and updates really changes your life.

---

### Post by Gumpers on 2008-09-13
> **SarahMarieNC2 said:**
> Okay, so I'm trying to just  get a working OS on my computer. It came with Vista and the Vista SP1 crashed it. It's refurbished so out of warranty. I ordered and paid for HP Recovery cds. They didn't work. I have a  boot mgr missing error and all the methods to fix this involve 1) cds that I can't get to work because I cant boot to the desktop or 2) a windows vista cd that I also dont have because my computer didnt come with one...  So someone told me about ubuntu. That's where you all come  lawin...

I tried to download it and it says it was going to take 7 hours!!! I'm on a wireless internet connection using my mother in laws laptop. Egads! 7 Hours??!!!!! It got to 33%  and then the internet got disconnected... I've tried a  few more times but the connection just isn't stable enough to get it completed.

So I ordered the cd... but the site says that can take 6-10 weeks???!! Seriously??? Is there a something I'm missing here or am I just going to have to wait it out. At this point I just want to get my computer working so I dont have to borrow my mother in laws... Is there something smaller that won't take so long? 

Thanks in advance.

Sarah
for what its worth I had same problem down loading from two different sites told me 10 or 11 hr although i have dsl. to make a long story short i did down load from the sites. But neither cd would work, so i order one, took  some time to receive it but it loaded with no trouble.

---

### Post by billgoldberg on 2008-09-13
> **SarahMarieNC2 said:**
> Okay, so I'm trying to just  get a working OS on my computer. It came with Vista and the Vista SP1 crashed it. It's refurbished so out of warranty. I ordered and paid for HP Recovery cds. They didn't work. I have a  boot mgr missing error and all the methods to fix this involve 1) cds that I can't get to work because I cant boot to the desktop or 2) a windows vista cd that I also dont have because my computer didnt come with one...  So someone told me about ubuntu. That's where you all come  lawin...

I tried to download it and it says it was going to take 7 hours!!! I'm on a wireless internet connection using my mother in laws laptop. Egads! 7 Hours??!!!!! It got to 33%  and then the internet got disconnected... I've tried a  few more times but the connection just isn't stable enough to get it completed.

So I ordered the cd... but the site says that can take 6-10 weeks???!! Seriously??? Is there a something I'm missing here or am I just going to have to wait it out. At this point I just want to get my computer working so I dont have to borrow my mother in laws... Is there something smaller that won't take so long? 

Thanks in advance.

Sarah

Depeding on your internet connection, 7 hours could be accurate.

Use the torrent instead of the http link to download.

If you lose your connection with a torrent download, you can just resume where you left off once you get your connection back.

If you don't know how to use torrents, google will help you.
--

PS, I would suggest your try Linux Mint instead of Ubuntu if you are new to linux.

---

### Post by SarahMarieNC2 on 2008-09-13
So I figured out part of the problem. My mother in law has WAY TOO MANY background processes running in the background. Like I literally closed maybe a dozen and went from 40kb/sec to 131 kb/sec. I wish I had a tangible copy of what processes are neccessary and which aren't so that I could help her out here. No wonder she complains about her new computer being slow! So it's still going to take me a little while, but no where near 7 hours. I've got about 40 minutes left :)

---

### Post by billgoldberg on 2008-09-13
> **LowSky said:**
> Hi I ordered mine and it took 4 weeks to get to New York. i completely forgot about them and was surprised They even came in. It all depend pon where you live I guess.

As for recovering the Computer, HP should have a restore partition on it that can be accessed during start up. It should fix everything

Mine got here in around 10 days (belgium).

They came from the UK and were shipped via Shiphol (holland). So they were a bit slow for that small distance.

---

### Post by Mornedhel on 2008-09-13
> **billgoldberg said:**
> Mine got here in around 10 days (belgium). [...] So they were a bit slow for that small distance.

Mine too (France). I think, as they don't have a lot of demand, they wait a few days, then send them in larger batches. It's worth it though. When you're trying to evangelize a friend, it looks much more attractive and professional.

---

### Post by mgranet on 2008-09-13
If you live anywhere near a Best Buy, you can go buy a copy for $10(USD) or so.

---

### Post by SarahMarieNC2 on 2008-09-13
I'm almost done downloading it now. 8% left to go.. :) Crossing my fingers this works.

---

### Post by arpanaut on 2008-09-13
This should be helpful in the near future:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Hope the DL goes well!

---

### Post by SarahMarieNC2 on 2008-09-13
Thanks so much, I was just reading something very similar, but I like your link better :) Waiting on it to burn now, we're at 92% of the burning process. I can feel myself getting antsy. I hope I know how to use thing. If not, it'll be a fun new adventure at least.

---

### Post by SarahMarieNC2 on 2008-09-13
Okay so I used the How To Burn ISO to CD and followed the instructions, had the ubuntu image when the cd was finished, put it in my computer and chose "try ubuntu without changing computer" and it asked what language, had a loading bar and then I get a scrolling page that says SQUASHFS Error Unable to Read Page; etc..... What did I do wrong? Oh yah and I used that WinSum thing to verify the download too.

---

### Post by gali98 on 2008-09-13
okay boot into the cd again and there should be an option to check cd or something like that.
It makes sure everything was burned correctly...

do that and see if it fives any errors.

Kory

edit:

Also tell us what computer you are trying to install on...

---

### Post by SarahMarieNC2 on 2008-09-13
Ha! I was just coming back to say that I did that check disk integrity option when I rebooted and it found 1 error. Ugh! I burned the ISO image to cd at 4x like suggested. Sigh! 

Oh, duh, I'm trying to install on an HP Media PC- M8100n. It has a 64 bit AMD processor so I downloaded the 64 bit Ubuntu 8.04 LTS

---

### Post by gali98 on 2008-09-13
that will work, but if you have the 32bit it will work too.
the problem was the cd probably... Your not using a cdrw are you?
that may be the problem.
Frankly I burn my ubuntu disks at full speed and have never had a problem with cd-r's so I don't know..... I would use 64bit though, as it uses your resources a little better, and, if you have 4 gig of ram will use it all.
good luck!
Kory

---

### Post by OutOfReach on 2008-09-13
32 bit also works on 64 bit processors...

---

### Post by SarahMarieNC2 on 2008-09-13
I have 3 Gig RAM. I was using a cd-r. In the template it said to burn it at 4x or  8x because otherwise it can lock up or something to that effect. I'll try to burn it again doing full speed and see if that works. I hope it does, I want my computer back.

---

### Post by SarahMarieNC2 on 2008-09-13
Okay, I burned it at max speed and this one didn't have any errors, so lets see what happens.. thanks everyoen so much for all your help.. Im gonna read a little about first time using ubuntu and then go play :)

---

### Post by gali98 on 2008-09-13
sometimes burning at high speeds can cause an error, so that's why they tell you to do it at a low speed. You just happened to be lucky enough to burn a bad disk :)
I would try out the live cd (the "try ubuntu" option) a while before installing to make sure you are ready.
Also always make sure to back up your files that you need to a disk or something so you will have them for ubuntu

Enjoy!

Kory

---

### Post by SarahMarieNC2 on 2008-09-13
> **gali98 said:**
> sometimes burning at high speeds can cause an error, so that's why they tell you to do it at a low speed. You just happened to be lucky enough to burn a bad disk :)
I would try out the live cd (the "try ubuntu" option) a while before installing to make sure you are ready.
Also always make sure to back up your files that you need to a disk or something so you will have them for ubuntu

Enjoy!

Kory


On the plus and minus, there's nothing to back up. HP had me do a bit by bit erase, took over 5 hours  For my 500 GB harddrive. I don't even want to talk about everything I lost... that was supposed to be on the data migration cd Firedog charged me $100.00 for. Sigh!

So on the plus side, I didn't have anything to lose and on the minus side, I lost everything. LOL! I've been checking out ubuntu. The install worked :) 

So now I have another question. I guess I should start a new thread since it's about something else... lol. ... or maybe I should just call this one "lets help sarah" and post all my questions in it LOL!

Okay.. going now...

---

### Post by gali98 on 2008-09-13
Okay good!

If you feel this thread is solved, please mark it as so.

At the top of the thread there should be a button named thread tools. In there there is a button called mark as solved.

Kory

---

### Post by skippuff54 on 2008-09-13
> **SarahMarieNC2 said:**
> So I figured out part of the problem. My mother in law has WAY TOO MANY background processes running in the background. Like I literally closed maybe a dozen and went from 40kb/sec to 131 kb/sec. I wish I had a tangible copy of what processes are neccessary and which aren't so that I could help her out here. No wonder she complains about her new computer being slow! So it's still going to take me a little while, but no where near 7 hours. I've got about 40 minutes left :)

is she runnin windows? if so, that's probably all kinds of spyware, adware, trojan horses etc.

you can put spybot  - search and destroy on her computer for spyware; ad-aware for adware; avg or avast! for antivirus. all available from download.com

it will take several hours total to download those and run all the scans, but it will drastically help her as well as offer future protection.

or you can just put ubuntu on her machine ; )

oh and get her some firefox.

---

### Post by mczonie on 2008-09-16
> **SarahMarieNC2 said:**
> So I ordered the cd... but the site says that can take 6-10 weeks???!! Seriously???

They say 6-10 weeks, but I got mine a lot quicker than that. I don't remember exactly how ling it took, but probably less than 2 weeks.

---


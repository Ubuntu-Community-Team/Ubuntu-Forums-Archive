---
title: "[SOLVED] Installing Ubuntu on my wifi laptop......."
date: 2008-09-15
forum: New to Ubuntu
---

### Post by jakewc2 on 2008-09-15
I have been trying to work out which was the best way to install Ubuntu on my laptop, either using a partition, or using Wubi. I had to reformat the laptop today, so it has very little on it. Which would be the best way to install it? 

The specs are Winsows XP SP3, with a Atheros AR5005G Wireless Network adapter, connecting to the internet via a netgear router, with an Intel(R) Core(TM) Duo CPU, T2350 @ 1.86 GHz, 1.18GBRAM.

Theres about 10gigs of free space for the partition.

With those specs can I create a partition, I just found an old Ubuntu disc, that Ubuntu 7.04 on it, that I (if its feasible) could use to create the partition with.

Any ideas?

John.

---

### Post by boblemur on 2008-09-15
i would make ubuntu its own partition. i also suggest you either download the new ubuntu or request one to be sent to you (alot of isp's host them, and so do alot of uni's so if you are tight on bandwidth you may be able to find unmetered downloads for them)

---

### Post by billgoldberg on 2008-09-15
According to this:

[http://madwifi.org/wiki/Compatibility/Atheros](http://madwifi.org/wiki/Compatibility/Atheros)

Your wireless card works out of the box with Ubuntu.

So you're good.

I would suggest you give Ubuntu it's own partition.

Running it under Wubi will give a worse experience than a real install would.

--

ps: take a look at the guides (codecs, customzing), they will be **very** helpful if you are new to Ubuntu.

--

You should really install Ubuntu 8.04 and not 7.04.

Download the gparted live cd and burn it as an image. I believe gparted is on the Ubuntu live cd, so you could use that one also (could be called gnome partition manager).

Again, install Ubuntu 8.04 (aka Hardy Heron).

---

### Post by jakewc2 on 2008-09-16
Sorry I didnt get back to you sooner, been a bit busy.

Thank you for your message. Where are the codecs/customizing guides?

Can somebody point me in the direction of some instructions on how to partition, I've been reading posts and things but havent found anything that gives point-by-point instructions for a laptop. Just wondered, anybody around to be able to point me in some direction?

Thank you.

John

p.s. I was just wondering, have been trying to get some information on paid help from Canonical Support, had an e-mail off somebody the same day, who was taking about business details (as in what Business I was running, how many pc's I had, gave him all my details (as in I am a private customer), and not heard anything back, and that was last Thursday. Has anybody had any help from Canonical? Are there any phone numbers?

---

### Post by northern lights on 2008-09-16
1. Download the 8.04 .iso from [http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download")

2. Follow [http://psychocats.net/ubuntu/installing]("http://psychocats.net/ubuntu/installing")

More of the content on the above website might be of interest also.

> **jakewc2 said:**
> I was just wondering, have been trying to get some information on paid help from Canonical Support, had an e-mail off somebody the same day, who was taking about business details (as in what Business I was running, how many pc's I had, gave him all my details (as in I am a private customer), and not heard anything back, and that was last Thursday. Has anybody had any help from Canonical? Are there any phone numbers?
Commercial support is pretty much targeted at a commercial audience...

---

### Post by stalkingwolf on 2008-09-16
Your best source for individual support is right here on this forum.
I have seen very few issues that have not been solved.

" the difficult we do immediately.  The impossible takes longer."

With a couple laptops I have had an issue with xp write protecting the HDD.
So I have ended up partitioning the drive then either leaving the second partition unformatted or formatting it fat32 so windows can see it.  Then
installing windows.  Then installing Ubuntu and using the partition manager
during install to set it up and format the way I want it.

---

### Post by jakewc2 on 2008-09-16
Hi, thank you for your message, I was just reading the download instructions, do I just download the default download, with the specs I have posted above for the laptop I have? 

I have cd's I can use to burn the download to disc, so that wont be a problem.

Thankyou again.

John.

---

### Post by jakewc2 on 2008-09-16
Hi stalkingwolf, that might cause a problem, I didnt get a copy of windows when I got my laptop, it was already installed, plus it uses the rescue option, which is how I reformated.

How will I get around that? 

Myproblem withnot having paid support is that as I have mentioend before, I am not really that technically minded with pc's, and if anything goes wrong I am not sure I have the ability to get round it. I'm not loaded with money either, so I tend to err on the side of caution, and rather pay for help than mess my pc or laptop up altogether. Which is why I chose the Wubi route for my installation of Ubuntu on my pc. I have been considering installing Ubuntu since the 7.04 version came out, but have been afraid to install it for that reason.

Since my laptop went on funny yesterday my option was reformat/rescue.

Which is why I have been asking for paid support.

---

### Post by Nepherte on 2008-09-16
Typically, the recovery option is located on a separate partition. You can safely format/delete the partition Windows is on. Often there is the possibility to burn the recovery partition to recovery cds so you don't have to keep the partition as well. You will have to check the manufacter's information. **As long as you don't delete that recovery partition**, you can go back to the original state when you received the laptop. You will have to be very careful during the 'setting up partitions' when installing Ubuntu. If you are uncertain which option to choose, consult this forum again.

I have no idea what the paid support looks like, but the support you get from the ubuntuforums members is often very good. Since the paid support people won't go to your home and give help on-site, I'd say you're good with the help you get here.

---

### Post by northern lights on 2008-09-16
> **jakewc2 said:**
> Hi stalkingwolf, that might cause a problem, I didnt get a copy of windows when I got my laptop, it was already installed, plus it uses the rescue option, which is how I reformated.

First off, you're hdd is probably not write protected. If that's the case you can go ahead and just install Ubuntu by rezising the Windows partition (defragment Windows partition first).

Should it indeed be somehow impaired, you have the right to install Windows even if the comp shipped without a CD. By buying a computer with a copy of Windows, even downloading a "pirated" Windows copy is legal as long as upon install you enter your unshared 25 digit serial number.

Plus, the psychocats tutorial is so comprehensive, that if you follow it closely, there's no way you can screw up during partitioning. Well, a power outage would make that happen...

---

### Post by jakewc2 on 2008-09-16
First off I just wanted to apologise for the way I sounded in my post about paid help, I was in no way criticising this forum. You are a really good bunch of very helpful people. I cant fault the way youhave been in the help that you have given me so far. I have learnt so much already about Ubuntu. Its just my insecurity.

I am about to try to create the partition now. I just completed the defrag, so my laptop is ready.

I'll keep you posted on how I do.

---

### Post by jakewc2 on 2008-09-16
Oh dear. The installation seemed to go ok. When it started first time there were launchers, then it said I needed to install updates which I did, and now the launchers wont start. Nothing happens I cant even open a terminal.

I can right click and I have the option to create a launcher. I can find open the box with all my files  in, is it called Nautillus?

Help?


John

---

### Post by jakewc2 on 2008-09-16
How do I get back to pre updates, then I might be able to work out what went wrong. I havwe tried everything but I cant see what I can do next?

Anybody there to help please?

---

### Post by northern lights on 2008-09-16
Unfortunately, I can't exactly picture what the situation on your desktop is like.

When you double-click a launcher, the respective application does not open?

How do you run nautilus (yes, that is the name of your filemanager) then?

How are you trying to open a terminal window? "Applications > Accessories > Terminal?

Does the shortcut 'Alt+F2' open a run dialog? If so,```
gnome-terminal
```should open an instance of it.

It is further unlikely that the updates screwed your system. Possible, granted. But unlikely, still. What else did you do in the last session before the trouble started happening?

Can you give some specs on your hardware setup?

---

### Post by jakewc2 on 2008-09-16
Hi, these are the specs of the laptop

> The specs are Windows XP SP3, with a Atheros AR5005G Wireless Network adapter, connecting to the internet via a netgear router, with an Intel(R) Core(TM) Duo CPU, T2350 @ 1.86 GHz, 1.18GBRAM.

I followed the instructionson the thread 

> [http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

exactly as it was shown and it worked, I was able to start Ubunt no problems,the desktop showed, there was a panel with everthing showing,even got the wifi working, then up popped the updates box, I updated, rebooted, and I can log into Ubuntu, but I get a blank desktop, nothing on it at all. 

I can bring up Nortillus by right clicking on the desktop,then going to Change Desktop Background, then Themes then install, and the Nautillus appears. I cant get anythinng else to work.

---

### Post by jakewc2 on 2008-09-16
How do I get it so that I can revert back to efore the updates, then I can see what happens.

---

### Post by jakewc2 on 2008-09-16
ah, got a terminal running, what next? I need to be able to bring up a panel with the normal Applications, Places, System etc. That doesnt load when Ubuntu loads after entering my username and password, like it did before the update.

---

### Post by northern lights on 2008-09-16
First off, I'm sorry I had forgotten/missed the specs - it's past midnight in central Europe...

I find it hard to single out your problem's possible cause(s) and I unfortunately know I won't come up with any decent idea tonight anymore.

Here are a few things off hand:

If I understand you right, the top and bottom panels do not appear after log-in and no icons are shown on the desktop.

After the initial install, nothing but you're partitions were shown, right? If you haven't moved a file to the desktop, they might just not be mounted. In nautilus, try moving a file to /home/USER/Desktop, where USER is your username. Does it show?
If not, nautilus (very anti GNU/Linux policy, this application also draws the desktop) is not drawing it.```
Alt+F2 > gnome panel
```should run the panels (of course, not a long-term solution).

Do you know whether you ran a kernel update also? How many updates where offered? Hundreds?
If so, you should be able to select an older kernel version (current Hardy main repository is on 2.5.24-19, the .iso's is 2.6.24-16, I think) from the GRUB menu. If you're GRUB menu does not show at boot, hit 'ESC' when it says 'GRUB loading - stage 1.5'

Best of luck, good night.

---

### Post by niglet101 on 2008-09-16
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by jakewc2 on 2008-09-16
hi, thanks for getting back to me, its late for me too, midnight, I'm in the UK.

A lot of what you have said makes not a lot of sense as I am new to Ubuntu.

125 updates were offered, like a fool I didnt check.

Before updates I had everything working, it was only since the updates the dektop stopped loading. 

I'll try to make see if I can understand what you mean, have a good night. :)

---

### Post by jakewc2 on 2008-09-16
help?????

Is there anybody else there that might be able to help? I just dont understand why the desktop is not loading?

---

### Post by jakewc2 on 2008-09-17
Well, I have to say and I feel dissapointed saing this, after my initial really good support cover on another issue, I am not very happy at all, especially since I voiced my concerns/need for paid suuport, and then being told that this is the best place for help anyway. Since I started this thread, I have felt a bit like I've been left in a sinking ship with no life-jacket, I feel like I'm being ignored here. Thanks guys.

---

### Post by northern lights on 2008-09-17
Canonical charges $250 per year for PC support during business hours and $2,750 per year for round-the-clock server support...

Anyhow, don't give up on either your comp, GNU/Linux, or the community so quickly.

I'll try to phrase my last pose in more layman like terms:

If I understand you right, the top and bottom panels do not appear after log-in and no icons are shown on the desktop.

After the initial install, you saw icons with harddisk images named after your partitions and nothing else on the desktop?

If you haven't moved a file to the desktop, they might just not be mounted (added to the filesystem). 

Can you drag and drop a file to the desktop from a filemanager window? In nautilus, try moving a file to /home/USER/Desktop, where USER is your username (go to your home directory, hold-click on any file, move it ontop of "Desktop" and let go of the mouse). Does it show?

If not, nautilus (very anti GNU/Linux policy, this application also draws the desktop) is not drawing the desktop.

Pressing 'Alt+F2' and typing```
gnome-panel
```should manually restore the panels (of course, not a long-term solution).

If you had had just a few updates of application they could not possibly have broken your system. If indeed the updates are the culprit it's most likely the kernel update. A kernel is the piece of an OS that allocates system resources to applications.

An updated Hardy runs on the kernel with the version number 2.5.24-19, the .iso comes with 2.6.24-16, I think. If a kernel is updated, the old one is not deleted by default. So you can select to boot with an older kernel from the GRUB menu. If you're GRUB menu does not show at boot, hit 'ESC' when it says 'GRUB loading - stage 1.5'. Select to run 2.6.24-16.

[EDIT]
P.S.
These forums are very active, not only in posts but also in terms of new threads and support requests. Had no one answered your thread might have been found cause it would have had 0 answers. It simply ended up on page whatnot and got lost in the haystack. Bumo your thread periodically if you feel it needs more input.

Plus, if this doesn't work out in a while a new thread with a more descriptive topic title might be in order as your situation has changed.
[/EDIT]

---

### Post by jakewc2 on 2008-09-17
Hi everybody, well I just need to say, I have the problem sorted, it was a profile problem, not sure exactly what the problem was,but we fixed it by adding a new profile and transferring admin privileges over to new profile. 

I went onto the irc Ubuntu irc channel, #Ubuntu-uk. If you cant find an answer here, try the IRC channel, as well. Two people in there:-

davey and popey (popeydc on these forums)

I just wanted to say thank you to them for the help they gave me this morning to sort it out.

I now have both ethernet and wifi connection on a partition on my laptop.

Thank to everybody who helped.

John.

---

### Post by stalkingwolf on 2008-09-17
One thing that would be good to remember, the people on this forum
are scattered WORLD WIDE. Time zones are a bitch. When you are in the 
middle of your day raring to go, I am most likely (hopefully) sleeping.

So the " impossible take a little longer" has several meanings.  Many times
a delay in response is nothing more than timezones.  Others it is the time it takes the UNPAID members of this community to research the problem and
attempt to arrive at the CORRECT answer.

I know I and I am sure others have, when resources are available tried to recreate issues that new users have had to find answers.  This also takes
time.

We are not ignoring you.  We are trying to help in the best way we know how.
We also have Jobs , Families, and lives.

As an example, I am currently installing several browsers on my laptop
in an effort to find one that will work with the " yellow flag black rodent" internet provider that we have at the resort where I work.  There
website will not display on Firefox, you get a blank page.  When I finish
I will have a Live CD with which I can boot any guests laptop from their
room,and be connected to the internet. In spite of their winblows wifi manager.  This service is of course also UNPAID.

I never thought I would ever , in any way fall into the classification of " Developer".

> I have felt a bit like I've been left in a sinking ship with no life-jacket, I feel like I'm being ignored here

Thats OK . Daily I feel as though I am re-arainging the deck furniture on the Titanic.

---

### Post by jakewc2 on 2008-09-17
Hi stalkingwolf, I'm really sorry that I came across as being ungratefull. I do underrstand. It was kind of frustrating, being told that there would be support, and none was there. I know this is done free of charge, I also did mention that I woul be willing to pay for the work done. I still am. Not that that would give me any extra's I would just know that the work would be done sometime, and I wouldnt have to worry about it. I kind of got into a panic.

I do appreciate what has been done for me. 

One last thing, the specs on my graphics card, somebody on here mentioned that it would work with Ubuntu, it does, for some reason it makes the interface look like the old Windows '98 did, plus its not giving me any chance of doing anything with the way Ubuntu looks. In windows it looks ok and I dont have any problems with graphics. (at least the graphics of the basic stuff I do)

What graphic cards work best with ubuntu? If I could find out, I could contact the supplier of my laptop to see if I can upgrade it. 

Thank you again,

John.

---

### Post by stalkingwolf on 2008-09-18
I may be missing something here. I cant seem to find where you mention
what graphics card you have.

I had a problem with my video adapter in my desk top. I found a solution
playing around.  I have the VIA/S3G unichrome Pro IGA which is also used
in several laptops.  I cured my low resolution/driver problem when I installed UbuntuEEE 8.04.1.  8.04.1 might also fix this issue, I dont know.
I havent had the need to down load it. I have the EEE version for my EEE701
and it works great.

---

### Post by jakewc2 on 2008-09-18
thank you for getting back to me, sorry about the lack of information, I thought I had added it. :(

I was just wondering, where do I look to find out where the specs are for my pc in Ubuntu, cant seem to find them.

---

### Post by jakewc2 on 2008-09-18
To see if I can find it I rebooted and went into windows, where I did find it.

Its a VIA Chrome9 HC IGP Familly. Hope that helps.

I wonder if you could still point me in the direction of where I could find the info on Ubuntu though, it would be a big help.

I am spending more and more time on Ubuntu rather than Windows.

Thank you for your help.

John.

---

### Post by stalkingwolf on 2008-09-22
try looking in System > Administration > Device Manager.  If device manager
isnt there you can install it from synaptic package manager.  Search for
Gnome Device Manager.   When installed you will find it under Applications
System tools ( at least that is where mine is).

---

### Post by jakewc2 on 2008-09-22
Hi, thanks for the help, I just installed it, its really useful.

---


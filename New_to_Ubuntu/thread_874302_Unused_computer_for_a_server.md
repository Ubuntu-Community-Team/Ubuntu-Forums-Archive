---
title: "Unused computer for a server?"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by iSuck on 2008-07-29
Hello,

I have three computers at my disposal. A laptop and 2 desktops. No, I am not spoiled. My dad just buys new computers and give his "old" ones to me. So, I have a macbook, a modded Dell tower w/ XP and Ubuntu, and an unused Sony VAIO.

I hate seeing a computer to go to waste. I can't sell it, cuz who the hell wants to buy a 6 year old comp with a weird OS named "Xubuntu", and no way I would reinstall Windows ME. Well, I can't give it away, cuz I might have a wacky idea and f____ around with it, so I made my research. 

Many web articles recommend of using the old computer in the corner and try to make a server out of it by using linux. Then some IT guy use his way of words to explain, which gets convoluted easily in my head. 

Here is my question:

-I still have a vague perspective of what a server is, what is it? and please dumb it down for me.
-I also remembered that there are different types of servers, what are they and what do they do?
-If you could, can you give me a recommendation on which type I should work on first to mess around with?

Many Thanks in advance!!

Sinc,
TN

---

### Post by Haioko on 2008-07-29
Servers are powerful machines which do many MANY tasks and communicate with other clients (computers)

Servers are used for things like uploading your website onto the internet, or hosting game matches. (like counter-strike or WoW)

They are also used to distribute software around a LAN or to share perepherals.

You really shouldn't have the need for a server unless your running a buisiness of some sort. Or if you have a gaming clan. But these machine have to be quite powerful as they have to be on 24/7 and have to get constant updates to keep the software up-to-date and all the people using the server can have optimum performance.

---

### Post by MatthewPlanchard on 2008-07-29
However, you can use your spare computer as a super mega ultra backup storage device. Set it up on the network and have simple backup config do daily backups to that machine, and never worry again.

---

### Post by tuxxy on 2008-07-29
Take a look at the server guide;

[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

---

### Post by Joeb454 on 2008-07-29
> **Haioko said:**
> Servers are powerful machines which do many MANY tasks and communicate with other clients (computers)

Servers are used for things like uploading your website onto the internet, or hosting game matches. (like counter-strike or WoW)

They are also used to distribute software around a LAN or to share perepherals.

You really shouldn't have the need for a server unless your running a buisiness of some sort. Or if you have a gaming clan. But these machine have to be quite powerful as they have to be on 24/7 and have to get constant updates to keep the software up-to-date and all the people using the server can have optimum performance.

That's not true at all (ok *some* of it is).

I ran a web-server and IRC bot (amongst other things, such as file sharing, ssh/sftp server etc.) from a 7 year old 1Ghz P3 with 256Mb RAM, with absolutely no issues.

I ran it from home too :) Either way, I think that proves a large part of the above post incorrect :)

---

### Post by Haioko on 2008-07-29
In my personal opinion, just keep the desktop for something else. Use it for a gaming rig or something. Set-up a dual system. or even give it to someone else. (Grandparents or someone) Or even sell it and upgrade the system you have just now.

Servers are the most tedious things to keep maintained. It's alot of hard work and it's costly. And if you don't have a use for one. Whats the point? Keep it mate =]

---

### Post by Haioko on 2008-07-29
> **Joeb454 said:**
> That's not true at all (ok *some* of it is).

I ran a web-server and IRC bot (amongst other things, such as file sharing, ssh/sftp server etc.) from a 7 year old 1Ghz P3 with 256Mb RAM, with absolutely no issues.

I ran it from home too :) Either way, I think that proves a large part of the above post incorrect :)

Actually most of that is correct.

I'm just saying that most servers these days are used for more powerful applications than just running an IRC channel and file sharing. If thats what he wants to use it for then by all means do it lol. But I'm sure the computer can be put to better use.

---

### Post by Joeb454 on 2008-07-29
But the OP wants to experiment with servers (that's what impression I got from the post) so an old desktop would be ideal for a home server (for backups etc.) just add in a nice big hard drive and you're good to go.

I have 2 old PC's I use as servers...both were free, so they're not exactly costly either

---

### Post by ace007 on 2008-07-29
So it sounds like you are talking about making a Network Attached Storages (NAS) type of thingy.  A server is a very vague term if you ask me, wikipedia it if you must.  (Like asking somebody what a computer is)  But pretty much a server is like a computer without all the bells and whistles.  It exists to mostly handle data on a network.  A NAS is what you want to use the old computer as.  It's a little complicated though.  

If I had an extra computer I would set it up like you did your desktop, (i.e. install Ubuntu) and then just select a bunch of stuff to be shared on the network.  You can unplug the computer monitor/mouse/keyboard and leave it attached to the network and you can use it to store all you movies, music, and junk.  You can access the shared stuff on any computer on the network.  You'll want to buy more hard drives naturally.  That is the really easy and dumbed down way.  Then there is no difference between doing that and just sharing from your current desktop.  Just an extra computer connected to the network that has data being shared on it.   

You could instead install a server distro that has absolutely no bells and whistles, not even a graphical display.  You can keep on adding things (i.e. RAID) to the server to make it more complicated, but you should read up first.  That would be ideal for a server in your home network.  

The question you have to ask yourself is if you need a centralized place where all(or some) of your data is stored and can be accessed by multiple computers that may not always be turned on or present.  If you have a house full of laptops then a NAS is a great idea.  Because you dont want to keep all your data on one laptop, and then when that one is gone, everyone on the network cant access its data.  

OR a house with a single desktop with no hard drive space, NAS again isn't a bad idea.

OR you need to offload some network and/or backup tasks from your own computer to a dedicated server.

But unless you go the complicated route of setting up a nice server, you should just share the data from your current desktop assuming it is always on.

---

### Post by Haioko on 2008-07-29
> **ace007 said:**
> So it sounds like you are talking about making a Network Attached Storages (NAS) type of thingy.  A server is a very vague term if you ask me, wikipedia it if you must.  (Like asking somebody what a computer is)  But pretty much a server is like a computer without all the bells and whistles.  It exists to mostly handle data on a network.  A NAS is what you want to use the old computer as.  It's a little complicated though.  

If I had an extra computer I would set it up like you did your desktop, (i.e. install Ubuntu) and then just select a bunch of stuff to be shared on the network.  You can unplug the computer monitor/mouse/keyboard and leave it attached to the network and you can use it to store all you movies, music, and junk.  You can access the shared stuff on any computer on the network.  You'll want to buy more hard drives naturally.  That is the really easy and dumbed done way.  Then there is no difference between doing that and just sharing from your current desktop.  Just an extra computer connected to the network that has data being shared on it.   

You could instead install a server distro that has absolutely no bells and whistles, not even a graphical display.  You can keep on adding things (i.e. RAID) to the server to make it more complicated, but you should read up first.     

The question you have to ask yourself is if you need a centralized place where all(or some) of your data is stored and can be accessed by multiple computers that may not always be turned on or present.  If you have a house full of laptops then a NAS is a great idea.  Because you dont want to keep all your data on one laptop, and then when that one is gone, everyone on the network cant access its data.  

OR a house with a single desktop with no hard drive space, NAS again isn't a bad idea.

But unless you go the complicated route of setting up a nice server, you should just share the data from your current desktop assuming it is always on.

Pretty much what he said.

I think the best option is to use the computer as extra storage. use it for back-up. If your main system fails, you'll still have all your data on your  LAN server. And you can just fix your main system and restore all your data from the server.

---

### Post by MatthewPlanchard on 2008-07-29
Yes, and you can cover the desktop with a nice blanket or something and use it as a little table next to a couch. Just make sure you provide coasters . . .

---

### Post by Haioko on 2008-07-29
I don't think the computer would be caple of doing such high level tasks such as that. You'd need atleast 1Tb hard drive just to sit the coffee on.

---

### Post by ace007 on 2008-07-29
> **MatthewPlanchard said:**
> Yes, and you can cover the desktop with a nice blanket or something and use it as a little table next to a couch. Just make sure you provide coasters . . .

Sounds like a terrific fire hazard.

---

### Post by MatthewPlanchard on 2008-07-29
> **Haioko said:**
> I don't think the computer would be caple of doing such high level tasks such as that. You'd need atleast 1Tb hard drive just to sit the coffee on.

We can get around that with 

```
sudo apt-get install xcoffeetray
```

It's the new lightweight version of the popular coffee tray module, designed specifically for older machines.

 . . . . and

It's not a fire hazard if you use a fire blanket!

Ha!

---

### Post by Haioko on 2008-07-29
What a guy.

New open source coffee tables. Just insert:
```
sudo apt-get install xcoffeetray
```
Into terminal and watch as your PC transforms into your favourite piece of furniture!

---

### Post by ace007 on 2008-07-29
> **MatthewPlanchard said:**
> 
It's not a fire hazard if you use a fire blanket!

Ha!

Of course, the blanket would contain the fire! Just be careful to not burn your tongue on the newly heated coffee!

---

### Post by Joeb454 on 2008-07-29
*tries to push the thread back on topic*

---

### Post by MatthewPlanchard on 2008-07-29
The only thing that's not open source is the blanket! You'll probably have to get a proprietary one unless your system can install the following packages:

```
sudo apt-get install cottonfield cottongin spinningwheel loom sewingmachine libfertilization libwater libthread
```

These packages only work on incredibly modern machines, so it's likely you're going to have to go with a proprietary blanket.

But don't worry! You can get one someone else has already scripted for little or no cost, most of the time! IT's fantastic!

Edit: Oh yeah, this thread was about something . . . I almost forgot.

Okay, to return to the topic at hand, if you're not going to use it as a coffee table, or even if you are, but you want to use it as a server as well, I agree that the best option for now is to set up sharing and simply host files on it.

If you want to have a free website host or host an IRC channel or CS games or something like that, well, my expertise putters and runs out of gas right here.

My only experience with servers was a pretty miserable attempt at making an Apache server on one of my old XP machines several years ago. It didn't work!

---

### Post by Haioko on 2008-07-29
Haha alright. Lets listen to the staff :P

I'm surprised that iSuck hasn't posted back yet.

---

### Post by MatthewPlanchard on 2008-07-29
> **Haioko said:**
> Haha alright. Lets listen to the staff :P

I'm surprised that iSuck hasn't posted back yet.

At first I thought you were insulting someone! And then I realized that the poster's nick is iSuck . . . and laughed.  Great handle.

---

### Post by Vivaldi Gloria on 2008-07-29
> **iSuck said:**
> ... using the old computer in the corner 

[http://www.dailycupoftech.com/2007/09/17/put-that-old-computer-to-good-use/](http://www.dailycupoftech.com/2007/09/17/put-that-old-computer-to-good-use/)

[http://kmandla.wordpress.com/2007/03/16/ten-things-you-can-do-keep-an-old-computer-useful/](http://kmandla.wordpress.com/2007/03/16/ten-things-you-can-do-keep-an-old-computer-useful/)

---

### Post by thedevnull on 2008-07-29
> **iSuck said:**
> Hello,

I have three computers at my disposal. A laptop and 2 desktops. No, I am not spoiled. My dad just buys new computers and give his "old" ones to me. So, I have a macbook, a modded Dell tower w/ XP and Ubuntu, and an unused Sony VAIO.

I hate seeing a computer to go to waste. I can't sell it, cuz who the hell wants to buy a 6 year old comp with a weird OS named "Xubuntu", and no way I would reinstall Windows ME. Well, I can't give it away, cuz I might have a wacky idea and f____ around with it, so I made my research. 

Many web articles recommend of using the old computer in the corner and try to make a server out of it by using linux. Then some IT guy use his way of words to explain, which gets convoluted easily in my head. 

Here is my question:

-I still have a vague perspective of what a server is, what is it? and please dumb it down for me.
-I also remembered that there are different types of servers, what are they and what do they do?
-If you could, can you give me a recommendation on which type I should work on first to mess around with?

Many Thanks in advance!!

Sinc,
TN

Hey,

I would say that you should go spend some time at a local book store and find some Linux administration books.  If you don't understand the basics you will need to start from square one.  There is a lot of great Linux Administration books and they will give you more details than you can even imagine.  Truth is you can build ANYTHING on free and open source like Linux.  

Additionally, I would look up if the is a LUG or Local User Group in your town and go to the meeting because everyone will help you there.

Best,
J

---

### Post by MatthewPlanchard on 2008-07-29
> **Vivaldi Gloria said:**
> [http://www.dailycupoftech.com/2007/09/17/put-that-old-computer-to-good-use/](http://www.dailycupoftech.com/2007/09/17/put-that-old-computer-to-good-use/)

[http://kmandla.wordpress.com/2007/03/16/ten-things-you-can-do-keep-an-old-computer-useful/](http://kmandla.wordpress.com/2007/03/16/ten-things-you-can-do-keep-an-old-computer-useful/)

Good articles . . . number ten on link two makes me want to get out the paints and go color crazy on my laptop. 

Perhaps luckily, I have no paints to go crazy with.

I thought the most interesting idea of the bunch was probably the ThinClient idea.  How neat is that? You could have like 5 really old computers running at breakneck modern speed on a virtual client, limited only by Bandwidth.

PrintServer also seems like a really good idea. It's always fun to have an excuse to get up and go get something.

FaxServer is interesting, but outdated, and how does a fax use less paper than anything else? You put in one piece of paper and it gets copied somewhere else. That is still two pieces of paper.

---

### Post by JoneYee on 2008-07-29
I am using an older Hp Slimline (AMD 64 dual core) tower with 2GB of RAM for samba, printing, scanning and sql. 

Server platforms don;t need to be robust if you don't have alot of users connecting to them.

---

### Post by cariboo on 2008-07-29
I've got a 1Ghz AMD64 with 512MB serving files, music and videos, normally it works quite well, but today for some reason the nvidia nic is losing its irq and then the server goes into a kernel panic. It would be ok if the server was in the house, but it is out in my garage, so every time it locks up I have to run out there and restart it. Best uptime before the last kernel upgrade was 168 days.

Jim

---

### Post by iSuck on 2008-07-30
This guy know exactly captured my point: (Thanks)

> **Joeb454 said:**
> But the OP wants to experiment with servers (that's what impression I got from the post) so an old desktop would be ideal for a home server (for backups etc.) just add in a nice big hard drive and you're good to go.

I have 2 old PC's I use as servers...both were free, so they're not exactly costly either

What's OP? Original Pimp? oh, thanks!

But really, awesome inputs too, everybody, thanks!
So here's what I picked up:
[LIST]
[*]File sharing is a super idea (same thing as NAS, right?)
[*]A simple server to do back up task, sounds easy, ehhh right? maybe?
[*]Now I feel like I need an open source coffee table more than ever
[*]ace007, super rawking idea. (same as the first on this list)
[*]vivaldi gloria (this guy loves his classical), great links man.
[*]thedevnull, I surely will look into that. Im always open on learning new things about linux/ubuntu. emmmm, how do I find LUGs??
[*]Is "IRC bot" the same thing  as Internet Relay Chat?
[/LIST]

Again, thanks everybody.
Out of all of the ideas, I think NAS would suit me the best. I'm a (new)CS college student that has to be on the run, a lot. I'm a computer guy that hates to do his work in his house, so I have to change locations all the time, so I dont get bored of the scenery(picky, I know). If I perceive this correctly, setting up a NAS would enable syncing, or sharing, my laptop and my desktop a lot easier than what I've been doing in the past, which is using a single external hard drive and manually copy the new files onto the external hard drive and then manually copy the new files from the exthd to the desktop, WITH A SINGLE USB CABLE (god, that's annoying). 

I'm still doing research, so I'm not going to do that just yet. Plus, I'll put the others' idea to test, too, maybe except the coffee table with some blanket on fire. I'll sure update when I make my decision or change my mind.

Sinc,
TN

---

### Post by iSuck on 2008-07-30
> **MatthewPlanchard said:**
> 
...
FaxServer is interesting, but outdated, and how does a fax use less paper than anything else? You put in one piece of paper and it gets copied somewhere else. That is still two pieces of paper.

Oh man, I hate working with faxes. Reely good point, though.

---

### Post by WRDN on 2008-07-30
If the PC you currently used isn't very powerful, then you could setup a [Thin Client]("https://help.ubuntu.com/community/ThinClientHowto"), and do some of the processing on the server. This is also useful if you are doing processor- intensive tasks such as video encoding, and want to offload some processes.
If not, I think the best thing to do is set up a file server/ peripheral sharing, and then leave it. Rather than having to be at the server to configure it, you could use VNC/ SSH to remotely access it.

---

### Post by anewguy on 2008-07-30
You've seen a lot of input here about the basics of a server - just think of the name - it SERVES.  It serves data across a network.  It can serve email, web sites, etc.  It can serve storage.

I like what you are trying to do - take an unused box, experiment and learn something in the process.  I come from the old, old, OLD days of computing and the experiment to learn process was about the only one available.  So what to run?  Start simple, as suggested, but don't be afraid to experiment to add functionality to it.  Sure things get a little more complex with each thing you add to it.  But isn't this part of the challenge of learning?  Growing your server from just a file server or backup device to other functions will enhance your knowledge, and won't hurt a bit when it comes to college and eventually a resume.  I don't know about others, but even being college educated, I still learned way, way more from experimenting and learning.  I used to be a systems programmer and systems administrator on big iron, mid-frames, minis and micros, and college taught me a lot of basic things, and even perhaps more directly related, a way to look logically at a problem and work out a solution.  But experimenting on the job is how I learned so much.

So, if you can get a jump-start on some of the things you'll likely run into in college, and in a career, and want to build upon a problem solving way of thinking, go for it all you want!  Remember - you're experimenting and any mistakes are never a big deal - they just teach you more.

:)

---


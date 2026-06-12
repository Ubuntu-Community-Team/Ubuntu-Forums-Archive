---
title: "Setting Up Evolution for sbcglobal mail"
date: 2012-05-10
forum: New to Ubuntu
---

### Post by Javelin Dan on 2012-05-10
[FONT=Arial]I just thought I’d share this for the benefit of other newbies who struggle as I do sometimes. I am fine tuning my fresh install of 12.04 Ppc on my wife’s eMac G4. Setting up an e-mail client for her sbcglobal account was my final frontier as this has always given me grief. I chose to set up Evolution because for some esoteric reasons I can’t explain, I like it better than Thunderbird, the default client on this install. [/FONT]
 
[FONT=Arial]This is very simple to do *_IF_* you have the right account settings, but it can make you tear your hair out if you don’t. Trying to find them on the ATT-Yahoo site is nearly impossible. I researched this heavily before I started, and I probably got a half dozen suggestions for configuration settings. I discovered that this is probably because these settings have morphed over time as sbcglobal melted into ATT, and ATT is slowly being absorbed by Yahoo. So if you’ve had an account set up for years and then try to reconfigure it using your old settings, it probably won’t work – or at least it didn’t for me. So, it became a maddening process of trial and error to find what would work. As of May 8, 2012, here’s what worked for me:[/FONT]
 
 
[CENTER]**[FONT=Arial]Incoming Mail[/FONT]**[/CENTER]
 
 
[CENTER]**[FONT=Arial](pop)[/FONT]**[/CENTER]
 
 
[FONT=Arial]pop.mail.yahoo.com[/FONT]
[FONT=Arial]Port 995 (pop3 over SSL)[/FONT]
[FONT=Arial]SSL encryption[/FONT]
 
 
 
[CENTER]**[FONT=Arial]Sending Mail[/FONT]**[/CENTER]
 
 
[CENTER]**[FONT=Arial](smtp)[/FONT]**[/CENTER]
 
 
[FONT=Arial]smtp.mail.yahoo.com [/FONT]
[FONT=Arial]Port 465 (smtp over SSL)[/FONT]
[FONT=Arial]SSL encryption[/FONT]
 
 
[FONT=Arial]After I successfully logged into Evolution, downloaded all her mail, and sent a couple of test messages, I had one final hurdle to jump. I tried logging onto a website and sending a link via my new account. When I clicked on “send a link”, a small email window popped up that looked a little foreign and just wouldn’t work. After scratching my head for a couple minutes, I suddenly recognized that there was a tiny Thunderbird icon in the upper corner of this window. I then realized that since Thunderbird was the default, it was naturally trying to send the link through that (which I hadn’t configured). I then went into Synaptic, entered “Thunderbird” and marked it for removal and hit the GO button. I closed out of everything, rebooted my browser and could then send links to web pages to my heart’s content. [/FONT]
 
[FONT=Arial]I know to all the experienced users, this is child’s play. But I can tell you that little niggling problems like this are the bane of newbies everywhere and are a big reason why people who are inexperienced with Linux get frustrated and migrate back to Windows. It’s often assumed that we should just all “know” this stuff through some sort of infused wisdom, but I can tell you we all don’t. As elementary as it might be to some, I’m going to keep posting my small victories for the benefit of other newbies who follow.[/FONT]

---

### Post by genterminl on 2013-02-23
Although those server addresses will likely continue to work for some time, the more official ones to use are inbound.att.net and outbound.att.net. 

I absolutely agree that this information is very difficulat to find on their site.  However, if you get the information for one of their supported email clients, you can usually adapt the settings.

---


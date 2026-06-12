---
title: "Should I install Ubuntu"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by bbawden on 2008-11-19
Hi all.

First off, I love the ethos of open source, and would not hesitate to recommend Ubuntu.

In my specific situation though, I'm not sure if it's right for me, and would like some input and advice.

My setup at the moment is a desktop that acts as a kind of server, handling shared files etc. It also has iTunes for syncing my pod. It's wired up to a router via ethernet. Also on ethernet is a Freecom Datatank NAS (500GB raid). This actually holds my media library and also my backups. I'm acutally thinking of ditching the desktop and getting a small laptop for a server. It makes much more sense to use a laptop for something that's on 24/7 because of the power consumption (plus it takes up less room).

For my main use I have a pretty specced up Dell laptop running Vista.

Now, a lot of what I do is image processing. I use Photoshop, and in my opinion GIMP just doesn't cut it for what I need.

Most of the rest of what I do is just internet browsing, general office docs etc.

I'm not sure that it's worth installing Ubuntu on my laptop, as I'd be constantly switching between that and Windows. But would it be worth installing it on the desktop?

My concerns:
-Can you remote desktop (or equivalent) to an Ubuntu box?
-How does it cope with accessing shared drives, such as my NAS?
-Would the ethernet setup cause it any problems?
-Can it share folders with windows PCs accessing it via the network?

Thanks for your input.

---

### Post by LeAstrale on 2008-11-19
I think in any case you should try to install ubuntu and set it up. The part that could be most tricky is to use ntfs for shares (sometimes causes problems)

There should be plenty of guides about how to share files between windows and ubuntu on these forums. 
And yes you can remote into Ubuntu liek you can with windows or most other OS's for that matter.

/LeAstrale

---

### Post by superprash2003 on 2008-11-19
you could definetly go about trying ubuntu for your desktop..
1) yes you can remote control using vnc
2)It should work well with your NAS
3)no
4)yes.. using samba 

Incase you require guides : 
remote control ubuntu from windows - [http://prash-babu.blogspot.com/2008/05/how-to-remote-control-ubuntu-machine.html](http://prash-babu.blogspot.com/2008/05/how-to-remote-control-ubuntu-machine.html)
samba setup howto - [http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html)

---

### Post by random turnip on 2008-11-19
> **bbawden said:**
> 
My concerns:
1-Can you remote desktop (or equivalent) to an Ubuntu box?
2-How does it cope with accessing shared drives, such as my NAS?
3-Would the ethernet setup cause it any problems?
4-Can it share folders with windows PCs accessing it via the network?

1 - Yeah, Ubuntu has one built in
2 - Should be able to, if it isn't recognised straight away you will be able to find a fix for it on the internet or this forum
3 - ethernet setups are easier on Ubuntu than wireless (trust me), they usually work perfectly
4 - Folders shouldn't be a problem, and OpenOffice can open any type of MS Office document, spreadsheet... however if you are gonna be using some less known file formats there may be problems with linux compatability, but I mean like really specialist programs, and there is usually a Linux alternative that will open them or you could run it through WINE.

Ubuntu is actually a great server.

---

### Post by bbawden on 2008-11-19
Thanks all.
I think I might take the plunge and make my server ubuntu. Seems to me that its stability makes it ideal for a server OS.

If I like it, I may make my laptop dual boot, but as I said, a lot of my stuff is photo related and GIMP, while good, is no photoshop.

What do you think of my other idea of getting a laptop (say an ASUS EeePc) to use as my server?

---

### Post by starcannon on 2008-11-19
> **bbawden said:**
> Hi all.

First off, I love the ethos of open source, and would not hesitate to recommend Ubuntu.

[LIST]
[*]Well thats a good reason to give Ubuntu a shot, and I would recommend a wubi install to start with, this lets you REALLY try before you buy so to speak, nearly as fast as a traditional install, fully configurable, and leaves you the option to uninstall it like any other windows program. Wubi is available on the default Ubuntu liveCD, just plug it in while running windows, and let it rip, it will setup a dual boot situation that if you decide later you do not like, can simply uninstall using Vista's Add/Remove programs utility.
[/LIST]
 > 
In my specific situation though, I'm not sure if it's right for me, and would like some input and advice.

My setup at the moment is a desktop that acts as a kind of server, handling shared files etc.

[LIST]
[*]I can not encourage you strongly enough to back up anything you can't live without, installing operating systems, regardless of brand, type, or versions, always runs the risk of something not going according to plan, don't be caught in the "I lost my data how do I get it back" club.
[/LIST]
> It also has iTunes for syncing my pod.

[LIST]
[*]Ipods will work with Ubuntu, even iTunes, but for both it requires a bit of working around the issues. If a perfect iTunes experience is a deal breaker, then Ubuntu might not be right for you. If however your open to other services like Amazon to mention one, or if your open to doing what it takes to make iTunes and iPods work correctly then you may reach a level of success that your happy with, as always, theres no reason you can't dual boot to make this a non-issue.
[/LIST]
> It's wired up to a router via ethernet.

[LIST]
[*]Typically wired ethernets work flawlessly, you *should* have no issue here.
[/LIST]
> Also on ethernet is a Freecom Datatank NAS (500GB raid).

[LIST]
[*]I wish I had some information, but I have never set anything like this up, perhaps someone qualified will be able to answer this detail for you, or google(I normally don't say "google it" but I really am out of my element on this particular item.
[/LIST]
> This actually holds my media library and also my backups. I'm acutally thinking of ditching the desktop and getting a small laptop for a server. It makes much more sense to use a laptop for something that's on 24/7 because of the power consumption (plus it takes up less room).

[LIST]
[*]sounds like a cool project.
[/LIST]
 
> For my main use I have a pretty specced up Dell laptop running Vista.

Now, a lot of what I do is image processing. I use Photoshop, and in my opinion GIMP just doesn't cut it for what I need.

[LIST]
[*]Some people have met a certain level of success running PS in wine, however, I would recommend keeping a dual boot situation for these sorts of things.
[/LIST]
 
> Most of the rest of what I do is just internet browsing, general office docs etc.

[LIST]
[*]You'll love Ubuntu for these activities, its very nice to surf the web and check my email, without being so worried about viruses that I have to have everything turned off. General office docs are handled very nicely by Open Office, and reviews of Open Office 3 make it sound like it is even better at certain tasks than its commercial counterpart MS Office.
[/LIST]
 
> I'm not sure that it's worth installing Ubuntu on my laptop, as I'd be constantly switching between that and Windows. But would it be worth installing it on the desktop?

[LIST]
[*]Yeah this is one of those, deals where if you don't like rebooting, then dual booting is gonna suck.
[/LIST]
 
> My concerns:
-Can you remote desktop (or equivalent) to an Ubuntu box?

[LIST]
[*]Yes, with options for all the protocols.
[/LIST]
 -How does it cope with accessing shared drives, such as my NAS?

[LIST]
[*]Looks like yes, look here [http://www.diynas.com/category/software/operating-systems/ubuntu-linux/](http://www.diynas.com/category/software/operating-systems/ubuntu-linux/)
[/LIST]
 -Would the ethernet setup cause it any problems?

[LIST]
[*]While there are no gaurantees, I don't foresee anything major, the only thing that may arise might be your wifi driver for the laptop, though I have not yet met one that would not work, even broadcoms are fine for me.
[/LIST]
 -Can it share folders with windows PCs accessing it via the network?

[LIST]
[*]Yes, using a utility called Samba, it works Very nicely and is very well documented.
[/LIST]
 
> Thanks for your input.

For your situation, it will require a bit of study on your part I think. Ultimately you could always run Ubuntu in a Virtual Machine on windows, saves you the dual boot hassels of rebooting your machine when you need something from the other OS, and when properly configured offers you all the security of linux for doing common websurfing and email tasks, while still having desktop access to all of your windows needs.

GL and fair well how ever you decide to go, at the end of the day its about having an enjoyable computing experience, and the only right way is the one that works best for you.

---

### Post by bbawden on 2008-11-20
Thanks starcannon, that was some really helpful advice.

You're absolutely right about backups. I currently backup all docs from both my laptop and desktop onto my NAS, which is a raid. I also backup onto a humyo online drive in case my whole house burns down! This is only about £40 a year for 100GB.

The only thing I don't do at the moment, which I really should, is take a full image in order to completely restore all docs, settings, and installed apps.

I think I'll try your idea of doing a VM installation on my laptop so I can have a play with it, and I'll definitely install it onto the desktop.

Cheers.

---

### Post by billgoldberg on 2008-11-20
> **bbawden said:**
> Hi all.

First off, I love the ethos of open source, and would not hesitate to recommend Ubuntu.

In my specific situation though, I'm not sure if it's right for me, and would like some input and advice.

My setup at the moment is a desktop that acts as a kind of server, handling shared files etc. It also has iTunes for syncing my pod. It's wired up to a router via ethernet. Also on ethernet is a Freecom Datatank NAS (500GB raid). This actually holds my media library and also my backups. I'm acutally thinking of ditching the desktop and getting a small laptop for a server. It makes much more sense to use a laptop for something that's on 24/7 because of the power consumption (plus it takes up less room).

For my main use I have a pretty specced up Dell laptop running Vista.

Now, a lot of what I do is image processing. I use Photoshop, and in my opinion GIMP just doesn't cut it for what I need.

Most of the rest of what I do is just internet browsing, general office docs etc.

I'm not sure that it's worth installing Ubuntu on my laptop, as I'd be constantly switching between that and Windows. But would it be worth installing it on the desktop?

My concerns:
-Can you remote desktop (or equivalent) to an Ubuntu box?
-How does it cope with accessing shared drives, such as my NAS?
-Would the ethernet setup cause it any problems?
-Can it share folders with windows PCs accessing it via the network?

Thanks for your input.

1. recommending something you haven't used is a wise thing to do

2. using a laptop as a server also isn't a good idea

3. stick with windows

---

### Post by bbawden on 2008-11-20
> **billgoldberg said:**
> 1. recommending something you haven't used is a wise thing to do

2. using a laptop as a server also isn't a good idea

3. stick with windows

Thanks for that. I have in fact used Ubuntu, I just don't have it installed myself. Even if I hadn't, have you never made a recommendation based on the large amount of positive feedback you've heard about it?

Why is a laptop not a good idea for a server? Screen is built in, lower power consumption.

What makes you say I should stick with windows?

---


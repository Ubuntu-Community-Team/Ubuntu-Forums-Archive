---
title: "USB Wireless Adapter"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by rskay00 on 2008-06-09
I posted this on the thread

SOLVED] How to activate WG311v3 (or any ndiswrapper or native) wireless
prshah 

where prshah gave a step-by-step guide to getting the wireless card to work with Ubuntu. But (maybe because of the "solved" tag) I had no replies. As you'll see I'm trying to work with a Linksys USB adapter but I'm hoping I can try the same kind of thing. Thanks for any advice.

Rick

Hi,

This my first posting. I really am an absolute beginner. A few months ago I installed Edgy on an old PC. It was connected to my wired home network. I stumbled around with a few things but was able with no effort to browse the internet.

I then moved and have just set up that old PC in a new house where I have wireless network. I have a Linksys Wireless-B WUSB11 ver. 4 USB wireless adapter. I'd like to use it with ubuntu but though I have read a zillion things still feel at sea.

Can I try and follow your instructions with this adapter?

Now- just to make clear how ignorant I am-- I suppose you are typing these commands in a terminal (something I just discovered yesterday).Also do I need to have the Windows driver for the adapter already installed? I don't. If so I need to know how to get it installed. I can download it from the Linksys site (with the laptop I'm using right now)on to a flash drive. Then what? Also if I need the Windows driver which version of windows should I get the driver for?

If, in fact, there's no way to get my adapter to work which (cheap) USB adapter should I get? Then I will have all the same questions for that one.

So you see I'm not kidding about the absolute beginner stuff. For example, I don't know what a kernel is

I never cease to wonder about the generosity and patience of people who post on these forums and I am really grateful for the help. I wish I knew enough about anything to be able to do something like that.

thanks,

Rick

---

### Post by s33nagain on 2008-06-13
THere are many ways to solve this:
 
(you might need a newer version of ubuntu, because the package database didn't have any ndiswrapper packages for your version of ubuntu)

[SIZE="4"]1[/SIZE]. Install Ndiswrapper (I reccomend getting the package since youre a beginner (no terminal needed)) You can find that here: 

[http://packages.ubuntu.com/search?searchon=names&keywords=ndiswrapper](http://packages.ubuntu.com/search?searchon=names&keywords=ndiswrapper)

Make sure to get the Utils and the commons. Put them on your linux partition, on the desktop (with admin privligies) and double click each. It will open a install window. 

I don't remeber which one you need to do first, but when you click on the wrong one, it will say "you need the following package in order to install: ndiswrapper-utils/commons".

Install both. Reboot (just to play it safe [in linux you don't need to reboot in many cases).


[SIZE="4"]2[/SIZE]. Get the windows drivers for the adapter. It should be in a folder on the Cd that came with the adapter, or in it's own zip archive on the internet 

CLARIFICATION: on the cd, there will be a folder with abuch of files, and two .inf files. Copy all of those files to a folder on your linux desktop called "whateveryouwant". 

Now, goto System>Administration>Windows Wireless Drivers

This is actually waht we just installed. Now, click add, goto the folder in your desktop, and click one of the two .inf files. THen Click the add button again but this time click the other .inf file. 

{NOTE: you might need to reboot again, maybe!}

One of them should say "Active", "Detected", "Enabled" or such. Delete the one that doesn't. Now goto the regualar networking window in Ubuntu: System>Administration>Network

The Wireless/OneOfTheWireless Adapters Shown is you network adapter! Configure apropiately!


GOOD LUCK! HAVE BETTER LUCK THAN ME!

My stress on this adapter (try this post before doing the reccommendations on that site!!!!!) : [http://www.return0.tk]("http://www.return0.tk")

---


---
title: "ndiswrapper freezing mouse....."
date: 2008-08-14
forum: New to Ubuntu
---

### Post by S-Fraz on 2008-08-14
I finally got ndiswrapper and madwifi installed.
But like 10 seconds after I hook my WUSB54GSC adapter up, my mouse stops working. (It's though usb port)

And also ndiswrapper stops working. Because if I type: ndiswrapper -l
It will just sit there forever doing nothing.

The whole system does not freez because I can still use keyboard. And I can use another mouse if it's not usb port.

Why the heck is it doing this??

Also if I go to Network Manager theres no option for Wireless Network. It just wired and phone line, Why is that?

---

### Post by S-Fraz on 2008-08-14
bump.....

---

### Post by nicedude on 2008-08-15
You didn't get Ndiswrapper & Madwifi both installed as its one or the other. Ndiswrapper lets people use drivers that are for Windows XP to control a Wifi adapter while Madwifi.org is a cool group of people that make drivers for Linux to control Atheros brand Wifi adapters. I would recommend you post here exactly what you did along with some simple network info and maybe everyone here can help. I would recommend the Madwifi drivers over any Ndiswrapper solution but if you have a USB Atheros wifi adapter then they won't work and you would be stuck with Ndiswrapper.


Wifi network info command
iwconfig

Try and tell us all what you did. As I re-read your post I see Ndiswrapper -l doesn't do anything, that means there  are no drivers loaded by it ( I believe ). That coupled with your not having wifi means you don't have a driver loaded for your wifi adapter. Please include along with what you have done, what you are doing it to :-) If you only know the laptop model number that is OK but if for any reason you know what Wifi adapter you actually have then include that as well as it will save me some googling.

nicedude

---

### Post by S-Fraz on 2008-08-15
Ill reply back later with details. It's 3:00 AM now. Thanks.

---

### Post by S-Fraz on 2008-08-15
Ok, Thanks for replying, nicedude.

This is the adapter I have:
[http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&pagename=Linksys%2FCommon%2FVisitorWrapper&cid=1154470123093](http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&pagename=Linksys%2FCommon%2FVisitorWrapper&cid=1154470123093)

I have done sooooo much to this point that I have no idea what I have done.
Whats the best why to clean install everything again? Like how do I completely remove ndiswrapper? And madwifi (if I have it installed)?

Let me start off by saying that I could not compile anything though terminal because I did not have the headers. So I went though the ubuntu cd-rom/pool/main and cr-rom/pool/restricted

I installed all the deb packages I could. (This includes ndiswrapper)

I noticed that after I installed the ndiswrapper deb files I could go System -> Administration -> Installed Windows Drivers

I could add drivers though that and terminal now. So I did.
Then when I went to type *modprobe ndiswrapper* in terminal it would give me some error like it was not found.

So I went and uninstalled it. (I'm not sure if it was completely removed)
Then I installed ndiswrapper-1.53 form source in terminal. (As I can now compile from source)

Well when I install it this way I no longer have System -> Administration -> Installed Windows Drivers

I have to do everything though terminal to install and manage drivers.

I don't know if thats version differences of what.

Anyway, The deb package will not freeze me up when I connect my adapter, But I think thats because *modprobe ndiswrapper*
Would not work. Where as when I installed though source It would. And that I think is whats freezing it up. Because I've tried hooking up my adapter before typing that and it won't freeze. I think *modprobe ndiswrapper* is need to run it. So I unhook my adapter and type *modprobe ndiswrapper*. Everything seems to go fine here. So I then hook my adapter up. 10-20 seconds later my mouse stops woorking. Some times the whole desktop freezes. I have to restart either way.
I noticed a while ago that if I have ndiswrapper installed and *modprobe ndiswrapper* has already been typed I can not boot into ubuntu with my adapter hooked up. Ubuntu will freeze as it's loading up the go to like some terminal screen with a bunch of numbers and letters. It just sits there like that, So I restart agian without the adapter and it boots fine.


Thats basically where I am now. Other than Ive tried installing and uninstalling madwifi, but done nothing with it as on the tuts that say install it don't tell you what to do with it.

BTW:
These are the driver files I used. (the attachment)

---

### Post by nicedude on 2008-08-15
OK here are some answers that will help you.

1. Madwifi drivers do not work with USB based wifi adapters at this time, none of them no matter what Atheros chipset they use. So you should not attempt to use any madwifi drivers to control this device. Instead your only option is to use Ndiswrapper

2. To uninstall something that you have compiled from source you just go back into the source directory and open a terminal and usually you would type "sudo make uninstall" but you can open the make file and look at what options it contains as some contain more options than others, it all depends on the author and how well he made the install setup.

3. To un-install something you installed via a deb package you can open synaptic package manager and search by name for it, such as "madwifi", you can also search by name for things you might need or want such as "build-essential" "linux headers" etc. I would recommend you search there and remove anything you find by searching for "madwifi" as it won't be needed and could cause problems.

4. The driver you posted looks OK as a Ndiswrapper driver goes, but I have absolutely zero experience with Ndiswrapper since I don't use USB based atheros adapter and therefore can use madwifi and so that is what I use and they are quite different in how they work. So I would recommend you read up on Ndiswrapper's way of functioning and see if you can't figure out how it works etc.  If you cant figure out something that you are supposed to do then I could possibly help but as far as I know you install it from repositories then open Ndiswrapper and point it to the driver you want to use and it does  it. It could be the madwifi drivers being present that is causing the conflict but I am unsure. You should have a setting called RESTRICTED DRIVERS under System -> Administration -> Restricted which you should check and see if it lists any madwifi drivers in use and if so uncheck them as that would cause a conflict.

So basically uninstall everything you did and start over with Ndiswrapper from the repositories and make sure you don't have the madwifi checked under restricted drivers and it should work. You could also just google the name of your adapter with the word Ubuntu and see if someone else has had any troubles with this exact model as you may find your answer that way as well.


hope all this helps and good luck, please PM me with your results as I would like to hear if you get a successfull outcome.


nicedude

---

### Post by S-Fraz on 2008-08-15
Still freezing.

When I add the driver like this:
```

sudo ndiswrapper -i WUSB54GSC.inf

```
It says something like 
```

Could not find SourceDiskFiles.... Continuing Anyway....
Installing Driver....

```

Is that bad?

I know if I try installing a different driver thats not mine it will just say:
```

Installing Driver....

```

Maybe thats why? I don't know how to fix it though...

---

### Post by nicedude on 2008-08-15
I don't know anything about Ndiswrapper besides what it is and why it is ( because there are not linux drivers for all wifi adapters ). I avoided it like the plague since I wanted and needed a driver that would go into monitor mode ( my favorite ) & do packet injection for hacking and penetration testing against wifi AP's. You can never do monitor mode or injection with Ndiswrapper, so I knew I did not want to even try it. Instead I spent a week to figure out how to setup my AR5007EG PCI adapter and when I finally succeeded I wrote a guide for others on how to do it. As far as your adapter & Ndiswrapper I would really suggest you read up on Ndiswrapper or better yet a guide on using it with your exact adapter.

I do know that with Ndiswrapper I don't believe you have to run any commands at the command line as I think it should have a gui type menu to say what driver to install etc.  If you are using Ndiswrapper you tried to compile from source then I would say go back and try to "sudo make uninstall" that and then just install the one from the repositories and start over by reading a Ndiswrapper guide ( as the newest version is probably not your problem ) and following the advice of someone that uses it, better still if you can find advice that is specific to your exact adapter. Google is your friend in this endevour as it can help you locate the answer, I am sure of that. Here is a tip for you about google, when searching google tries to match all the words you type but if you wrap a word or a series of words in "" quotes then it will only return pages that contain that word or phrase exactly as you put it. So if you put something like theis -> Ubuntu ndiswrapper "modelofyouradapter" | it would only return hits that contain the model of your adapter as well as any that had either of the other two words and rank them by relevance, this will remove allot of hits that don't apply and help you find the best match to your query. So try using some google tricks and searches and see if you can't find someone with exact steps they used to get this exact adapter working with Ndiswrapper ( it is a common adapter I would think ) , Sorry I couldn't be more help but I just don't have your system in front of me.

---

### Post by S-Fraz on 2008-08-15
Ive read everything there is on ndiswrapper And Every tut on this forum and over on other forums, none of them work.

Is there such thing as a linux adapter with a linux driver?
Or another alternative from ndiswrapper? 

I do everything that the tutorials say and what the ndiswrapper doc says. So obviously ndiswrapper doesn't work.


If I cant find an adapter that works with linux out of the box I'm wiping out linux and forgetting about it.

If I sound mad, yes I am, but not at you. Ive sat here for 4 days all day with this ndiswrapper junk.

So I'm done with it. And done with linux if I cant find an adapter.


Thanks for all your help though.

---

### Post by nicedude on 2008-08-15
Ok I googled for 30 seconds and find this thread here in the forums where someone is successfully using this adapter

[http://ubuntuforums.org/showthread.php?p=2296818](http://ubuntuforums.org/showthread.php?p=2296818)

Heres another one with a guide

[http://ubuntuforums.org/showthread.php?t=459617](http://ubuntuforums.org/showthread.php?t=459617)

And here is one that is dealing with 8.04 hardy specifically in case there are differences

[http://www.linuxquestions.org/questions/linux-newbie-8/problem-wwusb54gsc-in-ubuntu-8.04-639797/](http://www.linuxquestions.org/questions/linux-newbie-8/problem-wwusb54gsc-in-ubuntu-8.04-639797/)

After you undo all the things you did ( I have no idea as I am not you ) you could run this command to install both ndiswrapper and a nice gui & utilities to use with it, just paste the whole thing in a terminal and hit enter.

sudo apt-get install ndiswrapper-common && sudo apt-get install ndisgtk && sudo apt-get install ndiswrapper-utils-1.9



So I know it can be done, I am sorry if you feel you have to give up as I am sure that it can work. And as to are there linux adapters with linux drivers , first part NO second part YES . I suggest to everyone that when they buy hardware and want to use it with linux that they investigate the linux capability before purchase. Online reatailers such as NEWEGG have feedback from buyers who rate the products, in those feedbacks you will find people who say things like "worked with hardy 8.04 out of box" and then you know that it will be easy.

---

### Post by S-Fraz on 2008-08-15
YES!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! :D

I took out one of my old adapters (D-Link) And installed the driver. It worked right straight!!!!!!

I would rather use my other adapter as the transfer speed is better. So I will look at those links you gave me! :D

But still this one works!

---

### Post by nicedude on 2008-08-15
Glad to hear it :-) If you just stick with Linux it will learn ya !

---

### Post by pytheas22 on 2008-08-16
EDIT: sorry, I wrote this before realizing that there was a second page here.  I'm glad to hear the problem's solved.

But what I wrote was that I think the W54USB has a native Linux driver, so ndiswrapper is not necessary.  If you post the output of:

```
lsusb
lshw -C Network
```

that could be confirmed.  I think it has a Ralink chipset, which has very good Linux support, as Ralink released open-source drivers several years ago.  ndiswrapper was from the days when virtually no device vendors would support Linux; fortunately, ndiswrapper is becoming less and less necessary as Linux gets more support and drivers are reverse-engineered in situations where vendors are still uncooperative.

---

### Post by S-Fraz on 2008-08-16
W54USB? Is that the same as WUSB54GSC?

---

### Post by nicedude on 2008-08-16
I don't think WUSB54 and GSC are the exact same, I think that is an older version and the GSC is the newer version but is uses the same chipset I think ( I looked around real quick ) -> "ralink" so you should either see if this chipset is supported by default or not. I saw some claims of conflicts with Ndiswrapper if installed between it and the default system drivers, so that might be something to look at.

---

### Post by S-Fraz on 2008-08-16
Hmm, I'm pretty sure mine is a broadcom chipset. I saw it after I typed somthing in terminal. Maybe it was lsusb? I dunno.

Does linux work with broadcom?

---

### Post by pytheas22 on 2008-08-16
> Does linux work with broadcom?

Yes, there are reverse-engineered native drivers for Broadcom that work pretty well with most devices.  And recently Broadcom (which has spent the last six years hating on Linux) finally released drivers of its own, which is a good sign.  They're still mostly closed-source, but it's a start, and shows the leverage that we gain by having Ubuntu endorsed by Dell (as I understand, it was Dell, working with Canonical, that made Broadcom finally change its mind about Linux support, since Broadcom makes a lot of the wireless cards sold in Dell laptops).
> 
it uses the same chipset I think ( I looked around real quick ) -> "ralink" so you should either see if this chipset is supported by default or not.

If the USB device does indeed have an Ralink chipset, it may not necessarily be supported out-of-the-box.  Ubuntu ships with the "next-generation" Ralink drivers, but there are also legacy drivers that work better in some cases.  You can compile and install the legacy drivers yourself.

To see which chipset your card has, run the command "lsusb."  The output will look similar to this for your wireless card:
```

Bus 005 Device 003: ID **07d1:3c03** D-Link System 
```

It may not mention the chipset manufacturer (D-Link was the vendor of my card, but it has a Ralink chipset), but if you google the device ID (in bold above), you can usually figure it out pretty fast.

---


---
title: "Two things i have hated about Ubuntu. Do you share my frustration?"
date: 2009-12-20
forum: Recurring Discussions
---

### Post by donniezazen on 2009-12-20
Hi,

There should be many threads like this. Sorry for another redundant thread. I completely moved to Ubuntu 2-3 years ago and i keep Ubuntu installation in my flash drive because i like to mess it up. The two things that i have always hated are-

1. Getting wireless done is the biggest problem. I have to have a LAN connection to connect my laptop and install restricted drivers.

2. Since Ubuntu doesn't come pre-installed with restricted format and wifi doesn't work without restricted drivers, you are once again struck with the classic Ubuntu paradox.

Are developers working on these problem? Since in any case i will have to install restricted and proprietary drivers, why don't they come pre-installed (Ubuntu may add a notice to clear its software policy)?

Thanks,
SK.

P.S.-If there is an active thread going around these topics please merge them.

---

### Post by kerry_s on 2009-12-20
try "linux mint" it's built for that.
[http://www.linuxmint.com/about.php](http://www.linuxmint.com/about.php)

---

### Post by slakkie on 2009-12-20
Ubuntu already does a great job. Both Fedora and Debian require me to have a LAN connection available to setup my box.

But you could indeed try Mint, some friends use is and they are positive about it.

---

### Post by skierkyles on 2009-12-20
Well, the drivers are not included because they are not open source, and thus are against some Ubuntu motto somewhere... ;) 
But I do understand and why, and agree that they should not be included.

And the restricted extras are not included, because in some areas they are on very shaky legal ground.

---

### Post by donniezazen on 2009-12-20
> **kerry_s said:**
> try "linux mint" it's built for that.
[http://www.linuxmint.com/about.php](http://www.linuxmint.com/about.php)

> **slakkie said:**
> Ubuntu already does a great job. Both Fedora and Debian require me to have a LAN connection available to setup my box.

But you could indeed try Mint, some friends use is and they are positive about it.

I know Mint is great and based on Ubuntu, but can't really move to another distro.

> **skierkyles said:**
> Well, the drivers are not included because they are not open source, and thus are against some Ubuntu motto somewhere... ;) 
But I do understand and why, and agree that they should not be included.

And the restricted extras are not included, because in some areas they are on very shaky legal ground.

Does not really make sense. This is known as lack of common sense. Can't do anything.

Thanks.

---

### Post by ronacc on 2009-12-20
wireless and video both can be a challenge in any linux distro . That is why you should do your homework before buying new hardware , there are things that work "out of the box" others that are a bit of work and still other that are "sorry charlie".

---

### Post by RAOF on 2009-12-20
> **soham_1207 said:**
> ...
1. Getting wireless done is the biggest problem. I have to have a LAN connection to connect my laptop and install restricted drivers.

I suspect that means you've got a broadcomm wireless card, which requires non-free firmware.  The problem here is that Ubuntu (or anyone who isn't Broadcomm, for that matter) doesn't have the legal right to distribute the firmware.  The work-around we use is to download the windows drivers from the official site and extract the firmware from them.  This obviously requires an internet connection, though, which is a problem :).  Note that we **can't** download the windows drivers on Ubuntu servers, extract the firmware, and then ship it on the CDs; that would be distributing the firmware, which we're not allowed to do.

> **soham_1207 said:**
> 
2. Since Ubuntu doesn't come pre-installed with restricted format and wifi doesn't work without restricted drivers, you are once again struck with the classic Ubuntu paradox.

Are developers working on these problem? Since in any case i will have to install restricted and proprietary drivers, why don't they come pre-installed (Ubuntu may add a notice to clear its software policy)?


Generally because it's not legal to; we don't have the right to redistribute those pieces.  Adding a note "we're breaching your copyright to make things easier for our users" is not going to help :).

It can also be due to size - the (most recent - there are 4 others, required to support hardware of varying ages) nvidia drivers are 16MB compressed, 50MB unpacked; that's a serious chunk of the live & alternate CDs taken up.

---

### Post by phillw on 2009-12-20
> I suspect that means you've got a broadcomm wireless card, which requires non-free firmware. The problem here is that Ubuntu (or anyone who isn't Broadcomm, for that matter) doesn't have the legal right to distribute the firmware. The work-around we use is to download the windows drivers from the official site and extract the firmware from them. This obviously requires an internet connection, though, which is a problem :smile:.  Note that we **can't** download the windows drivers on Ubuntu servers, extract the firmware, and then ship it on the CDs; that would be distributing the firmware, which we're not allowed to do.
The answer to the OP is there -- get you & and as many as you know that use their hardware & complain to them. Make yourself a nuisance, post a blog, write a letter, complain that it is hampering your free choice and is therefore a cartel !!!!

Some companies are doing better than others at realising Linux is 'out there', It's no different to reporting to site owners that their wonderful web-site looks like a pile of dogs-mess when viewed in Fire Fox -- COMPLAIN - to THEM, not to the open source community. Letters to trade magazines do, sometimes get published when you write it to be included in the next resumee they do on Linux.

Phill.

---

### Post by reub2000 on 2009-12-20
I bought a laptop with linux thinking that it would contain hardware that was friendly with linux. Too bad it contains a broadcom chipset. Purchasing hardware like this can be hard becomes often times the only specs for the wireless cards is the supported wireless standards. I'm scratching my head trying to figure out what broadcom gains by restricting the firmware in such a manor. After all, they are in the buisness of selling wireless chipsets, not firmware for wireless chipsets.

Also, as I understand it, the OpenFWWF project us trying to create free firmware to go with the free b43 driver, but the project hasn't quite created usable firmware.

---

### Post by k3lt01 on 2009-12-20
> **soham_1207 said:**
> I know Mint is great and based on Ubuntu, but can't really move to another distro.Why not? I refer to your comment below. You seem to want others to break the law for you yet you are not willing to use a distro that enables you to have what you want.

> **soham_1207 said:**
> Does not really make sense. This is known as lack of common sense. Can't do anything.Why should Ubuntu change its policy for you? You use it knowing full well what the policy is yet you want them to break the law to make your life a little easier. Use your common sense and use a distro that is compatible with Ubuntu and allows you to have what you want.

Hope this doesn't sound harsh but think about it for a bit and you will see how your own comments can quite easily be used against you.

---

### Post by hikaricore on 2009-12-20
I'm not sure if i understand this issue?

Do you have an ethernet port and simply don't wish to use it ONCE for initial setup?
Seems a bit nitpicky to me personally.

---

### Post by twright on 2009-12-20
This ***is** *being worked on ... an open source firmware for b43 supported chips is in development and will probably be in the next version of Ubuntu - whether it will work for your particular chip is another matter.

Remember though, most Windows installs usually need Ethernet during setup - in one of my computers not even the Ethernet card is recognised so a USB is usually needed.

---

### Post by steveneddy on 2009-12-20
Using Linux supported hardware will solve most of these issues.

I use hardware purchased at [System76.com]("http://www.system76.com/") and have no issues with any of the hardware being unsupported in the last three years.

One either decides to work hard or work smart. I prefer to work smart and use supported hardware because I need to get work done, not create more work for myself.

---

### Post by phillw on 2009-12-20
> **twright said:**
> This ***is** *being worked on ... an open source firmware for b43 supported chips is in development and will probably be in the next version of Ubuntu - whether it will work for your particular chip is another matter.

Remember though, most Windows installs usually need Ethernet during setup - in one of my computers not even the Ethernet card is recognised so a USB is usually needed.

Choose wisely your kit .... Buy kit that works ....  Not being smug, but mine works 'out of the box' - the only thing I needed was the restricted drivers - and even Win didn't include the dvd codecs in the OS !!

Wireless chirped up part way through the install asking to go get updates ... ahh, sweet.

And as for the 3G huwaiie usb dongles, heck - it snaps them straight in as '3 - GSM' - Huwaiie made a simple move ... drivers available for new technology. The dinosaurs, however, are dooming themselves to extinction.

Oh, and I love this, as well --> [http://shop.canonical.com/product_info.php?products_id=577](http://shop.canonical.com/product_info.php?products_id=577)

Phill.

---

### Post by Seventh Reign on 2009-12-20
I have a Linksys wireless PCI Card and a Linksys wireless modem and Ubuntu works flawlessly with it.  No drivers needed to install.  Just boot up type in your passphrase and I'm online.  I've yet to find a Linux, BSD, Solaris or Windows system that didnt work with it.

---

### Post by autocrosser on 2009-12-20
I have been using Linux distros for many years now & I COMPLAIN to the hardware maker anytime it won't work with the OS of MY choice...I once was called by the Exec VP of Marketing for HP because I complained loudly about a scanner I had bought & would not work (this was in 2004)---And shortly after I was contacted by a Senior-Software-Designer about my "problem". Was nice to talk to people that could make a difference & I told him how to contact the developer for Sane---about 6 months later I was able to use that scanner & the developer contacted me with thanks.....felt good.

WE as a group CAN make a difference--Be polite, but get the point across that you are NOT changing your OS just to use the device--You bought the device to use & if you can't--everyone you know will know about it...............The more of us that do that----the sooner things will change.

---

### Post by buzzmandt on 2009-12-20
> **hikaricore said:**
> I'm not sure if i understand this issue?

Do you have an ethernet port and simply don't wish to use it ONCE for initial setup?
Seems a bit nitpicky to me personally.
this argument is like bamboo shoots under the fingernails, or fingernails across a chalkboard.  

I, for one, DO have an ethernet port.  I also don't always have access to a pluggin internet connection.  Just because you can don't mean others can.  My wireless happens to work ootb, but just because mine does I don't assume others will.

---

### Post by twright on 2009-12-20
> **autocrosser said:**
> I have been using Linux distros for many years now & I COMPLAIN to the hardware maker anytime it won't work with the OS of MY choice...I once was called by the Exec VP of Marketing for HP because I complained loudly about a scanner I had bought & would not work (this was in 2004)---And shortly after I was contacted by a Senior-Software-Designer about my "problem". Was nice to talk to people that could make a difference & I told him how to contact the developer for Sane---about 6 months later I was able to use that scanner & the developer contacted me with thanks.....felt good.

WE as a group CAN make a difference--Be polite, but get the point across that you are NOT changing your OS just to use the device--You bought the device to use & if you can't--everyone you know will know about it...............The more of us that do that----the sooner things will change.
It is great when support genuinely does move on. I personally pointed the developers to the correct firmware for one of my wireless cards and now it is supported out of the box.

---

### Post by KrazyPenguin on 2009-12-20
> **soham_1207 said:**
> Hi,

There should be many threads like this. Sorry for another redundant thread. I completely moved to Ubuntu 2-3 years ago and i keep Ubuntu installation in my flash drive because i like to mess it up. The two things that i have always hated are-

1. Getting wireless done is the biggest problem. I have to have a LAN connection to connect my laptop and install restricted drivers.

2. Since Ubuntu doesn't come pre-installed with restricted format and wifi doesn't work without restricted drivers, you are once again struck with the classic Ubuntu paradox.

Are developers working on these problem? Since in any case i will have to install restricted and proprietary drivers, why don't they come pre-installed (Ubuntu may add a notice to clear its software policy)?

Thanks,
SK.

P.S.-If there is an active thread going around these topics please merge them.
Had the same problem with windows xp and my laptop. Couldn't connect to the internet at all, so i had to USE ANOTHER COMPUTER TO DOWNLOAD THE DRIVERS and install the via usb stick LOL.

NEVER EVER had this problem with Linux!!!

Ubuntu = really good driver support for most computers

---

### Post by k3lt01 on 2009-12-20
> **buzzmandt said:**
> this argument is like bamboo shoots under the fingernails, or fingernails across a chalkboard.Hmmmmmm, I could say alot here but I think your signature sums it up perfectly.

---

### Post by twright on 2009-12-20
> **KrazyPenguin said:**
> Had the same problem with windows xp and my laptop. Couldn't connect to the internet at all, so i had to USE ANOTHER COMPUTER TO DOWNLOAD THE DRIVERS and install the via usb stick LOL.

NEVER EVER had this problem with Linux!!!

Ubuntu = really good driver support for most computers
Yes, Ethernet ports get used in servers so they have to support Linux - it is just a matter of waiting for progress.

---

### Post by buzzmandt on 2009-12-20
> **KrazyPenguin said:**
> Had the same problem with windows xp and my laptop. Couldn't connect to the internet at all, so i had to USE ANOTHER COMPUTER TO DOWNLOAD THE DRIVERS and install the via usb stick LOL.

NEVER EVER had this problem with Linux!!!

Ubuntu = really good driver support for most computers
I feel ya on this one, was on the road and nerffed my system, only thing i had was a winxp install disc (what a goof).  installed xp and didn't have drivers for ANYTHING.  video, wireless, sound, nothing worked at all.  I have been completely spoiled with linux just working on my laptop.

---

### Post by clivejo on 2009-12-20
> Hi,

There should be many threads like this. Sorry for another redundant thread. I completely moved to Ubuntu 2-3 years ago and i keep Ubuntu installation in my flash drive because i like to mess it up. The two things that i have always hated are-

1. Getting wireless done is the biggest problem. I have to have a LAN connection to connect my laptop and install restricted drivers.

2. Since Ubuntu doesn't come pre-installed with restricted format and wifi doesn't work without restricted drivers, you are once again struck with the classic Ubuntu paradox.

Are developers working on these problem? Since in any case i will have to install restricted and proprietary drivers, why don't they come pre-installed (Ubuntu may add a notice to clear its software policy)?

Thanks,
SK.

P.S.-If there is an active thread going around these topics please merge them.I totally agree with you.  For a newbie Ubuntu can be very hard to get your head around.  I also understand the legal reasons why Ubuntu has it do it this way.  

But surely there is a more simple way, rather then having to research each and every hardware device you have.  I personally enjoy rolling up my sleeves now and again and getting my hands dirty under the hood.  But for some who are new to it, they need it to 'just work'.  Ubuntu have to capture the hearts and minds of all computer users, not just the techies for it to become successful and widely used.

My understanding of the "Hardware Driver" feature was that it would allow simple hardware support, bit like the "Device Manager" in Windoze.  Is there no way Ubuntu / community could maintain a database to 'link' users to the drivers of there particular hardware.  For example "Lusty Lemming has detected a device which requires a 3rd party driver for its optimal operation, click OK to agree to the disclaimer/waiver and install the driver, or Cancel to abort"  This way even a Newbie can quickly get up and running and Ubuntu don't include or provide the copyrighted material directly via CD or on their servers.

---

### Post by hikaricore on 2009-12-20
> **buzzmandt said:**
> this argument is like bamboo shoots under the fingernails, or fingernails across a chalkboard.  

I, for one, DO have an ethernet port.  I also don't always have access to a pluggin internet connection.  Just because you can don't mean others can.  My wireless happens to work ootb, but just because mine does I don't assume others will.

So having to use a physical connection one time when installing to get your wireless working is gruesome torture?
Mmmkay.  Well that's good to know.  I'll inform my terrorist cells... i mean.... errrr.

---

### Post by ronacc on 2009-12-20
Its not so much doing your homework to find something that will work as to avoid the VERY FEW that won't or will work poorly . If I buy ANY piece of hardware even a simple mouse it comes with a driver disk for windows (with multiple drivers , one for each iteration of windows ) and when you plug it in a box pops up "new hardware detected please insert driver disk"  . However if you boot linux on the same box and plug the same hdw in 90% or more of the time it just plain works and the situation only gets better with time . And I have been 100% 64bit since the AMD64 first came out , wireless can be a problem with some chipsets but much less these days and some scanners and a few (not many) printers .I use cheap offbrand Chinese made wireless cards with a realtek chipset and they just work .

---

### Post by buzzmandt on 2009-12-20
> **hikaricore said:**
> So having to use a physical connection one time when installing to get your wireless working is gruesome torture?
Mmmkay.  Well that's good to know.  I'll inform my terrorist cells... i mean.... errrr.

I said "this argument", not "this action".
It IS possible that someone in this world might not have ethernet and have only wifi access.... Yes, it's possible.

---

### Post by RAOF on 2009-12-20
> **clivejo said:**
> ...
My understanding of the "Hardware Driver" feature was that it would allow simple hardware support, bit like the "Device Manager" in Windoze.  Is there no way Ubuntu / community could maintain a database to 'link' users to the drivers of there particular hardware.  For example "Lusty Lemming has detected a device which requires a 3rd party driver for its optimal operation, click OK to agree to the disclaimer/waiver and install the driver, or Cancel to abort"  This way even a Newbie can quickly get up and running and Ubuntu don't include or provide the copyrighted material directly via CD or on their servers.

This is *exactly* what the Hardware Drivers service already does.  The original poster's complaint was that this requires an Internet connection, and so when you need it to get your wireless card working, you need some other way of connecting to the Internet first.

---

### Post by donniezazen on 2009-12-20
> **k3lt01 said:**
> Why not? I refer to your comment below. You seem to want others to break the law for you yet you are not willing to use a distro that enables you to have what you want.

Why should Ubuntu change its policy for you? You use it knowing full well what the policy is yet you want them to break the law to make your life a little easier. Use your common sense and use a distro that is compatible with Ubuntu and allows you to have what you want.

Hope this doesn't sound harsh but think about it for a bit and you will see how your own comments can quite easily be used against you.

I am sorry for you. Instead of pursuing me and other Ubuntu users to agree with these absurdities, you better email some capitalist to go open.

> **hikaricore said:**
> I'm not sure if i understand this issue?

Do you have an ethernet port and simply don't wish to use it ONCE for initial setup?
Seems a bit nitpicky to me personally.

When i am outside at my school all i have is wireless and most Ethernet ports in departments are close Ethernet which requires special permission from the department authorities. I hope you don't want to get into the tedious process and a week of delay to get the permission.

> **twright said:**
> This ***is** *being worked on ... an open source firmware for b43 supported chips is in development and will probably be in the next version of Ubuntu - whether it will work for your particular chip is another matter.

Remember though, most Windows installs usually need Ethernet during setup - in one of my computers not even the Ethernet card is recognised so a USB is usually needed.

Great! thanks.

I don't agree with the most windows part. I never used Ethernet to download any driver for my Vista or 7's installation. It works out of box.

> **autocrosser said:**
> I have been using Linux distros for many years now & I COMPLAIN to the hardware maker anytime it won't work with the OS of MY choice...I once was called by the Exec VP of Marketing for HP because I complained loudly about a scanner I had bought & would not work (this was in 2004)---And shortly after I was contacted by a Senior-Software-Designer about my "problem". Was nice to talk to people that could make a difference & I told him how to contact the developer for Sane---about 6 months later I was able to use that scanner & the developer contacted me with thanks.....felt good.

WE as a group CAN make a difference--Be polite, but get the point across that you are NOT changing your OS just to use the device--You bought the device to use & if you can't--everyone you know will know about it...............The more of us that do that----the sooner things will change.

Great that is what we need to do.

Thanks.

---

### Post by k3lt01 on 2009-12-20
> **soham_1207 said:**
> I am sorry for you.Feeling is mutual, I feel sorry for you to. Think about what you say and maybe you will see how ludicrous your entire argument is.

> **soham_1207 said:**
> Instead of pursuing me and other Ubuntu users to agree with these absurdities,I'm not pursuing anyone, you chose to use Ubuntu as it is yet you want Ubuntu to change for you. Get over it, seriously.

> **soham_1207 said:**
>  you better email some capitalist to go open.Care to finish that sentence because as it is it make no sense at all.

Buzzmandt's signature sums it up nicely

[quote=Buzzmandt]If a conservative decides to be a vegetarian, He/She doesn't eat meat.
If a liberal decides to be a vegetarian, He/She wants to ban meat from everyone.[/quote]

The point to all of this is you have a choice, you can do it the easy way or the hard way, you are choosing the hard way. You have been given options yet you choose to keep going how you are. Stop demanding that Ubuntu does things your way and consider why they are doing it their way.

---

### Post by snowpine on 2009-12-20
Broadcom's Linux driver is freely available here: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

What's the big deal? ;)

---

### Post by donniezazen on 2009-12-20
> **k3lt01 said:**
> I'm not pursuing anyone, you chose to use Ubuntu as it is yet you want Ubuntu to change for you. Get over it, seriously.

Change=improvement. Don't you want to change. Do you still have Gusty?

> Care to finish that sentence because as it is it make no sense at all.

If it does not make sense go back to elementary school and take open source 101

> The point to all of this is you have a choice, you can do it the easy way or the hard way, you are choosing the hard way. You have been given options yet you choose to keep going how you are. Stop demanding that Ubuntu does things your way and consider why they are doing it their way.

Ubuntu is made for common free people and if it does not listen to common people's demands it will go trash. You are talking in a way  like NO, GET OUT! IT IS NOT POSSIBLE. BOO HOO. Where there is will there is way. Think of something positive. Don't waste our time with your negative doom-sayer dead-end thoughts.

---

### Post by ronacc on 2009-12-20
adding to what k3lt01 said . there is a right way to >  you better email some capitalist to go open and a wrong way . The wrong way is to get in their face and scream and threaten, no one responds well to that . Instead tell them they make a fine product and that you would like to use it but can't because of lack of linux support and that they could GAIN SALES by supporting linux . That way is much more likely to be productive .

---

### Post by hikaricore on 2009-12-20
I'm done participating in this whinefest.  Best of luck.

---

### Post by donniezazen on 2009-12-20
> **ronacc said:**
> adding to what k3lt01 said . there is a right way to  and a wrong way . The wrong way is to get in their face and scream and threaten, no one responds well to that . Instead tell them they make a fine product and that you would like to use it but can't because of lack of linux support and that they could GAIN SALES by supporting linux . That way is much more likely to be productive .

Totally agree. We do not have to live with this software apartheid. there is always a positive way. Better late then never.

---

### Post by snowpine on 2009-12-20
> **soham_1207 said:**
> Ubuntu is made for common free people and if it does not listen to common people's demands it will go trash. You are talking in a way  like NO, GET OUT! IT IS NOT POSSIBLE. BOO HOO. Where there is will there is way. Think of something positive. Don't waste our time with your negative doom-sayer dead-end thoughts.

That is a valid argument if you happen to live someplace with no software patent laws. Some "common people" do not have that luxury and would not be able to legally use Ubuntu if it included non-free software that breaks the law of their country. Ubuntu should always be free for everyone all around the world.

---

### Post by donniezazen on 2009-12-20
> **snowpine said:**
> That is a valid argument if you happen to live someplace with no software patent laws. Some "common people" do not have that luxury and would not be able to legally use Ubuntu if it included non-free software that breaks the law of their country. Ubuntu should always be free for everyone all around the world.

It is like telling Wright brothers that they cannot fly. People, the improvements i have seen in these past 2 year, don't say Ubuntu can't do something. It will make its own way.

---

### Post by snowpine on 2009-12-20
> **soham_1207 said:**
> It is like telling Wright brothers that they cannot fly. People, the improvements i have seen in these past 2 year, don't say Ubuntu can't do something. It will make its own way.

Your analogy is meaningless... Can the Wright Brothers land their plane on the White House lawn without permission? Of course not; the air force will shoot them out of the sky! Our freedoms are circumscribed by law.

Don't say you can't fix your wireless. You will make your own way! :)

---

### Post by k3lt01 on 2009-12-21
> **soham_1207 said:**
> Change=improvement. Don't you want to change. Do you still have Gusty?Change=improvement? if you really believe that for every instance then you are much younger or niave than I thought.

Check my signature it will tell you what I am running.

> **soham_1207 said:**
> If it does not make sense go back to elementary school and take open source 101 Mate, not alot of what you are saying is making sense.

It does not make sense to stand out of the front of your school installing the latest version of Ubuntu knowing you have no way of getting internet access to finish of the job, install it at home or somewhere you can obtain the access you so desperately need.

> **soham_1207 said:**
> Ubuntu is made for common free people and if it does not listen to common people's demands it will go trash. You are talking in a way  like NO, GET OUT! IT IS NOT POSSIBLE. BOO HOO. Where there is will there is way. Think of something positive. Don't waste our time with your negative doom-sayer dead-end thoughts.Ah finally something you are saying is correct. Guess what, the law in the grand old US of A is different than in many parts of the world. Some people are unable to access, legally, the types of things you are demanding that Ubuntu puts into its system so that you can have an easy life. There are more people on this planet than 330 million citizens of the USA who have to abide by the laws of their countries, Ubuntu is made for them to.

Your attitude is selfish and your demeanour is simply rude. You have free choice, start exercising it.

---

### Post by ranch hand on 2009-12-21
Why on earth is this thread on the testing forum?

It really belongs over in the troll bin, I mean community forum.

---

### Post by omskates on 2009-12-21
> **ranch hand said:**
> Why on earth is this thread on the testing forum?

It really belongs over in the troll bin, I mean community forum.

I agree, I was following it with interest buy now (LOL, interesting typo, I meant "by now") it has begun to deteriorate quite rapidly.  Much better to brainstorm solutions then to argue on non-productive opinions.

---

### Post by Gina on 2009-12-21
I have a Linksys wireless PCCard with a Broadcom chipset and it's been supported OOTB for the last few years in Ubuntu.  No having to find your driver CDROM as with another well known OS!!

---

### Post by clivejo on 2009-12-21
I've had a lot of problems with ATI graphics stuff in the past and have just brought a new laptop purposely avoiding ATI (the one I wanted was ATI). This is my choice, same as my choice to scrap Windoze 7 and install Ubuntu.

People may see this thread as whine-fest and negativity, but these issues do matter to new users.  In most countries people have choice and will exercise it.  It is true that most devices do work out of the box, but some do not and may never work!

I would love nothing more to see many more users turning to Ubuntu.   The more people using it, the more of a voice the community has and in the future certain company's will learn the hard way that Linux is here to stay.

PS. To the open source devs out there, your doing a great job, you've got my vote already. Its by working together that got it this far and I cant wait to see the progress yet to be made.

---

### Post by donniezazen on 2009-12-21
Ah! a little vindication (after open source prosecution). I started this thread just to bring developers' attention to these important issues. I am trying to convince other people to use Ubuntu and when they install it what do they face - they cannot wirelessly connect to internet, they cannot play music watch movies they own. Are they going to like Ubuntu? Should my grandmother build a new linux friendly computer?

---

### Post by ken_do_san on 2009-12-21
> **snowpine said:**
> Broadcom's Linux driver is freely available here: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

What's the big deal? ;)

snowpine, thanks for the link, worked first time after install.  Much easier than the last effort to get wireless working.

Cheers mate

:cool:

---

### Post by Rocket2DMn on 2009-12-21
Moved to Recurring Discussions.

---

### Post by Tibuda on 2009-12-21
> **soham_1207 said:**
> Ah! a little vindication (after open source prosecution). I started this thread just to bring developers' attention to these important issues. I am trying to convince other people to use Ubuntu and when they install it what do they face - they cannot wirelessly connect to internet, they cannot play music watch movies they own. Are they going to like Ubuntu? Should my grandmother build a new linux friendly computer?

Do you know this is also true for Windows, right? Stuff have improved a lot with Win7, but you still have to do some driver-hunting.

Keep in mind that just because your hardware don't work out-of-the-box, it does not mean every hardware would not work. My wireless card works perfectly. The Ubuntu LiveCD is a great way to test if it works before installing it.

---

### Post by Twitch6000 on 2009-12-21
I suggest using OpenSuse,unlike ubuntu it is a dvd and within that dvd contains all the software you need to get running. Heck it saves me about 30 minutes getting my laptop set up :).

---

### Post by Twitch6000 on 2009-12-21
> **danielrmt said:**
> Do you know this is also true for Windows, right? Stuff have improved a lot with Win7, but you still have to do some driver-hunting.

Keep in mind that just because your hardware don't work out-of-the-box, it does not mean every hardware would not work. My wireless card works perfectly. The Ubuntu LiveCD is a great way to test if it works before installing it.

Actually Windows 7 works on all 4 boxes I have tested right out of the box no driver finding needed.

You little kiddoes need to quit thinking about the ancient xp,yes it was and still is a great OS,but it is ancient. Windows Vista and 7 both have better hardware support out of the box.

You know why though,because unlike ubuntu they don't mind making a dvd size OS. The reason being is so it can contain all the things needed. This is why I like larger distros like Mandriva and Opensuse is all my stuff comes default in the dvd.

---

### Post by Grifulkin on 2009-12-21
> **soham_1207 said:**
> Hi,

There should be many threads like this. Sorry for another redundant thread. I completely moved to Ubuntu 2-3 years ago and i keep Ubuntu installation in my flash drive because i like to mess it up. The two things that i have always hated are-

1. Getting wireless done is the biggest problem. I have to have a LAN connection to connect my laptop and install restricted drivers.

2. Since Ubuntu doesn't come pre-installed with restricted format and wifi doesn't work without restricted drivers, you are once again struck with the classic Ubuntu paradox.

Are developers working on these problem? Since in any case i will have to install restricted and proprietary drivers, why don't they come pre-installed (Ubuntu may add a notice to clear its software policy)?

Thanks,
SK.

P.S.-If there is an active thread going around these topics please merge them.

My biggest gripe about Ubuntu is that it is too easy.  And installs a lot of extra stuff that I don't want and will never use.  As we speak I am in the process of converting my final laptop, that had #!Crunchbang on it to Arch.  Where I have to set up all the wireless myself.  So as far as I'm concerned Ubuntu is on the right track for getting that stuff to work out of the box for people such as yourself that like that sort of thing.

Also P.S. you can't blame them for not having the Restricted Drivers in the main install if they tried to just get all of the Wireless cards to work on a Live CD they would need a hell of a lot more room.

---

### Post by Tibuda on 2009-12-21
> **Twitch6000 said:**
> Actually Windows 7 works on all 4 boxes I have tested right out of the box no driver finding needed.

You little kiddoes need to quit thinking about the ancient xp,yes it was and still is a great OS,but it is ancient. Windows Vista and 7 both have better hardware support out of the box.

You know why though,because unlike ubuntu they don't mind making a dvd size OS. The reason being is so it can contain all the things needed. This is why I like larger distros like Mandriva and Opensuse is all my stuff comes default in the dvd.

Yes, I believe yo, but I'm not talking about XP, I'm talking about 7. I have installed it on my brother's laptop (that had Vista before) and had to use a wired connection to download the wireless card driver from the manufacturer website. But the sound card worked out-of-the-box, unlike Vista. That laptop never had XP installed.

---


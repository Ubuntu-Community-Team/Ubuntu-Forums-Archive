---
title: "Need help picking a Linux Distro"
date: 2008-10-22
forum: Other OS Talk
---

### Post by Twitch6000 on 2008-10-22
Well I didn't think I would need to do this,but it turns out I need to =[.

So my hp g60-120us is not liking any Linux distro I have gave it so far.

Ofcourse most of my Linux distro cds are atleast one version old(yeah I am that way).

So I need help choosing a distro that will work with it almost 100% or get wireless and the graphics in a few clicks.

I have tried these distros

Ubuntu 8.4 it tried to work but never went to the gui =[.

Ubuntu 8.10 beta had trouble with my graphics card(nvidia 8200 m)

PClinuxOs08 gnome edition I thought this one was going to work,but it froze during loading.

Linux Mint 4 same as Ubuntu 8.10.

Dream Linux 3.0 it trys to load the gui but either freezes or goes to the command line.

So yeah what might work with this crazy laptop lol.

Link for specs -[http://www.circuitcity.com/ssm/HP-G60-120US-15-6-Widescreen-Laptop-G60-120US/sem/rpsm/oid/223182/catOid/-12963/rpem/ccd/productDetail.do#prodspecs](http://www.circuitcity.com/ssm/HP-G60-120US-15-6-Widescreen-Laptop-G60-120US/sem/rpsm/oid/223182/catOid/-12963/rpem/ccd/productDetail.do#prodspecs)

Oh and it has a atheros wireless card(I know the link doesn't say that)

By the way I don't have anything I want specifically just not gentoo or arch.


Edit: Ok I am using Mandriva 2009 and it installed fine everything working and detected except wireless.

It needs something called ''wireless-tools''.

They are apparently missing. If someone can help me get them I should be able to get up and running :).

Edit 2: as it seems people are still bumping this thread... I have fixed my problem awhile back look at my siggy for what distros I am using :/.

---

### Post by simtaalo on 2008-10-22
use the LATEST version of mint. a year is a very long time in linux world.
[http://www.linuxmint.com/download.php](http://www.linuxmint.com/download.php)

it should pick everything up straightaway.

---

### Post by Twitch6000 on 2008-10-22
> **simtaalo said:**
> use the LATEST version of mint. a year is a very long time in linux world.
[http://www.linuxmint.com/download.php](http://www.linuxmint.com/download.php)

it should pick everything up straightaway.

Yeah I was thinking about that when I asked the question.

Downloading now.

Any other suggestions :) I am not a one Linux distro man :).

---

### Post by Dragonbite on 2008-10-22
> **Twitch6000 said:**
> Well I didn't think I would need to do this,but it turns out I need to =[.

So my hp g60-120us is not liking any Linux distro I have gave it so far.

Ofcourse most of my Linux distro cds are atleast one version old(yeah I am that way).

So I need help choosing a distro that will work with it almost 100% or get wireless and the graphics in a few clicks.

I have tried these distros

Ubuntu 8.4 it tried to work but never went to the gui =[.

Ubuntu 8.10 beta had trouble with my graphics card(nvidia 8200 m)

PClinuxOs08 gnome edition I thought this one was going to work,but it froze during loading.

Linux Mint 4 same as Ubuntu 8.10.

Dream Linux 3.0 it trys to load the gui but either freezes or goes to the command line.

So yeah what might work with this crazy laptop lol.

Link for specs -[http://www.circuitcity.com/ssm/HP-G60-120US-15-6-Widescreen-Laptop-G60-120US/sem/rpsm/oid/223182/catOid/-12963/rpem/ccd/productDetail.do#prodspecs](http://www.circuitcity.com/ssm/HP-G60-120US-15-6-Widescreen-Laptop-G60-120US/sem/rpsm/oid/223182/catOid/-12963/rpem/ccd/productDetail.do#prodspecs)

Oh and it has a atheros wireless card(I know the link doesn't say that)

By the way I don't have anything I want specifically just not gentoo or arch.

I have had best success with [[COLOR="Blue"]openSUSE [/COLOR]]("http://www.opensuse.org")in hardware detection. They are also supposed to have good 64bit support, though I've never had a 64bit system so I can't speak from experience.

The computer club has a couple servers and CentOS (a Red Hat clone) and Ubuntu couldn't install on it but openSUSE didn't have any problems.

On my laptop (prior to 8.04), Suspend and Hibernate didn't work with Ubuntu but worked fine with openSUSE.

For best results, make sure it is openSUSE with either KDE 3.5 or Gnome.  KDE 4 is not stable yet though they are working on it and openSUSE is one of the major contributors to KDE in general.

Oh, and their forums are friendly and helpful. Their Wiki can use some work but it does have a lot of information in there.

---

### Post by AllenGG on 2008-10-22
For quick and dirty hardware detection try Knoppix.  Should verify the hardware. HP usually puts in mid-range cards. CPU's are different one model to another.
Is yours : **AMD Turion 64 X2**

a 64 bit CPU needs Ubuntu 8.04 : amd-64-generic
Is that what you're using ?
Allen

---

### Post by xnostradamusx on 2008-10-22
try mandriva one 2009 [www.mandriva.com](www.mandriva.com) they got good hardware detection it was only the first distro i tryed did my atheros wireless card work no problem:popcorn:

---

### Post by simtaalo on 2008-10-22
> **Twitch6000 said:**
> Yeah I was thinking about that when I asked the question.

Downloading now.

Any other suggestions :) I am not a one Linux distro man :).

mint will probably be the easiest, but im sure the other suggestions would be good too. i have a HP laptop similar to yours and mint picked everything up on mine perfectly.

ive played around sabayon recently that looks pretty good too.

---

### Post by Helios1276 on 2008-10-22
what about the latest Fedora? It seems quite solid.

---

### Post by billgoldberg on 2008-10-22
Well, take a distro with the latest stable kernel.

The new kernel has better wifi support.

---

### Post by Twitch6000 on 2008-10-22
> **AllenGG said:**
> For quick and dirty hardware detection try Knoppix.  Should verify the hardware. HP usually puts in mid-range cards. CPU's are different one model to another.
Is yours : **AMD Turion 64 X2**

a 64 bit CPU needs Ubuntu 8.04 : amd-64-generic
Is that what you're using ?
Allen

yes my laptop is using AMD turion 64 X2 and I have tried Ubuntu 8.04 64 bit and 32 bit both gave the same problem.

> **xnostradamusx said:**
> try mandriva one 2009 [www.mandriva.com](www.mandriva.com) they got good hardware detection it was only the first distro i tryed did my atheros wireless card work no problem:popcorn:

Ahh yes what PClinuxOS is based on(well an older version,but still).

I might give that a go.

---

### Post by MasterNetra on 2008-10-22
meh, Knoppix doesn't upgrade. At least not back when i tried it. idk about now.

---

### Post by kdcoetzee on 2008-10-22
> **simtaalo said:**
> use the LATEST version of mint. a year is a very long time in linux world.
[http://www.linuxmint.com/download.php](http://www.linuxmint.com/download.php)

it should pick everything up straightaway.
Mint is based on Ubuntu. (I have never used it, that is why I am asking)

So if he had trouble with Ubuntu 8.04 and 8.10 beta. then he would have trouble with mint ?

And one of my colleague is using Mandriva and his hardware support is not bad.
I would just wait for Ubuntu 8.10 final. Just a few days left.

---

### Post by simtaalo on 2008-10-22
> **Juggernaut_KDC said:**
> Mint is based on Ubuntu. (I have never used it, that is why I am asking)

So if he had trouble with Ubuntu 8.04 and 8.10 beta. then he would have trouble with mint ?

mint is based on ubuntu yes, but it has extra bits.

---

### Post by Twitch6000 on 2008-10-22
Well just tried Linux Mint 5 and it didn't like me either =[.

I tried both start modes and both came up to that command like with the help options =[.

So I tried startx and it said it wasn't a command =[.

I guess i will get mandriva 09.

---

### Post by Dragonbite on 2008-10-22
> **Twitch6000 said:**
> Well just tried Linux Mint 5 and it didn't like me either =[.

I tried both start modes and both came up to that command like with the help options =[.

So I tried startx and it said it wasn't a command =[.

I guess i will get mandriva 09.

I still would suggest openSUSE. I've had good luck with them.

---

### Post by Twitch6000 on 2008-10-22
> **Dragonbite said:**
> I still would suggest openSUSE. I've had good luck with them.

I guess I can give OpenSuse a second chance.

I just hope it doesn't hate my wireless card like it did on my last laptop that only had a intel wireless chip lol.

---

### Post by Twitch6000 on 2008-10-22
Ok Opensuse11 worked and installed fine.

One problem though and only one :(.

I cannot figure out how to get my wireless card to work.

It is a atheros card so I know it might be hard to get to work >.>.

Anyways it was easy to set up a dual boot and get the graphics card set up.

Infact I think the only problem i am having is my wireless lol.

---

### Post by cardinals_fan on 2008-10-22
> **Twitch6000 said:**
> Ok Opensuse11 worked and installed fine.

One problem though and only one :(.

I cannot figure out how to get my wireless card to work.

It is a atheros card so I know it might be hard to get to work >.>.

Anyways it was easy to set up a dual boot and get the graphics card set up.

Infact I think the only problem i am having is my wireless lol.
[http://en.opensuse.org/Atheros_madwifi](http://en.opensuse.org/Atheros_madwifi)

---

### Post by Twitch6000 on 2008-10-22
> **cardinals_fan said:**
> [http://en.opensuse.org/Atheros_madwifi](http://en.opensuse.org/Atheros_madwifi)

Humm ok so I will have to hook up to ethernet first >.>.

---

### Post by Dragonbite on 2008-10-22
> **Twitch6000 said:**
> Ok Opensuse11 worked and installed fine.

One problem though and only one :(.

I cannot figure out how to get my wireless card to work.

It is a atheros card so I know it might be hard to get to work >.>.

Anyways it was easy to set up a dual boot and get the graphics card set up.

Infact I think the only problem i am having is my wireless lol.

From the openSUSE Wiki:
> In openSUSE, starting with version 10.1, the MadWiFi driver for Atheros wireless cards are not included in the distribution as its HAL module is only available as proprietary. However, it is still possible to use this driver. 

Here's a link for Atheros madwifi : [[COLOR="Blue"]http://en.opensuse.org/Atheros_madwifi[/COLOR]]("http://en.opensuse.org/Atheros_madwifi")

It also includes a link for a "One Click Install" for 11 which makes things easier.  Read around a little first.

Here's a link on their Wiki for using the Atheros ndiswrapper : [[COLOR="Blue"]http://en.opensuse.org/Atheros_ndiswrapper[/COLOR]]("http://en.opensuse.org/Atheros_ndiswrapper"). This link just lists 10.1 so I'm not sure how up-to-date it is.

So I would suggest trying the madwifi first and if that doesn't work try the ndiswrapper.

If you want, I could post a question on the forum for you, just let me know what you want to ask.

---

### Post by Twitch6000 on 2008-10-22
ok I installed the madwifi.rpm I got from one of those links and after that I restarted the networks.

I still however cannot get internet =[.

What else do I need to do?

---

### Post by cardinals_fan on 2008-10-22
> **Twitch6000 said:**
> ok I installed the madwifi.rpm I got from one of those links and after that I restarted the networks.

I still however cannot get internet =[.

What else do I need to do?
Did you also install madwifi-kmp-*?  Did you run ```
modprobe ath_pci
modprobe -l | grep ath
```?  Did you reboot?  Did you read this note > Note: in the openSUSE 11.0 there may be a conflict with built Atheros module ath5k, which seems is not functional yet, but prevents using madwifi's driver. Resolution is to add this module, to the blacklist. To do this add the line blacklist ath5k to the file /etc/modprobe.d/blacklist and reboot. 
?

---

### Post by Twitch6000 on 2008-10-22
> **cardinals_fan said:**
> Did you also install madwifi-kmp-*?  Did you run ```
modprobe ath_pci
modprobe -l | grep ath
```?  Did you reboot?  Did you read this note ?

Yes I installed the madwifi-kmp-* it had trouble installing and said it installed partly or something.

I didn't do the mod probe thing though.

Might that fix the problem?

---

### Post by cardinals_fan on 2008-10-22
> **Twitch6000 said:**
> 
I didn't do the mod probe thing though.

Might that fix the problem?
Yes.  It loads the kernel module.  You need to do it as root.

"man modprobe" might be helpful

---

### Post by Twitch6000 on 2008-10-22
> **cardinals_fan said:**
> Yes.  It loads the kernel module.  You need to do it as root.

"man modprobe" might be helpful

ok tried it and 

modprobe ath_pci

did not work.(yes I did tried as root).

---

### Post by cardinals_fan on 2008-10-23
> **Twitch6000 said:**
> ok tried it and 

modprobe ath_pci

did not work.(yes I did tried as root).
Maybe the driver didn't install right.  Reboot and try modprobeing it again.  If it still doesn't work, check that you downloaded the right madwifi-kmp version.

---

### Post by Twitch6000 on 2008-10-23
Ok I think I have found the problem =/.

Its the wireless card itself.

It is a Atheros AR5009 802.11a/g/n WiFi Adapter

---

### Post by Twitch6000 on 2008-10-23
Ok I think I have found the problem =/.

Its the wireless card itself.

It is an Atheros AR5009 802.11a/g/n WiFi Adapter

---

### Post by xnostradamusx on 2008-10-23
if you have time try mandriva one 2009 i have high hopes for when you try it everything works out of the box since im using atheros wireless also and everything was detected

---

### Post by Twitch6000 on 2008-10-24
Ok so opensuse has given me enough trouble and I gave up on it :/.

It seems it won't even detect my ethernet..(ofcourse this could just be me as I am not use to some of the tools it has)

So now I installed Mandriva09 and it is working great it detects my wireless card and everything else out of the box.

One problem though when I try to connect with wireless it doesn't work.

So I go ok maybe I need to still set it up,I try that and it says I am missing a wireless program or something.(I forget the name)

Other then that though Ethernet works,graphics work,the KDE desktop looks great,and has anything I need.

I just need my wifi so yeah help fix this tiny problem?

Oh and on a off topic note I have noticed something that I liked about both mandriva and opensuse11 that I disliked about ubuntu 8.04.

That is the installers they are very neat and clean on Mandriva and OpenSuse,while on Ubuntu it is somewhat clean,but hard to use.

---

### Post by forrestcupp on 2008-10-24
I suggest going back to Ubuntu 8.10.  The reason I say that is because you're going to have the same amount of trouble with your nvidia GPU no matter what distro you use.  Atheros wireless works out of the box with Ubuntu.  I got one for my desktop and plugged it in expecting to spend the day figuring it out.  When I booted into Ubuntu, it just worked.  It's in your Restricted Drivers Manager or whatever it is they call it now.  But for me, it just started up automatically enabled.

If you're patient and search the forums, you'll find plenty of help to get your nvidia working, and it shouldn't really be that hard.  You didn't even tell us what kind of trouble you *had* in 8.10 with it.

---

### Post by Twitch6000 on 2008-10-24
> **forrestcupp said:**
> I suggest going back to Ubuntu 8.10.  The reason I say that is because you're going to have the same amount of trouble with your nvidia GPU no matter what distro you use.  Atheros wireless works out of the box with Ubuntu.  I got one for my desktop and plugged it in expecting to spend the day figuring it out.  When I booted into Ubuntu, it just worked.  It's in your Restricted Drivers Manager or whatever it is they call it now.  But for me, it just started up automatically enabled.

If you're patient and search the forums, you'll find plenty of help to get your nvidia working, and it shouldn't really be that hard.  You didn't even tell us what kind of trouble you *had* in 8.10 with it.

I have a nvidia 8200 m and this card right now has a bug with the 8.10 beta where xserver fails to start..

This happens with 8.04 aswell.

I mentioned this already in my first post briefly.

Oh and OpenSuse11 and Mandriva 09 have not given me any trouble with my graphics card.

---

### Post by Dragonbite on 2008-10-24
> **Twitch6000 said:**
> Oh and OpenSuse11 and Mandriva 09 have not given me any trouble with my graphics card.
Just wireless, right?

---

### Post by Twitch6000 on 2008-10-24
> **Dragonbite said:**
> Just wireless, right?

Correct for Mandriva,Opensuse did not like ethernet either :(.
Mandriva is atleast showing that it knows it is there and telling me the problem.

Opensuse however I needed info off the site and it still didn't work due to the Ethernet not wanting to work correctly.

---

### Post by Twitch6000 on 2008-10-25
Ok I found what I need in mandriva 09.

It is called ''Wireless-tools''.

If I get these I will probably be able to hook right up no problem.

I do not know where to get this though because I normally use distros with .debs.

---

### Post by xnostradamusx on 2008-10-25
@forrestcupp mind you im using atheros wireless also but its detected by ubuntu but it isnt working at all it even says its supported and it is in use but when you right click on network manager there is no edit wireless that should be there when your wireless card is working

@twitch i know about that in mandriva which you can see wireless ap but cant connect when your trying to access it. there is one solution for that known bug here you go

[http://forum.mandriva.com/viewtopic.php?t=96921&highlight=](http://forum.mandriva.com/viewtopic.php?t=96921&highlight=)

---

### Post by K.Mandla on 2008-10-25
Moved to Other OS Talk.

---

### Post by Dragonbite on 2008-10-25
I've never heard of Linux having trouble with a wired NIC.  Guess I haven't been around enough.

Does anybody know of a way to make sure the wireless card is working?

I only ask this because on my system, my wireless is detected but it isn't working. I've verified it is not the router, and with the Ubuntu LiveCD I went through the same restricted drivers installation I did on the actual install (whence it did work for a while) and still did not work, so I am suspecting it is the wireless card gone kaput!

Might be aggrivating trying distro after distro if it is a hardware problem.

btw.. it's a Broadcomm

---

### Post by kdcoetzee on 2008-10-25
> **Dragonbite said:**
> I've never heard of Linux having trouble with a wired NIC.  Guess I haven't been around enough.

Does anybody know of a way to make sure the wireless card is working?

I only ask this because on my system, my wireless is detected but it isn't working. I've verified it is not the router, and with the Ubuntu LiveCD I went through the same restricted drivers installation I did on the actual install (whence it did work for a while) and still did not work, so I am suspecting it is the wireless card gone kaput!

Might be aggrivating trying distro after distro if it is a hardware problem.

btw.. it's a Broadcomm

Try connecting to a different router.
My wireless had a tendency to stop working when I used Ubuntu.
The wireless connect perfectly at work, but at home... not a change.
and the strange thing is. it works after a clean install but after a week it stops connecting on my wireless at home.
```

02:0e.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

```

But at this moment I am using Gentoo with openbox. and wireless is working great. even better that with Ubuntu.

So I doubt it is your wireless that broke.

---

### Post by Twitch6000 on 2008-10-26
> **xnostradamusx said:**
> @forrestcupp mind you im using atheros wireless also but its detected by ubuntu but it isnt working at all it even says its supported and it is in use but when you right click on network manager there is no edit wireless that should be there when your wireless card is working

@twitch i know about that in mandriva which you can see wireless ap but cant connect when your trying to access it. there is one solution for that known bug here you go

[http://forum.mandriva.com/viewtopic.php?t=96921&highlight=](http://forum.mandriva.com/viewtopic.php?t=96921&highlight=)

Humm that did not seem to fix my problem >.>.

@Dragonbite neither have I, until OpenSuse lol.

OpenSuse has shown me many things that other distros have not shown before.

So can someone show me how to get these ''wireless-tools''?

---

### Post by cardinals_fan on 2008-10-26
> **Twitch6000 said:**
> 
That is the installers they are very neat and clean on Mandriva and OpenSuse,while on Ubuntu it is somewhat clean,but hard to use.
I know what you mean about "neat and clean" installers, but I can't imagine any way in which Ubuntu's qualifies as "hard to use".

---

### Post by Twitch6000 on 2008-10-26
> **cardinals_fan said:**
> I know what you mean about "neat and clean" installers, but I can't imagine any way in which Ubuntu's qualifies as "hard to use".

Maybe I picked the wrong words,maybe the ubuntu installer has less ease of use.

What i mean is ubuntu has only three options when you get ready for the install itself.(you know for putting it on your hdd)

Then not only that the options are kind of hard to choose out of(for a novice user).

I mean heck when I was using gusty I mistook one of the options for something else and put ubuntu on my entire Hard drive instead of part of it =[.

Hardy did however do something right making wubi come with it and such.

With mandriva however you got like 5 options telling you what exactly they do.

Aswell as your normal custom install so it makes it real easy :).

---

### Post by Dragonbite on 2008-10-27
> **Juggernaut_KDC said:**
> Try connecting to a different router.
My wireless had a tendency to stop working when I used Ubuntu.
The wireless connect perfectly at work, but at home... not a change.
and the strange thing is. it works after a clean install but after a week it stops connecting on my wireless at home.
```

02:0e.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

```


The thing that keeps me from thinking it is the router is I also am not seeing the neighbor's networks (which I usually can .. there are 2 on one side of the house and 1 or 2 on the other side).

---

### Post by wykedengel on 2008-10-27
> **xnostradamusx said:**
> try mandriva one 2009 [www.mandriva.com](www.mandriva.com) they got good hardware detection it was only the first distro i tryed did my atheros wireless card work no problem:popcorn:


I also have to nod my head towards Mandriva 2009. So far (I haven't tried OpenSuse yet)it is the only distro that worked from me out the box, including wireless.

---

### Post by neoflight on 2008-10-27
centOS 5.2. Great distro.

---

### Post by Twitch6000 on 2008-10-27
Wow this is getting a weee bit off topic >.>.

Maybe I need to update the first post lol.

My new goal is this I am using Mandriva 2009.

Can someone show me how to get these ''wireless-tools''?

---

### Post by cardinals_fan on 2008-10-27
> **Twitch6000 said:**
> 
Can someone show me how to get these ''wireless-tools''?
I would think it should be included by default.  However, if it doesn't work, maybe it needs to be downloaded.  If Mandriva works with your ethernet, just use the GUI package manager (or urpmi, the CLI version) to install a package called "wireless-tools" or something along those lines.  If not, check the dependencies and download the RPMs, moving them over on a Flash drives (just like you would with a Debian-based distro; the differences are minor).

---

### Post by Twitch6000 on 2008-10-27
> **cardinals_fan said:**
> I would think it should be included by default.  However, if it doesn't work, maybe it needs to be downloaded.  If Mandriva works with your ethernet, just use the GUI package manager (or urpmi, the CLI version) to install a package called "wireless-tools" or something along those lines.  If not, check the dependencies and download the RPMs, moving them over on a Flash drives (just like you would with a Debian-based distro; the differences are minor).

I would prefer to just get the .rpm.

Do you know where to get it?

If so please link me =].

---

### Post by cardinals_fan on 2008-10-27
Wait a second.  Take a look at [http://forum.mandriva.com/viewtopic.php?t=96919&view=previous&sid=50492f653f8fbbb836239709b47a1dd2](http://forum.mandriva.com/viewtopic.php?t=96919&view=previous&sid=50492f653f8fbbb836239709b47a1dd2) and [https://qa.mandriva.com/show_bug.cgi?id=45062](https://qa.mandriva.com/show_bug.cgi?id=45062)

Could that be the problem?  Mandriva is supposed to include ath9k drivers by default in 2009...

---

### Post by Twitch6000 on 2008-10-27
> **cardinals_fan said:**
> Wait a second.  Take a look at [http://forum.mandriva.com/viewtopic.php?t=96919&view=previous&sid=50492f653f8fbbb836239709b47a1dd2](http://forum.mandriva.com/viewtopic.php?t=96919&view=previous&sid=50492f653f8fbbb836239709b47a1dd2) and [https://qa.mandriva.com/show_bug.cgi?id=45062](https://qa.mandriva.com/show_bug.cgi?id=45062)

Could that be the problem?  Mandriva is supposed to include ath9k drivers by default in 2009...

I tried that already and it did not fix anything.

I am still getting the same error.

---

### Post by cardinals_fan on 2008-10-27
> **Twitch6000 said:**
> 
I am still getting the same error.
...which is?

---

### Post by Twitch6000 on 2008-10-27
> **cardinals_fan said:**
> ...which is?

(wireless-tools are missing).... I click ok

It trys to download them

(unable to install wireless-tools)


Or something along those lines.

I also cannot use the main computer right now that has the Ethernet so.. I need the wireless-tools.rpm :/.

---

### Post by cardinals_fan on 2008-10-27
It's easy enough to find an rpm for wireless-tools.  However, rpmfind hasn't updated for Mandriva 2009 yet ([http://rpmfind.net/linux/rpm2html/search.php?query=wireless-tools](http://rpmfind.net/linux/rpm2html/search.php?query=wireless-tools)), and I don't know if Mandriva has an online package search (they should).

---

### Post by Twitch6000 on 2008-10-27
> **cardinals_fan said:**
> It's easy enough to find an rpm for wireless-tools.  However, rpmfind hasn't updated for Mandriva 2009 yet ([http://rpmfind.net/linux/rpm2html/search.php?query=wireless-tools](http://rpmfind.net/linux/rpm2html/search.php?query=wireless-tools)), and I don't know if Mandriva has an online package search (they should).

well do you think the 2008 version will work?

If it will I will just install it and update from there.

---

### Post by cardinals_fan on 2008-10-27
> **Twitch6000 said:**
> well do you think the 2008 version will work?

If it will I will just install it and update from there.
Doubtful (kernel versions have changed), but you can give it a shot.

If you have an ethernet connection, does Mandriva work with it?

---

### Post by Twitch6000 on 2008-10-27
> **cardinals_fan said:**
> Doubtful (kernel versions have changed), but you can give it a shot.

If you have an ethernet connection, does Mandriva work with it?

I know it detects it,I have not tried using it yet though.

I have another question now though.

I found the add/remove program thing like ubuntu has,but where is its package manager located at?

---

### Post by cardinals_fan on 2008-10-27
> **Twitch6000 said:**
> 
I found the add/remove program thing like ubuntu has,but where is its package manager located at?
That **is** the graphical package manager.  The CLI package manager is urpmi.

If you get the ethernet working, just download wireless-tools with the package manager.

---

### Post by Sorivenul on 2008-10-27
> **cardinals_fan said:**
> That **is** the graphical package manager.  The CLI package manager is urpmi.

If you get the ethernet working, just download wireless-tools with the package manager.

Correct.  More specifically, the CLI package installer is urpmi (though the entire package system is referred to as urpmi as well).  There is a great urpmi cheatsheet on DistroWatch.  Will try to find the link.  The actual graphical frontend you found is rpmdrake.  This doesn't help your "wireless-tools" issue, but is good knowledge going forward with Mandriva.  Good luck.

---

### Post by Twitch6000 on 2008-10-27
> **cardinals_fan said:**
> That **is** the graphical package manager.  The CLI package manager is urpmi.

If you get the ethernet working, just download wireless-tools with the package manager.

Oh ok that explains some things then lol.

Well then it does not come up with results for wireless-tools.

I might just have to wait for that other link you gave me to update their package :/.

---

### Post by cardinals_fan on 2008-10-27
> **Twitch6000 said:**
> Oh ok that explains some things then lol.

Well then it does not come up with results for wireless-tools.

I might just have to wait for that other link you gave me to update their package :/.
If you don't have an internet connection, you can't expect it to search for something.  If you do, look for a box involving graphical apps and change it to include CLI apps too (I'll look for a better description).

EDIT: If you have an internet connection, try (as root) "urpmi wireless-tools" in the console.

---

### Post by wolfen69 on 2008-10-28
i went  to distrowatch.com and went nuts. that's how i  learned.

---

### Post by alwez_loner_TZ on 2008-10-28
I wanted to know what do you people think of Dream linux and PC BSD?

---

### Post by Twitch6000 on 2008-10-28
> **alwez_loner_TZ said:**
> I wanted to know what do you people think of Dream linux and PC BSD?

Dream Linux 3.2 is decent,but can get real buggy after installing.

PC BSD I have not tried so I couldn't say.

---

### Post by Dragonbite on 2008-10-28
> **Twitch6000 said:**
> Dream Linux 3.2 is decent,but can get real buggy after installing.

PS BSD I have not tried so I couldn't say.

I have a co-worker who is a BSD guy.  He mentioned that BSD is supposed to have good wireless support.  

Don't know how real it is or not but that's something he mentioned when I told him about my wireless issues.

May be worth a look into, even if just their documentation and forums?

---

### Post by Twitch6000 on 2008-10-28
> **Dragonbite said:**
> I have a co-worker who is a BSD guy.  He mentioned that BSD is supposed to have good wireless support.  

Don't know how real it is or not but that's something he mentioned when I told him about my wireless issues.

May be worth a look into, even if just their documentation and forums?

I am more of a Open Solaris fan when it comes to others besides Windows,Mac,and Linux.

By the way I still have not tried what Cardinal fan suggested yet due to me not getting a chance lol..

I might have to wait it out and get Ubuntu 8.10 final.

---

### Post by phidia on 2008-10-28
I'm running Mepis the latest beta 4, I believe (see distro watch). 
On this hp laptop with the atheros 5007 card it found the card automatically and internet was working when I logged into the demo user. 

Mepis (not a great name choice) is based on debian so it's generally the same as ubuntu. KDE default desktop though. Maybe dl and give mepis a try?

---

### Post by Twitch6000 on 2008-10-28
Well I got something figured out finally...

After screwing up my bootup a few times and downloading about 5 different distros I got something that works lol.... sorta...

Ubuntu 8.10 RC1 is working fine for me right now along with mandriva 09.

With them both together I can get one fully working 100% lol.

Ubuntu has wireless working,but graphics not wanting too work.

Mandriva the opposite, graphics works great,but wireless is not working.

So give me a week and I will get one working....

If I don't well,that is just sad lol.

---

### Post by cardinals_fan on 2008-10-28
> **Dragonbite said:**
> I have a co-worker who is a BSD guy.  He mentioned that BSD is supposed to have good wireless support.  

Don't know how real it is or not but that's something he mentioned when I told him about my wireless issues.

May be worth a look into, even if just their documentation and forums?
I love NetBSD, and FreeBSD is also very good.  However, hardware support is usually worse than Linux.

I would recommend DesktopBSD over PC-BSD.

---

### Post by Zero Prime on 2008-10-31
Ultimate Edition has very good support for both graphics and wireless.  You could give it a try.  Ultimate Edition 2.0 will be out soon.  The web site is under re-construction right now but you can find download links at the Ultimate Forum.  The link to the forum is in my sig.

---

### Post by Twitch6000 on 2008-10-31
Uhmmm I have finally got what I need.

What I have choosen is all in my siggy :).

Big thanks to Cardinal fan and Dragon bite as they got me through my biggest problems.

Also thanks to everyone else that helped me along the way :D.

---

### Post by cardinals_fan on 2008-10-31
> **Twitch6000 said:**
> Uhmmm I have finally got what I need.

What I have choosen is all in my siggy :).

Big thanks to Cardinal fan and Dragon bite as they got me through my biggest problems.

Also thanks to everyone else that helped me along the way :D.
No problem :D

---

### Post by Dragonbite on 2008-10-31
> **Twitch6000 said:**
> Uhmmm I have finally got what I need.

What I have choosen is all in my siggy :).

Big thanks to Cardinal fan and Dragon bite as they got me through my biggest problems.

Also thanks to everyone else that helped me along the way :D.
Glad could be of help.

---

### Post by the_Ben on 2008-11-01
> **Twitch6000 said:**
> Uhmmm I have finally got what I need.

What I have choosen is all in my siggy :).

Big thanks to Cardinal fan and Dragon bite as they got me through my biggest problems.

Also thanks to everyone else that helped me along the way :D.

I'm rocking the HP G60 as well.  Just curious how you implemented your system.  Do you have Ubuntu 8.10 and Mandriva '09 on different partitions, or is there some mystical way of combining their features so you don't have to switch OS's if you need graphics or wireless?  Thanks in advance!

---

### Post by Twitch6000 on 2008-11-01
> **the_Ben said:**
> I'm rocking the HP G60 as well.  Just curious how you implemented your system.  Do you have Ubuntu 8.10 and Mandriva '09 on different partitions, or is there some mystical way of combining their features so you don't have to switch OS's if you need graphics or wireless?  Thanks in advance!

Oh I have Mandriva has the main host.

The windows on another partition.

Windows installed first and Mandriva second.

Mandriva then gets put as the bootloader and such.

Then I got into my windows partition and install ubuntu through wubi.

So if I wanna use ubuntu I use the windows bootloader.

I know its an odd way to tri boot,but it works for me :).

---

### Post by the_Ben on 2008-11-02
> **Twitch6000 said:**
> Oh I have Mandriva has the main host.

The windows on another partition.

Windows installed first and Mandriva second.

Mandriva then gets put as the bootloader and such.

Then I got into my windows partition and install ubuntu through wubi.

So if I wanna use ubuntu I use the windows bootloader.

I know its an odd way to tri boot,but it works for me :).

Ah.  I was hoping I could find something that wouldn't force me to switch OS's based on if I needed graphics or wifi.  I mean, I have to do that already for some Windows programs.  haha  Maybe I'll see if I can make due with ubuntu 8.10.

---

### Post by Twitch6000 on 2008-11-02
*deleted*

---

### Post by Twitch6000 on 2008-11-02
> **the_Ben said:**
> Ah.  I was hoping I could find something that wouldn't force me to switch OS's based on if I needed graphics or wifi.  I mean, I have to do that already for some Windows programs.  haha  Maybe I'll see if I can make due with ubuntu 8.10.

Might I note I am no longer having wifi and/or Graphics problems with Mandriva Or Ubuntu.

---

### Post by the_Ben on 2008-11-02
> **Twitch6000 said:**
> Might I note I am no longer having wifi and/or Graphics problems with Mandriva Or Ubuntu.

Actually, I installed 8.10 myself today and everything was pretty stellar out of the box!  The only issue is that flash movies run kinda choppy (i.e. youtube), but that seems to be an issue for everybody.  Thanks for the help anyway!

---

### Post by Twitch6000 on 2008-11-03
> **the_Ben said:**
> Actually, I installed 8.10 myself today and everything was pretty stellar out of the box!  The only issue is that flash movies run kinda choppy (i.e. youtube), but that seems to be an issue for everybody.  Thanks for the help anyway!

With Flash 10 It seems to run fine for me >.>.

Flash 9 however yes it does run choppy.

To get Flash 10 go to the adobe site and download the .deb file.

---

### Post by duanedesign on 2008-11-04
HP G60-120us

I am running ubuntu 8.10
2.6.27-7-generic

the nvidiaglx-177 driver works great with the 8200

---

### Post by the_Ben on 2008-11-06
So I installed the flash player 10 update, but it only seems to improve a little.  I'm also having an unusual issue with downloading stuff from the internet.  If I want to download a picture or something, I get the usual popup window that asks you where to save the file, but then that window freezes.  The unusual thing is all the buttons and text fields are still functional, it's just the image that's frozen.

Anyway, I could just designate everything to download to the desktop, but I'd like all the features of my OS to work.  ha  Anybody else have this issue?  FYI, I'm running 8.10 on the HP G60-125NR.

---

### Post by Twitch6000 on 2008-11-07
> **the_Ben said:**
> So I installed the flash player 10 update, but it only seems to improve a little.  I'm also having an unusual issue with downloading stuff from the internet.  If I want to download a picture or something, I get the usual popup window that asks you where to save the file, but then that window freezes.  The unusual thing is all the buttons and text fields are still functional, it's just the image that's frozen.

Anyway, I could just designate everything to download to the desktop, but I'd like all the features of my OS to work.  ha  Anybody else have this issue?  FYI, I'm running 8.10 on the HP G60-125NR.

I would start your own thread for that issue.

I myself have never ran into a problem like that so I would not know how to fix it.

My only guess would on it would be somthing relating to the video card or xserver.

---

### Post by 2hot6ft2 on 2008-11-24
I skipped a few pages since you kept going back and forth on flavors of Linux.

I have basically the same laptop a HP Pavilion [G60-125NR Notebook PC]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01533414&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN").

I am running Ubuntu Ultimate Edition 2.0 64 bit and XP Pro Ultimate on it and everything is working except the Light Scribe for the DVD Drive is only available for 32 bit Linux right now. So if you want Light Scribe to work in Linux go with the 32 bit x86.

The wifi took a little fiddling. First the AR5009 uses the AR928x driver (you have no idea how much I hate to say this but "Google it") and wireless-tools is available thru Synaptic Package Manager. So is Windows Wireless Drivers which makes it even easier. as for the graphics EnvyNG takes care of that just fine.

[Ubuntu Ultimate Edition]("http://ultimateedition.info/")

I tried UUE 2.0 on my desktop too but had to go back to UUE 1.9 64 bit because the new ATH5K for wifi was giving me headaches and there seems to be no fix as of yet.

Also UUE 2.0 uses a newer kernel than Ubuntu 8.10 I think it's 2.27.7 but wont swear to it since I'm on the desktop right now.

Hope this is useful to someone.:popcorn:

---

### Post by the_Ben on 2008-12-15
> I have basically the same laptop a HP Pavilion G60-125NR Notebook PC.

I am running Ubuntu Ultimate Edition 2.0 64 bit and XP Pro Ultimate on it and everything is working except the Light Scribe for the DVD Drive is only available for 32 bit Linux right now. So if you want Light Scribe to work in Linux go with the 32 bit x86.


Well, I'm convinced!  I'll give Ubuntu Ultimate a try and post whether it resolves all my issues or not.  Thanks!

---

### Post by mikjp on 2008-12-15
1) Get any new distro
2) Stay with it
3) Configure it

---

### Post by the_Ben on 2008-12-17
> **mikjp said:**
> 1) Get any new distro
2) Stay with it
3) Configure it

Yeah, looks like I'm going back to 8.10.  I was hoping there was some setting somewhere that Ubuntu Ultimate would have that would take care of the flash issue from the get-go.  No such luck, just a lot of extra programs I don't really need.  I'll be searching elsewhere in the forums to see if anyone with the same laptop has resolved the flash slowdown issue.

---


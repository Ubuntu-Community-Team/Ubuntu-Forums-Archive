---
title: "wicd or net_applet as default net applet"
date: 2008-06-18
forum: Recurring Discussions
---

### Post by danboid on 2008-06-18
Briefly

(k)networkmanager stinks, wicd should've been in the repos long ago (why is it still missing?) and if Ubuntu is serious about becoming a truly widespread, popular OS then replacing nm should become their priority for the next release, seriously!

Second, has anyone ever got Mandriva's net_applet to work under Ubuntu? The current stable version of wicd is good but the only perfect Linux wifi experience I've had has been under Mandriva. No drakconf no net_applet? Due to the prime importance of easy, reliable wifi I could only recommend Mandriva/PCLOS to any Linux newb as under Ubuntu theres a good chance they won't even get the net access required to download wicd.

---

### Post by Polygon on 2008-06-18
nm applet works perfectly fine for me. What exactly about it stinks?

---

### Post by Mazza558 on 2008-06-18
nm-applet all the way. Wicd broke my installation and I had to reinstall.

---

### Post by Papi-KB7VGW on 2008-06-18
I have not had any problems with nm either.

---

### Post by Judo on 2008-06-18
I don't like Gnome's manager (Ubuntu's default) very much.  It doesn't even show an option for a wireless connection when I know my drivers are installed correctly.  On the occasion that I got it to recognize the device, it didn't give me an option for WPA?  Or did I miss something?

WICD worked perfectly for everything.  There was one case where I had a friend install it from the official repos and it kept raises errors, but I've told the developer about that.  I eventually found a workaround, but I can see the problem with not having a network daemon.

---

### Post by 23meg on 2008-06-18
[QUOTE=danboid]wicd should've been in the repos long ago (why is it still missing?)[/QUOTE]

Because *gasp* nobody packaged it. If you do, it will be there.

[QUOTE=danboid]and if Ubuntu is serious about becoming a truly widespread, popular OS then replacing nm should become their priority for the next release, seriously![/QUOTE]

[http://ubuntuforums.org/showpost.php?p=5087997&postcount=4](http://ubuntuforums.org/showpost.php?p=5087997&postcount=4)
[http://ubuntuforums.org/showpost.php?p=5090589&postcount=6](http://ubuntuforums.org/showpost.php?p=5090589&postcount=6)
[http://ubuntuforums.org/showthread.php?p=5090602](http://ubuntuforums.org/showthread.php?p=5090602)

---

### Post by RiceMonster on 2008-06-18
I'm still using nm-applet because it works perfectly for me. No reason to change what works well.

---

### Post by danboid on 2008-06-19
polygon:

Why is nm so bad?

1- It doesn't work with static IP connections. It claims to, but I've never had any success with it. This is real fundamental stuff that is broke here. I can get static IP wired/wifi working fine via ifup and/or wicd but not nm. If you're not connecting DHCP via ethernet with nm then forget about it.

2- Far as I know, WPA2 still isn't supported by nm

3- nm has one of the most badly designed, confusing interfaces of any mainstream FOSS app I know of

4- All that password nonsense. wicd only requires you enter your WEP/WPA(2) password once. nm doesn't remember them and then asks you for a keyring password on top of that! Really frustrating

THose people who say they have no probs with nm likely don't use wifi, static IP addresses or move around using different networks, otherwise you'd have already switched to wicd or just give up on ubuntu as a internet platform.

I really would love to see ubuntu displace Windows as the primary OS (bug #1) but this will not happen with such a poor app being used for such a critical end-user task.

Before anyone starts, I could care less about nm's super-dooper back-end being 'done-right' - the program just doesn't work in anything but the most simple cases and it needs to totally scrap its GUI and start afresh. nm should try to support all the wifi drivers under Linux as well as wicd and Mandrivas net_applet does.

Apparently nm can also do vpn and dial-up but very few people require these versus wpa/wpa2/wep (static) wifi, which is much, much more important to get right. If this is the case I hope it handles those a lot better than it does ethernet and wifi but there are seaparate apps for connecting to dial-up and vpn which, combined with wicd, would form a much better networking solution for ubuntu.

---

### Post by beniwtv on 2008-06-19
> **danboid said:**
> 
1- It doesn't work with static IP connections. It claims to, but I've never had any success with it. This is real fundamental stuff that is broke here. I can get static IP wired/wifi working fine via ifup and/or wicd but not nm. If you're not connecting DHCP via ethernet with nm then forget about it.

The version in the Ubuntu repos still hasn't this feature I think. Version 0.7 will have that, AFAIK.  Hopefully it will be in for Intrepid.

> **danboid said:**
> 
2- Far as I know, WPA2 still isn't supported by nm


I use WPA2 without any problems so far.

> **danboid said:**
> 
3- nm has one of the most badly designed, confusing interfaces of any mainstream FOSS app I know of


Click on the NM icon, select your network, enter your password and there you go. What's confusing about that?

> **danboid said:**
> 
4- All that password nonsense. wicd only requires you enter your WEP/WPA(2) password once. nm doesn't remember them and then asks you for a keyring password on top of that! Really frustrating


It doesn't for me. On my PC, all passwords I enter are stored in the keyring. Only the first time on a new install of Ubuntu I have to create the keyring. After that, I am never again asked for the keyring. Ever. This could be related to KUbuntu, though (I'm using regular Ubuntu)...

> **danboid said:**
> 
THose people who say they have no probs with nm likely don't use wifi, static IP addresses or move around using different networks, otherwise you'd have already switched to wicd or just give up on ubuntu as a internet platform.


I roam between 2-3 networks, depending on the day. Granted, I don't use static IP's (because of NM), but it works fine here...

> **danboid said:**
> 
nm should try to support all the wifi drivers under Linux as well as wicd and Mandrivas net_applet does.

There is a reason NM doesn't support 100% yet: NM uses the wireless extensions, which not all drivers have been updated yet. However, they sooner or later will. Keep in mind that there are much changes happening right now, not just in NM, but in the whole FOSS community.

> **danboid said:**
> 
Apparently nm can also do vpn and dial-up but very few people require these versus wpa/wpa2/wep (static) wifi, which is much, much more important to get right. If this is the case I hope it handles those a lot better than it does ethernet and wifi but there are seaparate apps for connecting to dial-up and vpn which, combined with wicd, would form a much better networking solution for ubuntu.

I'm using VPN daily (OpenVPN and Cisco VPN), and they work indeed right with NM. I acually like it that I can do all my networking needs from only one program. Having multiple programs is more confusing for the users.

I'm not denying your experiences, but keep in mind that even if it doesn't work for you - for much people here it works really well. Please don't assume that everyone has the same problems as you, and that the software is bad. If you think something doesn't work right, file a bug report, talk to the NM developers, etc... so that we can all have a better product.

Cheers,

---

### Post by moore.bryan on 2008-06-19
although it's anecdotal, i've never heard of someone running ubuntu on a lenovo having success with nm and in my experience, wicd almost always solves their problems. lenovo has claimed in the past to be the "fastest growing laptop computer distributor" (sorry, no citation; couldn't find it), so it only makes sense wicd should be in the repos. however, it's not that hard just to add wicd's own repo (deb [http://wicd.longren.org/](http://wicd.longren.org/) hardy extras) to your sources list.

on my personal +1 for wicd, i've found it to be much more adaptive, intuitive, and "clean." that is made more pertinent for those of us running stripped-down boxes without gnome.

---

### Post by S-99 on 2008-07-04
I do mean to ressurect this. Yes, networkmanager sucks total balls. It really blows for wifi if it even works with wifi for many. Wicd is really the only recommendation for a full replacement of networkmanager for basic lan and wifi connectivity.

Anyway, while wicd is great. Mandriva's net_applet totally blows wicd and networkmanager out of the water. First off it works a lot better for wireless and lan connectivity. Secondly which is something ubuntu suffers from big time, it supports different types of connectivity that are out there under the sun. Stuff from ethernet, wifi, dialup, etc...all the way to dsl connectivity which is something that ubuntu lacks. You can get pppoe usage by going into the repositories and getting knet. But, knet in the repositories is currently an unstable binary (and i thought fglrx in hardy with a radeon 9500 was bad enough). And for dsl users who don't have routers and use ubuntu, are sort of a frakked when it comes to getting on the net through dsl to get a knet package from the repos that doesn't work (every normal user find it easy to use knet but not to compile it from source).

When it comes to getting a distro that people can use mandriva really makes up for what ubuntu doesn't have, even in quality. I know any one of you in this thread can grab the drakxtools or rather even just the net_applet rpms and use alien, convert to deb, and see if installation will work. Or try compiling from source. Nm, i'll try that and see where it gets me...

---

### Post by miggols99 on 2008-07-05
One annoying thing with NM is that you have to put the password in **every single user**. If it's for one person it's fine. But if it's a family computer, it can get a bit annoying...

---

### Post by smartboyathome on 2008-07-05
Anyone here try the new Network Manager from SVN? I did and it is good. I have never been a fan of WICD because it has a less than satisfactory interface, whereas Network Manager's interface is clean and simple.

---

### Post by S-99 on 2008-07-07
While the networkmanager frontends may look great. It's the backend that works like crap.

---

### Post by AdamWill on 2008-07-07
Just a technical note: I doubt it would be very easy to use Mandriva's networking tools in Ubuntu. AFAIK, we follow (more or less) the Red Hat / Fedora way of organizing and laying out network configuration files, while Ubuntu uses Debian's. The two are pretty different. So Mandriva's tools likely wouldn't do anything useful on Ubuntu as they are, even if you built them.

---

### Post by S-99 on 2008-07-07
Ubuntu uses whatever the hell is stock for a configuration modules in each of desktop environment. Preferably a better configurator would be awesome. Ubuntu system config and kubuntu system config are ok, but could work a lot better. I know one thing, and that is the kubuntu network configuration works like crap. That's because it is, and i was hoping that kde4 will offer a superior network config module.

If say the kubuntu network configuration module actually worked right. Probably a lot less people would just remove networkmanager and it's front ends because the network config module was working correctly in the first place. Something like mandriva's control panel along with network applet ported to debian would be just awesome for ubuntu. That would also make ubuntu's different desktops a little more consistent because they have the same system configurator that works a lot better than what each of the different ubuntu releases currently has in different DE configurator modules some of which don't work.

EDIT: Oh yeah i did try out mandriva's network applet rpms to see if i could install them in ubuntu. Whether using alien or using rpm to install them. They both complain about not having perl 5.8.8 which i have so idk what the hell it's really looking for. As far anything goes, it's possible to install but won't run. There's probably a lot more to do than i know about to make it run.

---


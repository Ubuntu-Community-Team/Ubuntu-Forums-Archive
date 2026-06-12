---
title: "Remote control Ubuntu with Teamviewer to send WoL packet over home network?"
date: 2016-11-23
forum: New to Ubuntu
---

### Post by shiznoroe88 on 2016-11-23
I have been trying for years to get a working WoL setup for my home network while i'm not home. I have gotten it to work intermittently a few times but have settled on wanting an always on device that uses very little power and has its own battery that I can remote control via Teamviewer or Chrome Remote Desktop and then send the WoL magic packet over the local network with said device. I have an old Nexus 4 and Nexus 5 that I wanted to use for this, but so far they can't be remote controlled the way I need. I can mirror the screens but they don't support remote input. I considered building a raspberry pi for this but it wouldn't have a battery.

Now I want to try installing Ubuntu onto a cheap chromebook and then use Teamviewer to remotely control it and send a WoL magic packet.

First, I need to know if this is even possible.

Second, I need to know if there is a utility/application for Ubuntu that can send WoL magic packets like there is for windows. Example [here]("http://www.nirsoft.net/utils/wake_on_lan.html") and [here]("http://magicpacket.free.fr/").

I would greatly appreciate tips and help.

---

### Post by DuckHook on 2016-11-23
Welcome to the forums, shiznoroe88,

What you are asking for is conceptually not difficult. However, you should familiarize yourself with the risks, because your stated strategy is fraught with pitfalls and could easily lead to you getting pwned. I am not trying to be elitest, really I&#8217;m not, but a lot of that risk is a legacy of your Windows mindset.

The biggest security hole in your strategy is Teamviewer. Remote desktop apps like these are notorious for account hijacking. There are Linux equivalents, but I would urge against using any of them. Instead, I would recommend an ssh server. This type of server means using the command line, but ssh *if properly configured* is *far* more secure than any remote desktop app, and magic packets can easily be sent from the command line too. Your security footprint would then be a tiny fraction of what it would otherwise be with a remote desktop.

All ssh traffic is encrypted. That&#8217;s how ssh works. You must set it up using encrypted keys, then disable password authentication altogether. Furthermore, a RPi or similar super-lightweight appliance can act as a very effective ssh server. You can even modify a router to can act as a ssh server, although the procedure to replace the original firmware with openwrt or dd-wrt is not trivial.

Unfortunately, I am on the road, responding to your thread from an Android device. This makes it very difficult for me to give details or directions. However, this general strategy is sound, and vastly more secure than the one your are proposing. Hopefully, other posters can fill you in on the details.

Hope this helps.

---

### Post by bearlake on 2016-11-23
+1 at post 2.

Setup my first ssh server this week with encrypted keys, disabled password authentication altogether.

Still running it behind the router with only port222 open in the firewall.

Was surprised on how easy it was and the amount of good info there was to be had.

Just need to open it up now to test it on the web.

---


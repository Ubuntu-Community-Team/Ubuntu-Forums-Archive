---
title: "Howto network manager applet (nm-applet) in xubuntu to switch wireless networks"
date: 2006-08-18
forum: Outdated Tutorials &amp; Tips
---

### Post by stani on 2006-08-18
First make sure you have a "System Tray" applet on of your panels otherwise the applet won't show up. Xubuntu provides one by default in the right part of the upper panel. So normally this should be ok.

Install the packages from the terminal:
```
sudo apt-get install network-manager network-manager-gnome
```

Go to Settings>Autostarted Applications:
- click "+ Add"
- type in these values:
  - name = "network applet"
  - command = "nm-applet --sm-disable &"

That is all.

---

Some people complain of having multiple nm-applets running... An easy trick is to remove the applet:
```
sudo apt-get remove network-manager-gnome
```

Quit all applications and reboot while saving your session.

To install again the applet, start at the beginning of this howto.

---

Good luck,

Stani

[http://www.stani.be](http://www.stani.be)
[http://pythonide.stani.be](http://pythonide.stani.be)

---

### Post by rlgoddard on 2006-08-19
Hi,

Your instructions worked like a charm!  Thanks!

The reason how I found out about the six instances was that I never had the system tray enabled until yesterday (didn't know about its existence until I was looking for help on how to get update manager to appear in the panel).  I now have just one instance, but I am still unable to configure using nm-applet.  It always shows two computers with a red "x".  I can go to System --> Networking and bring up the network configuration applet, and I still have network access, so it's no biggie.

Thanks and take care,
Russ

---

### Post by foxy123 on 2006-08-22
Is there any way to avoid entering WPA key every time I boot up my laptop?

---

### Post by dannyboy79 on 2006-08-22
I wouldn't suggest installing Gnome Apps in Xubuntu. The whole reason you are using Xubuntu is so that it's a LITE Distro. Well that's the reason I am using Xubuntu on my Pentium MMX 266mhz with 128mb RAM. Anyway, a much better choice is to install WIFI Radar. You can create tons of wireless profiles, they keep your security settings and everything! I thought I installed it from synaptic but I may have downloaded the .deb and installed it that way. Just goggle it and you'll find it!

---

### Post by foxy123 on 2006-08-22
> **dannyboy79 said:**
> I wouldn't suggest installing Gnome Apps in Xubuntu. The whole reason you are using Xubuntu is so that it's a LITE Distro. Well that's the reason I am using Xubuntu on my Pentium MMX 266mhz with 128mb RAM. Anyway, a much better choice is to install WIFI Radar. You can create tons of wireless profiles, they keep your security settings and everything! I thought I installed it from synaptic but I may have downloaded the .deb and installed it that way. Just goggle it and you'll find it!

I have never managed to make it work with my BCM43xx chip and ndiswrapper.

---

### Post by dannyboy79 on 2006-08-23
Well I don't use the ndiswrapper so I can't comment on that but I thought the purpose of it was only so that you can use a windows wireless adapter driver to get your wireless card to see networks, I didn't think it had anything to do with controlling what network you attach to or what security settings you use to attach to it. Why don't you use the ndiswrapper to get your wireless card to see your network and then install WIFI radar to control what different networks you attach to and what each security settings they have.

---

### Post by dom on 2006-09-20
> **rlgoddard said:**
> Hi,
<snip>
...
 I am still unable to configure using nm-applet.  It always shows two computers with a red "x".  I can go to System --> Networking and bring up the network configuration applet, and I still have network access, so it's no biggie.
...
,/snip>


I also have this issue, just installed network-manager and shows up, but it doesnt see the network interfaces working.

I installed it in the hope of managing various network profiles :(

---

### Post by dolphinsonar on 2006-09-21
Wifi Radar is in Synaptic Package Manager.

---

### Post by dom on 2006-09-22
> **dolphinsonar said:**
> Wifi Radar is in Synaptic Package Manager.

Cheers, Looking good ! Much better in fact! 

Any ideas on proxy setup. Some networks have 'em, some dont, I'd like to automate rather than having to re-set firefox each time i change network.

Any ideas on ethernet (or dual wifi/ethernet ) equivalents ?

---

### Post by Philip g on 2006-09-29
Thanks for the howto stani, worked a treat.

But I found in xubuntu 6.06.1 that the :-

Go to Settings>Sessions and Startup Settings>Advanced
 Enable "Launch Gnome services on startup"

bit was uneccessary.


In reply to dom with regard to network manager I found that the advise found in the dapper issues section of:-

[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

worked for me.  Essentially network manager didn't work, even on a fresh install until I 'hashed' out the reference to all interfaces except lo in the file:-

/etc/network/interfaces

hope this helps but please read the referenced doc as it contains more details of how to do this and why.

---

### Post by stani on 2006-09-29
> **Philip g said:**
> Thanks for the howto stani, worked a treat.

But I found in xubuntu 6.06.1 that the :-

Go to Settings>Sessions and Startup Settings>Advanced
 Enable "Launch Gnome services on startup"

bit was uneccessary.

Updated! Thanks, less is more.

---

### Post by pthivent on 2006-11-25
> **dom said:**
> Any ideas on proxy setup. Some networks have 'em, some dont, I'd like to automate rather than having to re-set firefox each time i change network.

Try Firefox's [SwitchProxy]("https://addons.mozilla.org/firefox/125/") plugin. Works like a charm for me.

Pascal

---

### Post by kristjans on 2007-01-27
I typed the startup program as you said, but I can't log in to Xubuntu anymore any other way than to the terminal... Please help me to remove it from the startup programs. :(

---

### Post by jsares on 2007-02-06
Works great for me!  Thanks!

---

### Post by arvvvs on 2007-04-13
I don't have internet connection, and requires internet:confused: 
wat to do

---

### Post by vjones777 on 2007-08-05
If you can get to the internet on another machine, one method is to download the repository there.  Get (download and burn, buy or borrow) a copy of an ubuntu live install CD and boot the PC from the CD.  Then use APTonCD to download the repository that has network manager.   I think the latest version of the live CD automounts the hard drive so you can save the download.  Take the downloaded images to your off-line machine.
You should then add the new iso files to your list of repositories.

---

### Post by GV1pJTHl on 2007-08-30
> **dannyboy79 said:**
> Anyway, a much better choice is to install WIFI Radar. You can create tons of wireless profiles, they keep your security settings and everything!
Nice, didn't know this existed...thanks for the heads up.

---

### Post by rekees on 2009-05-04
I cannot find the applet on the Add To Panel list, so I can't add it back to see it running. It's running, since I can't restart it from the command prompt. I am using Ubuntu 9.04, so I don't have System > Networking menu either. I'm a little lost right now, since I can't even know if I have connected to a network or not. 
Thanks much.

---

### Post by stani on 2009-05-08
Just press Alt+F2 and type "nm-applet". If you want to make this permanent, add it to system preferences > session.

---

### Post by rekees on 2009-05-11
I was able to install the applet, networking seems fine right now. But the applet doesn't show up in the list to add to the panel. So I don't have a problem starting the network applet, but the original icon and behavior - where at network startup a transparent object on the desktop would notify of connecting to a network - is gone. The icon looked like a set of growing bars.
Anyway, thank you much.

---


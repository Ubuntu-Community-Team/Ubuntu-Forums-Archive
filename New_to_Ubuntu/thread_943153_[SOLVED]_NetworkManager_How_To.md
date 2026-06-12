---
title: "[SOLVED] NetworkManager How To?"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by Tu1J4kXk8NUhMz on 2008-10-09
I feel like such a n00b asking this question (although I suppose I am...I installed Ubuntu only two weeks ago or so), but how do you work NetworkManager?

I'm running Ubuntu Studio on a Macbook Pro 15" (Core2Duo) and just installed the appropriate drivers for my Atheros wireless card. I ran Hardware Test, and it recognizes there is a wireless card there, so I assume that the drivers are appropriately installed and the card is properly communicating with my computer.

I've also installed NetworkManager to work with my wireless card (as for some reason it wasn't already installed). However, I have NO idea how to get the darn thing running! I searched for a file to run, tried to Add/Remove it (which tries to connect me to the internet...which I don't have)...I'm not sure where to go from here. Can someone point me in a good direction? A step-by-step on how to set NetworkManager up and make sure it loads every boot would be AWESOME! But any help would be greatly appreciated. Thanks!

---

### Post by anewguy on 2008-10-09
It's probably running but not showing on your bar.  Open a terminal window and type nm and press enter.

---

### Post by Tu1J4kXk8NUhMz on 2008-10-10
> **anewguy said:**
> It's probably running but not showing on your bar.  Open a terminal window and type nm and press enter.

I believe that's for Network Monitor, not Network Manager. Regardless, I tried this and it didn't show me anything. This is my problem...I don't know how to access the program to choose a wireless connection as I don't know where the actual program is. If someone could show me how to get Network Manager on the toolbar, that would be helpful too.

---

### Post by Keen101 on 2008-10-10
There should be a little icon on your upper panel. I am not familiar with how ubuntu studio is set up, but it should display next to your volume control in the notification area. If you don't have a notification area right click on your panel and add "notification area" to your panel.

If you do, or just did that and you still do not see it runing add this command to >System >Preferences >Sessions

command : "nm-applet --sm-disable"

reboot, and it should be next to your volume controll next time you start up.

or you could just try that command in a terminal if your in a hurry. But, if you add that to run on every session, then it will run everytime you boot up.

```
nm-applet --sm-disable
```

---

### Post by iponeverything on 2008-10-10
nm-applet will start the network manager

If you go to:

System -> Preferences -> Sessions

you can add it to start with the window manager with the command:

nm-applet --sm-disable

---

### Post by jemate18 on 2008-10-10
did you tried
type
```
network-admin
```

---

### Post by /////// on 2008-10-10
How did you go about installing network manager? If you typed sudo apt-get install network-manager, try this instead: sudo apt-get install network-manager-gnome. I find that this one actually installs the applet in the bar at the top. Furthurmore, if you cannot get network manager to work, you can always try WICD

---

### Post by Jackelope on 2008-10-10
I'm not sure if this is your issue, but if you simply can't see a wireless indicator this might help. Right click on your panel in any empty place, choose "add to panel," and in the window that opens find the applet called "notification area" and add it to the panel. When I first started I accidentally deleted mine and it took me days to figure out how to get it back (should have come here :)).

---

### Post by Tu1J4kXk8NUhMz on 2008-10-10
Okay...well I'm thoroughly confused. I did the "nm-applet" command in terminal, and it didn't work. Apparently, "network-manager" in APT-GET is different than "network-manager-gnome"...I assume the latter is specific to Gnome where the former is for Linux in general. Anyhow, I downloaded network-manager-gnome, then launched nm-applet. This brought up my Network Settings. However, I have no idea what I'm supposed to do with Network Settings in order to use wireless.

Also, I thought that the NetworkManager icon was similar to the cell phone kind of icon, with the four bars? At least, that's what they show on the internet. But the one that nm-applet brought up was two computers connection, much like the Windows network connection icon.

AND...why would I need to download network-manager-gnome to use nm-applet even though typing in nm-applet brought up a Network Settings box which I already had?

I hope these statements aren't read as me challenging what others have suggested...I'm not. I'm just quite confused.

---

### Post by Tu1J4kXk8NUhMz on 2008-10-10
> **Jackelope said:**
> I'm not sure if this is your issue, but if you simply can't see a wireless indicator this might help. Right click on your panel in any empty place, choose "add to panel," and in the window that opens find the applet called "notification area" and add it to the panel. When I first started I accidentally deleted mine and it took me days to figure out how to get it back (should have come here :)).

I have the Notification Area, it's just not showing anything...however, I've figured out how to get the Network Manager in there.

> **jemate18 said:**
> did you tried
type
```
network-admin
```

I did, and I may have figured out that Ubuntu Studio DOES actually have Network Manager...it just doesn't look how I thought it looked. That being said, I'm even more confused because this program doesn't seem to be showing how to initiate wireless.

The Network Manager icon shown in the notification bar has a Selection under the right-click menu which says "Show Wireless Connections." I click that and there are none. Ugh!

---

### Post by hyper_ch on 2008-10-10
I'd try WICD as network manager. Since I use it it has been a better experience --> you can find it on sourceforge an you'll just need to add a repo for it :)

---

### Post by Tu1J4kXk8NUhMz on 2008-10-10
> **hyper_ch said:**
> I'd try WICD as network manager. Since I use it it has been a better experience --> you can find it on sourceforge an you'll just need to add a repo for it :)

Okay, I took your advice and I'm happy I did. WICD is much more intuitive than Network Manager. HOWEVER, I am getting no wireless connections listed in the WICD window. In looking around a bit, I found that it's helpful to alter etc/network/interfaces to read only the following lines:

```
auto lo
iface lo inet loopback
```

So I altered that, then restarted and still nothing. I then ran iwconfig and the output showed this:

```
lo  no wireless detected
eth0   no wireless detected
```

I didn't write down the EXACT output, but this is pretty darn close. Also, I'm not sure what WPA Supplicant Driver to pick, or what to put in Wireless Interface (presently, this is empty). Thoughts? Suggestions? I am running a MacBook Pro, so I installed the ath9k driver...have not tried the Madwifi/ndiswrapper solution I've heard suggested. And for good reason, I don't have internet so I have no idea how to roll-back versions without using the web and Subversion (as outlined in [https://wiki.ubuntu.com/MacBookPro]("https://wiki.ubuntu.com/MacBookPro"))

I feel like Charlie Brown playing football with Lucy. I run at that ball as hard as I can, but Ubuntu keeps pulling it away...and I keep landing on my ***. ARRRGH!

---

### Post by hyper_ch on 2008-10-10
well, you can enter the SSID of the wireless also manualy (Network --> hidden network)... and for the WPA supplicant driver you only need it if you use WPA... if so, then just try each one out :)

---

### Post by Tu1J4kXk8NUhMz on 2008-10-10
> **hyper_ch said:**
> well, you can enter the SSID of the wireless also manualy (Network --> hidden network)... and for the WPA supplicant driver you only need it if you use WPA... if so, then just try each one out :)

Our network uses WPA (it's a college network), but I think my best bet is the Madwifi Supplicant. I just looked it up.

I will try the hidden network thing, and see if that works. Otherwise, I may wind up trying another driver solution. Is there some way to find out if my wireless card is actually communicating with my computer? In other words, how can I know that my driver solution actually worked? If it didn't, then I need to use ndiswrapper.

---

### Post by hyper_ch on 2008-10-10
run 
```

iwconfig

```

---

### Post by /////// on 2008-10-10
Looks like the drivers for your wireless card don't work properly or aren't there.

---

### Post by anewguy on 2008-10-10
I'm not familiar with the look of Ubuntu Studio, but if you have the top bar with network manager showing on it, then go to System/Administration/Network and see if wireless shows there,  If not, you still have a driver problem.  If it does show, be sure to set it to roaming mode.

I've been following your other post for wireless, and these things are all related to the driver.  You noted you had been trying to use ndiswrapper but hadn't gotten it installed yet.  Without it or the graphical front end ndisgtk, your drivers aren't being loaded.

So, first locate the Windows XP drivers for your wireless adapter. Download them and unpack them.  Then, following what is in the other post, install ndiswrapper (and ndisgtk if you can find it without a network connection).

When you have done that, post back to one of these threads - not both - and we'll go from there.

Dave :)

---

### Post by Tu1J4kXk8NUhMz on 2008-10-11
I don't have a clue if this counts as "SOLVED," so please enlighten me if it is. I tried ndiswrapper as described in this tutorial:

[https://help.ubuntu.com/community/MacBook]("https://help.ubuntu.com/community/MacBook")

I couldn't find anything regarding ndiswrapper in specific to my Macbook Pro, so I did my best. Anyhow, I follwed the instructions to a T as provided there, and.....NOTHING! No connection, and it's still not recognizing my wireless card.

So here's my solution: Ubuntu Studio, while a perfect Ubuntu "flavor" for me and my specialties, seems too young. I'm switching to plain ol' Ubuntu supplemented with the programs from Ubuntu Studio I use most often. HOPEFULLY I can get wireless working there. I fear the problem here is that Ubuntu Studio is stripped down (to allow for multimedia production programs) so much that it's incredibly difficult to configure wireless. Ubuntu Studio is so specific and stripped down, along with the fact that I'm running it on a Macbook Pro (which has it's own wireless issues with Ubuntu), it's too much for me to bother tackling.

So anyhow...Just wanted to pass that information on and let all who have helped me that it's greatly appreciated. I should have Ubuntu "vanilla" installed by tomorrow or so, and I'll post to let you all know how well wireless works. I'll let you know if I need anymore help. Thanks!

---

### Post by Tu1J4kXk8NUhMz on 2008-10-12
> **teamjh14 said:**
> So anyhow...Just wanted to pass that information on and let all who have helped me that it's greatly appreciated. I should have Ubuntu "vanilla" installed by tomorrow or so, and I'll post to let you all know how well wireless works. I'll let you know if I need anymore help. Thanks!

From reading, I've learned that a few other people have had issues with Ubuntu Studio 8.04 using wireless. No clue why, but glad I switched over! Got wireless working like a charm...used NDIS-gtk (that was very helpful) to implement the net5416.inf driver like the above tutorial said. HOWEVER, to anyone stumbling across this, you should know that the tutorial sites "ath0" as the Wireless Interface in WICD. That didn't work for me, so I used "wlan0" and that seems to work fine. Marking solved, as I need no more help. Thanks again!

---


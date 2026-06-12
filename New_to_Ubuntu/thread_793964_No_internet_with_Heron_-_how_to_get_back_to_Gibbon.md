---
title: "No internet with Heron - how to get back to Gibbon?"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by jnorris235 on 2008-05-14
I don't know why I believe them - hardy heron is ready!!
Yet another upgrade that has destroyed my wireless connection (Intel PRO/Wireless 3945ABG) and another card on my desktop.

Plug in the blue ethernet connection to the router and it just ignores it. And most solutions tell you to use apt-get!!!!!!!!!

Please - is there an easy way to undo the upgrade and hopefully get back to a working solution? I cant be doing with hours fiddling with things I have no knowledge of.

I have tried to convert people to Ubuntu but my heart isnt in it when upgrades go backwards on essential things like internet access. Thank god I still have XP - or hopefully Gutsy Gibbon!

---

### Post by Cypher on 2008-05-14
There is no downgrade path..your only recourse is a re-install to get Gusty back..

---

### Post by jnorris235 on 2008-05-14
Thanks for quick response!!

Pretty awful that they say 'Do you want to upgrade' without warning you that things don't work properly yet. I realise they can't work with everything - but if it worked in 7, why not 8? We used to moan about MS being late and then following with Update releases!! I wish Ubuntu did the same and only truly recommended it when major bugs (internet access) were fixed. Anyway - nowt to do with you - thanks for your help!

This, after three upgrades, every one a fight - has just pushed me back to XP and Google Docs etc.

---

### Post by cmnorton on 2008-05-14
Is NetworkManager running?

What is the content of your /etc/network/interfaces file? The problem might be a simple as re-setting that file. 

You are not alone in needing to re-install 7.10, but before you do it, you could look to see what is making you not connect.

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0

---

### Post by Cypher on 2008-05-14
But before you go down that path..did you have to do anything extra to get your wireless working in Gutsy, or did it work right out of the box?

---

### Post by takuhii on 2008-05-14
When you upgrade to Hardy Heron, for some reason, it locks your Network settings. Go to Network Settings and there will be a button that says Unlock, this might be preventing your cards from working, as it effectively switches off networking, you should only have to do this once...

---

### Post by jnorris235 on 2008-05-15
Well this is just crazy - talk about shooting yourself in the foot! There are hundreds of people having this problem.

Takuhii - have to do that everytime!
Cypher - I think it worked fine.
cmnorton - I don't seem to have Network manager. My /etc/network/interfaces file has only two lines:
auto lo
iface lo inet loopback

If this is the problem (cos it doesn't mention eth1) please tell me exactly what to do!! Meanwhile I'll go back and try adding 'auto eth1'
Thank you all, by the way.

I understand that Hardy is using a new Intel driver. Fine! It's there - but it is way beyond me to find out if Hardy is using it.
Presumably not!

I don't know what files to check!

iwlist scan - shows eth1 with all sorts of stuff, whereas the other ones (like eth0) say they cant be scanned. So I'm assuming it's trying!

I created a file in etc/modprobe.d/ called iwl3945 like others have.
It has just the line:
alias iwl3945 options iwl3945 disable_hw_scan=1 hwcrypto=1

I tried: sudo aptitude remove linux-image-2.6.24-12-386
It couldn't find the thing - so i guess that was good.

I tried dmesg - and there was no killswitch mentioned.

I can't tell you how angry I am that they release a thing like this!!!!! Bang goes any business I was trying to run online! Beware any Noobs moving from Windows - it aint ready!!

---

### Post by Ayuthia on 2008-05-15
> **jnorris235 said:**
> Well this is just crazy - talk about shooting yourself in the foot! There are hundreds of people having this problem.

Takuhii - have to do that everytime!
Cypher - I think it worked fine.
cmnorton - I don't seem to have Network manager. My /etc/network/interfaces file has only two lines:
auto lo
iface lo inet loopback

If this is the problem (cos it doesn't mention eth1) please tell me exactly what to do!! Meanwhile I'll go back and try adding 'auto eth1'
Thank you all, by the way.

I understand that Hardy is using a new Intel driver. Fine! It's there - but it is way beyond me to find out if Hardy is using it.
Presumably not!

I don't know what files to check!

iwlist scan - shows eth1 with all sorts of stuff, whereas the other ones (like eth0) say they cant be scanned. So I'm assuming it's trying!

I created a file in etc/modprobe.d/ called iwl3945 like others have.
It has just the line:
alias iwl3945 options iwl3945 disable_hw_scan=1 hwcrypto=1

I tried: sudo aptitude remove linux-image-2.6.24-12-386
It couldn't find the thing - so i guess that was good.

I tried dmesg - and there was no killswitch mentioned.

I can't tell you how angry I am that they release a thing like this!!!!! Bang goes any business I was trying to run online! Beware any Noobs moving from Windows - it aint ready!!

You might be able to use the Gutsy kernel.  If you go into /boot/grub/menu.lst you should be able to find the old kernel there (should start with 2.6.22).  You can comment out (place a # at the begging of the line) the Hardy version (after you make sure that this works).  To edit the file:
```
gksu gedit /boot/grub/menu.lst
```
If you are only using Ubuntu on this computer, when you start up your computer you will have to press ESC before the timer runs out so that you can see the list of menu items.  From there select the 2.6.22 kernel.

Hope that helps.

---

### Post by stchman on 2008-05-15
> **jnorris235 said:**
> I don't know why I believe them - hardy heron is ready!!
Yet another upgrade that has destroyed my wireless connection (Intel PRO/Wireless 3945ABG) and another card on my desktop.

Plug in the blue ethernet connection to the router and it just ignores it. And most solutions tell you to use apt-get!!!!!!!!!

Please - is there an easy way to undo the upgrade and hopefully get back to a working solution? I cant be doing with hours fiddling with things I have no knowledge of.

I have tried to convert people to Ubuntu but my heart isnt in it when upgrades go backwards on essential things like internet access. Thank god I still have XP - or hopefully Gutsy Gibbon!

There is a new 3945 driver for Hardy in the restricted driver manager.

You will need to go and hook your laptop up to a wired connection and do a:

```
sudo apt-get update
```

After that you can enable the ipw3945 driver.  I had to do the same for my ATI card.

Trust me the 3945 card works with Ubuntu.

---

### Post by Tatty on 2008-05-15
> **takuhii said:**
> When you upgrade to Hardy Heron, for some reason, it locks your Network settings. Go to Network Settings and there will be a button that says Unlock, this might be preventing your cards from working, as it effectively switches off networking, you should only have to do this once...

The "Unlock" button is part of the new policykit software which is included in hardy heron.

It allows you to give users specific rights to certain parts of your system which you would previously have had to have full sudo rights to change.

It does not switch off networking, its simply prevents you from altering the network settings unless you are given the rights to do so.

These settings can be changed in system->administration->authorizations

---

### Post by bmac on 2008-05-15
Obviously, threating to go back to M$ worked again!!!
"My heart isn't in it"

Maybe that could be said of a lot of things. The woe is me and I'm going back to M$ post, again has resulted in a flurry of activity from the forum. 

No one can fault this forum for not endeavoring to assist everyone. Especially those who demand attention by threating to leave the Ubuntu community.... We really need to quit patronizing individuals who display this type of behavior. Continuing to condone this behavior simply increases it and frustrates many who assist in the forum. Maybe it would help if we expressed our dissatisfaction with their post each time an individual posts a similar statement. I do understand the frustrations and have had a few of my own. However, I've never threaten the forum with returning to M$ just to get attention. Similar to others I endeavor to solve the problem and then if necessary respectfully ask for assistance. What a novel concept....:sad:

---

### Post by cmnorton on 2008-05-16
> **Cypher said:**
> But before you go down that path..did you have to do anything extra to get your wireless working in Gutsy, or did it work right out of the box?

What I found with a full install of 8.04 was KNetworkManager could not handle my network coming in from a USB docking station. I entered a bug. 7.10 knows to fail over from usb0 to eth1; 8.04 could not. I did try using a straight ethernet cable bypassing the USB, and that worked. I did not see any unlock button, but then my upgrade failed.

---

### Post by jnorris235 on 2008-05-16
bmac: I know I was throwing my toys out of the pram by mentioning M$. However the threat was quite obviously NOT at the really helpful people who willingly try to help people like me. I have been careful to say thank you. I think I've been respectful, too.

I just hope that the guys responsible for this error get to hear of it, but they don't seem to, or there would be a definitive answer. The number of endless problems that require you and others to reply to thread after thread after repeated thread! Whoever wrote this bit of code - sort it! and save everyone a whole load of time. Otherwise Ubuntu still belongs to the nerds! Hence my - not a threat - need to return to M$ simply because I actually need the internet!

Note that my problem is not solved. The new driver is there - but how to make Hardy use it?

stchman: I used to have a line on Preferences about restricted drivers - but that entry has disappeared.

The clue might be in your line: After that you can enable the ipw3945 driver.
How do you enable that driver - that is my problem!

---


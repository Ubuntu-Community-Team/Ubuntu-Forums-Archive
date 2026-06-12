---
title: "no wifi after 9:00pm?!? WTF?!?!"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by minibeardeath on 2008-05-07
currently i am running gutsy, and everything works great (except no dvd, but im working on that as i type). there is one bizarre problem tho. as mentioned in the title of this post, my wireless card does not work after about 8:50 - 9:00, unless i move my pc into my mom's office where the router is located. the *only* thing that occurs at 9:00 every night is that my brother goes to bad, and stops using the internet on my mom's computer (but leaves the computer on). the router is on 24/7 and it works if i am in the same room as the router. this is really starting to bug the hell out of me because i must move my whole computer and screen into my mom's office (on the other side of the house) if i want to do anything such as updates or downloading vidoes. somebody please help! 
(this has gotten to the point where i am seriously reconsidering XP (i may have had random shut-downs, but at least all of my hardware worked when i told it to)):mad::mad::mad:

---

### Post by llamakc on 2008-05-07
Check the router (if you have permission) for any restrictions set. Test access to the net by trying it wired after 9 too.

---

### Post by toddward on 2008-05-07
Agreed, that's probably your best bet.  You don't think your brother would screw with you, do you?

---

### Post by minibeardeath on 2008-05-07
there are no restrictions on the router (im the IT guy in the house so i basicly have free range of the house electronics). as far as my brother goes, i found out last night that he has not been allowed on the internet for the past three nights because he is grounded. the thing that makes this weird is that my wireless works perfectly fine when my computer is in the room with the computer, and it works flawlessly during the rest of the day. 

one possibility that my dad wondered about is could someone be hi-jacking our wirelss and causing me to lose connection? (i think that this is very unlikely as we have WPA-PSK enabled, and, although it is not possible to connect both mine and my dad's wifi at the same time, it is always the second person connecting who experiences loss of connection.)

so any other suggestions?

---

### Post by dtrot55 on 2008-05-07
I'm just curious...i had issues with my wireless router at one point.  Ruled it out as an environmental thing...wireless phones working on 2.4ghz also cable modem to close.  I went in and change the frequency my wireless router broadcasted at and it fixed it...dont know if you could try that?  This was all in windows...so i dont know how different the drivers would be for you.  Also it could be that your ISP is doing some kind of maintaince at that time? or has this been going on ever since you installed Ubuntu?

---

### Post by dwhitney67 on 2008-05-07
Your father may be a little off-base, but nevertheless it possible that someone in the vicinity of your home is activating their wireless router and the signal of this router is interfering with yours.  I would recommend that you change the channel number that your wireless router uses to broadcast to see if that helps.

---

### Post by Vegadark on 2008-05-07
I agree with the last post. It sounds like interference from another wireless source. That makes perfect sense why you can access it when you are right next to it, but not from farther away. I would scan wireless networks when its working fine, write down the networks found and then do another scan when the problem occurs and compare to see if a new one always comes on at that time. It could also be several other things, depending on the radio frequency being used, like wireless headphones, cordless phone, wireless video (security maybe?), among other things.

---

### Post by minibeardeath on 2008-05-08
i will try that. the problem has only occured since using ubuntu. as far as i can tell its not the ISP (because i can use the hard line perfectly fine right now). tonight i managed to go until 9:40 so im thinking that the environmental interference is sounding like the most likely cause.

---

### Post by minibeardeath on 2008-05-08
> **Vegadark said:**
> I agree with the last post. It sounds like interference from another wireless source. That makes perfect sense why you can access it when you are right next to it, but not from farther away. I would scan wireless networks when its working fine, write down the networks found and then do another scan when the problem occurs and compare to see if a new one always comes on at that time. It could also be several other things, depending on the radio frequency being used, like wireless headphones, cordless phone, wireless video (security maybe?), among other things.

just checked, and the only networks that are deteced are the same two as always.

also just changed the wireless channel and still no signal

---

### Post by minibeardeath on 2008-05-12
so ive let this go for a couple of days so that i might be able to observe any other patterns in the failure. here is what i have found:
1) 10-15 min after i start any app w/ audio the wifi stops working until i do a full restart of the computer. at first i thought that it was my external HDD spinning that was the problem, but watching a video on the internet also causes the wifi to not work after 10-15 min.
2) the no wifi after 9:00pm usually only occurs on fri and sat night (sun i can usually go until midnight or later w/ full access)
3) i know for a fact that it is not due to the actions of any of my family members because they would not know how to make something like this happen.

any suggestions on a fix. i did so looking and this seems like a some what uncommon situation. also, is the idea of the sound card interfereing w/ the wifi card even possible (the sound card is in the PCI slot directly above the wireless card, but i dont know if that would change anything). please help. this is starting to get more than a little annoyning.

---

### Post by raydeen on 2008-05-12
Ok, probably a stupid question here, but are you sure you're connecting to the wireless unit in your house? I read an article a while ago where a fellow thought he was connecting to his router but in actuality had been connecting to a neighbor's router for a year or two. Both routers were the same make and model and both still had the default username/password for router access. He only figured it out when he physically connected to the router (he had done the router setup wirelessly on his first connect and for some reason had picked up his neighbor's instead of his). Try changing the SSID and see if you're actually connecting to that router. Maybe a neighbor turns theirs off after 9.

---

### Post by minibeardeath on 2008-05-12
thats a valid question. 

yes i know that its mine because ours does not use the default password, and i am able to log on usually after i restart my computer even if its after 9. last night, i noticed that i was getting some activity in the log related to the wifi. here is what the log said:
```
May 11 23:56:04 patrick-desktop dhclient: No DHCPOFFERS received.
May 11 23:56:04 patrick-desktop dhclient: No working leases in persistent database - sleeping.
May 11 23:56:04 patrick-desktop avahi-autoipd(wmaster0)[10778]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
May 11 23:56:04 patrick-desktop avahi-autoipd(wmaster0)[10778]: Successfully called chroot().
May 11 23:56:04 patrick-desktop avahi-autoipd(wmaster0)[10778]: Successfully dropped root privileges.
May 11 23:56:04 patrick-desktop avahi-autoipd(wmaster0)[10778]: Interface not suitable.
May 11 23:58:22 patrick-desktop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
May 11 23:58:30 patrick-desktop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
May 11 23:58:41 patrick-desktop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
May 11 23:58:47 patrick-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
May 11 23:58:51 patrick-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
May 11 23:58:52 patrick-desktop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 1
May 11 23:58:53 patrick-desktop dhclient: No DHCPOFFERS received.
May 11 23:58:53 patrick-desktop dhclient: No working leases in persistent database - sleeping.
May 11 23:58:57 patrick-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
May 11 23:59:05 patrick-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
May 11 23:59:18 patrick-desktop dhclient: No DHCPOFFERS received.
May 11 23:59:18 patrick-desktop dhclient: No working leases in persistent database - sleeping.
May 11 23:59:35 patrick-desktop dhclient: DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 3
May 11 23:59:38 patrick-desktop dhclient: DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 4
May 11 23:59:41 patrick-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
May 11 23:59:42 patrick-desktop dhclient: DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 6
May 11 23:59:46 patrick-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May 11 23:59:48 patrick-desktop dhclient: DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 14
May 11 23:59:53 patrick-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
```
sequence of entries is repeated several dozen times including @ start up & when i have no internet troubles & when i do have the troubles so i dont know if its really relevant. thanks for all the support so far ;)

---

### Post by minibeardeath on 2008-05-15
so ive established that it is entierly a problem w/ my computer because the dropped signals always occur when i am listening to my music.

---

### Post by minibeardeath on 2008-05-18
Problem solved!!! my new wireless mouse was causing the interference.

---

### Post by SIXAXIS on 2008-05-19
That makes sense, but do you start using the mouse after 9?

---

### Post by minibeardeath on 2008-05-19
thats the weird thing. i use the mouse all the time. over the past couple of days, the signal loss issue had gotten much worse and more sporadic (esp once i started using torrent). now that i am not using that mouse, i have perfect connection except for the whole 9 o'clock issue, but i can solve that by simply restarting the computer at 9.

the reason that it took so long to recognize that the mouse was the problem was that i got the mouse literally the same day as i switched from XP to Linux (the switch and the new mouse were coincidence). i had never had the problem with my old wireless mouse/keyboard set, but i never made the connection because i just assumed that it was an issue with the hardware compatibility under linux, so i was sort of right. anyways, thanks for the help everybody

---


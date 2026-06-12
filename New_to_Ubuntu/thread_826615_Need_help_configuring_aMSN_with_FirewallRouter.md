---
title: "Need help configuring aMSN with Firewall/Router"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by Linux_noob616 on 2008-06-12
Hello, So i have a problem. Fire transfers and webcams are blocked/slow.

looked for why, and low and behold i'm firewalled and my router is messing with me.

Configured my router (or so i thought...) and turned off the firewall Ubuntu recommended cause im not sure how to configure it (help there would be nice..)

All i got was slow webcam and same file transfers...

Can anyone help me?

---

### Post by hyper_ch on 2008-06-12
well, if it works then it's not a routing/firewall issue but rather a connectivity one... you'll have to check with your isp and the isp of the other person... maybe the one sending to you runs also torrents that use a lot of upload....

---

### Post by Kronie on 2008-06-12
yup i have exactly the same problem.. my down/up speed (in kilobytes) 320/60, and the downloads in pidgin with msn account are as if i were on 52k dialup.. i get full speed when im downloading with firefox or downloading/uploading with bittorrent.. the guy who i usually do the transfers has 1 megabyte down and 90 kilobyte up speed... the transfer can go highest of 13 kB/s.. most of the time it stays on 5-7... didnt try the webcam yet tho. and im using linksys WRK54G router

---

### Post by Linux_noob616 on 2008-06-12
thats just it, in pidgin it works fine (haven't used webcam though) but in aMSN it doesn't =/

---

### Post by Kronie on 2008-06-12
dude, mind helping me figuring out if aMSSN worx for me or not? all my buddies are offline T_T i just need to test the down/up speed...

---

### Post by fesk on 2008-06-20
i have this problem too. when i try to upload files to someone i have a stabile transfer at 5-6 kbs. i have forwarder my ports and im not behinde a firewall. can someone please help ? i really like amsn and i cant switch to pidgin ..


-fesk

---

### Post by waapwoop1 on 2008-06-29
Any tips for this. I have this problem.

I am assuming i go into my modem and the NAT settings and do some port forwarding. Anyone know exactly waht i need to do. I am using amsn and my webcam doesn't work in it because i am firewalled.
The webcam works in general though.

---

### Post by Claus7 on 2008-06-30
Hello,

this is what you have to do:
[http://ubuntuforums.org/showthread.php?t=472123](http://ubuntuforums.org/showthread.php?t=472123)

except that you have to do it for port 6881 (If you check also in preferences of amsn you will see that this is the port that amsn uses).

You might also have to open : TCP 443 and TCP 1863.

Regards!

---

### Post by tanya1979 on 2008-08-06
hi. im having a problem connecting with amsn. It says that I am firewalled or behind a router. I dont have a firewall program on my pc and i don't have a router.I have a digital broadband modem which runs my internet and my home phone. Does anyone have any clues to what is going on here? thanks

---

### Post by Claus7 on 2008-08-07
Hello,

Ubuntu by default has closed ports for securith reasons. With firestarter you would be able to configure them. 
Just look at this :
[http://ubuntuforums.org/showthread.php?p=5542211#post5542211](http://ubuntuforums.org/showthread.php?p=5542211#post5542211)

and omit the part about the router.

Now, there was a debate in the forums, whether firestarter is itself a firewall or not. I would propose you to use it and see if you can solve your problem. 

Regards!

---


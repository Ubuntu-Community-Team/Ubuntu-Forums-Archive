---
title: "[SOLVED] Quick question about samba speed o.O"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by Ryuki_NdranC on 2008-05-10
I just successfully installed samba in my 2 home laptops (both with ubuntu hard... i know,i know i didn't need samba but i JUST learn that) anyway all fine except the transfer speed is 55 kbps :S it takes 4 hours to transfer 700 mb. As far as i can remember in windows was a but load more faster (2 mbps if i remember correctly).

My questions are:

Bad samba config??? 
Bad wireless driver (BCM43XX with b43-fwcutter)???
Just bad samba (using nfs should work great)???
yes in windows it's better and i can't do a thing under linux???
god hates me???

:) I can't seem to find any speed related post around so i was hopping some answers :) thx in advance

---

### Post by DrPppr242 on 2008-05-10
Samba shouldn't affect the speed at all, it's just the mechanism used to share and download, however that's a very very slow speed for an internal network, the only thing I can think is if your using fwcutter, it seems like that limits the wireless speeds to the 802.11b protocol, which might be why it's faster in windows.

---

### Post by Ryuki_NdranC on 2008-05-10
> **DrPppr242 said:**
> Samba shouldn't affect the speed at all, it's just the mechanism used to share and download, however that's a very very slow speed for an internal network, the only thing I can think is if your using fwcutter, it seems like that limits the wireless speeds to the 802.11b protocol, which might be why it's faster in windows.

At least i know for sure now that i'm not imagining things :)

Do you think installing ndiswrapper (in the case b43-fwcutter is the culprit) should improve the speed? I hate ndiswrapper in hardy... Way too messy to install :s

Thanks for the answer ^^

---

### Post by Ryuki_NdranC on 2008-05-11
./bump :(

No one else has anything to say? Maybe about your own experience?

---

### Post by freebeer on 2008-05-11
I've never tried Samba over a wireless connection, but I do know that over wired connection it's speed is just fine.  It's comparable to copying to a Win2003 Server, as far as I can tell.

I suspect there's a issue with the wireless connection itself as Samba is just simulating Window's networking protocol.  It's not controlling the wireless connection per se.

---

### Post by Ryuki_NdranC on 2008-05-12
> **freebeer said:**
> I've never tried Samba over a wireless connection, but I do know that over wired connection it's speed is just fine.  It's comparable to copying to a Win2003 Server, as far as I can tell.

I suspect there's a issue with the wireless connection itself as Samba is just simulating Window's networking protocol.  It's not controlling the wireless connection per se.

I actually installed samba because i didn't know it was made thinking in mix networks with windows stations. I just have 3 pcs with linux :P

Problem is the 3 of them have b43-fwcutter. But so far in download speed from the internet is really fast, not to say maximum potential.

Thats why i still have some doubts about if ndiswrapper will fix my problem. Besides ndiswrapper under hardy is kind of a pain in the ***. <_<

Is there a difference between samba a nfs? i have a printer in the net, i wanna share that one too...

Thanks for your answer ^^

---

### Post by freebeer on 2008-05-12
So all the machines are wireless?  I suspect, then, that's your issue.  The max theoretical throughput of a wireless router over the wireless channel is what? 56mbits?  That 56 needs to be shared among all the connected machines (and don't forget the overhead).  So a copy from one machine to the other has a theoretical max of 28 mbits.  Add a third device...

It's also quite possible that your Samba isn't fully set up yet.  Here's where my understanding of exactly what's going on with the Windows protocol is a little unclear.  If Samba doesn't have names to work with (WINS Server?) there's a lot more overhead involved in routing the packets as it may have to use broadcast mode (meaning speaking to everyone) and since you only have the one wireless pipe... 

I've never set up NFS, but I suspect that it'll be faster and probably easier to maintain if you're only speaking to other Linux boxes.  I don't anticipate network printers will be a problem (but again, if it's wireless, too, you've got a lot of traffic sharing a single pipe).  I'd go wired wherever possible (wired gets 100mbits (possibly 1000 if you have a gigabit router and card) and it doesn't have to share that leg).

---

### Post by Ryuki_NdranC on 2008-05-12
> **freebeer said:**
> So all the machines are wireless?  I suspect, then, that's your issue.  The max theoretical throughput of a wireless router over the wireless channel is what? 56mbits?  That 56 needs to be shared among all the connected machines (and don't forget the overhead).  So a copy from one machine to the other has a theoretical max of 28 mbits.  Add a third device...

It's also quite possible that your Samba isn't fully set up yet.  Here's where my understanding of exactly what's going on with the Windows protocol is a little unclear.  If Samba doesn't have names to work with (WINS Server?) there's a lot more overhead involved in routing the packets as it may have to use broadcast mode (meaning speaking to everyone) and since you only have the one wireless pipe... 

I've never set up NFS, but I suspect that it'll be faster and probably easier to maintain if you're only speaking to other Linux boxes.  I don't anticipate network printers will be a problem (but again, if it's wireless, too, you've got a lot of traffic sharing a single pipe).  I'd go wired wherever possible (wired gets 100mbits (possibly 1000 if you have a gigabit router and card) and it doesn't have to share that leg).

Interesting... I never had the chance to try when both laptops had windows xp, but i guess your are right. It sound logical to me. so far i have winxs server activated in samba, but i just followed a HOWTO from this forum. For me it seems less likely that ndiswrapper is gonna improve somehow my speed. 

This NFS is like samba? I just configure it and access to my network places via workgroups, etc??? and It allows me to use share printers?

P.S: the 3 laptop doesn't come that much, so i guess you can count it out of the picture :)

I'm really appreciated with your answers, can't wait to get home and investigate a over google about linux share system. Can't believe i wasted all my life under the wrong SO.

---

### Post by freebeer on 2008-05-13
Hopefully my answers are at least close to the mark.  :tongue:  I don't profess to be an expert, or even deeply experienced... just trying to help out a little.  The folks here on this forum will chime in, I'm sure, if I'm too far off the mark.  (And that way I get to learn one more piece of the puzzle!)  :D

From what little reading I've done on NFS, it's a fully capable network sharing system.  I suspect that it doesn't work off the "workgroups" concept as that is more of a Windows creation.  Unix/Linux has always supported multi-user access and the file permission system reflects that (user,groups,other file permissions) out of the box.  Windows had to create the concept of workgroups because they simply didn't have a file system/privilege system in place that supported it until NTFS.

---

### Post by Nythain on 2008-05-13
here's my advice... switch to nfs... if there's no windows pc's on the network, there's no real need for samba.

in my experience, samba + wireless = bad mojo... though my experience is limited, but it sucked...
i ultimately had to throw the server onto a wired connection, and that onlyhalf helped remey the problem, as the wireless connections were still recieving only a fraction of the speed they should have.

drives and wireless and all that jazz aside, another common culprit could be you smb.conf itself... i noticed an over cluttered and default configured conf file can wreak havok on a network :)

but in all reality, you would be much better off just switching to NFS instead of trying to continuously troubleshoot samba

---

### Post by Ryuki_NdranC on 2008-05-13
I switched to NFS and i have to say... WOW

I'm now transferring (via wireless... both laptops still) 200 kbps to 300 kbps... I know... still slow but at least compared with 30 kbps from before its heaven for me. I don't think i'm gonna be able to use a wired network because all my pcs are laptops and i keep moving them a lot. Besides if my sister sees a net cable laing around by the house, i'm gonna be a dead man.

I like a lot NFS stile, it works just like a pendrive :)

I notice that NFS its just for file share. I notice also that CUPs has some kind of network server. My question is... if i want to connect my printer to the net i still need samba? can i use NFS? or i don't need ether just use my "CUPs" weird server?

P.S: Seriously i can't wait and learn shell scripting and stuff. I'm gonna be sooo happy when i make my own conkyrc file and my own scripts :)

---

### Post by freebeer on 2008-05-13
Good stuff.  Glad you got it working.

CUPS should be sufficient for your printing needs.  Give it a try. :D

---


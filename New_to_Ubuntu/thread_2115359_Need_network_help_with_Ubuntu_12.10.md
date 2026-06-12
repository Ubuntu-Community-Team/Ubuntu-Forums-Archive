---
title: "Need network help with Ubuntu 12.10"
date: 2013-02-12
forum: New to Ubuntu
---

### Post by punomatic on 2013-02-12
I have searched the forum and the internet and have not found an answer to my specific problem. I apologize if this is a common question that has been answered already. 

Hi, ):P I'm a new (as of a week ago) Ubuntu user. Have played with Linux a tiny bit in the past, but consider me a total newcomer.  Please be gentle.

I am running Ubuntu 12.10 on a Toshiba Satellite Laptop.  Everything seems really easy to work, except networking. I have a home network with 2 Win7 pcs and a MacBook.  I used Samba to set up my Ubuntu box for networking. Here is what I have now. 

[LIST=1]
[*]I can access all shared files on the Ubuntu box from both of the Win7 pcs.
[*]I cannot even see the Win7 pcs from the Ubuntu box. I get as far as home/network/windows network/workgroup, but then I get the following message: Unable to mount location. Failed to retrieve share list from server.
[*]I have run smbtree. It shows all of the computers on the network.
[*]I can ping the Win7 pcs. (I haven't tried the MacBook. That's my wife's computer, and she could care less about networking, as long as the internet works.)
[*]I have scoured the internet and tried numerous suggestions, but the result is always the same: Ubuntu box can't see Win7 pcs; Win7 pcs can open shared files in Ubuntu box.
[/LIST]
What am I doing wrong/overlooking?  File sharing is turned on on the PCs, and they communicate fine with each other. All computers are in the same workgroup and on the same LAN. 



HELP!

---

### Post by Cheesemill on 2013-02-12
Are you using a workgroup or a homegroup for file sharing on your Windows machines?

Homegroups will only work with Windows 7 or 8, they aren't compatible with Linux (or earlier versions of Windows).

---

### Post by punomatic on 2013-02-12
Addendum: 

I started the MacBook and found that I am able to ping the Ubuntu box from the Mac and vice versa. But I still can't see any computers on the network from the Ubuntu box.

---

### Post by punomatic on 2013-02-12
> **Cheesemill said:**
> Are you using a workgroup or a homegroup for file sharing on your Windows machines?

Homegroups will only work with Windows 7 or 8, they aren't compatible with Linux (or earlier versions of Windows).
I have a homegroup set up, but I thought I also had a workgroup. Now that I think about it, are they mutually exclusive? I'll check on that. Thanks.

---

### Post by punomatic on 2013-02-12
> **punomatic said:**
> I have a homegroup set up, but I thought I also had a workgroup. Now that I think about it, are they mutually exclusive? I'll check on that. Thanks.
Yes, I have a homegroup set up, but I also have a workgroup. In order to be sure the workgroup was communicating, I started a new workgroup and reset all computers to that workgroup.  I ran smbtree and found that all computers show up in the workgroup. Unfortunately, I still can't see any computers in the LULU (my new workgroup name) folder when I access it through  network/windows network/workgroup/LULU .  

I can get as far as seeing the LULU folder, but when I try to  open it, my old friend "Unable to mount location. Failed to retrieve share list from server" shows up. I also learned that the MacBook shows up in the network folder on the Ubuntu box, and I can access the files in the drop box.  Am I correct in  assuming that the Win7 computers have a switch turned on or off that is  preventing them from showing up? 

Earlier today, I removed one of the Win7 pcs from the homegroup, but it still didn't show up on the Ubuntu pc. Good thing I love a puzzle!!:D

---


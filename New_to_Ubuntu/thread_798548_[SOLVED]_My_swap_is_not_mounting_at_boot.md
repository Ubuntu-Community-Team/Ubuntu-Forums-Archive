---
title: "[SOLVED] My swap is not mounting at boot"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by patrickaupperle on 2008-05-18
I have a swap partition, but it is not mounting as swap at boot.
I can swapon it with gparted.

---

### Post by overdrank on 2008-05-18
> **patrickaupperle said:**
> I have a swap partition, but it is not mounting as swap at boot.
I can swapon it with gparted.

HI and this link has helped me with swap issues in the past
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by Gone fishing on 2008-05-18
So if you do swapon -s in a terminal it gives you blanks - mine looks like 

> /dev/sdb7           partition	1020088	0	-1   

because I'm not using any of the swap space, in fact I'm only using less than half of the RAM I have installed which is only 1Gig. If it does give you blanks then it must be wrong in fstab file mine looks like

> # /dev/sdb7
UUID=43c3e514-9499-4eb0-88e7-800fd31ff69a  none           swap         sw                          0  0  


On a PC I cloned the swap refused to mount until I changed the entry to:


> 
 /dev/sdb7 none           swap         sw                          0  0  


I must admit I wonder if Ubuntu running on a Gig or RAM or more even needs a SWAP partition

---

### Post by patrickaupperle on 2008-05-18
> **Gone fishing said:**
> So if you do swapon -s in a terminal it gives you blanks - mine looks like 



because I'm not using any of the swap space, in fact I'm only using less than half of the RAM I have installed which is only 1Gig. If it does give you blanks then it must be wrong in fstab file mine looks like



On a PC I cloned the swap refused to mount until I changed the entry to:




I must admit I wonder if Ubuntu running on a Gig or RAM or more even needs a SWAP partition

I think my fstab is incorrect.

---

### Post by Gone fishing on 2008-05-18
Well I think if you opened your fstab file for modification (might be wise to make a back up as well) by opening a terminal and entering 

$ gksu gedit /etc/fstab

them modifying the swap section to look like 

/dev/sda5  none           swap         sw         0  0  

it should work

---

### Post by patrickaupperle on 2008-05-18
> **Gone fishing said:**
> Well I think if you opened your fstab file for modification (might be wise to make a back up as well) by opening a terminal and entering 

$ gksu gedit /etc/fstab

them modifying the swap section to look like 

/dev/sda5  none           swap         sw         0  0  

it should work

It worked.

---

### Post by Gone fishing on 2008-05-18
> It worked. 

Good, however, it does make me wonder if you need a swap partition if you have a Gig or more of RAM - I note your swap partition is 2 Gig I guess thats too big (not that it matters just a little wasted space)

---

### Post by patrickaupperle on 2008-05-25
most people say to make your swap twice your ram. I have heard that I should follow this as long as the combined is not over 4 gigs. This is what I am going to follow, at least untill I get a 64 bit processor.

---


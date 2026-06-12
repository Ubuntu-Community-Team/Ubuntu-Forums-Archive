---
title: "ThinkPad T60 dual boot partition question."
date: 2008-05-24
forum: New to Ubuntu
---

### Post by archer6 on 2008-05-24
Two questions please:

I want to install Ubuntu 8.04 on my ThinkPad T60 Win XP Pro Laptop as a dual boot config with XP Pro. My hard drive is 100G in size. There is a "hidden" rescue partition on my hard drive that is there to restore Win XP after a crash. This is in lieu of restore disks. 

1) How do I partition the hard drive without writing over and losing this rescue partition? 

2) Of the 100GB capacity I have 80GB free space. What would be a good size for the Ubuntu Partition. I'm thinking about 40GB. 

Thanks!

---

### Post by lud666 on 2008-05-24
If you are installing from a Live CD you should easily be able to resize your Windows partition (without affecting any other partitions) using the guided option like this: [IMG]https://help.ubuntu.com/community/GraphicalInstall?action=AttachFile&do=get&target=6.png[/IMG]

However, if you choose the manual option you will have more control. You will be able to see all the partitions on your hard drive and tell the installer exactly how to change them. This is probably your best option.

Check out [THIS]("https://help.ubuntu.com/community/forum/installation/Partitioning") and [THIS]("https://help.ubuntu.com/community/GraphicalInstall").

---

### Post by Steve413z on 2008-05-24
ThinkPad T60 user here...

There is a Thinkpad utility that comes installed in Windows to burn that recovery partition to a DVD if you want. 

I burned that to DVD and deleted that partition, and I installed Windows XP from scratch with a regular install CD (not the thinkpad recovery)

However... now, I just run linux, no Windows XP anymore


...Just my two cents...

---

### Post by archer6 on 2008-05-24
> **lud666 said:**
> If you are installing from a Live CD you should easily be able to resize your Windows partition (without affecting any other partitions) using the guided option like this:


Thanks for the very rapid response and answer to my question. The screen shot, is especially helpful, as I'm sure I'm more paranoid about wiping this partition off than I need to be....:)

Cheers!

---

### Post by archer6 on 2008-05-24
> **Steve413z said:**
> ThinkPad T60 user here...

There is a Thinkpad utility that comes installed in Windows to burn that recovery partition to a DVD if you want. 

I burned that to DVD and deleted that partition, and I installed Windows XP from scratch with a regular install CD (not the thinkpad recovery)

However... now, I just run linux, no Windows XP anymore 

All I can say is Wow! This is a great forum, two responses in lightning fast speed! 

As a fellow T60 user I will post my config here so you might be able to assess if there is anything that I need to pay attention to, or potential issues to be aware of. 

T60 2007-73U 2GHz CoreDuo 2GB 100GB ATI X1400 graphics 15" 1400x1050

I would burn the recovery partition as I was aware of that but my burner failed. And I hate to buy a new one just for that. Normally I use an ultrabay battery. 

So if I'm reading your post correct you installed XP from a regular OEM disc? I do have an OEM disc of XP Pro with SP2, it's what I used to load XP on my MacBook Pro. 

That said, I'm headed in the same direction as you, I would eventually like to stop using XP, and use Ubuntu for everything. 

Any further tips or suggestions are greatly appreciated.

---

### Post by Steve413z on 2008-05-24
> **archer6 said:**
> All I can say is Wow! This is a great forum, two responses in lightning fast speed! 

As a fellow T60 user I will post my config here so you might be able to assess if there is anything that I need to pay attention to, or potential issues to be aware of. 

T60 2007-73U 2GHz CoreDuo 2GB 100GB ATI X1400 graphics 15" 1400x1050

I would burn the recovery partition as I was aware of that but my burner failed. And I hate to buy a new one just for that. Normally I use an ultrabay battery. 

So if I'm reading your post correct you installed XP from a regular OEM disc? I do have an OEM disc of XP Pro with SP2, it's what I used to load XP on my MacBook Pro. 

That said, I'm headed in the same direction as you, I would eventually like to stop using XP, and use Ubuntu for everything. 

Any further tips or suggestions are greatly appreciated.


well actually, I used a student copy of XP Pro, I used the key I had with my student license, and used the CD i got from the school. However I think the CD they gave us was a "corporate" CD, but I think using the OEM key on your thinkpad with the OEM disk you used on your macbook, should work fine.

edit: on second thought, it is microsoft

---

### Post by archer6 on 2008-05-24
> **Steve413z said:**
> well actually, I used a student copy of XP Pro, I used the key I had with my student license, and used the CD i got from the school. However I think the CD they gave us was a "corporate" CD, but I think using the OEM key on your thinkpad with the OEM disk you used on your macbook, should work fine.

edit: on second thought, it is microsoft

Will I need anything else on the Ubuntu side or is it all compatible with my ATI X1400 graphics card and display of 1400x1050?

---

### Post by Steve413z on 2008-05-24
ATI card is supported, (and 8.04 improved the ATI driver so now compiz works) 

the only thing you might run into a problem with is the wireless card, if you have an intel wireless card, it should work ok

---

### Post by archer6 on 2008-05-24
> **Steve413z said:**
> ATI card is supported, (and 8.04 improved the ATI driver so now compiz works) 

the only thing you might run into a problem with is the wireless card, if you have an intel wireless card, it should work ok

Good point I forgot about the wifi and it's crucial for me as I use it everyday at the office, home and on the road at starbucks so it's the only way I access the net.

---

### Post by Steve413z on 2008-05-24
you might want to install the package known as "laptop-net" once you install ubuntu, because the wired network card does this weird thing, where it doesn't work unless you boot ubuntu with the network cable plugged in, "laptop-net" should help resolve that problem

---

### Post by archer6 on 2008-05-24
> **Steve413z said:**
> you might want to install the package known as "laptop-net" once you install ubuntu, because the wired network card does this weird thing, where it doesn't work unless you boot ubuntu with the network cable plugged in, "laptop-net" should help resolve that problem

I never use a hard wired ethernet connection though I only use WiFi. As I'm super mobile. would I still need Laptop-Net?

---

### Post by Steve413z on 2008-05-24
no, however, I still recommend it, you never know when you might need to use a wired network card

(wireless screws up, need to access network via wired LAN, etc.)

---

### Post by archer6 on 2008-05-24
> **Steve413z said:**
> no, however, I still recommend it, you never know when you might need to use a wired network card

(wireless screws up, need to access network via wired LAN, etc.)

Very good point, I agree. Thanks very much for all your time and effort as well as fast responses. I greatly appreciate it.

Cheers!

---


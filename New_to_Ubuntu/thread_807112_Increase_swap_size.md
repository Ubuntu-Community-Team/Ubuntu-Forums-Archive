---
title: "Increase swap size"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by philipluna66 on 2008-05-25
I have a very old computer with Pentium 111 375 mb ram and 385 mb swap. I am downloading and my swap is to the limit is it possible to increase the size till I can get things sorted Or any other suggestions.I have bought two 500mb stick of ram but the motherboard will not read it so I need a new motherboard which is coming next month With a faster processor I hope

---

### Post by sayakb on 2008-05-25
To increase your swap, shrink an existing partition using gparted. Now swapoff the existing swap and delete the existing swap. Now create a new swap with the free space from the drive included and right click and select swapon.

---

### Post by Inxsible on 2008-05-25
You can use Gparted and recreate/resize the partitions to increase the swap. Gparted in on the Live Cd

---

### Post by kerry_s on 2008-05-25
sudo apt-get install swapd

it will create swap files when more swap is needed and remove it when no longer needed. it's automatic so you don't have to do anything.

---

### Post by philipluna66 on 2008-05-25
Did what you said it gave me from 384 to 386 mb I was hoping to get more. Please bare in mind I am new to this so an idiots guide would be helpfull Thanks

---

### Post by evertsfnic on 2008-05-25
Me too, it's kind of hard for me to   learn new os, I AM TRYING..........

---

### Post by kerry_s on 2008-05-25
> **philipluna66 said:**
> Did what you said it gave me from 384 to 386 mb I was hoping to get more. Please bare in mind I am new to this so an idiots guide would be helpfull Thanks

sorry, forgot to tell you it makes 4mb swap files at a time default, it will make as many as needed when needed. you can change the setting in /etc/swapd.conf

you must edit as root:
gksudo gedit /etc/swapd.conf

see pic->

---

### Post by philipluna66 on 2008-05-26
I did this and tried  sudo apt-get install swapd and it says you already have the latest version ???

---

### Post by housam on 2008-05-26
this [[COLOR="Red"]_guide _[/COLOR]]("https://help.ubuntu.com/community/SwapFaq#head-75ffcb00cefe143fc380f84d7ea9203f16a596d0")is about adding more swap:

---

### Post by ZabiGG on 2008-05-26
Just follow the tutorial below to the letter, and you should achieve what you are looking for:

[http://desktopwithubutnu.wordpress.com/increase-swap-after-installation/](http://desktopwithubutnu.wordpress.com/increase-swap-after-installation/)

Hope this helps,

Z.

P.-S. For starter documentation, if you want to learn more about Ubuntu and Linux, just click on the first link in my signature below.

---

### Post by philipluna66 on 2008-05-26
Hi I followed the tutorial and at the first comand dd if=/dev/zero of=/extra-swap bs=1M count=1024 I got permision denied So I couldnt do anything else Thanks for the tip anyway

---

### Post by ZabiGG on 2008-05-26
I should have mentioned it:

insert 

sudo

before each command. The system will ask for your password the first time, but will not for the subsequent commands. So you'll need to enter it as follows from dd:

*sudo dd if=/dev/zero of=/extra-swap bs=1M count=1024* 

We’ll use the mkswap command to make our file swap-consumable for the Linux kernel.

*sudo mkswap /extra-swap*
 

To turn on the swap file run

*sudo swapon /extra-swap*
 

Now* swapon -s* will show the new file also.
 

And to make this swap on even after booting your machine you have to enter

 

*sudo cp /etc/fstab /etc/fstab.mybackup*
 

That should work.

---

### Post by philipluna66 on 2008-05-26
OK THANKS for that I did everything you said it went well actually to well i created 1.4gig I backed it up rebooted but my widget is now saying I only have 385 mb Is it there when I need it or did I not wait long enough for it to back up before rebooting. I think 1.4 gig is a little to much swap I thought about 800 - 1000 mb

---

### Post by jeffus_il on 2008-05-26
Monitor your swap space usage before making changes, you can know how much swap you really need. Use the system monitor->resource tab in Ubuntu.

---

### Post by ZabiGG on 2008-05-26
The swap you created is a supplementary swap. It is only used when needed and as much as needed.

---

### Post by philipluna66 on 2008-05-26
Thanks I changed the sudo dd if=/dev/zero of=/extra-swap bs=1M count=1024  from 1024 to 500 and I hope I have saved it OK THANKYOU FOR ALL YOURE HELP

---

### Post by philipluna66 on 2008-05-26
Hi I eventually created 800mb of swap But I have just booted up again and my swap according to my widget is only 384mb as before. Is my extra swap there or do I have to create it every time???

---

### Post by kerry_s on 2008-05-26
philipluna66, if you installed swapd and made the change in swapd.conf you don't need to worry about swap, it will make a swap file 128mb at a time only when needed and remove it when no longer needed.

if your under the impression that swap can increase your performance your wrong, swap is slow, you want to use as less of it as possible, it's just emergency memory and not used all the time.

---

### Post by Inxsible on 2008-05-26
Wouldn't it have been easier to just increase swap using Gparted and resizing the appropriate partitions?

And I agree with kerry. The less the swap is used, the better it is

---


---
title: "Login password removed and disabled after reboot"
date: 2021-08-16
forum: New to Ubuntu
---

### Post by jeuan on 2021-08-16
Hello! 

I am new to Linux and my system is a portable Ubuntu 20.4 on a USB stick. I have set a password for my account (it's my first account after installing Ubuntu, so it is a super-user I suppose?) and I have disabled Auto Login in Setting > User. But every time after a clean reboot, my password is gone and I could just login without a password. I would set it again and it will be gone after another reboot. Logging out and back in without a reboot is fine (i.e. requires password). I have created a second user account w/o admin rights and that account has no such problem. Since I have been using my first account for a while with many saved settings, I prefer not to migrate to a new user account.  Is there a way to solve this problem?  Many thanks for any advice :)

---

### Post by monkeybrain20122 on 2021-08-17
Well if it is a live usb then by default it doesn't store anything so every time you reboot you start with a clean slate. The live usb is not meant to be a "portable install", it is for testing, installing and trouble shooting. You can enable persistence when you create the live usb but AFAIK it is limited to 4G because the USB is is formatted in FAT.

---

### Post by jeuan on 2021-08-17
Thanks so much for the explainer! I formatted a 128GB USB Flash Drive in exFAT and it seems to work, except this login issue.

---

### Post by monkeybrain20122 on 2021-08-17
> **jeuan said:**
> Thanks so much for the explainer! I formatted a 128GB USB Flash Drive in exFAT and it seems to work, except this login issue.

If you are doing a full install into a flash drive then you should format it in a Linux file system such as ext4, not exFAT. I don't think you can even install in exfat so it is a live system.

---

### Post by ActionParsnip on 2021-08-17
Did you use another USB stick or optical media (CD/DVD) to install Ubuntu to the USB stick or did you use a tool like Rufus/Etcher to transfer the ISO to the USB stick?

---

### Post by jeuan on 2021-08-17
Yes you are right, my USB stick was formatted as FAT for the Ubuntu partition and Ext3 for persistent storage :P

---

### Post by jeuan on 2021-08-17
> **ActionParsnip said:**
> Did you use another USB stick or optical media (CD/DVD) to install Ubuntu to the USB stick or did you use a tool like Rufus/Etcher to transfer the ISO to the USB stick?

Hi, I used Rufus to transfer the ISO to the USB stick. I learned that from installing TAILS :p

---

### Post by tea for one on 2021-08-17
Rufus cannot [COLOR="#0000FF"]fully install[/COLOR] Ubuntu to a USB stick.
It can only create a [COLOR="#0000FF"]live[/COLOR] USB (with or without persistent storage)

During the installation procedure for a [COLOR="#0000FF"]full install[/COLOR], you would be asked for certain details:-

Language
Location
User name
Password
Etc

Rufus does not prompt for this info.

Please boot into your system (without selecting the second user) and open a terminal.
What is on the first line before typing anything else?
```
ubuntu@ubuntu:~$
```

---

### Post by jeuan on 2021-08-20
> **tea for one said:**
> Rufus cannot [COLOR=#0000FF]fully install[/COLOR] Ubuntu to a USB stick.
It can only create a [COLOR=#0000FF]live[/COLOR] USB (with or without persistent storage)

During the installation procedure for a [COLOR=#0000FF]full install[/COLOR], you would be asked for certain details:-

Language
Location
User name
Password
Etc

Rufus does not prompt for this info.

Please boot into your system (without selecting the second user) and open a terminal.
What is on the first line before typing anything else?
```
ubuntu@ubuntu:~$
```

Thanks for the info and sorry for my late response as I was sick for the past two days... 

I followed your instructions above and the terminal windows shows exactly what you suggested: 

ubuntu@ubuntu:~$

The reason I wanted to keep using the USB stick is because I want a clean slate for doing my banking and finance matters.  My computer at home is shared with my kids and they love to install games and other plugins - although they have separate accounts I don't feel safe working on the same machine running Windows. I guess if the USB stick cannot facilitate a password then I just have to lock it up somewhere safe...

---

### Post by tea for one on 2021-08-20
> **jeuan said:**
> I guess if the USB stick cannot facilitate a password then I just have to lock it up somewhere safe...

Do you have another USB stick?
You can use your current live USB stick to [COLOR="#0000FF"]fully install[/COLOR] Ubuntu to [COLOR="#0000FF"]another[/COLOR] portable USB device.

When you follow the instructions for a full installation, you will be asked to create a username, password etc.

Would this not solve your domestic security question?

---

### Post by monkeybrain20122 on 2021-08-20
> **jeuan said:**
> 

The reason I wanted to keep using the USB stick is because I want a clean slate for doing my banking and finance matters.  My computer at home is shared with my kids and they love to install games and other plugins - although they have separate accounts I don't feel safe working on the same machine running Windows. I guess if the USB stick cannot facilitate a password then I just have to lock it up somewhere safe...

Well why do you need a password if you can't store anything so nothing to protect? That is exactly what you want, to start with a clean slate every time you boot up and no revealing info or malicious code can be stored. On the other hand I don't see what purpose of locking it up somewhere would serve. It would be quite useless to access your bank account without any info, and anyone can make a identical live usb. :)

---

### Post by jeuan on 2021-08-20
> **tea for one said:**
> Do you have another USB stick?
You can use your current live USB stick to [COLOR=#0000FF]fully install[/COLOR] Ubuntu to [COLOR=#0000FF]another[/COLOR] portable USB device.

When you follow the instructions for a full installation, you will be asked to create a username, password etc.

Would this not solve your domestic security question?

Thanks for the suggestion! I will try that today :) 

Cheers!

---

### Post by jeuan on 2021-08-20
> **monkeybrain20122 said:**
> Well why do you need a password if you can't store anything so nothing to protect? That is exactly what you want, to start with a clean slate every time you boot up and no revealing info or malicious code can be stored. On the other hand I don't see what purpose of locking it up somewhere would serve. It would be quite useless to access your bank account without any info, and anyone can make a identical live usb. :)

Actually I am able to store all my files and settings. It's only the login password that keeps resetting. I first tried using TAILS with persistent storage enabled, but it was too much of a hassle for everyday use so I switched to Ubuntu. I just don't want too much exposure to potential viruses and malware on windows where my kids installs everything they pick up. I cannot afford to buy a new PC at this point so this seems like a viable option.

---

### Post by tea for one on 2021-08-21
When you install  Ubuntu to an external USB device, it is a good idea to isolate, remove or de-activate your internal drive to avoid subsequent boot problems with Windows.

Also please have a look at [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by jeuan on 2021-08-21
> **tea for one said:**
> When you install  Ubuntu to an external USB device, it is a good idea to isolate, remove or de-activate your internal drive to avoid subsequent boot problems with Windows.

Also please have a look at [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I just tried your previous suggestion and now I have a new and proper copy of Ubuntu on an external SSD. It's working very smooth so far.

Yes, I disconnected all the internal HDDs on my PC before doing the above just in case anything goes wrong with the Windows partition. Always better to be safe ;)

This is a great community and I am all in for Ubuntu - thank you again for the advice! 

Take care and stay safe!

---

### Post by tea for one on 2021-08-21
Splendid - It's nice to read about successful results.

If appropriate, you could consider [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---


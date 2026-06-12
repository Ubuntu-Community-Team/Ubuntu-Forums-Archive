---
title: "Dell Service Tag number location in the system"
date: 2012-01-26
forum: New to Ubuntu
---

### Post by RangerRay on 2012-01-26
I have a Dell Dimension 2400, that has a virus or possibly a hacker that tracks everything I do. With my service tag number, the virus or hacker finds me with no problems. I tried asking Dell Support to please issue me a new one, since it was Dell Support drivers download that passed the virus on to me. They said they could, but it would cost me $129.00, to issue me a new one and dispose of my unwanted guest. They gave me the virus, and I have to pay them to dispose of it. Does anyone know where I can locate it in the file system or a microchip, (where it is read by other computers). This would help me out, in getting rid of the virus, by flashing my BIOS. Hoping by flashing BIOS. I know the IP Address of my guest, I've used Hp Hosts, and the call it a URI Virus, and that I no longer have it. But I know it's still there. Also, quick question, to sign in, i noticed I have Ubuntu, and Ubuntu 2D where my sign in password box is, is this suppose to be like that.:confused:

---

### Post by Double.J on 2012-01-26
Hi there, First do not buy a new service tag number... I'll explain..

---

### Post by Double.J on 2012-01-26
The service tag is just an Identifier to the dell website/service database to let them know what's inside your box - a new service tag number would still point to the exact same drivers/info/software that the old one did.

Which OS are you having problems with? Windows or Ubuntu? I'll assume Windows as you said it was a dell drivers download:

Second it is very unlikely that the malware came from dell. It is of course possible that their servers/mirrors were attacked, but this is very unlikely. What's more likely is that it was either a dummy site, or more likely, that the download co-insided with the activation of malware - Vendor downloads tend to require a restart. Quite a fair bit of malware will activate upon a restart. 

As to the intruder sinario, I'd say this is also unlikely - it could be the case, but generally speaking if an intruder gains access to a system, their goal would be to go unnoticed, seek out any financial documents and disconnect before you notice - If you knew they were there, you'd change your info ;)

With regards to the malware - if you have the same problem in Ubuntu and Windows, it is almost definitely a hardware issue - what are the symptoms? If it's just windows, it may well be malware

First check if you have any malware - use antivirus to scan all your windows partitions -also move the contents of your /home directory to a windows partition/folder and scan. use a program such as clam Av or AVG to scan your ubuntu partitions.

As for antivirus to scan windows, I don't use it enough to be able to recommend a good brand, but I understand that Microsoft supply their own maintained antivirus in the forms of Microsoft Security Essentials more info [here]("http://windows.microsoft.com/en-US/windows/products/security-essentials")

A list of MS recommended 3rd party checkers is [here]("http://www.microsoft.com/windows/antivirus-partners/windows-7.aspx")



All the best - good luck!

---

### Post by Double.J on 2012-01-26
> **RangerRay said:**
>  i noticed I have Ubuntu, and Ubuntu 2D where my sign in password box is, is this suppose to be like that.:confused:

Yes :) 2d is designed to speed up the Ubuntu interface on hardware that struggles with unity (3D - the default)

---

### Post by Bartender on 2012-01-26
RR, I'm sorry, but your post doesn't make any sense.  Someone is tracking you using your Dell Service Tag??  I think you misunderstand the entire concept.

gnu/mirow is correct; the Service Tag just helps keep track of your original build.  Using your Service Tag, you can go into Dell's site and pull up a database that tells you what was inside _when it was built_.  If you pulled out your video card and replaced it, or upgraded the RAM, Dell's Service Tag data wouldn't change.  It's historical data, nothing more.  

Plus the Tag can be handy to you when looking for drivers.  ONLY if you're still running the exact same operating system that was originally installed!

There's absolutely no point at all in 'buying' another Service Tag.  I can't imagine that such an option even exists.  If you've got someone on the phone telling you that you can buy another Service Tag for $130 I think you're being scammed.  

Are you dual-booting?  Because you said you're running Ubuntu.  Ubuntu doesn't use any of the drivers from the Dell Downloads site.  If you're running Linux only, and NOT dual-booting, Dell's Service Tag is just a sticker on the side of your case.

---

### Post by RangerRay on 2012-02-13
> **gnu/mirow said:**
> Hi there, First do not buy a new service tag number... I'll explain..
First of all, i want to apologize to all of you for not responding to this post fast enough. I opened this forum up daily, but didn't know how to find my threads, until two days ago. That because I started posting my major problem in resolutions. I now thank you all for your feedback, unfortunately, i decided to disassembly my dell 2400 and put a different motherboard. It still hasn't solved my problem, but at least I know a hacker can't be tracking me from service tag number, again that you all. :p

---

### Post by RangerRay on 2012-02-13
> **gnu/mirow said:**
> The service tag is just an Identifier to the dell website/service database to let them know what's inside your box - a new service tag number would still point to the exact same drivers/info/software that the old one did.

Which OS are you having problems with? Windows or Ubuntu? I'll assume Windows as you said it was a dell drivers download:

Second it is very unlikely that the malware came from dell. It is of course possible that their servers/mirrors were attacked, but this is very unlikely. What's more likely is that it was either a dummy site, or more likely, that the download co-insided with the activation of malware - Vendor downloads tend to require a restart. Quite a fair bit of malware will activate upon a restart. 

As to the intruder sinario, I'd say this is also unlikely - it could be the case, but generally speaking if an intruder gains access to a system, their goal would be to go unnoticed, seek out any financial documents and disconnect before you notice - If you knew they were there, you'd change your info ;)

With regards to the malware - if you have the same problem in Ubuntu and Windows, it is almost definitely a hardware issue - what are the symptoms? If it's just windows, it may well be malware

First check if you have any malware - use antivirus to scan all your windows partitions -also move the contents of your /home directory to a windows partition/folder and scan. use a program such as clam Av or AVG to scan your ubuntu partitions.

As for antivirus to scan windows, I don't use it enough to be able to recommend a good brand, but I understand that Microsoft supply their own maintained antivirus in the forms of Microsoft Security Essentials more info [here]("http://windows.microsoft.com/en-US/windows/products/security-essentials")

A list of MS recommended 3rd party checkers is [here]("http://www.microsoft.com/windows/antivirus-partners/windows-7.aspx")



All the best - good luck!
  I spent about 4 different days with Microsoft and waited an hour, just to talk to someone, then i was given from one person to another, the first day, not resolving my problem. The second day, finally talk somebody that would help me out, after waiting about 45 minutes to talk to someone. Were talking, he puts me on hold, the connection is lost, this is a landline. I try calling back, I again am given a run around, spoke to six different people, except for the one i wanted to talk to. After four days of trying, i gave up. I was started using the computer in the lobby where i live. I have never used this type operating system, which is Ubuntu. So, I went on Ebay and started looking for operating systems, when I came upon Ubuntu, I paid $5.00 for the live CD, including postage.  But, thank you anyway, I want to get away from Microsoft. I want to get rid of them so bad, they're still haunting me on my hard drive, can't seem to delete windows OS from my hard drive. That's another issue. :D

---

### Post by BlinkinCat on 2012-02-13
> **RangerRay said:**
> I spent about 4 different days with Microsoft and waited an hour, just to talk to someone, then i was given from one person to another, the first day, not resolving my problem. The second day, finally talk somebody that would help me out, after waiting about 45 minutes to talk to someone. Were talking, he puts me on hold, the connection is lost, this is a landline. I try calling back, I again am given a run around, spoke to six different people, except for the one i wanted to talk to. After four days of trying, i gave up. I was started using the computer in the lobby where i live. I have never used this type operating system, which is Ubuntu. So, I went on Ebay and started looking for operating systems, when I came upon Ubuntu, I paid $5.00 for the live CD, including postage.  But, thank you anyway, I want to get away from Microsoft. I want to get rid of them so bad, they're still haunting me on my hard drive, can't seem to delete windows OS from my hard drive. That's another issue. :D

All the very best of luck to you RangerRay -    :P

---


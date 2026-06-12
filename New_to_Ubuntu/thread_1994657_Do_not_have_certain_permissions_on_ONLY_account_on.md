---
title: "Do not have certain permissions on ONLY account on my computer"
date: 2012-06-03
forum: New to Ubuntu
---

### Post by mimicatastrophe on 2012-06-03
I am not sure which ones, but I know I cannot open "root" folder and a few others in the file system...also some tasks on the computer. I cannot clear the cache memory by running the echo 3 command I saw on another forum post. 

Also, should I be able to just place a CD in my CD-Rom drive and see/use it? That's not happening but could be the drive.

this is my only account, the one i set up on install and there is no other option when i log out except for guest.

---

### Post by steeldriver on 2012-06-03
that's normal - the account you created at install time *will* be a member of the admin / sudo group, but you can't just do tasks that require root permissions without confirming via sudo or gksudo - kind of the same as  Win7 'run as...' 

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

hope this helps

oops the CD stuff is *not* normal but let's take a closer look at that

---

### Post by jtarin on 2012-06-03
> **mimicatastrophe said:**
> 
Also, should I be able to just place a CD in my CD-Rom drive and see/use it? That's not happening but could be the drive.

Could be the CD also......does this happen to all CD's?

---

### Post by mimicatastrophe on 2012-06-03
probably haha I wasn't sure where I would be finding the CD on the system honestly-- brand new. I of course assumed the places that made sense and its a music cd so figured also it would come up in rhythm but I have tried a few now and nothing so probably the drive...and thanks for that link above! very very helpful.

I had 2 more questions starting out that I just put in general help if there are any leads or links I'd be 100% cured! Just a memory issue but that could be the computer also so guess it's time to open her up.

Thanks again!!

---

### Post by mcduck on 2012-06-03
> **mimicatastrophe said:**
> I am not sure which ones, but I know I cannot open "root" folder and a few others in the file system...also some tasks on the computer. I cannot clear the cache memory by running the echo 3 command I saw on another forum post. 

Also, should I be able to just place a CD in my CD-Rom drive and see/use it? That's not happening but could be the drive.

this is my only account, the one i set up on install and there is no other option when i log out except for guest.

Absolutely normal, there is no such situation as having only a single user acocunt on a Unix/Linux system. And the user acocunt created during install is not a full-time root account, it only has the permission to *temporarily gain full privileges*, when specifically requested by the user.

So no, you are not supposed to be able to access /root when youa re not actually running as the root user. Not that you'd usually even need to, /root is just root user's home directory and should be pretty much empty considering Ubuntu's default security model doesn't sue root account directly.

For more information about Ubuntu's security model you should read this guide: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

What comes to the CD-ROM, yes, syou should be able to just pop in a disc and see it. If you can actually do anything with the disc after that of course dpeends on the type & contents of the disc...

---

### Post by mimicatastrophe on 2012-06-03
thanks I have read that sudo wiki now and i understand! i don't want to mess with the system especially myself but i do want to get it all running the way i need/prefer so that i wont need to make changes in the future. 

 so thanks for your help both of you. fastest and kindest forum help i have had so at least that is assuring when it comes to making the switch from windows.

---

### Post by mimicatastrophe on 2012-06-03
...

---


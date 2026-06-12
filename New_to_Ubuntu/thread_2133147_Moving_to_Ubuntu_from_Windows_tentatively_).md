---
title: "Moving to Ubuntu from Windows tentatively :)"
date: 2013-04-07
forum: New to Ubuntu
---

### Post by Wise1 on 2013-04-07
Good Afternoon,

I have been searching the forums but not really seeing any clear answers to my questions.  Basically I am a long term windows user, probably no surprise.  A friend put me on to Ubuntu and so far I am loving it.

Currently I am dual booting with Windows 7 just in case I get the shakes and need to go back to it, however so far so good, in fact I am incredibly surprised as to just how much can run on Linux through Wine and other methods such as virtual Box.

So 2 questions really.

1)  How efficient would it be to simply run Windows 7 in virtual box with Ubuntu as my main OS?  I run some games that simply won't work under Wine for example.  Would a virtual windows install work smoothly?  I have not tried as I don't have enough space on my SSD with the current dual boot setup.

2)  Once I decide to remove Windows 7 and thus kill the dual boot, can I just simply delete the windows partition and resize it so Ubuntu takes it all over?

Thanks for you help

Lee

---

### Post by Paqman on 2013-04-07
> **Wise1 said:**
> 
1)  How efficient would it be to simply run Windows 7 in virtual box with Ubuntu as my main OS?  I run some games that simply won't work under Wine for example.  Would a virtual windows install work smoothly?  I have not tried as I don't have enough space on my SSD with the current dual boot setup.


For most things virtualisation works extremely well, but for not for gaming. Virtualisation of 3D graphics cards is in its infancy, and performance would be poor. If you have games that work best on Windows, keep the Windows side of your dual boot. Windows is an excellent gaming platform, no harm in using it for what it's best at.

Obviously you could play any games that don't require decent 3D performance in a VM.

> 
2)  Once I decide to remove Windows 7 and thus kill the dual boot, can I just simply delete the windows partition and resize it so Ubuntu takes it all over?


Yep, if you like. You'd just boot up into your live disk/USB and delete that partition, then expand the Ubuntu one(s) into the gap.

---

### Post by fantab on 2013-04-07
I would say keep Windows 7 until its support runs out. After all you paid for it. Also WINE tends to work better if actual Windows is present. There a couple of applications I use that don't work on Linux only machine with Wine. But on my another machine that Multi-boots Linux and Windows those applications run quite well when loaded with Wine. I just mount the Windows C: and run Windows applications and games installed in windows through Wine in Ubuntu. 

What you can do is, install Windows on HDD and keep SSD for Ubuntu. You can just keep the Windows C: remove other partitions and reuse them for Linux. 

My two cents...

---

### Post by Wise1 on 2013-04-07
You are probably right in just keeping windows, my first thought was simply keeping the dual boot, re-installing Windows 7 with the minimum for my needs, currently it's about 70GB, no idea where all that is being used but I am certain it's just bloat over the last couple of years since I got this PC.  As suggested I could install it on the HDD as it's 500GB about 300GB free at present.

Thanks for the advice, I feel such a beginner again, but in a good way :)

---

### Post by pfeiffep on 2013-04-07
I suggest you not underestimate your need for Win 7 - I started about a year ago to move away from Win ?? in general and found quite a bit of open source available in Windows. I replaced Office with Open Office, OutLook with Thunderbird, IE with Chrome. I just started using Linux this Feb and really do like it. I'm not yet willing to embark on a no Win approach as yet for these reasons: 

[LIST=1]
[*]Learning curve for GIMP to replace photoshop
[*]Desk top version of tax program (not certain of the online versions that will certainly work regardless of OS)
[*]Finding fully functional iCloud replacement for my iPhone
[*]Learning curve and replacement app for digitizing my vinyl and tape library
[/LIST]
I am actively looking for those and hope I can remedy them without too much pain. The learning curve of a new OS is a bit daunting so I don't want to complicate it with the above.

---

### Post by fantab on 2013-04-07
Whenever you resize/move or delete your Windows partitions run Windows Defragmentation first. Run it a couple of times. Also, Windows installs work best when the main C: partition has at least 25% of free space. Do take this into account when you restructure your partitions.

---

### Post by bigmac15 on 2013-04-07
Sorry, when you refer to wine is it this [WineHQ](http://adf.ly/MSpem)?  Im new to ubuntu and am currently running fedora 17

---

### Post by ave2 on 2013-04-07
I still have win xp running on my system for games. Lunux is awesome and I do 90% of my work in it, but photoshop is a mess and a lot of games give me hassles, so it's just not worth the trouble. I am looking forward to the day I can nuke windows, but right now we have to suffer a little linger :p

---

### Post by Wise1 on 2013-04-07
> **pfeiffep said:**
> I suggest you not underestimate your need for Win 7 - I started about a year ago to move away from Win ?? in general and found quite a bit of open source available in Windows. I replaced Office with Open Office, OutLook with Thunderbird, IE with Chrome. I just started using Linux this Feb and really do like it. I'm not yet willing to embark on a no Win approach as yet for these reasons: 

[LIST=1]
[*]Learning curve for GIMP to replace photoshop
[*]Desk top version of tax program (not certain of the online versions that will certainly work regardless of OS)
[*]Finding fully functional iCloud replacement for my iPhone
[*]Learning curve and replacement app for digitizing my vinyl and tape library
[/LIST]
I am actively looking for those and hope I can remedy them without too much pain. The learning curve of a new OS is a bit daunting so I don't want to complicate it with the above.

Indeed, I am actually not new to Linux, however all my experience is via hosting, I run a lot of websites via Virtual Private Servers and Dedicated servers using Centos, it's all command line though but over the years I suppose I have learnt the benefits compared to Windows.  I have been running Ubuntu for a while on Virtualbox and really my dependency on Windows comes down to nothing more than occasional gaming. 

I moved pretty all of what I do to Google; mail, cloud storage, apps and so on.  My goal is really a more robust but integrated experience Whether on desktop, tablet or phone.  I want to pretty much do everything I currently do wherever I am and whatever I am using.  I really don't see windows 8 as being a viable opportunity, in fact I would go as far as to say Windows 8 is going to Microsoft's Nemesis more than anyhting in the past.  Apple is too focussed on controlling what It's users can do and I don't like that.

So a combination of Linux and Android appears the best solution other than gaming.

---

### Post by blackbird34 on 2013-04-07
> **bigmac15 said:**
> Sorry, when you refer to wine is it this [WineHQ]("http://adf.ly/MSpem")?  Im new to ubuntu and am currently running fedora 17

WineHQ is a database of applications that work well - or not so well - under WINE. 
The [PlayonLinux]("http://www.playonlinux.com/en/") team do a lot of work on making Wine work better, and making it easier to set stuff up, too. [http://en.wikipedia.org/wiki/PlayOnLinux](http://en.wikipedia.org/wiki/PlayOnLinux)

---

### Post by Paqman on 2013-04-07
> **fantab said:**
> Windows installs work best when the main C: partition has at least 25% of free space.

That actually goes for any OS. No filesystem likes being run too full, you'll get fragmentation.

---

### Post by fantab on 2013-04-08
> **Paqman said:**
> That actually goes for any OS. No filesystem likes being run too full, you'll get fragmentation.

+1. I agree.

---

### Post by Thee on 2013-04-08
> **pfeiffep said:**
> 
[LIST=1]
[*]Learning curve and replacement app for digitizing my vinyl and tape library
[/LIST]


If you were familiar with software like SoundForge on Windows, you should check out [http://www.ocenaudio.com.br/](http://www.ocenaudio.com.br/)

---


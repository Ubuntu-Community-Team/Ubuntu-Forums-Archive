---
title: "If I get a virus on xp will it affect ubuntu?"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by aknisely on 2008-05-14
I'm getting ready to set up my PC to dual boot with windows and Ubuntu. I'll be running each OS on their separate hdd but I want to know If I get a  virus on windows will it affect Ubuntu? Thanks

---

### Post by jimv on 2008-05-14
No.

---

### Post by Oldsoldier2003 on 2008-05-14
> **aknisely said:**
> I'm getting ready to set up my PC to dual boot with windows and Ubuntu. I'll be running each OS on their separate hdd but I want to know If I get a  virus on windows will it affect Ubuntu? Thanks

Nope. windows viruses have no impact on your Linux system. Theoretically they can cause some issues in wine, but they can only affect the operation of your system temporarily.

---

### Post by SunnyRabbiera on 2008-05-14
No, as linux is immune to windows viruses.

---

### Post by psusi on 2008-05-14
If it is a boot virus it can replace or corrupt grub, so yes, but those are very, very rare these days.

---

### Post by Thingymebob on 2008-05-14
Or re-write the MBR/Partition table and screw everything (again rare)

---

### Post by RequinB4 on 2008-05-14
The answer is No. :)

> **Oldsoldier2003 said:**
> Nope. windows viruses have no impact on your Linux system. Theoretically they can cause some issues in wine, but they can only affect the operation of your system temporarily.

Not that Oldsoldier is talking about being ON linux and getting a virus through Wine (which allows you to run windows programs), not getting a virus on windows.

Though that is extremely unlikely, considering 1) most likely you would have to be running internet explorer with wine (why, when you have firefox native?) or using some other internet connection with wine, and 2) Very few windows viruses are smart enough (None do it on purpose) to damage anything outside of your virtual C:\, which means most likely nothing can be affected except your Wine programs, and even then only temporarily

---

### Post by mkoehler on 2008-05-14
> **Oldsoldier2003 said:**
> Nope. windows viruses have no impact on your Linux system. Theoretically they can cause some issues in wine, but they can only affect the operation of your system temporarily.

No, they can not affect your Ubuntu installation.  Additionally, I would like to clarify the statement above.  Wine doesn't use your windows installation at all - it creates a virtual windows filesystem in your home directory (~/.wine/drive_c).  Therefore, any viruses that are installed in windows will not affect your wine installation either.  However, it is theoretically possible to install a windows virus with wine - even so, very wine is still too bad to run most common windows viruses (even if you try).  Therefore, you've got nothing to worry about. :)

---

### Post by Dribbel on 2008-05-14
Well I would be carefull because it could effect your harddisk and since Ubuntu is on your harddisk it could effect your Ubuntu..:?

---

### Post by Dribbel on 2008-05-14
> **mkoehler said:**
> No, they can not affect your Ubuntu installation.  Additionally, I would like to clarify the statement above.  Wine doesn't use your windows installation at all - it creates a virtual windows filesystem in your home directory (~/.wine/drive_c).  Therefore, any viruses that are installed in windows will not affect your wine installation either.  However, it is theoretically possible to install a windows virus with wine - even so, very wine is still too bad to run most common windows viruses (even if you try).  Therefore, you've got nothing to worry about. :)

Yeah, I'll go with mkoehler > Wine isn't connected to your windows-installation

---

### Post by billgoldberg on 2008-05-14
No need to scare him with theoretical wine viruses.

1. I never heard of such a thing in real life
2. More than likely he won't use Wine at all (why should you when you dual boot)?

---

### Post by TeoBigusGeekus on 2008-05-14
> **mkoehler said:**
> No, they can not affect your Ubuntu installation.  Additionally, I would like to clarify the statement above.  Wine doesn't use your windows installation at all - it creates a virtual windows filesystem in your home directory (~/.wine/drive_c).  Therefore, any viruses that are installed in windows will not affect your wine installation either.  However, it is theoretically possible to install a windows virus with wine - even so, very wine is still too bad to run most common windows viruses (even if you try).  Therefore, you've got nothing to worry about. :)

Please everybody, take a look at an old thread I discovered:
[http://ubuntuforums.org/showthread.php?t=72598]("http://ubuntuforums.org/showthread.php?t=72598")

---

### Post by Oldsoldier2003 on 2008-05-14
> **Dribbel said:**
> Yeah, I'll go with mkoehler > Wine isn't connected to your windows-installation

I take it that you guys don't realize that you can run applications through wine that reside on your XP partition. Not recommended behavior but there are people out there that do it :)

If you were to grab a virus that way it still wont affect Ubuntu, other than possibly hosing your wine installation or slowing down the system temporarily. Most viruses don't work correctly under wine and will hang up causing a system slowdown until you kill wine.

---

### Post by ibuclaw on 2008-05-14
Just regularly scan common shared folders between both operating systems, and you'll be OK!

Worst case scenario that can happen is infact the reverse!

Ubuntu can be a carrier! If you download executables from untrusted or alien sites with Ubuntu, chances are they won't get scanned on download (unlike Windows, for example). So when you transport that installer, boot into Windows. You are effectively pulling the thread on the guillotine that you put your head on!

Although, speaking on behalf of the majority of the Linux Community.
I believe we succeed in being Virus-free by being smarter than most other OS users!

Only stick to what you know. Don't download it if it's from a site that you just googled!

Regards
Iain

---

### Post by Oldsoldier2003 on 2008-05-14
> **billgoldberg said:**
> No need to scare him with theoretical wine viruses.

1. I never heard of such a thing in real life
2. More than likely he won't use Wine at all (why should you when you dual boot)?

knowledge is power. This isn't scaring , its informing. It should be no more scary then knowing about viruses in windows.
1. every windows virus is a potential wine virus
2. people often use wine for a quick task rather than reboot to start windows. Wine is often a bridge during the time folks learn to become Microsoft free.

As an aside on the journey to becoming Microsoft free lots of people use Wine for recreational purposes. One of the sad facts about wine is that a lot of games need to be "cracked" in order to perform on wine. And of course cracks are not always as innocent as you would hope- the internet has loads of nasty people out there...

---

### Post by Tomatz on 2008-05-14
> **aknisely said:**
> I'm getting ready to set up my PC to dual boot with windows and Ubuntu. I'll be running each OS on their separate hdd but I want to know If I get a  virus on windows will it affect Ubuntu? Thanks


No its fine you can keep downloading po...

...nies. 

Yeah ponies ;)

---

### Post by mkoehler on 2008-05-14
> **mkoehler said:**
> No, they can not affect your Ubuntu installation.  Additionally, I would like to clarify the statement above.  Wine doesn't use your windows installation at all - it creates a virtual windows filesystem in your home directory (~/.wine/drive_c).  Therefore, any viruses that are installed in windows will not affect your wine installation either.  **However, it is theoretically possible to install a windows virus with wine** - even so, very wine is still too bad to run most common windows viruses (even if you try).  Therefore, you've got nothing to worry about. :)

Look above ^^ I said you CAN, but that it isn't a big deal.

---

### Post by fmartinez on 2008-05-14
The main thing to remember is how a virus actually works. Because Windows is used by 95% of the population most viruses are geared to infect a Windows system and it's flaws. Most Viruses use .exe files to excute which in Windows are executible files. Linux has no notion of executible files as Windows does. 
Now there are Boot viruses and Viruses that you can get from the Web and target the flaws through a web site. Like flash or itunes or any other popular 3rd party tool used by websites. Be smart about what you do and where you go, and 9 out 10 times you shouldn't have to worry about viruses. 

Even being on the paranoid side sometimes help!

---

### Post by Yoooder on 2008-05-14
> **Oldsoldier2003 said:**
> Nope. windows viruses have no impact on your Linux system. Theoretically they can cause some issues in wine, but they can only affect the operation of your system temporarily.

I'll have to do some hunting, however there was a blog post a month or so ago where someone intentionally tried to infect wine with viruses and failed to get them to run :)

---

### Post by mkoehler on 2008-05-14
Yoooder,

I think this is the link that you're looking for: [http://www.linux.com/feature/42031](http://www.linux.com/feature/42031)

---

### Post by Yoooder on 2008-05-14
> **mkoehler said:**
> Yoooder,

I think this is the link that you're looking for: [http://www.linux.com/feature/42031](http://www.linux.com/feature/42031)

Right on, that's the one :)

---

### Post by Oldsoldier2003 on 2008-05-14
> **mkoehler said:**
> Yoooder,

I think this is the link that you're looking for: [http://www.linux.com/feature/42031](http://www.linux.com/feature/42031)

Indeed, thats the article that came to mind when i said they can cause a temporary slowdown.

---

### Post by mkoehler on 2008-05-14
Of course they can, every additional program that you run will cause a little bit of a slowdown.  The point I was trying to get across is that it will not damage your computer in any way.

You can see a much more significant slowdown by opening a document in evince with a non-native font.  From my experiences, I've seen memory spikes of up to 600MB (and don't worry, this is all being worked out as we speak), but all in all, I was just trying to inform the poster that he has nothing to worry about.

---

### Post by kansasnoob on 2008-05-14
My simple answer is no. A Windows virus will not harm your Ubuntu system.

But it's still important to keep your Windows system virus free so you don't pass a virus along to those who use Windows. (Especially if you share files between Windows and Ubuntu on a FAT32 partition as I do)

AVG Free 8.0 even has some basic Spyware by default. Zonealarm provides a fairly effective free firewall for Windows. Go ahead and maintain your Windows system until you decide to dump it altogether.

BTW, my favorite "first-time" dual boot guide is here:
[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

It just works! But 8.04 is so good that it really is almost foolproof.

What I now prefer to do is just use Gparted to shrink my Windows partition enough to allow about 10GB for Ubuntu, then when I restart with the 8.04 Live CD I can just select "Guided largest continuous free space", but I used the APC guide with no trouble at least three times before I progressed to that point.

---

### Post by Oldsoldier2003 on 2008-05-14
> **mkoehler said:**
> Of course they can, every additional program that you run will cause a little bit of a slowdown.  The point I was trying to get across is that it will not damage your computer in any way.

You can see a much more significant slowdown by opening a document in evince with a non-native font.  From my experiences, I've seen memory spikes of up to 600MB (and don't worry, this is all being worked out as we speak), but all in all, I was just trying to inform the poster that he has nothing to worry about.

Oh I agree that its insignificant in the long run, Wine causes enough slowdown as it is. Windows viruses are just a minor annoyance in the grand scheme of Linux, not a show stopper like they are in Windows. (with the exception of a virus that overwrites the MBR ). as wine becomes more polished the threat of a windows virus becoming seriously annoying increases, though the threat of it doing any "real" damage doesn't.


Interestingly enough though people don't realize you can indeed run windows apps from off of your Windows partition by using wine. In some cases it works fine and in other cases you fine files being dumped into your home directory.

---

### Post by nicedude on 2008-05-14
Since they said they will be DUAL BOOTING with each OS on seperate hard drives, and the question was could it affect my ubuntu installation the answer is most definatly YES simce a windows virus could easily destroy your Ubuntu disks data thereby rendering it useless ( which in my opinion would "AFFECT UBUNTU"). But this is not normal virus or malware behavior since they like to hide and do sneaky things instead ( like steal your passwords and email spam )

So there is nothing special about Ubuntu or any other linux distro I am aware of that could stop me or anyone from writing a windows based virus that could search out your linux partitions ( would be simple to diferentiate since they will be Ext2 or 3 formated ) and then just run an fdisk command on them and bye-bye no more linux. But to my knowledge no cyber jerks have made such a virus that I know of. 
 
But windows viruses cannot spy on you in linux or operate in that enviroment, so once your Ubuntu is fired up off its drive you are safe from cyber scumbags. At least until you fire-up one of Bill G's wonderful software nightmares :-) 

Just use your ubuntu to do anything with your personal information such as online shopping, email & private websites. This way you will be protected much better than the sheeple using Microscum products.

---

### Post by bodhi.zazen on 2008-05-14
> **TeoBigusGeekus said:**
> Please everybody, take a look at an old thread I discovered:
[http://ubuntuforums.org/showthread.php?t=72598](http://ubuntuforums.org/showthread.php?t=72598)

There is a lot of FUD regarding wine. For updated information please see this link :

[http://ubuntuforums.org/showpost.php?p=4843786&postcount=22](http://ubuntuforums.org/showpost.php?p=4843786&postcount=22)

Also, one more thing you should all be aware of ...

If you install wine check out ~/.wine/dosdevices

```
ls -l ~/.wine/dosedvices
```

yep, that's right z: linked to /  bad, bad, bad. Linking to $HOME is "OK" but personally I think you should not link to anything outside of ~/.wine.

==========

Please, lets not spread FUD about wine.

---

### Post by nerdman978 on 2008-05-14
> **aknisely said:**
> I'm getting ready to set up my PC to dual boot with windows and Ubuntu. I'll be running each OS on their separate hdd but I want to know If I get a  virus on windows will it affect Ubuntu? Thanks

negatory my dear watson

---

### Post by Joeb454 on 2008-05-14
If you wanted to specifically run a virus in Wine I'm sure you'd have to remove all Wine files ;)

There's some documentation somewhere where somebody has done this :)

---

### Post by louieb on 2008-05-14
> **nicedude said:**
> ...DUAL BOOTING...affect my ubuntu installation the answer is ... YES since a windows virus could easily destroy your Ubuntu disks data thereby rendering it useless ...would "AFFECT UBUNTU...

Nicely put. =;The key to prevention is don't use windows.

---


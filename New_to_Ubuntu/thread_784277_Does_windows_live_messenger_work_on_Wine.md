---
title: "Does windows live messenger work on Wine?"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by MarkX on 2008-05-06
Since it is so far impossible in Linux to voice chat or conference with windows messenger I'd like to know if one can get WLM to work in WINE please?

(would be nice because then I could get LOADS of people to dump windows, including myself!)

---

### Post by vishzilla on 2008-05-06
You might wanna install Kopete for A/V support
```
sudo apt-get install kopete
```

---

### Post by justifier on 2008-05-06
skype? different protocoll but will do the same thing, its about time pidgin had A/V support

---

### Post by linuxlizard on 2008-05-06
One I really like is gizmo.

---

### Post by vishzilla on 2008-05-06
> **justifier said:**
> skype? different protocoll but will do the same thing, its about time pidgin had A/V support

As per this [page]("http://developer.pidgin.im/wiki/GSoC2008/VoiceAndVideo") they have accepted Audio Video support as a project in the Google Summer of Code.

---

### Post by MarkX on 2008-05-06
Just to be clear: I need Windows Live Messenger VOICE (not something else) to work in Linux and I am asking if it works under WINE since there is no other Linux prog that will do this.

---

### Post by MarkX on 2008-05-06
Just to be clear: I need Windows Live Messenger VOICE (nothing else) to work in Linux and I am asking if it works under WINE since there is no other Linux prog that will do this.

(oops, double post, sorry!)

---

### Post by aysiu on 2008-05-06
Doesn't look as if it does:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=8146&iTestingId=13421](http://appdb.winehq.org/objectManager.php?sClass=version&iId=8146&iTestingId=13421)

---

### Post by MarkX on 2008-05-06
> **aysiu said:**
> Doesn't look as if it does:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=8146&iTestingId=13421](http://appdb.winehq.org/objectManager.php?sClass=version&iId=8146&iTestingId=13421)

Thanks for the quick reply! 
Windows messenger voice support is now the only thing stopping me and numerous others running 100% Ubuntu. I wish Canonical would get involved in changing this major setback to uptake...

---

### Post by aysiu on 2008-05-06
> **MarkX said:**
> I wish Canonical would get involved in changing this major setback to uptake... I wish Microsoft would get involved in changing this setback to uptake.

I don't know anyone who uses Windos Live Messenger, though, so I don't know how major a setback it is. I know far more people who use Skype or AIM.

---

### Post by SunnyRabbiera on 2008-05-06
> **MarkX said:**
> Thanks for the quick reply! 
Windows messenger voice support is now the only thing stopping me and numerous others running 100% Ubuntu. I wish Canonical would get involved in changing this major setback to uptake...

You are placing the blame on the wrong people pal, it is MICROSOFT that needs to step up to the plate.
They have threatened us, they have intimidated us, if it is anyone who you should point your blame it is Microsoft... they WANT you to be dependent on them, they WANT you to use their products.
If Microsoft wants market dominance they will get it, they want you to be tied to their software and they dont want you to use anything else...
REMEMBER, we can only do so much without the help of such companies like Microsoft who wish to be greedy and not wanting to share...

I am not shouting at you, I am adding emphasis.

---

### Post by mister_pink on 2008-05-06
You say there is no linux program that will do this, but have you tried aMSN or kopete? I know they both do video, so I'd be surprised if they didnt do audio too.

---

### Post by T-Virus on 2008-05-06
Do not forget to try aMSN. I found it a quite awesome alternative.

---

### Post by MarkX on 2008-05-06
> **aysiu said:**
> I wish Microsoft would get involved in changing this setback to uptake.

I don't know anyone who uses Windos Live Messenger, though, so I don't know how major a setback it is. I know far more people who use Skype or AIM.

Everyone I know uses WLM, in fact I'm the only one even using Linux apart from two noobs I've converted. Looking at numerous forums though it's what's holding back loads of people. In amsm it's top of the list for wanted features.

---

### Post by MarkX on 2008-05-06
> **SunnyRabbiera said:**
> You are placing the blame on the wrong people pal, it is MICROSOFT that needs to step up to the plate.
They have threatened us, they have intimidated us, if it is anyone who you should point your blame it is Microsoft... they WANT you to be dependent on them, they WANT you to use their products.
If Microsoft wants market dominance they will get it, they want you to be tied to their software and they dont want you to use anything else...
REMEMBER, we can only do so much without the help of such companies like Microsoft who wish to be greedy and not wanting to share...

I am not shouting at you, I am adding emphasis.

I know it's Micro$cam, but there must be a way around it surely?
Legally, the EU seem to not be afraid of tackling them for anti-competitive practices.

---

### Post by MarkX on 2008-05-06
> **mister_pink said:**
> You say there is no linux program that will do this, but have you tried aMSN or kopete? I know they both do video, so I'd be surprised if they didnt do audio too.

They are working on it but NO linux app does voice on Live Messenger as far as I know (when I say "they are working on it" I think it's actually only a single lonesome developer, from the aMSM team). That's why I think Canonical's help might be useful to organise the various Linux messenger providers  into a concerted effort on solving it.



M$ would then keep changing the protocols so it would have to be an ongoing project.

---

### Post by aysiu on 2008-05-06
> **MarkX said:**
> That's why I think Canonical's help might be useful to organise the various Linux messenger providers  into a concerted effort on solving it. > M$ would then keep changing the protocols so it would have to be an ongoing project. I think this last sentence here should show you why it's not up to Canonical to solve this problem. Microsoft is deliberately not playing nice.

---

### Post by MarkX on 2008-05-06
> **aysiu said:**
> I think this last sentence here should show you why it's not up to Canonical to solve this problem. Microsoft is deliberately not playing nice.

It's not "up to" anyone to do anything in Linux, but Canonical's help in this would boost uptake.
I keep coming across this voice thing as the main reason why husbands/boyfriends won't put their families/kids/girlfriends onto Linux. It's sure stopping me putting it on numerous people's computers, and the only reason I still have XP wasting drive space.

---

### Post by lswest on 2008-05-06
aMSN runs on the Windows Messenger protocol, and offers support for audio and visual chat.  It works fine for me (though, admittedly, i don't use audio - no good quality microphone).```
sudo apt-get install amsn
```

I do believe it offers audio support, because you can go to (in a chat window) edit-->edit audio and video settings, and select your microphone & video device.  Maybe give it a thorough look-through?

*EDIT* hmm, a quick google showed that it's not officially supported yet (should be in the next release though) but i did see this [article]("http://amsn.sourceforge.net/devwiki/tiki-index.php?page=Installing+Plugins+and+Skins#linphone"), maybe have a read through it?  Or maybe [this]("http://llbb.wordpress.com/2008/01/01/amsn-with-audio-support-snack-on-fedora-8/")?

*Last edit* also saw this, looks promising: [http://www.amsn-project.net/forums/viewtopic.php?t=4799](http://www.amsn-project.net/forums/viewtopic.php?t=4799)

---

### Post by MarkX on 2008-05-06
> **lswest said:**
> aMSN runs on the Windows Messenger protocol, and offers support for audio and visual chat.  It works fine for me (though, admittedly, i don't use audio - no good quality microphone).```
sudo apt-get install amsn
```

it offers voice *clips* but not live voice conversations on WLM.

---

### Post by lswest on 2008-05-06
> **MarkX said:**
> it offers voice *clips* but not live voice conversations on WLM.

i just edited my above post with 3 threads that claim they got audio working in aMSN, so maybe have a look at those, i'd start with the last edit, seems to be the most recent and likely to work.

---

### Post by quinnten83 on 2008-05-06
> **mister_pink said:**
> You say there is no linux program that will do this, but have you tried aMSN or kopete? I know they both do video, so I'd be surprised if they didnt do audio too.

amsn doesn't do audio for live chats
or winks you can send them, but if there is a way to view them, I haven't found it.
it does log you camsessions tough, which is nice :D.

---

### Post by Martje_001 on 2008-05-06
MSN Live:
> The combined Windows Live Installer does not work. Therefore, to install the software, do the following:

   1. Set your Windows Ver to Windows XP (in winecfg)
   2. Download the Raw MSI file from [http://www.vistax64.com/windows-live/92348-windows-live-beta-2-suite-downloads.html](http://www.vistax64.com/windows-live/92348-windows-live-beta-2-suite-downloads.html)
   3. msiexec /i filename.msi
   4. Start Messenger, it will crash
   5. Restart messenger, it will now start (but crash on exit). 
Worth to try?

---

### Post by Kinst on 2008-05-06
Unfortunately, no one has ever had any success with the actual MSN/WLM program in wine as far as I know.

---

### Post by aysiu on 2008-05-06
This is why I'm against people straight-up trying to switch people to Linux. The first step of the migration should be a switch to sensible, cross-platform (but preferably open source) Windows applications. A user who uses Thunderbird, Firefox, Songbird, Skype, and OpenOffice in Windows is going to have a much easier time switching to Linux than a user who uses Outlook, Internet Explorer, Windows Media Player, Windows Live Messenger, and Microsoft Office will.

MarkX, you say everyone you know uses Windows Live Messenger? How about getting them to switch to something else (but still stay with Windows)?

---

### Post by MarkX on 2008-05-06
> **lswest said:**
> i just edited my above post with 3 threads that claim they got audio working in aMSN, so maybe have a look at those, i'd start with the last edit, seems to be the most recent and likely to work.

Had a look at that, thanks. It looks like it's in the pipeline, so when/if they bring it out in the next version I'll be the first to download it. 

Seems wrong though, that one lonely developer (kakaroto) is doing what countless people are asking for. Can't someone help the guy?

---

### Post by MarkX on 2008-05-06
> **aysiu said:**
> This is why I'm against people straight-up trying to switch people to Linux. The first step of the migration should be a switch to sensible, cross-platform (but preferably open source) Windows applications. A user who uses Thunderbird, Firefox, Songbird, Skype, and OpenOffice in Windows is going to have a much easier time switching to Linux than a user who uses Outlook, Internet Explorer, Windows Media Player, Windows Live Messenger, and Microsoft Office will.

MarkX, you say everyone you know uses Windows Live Messenger? How about getting them to switch to something else (but still stay with Windows)?

Impossible, unfortunately, there are just too many. The wife's friends+family are all over the place. It's how they all stay in touch over long distances.

---

### Post by aysiu on 2008-05-06
> **MarkX said:**
> Impossible, unfortunately, there are just too many. The wife's friends+family are all over the place. It's how they all stay in touch over long distances.
That's unfortunate.

Well, this leaves you with a few options, I guess: [list][*]Dual boot Windows [*]Give that lone developer some money [*]Don't use Windows Live Messenger[/list]

---

### Post by billgoldberg on 2008-05-06
> **aysiu said:**
> This is why I'm against people straight-up trying to switch people to Linux. The first step of the migration should be a switch to sensible, cross-platform (but preferably open source) Windows applications. A user who uses Thunderbird, Firefox, Songbird, Skype, and OpenOffice in Windows is going to have a much easier time switching to Linux than a user who uses Outlook, Internet Explorer, Windows Media Player, Windows Live Messenger, and Microsoft Office will.

MarkX, you say everyone you know uses Windows Live Messenger? How about getting them to switch to something else (but still stay with Windows)?

I have no idea what part of the world you are from, but here in W-EU everyone uses windows live messenger.

The vast majority of people haven't even heard about AIM, ICQ, Google Talk, or things like that.

---

### Post by aysiu on 2008-05-06
> **billgoldberg said:**
> I have no idea what part of the world you are from, but here in W-EU everyone uses windows live messenger.

The vast majority of people haven't even heard about AIM, ICQ, Google Talk, or things like that. Maybe that is the problem. I live in the US (California). I know literally no one who has made it publicly known she uses Windows Live Messenger. The only program I hear about from my Windows-using friends is Skype.

---


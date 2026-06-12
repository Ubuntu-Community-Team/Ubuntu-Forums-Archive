---
title: "Attempting to eliminate last reliance on Windows (iTunes, Office 365, OneDrive)"
date: 2022-12-05
forum: New to Ubuntu
---

### Post by geesloper on 2022-12-05
[FONT=Calibri]Helloall,

[/FONT]
[FONT=Calibri]I'm not *completely* new to Ubuntu - every couple ofyears, I'll set up a dual boot on my personal computers and see how much of mysoftware I can get to work in Linux. This time round I've been pleasantlysurprised about how much progress I've been able to make, to the extent thatI've made Ubuntu the 'main' OS on my laptop, and reduced Windows to just a verybasic setup with a couple of key items of software. I've done quite a bit ofgoogling over the past few weeks to try and eliminate this last bit of relianceon Windows, without much luck, so that's what I wanted to run by the communityhere.[/FONT]

[FONT=Calibri]I'm notbrave enough to try this on my (gaming) desktop - there are a handful ofmy games that are very cranky about Linux (even with Valve's proton), but I'dconsider it a big win if I could sort the laptop out.[/FONT]
[FONT=Calibri]
***Main Issues***
[/FONT]
[FONT=Calibri]**_ iTunes_**[/FONT]
[FONT=Calibri]To a large extent, I only use iTunes to manage podcast subscriptions and keep those subscriptions synchronized across devices. I thought I'd found a solution in the form of gpodder, but it looks like gpodder.net hasn't been accepting new accounts for a few months, and might (possibly) have been abandoned. No judgement, I realize it's run by volunteers! I also tried using PlayOnLinux toinstall iTunes, but I couldn't get it to work, even with the older 32-bit versions.  I'm also wary of this as a solution, because then I'd be at the mercy of Apple deciding to deprecate the older versions. I considered Spotify as well, but some of my podcasts need to be manually added by URL, so that was a no-go.[/FONT]

[FONT=Calibri]**_Office_**[/FONT]
[FONT=Calibri]For both work and personal purposes, I need to be able open and run XLSM and XLSB files, without compromising or corrupting them. Office 365 (Web) is fine for everything else, of course.


For both of these, I did consider setting up a VM but I'm not thrilled at the idea of having to pay MS another license fee, just for a VM.[/FONT]
[FONT=Calibri]

[B][I]Nice-to-have
[/I][/B][/FONT]
[FONT=Calibri]_**OneDrive**_
I can use the web interface, but there are some things that are backed up here that I'd like to mirror into folders in my Ubuntu install, for various reasons (photos, music, and a couple of data folders for games and applinks that I symlink in Windows). I did consider moving it all to Google Drive, but a) I'm already paying for expanded OneDrive storage because I pay for my family's Office 365, b) I'd lose the tidy integration with Windows, which is important for my work computer and my gaming PC, and c) it *seems* like the Google Drive integration in Ubuntu 'streams' - that is, I haven't found a way to force certain folders to always be available offline, and/or to be mounted or symlinked to a specific location.[/FONT]
[FONT=Calibri]
[/FONT]

Any insights would be very much appreciated! For now, dual-booting is fine, but it seems like overkill for literally two or three items of software.


Brett

---

### Post by ian-weisser on 2022-12-05
iTunes: You are correct -- the Windows version does not run in a Linux environment. The problem is not with the Wine developers, who would love to make it work. Apple has made the decision --and actively put their engineering power behind it-- that iTunes shall not work on Linux. You're out of luck if you want to use iTunes. Happily, gpodder is but one option among many Linux-native podcast managers. Try a few others.

Office: For all of Microsoft's recent changes of character to be friendlier to the open source community, Office deliberately maintains their vendor lock-in. Microsoft has not released their implementation of MSOOXML, nor clarified the vague ares of that standard. So we don't know what secret sauce they use that prevents corruption and misformatting. The LibreOffice engineers have been trying to untangle the mysteries and deliberate obfuscations of MSOOXML for a decade. You might be stuck there.

OneDrive: You are correct that support by all the large platforms for Linux is shaky. It comes and goes. Open source developers work miracles with what they have...and occasionally the large platforms sabotage those miracles. Google, for example, does not have a Linux client for Drive -- whatever you were using, it was a workaround that used their limited public API (which is why it lacked features that you sought).

Since you need both Office and OneDrive for both personal and business, seems like you're already fully locked into Windows. You can get out of that hole, but it won't be easy or fast.

---

### Post by geesloper on 2022-12-05
> [COLOR=#000000]Since you need both Office and OneDrive for both personal and business, seems like you're already fully locked into Windows. You can get out of that hole, but it won't be easy or fast.[/COLOR]

Yea, that's where my thinking is at. It's super frustrating, because I can get 95% of what I need to work. I just wanted to check with the experts, to see if there's anything I've missed. I guess there's no harm in dual booting, or running a non-activated VM version of Windows.

> [COLOR=#000000]Google, for example, does not have a Linux client for Drive -- whatever you were using, it was a workaround that used their limited public API (which is why it lacked features that you sought).

[/COLOR]Just the Gnome integration in Ubuntu, but that seems to be more of a loose API-based interface, rather that strictly a sync client.

> [COLOR=#000000]Happily, gpodder is but one option among many Linux-native podcast managers. Try a few others.[/COLOR]
gpodder looks perfect on paper, but it seems you can't currently create new accounts on gpodder.net, so no way to synchronize the subscriptions cross-platform. The other options I've found either don't have a Windows version and/or don't allow sync.

---

### Post by donald187 on 2022-12-05
I have Pocket Casts on my Android phone.  There's a snap Pocket Casts which I have not tried.  If you subscribe to Pocket Casts Plus for 99 cents per month they say it will sync across all your devices.  I haven't tried Pocket Casts Plus but I have used the Android app and it works well.  At least it did a couple of years ago when I was using it regularly.

[https://pocketcasts.com/plus/](https://pocketcasts.com/plus/)

---

### Post by geesloper on 2022-12-05
> **donald187 said:**
> I have Pocket Casts on my Android phone.  There's a snap Pocket Casts which I have not tried.  If you subscribe to Pocket Casts Plus for 99 cents per month they say it will sync across all your devices.  I haven't tried Pocket Casts Plus but I have used the Android app and it works well.  At least it did a couple of years ago when I was using it regularly.

[https://pocketcasts.com/plus/](https://pocketcasts.com/plus/)

Thanks, will investigate! :)

---

### Post by donald187 on 2022-12-05
[https://snapcraft.io/pocket-casts](https://snapcraft.io/pocket-casts)

I should have posted this link before.

---

### Post by donald187 on 2022-12-05
Here's a little more about the Pocket Casts snap.  It's not packaged by the Pocket Casts team but by another developer.  I don't know if that should be a factor or not.

[https://github.com/felicianotech/pocket-casts-desktop-app](https://github.com/felicianotech/pocket-casts-desktop-app)

---

### Post by ActionParsnip on 2022-12-05
You can use MS Office in your browser too. Works well

---

### Post by geesloper on 2022-12-06
Thanks for the tips, all - I ended up finding a Win11 license on special, and used that to create a VM just for Office :P

I actually did manage to get Office 365 to *open* using CrossOver, but none of the critical functionality worked (external data connections, macros etc).

Pocket Casts has solved the iTunes problem, though :-)

---

### Post by Tadaen_Sylvermane on 2022-12-06
> Apple has made the decision --and actively put their engineering power behind it-- that iTunes shall not work on Linux.

Indeed. One could argue that it wouldn't even be on Windows if they could help it. Market share to big to pass up though...

For Office 365 is the online version not enough? I use Google Docs when I have to but honestly my usage is very low level so it's not lacking for me.

---

### Post by geesloper on 2022-12-06
> **Tadaen_Sylvermane said:**
> For Office 365 is the online version not enough? I use Google Docs when I have to but honestly my usage is very low level so it's not lacking for me.

Unfortunately not :-( A lot of the Excel files from my work in particular have macros and/or external data connections, neither of which will run on the web. Maddening, because of course things like GoogleDrive *will* let you do those things.

---

### Post by donald187 on 2022-12-06
> **geesloper said:**
> 
Pocket Casts has solved the iTunes problem, though :-)
Nice!

---

### Post by TheFu on 2022-12-06
Every time I've been asked or tried to ween myself from MS-Windows, the normal best answer was to drop/stop using proprietary code on MS-Windows first.  There are lots of F/LOSS tools that run on all 3 platforms, so start by switching to those tools on Windows first.

As long as you are tied to proprietary code and proprietary data formats, those companies have you by the balls.   Their cloudy servers are just a bad - well - all cloudy servers are bad, but getting away from MSFT cloud stuff would be a critical step.

Even after all this work, you'll likely need an MS-Windows instance available a few times a year. I have one that is in a virtual machine to do financial tracking, decisions and taxes.  18 months ago, I was still using MS-Windows for video editing, but that all ended as some new software finally became good enough for my needs.  So about every 2 weeks, I boot that Windows virtual machine, spend 5-15 minutes using it, save a backup file of the new data to a Linux system and shut down the VM.  During tax season, it is booted for a few hours a day for about 5 days.

The rest of my time is spent happily in Linux, with a smile.

At some point, I'll be forced to a new version of MS-Windows when the tax program I use stops working.  I have no plans to change the stock and other proprietary financial account tool that I've been using and stopped updating in 2011, but I might be forced to change. When that happens, I'll switch to a F/LOSS tool and "embrace the suck."  It is likely that I'll need to write my own stock management tool, since 'beancounter' has died off.  A little tool like that is about the same size as my TV schedule and recording tools - another itch I needed to scratch.  Of course, these are personal projects that will never to shared. Far too many little issues that only work with my exact needs, but would likely break on anyone else's system if there is a slight breeze. ;)

Dump proprietary software, data formats, and proprietary cloud tools. That's step 2, after admitting you have a problem, which is step 1. ;)

BTW, I moved my mother off Windows onto Linux using this method.  She had been using F/LOSS tools for years, so when the OS was changed underneath, her fears - she was really afraid - all went away.  Firefox is firefox.  Thunderbird is Thunderbird.  LibreOffice is LibreOffice.  I even got Quicken working under WINE for her and she was happy about that. I think the version of Quicken she had was the last one that ever worked under WINE, however.  Mom never stored anything on cloudy storage or the internet.

---


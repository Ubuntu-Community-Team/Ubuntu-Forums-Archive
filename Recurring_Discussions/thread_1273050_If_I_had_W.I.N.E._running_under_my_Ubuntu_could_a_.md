---
title: "If I had W.I.N.E. running under my Ubuntu could a Windows Virus wreck my Ubuntu?"
date: 2009-09-22
forum: Recurring Discussions
---

### Post by Goveynetcom on 2009-09-22
If I had W.I.N.E. running under my Ubuntu could a Windows Virus wreck my Ubuntu? Sorry if this is a really noobish question I'm just beginning to really use my newly installed Ubuntu. I have a Windows XP Machine, but I was wondering if Ubuntu would be unsucceptble to Windows Virus if it had run under W.I.N.E. I ask because I have gotten a virus or two before on Windows and they can occasionally just destroy Windows. My main use for W.I.N.E. would be for Photoshop (Yes I know that their is GIMP, and I already use it too) and maybe Flash, possibly some emulators (Videogame emulators are just better on Windows). Thanks for any help you have.

- Your, Pal Goveynetcom :popcorn:

---

### Post by scragar on 2009-09-23
There have been numerous attempts to run a few different viruses in ubuntu via wine, and the closest thing to success reported was that one virus eat up a good chunk of processing power with some form of infinite loop until it was killed.
No virus running on wine to the best of my knowledge has ever been able to damage anything.

---

### Post by Goveynetcom on 2009-09-23
Few, that is a load off my back. Thanks for the info.

---

### Post by dvlchd3 on 2009-09-23
It is very likely that virus will be able to run under wine, however, they will stay in the wine directory (~/.wine).  If you ever suspect you have a virus running under wine, you can simply remove that directory, and restore it from a known good backup.

---

### Post by The Cog on 2009-09-23
Many viruses don't run in wine because they try to do things that bypass the normal win32 API which is what wine supports. Some malware could conceivably run though. And the default wine install maps / to Z: so that malware would have the same read/write access to the Linux system as the user running wine has. It could read and perhaps delete or overwrite all the users documents for instance. If it was smart, it could figure out it was in wine and then (for instance) then drop bash scripts in ~/.bashrc to run next time you log in. This is all unlikely (unheard of even), but theoretically possible.

---

### Post by snakeman21 on 2009-09-23
Windows viruses--and programs--are tailored for a Windows environment.  They need the windows directories such as C:/Windows to grow and cause damage.  Wine creates a virtual C: drive, thereby allowing Windows programs (and occasionally, viruses) to run.  But because the virtual C: drive is essentially nothing but a directory inside your Linux install, the virus will not recognize your other directories, and will be confined to the Wine directory, making it easy to eradicate.  

If, somehow, the virus was able to get to your Linux directories, it would be stopped in its tracks, as Linux requires manual user permission to install new software, not to mention the fact that .exe files *can't* run on Linux except in the wine directory.  Trust me, your safe.  Periodically, make backups of your Wine directories.  That way, in the unlikely event of a virus, you can just delete them and paste your backups there, erasing the virus.

EDIT:  And don't worry about asking n00b questions... That's how we learn!

---

### Post by HermanAB on 2009-09-23
See the Codeweavers web site for a white paper on viruses and WINE.

---

### Post by imbjr on 2009-09-23
> **dvlchd3 said:**
> It is very likely that virus will be able to run under wine, however, they will stay in the wine directory (~/.wine).  If you ever suspect you have a virus running under wine, you can simply remove that directory, and restore it from a known good backup.

Actually, if you look at your default Wine install you will see a Z drive mapped to the root directory. So WINEd software CAN see your Linux files.

---

### Post by SunnyRabbiera on 2009-09-23
No windows viruses will not work in general under linux, and wine is not a part of the core OS.
Also you are not browsing the net using wine right?

---

### Post by hoppipolla on 2009-09-23
I wondered about this one too!

A while back I used to like trying to run viruses under Linux with Wine just out of curiosity, and nothing ever happened (I also tried some really bad ones as well, but no still nothing).

That's worrying though if Wine maps / to Z:... especially if you have root privileges. In theory then a virus could do damage...

Maybe the lesson is just to run Wine as your normal user when possible :)

---

### Post by coldReactive on 2009-09-23
> **imbjr said:**
> Actually, if you look at your default Wine install you will see a Z drive mapped to the root directory. So WINEd software CAN see your Linux files.

This is to make sure you can execute windows apps on your desktop without problem. ;)

That's why removing the Z: you have to download all exe files into drive_c.

---

### Post by bobince on 2009-09-24
A Windows virus running through WINE can do the same things as a Linux virus you're running as a normal user: it can trash your documents and settings and leak privacy-sensitive information, but it can't root the OS. In practice little current malware will “work” well under WINE, but it's certainly doable if someone were to write malware that specifically targeted it.

If you're concerned about guest-OS security affecting the host, you'd probably be better off running a Windows installation in Virtualbox. Then you can take a copy of the virtual machine in a known-good state, and simply trash and replace any time the guest gets infected.

---

### Post by Chronon on 2009-09-24
> **coldReactive said:**
> This is to make sure you can execute windows apps on your desktop without problem. ;)

That's why removing the Z: you have to download all exe files into drive_c.

or from your optical drive.  Is mounting your root directory only for this convenience?  It seems to me that confining all windows executables to drive_c is preferable anyway.

---

### Post by coldReactive on 2009-09-24
> **Chronon said:**
> or from your optical drive.  Is mounting your root directory only for this convenience?  It seems to me that confining all windows executables to drive_c is preferable anyway.

Wine should auto-detect your optical drives, USB Drives, etc. as drives other than Z. Report a bug if it doesn't (IE: PSP)

---

### Post by potat on 2009-09-24
Basically, for a Wine virus to do any damage, it would have to be a virus designed specifically for Wine and not a generic Windows virus. This is incredibly unlikely, but theoretically possible. And it could still only have access to the files of the user running Wine.

If you are really worried about it, you can always un-map the Z: drive in the WINE settings. Then if you need Wine to access files on your filesystem, you can copy, move, or symlink them somewhere in Wine's virtual C: drive ( ~/.wine/dosdevices/c: ).

---

### Post by Chronon on 2009-09-24
> **coldReactive said:**
> Wine should auto-detect your optical drives, USB Drives, etc. as drives other than Z. Report a bug if it doesn't (IE: PSP)

Sorry.  I wasn't clear.  My dvd drive is mapped to a unique drive letter.  So, removing Z: from the virtual file system that WINE inhabits should still allow you to run software off of your optical drives, etc.

Time for the morning cuppa, I think.  ;)

EDIT: For the poster upthread, I can think of no compelling reason to ever run Windows software as root.

---

### Post by psihokiller4 on 2010-10-15
> **The Cog said:**
> Many viruses don't run in wine because they try to do things that bypass the normal win32 API which is what wine supports. Some malware could conceivably run though. And the default wine install maps / to Z: so that malware would have the same read/write access to the Linux system as the user running wine has. It could read and perhaps delete or overwrite all the users documents for instance. If it was smart, it could figure out it was in wine and then (for instance) then drop bash scripts in ~/.bashrc to run next time you log in. This is all unlikely (unheard of even), but theoretically possible.


I think this is best answer for this Q
and thanks man
saying how could damage is better than how can't ;)

now I know I'm still on safe side if I use wine
thanks

---

### Post by alexan on 2010-10-17
...or more simply, see the [reference](http://cdn0.knowyourmeme.com/i/28453/original/necropost.jpg?1259372901)

---

### Post by kio_http on 2010-10-17
> **potat said:**
> Basically, for a Wine virus to do any damage, it would have to be a virus designed specifically for Wine and not a generic Windows virus. This is incredibly unlikely, but theoretically possible. And it could still only have access to the files of the user running Wine.

If you are really worried about it, you can always un-map the Z: drive in the WINE settings. Then if you need Wine to access files on your filesystem, you can copy, move, or symlink them somewhere in Wine's virtual C: drive ( ~/.wine/dosdevices/c: ).

This plus it could do the job it was supposed to do with Wine itself. E.g replace a dll to cause windows to crash, on wine this will probably make wine crash.

---

### Post by beew on 2010-10-17
Fortunately most Windows programs don't run well in WINE even if intended. If you ever get infected by a virus through WINE you may want to post it on the list at WINE hq and give it a gold or platinum.

---

### Post by blueturtl on 2010-10-25
Don't mean to sound alarming, but at least in my Ubuntu installs, if not modified the WINE default configuration will map your /home directory to some popular Windows equivalent "My Documents" folders. Because WINE is being run with your user privileges it could potentially erase all your data for example. This is why I always barricade WINE from having access to anything but the .wine subfolder. Anything run inside will stay inside.

The Ubuntu WINE defaults are unsafe for promiscuous use. Either use the same care you would running Windows, or then unmap your own user and root directories!

---

### Post by gregzeng on 2010-10-26
> **alexan said:**
> ...or more simply, see the [reference](http://cdn0.knowyourmeme.com/i/28453/original/necropost.jpg?1259372901)

The above reference led me to a meaningless (anti AIDS?) advertisement.  

Most people commenting here seem to be unaware that CLAM-AV exists in Linux, including Ubuntu.  The major danger as I see it, is not that my AVI, web-page-saved file, or whatever affects my Linux computer.  But if I refer it onto someone who opens up in a Windows computer, it will malware THEIR computer, and then BLAME ME for wrecking their computer.

Sorry - I'm not an island; dumb and solitary.  But I do receive web-pages that I sometimes refer all or part of them onto other people I know.

btw:  the above rubbish web site MIGHT be such a malware site.  Luckily I opened it in Ubuntu.  Not sure if anyone used a windows operating system to open that possibly dangerous URL.

Retired (medical) IT Consultant
Australian Capital Territory

---

### Post by julio_cortez on 2010-11-05
> **blueturtl said:**
> Either use the same care you would running WindowsIf everyone used the same care in WINE that they use in Windows, we'd be busted in no time.

Anyway, user permissions exist for a reason:  I consider WINE a safe way to test things you're not really sure of for the exact reason that it can't go outside his **/home/*yourname*/.wine** folder.
If you, while you run something in WINE, get a virus to screw your / directory, this is probably due to something misconfigured because of a PEBKAC.

---


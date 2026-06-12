---
title: "HowTO: Adobe Photoshop CS2 in Wine!"
date: 2006-10-11
forum: Outdated Tutorials &amp; Tips
---

### Post by Old Pink on 2006-10-11
It's the guide you've all been waiting for! :D

But I didn't write it...

[http://blog.publicidadpixelada.com/2006/10/10/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/](http://blog.publicidadpixelada.com/2006/10/10/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/)

---

### Post by Old Pink on 2006-10-11
Finally... there's a way. :cool:

[http://blog.publicidadpixelada.com/2006/10/10/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/](http://blog.publicidadpixelada.com/2006/10/10/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/)

Surely this will put a not-so-tragic end to some people's windows partitions? :D

---

### Post by maniacmusician on 2006-10-11
hmm, shouldnt this be in the howto section?
[SIZE=1]      ---merged into duplicate in howtos : PriceChild[/SIZE]


anyways, really cool link, thanks for posting

---

### Post by %hMa@?b&lt;C on 2006-10-11
cool link. if i had a windows box and a copy of CS2 I would try it.

---

### Post by skyshock21 on 2006-10-11
Nope, sorry, it doesn't work.

When you try to recode that .reg file this is what will happen:

```
recode: adobe.reg failed: Untranslatable input in step `ISO-10646-UCS-2..ANSI_X3.4-1968'

```

I tried to open that file w/ Gedit and just add ucs-2 encoding and chose it.  Then I copied/pasted all the text into a new file and imported it.  It seemed to import fine, but when you run Photoshop you get this...

```
err:shell:HCR_GetFolderAttributes HCR_GetFolderAttributes should be called for simple PIDL's only!
fixme:keyboard:UnregisterHotKey (0x10024,99): stub
fixme:keyboard:RegisterHotKey (0x10024,99,0x00000000,27): stub
fixme:keyboard:UnregisterHotKey (0x10024,99): stub
fixme:ole:CoSuspendClassObjects
fixme:keyboard:RegisterHotKey (0x10024,99,0x00000000,27): stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:keyboard:UnregisterHotKey (0x10024,99): stub
fixme:keyboard:RegisterHotKey (0x10024,99,0x00000000,27): stub
fixme:keyboard:UnregisterHotKey (0x10024,99): stub
fixme:keyboard:RegisterHotKey (0x10024,99,0x00000000,27): stub

```

Then the program tells you it's unregistered (it's a registered version on my windows machine) and closes abruptly.  You can't recode the registry file the way that guy specifies, so until we have that missing piece of info. mark this as inaccurate.

---

### Post by PriceChild on 2006-10-12
*merges threads*

---

### Post by slynki on 2006-10-12
I had the same issue recoding the .reg file. 
I went back to windows and opened the .reg file in notepad then saved in utf-8 encodeing. Returned to Ubuntu and ran it; $wine regedit adobe.reg
It worked.
I do have other issues though.

---

### Post by skyshock21 on 2006-10-12
Supposedly this has worked to help people import that .reg file but it still won't import for me... 

[http://appdb.winehq.org/commentview.php?iAppId=17&iVersionId=2631&iThreadId=10902](http://appdb.winehq.org/commentview.php?iAppId=17&iVersionId=2631&iThreadId=10902)

---

### Post by skyshock21 on 2006-10-12
Okay guys, I've come about as close as I've ever come tonight.  I went on to my favorite Bit Torrent site and picked up a little app someone hacked together called Portable Photoshop CS2.  It's got everything contained in one package.  I'm sure it's illegal as hell, but it's all in the name of spreading information and learning how stuff works you know?  You just have to import the ONE registry key they provide using 

```
wine regedit.exe PSCS2.reg
```

Then when I run the Photoshop.exe using wine, it opens and I don't get that message saying it's an unregistered version, however it hangs up.  I can post the last bit of command line output if anyone's interested.

---

### Post by Old Pink on 2006-10-13
> **maniacmusician said:**
> hmm, shouldnt this be in the howto section?
[SIZE=1]      ---merged into duplicate in howtos : PriceChild[/SIZE]


anyways, really cool link, thanks for posting

> **PriceChild said:**
> *merges threads*

Yeah, sorry about that. I figured it wouldn't get through HowTO moderation as it was purely a link.

Probably should've waited before making a duplicate, but if your HowTO gets rejected you don't get notified, so.... :rolleyes:

---

### Post by skyshock21 on 2006-10-13
> **slynki said:**
> I had the same issue recoding the .reg file. 
I went back to windows and opened the .reg file in notepad then saved in utf-8 encodeing. Returned to Ubuntu and ran it; $wine regedit adobe.reg
It worked.
I do have other issues though.

I think I'll try this method as well.  What are the other issues you're having?  Does it have anything to do with the fonts?

---

### Post by slynki on 2006-10-13
skyshock21 - No, I don't think I am having any issues with the fonts. I have photoshop running in Ubuntu, but when it loads I get a message about missing registration info. I checked it out and the needed info is missing from the .reg file. I need to go back to windows and track it down. It's probably located under HKEY_CURRENT_USER instead of HKEY_LOCAL_MACHINE.

---

### Post by computergee on 2006-10-14
The registry key with the registration info is in:
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall\{EFB21DE7-8C19-4A88-BB28-A766E16493BC}, the last part may be different for you though.

I am past the registration error, but it says I don't have permission to run program, I still need a fix for that.

---

### Post by alphagamma on 2006-10-21
Ok. I just followed this guide, and it worked... once. 

i rebooted and try to run photoshop thru wine, it loads, hangs at the plugins for a minute, finishes loading and then i get an error:
"Unable to continue because of a hardware or system error.
Sorry bit this error is unrecoverable"


any ideas?

---

### Post by qrm on 2006-10-21
would it work for Illustrator too if it would be a lil bit altered?

Id get rid of this ol crashin winxp home from my hdd

E: at the moment I recoded the reg file with "recode ucs-2-internal adobe.reg" instead of the original ascii command. Well, i got it imported and now Ive got to look around for the Illustrator.exe file which seems nowhere to be found ](*,)

E2: found it, its in the Support Files/Contents/Windows/ catalogue

E3: now it just hangs while loading plugins. But I see the light :D

E4: trying to get Illustrator CS working, its just asking for windows dlls, google, here I come :d

---

### Post by Jbloudg20 on 2006-11-08
I pretty much have it running, but it doens't like opening files from my Linux directories. Is that a shortfall of wine, or just an incompatibility of running Photoshop?

---

### Post by Jbloudg20 on 2006-11-08
Nevermind, seems to be a problem opening jpg any ideas? It just closes as soon as I try to open a jpg.

---

### Post by BKK on 2006-11-10
Hello. I have it almost working as well.

It takes a very long time at the loading plugins section, but it eventually loads. 

I finally gives me an error about not having administrative rights to run it.

for the .reg coding what i do is export the .reg file in windows then

wine notepad adobe.reg

then save the file

then

wine regedit adobe.reg

---

### Post by iceman138 on 2006-11-10
I got Photoshop CS2 to work pretty well tonight in Edgy by exporting these two registry groups from Windows:

HKEY_LOCAL_MACHINE/Software/Adobe/
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall\{236BB7C4-4419-42FD-0409-1E257A25E34D}

I used “ucs-2..utf-8&#8243; for .reg file recode.

Photoshop loads and I can open images and modify them.  The problem I'm having now is that none of the keyboard shortcuts work, like Ctrl-A, Ctrl-D, etc.  I get a bunch of errors in the terminal regarding hotkeys.  Could this be related to the recode?

fixme:keyboard:UnregisterHotKey (0x10024,99): stub
fixme:keyboard:RegisterHotKey (0x10024,99,0x00000000,27): stub


Anyone run into this problem?

---

### Post by Jeom123 on 2006-11-17
Hmmm...

I get the following problem:

“johan@johan-desktop:~/.wine/c/Program Files/Adobe Photoshop CS2$ sudo wine –winver winxp Photoshop.exe
Password:
wine: could not load L”c:\\windows\\system32\\\2013winver.exe”: Module not found”

Winver.exe is there. Anyone having the same problem or a solution?

---

### Post by Turin Turambar on 2006-11-19
No, PS still displays the same message: user, organisation, blah blah is not good and it needs to close!

---

### Post by neorush on 2006-11-22
Also fix this reg file convert problem with 
wine notepad adobe.reg
file -> save
then do your import

---

### Post by baalthazar on 2006-11-28
greetings people!

im kinda having a bit of problems trying to install photoshop cs2 to ubuntu **[[COLOR="Red"]following this tutorial[/COLOR]]("http://blog.publicidadpixelada.com/2006/10/10/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/")**, and im stuck trying to copy the files from one place to another.. from what i know, i already have wine, but what i dont understand is how do i copy the files from the windows folder (wich i have mounted in a folder in my linux and is viewable) to home/YOURNAME/.wine/drive_c/Program Files/ (<- i know it need my username)
the main problem is that i cant get at all to that address, btw, since my windows is in spanish, would i have to change some parts of that address to spanish? and does the part of drive_c needs any relevant name or is that ok?

---

### Post by silent_scream on 2006-11-30
> **iceman138 said:**
> I got Photoshop CS2 to work pretty well tonight in Edgy by exporting these two registry groups from Windows:

HKEY_LOCAL_MACHINE/Software/Adobe/
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall\{236BB7C4-4419-42FD-0409-1E257A25E34D}

I used “ucs-2..utf-8&#8243; for .reg file recode.

Photoshop loads and I can open images and modify them.  **The problem I'm having now is that none of the keyboard shortcuts work, like Ctrl-A, Ctrl-D, etc.  I get a bunch of errors in the terminal regarding hotkeys.  Could this be related to the recode?**

fixme:keyboard:UnregisterHotKey (0x10024,99): stub
fixme:keyboard:RegisterHotKey (0x10024,99,0x00000000,27): stub


Anyone run into this problem?

I have the same prob...
I don't think it's related to recode... :-k 
any ideas?

---

### Post by Julolidine on 2006-12-17
Got it!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

All the key bindings work, only key that doesn't work is Alt/Ctrl -  at this point in time -  because Alt+Click grabs the window, I hope theres some way around it, because it would suck to be without the clone tools.

Everything works as far as I can tell...layers, curves, AKA the things I need.  Even the History works!:

:-D :-D :-D :-D :-D :-D :-D 

A dirty edgy system with a new wine (.927) or whatever the latest one is.  I have a legit copy of CS2 on my computer, and I couldn't get it to work the other way - I kept running into the same stupid "Administrator" problem.  The key was finding the USB-key version at a very 'demonic' sort of place.  From there is was simple.  Just extracted the USB-key exe from command line in the c-drive, and it automatically places itself in Program Files/Adobe/CS2

[[IMG]http://img187.imageshack.us/img187/1407/screenshotwp4.th.png[/IMG]](http://img187.imageshack.us/my.php?image=screenshotwp4.png)

Edit: Almost everything works.  I've managed to kill it once though, and it seems to die when I try to resize the palettes.  You can move them around fine, and you can even minimize/maximize, but if you manually try to do it, it dies.  Its *really* fast once it gets booted.  Feels just as smooth as windows version.  Gradients work, quick mask works....filters seem to work, although I have yet to try a really big file.  Saving definately works.  

Moral of the story is save and save often, because its still not 100%. 

Anyone know how to remap a key just inside of wine?

---

### Post by Nemesis Teufel on 2006-12-26
its the same on edgy eft?
what i have to change to work it?

The guide said that is for dapper

---

### Post by Nemesis Teufel on 2006-12-26
sorry for the double post

---

### Post by Anonii on 2006-12-27
So... Do we have a method for a working CS2?

---

### Post by Hairy_Palms on 2006-12-27
we appear to, but by the sounds of it YMMV

oh and btw, when you export your registry under windows, just save them as text files and you can import them without any hassle

---

### Post by Green_Star on 2006-12-27
I am getting following error. 

"Your Adobe Photoshop user name, organization or serial number is mising or invalid. The application cannot continue and must now exit"

any clue? I followed the same what explained in the tutorial !!

---

### Post by boast on 2007-03-01
> **Green_Star said:**
> I am getting following error. 

"Your Adobe Photoshop user name, organization or serial number is mising or invalid. The application cannot continue and must now exit"

any clue? I followed the same what explained in the tutorial !!

same here. CS2 worked fine for about 5 tries, but now it tells me this. I tried copying over any .reg's I found in guides, and I still get that problem.

I'm running it off my windows partition though. Don't want to waste space.

---

### Post by Hairy_Palms on 2007-03-04
photoshop cs2 portable version works 100% in wine, i think its legal as long as you own real photoshop. search torrent sites for it.

---

### Post by the79bomb on 2007-03-04
I got around the winver.exe error by removing the -winver winxp from the command line.

---

### Post by J-Red on 2007-03-04
Using that tutorial, it almost works. I start it up, it takes real long,then it says my serial is invalid. how do I fix this? (I did all the .reg things and copied everything)

---

### Post by Hairy_Palms on 2007-03-05
see my above post j-red

---

### Post by J-Red on 2007-03-05
How exactly does photoshop portable work?

---

### Post by proalan on 2007-03-06
very well

---

### Post by PartisanEntity on 2007-03-16
Are these instructions compatible with Edgy?

I am trying to get this to work and I have a couple questions:

1. Who should be the owner of .wine? (at the moment in my case its root).

2. What's the default charset in win xp sp2?

3. Whats the default charset of ubuntu?

4. Once you have done all these steps how do you actually launch Photoshop? I mean what is the complete command, can someone show me an example? (I saw the example listed in the How To but I would like to know exactly how the path looks like).

Thanks!

---

### Post by PartisanEntity on 2007-03-18
I managed to get it to load but I get the following message:

> You are not allowed to continue because your account does not have the proper privileges. Please log in using an account with admnistrator privileges and try again.

Anyone know where in the registry this info can be found, or wether I can edit a certain entry in 
```
wine regedit
``` 
to give myself administrator privileges?

Thanks.

---

### Post by J-Red on 2007-03-18
when I saw that, I just used sudo. It worked for me but I still couldn't get Photoshop Running properly.

---

### Post by PartisanEntity on 2007-03-19
Does anyone know which registry-key in winxp defines my winxp-user-account as having administrator privileges?

---

### Post by Sonicgoo on 2007-03-20
Takes forever to load and then it says there is a hardware error. How do we fix that?

---

### Post by Sonicgoo on 2007-03-20
So does anybody know how to get past the hardware error?

---

### Post by jfanaian on 2007-03-21
I got it working fine, my only problem is that when I minimize photoshop it leaves all the toolbars on top of any other window. Why is this? Is there a fix to it? Thanks

---

### Post by PartisanEntity on 2007-03-23
Concerning the administrator privileges issue:

Some of us have had to deal with a pop up message in Photoshop informing us that we need to run Photoshop using an account with administration privileges. Using 'sudo' did not solve this problem so the logical assumption is that this message refers to the Windows user profile data inside the WIne registry and not to your Ubuntu user profile.

I have come across a tool called RegShot, it is a freeware windows tool that makes small snapshots of the Windows registry for comparisons. This could be used to do the following:

Load up and log in to your WIndows machine or virtual machine. Install RegShot. 

Make a new Windows user account and give it administrator privileges and make a snapshot of your registry.

Then edit your account to remove its Windows administrator privileges and make another snapshot using RegShot.

Now you can compare the newer snapshot file with the older snapshot file to see what changed. This way, you will be able to perhaps identify which registry keys you need to export in order to retain administrator privileges in the Wine user profile.

Since I last posted in this thread I have reinstalled Ubuntu and have not as of yet installed Wine or vmware, so I cannot test this right now.

But I thought I would post this here in the hopes that it might help someone else.

RegShot can be found here:
[http://www.majorgeeks.com/RegShot_d965.html](http://www.majorgeeks.com/RegShot_d965.html)

---

### Post by Stickymaddness on 2007-03-26
Has anyone managed to get CS2 running 100% stable yet? I haven't had any registration problems, but it is very, very unstable...

---

### Post by cisforcojo on 2007-03-26
When using Photoshop Portable, can you use the updater? 
I'm getting errors about this. Says to re-install. 

In what ways is the photoshop portable software limited?

---

### Post by PartisanEntity on 2007-03-27
> **Stickymaddness said:**
> Has anyone managed to get CS2 running 100% stable yet? I haven't had any registration problems, but it is very, very unstable...

I have actually been forced to go back to dual booting with XP in order to use Photoshop because in Wine I kept getting that message about administrator privileges.

---

### Post by Stickymaddness on 2007-03-27
> **PartisanEntity said:**
> I have actually been forced to go back to dual booting with XP in order to use Photoshop because in Wine I kept getting that message about administrator privileges.

Yeah same here :/

---

### Post by ShinjiLeery on 2007-05-15
> **Stickymaddness said:**
> Yeah same here :/

Same here... Any news about it ?

---

### Post by Stickymaddness on 2007-05-15
> **ShinjiLeery said:**
> Same here... Any news about it ?

Nope :( I've had to settle for Photoshop 6 for the moment....

---

### Post by PartisanEntity on 2007-05-15
I still have a dual boot set up, but I have been using Gimp quite often and I am beginning to realise that for many of my needs it works as well as Photoshop so I haven't logged into my XP installation very often.

---

### Post by dankegel on 2007-09-29
As of wine-0.9.46, you don't need to jump through hoops,
just run the Photoshop CS2 installer and you're good.

If you run into trouble, try starting with a clean .wine and 
installing ms corefonts.

See also [http://wiki.winehq.org/AdobePhotoshop](http://wiki.winehq.org/AdobePhotoshop)

---

### Post by techpr on 2007-09-29
I have PS CS2 installed and runs but I cannot pass the activation step. When I click on the Activation by Phone then it shows the pop-up error in the screenshoot and I have over 35GB of free space.

I have the latest Wine 0.9.46

---

### Post by tlacuache on 2007-10-03
> **techpr said:**
> I have PS CS2 installed and runs but I cannot pass the activation step. When I click on the Activation by Phone then it shows the pop-up error in the screenshoot and I have over 35GB of free space.

I have the latest Wine 0.9.46

I'm having this same problem. The installation goes fine until I choose Activation by Phone, then I get the out of space error.

---

### Post by aldebarn42 on 2007-10-09
> **tlacuache said:**
> I'm having this same problem. The installation goes fine until I choose Activation by Phone, then I get the out of space error.

Exact same issue here! Any solutions?

---

### Post by twickline on 2007-10-09
Over this past week end I have posted four Adobe Photoshop on Linux with Wine articles, versions 6 through CS2 are covered.

The PhotoShop 6 article is located [here]("http://wine-review.blogspot.com/2007/10/photoshop-6-on-linux-with-wine.html")

The Photoshop 7 article [here]("http://wine-review.blogspot.com/2007/10/photoshop-7-on-linux-with-wine.html") 

The Photoshop CS  article [here]("http://wine-review.blogspot.com/2007/10/photoshop-cs-on-linux-with-wine.html") 

And Photoshop CS2 is [here]("http://wine-review.blogspot.com/2007/10/photoshop-cs2-on-linux-with-wine.html"). 

All four articles have code samples and lots of screen shots for new and experienced Linux users.

---

### Post by BLTicklemonster on 2007-10-30
Thank You, Twickline! :guitar:

Wow, talk about slow, then it goes unresponsive. meh, I'll keep messing around with it.

---

### Post by similas on 2007-11-08
On wine 0.9.48 works good, but shortcuts still are not working... Also type tool crashes app... Something new about it?

---

### Post by boast on 2007-11-27
> **aldebarn42 said:**
> Exact same issue here! Any solutions?

patch: [http://bugs.winehq.org/attachment.cgi?id=9132](http://bugs.winehq.org/attachment.cgi?id=9132)

[I]"Using the SCSI ATA PASSTHRU method:

Make your primary harddisk block device (/dev/hda or /dev/sda .. whatever,
owned by root) raw accessible to the wine user.
At least: chmod g+rw /dev/hda (sda), if you are in "disk" group.
If not: chmod a+rw /dev/hda (sda).
+r is not enough because the block device is unfortunately opened with default
READ_WRITE permissions requested.
Don't be scared .. "write" isn't used at all.

Make the following symlink in .wine/dosdevices: "ln -s /dev/hda c::"

Start Photoshop CS2 and wait for activation dialog. It should now show
activation code. Fill in required authorization code to activate your copy.

If successful you can remove the symlink and revoke permissions to hda/sda."[/I]

---

### Post by Takster on 2007-12-01
> **boast said:**
> patch: [http://bugs.winehq.org/attachment.cgi?id=9132](http://bugs.winehq.org/attachment.cgi?id=9132)

[I]"Using the SCSI ATA PASSTHRU method:

Make your primary harddisk block device (/dev/hda or /dev/sda .. whatever,
owned by root) raw accessible to the wine user.
At least: chmod g+rw /dev/hda (sda), if you are in "disk" group.
If not: chmod a+rw /dev/hda (sda).
+r is not enough because the block device is unfortunately opened with default
READ_WRITE permissions requested.
Don't be scared .. "write" isn't used at all.

Make the following symlink in .wine/dosdevices: "ln -s /dev/hda c::"

Start Photoshop CS2 and wait for activation dialog. It should now show
activation code. Fill in required authorization code to activate your copy.

If successful you can remove the symlink and revoke permissions to hda/sda."[/I]

Can anyone explain these terminal commands to a newbie?

I have CS2 running perfect - apart from the phone validation - which i require.
Removing the symlink and revoking the permissions, and these needed changes within /dev/hda is all new to me. Sounds a bit dangerous for a beginner.

Thanks.

---

### Post by paviaani on 2007-12-04
> **boast said:**
> patch: [http://bugs.winehq.org/attachment.cgi?id=9132](http://bugs.winehq.org/attachment.cgi?id=9132)

[I]"Using the SCSI ATA PASSTHRU method:

Make your primary harddisk block device (/dev/hda or /dev/sda .. whatever,
owned by root) raw accessible to the wine user.
At least: chmod g+rw /dev/hda (sda), if you are in "disk" group.
If not: chmod a+rw /dev/hda (sda).
+r is not enough because the block device is unfortunately opened with default
READ_WRITE permissions requested.
Don't be scared .. "write" isn't used at all.

Make the following symlink in .wine/dosdevices: "ln -s /dev/hda c::"

Start Photoshop CS2 and wait for activation dialog. It should now show
activation code. Fill in required authorization code to activate your copy.

If successful you can remove the symlink and revoke permissions to hda/sda."[/I]

it doesn't work :(

---

### Post by hieund on 2007-12-21
>  Originally Posted by boast  View Post
patch: [http://bugs.winehq.org/attachment.cgi?id=9132](http://bugs.winehq.org/attachment.cgi?id=9132)

"Using the SCSI ATA PASSTHRU method:

Make your primary harddisk block device (/dev/hda or /dev/sda .. whatever,
owned by root) raw accessible to the wine user.
At least: chmod g+rw /dev/hda (sda), if you are in "disk" group.
If not: chmod a+rw /dev/hda (sda).
+r is not enough because the block device is unfortunately opened with default
READ_WRITE permissions requested.
Don't be scared .. "write" isn't used at all.

Make the following symlink in .wine/dosdevices: "ln -s /dev/hda c::"

Start Photoshop CS2 and wait for activation dialog. It should now show
activation code. Fill in required authorization code to activate your copy.

If successful you can remove the symlink and revoke permissions to hda/sda."
it works perfectly with me

---

### Post by Rizado on 2007-12-22
> **paviaani said:**
> it doesn't work :(Didn't work for me either, but the second method works great!

[http://bugs.winehq.org/show_bug.cgi?id=10018#c16](http://bugs.winehq.org/show_bug.cgi?id=10018#c16)

---

### Post by toastysquirrel on 2008-01-28
> **boast said:**
> patch: [http://bugs.winehq.org/attachment.cgi?id=9132](http://bugs.winehq.org/attachment.cgi?id=9132)

[I]"Using the SCSI ATA PASSTHRU method:

Make your primary harddisk block device (/dev/hda or /dev/sda .. whatever,
owned by root) raw accessible to the wine user.
At least: chmod g+rw /dev/hda (sda), if you are in "disk" group.
If not: chmod a+rw /dev/hda (sda).
+r is not enough because the block device is unfortunately opened with default
READ_WRITE permissions requested.
Don't be scared .. "write" isn't used at all.

Make the following symlink in .wine/dosdevices: "ln -s /dev/hda c::"

Start Photoshop CS2 and wait for activation dialog. It should now show
activation code. Fill in required authorization code to activate your copy.

If successful you can remove the symlink and revoke permissions to hda/sda."[/I]
I'm running into the "not enough disk space" error when trying to activate by phone as well.  It sounds like this is supposed to fix it, however I was wondering if someone might be able to translate the steps for someone completely new to Linux... such as myself :)

---

### Post by CFBauer on 2008-03-05
> **toastysquirrel said:**
> I'm running into the "not enough disk space" error when trying to activate by phone as well.  It sounds like this is supposed to fix it, however I was wondering if someone might be able to translate the steps for someone completely new to Linux... such as myself :)
I tried this as a pretty close to beginner at the command line, and ran into trouble.

Now nothing is running in wine.  I get this error:
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
wine: cannot find 'C:\Program Files\Adobe\Adobe Photoshop CS2\Photoshop.exe'

Also I'm a bit concerned that I may have not brought by permissions back to where they need to be.  I hope no baddies are reading this ;).

A running of this guy:

ls -la /dev/sd*

Shows my permissions at br--r--r-- . Does this sound right?  At this point my system security is higher on my priority list than getting Photoshop in wine, but that would be nice too.

Thanks for reading!

edit:
I may have answered my question with this thread:
[http://ubuntuforums.org/showthread.php?t=701928&highlight=default+sda+permissions](http://ubuntuforums.org/showthread.php?t=701928&highlight=default+sda+permissions)

---

### Post by SomeGuyDude on 2008-04-27
You know what's hilarious?

**I cannot uninstall it either thanks to the "administrator" ********.**

---

### Post by jermsie on 2008-05-01
Whether this helps or not I dont know.

[http://heanet.dl.sourceforge.net/sourceforge/corefonts/times32.exe](http://heanet.dl.sourceforge.net/sourceforge/corefonts/times32.exe) Install that and the tahoma font, run the setup.exe as xp

I'm just hoping that photoshop cs2 will function fine now

---

### Post by ayap on 2009-06-01
I run my Adobe PhotoShop CS2 in Ubuntu 9.0.4 under wine , when I press "T" logo in the tools bar and point it to the place I am going to type my word I have the problem of 

"Could not complete your request because of a program error" 

Can someone help ? It's look like can't support Fonts.

---

### Post by asmall on 2009-06-07
If you get this Message "Unable to continue because of a hardware or system error.
Sorry bit this error is unrecoverable" you need to install Times New Roman font:
[http://heanet.dl.sourceforge.net/sou...ts/times32.exe]("http://heanet.dl.sourceforge.net/sourceforge/corefonts/times32.exe")

---


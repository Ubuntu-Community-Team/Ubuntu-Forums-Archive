---
title: "Word Processing"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by zamby on 2008-09-17
Hello,

I am new to Linux so I apologize for any dumb questions.  I am so new I haven't even downloaded it.  I've downloaded Wubi and am loving it.  I have one problem though - I need to have Microsoft Word.  My wife is kind of open to the idea of putting Ubuntu on, but her only caveat is that she can have Office for her work.  I'm also a PhD student and need to write papers, dissertations, etc.  I can't really risk not being able to have Times New Roman or other basic fonts as I pass papers back and forth between other students.

Can anyone help me?  I'm really excited about possibly downloading Ubuntu and am hoping to find a way to make this work.  I have heard of Crossover and Wine, but have no idea what they are.  Are they emulators or programs that look like Word that my wife can double click on and not know the difference.  How do they work?  If anyone could help, that would be great.  Thanks everybody.

---

### Post by dpolehn on 2008-09-17
Have you tried to use open office?

---

### Post by anewguy on 2008-09-17
Did you install OpenOffice?  The word processor in there is very good and similar to Microsoft Word, and supposedly (I've never done it) you can read/write Microsoft Word documents.

Dave :)

---

### Post by OutOfReach on 2008-09-17
WINE is not a emulator (It says so in it's name too **W**ine**I**is**N**ot an **E**mulator) it's a compatibility layer.

OpenOffice is a lot like Microsoft Word, and you can have Microsoft fonts installed too

---

### Post by LinuxFox on 2008-09-17
Check out Open Office, it's included with Ubuntu.  It works with Word's doc files I believe.

I don't know if Word would work with Wine, though I've tried Wine with a couple of my Windows games, and I only got one game working.  There's a chance it might not work.

---

### Post by cardinals_fan on 2008-09-17
Use OpenOffice (I didn't like the current stable version at all, but the new RC for version 3 is awesome), Abiword, or, better yet, just write your docs in HTML.

---

### Post by chuuk on 2008-09-17
OpenOffice comes with the Ubuntu Desktop edition so there's no need to download anything extra, it's very similar to Word, almost no learning curve at all.

---

### Post by tuxxy on 2008-09-17
You can run word through virtualbox if you needed, also it is possible with WINE but takes a little time.

Open Office will not have windows fonts by default but you could download them in the **msttfcorefonts **package, also the spell check function isnt as accurate, other than that its excellent.

---

### Post by Sef on 2008-09-17
> I am new to Linux so I apologize for any dumb questions.

Asking a question that you don't know the answer to is _never_ dumb.  Instead it shows intelligence because you are asking to learn something that you don't know about.

---

### Post by Vivaldi Gloria on 2008-09-17
> **zamby said:**
> have Times New Roman or other basic fonts 

Start

system menu > admin > synaptic

Enable restricted and multiverse repositories from the repository settings to get a more complete list. Then click refresh. 

Now you can search and install whatever you want in synaptic. For example search and install

```
ubuntu-restricted-extras
```

which contains fonts (including times new roman etc.), java, codecs, flash, and other goodies.

---

### Post by zamby on 2008-09-17
> **dpolehn said:**
> Have you tried to use open office?

I should have clarified this.  I have played around w/ Open Office, but have not been able to find Times New Roman and I believe Arial.  Sorry for the confusion.

---

### Post by zamby on 2008-09-17
Someone mentioned that WINE is not an emulator, but a compatibility layer.  Can you please clarify what that means?  Does that mean that it makes it compatible to install a Windows CD on Linux or does it mean that it minimizes the compatibility errors between the two?  

Also, how does WINE differ from Crossover ([http://www.codeweavers.com/products/cxlinux/)?](http://www.codeweavers.com/products/cxlinux/)?)   

Sorry for all the questions.  I might be able to convince my wife, but just have to double check a couple more things.  Thanks everyone!

---

### Post by clive littlewood on 2008-09-17
Hi

just download the msttfcorefonts package using synaptic and this has both Times New Roman and Aerial in the package.

Hope this helps

cl

---

### Post by anotherdisciple on 2008-09-17
> **zamby said:**
> Someone mentioned that WINE is not an emulator, but a compatibility layer.  Can you please clarify what that means?  Does that mean that it makes it compatible to install a Windows CD on Linux or does it mean that it minimizes the compatibility errors between the two?  

Also, how does WINE differ from Crossover ([http://www.codeweavers.com/products/cxlinux/)?](http://www.codeweavers.com/products/cxlinux/)?)   

Sorry for all the questions.  I might be able to convince my wife, but just have to double check a couple more things.  Thanks everyone!


To the best of my understanding... WINE tries to translate programs into something that linux can understand. It doesn't try to be Windows... it just translates.

If you want to run windows on linux you need a Virtual Desktop... like VMware

---

### Post by zamby on 2008-09-17
All this information is great.  If all else fails, I can do the VMWare thing.  Are any of you interested w/ Crossover?  I did a google search on it, but most of the press releases seem to be from 2006 or earlier.  If anyone has any thoughts about the compatibility, I would appreciate it.

---

### Post by zamby on 2008-09-17
> **anotherdisciple said:**
> To the best of my understanding... WINE tries to translate programs into something that linux can understand. It doesn't try to be Windows... it just translates.

If you want to run windows on linux you need a Virtual Desktop... like VMware

That's great to know.  Thanks for that.  Does that mean that I have to find a Microsoft Word CD to install on top of WINE or does WINE take care of that?  Thanks again.

---

### Post by philinux on 2008-09-17
Once you've got the fonts you need. All you need to do is save files as .doc or import .doc.

No problem. No complications.

---

### Post by anotherdisciple on 2008-09-17
Using open office... somewhere in the settings you can set it to automatically save as Microsoft Word (.doc) if you need to. Open Office recognizes word documents... it doesn't need wine to run... if that is what you are asking... I'm not sure if it is.

---

### Post by halitech on 2008-09-17
as far as fonts go, if you want to install new ones, create a folder in your /home folder called .fonts (the . is important, makes it a hidden folder) and then copy the font files in there. Basically any .ttf font will work.

---

### Post by alienexplorers on 2008-09-17
Why not just dual boot.  This way you have access to Microsoft Office in Windows and you can also run Ubuntu and learn all there is about Open Office.

---

### Post by howefield on 2008-09-17
> **zamby said:**
> Someone mentioned that WINE is not an emulator, but a compatibility layer.  Can you please clarify what that means?  Does that mean that it makes it compatible to install a Windows CD on Linux or does it mean that it minimizes the compatibility errors between the two?  

Also, how does WINE differ from Crossover ([http://www.codeweavers.com/products/cxlinux/)?](http://www.codeweavers.com/products/cxlinux/)?)   

Sorry for all the questions.  I might be able to convince my wife, but just have to double check a couple more things.  Thanks everyone!

Crossover is a commercial application, ie you pay for it. It is based on Wine which is free. The few windows applications I run are quite happy running through wine, including office.

[http://appdb.winehq.org/appview.php?appId=31](http://appdb.winehq.org/appview.php?appId=31)

will give you an idea of how a particular application might run with Wine.

---

### Post by anotherdisciple on 2008-09-17
> **alienexplorers said:**
> Why not just dual boot.  This way you have access to Microsoft Office in Windows and you can also run Ubuntu and learn all there is about Open Office.

Don't dual boot if all you need is office... There are plenty of good alternatives to MS Office... 

IMO you should only dual-boot if you NEED a program that doesn't have a good alternative and it can't be run in WINE.

For instance... Autocad is a good reason to dual-boot... there isn't a good alternative for it... Yes, I know... there are CAD programs for linux... but they don't compare!

---

### Post by zamby on 2008-09-17
> **anotherdisciple said:**
> Don't dual boot if all you need is office... There are plenty of good alternatives to MS Office... 

IMO you should only dual-boot if you NEED a program that doesn't have a good alternative and it can't be run in WINE.

For instance... Autocad is a good reason to dual-boot... there isn't a good alternative for it... Yes, I know... there are CAD programs for linux... but they don't compare!

My wife and I are trying to buy a new computer.  I am probably going to buy one that comes pre-built w/ a Linux to avoid the hassle.  

If I were to have a dual boot, wouldn't I have to buy a Windows license?  Also, wouldn't the dual boot method considerably slow down my computer when I'm running linux even if i'm not using the other OS?

---

### Post by bobnutfield on 2008-09-17
> **zamby said:**
> My wife and I are trying to buy a new computer.  I am probably going to buy one that comes pre-built w/ a Linux to avoid the hassle.  

If I were to have a dual boot, wouldn't I have to buy a Windows license?  Also, wouldn't the dual boot method considerably slow down my computer when I'm running linux even if i'm not using the other OS?

Yes, you will have to have a Windows license if you are going to install on your computer, either as stand alone or dual boot.

When dual booting, the OS's are independently loaded and are not affected by each other while running.  You can access Windows files from Ubuntu (though doing the same in Windows to access Linux files is a little more complicated.)

---

### Post by Bloch on 2008-09-17
Dual booting doesn't slow down either operating system. 
In my experience it is easier to install Ubuntu on a windows system than it is to install Windows on an Ubuntu system. Most people have windows pre-installed on their system and use the Ubuntu CD to install Ubuntu - it will not disturb your windows system. 

I use Openoffice for my translation work sometimes. Occasionally I get compatibility problems, but usually only if the document has lots of complex stuff like bookmarks, automatically generated table of contents etc.
I have found Openoffice to be generally better at opening the documents I get than MS word on the mac.  To put it this way: I find Openoffice is more compatible with MS WORD 2000 than the different versions of word are amongst themselves.

Excel <-> OO calc can have problems with the display of graphics, but the tables themselves have always been fine for me.

There are lots of people who work with Openoffice and take on MS word docs regularly.
[http://news.cnet.com/8301-13880_3-9864262-68.html](http://news.cnet.com/8301-13880_3-9864262-68.html)

---

### Post by Grez on 2008-09-17
> **zamby said:**
> My wife and I are trying to buy a new computer.  I am probably going to buy one that comes pre-built w/ a Linux to avoid the hassle.  

If I were to have a dual boot, wouldn't I have to buy a Windows license?  Also, wouldn't the dual boot method considerably slow down my computer when I'm running linux even if i'm not using the other OS?

Hi Zamby.

Going back to your first enquiry: OpenOffice is very good. I've always used it at home (even under Windows) in preference to MS Office. It has always handled (and reverse-handled) MS Woed (.doc) documents very well, and I've transferred stuff between home (Open..) and work (MS..) without much hassle at all.

If you want the Arial and Times New Roman fonts by all means get them using Synaptic in the way suggested earlier. TBH Nimbus Roman No.9 L is a good replacement for Times New Roman, and Nimbus Sans L does the Arial job!

If you're wanting to share files with others, but as read-only (i.e. you don't **need** other people to edit them) then there's an excellent .pdf export facility which allows very good file sharing, and is multi-browser compatible too. I've used it a lot over the last few years and have never been disappointed with the results.

I had a bad experience with Vista on this machine and so I dual-boot with Ubuntu 8.04 (Hardy Heron). The dual-boot only affects your machine in terms of the size of your HDD partitions. You can't easily use your Linux partition for Windows, although (while people say it's not fully supported), I've had no trouble reading and writing to my Windows partition from Linux. 

I'm no great expert on Ubuntu, but it certainly beats the pants off Vista in terms of speed, stability and price (!), and when I have the misfortune to boot into Windows for the odd reason, I'm struck by the lack of responsiveness, the almost unceasing hard drive access and the sheer lethargy of the experience. 

To dual-boot, you would need to buy a licensed copy of Windows (get XP and avoid Vista like the plague!), but you could get a pre-installed job, download Linux from the website, try running it off the CD-ROM a couple of times to see if you like it before you actually then install it.

That way you get the best of both worlds. Just make sure your PC has a nice big HDD on it!

Wish you all the best!

---

### Post by zamby on 2008-09-18
> **anotherdisciple said:**
> Using open office... somewhere in the settings you can set it to automatically save as Microsoft Word (.doc) if you need to. Open Office recognizes word documents... it doesn't need wine to run... if that is what you are asking... I'm not sure if it is.


That is kinda what I'm getting at.  I heard that OOo can run Word docs and share it, but I am just worried about formatting errors.  I am a phd student so i have to write and share a lot of papers w/ graphs and tables and I've heard that OOo can be problematic w/ that.  I just want to make sure nothing gets lost in translation.  Do you know of any other that are a little more seamless?  I've heard good things from Abiword

---

### Post by zamby on 2008-09-18
After talking with my wife and finding out what we need, these are things that boil down to.  I would assume most of the "average user" has the computer for these tasks

1) Surfing the internet
2) Uploading pictures from a digital camera
3) Itunes (Unforunately can't compromise because we've bought a lot of songs from there and my wife likes it)
4) MS Office (once again, can't risk compromising because of all the charts in my research papers)

I still have to research the camera thing.  I don't mean to sound harsh, but it looks like I will have to use Windows or Mac for 3 of the 4 "must haves".  If that's the case, I don't know if I can rationalize putting Linux on there for surfing the internet no matter how much I like Ubuntu.  From a practical standpoint, I know my wife (the typical "average user") won't like jumping between environments when an OS like Mac can do it all.  If i'm missing anything, please let me know.  

I hope this doesn't sound like I'm bashing Ubunut.  I have a 6 year old computer and am running Unbuntu on a lower graphics card and still think it's way better than any OS out there.  If anyone can help me rationalize those 3 issues (at least #3,4), I would greatly appreciate it.

---

### Post by halitech on 2008-09-18
> **zamby said:**
> After talking with my wife and finding out what we need, these are things that boil down to.  I would assume most of the "average user" has the computer for these tasks
depends on what you define as 'average' ;)
> 
1) Surfing the internet
obviously no issues there are at. Can use F-spot, digikam, and other programs to import pictures from cameras :)
> 
2) Uploading pictures from a digital cameranot normally an issue unless you have a strange camera
> 3) Itunes (Unforunately can't compromise because we've bought a lot of songs from there and my wife likes it)
check here: [http://ubuntuforums.org/showthread.php?t=878395&highlight=itune](http://ubuntuforums.org/showthread.php?t=878395&highlight=itune)
> 4) MS Office (once again, can't risk compromising because of all the charts in my research papers) don't see there being a problem here but if you want to test it, install OO in windows and open them in both and see what happens

> 
I still have to research the camera thing.  I don't mean to sound harsh, but it looks like I will have to use Windows or Mac for 3 of the 4 "must haves".  If that's the case, I don't know if I can rationalize putting Linux on there for surfing the internet no matter how much I like Ubuntu.  From a practical standpoint, I know my wife (the typical "average user") won't like jumping between environments when an OS like Mac can do it all.  If i'm missing anything, please let me know.  

I hope this doesn't sound like I'm bashing Ubunut.  I have a 6 year old computer and am running Unbuntu on a lower graphics card and still think it's way better than any OS out there.  If anyone can help me rationalize those 3 issues (at least #3,4), I would greatly appreciate it.

research is the best thing to do to make sure *you* are happy with what you are getting.

---

### Post by pyromanic123boom on 2008-09-18
> **zamby said:**
> After talking with my wife and finding out what we need, these are things that boil down to.  I would assume most of the "average user" has the computer for these tasks

1) Surfing the internet
2) Uploading pictures from a digital camera
3) Itunes (Unforunately can't compromise because we've bought a lot of songs from there and my wife likes it)
4) MS Office (once again, can't risk compromising because of all the charts in my research papers)

I still have to research the camera thing.  I don't mean to sound harsh, but it looks like I will have to use Windows or Mac for 3 of the 4 "must haves".  If that's the case, I don't know if I can rationalize putting Linux on there for surfing the internet no matter how much I like Ubuntu.  From a practical standpoint, I know my wife (the typical "average user") won't like jumping between environments when an OS like Mac can do it all.  If i'm missing anything, please let me know.  

I hope this doesn't sound like I'm bashing Ubunut.  I have a 6 year old computer and am running Unbuntu on a lower graphics card and still think it's way better than any OS out there.  If anyone can help me rationalize those 3 issues (at least #3,4), I would greatly appreciate it.

I'm no expert, but here's my *opinion*. Internet? Absolutely no problem in **the least.** Firefox is cross-platform and works perfectly. Even better than IE.

Uploading Pictures - I used my sister's camera in a plug and play mode...no issues there. She had a Cannon I believe. So really, as long as oyou can mount the camera, you can pull the pictures using one of those little programs that is usually already installed.

iTunes is where you really hit a major block, to be honest. I was trying to get itunes to work in my system a few weeks ago and gave it up as a bad job. I have 4gb of RAM and was only trying to run iTunes 4.3. It still lagged with WINE (that runs most windows programs) and was virtually unusable. The only thing you could do is convert all your copyrighted music somehow using a decrypter and then use a online music store. Apple has one online, most likely.

And the MS Suite. So far, (being a recent windows to linux switch myself,) I've been using OpenOffice and it works fine for **me.** Now, I don't create tables and complicated papers. I'm only 15, so I use it for basic purposes. But I did install KOffice (a feature of kubuntu that works under ubuntu) for some pdf to doc and back to pdf for editing. KOffice seams more detailed with the advanced word editing - it has some extra things I have seen but haven't used. As a another option, you could use Ms Office with WINE or Crossover Office. Here is the offical documentation on doing just that: [https://help.ubuntu.com/community/Microsoft_Office](https://help.ubuntu.com/community/Microsoft_Office). It doesn't look difficult.

All these things may look overwhelming, especially the iTunes problem. That could kill your wishes to run linux. Personally, I switched to linux because I wanted to try it, and get away from windows and closed source. I was already using most open source programs then and downloading some torrented programs. Now, I never have to do that and don't feel bad because I am using a program that I should have paid for. Nobody charges in open source. If I were you (and people may hate me for saying this,) if you want ubuntu, you will fix the problems and go ahead with it. But maybe you should just stay with windows and not worry about the hassle. You can find some open source for windows, and if you need native programs, why switch someplace where things you need aren't native and are difficult to get to work? If you choose to install ubuntu, you can find all you need to know on the forums, other linux and ubuntu sites, and of course, google. Good luck.

---

### Post by Vivaldi Gloria on 2008-09-19
> **zamby said:**
> 2) Uploading pictures from a digital camera


I prefer taking out the memory card out of the camera and use a usb card reader. This is better on two accounts: 1) Card readers are just recognized as external disks 2) They're faster. 

So I suggest you use a usb card reader in any OS (including windows).

---


---
title: "Setting up a flash video player"
date: 2015-05-31
forum: New to Ubuntu
---

### Post by craigt2 on 2015-05-31
Hello everyone.
I recently dug out my 10 year old computer in the hope of setting it up in my parents house so they could use the internet, watch youtube/naughty film (my dad won't be telling my mam about that one) streams and do general old people stuff.
Upon trying it out....yeah. It wasn't working. My old windows xp install was running like a dog. My legit xp lost I tried a copy of tiny xp which also didn't work so I decided to give linux a crack.
In the past I've had bad experiences with ubuntu and missing drivers but I'd read good things about lubuntu bringing old computers to life. So I've decided to give it a try.
So far....
Things aren't going so great.
I have a number of issues.

1: Chromium won't boot up. I just get an error message straight away2
2: Firefox crashes when I try to play a youtube video.3
3: The whole thing isn't running very smoothly. It is all rather jerky. Text takes a while to appear on the screen. Like when you have a major memory overload....but that shouldn't be the case as this computer has 1gb of memory.

Also I wonder,
4: Is thre anyway to get netflix to work on a linux machine?

---

### Post by craigt2 on 2015-05-31
here is an example of my youtube crashes:

Add-ons: ubufox%40ubuntu.com:3.0,%7B972ce4c6-7e08-4474-a285-3208198ce6fd%7D:38.0,langpack-en-ZA%40firefox.mozilla.org:38.0,langpack-en-GB%40firefox.mozilla.org:38.0
BuildID: 20150511103309
CrashTime: 1433094884
EMCheckCompatibility: true
Email: [email]me@ctallentire.com[/email]
EventLoopNestingLevel: 1
FramePoisonBase: 00000000f0dea000
FramePoisonSize: 4096
InstallTime: 1433093230
Notes: OpenGL: X.Org R300 Project -- Gallium 0.4 on ATI R430 -- 2.1 Mesa 10.5.2 -- texture_from_pixmap
WebGL? libGL.so.1? libGL.so.1+ GL Context? GL Context+ WebGL+ 
ProductID: {ec8030f7-c20a-464f-9b0e-13a3a9e97384}
ProductName: Firefox
ReleaseChannel: release
SecondsSinceLastCrash: 1164
StartupTime: 1433094126
Theme: classic/1.0
Throttleable: 1
URL: [https://www.youtube.com/watch?v=DtxhCFg_4kY](https://www.youtube.com/watch?v=DtxhCFg_4kY)
Vendor: Mozilla
Version: 38.0
useragent_locale: chrome://global/locale/intl.properties

This report also contains technical information about the state of the application when it crashed.




This is really odd stuff since I used this computer myself until 4-5 years ago (with xp) and I used to watch streaming video just fine.

---

### Post by Mike_Walsh on 2015-05-31
In case you didn't know, 1 GB of RAM is considered absolutely minimal by modern standards, I'm afraid. You'll find that most people running the 'buntus have at LEAST 2 GB, if not 4, 6, or 8. Ubuntu (with Unity) in particular, needs a minimum of 2 GB to run anyhow at all.....this is in large part due to the 3D acceleration required by Unity.

Even Lubuntu, if you're watching streaming video, is pushing the envelope a wee bit with only 1 GB. I use Puppy Linux on an elderly Dell lappie with 1 GB of RAM; it only needs a couple of hundred MB of RAM to run Puppy, but as soon as you start playing videos'n'stuff, you very quickly max out what RAM you do have...


Regards,

Mike. ;)

---

### Post by Yellow Pasque on 2015-05-31
I think Chrome's your best bet. That's what I used on my m0m's Windows laptop, though I had to manually enable hardware decode acceleration because her APU was blacklisted for some reason. Now she doesn't complain about lagging/stuttering. 
chrome://flags
chrome://gpu

If chrome/chromium is crashing, give a more specific error message.

---

### Post by tristan16 on 2015-05-31
> **craigt2 said:**
> Hello everyone.
  Like when you have a major memory overload....but that shouldn't be the case as this computer has 1gb of memory.



As already stated, a major memory overload is *very* easy when you only have 1GB of RAM, especially with Ubuntu. Lubuntu will work much better, but you might want to find an even more lightweight alternative.

> **craigt2 said:**
> 
Also I wonder,
4: Is thre anyway to get netflix to work on a linux machine? 

Try this: [http://www.howtogeek.com/130372/how-to-watch-netflix-on-ubuntu-with-the-netflix-desktop-app/](http://www.howtogeek.com/130372/how-to-watch-netflix-on-ubuntu-with-the-netflix-desktop-app/)

As for your question's title about Flash Video Player, Adobe Flash Player for Linux has been stopped at V11.2. You can download it through the Ubuntu Software Center, or from here for other Linux variants: [https://get.adobe.com/flashplayer/](https://get.adobe.com/flashplayer/)

---

### Post by craigt2 on 2015-05-31
If 1gb is too little for basic operation (it obviously is for modern stuff) how come it used to work fine for YouTube?
Did they change something to decrease the memory efficiency of their site?

I really don't think you can so easily point to the low memory of the computer as the problem here. I remember when I had a 500mb computer, even then I could type things on the internet smoothly.

---

### Post by tristan16 on 2015-05-31
> **craigt2 said:**
> If 1gb is too little for basic operation (it obviously is for modern stuff) how come it used to work fine for YouTube?
Did they change something to decrease the memory efficiency of their site?

I really don't think you can so easily point to the low memory of the computer as the problem here. I remember when I had a 500mb computer, even then I could type things on the internet smoothly.

Many things have changed recently. For example, Google Chrome uses more memory and is a little slower than it was when it first came out.

As far as YouTube, you're running into their HTML5 conversion and the outdated Flash Player problem. YouTube is trying to move to the HTML5 standard, which means you won't need Flash Player to use it. HTML5 might use more/less memory than Flash Player, and also only works on newer browsers. As browsers get updated with more security fixes and features, there's more data to load.

The bottom line is just because a 500Mb computer worked before doesn't mean it will work as well now.

---

### Post by grahammechanical on 2015-05-31
My machine runs Ubuntu 15.04 fine with 1 GB of RAM but I also have a video adapter with 1 GB of its own memory and that makes a difference.

Apart from the amount of RAM you do not tell us anything about the hardware specification of that machine. 

Regards.

---

### Post by mattharris4 on 2015-05-31
> **tristan16 said:**
> As already stated, a major memory overload is *very* easy when you only have 1GB of RAM, especially with Ubuntu. Lubuntu will work much better, but you might want to find an even more lightweight alternative.

Try this: [http://www.howtogeek.com/130372/how-to-watch-netflix-on-ubuntu-with-the-netflix-desktop-app/](http://www.howtogeek.com/130372/how-to-watch-netflix-on-ubuntu-with-the-netflix-desktop-app/)

As for your question's title about Flash Video Player, Adobe Flash Player for Linux has been stopped at V11.2. You can download it through the Ubuntu Software Center, or from here for other Linux variants: [https://get.adobe.com/flashplayer/](https://get.adobe.com/flashplayer/)

I use a replacement for Adobe's Flash Player called Pepper Flash.  Here is more about it, the article states it does not work with Firefox but it does actually work with that browser now as well (at least in my experience).  Of course you can install and use Chromium if you wish.

[http://www.omgubuntu.co.uk/2014/06/install-pepper-flash-chromium-ubuntu-14-04](http://www.omgubuntu.co.uk/2014/06/install-pepper-flash-chromium-ubuntu-14-04)

Whether you can get this computer to run Lubuntu with only 1GB RAM is dicey.  Many sites will work assuming the CPU is up to it but there is that 20% or so that require more RAM.  In my experience the most RAM I use with Lubuntu is about 1250-1300MB.  If the computer is only ten years old you should be able to pull a stick, get the specs for it off of its sticker and purchase higher capacity RAM sticks off of Amazon.  Any CPU that is a Pentium 4 3.0GHz (the first dual-core CPU, sold between 2002 and 2007) or better should run although scrolling CPU hog webpages will be jerky and tedious with a delay in responding to clicks and scrolling.  I usually recommend at least a Core 2 Duo or better when people are looking for a refurb computer but I used the aformentioned P4 3.0GHz CPU in my computer with both Edubuntu and Xubuntu and until recently it worked well enough (I think the computer itself is nearly dead rather than some major change in the OSes in the past two weeks).

Things have changed drastically since 2005.  That year I bought a new computer then with 256MB of RAM and a Pentium D CPU and ran XP on it until it died five years late (512MB RAM and a P4 CPU was top of the line then).  My parents first computer in about 1997 was only 32MB RAM (I don't remember what CPU it had but I have a laptop from that era someone gave me with 16MB RAM and a Pentium 1 CPU so theirs should have been in that general line).  My first computer in about 1982 had 16KB (kilobytes, 1024KB=1MB) and a cassette tape recorder to save data on cassette tapes like we used to play in our stereos.

Netflix is supposed to work with Chrome only in Linux but when I tried it with that P4 computer it kept glitching and did not play smoothly.  I haven't tried it on a newer computer with Linux on it.  If your parents want Netflix I would recommend spending the $150 and buying them a newer refurb computer, Newegg and Tiger Direct sell them but make sure you get at least a Core 2 Duo CPU, at least a 250GB hard drive, 4GB RAM and a DVD-RW (DVD burner) drive -- and check the warranty length to make sure it has a one year warranty and not just 90 days.  You can check the Passmark score on a CPU, Google the CPU along with the word Passmark.  Ideally you want something that Passmarks at 1250 or higher.  As I said above you are looking at about $150 or so for these specs.  They come with Windows 7, you can dual-boot with Lubuntu, Xubuntu, Ubuntu, etc and if it won't play in the Linux install they can boot up Win 7 and play it on that.  

Of course if you are willing to spend the cash a new computer is an option, you can buy a computer with an i3 CPU, 500GB HDD, 4GB RAM, Win 8.1 and a DVD burner drive for $450-$500.  Don't buy an HP new if you wish to run Linux on it (a refurb HP should be OK if it is at least three years old and runs Win 7), they have designed their UEFI to only boot Windows and it is a pain to change code to trick it into booting into GRUB where you select either Windows or Linux.  Sonys as well as some Toshibas and Acers also have a similar issue (although my Toshiba laptop made in early 2014 dual-booted fine).  Dell actually sells computers with Ubuntu pre-installed (unfortunately the available choices in the Ubuntu pre-installed line are only laptops with Celerons, Pentiums and i7's with no i3s or i5s available -- don't buy a Celeron, a Pentium should be OK but it is the bare minimum for a new computer IMO but is less than $350 and the i7 is a top of the line processor but costs $1300 so I cannot recommend it just because of cost) and people say they dual-boot just fine if you buy one with Win 8.1 on it.  If you have a VGA or HDMI monitor you should be able to re-use it with a new (or in the case of VGA a refurb computer).

---

### Post by deadflowr on 2015-06-01
Post the output of the following command from a terminal:
```
sudo lshw
```
copy the output of that command and come back to this thread and use either adv reply or reply to thread so you can use the easy to use code tags.
(in reply to thread, or adv reply click on the # symbol for code tags, then paste the copied output in between the two code brackets.)

The requirements for flash (or any video streaming for that matter) use are more demanding now then they were only a few years ago.
So knowing what your system has will make it far easier to give advice going forward.

Edit: Oh and I was going to say, Google Chrome runs Netflix out of the box, no extra anything needed.
You need to go to google's chrome web page and download it from there, then double click on the file to start it's installation.

Also, I think the ehoover-compolio ppa for netflix-desktop is dead and moved to the more robust pipelight 
see: [http://pipelight.net/cms/install/installation-ubuntu.html](http://pipelight.net/cms/install/installation-ubuntu.html)
You can use the pipelight packages if you want to use firefox, or other browsers other than chrome.
fwiw

---

### Post by monkeybrain20122 on 2015-06-01
As others said, we need to know the specs of your machine. 1 G is sufficient to run lubuntu. You probably have other issues rather than ram.

---

### Post by monkeybrain20122 on 2015-06-01
> **Temüjin said:**
> I think Chrome's your best bet. That's what I used on my m0m's Windows laptop, though I had to manually enable hardware decode acceleration because her APU was blacklisted for some reason. Now she doesn't complain about lagging/stuttering. 
chrome://flags
chrome://gpu

If chrome/chromium is crashing, give a more specific error message.

Chrome is a memory hog though. I think the best option for flash streaming is Firefox + [https://addons.mozilla.org/en-us/firefox/addon/watch-with-mpv/](https://addons.mozilla.org/en-us/firefox/addon/watch-with-mpv/) Works for many sites (need to install mpv and youtube-dl) It uses a lot less resources than any flash or html5 option.

---


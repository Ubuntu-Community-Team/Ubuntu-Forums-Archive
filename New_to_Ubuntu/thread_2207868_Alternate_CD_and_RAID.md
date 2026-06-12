---
title: "Alternate CD and RAID"
date: 2014-02-25
forum: New to Ubuntu
---

### Post by ken18 on 2014-02-25
I want to install Software RAID using 12.04 Desktop and have read that RAID options are available using the "alternate CD".  I know I can install server then install desktop but I like the idea of a single step instead of two.  Trouble is, I don't know what to pick for the download.  Is the following site the right one?

[http://www.ubuntu.com/download/alternative-downloads](http://www.ubuntu.com/download/alternative-downloads)

Also, if I pick the  "Ubuntu 12.04.4 LTS torrents" option, the ISO file is only 28.8k in size.  A regular ISO is more like 670MB.  What am I doing wrong or not properly understanding?

Ken

---

### Post by Bryan55 on 2014-02-25
You have gone to the wrong place. Look here [http://cdimage.ubuntu.com/releases/12.04.4/release/](http://cdimage.ubuntu.com/releases/12.04.4/release/)

This might help. [https://help.ubuntu.com/12.04/installation-guide/](https://help.ubuntu.com/12.04/installation-guide/)

You can go straight for the Desktop.

Bryan

---

### Post by zvacet on 2014-02-25
I don´t believe you are doing anything wrong. File 28.8kb is probably torrent file so save it and then open with torrent client.I can not think of anything else.

@ **Bryan55**

He is not on wrong link.He can not use link you gave to him,because there is alternate Cd just for power pc. :wink:

---

### Post by Bryan55 on 2014-02-25
Sorry you were in the right place but the other link should help.

---

### Post by ken18 on 2014-02-25
Actually, there is something I'm not understading.  My perception of an 'alternate CD' is another ISO that should be the same size or larger than the standard ISO since it has more features (i.e. RAID options).  Does such an ISO exist?  I only mentioned bit torrent because that was the only thing on the page that made any sense at all.  I'd really rather avoid having to install some client just to install Ubuntu.  I'm definitely missing something (conceptually).  What is it?

---

### Post by Vladlenin5000 on 2014-02-25
> **ken18 said:**
> I'm definitely missing something (conceptually).  What is it?

Truth to be told you're missing/misunderstanding a lot of concepts:

1. Torrent. I guess you never used otherwise you'd know at least the basics and why you don't need it if you don't want because...
2. You can download the exact same ISO file directly in your web browser, in the same page, [B]but is it what you really want/need?

[/B]3. "Alternate CD" has exactly the same OS of the regular one, the only difference is the installer.

[B]*AND*


[/B]4. I already told in another thread that **Ubuntu and many others has native support for your Intel Matrix**. It doesn't matter which version, flavor, desktop or server (and you want desktop, use the regular ISO for Ubuntu 12.04 or 13.10, your choice) but most important of all
**5. Having a hardware (BIOS) *real* RAID manager already, why on Earth someone would want to have a software one? **I can tell you a couple of reason but none concerns you in regard of what you want. You already have a RAID capable motherboard and it supports the RAID level you want;
6. There's no specific way to install Ubuntu for installing in an array already created when the installation starts different than in a non-RAID system.

***AND***

7. What you need to do in your Dimension with Intel Matrix is, during POST, press CTRL+I and configure your array using the Intel tool (OS independent, obviously) and proceed installation as usual, booting from CD/DVD or USB. The (Ubuntu) installer will see your array as it is.
8. Software RAID - this one is the fake-RAID, not the other way around - is something you do with a software already installed in a OS, in turn installed in a non-RAID system.

---

### Post by ken18 on 2014-02-25
Before I continue, I have to say I greatly admire anyone who is willing to reply to posts in an "Absolute Beginners Section".  It must be extremely frustrating to deal with people that know far less than they do.  The patience they exhibit is to be commended.  Now for my reply:

(1) Alternate CD - when I go to the 'Alternative downloads' page the only items I see to download are (a) Network Installer, and (b) BitTorrents.  (the only reason I mentioned BitTorrent in my previous post is that I figured I didn't want Network Installer).  The only other thing on the page are links to other images by country.  I guess I now need to assume that 'links to other images' is the right place to go.  I pick an appropriate mirror and see a directory.  Not sure whether to pick '12.04.03' or '12.04', but if I pick '12.04' and 'release' I see several main headings: 'Desktop CD', 'Alternative Install CD', 'Install/Live DVD', 'Preinstalled desktop image', 'Preinstalled desktop filesystem archive', and 'Preinstalled server image'.  Under the 'Alternative Install CD' heading there appears to be only a 64-bit version (my machine is 32-bit).  Does that mean PC (Intel x86) install/live DVD is the right one? 

(2) I decided to try Software RAID (i.e. instead BIOS RAID) simply as an experiment to see the difference.  I'm in leaning mode and in general find it useful to try different approaches as a way to learn.

(3) BIOS RAID - I'd rather reply on the other thread so as to not mix topics.

Regards,  Ken

---

### Post by Vladlenin5000 on 2014-02-25
The one you want is this: [http://cdimage.ubuntu.com/releases/12.04.4/release/ubuntu-12.04.4-dvd-i386.iso](http://cdimage.ubuntu.com/releases/12.04.4/release/ubuntu-12.04.4-dvd-i386.iso)
the standard 32-bit 12.04.4 directly from the server. "Alternative downloads" and "alternate CD" aren't the same things, just sound similar... The former (your first link) is for the latest release via (or for) network install, to download the latest release ISO via torrent, hence the provided torrent file (the small one) and for previous releases (12.04.3 and earlier) from a few mirrors (content varies); the latter - alternate CDs/DVDs are ISOs featuring an alternative text-mode installer. Again, you want the one linked above for your convenience.

PS - But why not use torrent? Ubuntu have TransmissionBT installed by default, one of the best clients around.

---

### Post by ken18 on 2014-02-25
Thank you!  Looks like the same one I found by going here:

[http://www.ubuntu.com/download/alternative-downloads](http://www.ubuntu.com/download/alternative-downloads)

Then: Other Images (United States in my case) ==> 12.04/ ==> release ==> Install/live DVD ==> 'PC (Intel x86) install/live DVD'.  I must say, it's hard for a newbie to know/understand the above path will arrive at the 'alternative download' for x86.  That's why I'm so thankful for this forum!  Thanks again for your help.

Re why not use torrent, it's important to crawl before walking before running...

Ken

---

### Post by mastablasta on 2014-02-26
as a newbie then you would just go here and download desktop: [http://www.ubuntu.com/download](http://www.ubuntu.com/download)

text installer was there for people with old mashcines that couldn't run the nicer graphical installer. and that is all there is. if you have 512MB ram or more the graphical installer will run. if you have less than 256MB (where you would need alternate installCD) then you can't run latest desktop anyway. for those there are other distros (like Lubuntu) or minimal barebones OS install iso (= network installer - where you install basic os from CD and the rest you pull off the internenet).

why torrent was suggested - because when you are donwloading usign torrent the file is conctantly checked for consistency and in the end you get exactly same file as it was on server. while with normal download and big files small part of file can get lost. and since this is OS image you can get a lot of issues if small part get's lost during dowload. to avoid any errors always do this after downloading the image : [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

beside when you use torrent you help others by sharing the server load, sharing the downloaded image...

---

### Post by zvacet on 2014-02-26
@ [B]ken18
 
[/B]I don´tknow if you can get alternate CD for your architecture.As far I understand from [here]("http://cdimage.ubuntu.com/releases/12.04/release/") it is only for power pc architecture.I´m not famialiar with installing on RAID with regular Ubuntu image.

---

### Post by ken18 on 2014-02-26
Yep, I'm more or less convinced that what I'm looking for does not exist (i.e. Desktop x86 Ubuntu 12.04 with manual partition options for RAID).  The ISO from the following link turned out to have no manual partition options:

[http://cdimage.ubuntu.com/releases/1...4-dvd-i386.iso]("http://cdimage.ubuntu.com/releases/12.04.4/release/ubuntu-12.04.4-dvd-i386.iso")

Unless I'm still missing something (entirely possible), I guess I'm stuck installing the server version (to get the manual partition options), then install desktop on top of it.  I'm really surprised, because in my web searches I've seen so many references to 'alternate download' as a way to get RAID install options, but the site:

[http://www.ubuntu.com/download/alternative-downloads](http://www.ubuntu.com/download/alternative-downloads)

doesn't appear to have an appropriate link for my machine.

---

### Post by sudodus on 2014-02-26
'Something else' at the partitioning page of the desktop installer is manual partitioning, but I think you need to install Ubuntu ***server*** to get RAID.

---

### Post by ken18 on 2014-02-26
Hmm.  From the below site:

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

I found the following:

If you're building a desktop then you need the "Alternate" install CD for Ubuntu. Read [Getting Ubuntu Alternate Install disk]("https://help.ubuntu.com/community/GettingUbuntu#head-40b5bcdbc1d4ec7b8149519dfd4f08c7fa274559") and [How to do a Ubuntu Alternate Install]("https://help.ubuntu.com/community/Installation#head-194b248381c71c37f7b187c6b814bbe7e31d91d6")

Trouble is, the trail quickly runs cold on actually finding the 'Alternate Install CD'.  So far it appears to be a phantom.

Ken[URL="https://help.ubuntu.com/community/Installation#head-194b248381c71c37f7b187c6b814bbe7e31d91d6"]
[/URL]

---

### Post by sudodus on 2014-02-26
What about the official Ubuntu site to download Ubuntu Server?

See the attached screenshot! Downloading started automatically for me, but if you click on [COLOR=#ff0000]download now[/COLOR], you get the small dialogue window ...

Edit: I browsed the internet for ***download Ubuntu server*** and found [http://www.ubuntu.com/download/server](http://www.ubuntu.com/download/server)

---

### Post by ken18 on 2014-02-26
I want the desktop.  I know I can download and install server, then install desktop on top of that (i.e. sudo apt-get ubuntu-desktop), but I was rather hoping for just one step installation, not two.

---

### Post by sudodus on 2014-02-27
RAID is less used and therefore less described. So a good strategy is to use the available instructions to install RAID as the first step, and then install the desktop environment as a second step.

---


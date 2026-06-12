---
title: "Problems with HP Printers"
date: 2013-02-04
forum: New to Ubuntu
---

### Post by Javelin Dan on 2013-02-04
Running Ubuntu 12.04 Ppc on an emac G-4, 80 GB hard drive, 1 GB RAM, 1 Gz processor.
   
   
  Until last week, I&#8217;ve been using an HP Photosmart D110 all-in-one printer / scanner. When I got it, everything worked fine. Eventually, it got so it would scan and print text perfectly, but photos would print streaked and blurry and look sort of like an impressionist painting. I tried dumping the driver (originally loaded through plug-n-play via Ubuntu) and re-installing via HPLIP, but it worked the same. So last week I bought a new HP Deskmate 3510e all-in-one printer / scanner.
   

   At first, I tried installing it through plug-n-play; it would print just fine, but trying to use Simple Scan (or the scanning utility on the printer) showed &#8220;no device found&#8221;. I then downloaded the proper driver from HP&#8217;s website, and installed it following their installation wizard. Everything worked, but while the photos print a little better, they still appear somewhat streaked. BUT, now when I shut down the printer and restart it, I&#8217;m back to square one and have to reload the driver in order to recognize my scanner. 
   

  I called HP&#8217;s Help Center and talked to a nice man in a far-off, foreign land. He politely informed me that HP does not actually &#8220;directly&#8221; support Linux, but all the help available must come from the HPLIP website. Other than downloading and installing the correct driver, I&#8217;m lost. Anyone have any suggestions?

---

### Post by oldfred on 2013-02-04
I just installed a HP3520. And did somewhat the same. It installed a default driver automatically.
But then I went to the HP site and installed. Once I got the HP Device Manager working I was able to correctly configure Wifi and other settings. But I had to uninstall the old printer that I had installed from Ubuntu.

Is the 3510 new or very old? I do not see it in this list of 3500?
[http://hplipopensource.com/hplip-web/models/deskjet/deskjet_3500.html](http://hplipopensource.com/hplip-web/models/deskjet/deskjet_3500.html)

---

### Post by Javelin Dan on 2013-02-04
Yes – the printer is brand new. I bought it at a “large box retail store” that uses a lot of the color red. You’re right, I checked out that same list and didn’t see it either, but when you start searching for drivers’ it’s there. 
   
  Please give me precise instructions on how to uninstall the old drivers. All I did was go into “Print Manager”, highlighted the installed printer, right clicked, and clicked “Delete”. The printer icon went away. Is that good enough or no?

---

### Post by Javelin Dan on 2013-02-04
One thing I forgot to say in my previous post - As I was watching the progress of re-installation of the driver from HPLIP last night, I noticed one section where it said "Making Clean". Is that not removing old drivers?

---

### Post by oldfred on 2013-02-04
I just followed the auto script. At some point I had three printers installed. I just uninstalled all and reinstalled one from the HP Device Manager to have a clean install.

One of the command I run is this. I did not pay attention if script ran it or not.

       apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)

---

### Post by DuckHook on 2013-02-04
I've found that the best way to install HP printers is through the HPLIP GUI Toolbox. This will automatically find your printer (even over a network), match it up with HP's printer database, and download the appropriate driver for you that allows not only printing, but faxing and scanning support. Downside: it hauls in a bunch of QT dependencies and generally bloats up your system, so not recommended for QT critics or those who want minimalist systems. I put up with it because the resulting ease of use is very attractive.

If you want to go this route, do:

```
sudo apt-get install hplip-gui
```To set up your printer you will have to do:

```
gksudo hp-setup
```You must invoke hp-setup app as root (as per above). If you try to setup your printer using the more intuitive GUI app in your launcher, the setup process will run, but then it will choke at the point where it tries to install the driver because it is only running with user privileges. Took me a few installs to figure this out. It would be nice if the setup app was smart enough to realize that it had insufficient privileges and to run the sudo routine from the outset, but it isn't, so please make sure you invoke it with gksudo.

If your network is broken into a lot of separately switched segments like mine, then hp-setup will also fail to automatically find your printer. If so, then assign your printer a static IP and manually point hp-setup to that IP address. It should recognize the printer and automatically set it up for you from there.

---

### Post by Javelin Dan on 2013-02-05
I&#8217;ll apologize in advance if this is a little wordy, but I feel it&#8217;s important to be descriptive when something works to make it understandable for other newbies like me who might stumble across this later. Here&#8217;s what I did:
   
   
  I first followed DuckHook&#8217;s script which did eventually get me to the GUI set-up page for configuring the printer. As soon as I got there, I realized I had already been there. Previous to my original post, I had actually found the installer for the GUI in Synaptic and tried that as well. But in both cases, after I made sure the connection source was USB and clicked continue, the next page frustratingly showed no devices found. I recycled this a couple of times to make sure with the same results. Thanks DuckHook, but time to try something else. 
   
   
  I next logged onto the HPLIP website. The night before my post, I had been on this page and followed the installation instructions from A to Z. The first thing you do is select your operating system, printer series, and exact model number. Next, you download a &#8220;run&#8221; file which I am assuming contains the actual driver plus a set of automated installation instructions for your computer to follow. In my case, it looked like this: hplip-3.12.11.run. You are next instructed execute a &#8220;cd&#8221; command to start running this script: &#8220;*cd Desktop&#8221;* then *&#8220;sh hplip-3.12.11.run&#8221;. *A bunch of stuff happens here and you are asked a few questions along the way, and one of them is that the old driver is uninstalled and &#8220;made clean&#8221;. I was told that hplip-3.12.11.run already existed and was asked if I would like to replace it with any updates. Figuring that updated is always better, I said &#8220;yes&#8221; and let the installer run. Ultimately, the GUI popped up and when I clicked to the second page looking to find my printer, it wasn&#8217;t there - no devices found! Doah!!
   
   
   I next tried the &#8220;manual&#8221; set-up where you are asked about every decision concerning the installation. Other than that, it is basically the same automated installation procedure as in the automatic install. After I clicked on all my choices, I realized that they were all the same ones included in &#8220;automatic&#8221;, so I&#8217;m not sure there was any advantage for me. But once again, I chose to opt for any updates. This took noticeably longer and ultimately failed at the same point with the GUI showing no devices. Damn it!
   
   
  I started racking my brain trying to figure what I had done differently the night before that at least allowed the printer to work normally until I shut it down. I then realized that the previous night I had NOT chosen to replace the &#8220;run&#8221; file with an updated version, but had just used what had already been downloaded to my desktop. I repeated the auto install, but this time using hplip-3.12.11.run file I already had on my desktop. When the GUI came up and I clicked to the second page, I was rewarded with seeing my printer there highlighted in blue! I completed the installation prompts and everything now worked as before, scanning included.
   
   
  Now I&#8217;m trying to reason why previously, everything headed south once I shut down the printer. A light bulb came on and playing a hunch, I went into the print manager (for any newbies it&#8217;s Applications &#8211; System Tools -Printing). There were two icons for my printer; HP 3510, and HP 3510-2. I have no idea why it installs two icons, but I had noticed this on a previous attempt. Anyway, I realized I hadn&#8217;t chosen one as my default printer before. You aren&#8217;t told to do this anywhere, and again, I was just playing a hunch. But which one to choose? I literally did the &#8220;eeny, meeny miny, mo&#8221; routine and picked the one on the right &#8211; HP 3510-2 (right click, select make default printer). It worked!! I have since shut down both the printer and computer about four times and still have full function of printing and scanning. 

   
  I learned three things that at least I need to do to make this work for me (your mileage may vary):
  [FONT=Calibri]1.)    [/FONT]Download the &#8220;hplip.run&#8221; file as prompted in the beginning of the install and save to the desktop. 
  [FONT=Calibri]2.)    [/FONT]Refuse to update or replace that file when asked.
  [FONT=Calibri]3.)    [/FONT]Make sure to select the installed printer as &#8220;default&#8221; after installation (I chose the second icon on the right). 

   
  I&#8217;m going to leave this thread open for a couple of days to make sure nothing changes and then I&#8217;ll mark it &#8220;Solved&#8221;. I&#8217;d still like someone to weigh in on why my photo printing is streaked. It may have changed when I moved from Ubuntu 10.10 to a clean install of 12.04 &#8211; I don&#8217;t recall having the problem before that. Maybe something to do with the powerpc thing? Any comments welcome. Thanks to all who tried to help!

---

### Post by Javelin Dan on 2013-02-20
I will go ahead and mark this as &#8220;Solved&#8221; with a final note. The streaky printing of photos was bugging me and I did a lot of thinking about it. It seemed to me that it only started AFTER I did a clean install of 12.04 from my previous install of 10.10. I then started thinking that it may have to do with all the hinky interactions that take place between a powerpc Mac and Ubuntu Linux. So I decided to try an experiment. I hauled the printer downstairs and connected it to my Compaq Presario dual core laptop running the x86 version of Ubuntu 12.04 and installed the driver. I transferred the same pictures I was trying to print on the Mac via a flashdrive and they printed perfectly! Apparently, I will just have to live with this arrangement until or unless it is addressed in a future update. At least I know I can print what photos I need to on the Compaq if necessary.

---


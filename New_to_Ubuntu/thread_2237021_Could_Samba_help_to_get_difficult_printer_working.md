---
title: "Could Samba help to get difficult printer working?"
date: 2014-07-30
forum: New to Ubuntu
---

### Post by Sleepy-zz-John on 2014-07-30
Hi,   Been trying for years to get a Lexmark  Z2420 printer,  which works fine on Windows, working on recent Ubuntu distros without success.  No compatible driver or .ppd file since Ubuntu 10.10 and Lexmark gave up their support.    I have Lexmark's Windows installation CD and it's easy enough to get the printer working in Windows, both USB and wifi with a fixed IP address.

Just wondering if there's a chance that Samba could get it working.   Sorry I'm not really clear how Samba works and what it can or can't do.  Could I, after installing Samba,  hope to be able to use Lexmark's Windows CD to install the printer and get it working on Ubuntu that way?  .  .      

Had problems understanding Samba documentation so just looking for guidance.at this stage as to whether Samba would be worth pursuing in this kind of situation.   

Tks.

---

### Post by kc1di on 2014-07-30
Samba is most likely not the solution unless you want to hook it up as a network printer, even then you still need the printer driver to work in linux. 

Best chance I believe you would have is using NDIS wrapper.  It works with some print drivers.  Not sure about Lexmark - they had a bad reputation with linux.
here's[ a page]("http://www.cyberciti.biz/faq/linux-ndiswrapper-wpa_supplicant-howto/") that may be of help.

also [here.]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

---

### Post by plucky on 2014-07-30
Could [This](http://ubuntuforums.org/showthread.php?t=1442219&p=9046926&viewfull=1#post9046926) help?

Good Luck

---

### Post by Sleepy-zz-John on 2014-07-30
Many thanks for the suggestions folks,  and for the good luck wishes which will very likely be necessary for the difficult task I'm trying to crack.  ](*,)

I'm going to try your NDIS wrapper suggestion,  kc1di, and hope to come back with a report on whether it gets me anywhere or not in due course.  

I'd already tried the lexmark-08z-series-driver-1.0-1.i386. driver suggested in your link to 2010 threads,  plucky, where they were on Lucid and Natty.  My installation appears to complete OK on Precise but fails to print anything,  the cause if I understand correctly being incompatibility of later Ubuntu distros to work with either that driver or Lexmark's .ppd file.   This is reflected by Lexmark only showing drivers compatible with Ubuntu distros up to 2010 on their website.   Hmmm...   :icon_frown:

I'm just wondering if there's any hope that the driver incompatibility that I suspect first occurred with Maverick,  could be retrospectively corrected in Trusty??      Any thoughts?

---

### Post by Sleepy-zz-John on 2014-08-17
I installed Ndiswrapper and its GUI supplement ndisgtk and tried to follow the steps in the cybercity link that kc1di suggested.  Found LXDQprc.inf  and autorun.inf on the Lexmark CD that came with the printer,  and tried installing those,  but Ndiswrapper marked them both as invalid drivers.  Couldn't find any other .inf files on the CD.  Looked for .sys files there too,  but failed to find any.  Also looked for Lexmark .inf and .sys files in the Win7 installation where the printer is installed and working in wireless mode,  but without success.    Not sure whether I'm just not looking in the right place for these .inf and .sys files or whether it's Ndiswrapper that basically can't handle Lexmark stuff.   

It's frustrating that this Lexmark installs and works perfectly well on Windows,  but I can't find any way of getting it to work on Precise.

---

### Post by mv-baker-146 on 2014-08-18
I know a silly question, but any reason you're still struggling with the Lexmark? we had a Dell AiO which was a rebadged Lexmark and it gave us no end of trouble (came free with the Dell ;) laptop). Now using an Epson workforce on WiFi and it's been a breeze to setup (precise and trusty) - probably about the same price too.
btw, can network print with Samba onto a win-7 PC OK

---

### Post by Sleepy-zz-John on 2014-08-18
No,  that's a fair enough question mv-baker-146.  Actually the printer isn't my own.  I'm trying to get it to work for a none-too-cyber-savvy neighbour who I've managed to persuade and help to go over from winwoes to Ubuntu.  They only need to use their printer very occasionally. but my inability to bring this Lexmark over to Ubuntu means struggling on helping them to maintain their troublesome Vista    It would be so much easier and cleaner if we could completely abandon their winwoes.   Part of the argument is because this Lexmark continues to work perfectly on Windows.   Hard to consign it to the rubbish bin and expect them to fork out for a new one under these circumstances.

So I'm still looking for a miracle solution here!

---

### Post by JKyleOKC on 2014-08-18
I had a somewhat similar situation here in which I could not get either of my two printers to work properly via CUPS (I eventually discovered that I was not using the correct communication technique and they do work properly now). In order to make them work, I created a virtual machine (using VirtualBox) with minimum resources, and installed a copy of WinXP on it. When creating the VM, I set it up to be a separate independent station on my little LAN, but it could have been set up to be only a slave on the machine hosting VBox so that it acted very much like a rather large printer driver.

I then installed the printers in that copy of WinXP, using the manufacturer's CDs, and configured them for file sharing. I disabled all updating and external web access for the copy; its only purpose was to be a local print server for the machines on my LAN.

Finally, back at the host (and the other machines on my LAN, four at the time) I configured CUPS to connect to the networked printers.

This worked quite well for a couple of years, until I finally discovered almost by accident how to configure CUPS properly for direct connections! It might be more than a slight bit of overkill for a non-technical neighbor's system, though. Virtual machines seem very much like magic to non-geeks -- my wife still doesn't believe in their existence, although I've put two of them on her Win8.1 system, so that she can run some of her favorite games left over from Windows 3.1 days, and she uses them like any other program...

---

### Post by dave131 on 2014-08-19
I don't believe you can use ndiswrapper either - I think ndiswrapper is only for things like network controllers on your PC - not for remote devices.

---

### Post by dave131 on 2014-08-19
Deleted. I accidently posted before I was finished.  The finished post is below.

---

### Post by dave131 on 2014-08-19
Try:

- open System Settings

- open Printers

- click Add

- select the printer (may just be a raw device on a USB port)

You may want to follow this link.  While it is in a discussion about a Dell printer, judging from what it is showing I think it applies to most any printer:

[http://askubuntu.com/questions/179957/where-can-i-find-the-ubuntu-drivers-for-a-dell-1700-printer](http://askubuntu.com/questions/179957/where-can-i-find-the-ubuntu-drivers-for-a-dell-1700-printer)


BTW - I downloaded the linux driver from lexmark but the downloaded file is actually a binary and the driver is included within that binary, and it doesn't install in newer versions of Ubuntu.  Looks like the last supported was 10.xx .  I tried running it but it comes up with an error - it's looking for a file in a specific system path and it's not found.  I tried a find on the file name and it appears it is no longer included with Ubuntu.

08/19/2014 EDIT:  I was able to get the installer to start, but there are other errors being encountered when it actually tries to install.  I have asked for help and gotten great help in a thread I opened, but no solution has been found yet.  I'm keeping me fingers crossed that someone can figure something out so that if worse comes to worse we get the driver-only files loaded somehow and then let Ubuntu find the printer via the above suggestions for Printers.  Don't know if that can be done either.  The main problem here is that lexmark hasn't offered any updates to that driver since 2010 and for what is now a really old version of Ubuntu.  It may end up not being possible.

---

### Post by dave131 on 2014-08-21
I found something I need you to try as I *think* it's the driver for your printer!

(1) go to [http://www.mediafire.com/download/w545ftercecb1vu/New-lexmark-08z-series-driver-1.0-1.i386.deb.deb](http://www.mediafire.com/download/w545ftercecb1vu/New-lexmark-08z-series-driver-1.0-1.i386.deb.deb)

This will download the driver installation file and put it in your Downloads folder.

Now do this:

(1) Open a terminal window - ctrl/alt/F1

(2) Type:

sudo dpkg -i New-lexmark-08z-series-driver-1.0-1.i386.deb.deb

When that completes, do the following:

(1) hook up the USB cable to your printer

(2) go to System Settings

(3) click on Printers

(4) click Add

(5) *hopefully* your printer will show in the list - click on it and follow the on-screen prompts.  When it asks, try printing the test page.

*IF* this works, you should be able to try the wireless printing next.

Please post back with any and all results/questions.

---

### Post by Sleepy-zz-John on 2014-08-22
Oh,  fantastic!!    It works!   After struggling for 2 years, finally we have success!    That new driver New-lexmark-08z-series-driver-1.0.i386.deb.deb is clearly the secret that's done the trick.  

Once I had it working via USB,  for the wireless, I unplugged my USB lead and used CUPS to install a new printer which I simply called "Lexmark Wireless".  Using Lexmarks Windows software, I had previously set the Lexmark up to use a fixed IP address (in my case of 192.168.1.69) and I'd already set my router to use that same fixed IP address.  So then in CUPS I set socket://192.168.1.69:9100 and that was it.  It did a test print via wireless without any problem.  The net result is that in Settings -> Printers I now have two Printers,  one is "Lexmark" which works on USB,   the other is "Lexmark Wireless" and they both work equally well.  

So thank you very much Dave 131.  Very good result!    I'm quite curious to know where this new driver has come from and who produced it so that I can thank them.

---

### Post by dave131 on 2014-08-22
Here's the link to the page:

[http://askubuntu.com/questions/71424/how-do-i-get-a-lexmark-x4690-printer-working/514846#514846](http://askubuntu.com/questions/71424/how-do-i-get-a-lexmark-x4690-printer-working/514846#514846)

I'm glad this worked for you!  I'm just a newbie myself so this was a rather exciting thing to work on, and I'm glad someone had a solution for version 11.xx that still works now.  I was able to install the driver on my PC with version 14.04 - I just don't have a printer like that to test it with - but I might assume since it did install that it might work in 14.04 as well.

Thank you for letting me work on this with you.  It's been a real learning experience for me!

dave

BTW  if you could go to the first post on this page, select Thread Tools, then mark as solved it would be great as then others could see there is a solution.

---

